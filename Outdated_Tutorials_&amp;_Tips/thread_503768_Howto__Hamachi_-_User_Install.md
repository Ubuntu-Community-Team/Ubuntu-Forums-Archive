---
title: "Howto:  Hamachi - User Install"
date: 2007-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-07-18
I created this for the [Hamachi Forums]("http://forums.hamachi.cc/viewtopic.php?t=15075").  Also I would like to thank [KingOfNowhere]("http://ubuntuforums.org/member.php?u=57747") for his earlier post on installing [hamachi.]("http://ubuntuforums.org/showthread.php?t=135036")



I'm not sure if this will help but I like to install hamachi to specific users.  This is how I always get it working:

```
$ sudo modprobe tun
```
```
$ sudo gedit /etc/modules
```
[SIZE="3"][COLOR="Red"]add[/COLOR]** tun**[/SIZE].
save and close.

Now run the following:
```
$ ls /dev/net/tun
```
You should get "[COLOR="Red"]/dev/net/tun[/COLOR]"
If you don't then do the following:
```
$ sudo mkdir /dev/net
```
```
$ sudo mknod /dev/net/tun c 10 200
```
Download the newest hamachi version from [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/) or
```
$ wget wget http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz
```
Extract hamachi
```
$ tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
```
Move into hamachi directory
```
$ cd hamachi-0.9.9.9-20-lnx/
```
Install hamachi
```
$ sudo make install
```
Start tuncfg
```
$ sudo tuncfg
```
Create hamachi group
```
$ sudo groupadd hamachi
```
Add myself to the hamachi group
```
$ sudo gpasswd -a handband2 hamachi
```
Add root to the hamachi group
```
$ sudo gpasswd -a root hamachi
```
Change file permissions for tuncfg.sock
```
$ sudo chmod 760 /var/run/tuncfg.sock
```
Change the group for tuncfg.sock
```
$ sudo chgrp hamachi /var/run/tuncfg.sock 
```
Create RSA keypair
```
$ hamachi-init
```
Start hamachi
```
$ sudo hamachi start
```
Create hamachi account name
```
$ sudo hamachi set-nick handband2
```
Login to hamachi network
```
$ sudo hamachi login
```
Join a network
```
$ sudo hamachi join HANDBAND2
```
or Create a network
```
$ sudo hamachi create HANDBAND2
```

Now I add ghamachi:
Download it from here: [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)
or
```
$ wget -L http://purebasic.myftp.org/?filename=files/3/projects/hamachi/v.0.8.1/gHamachi_0.8.1.tar.gz
```
Rename the downloaded file
```
$ mv index.html\?filename\=files%2F3%2Fprojects%2Fhamachi%2Fv.0.8.1%2FgHamachi_0.8.1.tar.gz gHamachi_0.8.1.tar.gz
```
Extract the files
```
$ tar -zxvf gHamachi_0.8.1.tar.gz
```
Move ghamachi to the /usr/bin/
```
$ sudo mv ghamachi /usr/bin/
```
Make ghamachi executable
```
$ sudo chmod +x /usr/bin/ghamachi
```
Download ghamchi icon
```
$ wget http://wonsheimlan.wo.funpic.de/hamachi.png
```
Move icon to /usr/share/pixmaps/ folder
```
$ sudo mv hamachi.png /usr/share/pixmaps/
```
Add hamachi as an application
```
$ sudo gedit /usr/share/applications/hamachi.desktop
```
Add the following
```
[Desktop Entry]
Encoding=UTF-8
Name=Hamachi
Exec=ghamachi %u
Icon=/usr/share/pixmaps/hamachi.png
Type=Application
Categories=Application;Network;
MimeType=text/rss;text/xml;text/php;application/rss+xml
Comment=Instant VPN software
```

**After this I restart**.  Now when you click on hamachi, ghamachi should ask for password (which I like for security).  Don't forget to right click on your network to : "go-online"

A great program to use with hamachi:  [http://gnome-rdp.linuxforge.hu/](http://gnome-rdp.linuxforge.hu/)
```
$ sudo apt-get install gnome-rdp
```

I hope this can help.

---

### Post by llnk on 2007-11-23
Thanks for the tutorial. I am running into a problem though. After rebooting i tried launching Hamachi from applications/internet. It prompts for the sudo password then loads the icon in the system tray. When i hit the power button on the UI it attempts to logon to Hamachi but it always fails. Does anyone know what the problem is?

Thanks

---

### Post by Blind Tiger on 2007-11-23
I followed this guide (from the Hamachi forums) also.  Now when I try to launch Hamachi from the Gnome menu, I get the message "Hamachi could not be started."  From the command line, I have already created a nickname, joined a network that I created a while back while using XP, and I can start and login to hamachi using the command line.  Also, when I login to my.hamachi.cc, my linux box nick is listed as a member, but not online.  When I try to go-online from the command line, I get the response that I am not a member of the network???  Any pointers?  Is it an iptables issue?

---

### Post by accog on 2007-11-29
I am having the same problem. When i try to login into hamachi via the power button I cant. Any got any ideas?

---

### Post by sean... on 2008-04-26
I realize this topic is a bit old, but anyway...

Hamachi works fine for me if I just start it via the terminal with
```
sudo ghamachi
```
Other than that, it works great!  Also, you don't need to restart your whole computer, just restart your X session with Ctrl-Alt-Backspace to finish setting up ghamachi.

---

### Post by handband2 on 2008-04-27
sean...,

Thanks for the feedback.  

If you need to ever install hamachi again I've written a script to do the installation.  It is at the hamachi forums:  [https://forums.hamachi.cc/viewtopic.php?t=16590](https://forums.hamachi.cc/viewtopic.php?t=16590)

---

### Post by jspraggett on 2009-07-11
Hi. I want to setup a remote pc in the US as a proxy using Hamachi so that my IP will appear to be a US IP. Do you know how to do this?

Jim

---

### Post by TomasFitz on 2011-06-24
I get to a problem at the line:

```
sudo chmod 760 /var/run/tuncfg.sock
```

I get the message: chmod: cannot access `/var/run/tuncfg.sock': No such file or directory

Everything goes fine up to here. Anyway around this?

---

### Post by geazzy on 2011-06-25
great threads :)

---

