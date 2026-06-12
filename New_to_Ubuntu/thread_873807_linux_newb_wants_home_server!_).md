---
title: "linux_newb wants home_server! :)"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by jcway212 on 2008-07-29
I am very new to linux, and just got together the parts for a home server...nothing fancy. 

Here is what I want to do:

Skype

File and Print Server

Server accessed via remote desktop through my XP machine. I want to be able to play around in my linux box from my XP machine. :)


I am trying to choose which distro to use, because I need some sort of GUI to do this, because I am so new. 



Anyways, I narrowed down my search to either:
Ubuntu Hardy
Linux Mint
OpenSUSE



Any suggestions?



Thanks,
Paul

---

### Post by forger on 2008-07-29
Ubuntu hardy, but since you like GUI, try the desktop first, and install your server stuff later

The ubuntu wiki and help sites can be really helpful:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[https://help.ubuntu.com/community/VMWare](https://help.ubuntu.com/community/VMWare)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
etc...

---

### Post by jcway212 on 2008-07-29
So you are saying install the desktop version first and use that as a server and install the apps, etc. The one thing I am going to do is make this linux server a headless unit and access it via remote desktop on my computer which is running XP. Any other suggestions?

---

### Post by halitech on 2008-07-29
if you are going headless, make sure you install some kind of remote control app while you have the monitor connected and make sure you can log in before you make it headless. Nothing as frustrating as getting it where you want only to find out you can't remote into it and have to dig it back out

---

### Post by jcway212 on 2008-07-29
> **halitech said:**
> if you are going headless, make sure you install some kind of remote control app while you have the monitor connected and make sure you can log in before you make it headless. Nothing as frustrating as getting it where you want only to find out you can't remote into it and have to dig it back out

Very true, what would you suggest be the best app for remote desktop? or should I use the one built into ubuntu or whichever distro I choose?

---

### Post by halitech on 2008-07-29
the only 2 I've used that work on Linux (still waiting for Logmein to come out with a version that works) is VNC and the built in Terminal server Client. I think I used VNC on the server I was using (been a while since I dumped the server) and used the TSC from my desk top. I've also used VNC to remote control my mothers system (she makes a lot of errors but don't tell her I said that ;) ) and it seems fine. Where it is going to be behind a router (I'm assuming), just plain VNC will do fine without using SSH to encrypt the connection.

---

### Post by jcway212 on 2008-07-29
awesome, thanks Halitech, question for you.....would you do Ubuntu over Mint or SUSE?

---

### Post by youthforlinux on 2008-07-29
I wouldn't use Mint for a server....

---

### Post by cariboo on 2008-07-29
I would install the server version of hardy and do all the administration via ssh and a web based server admin suite like webmin. That way you don't have to worry about sound and video if your video and sound cards are not well supported. Have a look at webmin here:

[http://www.webmin.com/](http://www.webmin.com/)

There is a webmin howto here:

[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

I don't think you're going to be able to run a skype server, as that is proprietary software.

Jim

---

### Post by tuxxy on 2008-07-29
Dont waste you time with Mint

---

### Post by Sef on 2008-07-29
> I don't think you're going to be able to run a skype server, as that is proprietary software.

Check out OpenWengo, which is open-source.  It is in the repositories.

---

### Post by jcway212 on 2008-07-29
> **cariboo907 said:**
> 

I don't think you're going to be able to run a skype server, as that is proprietary software.

Jim

Let me rephrase, its not exaclty a skype server, i will run skype off my server 24/7 with a USB adapter for my phone so that my home phone will be on will skype all the time, does that make sense?

---

### Post by Efros on 2008-07-29
Be aware that if you are running headless that when you reboot, with your monitor switched off or no monitor attached the resolution will got to 640x 480. Which really kinda sucks. Inbuilt remote desktop server is pretty good in ubuntu, I use it connecting from XP and OS X machines.

---

### Post by jcway212 on 2008-07-29
> **Efros said:**
> Be aware that if you are running headless that when you reboot, with your monitor switched off or no monitor attached the resolution will got to 640x 480. Which really kinda sucks. Inbuilt remote desktop server is pretty good in ubuntu, I use it connecting from XP and OS X machines.

O, wow, I didn't knnow that, thanks for the info!

---

### Post by halitech on 2008-07-29
I've never used Mint or Suse so I can't really say. I was using Ubuntu 6.06 when I was running the server and it was rock solid so I would have to give a biased opinion of Ubuntu.

---

### Post by jcway212 on 2008-07-30
> **halitech said:**
> I've never used Mint or Suse so I can't really say. I was using Ubuntu 6.06 when I was running the server and it was rock solid so I would have to give a biased opinion of Ubuntu.

Thats fine, thanks, It seems like Ubuntu will be the OS of choice. Now should I do the server version or the desktop version? The reason I am asking is because I would gather do as much configuring and playing around with Ubuntu in X or GUI and not the command line, I am still trying to get used to linux and am just not comfortable with that idea.

This maybe a stupid question, but will the server version run X?

Couple that question with this one....

I am interested in installing WINE and running this as my linux box as well as a server....So I just might, for testing purposes, install STEAM via WINE, so I can pwn a few noobs in linux on CS:S.

---

### Post by halitech on 2008-07-30
the server is the desktop version minus the gui so yes it will run either way. I would recommend doing the dektop install and then adding your server programs that you want to install.

word of warning, if you come back here asking for help, most times you will get instructions for the command line simply because it is easier then trying to figure out which GUI you have installed and trying to tell you what tab or button to click on to resolve issues. That doesn't mean you need to become best buddies with the command line, just be prepared to copy and paste things in if you ask for help

---

### Post by Gourgi on 2008-07-30
have a look at this
[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)
i think it is a good start

---

### Post by maybeway36 on 2008-07-30
> **Efros said:**
> Be aware that if you are running headless that when you reboot, with your monitor switched off or no monitor attached the resolution will got to 640x 480. Which really kinda sucks. Inbuilt remote desktop server is pretty good in ubuntu, I use it connecting from XP and OS X machines.

I use a custom xorg.conf (generated on an old version of Ubuntu) so this doesn't happen.

---

### Post by Efros on 2008-07-30
Wanna share how you do this, I've tried to force resolution but I just cant seem to get it to work.

Also to previous poster, just installed webmin and its really nice.

---

### Post by jcway212 on 2008-07-30
> **halitech said:**
> the server is the desktop version minus the gui so yes it will run either way. I would recommend doing the dektop install and then adding your server programs that you want to install.

word of warning, if you come back here asking for help, most times you will get instructions for the command line simply because it is easier then trying to figure out which GUI you have installed and trying to tell you what tab or button to click on to resolve issues. That doesn't mean you need to become best buddies with the command line, just be prepared to copy and paste things in if you ask for help


Awesome! Great response, thanks! That makes sense, I am not against using the command line at all, I just want the functionality of the GUI to use while learning the command line. I am very much looking forward to learning all of that....im just a noob now :)

---

### Post by halitech on 2008-07-30
we all started out at the same place, some just pick up on it faster then others :)

good luck and hopefully we'll see you posting help for others soon :D

---

### Post by forger on 2008-07-31
> **halitech said:**
> the server is the desktop version minus the gui so yes it will run either way. I would recommend doing the dektop install and then adding your server programs that you want to install.

..hence we're back to my initial reply :P

---

### Post by jcway212 on 2008-07-31
> **forger said:**
> ..hence we're back to my initial reply :P

You are correct sir....lol.... go, go, gadget, THANKS! :lolflag:

---

