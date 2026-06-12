---
title: "Howto: Ubuntu Gutsy Gibbon 7.10 - User Install"
date: 2007-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-12-13
Hamachi Install

This works on a clean install of Ubuntu 7.10. I have not tried it on a upgraded version of Gutsy.

First we need to install a few things
Code:
```
$ sudo aptitude install build-essential upx-ucl-beta
```

Configure tun module
Code:
```
$ sudo modprobe tun
```

Code:
```
$ sudo gedit /etc/modules
```

add **[SIZE="2"]tun[/SIZE]**.
save and close.
Code:
```
$ ls /dev/net/tun
```

You should get "/dev/net/tun"
If you don't then do the following:
Code:
```
$ sudo mkdir /dev/net
```

Code:
$ sudo mknod /dev/net/tun c 10 200

Download the newest hamachi version from [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/) or
Code:
```
$ wget [http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz](http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz)
```

Extract hamachi
Code:
```
$ tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
```

Move into hamachi directory
Code:
```
$ cd hamachi-0.9.9.9-20-lnx/
```

Install hamachi
Code:
```
$ sudo make install
```

Move to /usr/bin directory
Code:
```
$ cd /usr/bin
```

Unpack the hamachi binary with upx -d
Code:
```
$ sudo upx -d hamachi
```

Start tuncfg
Code:
```
$ sudo /sbin/tuncfg
```

Create hamachi group
Code:
```
$ sudo groupadd hamachi
```

Add myself to the hamachi group
Code:
```
$ sudo gpasswd -a handband2 hamachi
```

Add root to the hamachi group
Code:
```
$ sudo gpasswd -a root hamachi
```

Change file permissions for tuncfg.sock
Code:
```
$ sudo chmod 760 /var/run/tuncfg.sock
```

Change the group for tuncfg.sock
Code:
```
$ sudo chgrp hamachi /var/run/tuncfg.sock
```

Create RSA keypair
Code:
```
$ hamachi-init
```

Start hamachi
Code:
```
$ sudo hamachi start
```

Create hamachi account name
Code:
```
$ sudo hamachi set-nick handband2
```

Login to hamachi network
Code:
```
$ sudo hamachi login
```

Join a network
Code:
```
$ sudo hamachi join HANDBAND2
```

or Create a network
Code:
```
$ sudo hamachi create HANDBAND2
```


Choose from two hamachi gui's:
----------------------------------------------------------------------------------------------------------------
1st:
---------------

[IMG]http://www.penguinbyte.com/software/ghamachi/images/mainwindow.jpg[/IMG]

