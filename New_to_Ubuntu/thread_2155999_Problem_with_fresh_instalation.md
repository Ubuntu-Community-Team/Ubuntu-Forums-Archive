---
title: "Problem with fresh instalation"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by comi94pfc on 2013-06-20
Hello guys, I just registered today on this forum because I need some help. I've been running Ubuntu 13.04 for some time here on my desktop, and I got this old computer from my friend and because it's like 10 years old I wanted to instal ubuntu on it so it will run faster than windows for exp. I tryed instaling it like I did on my computer but something went wrong, when I start up the computer it loads up to the desktop but i cant see the top notification bar or the side launcher! I don't know what to do, somehow it can enter thunderbird and mozila trough my keyboard shortcuts but I cant exit them because I cant see the window bar at the top of the window where the exit, minimise and fullscreen buttons are. I think I can't even switch to Windows now... It doesn't boot my CD :( Please help me guys!

---

### Post by newb85 on 2013-06-20
That 10-year-old machine is probably not powerful enough to run Unit, the default Desktop Environment for Ubuntu. Please give some of your system details. RAM, processor, graphics card, etc.

---

### Post by nerdtron on 2013-06-20
Try Lubuntu on that computer instead. And you mention that it doesn't boot you CD? Try your CD on your computer first just to make sure it is burned correctly.

---

### Post by comi94pfc on 2013-06-20
RAM: 994.3MiB
Processor: Intel Celeron (R) CPU 2.66HGz
Graphics: Intel 865G x86/MMX/SSE2
OS: 32 bit
DISK: 38.2GB

Nerdtron, I used that CD to install the OS on the computer, so it booted well when I was instaling it, now something is messed up.. Windows XP CD won't boot ether

EDIT:
I also got these errors, I don't know if it helps:
1) ExecutablePath
    /usr/bin/compiz
    package
    compiz-core 1:0.9.9-daily 13.03.29- 0ubuntu1
2) ExecutablePath
    /usr/bin/nautilus
    package
    nautilus 1:3.6.3-ubuntu13
    crashed with SIGABRT

---

### Post by sudodus on 2013-06-20
I would definitely recommend a lighter desktop environment than Unity, which is the standard for Ubuntu. Lubuntu as already recommended by *nerdtron* will probably be good.

But if you have problems with your CD/DVD drive, you need not download, burn and install another full system. Instead you can install the desktop environment like this

```
 sudo apt-get install lubuntu-desktop
```

and select Lubuntu at the log in screen. Later on you can uninstall Unity according to this link

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

unless you want to keep it or keep some parts of it.

Another option is to install from a USB pendrive. See for example this link 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by comi94pfc on 2013-06-20
> **sudodus said:**
> I would definitely recommend a lighter desktop environment than Unity, which is the standard for Ubuntu. Lubuntu as already recommended by *nerdtron* will probably be good.

But if you have problems with your CD/DVD drive, you need not download, burn and install another full system. Instead you can install the desktop environment like this

```
 sudo apt-get install lubuntu-desktop
```

and select Lubuntu at the log in screen. Later on you can uninstall Unity according to this link

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

unless you want to keep it or keep some parts of it.

Another option is to install from a USB pendrive. See for example this link 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I've just installed lubuntu from terminal like you said, and nothing changed exept for the welcome screen now saying "lubuntu" and being all blue.

---

### Post by sudodus on 2013-06-20
Do you reach the log in screen, where to select user and enter password?

If you still have the Ubuntu log in screen, click on the circular icon near the password window to select session (Lubuntu or Ubuntu). If you have the Lubuntu log in screen, it is more evident, where to select session.

---

### Post by comi94pfc on 2013-06-20
Thanks sudodus, it worked, im now in lubuntu!:) But when I start the computer I get instant errors so when I skip them it's all working.. 
Now I just have a few more questions.. How can I make youtube videos play, I mean I can hear the sound but the video is bugged somehow.. Any ideas?

---

### Post by sudodus on 2013-06-20
Please describe the 'instant' errors you get!

Use ***Synaptic*** to activate repositories and install ***lubuntu-restricted-extras*** which contain support for multimedia. Maybe you also need to install ***flashplugin-installer***

---

### Post by comi94pfc on 2013-06-20
Ok, the erors stoped showing up after restarting my computer a few times.. Now only the flash player problems... Look at this, this is how it looks when i try to play a youtube video:
P.S. Please don't mind the video, it's the first thing that came up



[IMG]http://www.dodaj.rs/f/3K/10x/2q15XHUX/screenshot-from-2013-06-.png[/IMG]

---

### Post by sudodus on 2013-06-20
I know there are issues with that old Intel graphics in 13.04. I have similar issues in my son's old IBM Thinkcentre. The support for old Intel graphics works better with the version 12.04 LTS.

