ircDDBGateway “Node” Dashboard {.western}
==============================

By: John Hays, K7VE

\

IrcDDBGateway node dashboard is a lightweight, real-time, self configuring dashboard for G4KLX's

D-STAR gateway. Both the server and client are written JavaScript.
Presentation is in a single index.html file with css styling.

\

Adding local content to the webpage is simply a matter of editing the

**index.html** file.

\

Additional html pages can be added to the 'public' folder.

\

The dashboard will run on the computer where ircDDBGateway is installed.

Preparation {.western}
-----------

This dashboard requires the installation of node.js, a framework to run server applications written in JavaScript.

\

A fairly recent version of node.js should be used v0.10.0 or newer should be sufficient. Due to limited availability of v4.0.0 or newer on ARM based computers like the Raspberry Pi, it has not been extensively tested on that platform.

All testing has been on Linux based systems, mostly Raspbian and Ubuntu. It will likely run on Windows[^1^](#sdfootnote1sym) or MacOS if the paths to configuration and log files are available.

\

The main **node.js** installation site is [https://nodejs.org/en/download/](https://nodejs.org/en/download/), with many Linux package manager installations documented at [https://github.com/nodejs/node-v0.x-archive/wiki/Installing-Node.js-via-package-manager](https://github.com/nodejs/node-v0.x-archive/wiki/Installing-Node.js-via-package-manager)

\

(Raspberry Pi users probably want to use the directions for
Debian/Ubuntu).

\

Once **node.js** has been successfully installed, install the package forever.  

\

**sudo npm install forever**

\

See: [http://blog.nodejitsu.com/keep-a-nodejs-server-up-with-forever/](http://blog.nodejitsu.com/keep-a-nodejs-server-up-with-forever/)



Installation {.western}
------------

1.  Download ircNodeDashboard.tgz (available in the Files section of the
    Yahoo! Group

2.  ircDDBGateway)

3.  Make a directory for the server, e.g. /opt/webserver

4.  Unpack ircNodeDashboard.tgz into the directory

5.  If ircNodeDashboard.tgz is in your home directory and the
    destination directory is /opt/webserver, the commands would be:\
    \
    **cd /opt/webserver\
    tar xzvf \~/ircNodeDashboard.tgz\
    **

6.  Install needed libraries\
    \
    **npm install**

    \
    (This will take some time, and there will be 'errors' for optional sub-components, you can ignore these warnings.)

7.  Make sure no other webserver is running on port 80 (e.g. Apache)

8.  Start up a test run in a terminal window
    \
    **node webserver.js**
    \
9.  Open a web browser and see if you see the webpage, if so then kill (Control-C) the program

Running ircNodeDashboard {.western}
------------------------

In a terminal run

\

**sudo nohup forever webserver.js \> webserver.log &**

\

Note: Some distributions may install node as nodejs, if the node or forever commands fail, you may need to navigate to the directory where nodejs is installed and create a soft link from node.

\

**ln -s nodejs node**

\

You may want to create a script to start and stop the webserver and have it automatically restart on reboot.

\

[1](#sdfootnote1anc)Windows may be problematic due to configuration being held in the registry, though one could extract the registry data into a ircDDBGateway text configuration file or an industrious developer could modify **webserver.js** to populate the config object directly from the registry using a library like [https://www.npmjs.com/package/winreg](https://www.npmjs.com/package/winreg) - The author is not a fan of Windows for server applications, so he has not undertaken any work in this area.