Download it from here: [http://www.penguinbyte.com/software/ghamachi/](http://www.penguinbyte.com/software/ghamachi/)
or
Code:
```
$ wget -O gHamachi_0.8.1.tar.gz 'http://purebasic.myftp.org/?filename=files/3/projects/hamachi/v.0.8.1/gHamachi_0.8.1.tar.gz'
```

Extract the files
Code:
```
$ tar -zxvf gHamachi_0.8.1.tar.gz
```

Move ghamachi to the /usr/bin/
Code:
```
$ sudo mv ghamachi /usr/bin/
```

Make ghamachi executable
Code:
```
$ sudo chmod +x /usr/bin/ghamachi
```

Download ghamchi icon
Code:
```
$ wget [http://wonsheimlan.wo.funpic.de/hamachi.png](http://wonsheimlan.wo.funpic.de/hamachi.png)
```

Move icon to /usr/share/pixmaps/ folder
Code:
```
$ sudo mv hamachi.png /usr/share/pixmaps/
```

Add hamachi as an application
Code:
```
$ sudo gedit /usr/share/applications/hamachi.desktop
```

Add the following
Code:
```
[Desktop Entry]
Encoding=UTF-8
Name=Hamachi
Exec=ghamachi %u
Icon=/usr/share/pixmaps/hamachi.png
Type=Application
Categories=Application;Network;
Comment=Instant VPN software

```

2nd:
---------------

[IMG]http://hamachi-gui.sourceforge.net/screenshots/sneakpeak-small.png[/IMG]

Go here to download the file: [https://forums.hamachi.cc/viewtopic.php?t=15682](https://forums.hamachi.cc/viewtopic.php?t=15682)
or (for gutsy i386)
Code:
```
$ wget http://superb-west.dl.sourceforge.net/sourceforge/hamachi-gui/hamachi-gui_0.9.0-0_i386-gutsy.deb
```

Double click on the hamachi-gui_0.9.0-0_i386-gutsy.deb file or
Code:
```
$ sudo dpkg -i hamachi-gui_0.9.0-0_i386-gutsy.deb
```



----------------------------------------------------------------------------------------------------------------

After this I restart. Now when you click on hamachi, ghamachi should ask for password (which I like for security). Don't forget to right click on your network to : "go-online"

A great program to use with hamachi: [http://gnome-rdp.linuxforge.hu/](http://gnome-rdp.linuxforge.hu/)
Code:
```
$ sudo apt-get install gnome-rdp
```


I hope this can help.

**[SIZE="3"]Edit:[/SIZE]** If you need to remove hamachi
[http://forums.hamachi.cc/viewtopic.php?t=5778](http://forums.hamachi.cc/viewtopic.php?t=5778)

**[SIZE="3"]Edit:[/SIZE]** Some people have had problems starting ghamachi and/or hamachi-gui. The problem comes from starting ghamachi and/or hamachi-gui as root (sudo). When ghamachi and/or hamachi-gui is used for the first time they create files in the **~/.hamachi** or **/home/$USER/.hamachi** folder. So if the program is started as sudo the files are created for the root user. Also if hamachi was started under sudo [**sudo hamachi start**] then the error will occur.

[COLOR="Red"]Error[/COLOR]: Hamachi will only run as sudo (root)
**Fix** - change owner permissions:
```
sudo chown -R $USER:$USER ~/.hamachi
```

**Fix** - hamachi running as sudo (root):
```
sudo hamachi stop
```

**[SIZE="3"]Edit:[/SIZE]**  I've recently created a script to install hamachi. 
The script is posted on the hamachi forums:  [https://forums.hamachi.cc/viewtopic.php?t=16590](https://forums.hamachi.cc/viewtopic.php?t=16590)

I'm a beginner creating scripts so if you have any issues or feedback please let me know!  Thanks!

---

### Post by crazycarlt on 2008-01-10
Thanks for the tutorial, it was the only way I could get Hamachi to work, sort of.
Unfortunately, neither of the GUIs seem to work.

GUI 1 simply says 'could not start hamachi' and closes. The second one flickers on the 'waiting' icon for the cursor and doesn't appear to do anything.

Also, if I start and use hamachi with the terminal, I cannot access any systems on teh network.

```

carl@hoenheim:~$ sudo hamachi list
   [thuringia]
       5.39.66.212                               
     * 5.45.47.44                                
       5.66.73.212                               
       5.70.73.44                                
carl@hoenheim:~$ sudo hamachi get-nicks
Retrieving peers' nicknames .. 
carl@hoenheim:~$ ping 5.45.47.44
PING 5.45.47.44 (5.45.47.44) 56(84) bytes of data.
From 5.32.27.101 icmp_seq=1 Destination Host Unreachable
From 5.32.27.101 icmp_seq=2 Destination Host Unreachable
From 5.32.27.101 icmp_seq=3 Destination Host Unreachable
From 5.32.27.101 icmp_seq=4 Destination Host Unreachable
From 5.32.27.101 icmp_seq=5 Destination Host Unreachable
From 5.32.27.101 icmp_seq=6 Destination Host Unreachable
From 5.32.27.101 icmp_seq=7 Destination Host Unreachable
From 5.32.27.101 icmp_seq=8 Destination Host Unreachable
From 5.32.27.101 icmp_seq=9 Destination Host Unreachable
From 5.32.27.101 icmp_seq=10 Destination Host Unreachable
From 5.32.27.101 icmp_seq=11 Destination Host Unreachable
From 5.32.27.101 icmp_seq=12 Destination Host Unreachable
From 5.32.27.101 icmp_seq=13 Destination Host Unreachable
From 5.32.27.101 icmp_seq=14 Destination Host Unreachable
From 5.32.27.101 icmp_seq=15 Destination Host Unreachable

--- 5.45.47.44 ping statistics ---
16 packets transmitted, 0 received, +15 errors, 100% packet loss, time 15040ms
, pipe 3

```

---

### Post by Mular on 2008-01-11
I am trying to get hamachi-gui to work right..

If I add it to the application menu like you said, it loads up but it just says connection.....

if I run it via terminal as gksudo hamachi-gui - just stays on connecting...
if I run it via terminal as sudo hamachi-gui it connects perfectly..

How can I make an application shortcut on my gnome menu bar that will get it to run right? sudo works but since you can't type in a password it doesn't always work.. and gksudo loads up and asks for password but its like it can't find my user information

---

### Post by KhanTG on 2008-01-23
I have tried to access the script that you created.. It doesn't seem to be on the server any more.  Can you please put it back up.  I have used it just a couple of weeks ago and am looking to use it on three more boxes.  thanks.

---

### Post by handband2 on 2008-01-23
**crazycarlt** & **Mular**,

There might be a permission problem in your **~/.hamachi** folder.  I've posted some answers to problems on the first post.

See if this will fix the problem you are having.

```
sudo chown -R $USER:$USER ~/.hamachi
```




**KhanTG**,

Sorry, about that.  I updated the file and didn't check if it uploaded correctly.

If anything happens to the file you can go where I've posted the code:  [**hamachi install**]("https://forums.hamachi.cc/viewtopic.php?p=59814#59814")

---