Unfortunately Lubuntu is not included in the long time support, but Xubuntu is (until April 2015), so an alternative is to ***try Xubuntu 12.04 LTS*** instead of Lubuntu 13.04. Xubuntu might be slightly slower, but it has advantages too.

You cannot fix that by installing a few new packages. You need to download the iso file and make either a CD or a USB drive. I think your computer is new enough to boot from USB (if you still have problems with the CD/DVD drive).

---

### Post by critin on 2013-06-20
My old computer won't run unity any 13. versions.  I can run 12.04/12.10 xubuntu just fine, and ubuntu (without unity)

---

### Post by comi94pfc on 2013-06-21
Thanks, downloading xubuntu 12.04 LTS as I post, i'll be back in a few if i have any problems instaling it or something like that..

---

### Post by comi94pfc on 2013-06-21
Downloaded, installed, everything works like a charm!!! Thanks sudodus for your time and help! The comuter is runing like a jet, so much faster than on windows.. Only one question left, is there a way to make my bottom panel show itself when i'm on desktop and automatically hide when i'm in web browser of something like that in fullscreen?

---

### Post by monkeybrain2012 on 2013-06-21
> **sudodus said:**
> I know there are issues with that old Intel graphics in 13.04. I have similar issues in my son's old IBM Thinkcentre. The support for old Intel graphics works better with the version 12.04 LTS.

Unfortunately Lubuntu is not included in the long time support, but Xubuntu is (until April 2015), so an alternative is to ***try Xubuntu 12.04 LTS*** instead of Lubuntu 13.04. Xubuntu might be slightly slower, but it has advantages too.

You cannot fix that by installing a few new packages. You need to download the iso file and make either a CD or a USB drive. I think your computer is new enough to boot from USB (if you still have problems with the CD/DVD drive).

Lubuntu is definitely lighter than xubuntu and probably the only thing with acceptable performance on that machine. I would not worry about it being a non LTS. Other than the lxde-desktop everythig is from Ubuntu 12.04 repo which means they will be supported for as long as ubuntu 12.04 and even with the lxde stuffs you can probably find a ppa for Ubuntu 12.04. I have installed lubuntu 12.04 on some old machines for some people. I am not going to upgrade them as it took me a while to get every thing to work. 

One can also try LXLE which is lubuntu 12.04 with extended long term support [http://www.lxle.net/](http://www.lxle.net/)

---

### Post by sudodus on 2013-06-22
> **comi94pfc said:**
> Downloaded, installed, everything works like a charm!!! Thanks sudodus for your time and help! The comuter is runing like a jet, so much faster than on windows.. Only one question left, is there a way to make my bottom panel show itself when i'm on desktop and automatically hide when i'm in web browser of something like that in fullscreen?

I'm glad it works well :-)

The bottom panel should pop up, when you move the cursor to the bottom edge of the screen, and auto-hide otherwise. I don't know if you can get the action you want. Let us hope someone else knows about it and tell us.

It may attract more Xubuntu users, if you make a new thread with the Xubuntu tag and ask a detailed question.

---

### Post by sudodus on 2013-06-22
> **monkeybrain2012 said:**
> Lubuntu is definitely lighter than xubuntu and probably the only thing with acceptable performance on that machine. I would not worry about it being a non LTS. Other than the lxde-desktop everythig is from Ubuntu 12.04 repo which means they will be supported for as long as ubuntu 12.04 and even with the lxde stuffs you can probably find a ppa for Ubuntu 12.04. I have installed lubuntu 12.04 on some old machines for some people. I am not going to upgrade them as it took me a while to get every thing to work. 

One can also try LXLE which is lubuntu 12.04 with extended long term support [http://www.lxle.net/](http://www.lxle.net/)

I avoid recommending to run software beyond the end of life. The security risk will increase. But I can agree that in this particular case, it will not increase much. But it is not only the LXDE stuff, there are also application program packages that are unique to Lubuntu.

I think LXLE is a good alternative, if the drivers in new Lubuntu versions cause problems, and Xubuntu has too large foot-print. LXLE is also nicely tweaked.

However, the OP of this thread seems happy with Xubuntu 12.04 LTS.

---

### Post by newb85 on 2013-06-22
> **sudodus said:**
> I avoid recommending to run software beyond the end of life. The security risk will increase. But I can agree that in this particular case, it will not increase much. But it is not only the LXDE stuff, there are also application program packages that are unique to Lubuntu.

I think LXLE is a good alternative, if the drivers in new Lubuntu versions cause problems, and Xubuntu has too large foot-print. LXLE is also nicely tweaked.

However, the OP of this thread seems happy with Xubuntu 12.04 LTS.

If you're going to run Lubuntu past EOL, you should make sure you're using a browser (and email client if you use one) that's still supported.

---

