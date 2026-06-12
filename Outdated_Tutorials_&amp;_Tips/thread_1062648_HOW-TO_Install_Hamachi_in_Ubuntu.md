---
title: "HOW-TO: Install Hamachi in Ubuntu"
date: 2009-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by curtlee2002 on 2009-02-07
NOTE: Most of this post was taken from [http://ubuntuforums.org/showthread.php?t=135036]("http://ubuntuforums.org/showthread.php?t=135036").  I made it a striped down Hamachi install only. I also added information to use upx-ucl to decompress hamachi's executable so it can be ran on the newer ubuntu releases that require hamachi to be decompressed. A few other tweaks have been added. Thanks to [KingOfNowhere]("http://ubuntuforums.org/member.php?u=57747") for all his hard work.



**Hamachi**

1.A) The 'tun' Module

The very first part of the Hamachi installation is to enable IP Tunnelling support in your kernel. This can be done like this:
```
sudo modprobe tun
```
then open your /etc/modules file and add tun to the list of modules:
```
 sudo gedit /etc/modules
``` 

If you are using a standard Ubuntu kernel, this should be all you need to do. However, if you compiled your own kernel, you made need to recompile it with IP Tunnelling support (only if you recieve an erro with 'modprobe'). If anyone needs help installing the module, see [HOWTO: Hamachi Linux Guide (2.4.x and 2.6.x)]("http://forums.hamachi.cc/viewtopic.php?t=3523") By Kamel

1.B) Installing Hamachi

Okay, now on to the actual Hamachi software. But first, we need to make sure that a valid tunnelling node has been created in /dev. This is done like this:
```
ls /dev/net/tun 
```

If you get a "No Such File or Directory" error, you need to create a new node like this:
```
sudo mkdir /dev/net
sudo mknod /dev/net/tun c 10 200
```

Okay, now that we have a valid IP Tunnel node, time to install Hamachi. 

Download the latest version of Hamachi from [http://files.hamachi.cc/linux/]("http://files.hamachi.cc/linux/").

Enter the directory where you downloaded it and here is how to install it:
```

#Extract the archive
tar -zxvf hamachi-0.9.9.9-*.tar.gz
cd hamachi-0.9.9.9-*/

#install Hamachi
sudo make install

#decompress hamachi's executable
sudo apt-get install upx-ucl
sudo upx-ucl -d /usr/bin/hamachi

#start tuncfg
sudo tuncfg


#Hamachi is installed
```

1.C) Setting User Permissions

For security sake, we are going to set the permissions of Hamachi so that it can only be started by members of the 'hamachi' group. This is done like so:
```

#Create the 'hamachi' group
sudo groupadd hamachi

#Add your user to the group
sudo gpasswd -a $USER hamachi

#Add root to the group
sudo gpasswd -a root hamachi

#Set socket permissions
sudo chmod 760 /var/run/tuncfg.sock

#Finally, changing the group of the file
sudo chgrp hamachi /var/run/tuncfg.sock
```

Now that permissions are done, on to configuration.

1.D) Hamachi Configuration - System Service

Follow this section if you want Hamachi to run as a system service (in the background). I chose to list this method of configuration first because it seemed most relivant to the guide. If you want to have Hamachi run as a user application and install the gtk frontend, skip to section '1.E'. 

1.D.1) Base Configuration

Creating an initial configuration can be done like so:
```

sudo hamachi-init -c /etc/hamachi
```

the result should be something like this:
```

Initializing Hamachi configuration (/etc/hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making /etc/hamachi directory .. ok
  saving /etc/hamachi/client.pub .. ok
  saving /etc/hamachi/client.pri .. ok
  saving /etc/hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

```

Okay, next is to start Hamachi:
```

sudo hamachi -c /etc/hamachi start
```

Now that we are up and running, you need to set your nickname:
```

sudo hamachi -c /etc/hamachi set-nick "YourNickHere"
```

