---
title: "HOWTO: FreeNX over Authenticated Web Proxy Server"
date: 2005-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by NoogiE on 2005-09-14
I'd been wondering how to do this for quite some time, then finally, I found transconnect!

You can read the full document here - [http://noogies.org/index.php?option=com_content&task=view&id=14&Itemid=1](http://noogies.org/index.php?option=com_content&task=view&id=14&Itemid=1)

or below (Though please click on some of the google advertisements to help me pay for hosting if you found this a useful document!).

1. Download and install transconnect

Transconnect is hosted on sourceforge - download it here [http://sourceforge.net/project/showfiles.php?group_id=21209](http://sourceforge.net/project/showfiles.php?group_id=21209)

Extract and install

>tar zxvf transconnect-1.2.tar.gz

>cd transconnect-1.2

>make

cc -Wall  -shared -ldl -o tconn.so tconn.c

>make install


This will create ~/.tconn and copy the library file there.

2. Configure transconnect

> vi ~/.tconn/tconn.conf


Enter the IP, port, your username and password in to the relevant sections of this file. Pay attention to the warnings in this file (such as double quoting your username and password etc).


3. Install FreeNX on the client machine

A quick search of the Ubuntu forums will show you how to do this. I used the packages from [http://ubuntulinux.nl/](http://ubuntulinux.nl/).
In short, add this to your /etc/apt/sources.list file, apt-get update and then apt-get install.

>sudo echo "deb [http://ubuntulinux.nl/](http://ubuntulinux.nl/) /" >>/etc/apt/sources.list

>sudo apt-get update

>sudo apt-get install freenx


4. Setup /etc/resolv.conf

You will need to use a resolver that can resolve names on both your local and remote network, otherwise you will have to use IP's. See the transconnect documentation for more information.

5. Run FreeNX, using the tconn library

>export LD_PRELOAD=$HOME/.tconn/tconn.so

>/usr/NX/bin/nxclient


6. Configure FreeNX

When the FreeNX gui appears, click on the Configure button. On the general tab, first setup the host you wish to connect to. Enter the hostname of the FreeNX server, and setup the Port that A) Your proxy server will ALLOW you to connect to, and B) ssh on the client machine is configured to listen on. You may need to edit /etc/ssh/sshd_config  (on debian/ubuntu) on the FreeNX server to listen on a new port. Most proxies will at least allow 80 (http) and 443 (https), and most will also allow 21 (ftp). If anyone knows any easy way to find out all of the ports that a proxy server will allow I'd like to know....
Also, select the desktop you wish to use, speed of your connection to the FreeNX server, and the size of the display you wish to use.

Under the Advanced tab, YOU MUST "Enable SSL encryption of all traffic", otherwise it will not work. If you do not enable this, you will need to forward ports (port 5000 + the ID of your NX session, as far as I know), similar to the way a normal X session works. When you do enable encryption, all traffic will be tunneled over the single port that we are connecting over.

You might also want to up your memory cache here if you have plenty of RAM. Setup any other services and your environment if the defaults wont do.

7. Install FreeNX on the server

>sudo echo "deb [http://ubuntulinux.nl/](http://ubuntulinux.nl/) /" >>/etc/apt/sources.list

>sudo apt-get update

>sudo apt-get install freenx


8. Cross your fingers and try to connect!

Good luck!

Your mileage may vary, but feel free to email me if you think I need to change this document in any way.

---

### Post by dragonfyre13 on 2006-04-07
Make sure to change the permissions of the ~/.tconn/tconn.so file so that it can be accessed by the preload. I just chmodded the whole directory to 777, but again, YMMV.

---

