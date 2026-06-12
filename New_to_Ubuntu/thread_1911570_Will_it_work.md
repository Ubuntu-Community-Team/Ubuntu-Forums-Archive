---
title: "Will it work?"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by khalid1997 on 2012-01-19
Hi,
I recently installed Linux ubuntu to my pc by fromatting my Windows XP, as many people saying Linux OS('s) are much faster and better for servers, however,i downloaded it from this official ubuntu site : [http://www.ubuntu.com/download/......]("http://www.ubuntu.com/download/ubuntu/download")

Then i installed ubuntu from a USB drive (8GB), after finishing all installation progress's, i rebooted the pc, but ubuntu won't show the desktop as it's supposed to be, it only shows something like a Dos asking for log in information, in  the top it's called tty1, i googled a lot, trying to know whats the problem, some people were saying it's the compiz, some saying remove that and install this, but none of them work, but i found a site saying install ubuntu GUI, i entered it says that i do something like this in the tty1,
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

But i'm still installing it, but WILL IT WORK?

---

### Post by Grenage on 2012-01-19
If you installed the Ubuntu server edition - you wouldn't get a GUI; most people wouldn't use it.

As for installing ubuntu-desktop, yes, it should work.

---

### Post by anewguy on 2012-01-19
That window is the terminal window - what some call the command line.  To help us (I think you just need either the driver for or a parameter entered for your video adapter), please post back the output of the following:

lspci | grep VGA

That will tell us the adapter type and the chipset so we can go from there.

EDIT:  Didn't notice until I saw Grenage's reply -> did you install the server version or the regular "desktop" version?

Dave ;)

---

### Post by khalid1997 on 2012-01-19
First of all, thanks for the replies i really appreciate it.

> **anewguy said:**
> 

EDIT:  Didn't notice until I saw Grenage's reply -> did you install the server version or the regular "desktop" version?

Dave ;)

I really don't know which version i installed :confused:, but in the Unetbootin menu in the startup (as i said i installed from a USB drive) i chose the one called install, i only did that, but anyway it worked :D the desktop appeared. However, there was a second option in the boot menu that says 'Install ubuntu server'
but i didn't choose it. 

 Also just one last question, how can i copy the output of this```

lspci | grep VGA
``` ?
In the terminal it showed like this ( sorry for the mistakes i had to copy this by hand )
```

00:02.0  VGA compatible controller : Intel corporation 82865G Integrated Graphics Controller (rev 02)

```Also if theres a command to check the sound driver\adapter name please post it as i forgot to back up my drivers :(.

And how to run any familiar applications, like I'm a gamer, i want to run Counter-Strike(it's an .exe file) or another program that i might need ( like utorrent which i tried to download it from the official site, but no success ), but i can't as it shows a new windows saying failed to execute ( i forgot to mention that the necessary files are located in another partition ) .

There is a picture in the attachments for the 'failed to execute' thing, it showed when i tried to run the utorrent installation file ( it's down in the picture ).

Excuse me  for my long reply :).

---

### Post by anewguy on 2012-01-19
Your screen capture is already showing a gui'd desktop, so I don't understand what you are asking.

---

### Post by mastablasta on 2012-01-19
.exe files are windows files. you can install some of them using WINE. don't coun't on latest Windows games to just work in Linux. It's a totally different operating system (for startesr it doesn't have DirectX as this is a Microsoft only product). though Counter strike should work ok in wine.

you need to install wine first and then install the game within wine. you can also use Play on linux which gives some presets (it's an easy to configure wine) for most played games. to see what and how it run you can check this site: [http://appdb.winehq.org/](http://appdb.winehq.org/)

utorrent has a linux verison that is still under development and alpha stage ([http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)), but you might be better off trying some other alternatives such as the defaultly installed transmission, deluge and ktorrent (both of the latter are kind of like utorrent i think). deluge is also light on resources.

And like i said Linux is not free of charge Windows. It is another operating system based on community and opensource software. it has only limited A-class commercial software available. Games in particular are lacking support from their makers.

---