Next, we need to login to Hamachi and then either login to an existing network or create a new one. Like this:
```

#Login to Hamachi
sudo hamachi -c /etc/hamachi login

#To join an existing network
sudo hamachi -c /etc/hamachi join network password

#Or to create a new network
sudo hamachi -c /etc/hamachi create network password

#Lastly, to go online to the network you joined
sudo hamachi -c /etc/hamachi go-online network

```

*NOTE ABOUT NETWORK PASSWORDS*
I would recommend visiting [http://grc.com/passwords]("http://grc.com/passwords") for a random string password. They are very strong passwords and adds to the security of your setup.

Now your machine is up and running on it's own Hamachi VPN. The last part of the installation is a script written by Kamel that will allow Hamachi to run on startup.

1.D.2) Hamachi Startup Script

Open gedit and save the following as /etc/init.d/hamachi
```

#!/bin/sh

hamachi_start() {
  echo "Starting hamachi..."
  /sbin/tuncfg
  /usr/bin/hamachi -c /etc/hamachi start
  /bin/chmod 760 /var/run/tuncfg.sock
  /bin/chgrp hamachi /var/run/tuncfg.sock
  /bin/chmod 770 -R /etc/hamachi
  /bin/chgrp hamachi -R /etc/hamachi
}

hamachi_stop() {
  echo "Stopping hamachi..."
  killall tuncfg
  /usr/bin/hamachi -c /etc/hamachi stop
}

hamachi_restart() {
  hamachi_stop
  sleep 1
  hamachi_start
}

case "$1" in
'start')
  hamachi_start
  ;;
'stop')
  hamachi_stop
  ;;
'restart')
  hamachi_restart
  ;;
*)
  hamachi_start
esac

```

Lastly, you need to make the script executable and add it to startup:
```

sudo chmod +x /etc/init.d/hamachi
sudo update-rc.d hamachi defaults
```

1.E) Hamachi Configuration - User Application

Follow this section if you want Hamachi to run as a user application and to use the pretty gtk frontend. If you want to have Hamachi run as a system service in the background, go back to section '1.D'. 

1.E.1) Base Configuration

Creating an initial configuration can be done like so:
```

hamachi-init 
```

the result should be something like this:
```

Initializing Hamachi configuration (/home/user/.hamachi). Please wait ..

  generating 2048-bit RSA keypair .. ok
  making (/home/user/.hamachi directory .. ok
  saving (/home/user/.hamachi/client.pub .. ok
  saving (/home/user/.hamachi/client.pri .. ok
  saving (/home/user/.hamachi/state .. ok

Authentication information has been created. Hamachi can now be started with
'hamachi start' command and then brought online with 'hamachi login'.

```

Okay, next is to start Hamachi:
```

hamachi start
```

Now that we are up and running, you need to set your nickname:
```

hamachi set-nick "YourNickHere"
```

Next, we need to login to Hamachi and then either login to an existing network or create a new one. Like this:
```

#Login to Hamachi
hamachi login

#To join an existing network
hamachi join network password

#Or to create a new network
hamachi create network password

#Lastly, to go online to the network you joined
hamachi go-online network

```

*NOTE ABOUT NETWORK PASSWORDS*
I would recommend visiting [http://grc.com/passwords]("http://grc.com/passwords") for a random string password. They are very strong passwords and adds to the security of your setup.

Now your machine is up and running on it's own Hamachi VPN. The last part of the installation is to install the GUI for Hamachi. Here is how that is done.

1.E.2) Hamachi GUI (gHamachi) Installation

First, visit the Hamachi forums and download the most recent version of the gHamachi frontend for either gtk 2.0 or gtk 1.2 (whichever you prefer).

[gHamachi can be found here.]("http://forums.hamachi.cc/viewtopic.php?t=2488")

Second, simply unpack the gHamachi tarball, copy the binary to /usr/bin, and give it permission to run (chmod +x).

```

tar xfz gHamachi_gtk2.tar.gz
sudo mv ghamachi /usr/bin/
sudo chmod +x /usr/bin/ghamachi
```

Once that is done, the Hamachi GUI is completely installed.

Start the GUI like this:
```
ghamachi
```

Hamachi is all set up now, now on to VNC.

Please post any comments or corrections you my have.

---

