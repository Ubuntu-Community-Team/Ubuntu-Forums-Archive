---
title: "No Desktop Effects : ("
date: 2008-10-20
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-20
So I finally decided to take the plunge into Linux after seeing a few Compiz videos on Youtube :D

The only trouble is, that I can't enable desktop effects under "Appearances." My first guess was that I needed to install Linux-friendly drivers for my graphics card (Radeon HD 4850). I checked "Hardware Drivers" and it said that there were no proprietary drivers installed. So, is there any special way to get/install the drivers (read something about Synaptics Manager a while ago) or do I just go straight to ATI's driver page and download and install the drivers from there. I'm also wondering if there's a way that Ubuntu can automatically downloads drivers for my hardware because I noticed that I didn't have to install a driver for my desktop's wifi card.

Hope to hear back from you guys soon. In the meantime, I'm going to go play around with everything else Ubuntu has to offer!

---

### Post by eternalnewbee on 2008-10-20
Hi there, and welcome to Ubuntu.
Do you know what kind of graphic card you've got?

---

### Post by eternalnewbee on 2008-10-20
Hi there, and welcome to Ubuntu.
Do you know what kind of graphic card you've got?

---

### Post by Victormd on 2008-10-20
Assuming that you're using Ubuntu 8.04, open synaptic package manager and search for envyng-gtk then mark for installation (it will tell you that it needs envyng-core, that's Ok)
Once installed, go to applications>tools and run the program Envy-NG, select ATI and it will automatically choose the best driver to install and install it for you...

---

### Post by psyoptic on 2008-10-20
Hey there, eternalnewbee!

My graphics card is a Radeon HD 4850.

Edit: It is 8.04. I installed it through WUBI (not sure if that makes a difference). Thanks for the tip, I'll see if that works.

---

### Post by eternalnewbee on 2008-10-20
Edit. OK you've got ATI.
Go to Main Menu > System > Administration > Hardware Drivers and enable it.

---

### Post by Victormd on 2008-10-20
Sorry, one more thing. Once the driver is installed, you'll need to install the compiz manager. To do this, either look for compizconfig-settings-manager in synaptic or you can open a terminal and type
```
sudo apt-get install compizconfig-settings-manager
```
This will allow you to configure the desktop effects settings...

---

### Post by psyoptic on 2008-10-20
Where can I find Synaptic Package Manager?

---

### Post by Victormd on 2008-10-20
> **psyoptic said:**
> Edit: It is 8.04. I installed it through WUBI (not sure if that makes a difference)

That shouldn't be a problem... :)

---

### Post by Victormd on 2008-10-20
> **psyoptic said:**
> Where can I find Synaptic Package Manager?

it's under SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER

Edit: Sorry again... :)

Another thing you'll have to do before this is go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and under the UPDATES tab, mark all the **Ubuntu updates** (i.e., important security..., recommended..., pre-release..., unsupported...). I don't think you'll find envyng in synaptics unless you do this.

---

### Post by Victormd on 2008-10-20
Another thing to keep in mind is that you should have all the updates prior to doing this. To check if your system is up-to-date:
1. Go to SYSTEM>ADMINISTRATION>UPDATE MANAGER and check and install any updates, or
2. Open a terminal and type:
```
sudo apt-get update
```
(this will update your software sources)
```
sudo apt-get upgrade
```
(this will install any available updates)

---

### Post by eternalnewbee on 2008-10-20
OK. Follow Victor's advice.
One more thing. Once you've installed compiz, you should go to Main Menu > System > Preferences > Appearance > Visual Effects and tick one of the boxes, except none, of course.
Do let us know about your progress.
Good luck.

---

### Post by psyoptic on 2008-10-20
I found envyng in synaptics before that, thanks anyways. Should all those boxes be checked off in  "Updates" anyways? Important security updates seems like a good thing to have checked.

Btw, envyng didn't work. I'm going to try getting the drivers off of ATI's site. Do you know how to check if this Ubuntu installation is 32 bit or 64 bit?

---

### Post by Victormd on 2008-10-20
> **psyoptic said:**
> Should all those boxes be checked off in  "Updates" anyways? Important security updates seems like a good thing to have checked.

They should be checked on, by default 2 are selected and 2 are not (I think), you should select all of them.

---

### Post by psyoptic on 2008-10-20
Ok, I'll check them off then.

I'm about to download the drivers for my graphics card manually, but I'm not sure whether I have a 32 bit or 64 bit OS. Do you know how I can check it?

---

### Post by eternalnewbee on 2008-10-20
There is a system tool you can install from Add/ Remove Applications called Sysinfo. This is how it looks like: This will give you detailed information about your system.[ATTACH]89060[/ATTACH]

---

### Post by Victormd on 2008-10-20
> **psyoptic said:**
> Ok, I'll check them off then.

Now I'm confused... hehehe... they should be marked/selected to be used as update sources...

---

### Post by Victormd on 2008-10-20
> **psyoptic said:**
> Ok, I'll check them off then.

I'm about to download the drivers for my graphics card manually, but I'm not sure whether I have a 32 bit or 64 bit OS. Do you know how I can check it?

If you downloaded the i386 version of the live CD, then it's 32 bits, otherwise it's 64 bits... :)

BTW, hardy is still a bit sticky with newer graphics cards. You might want to try downloading Intrepid Beta as the hardware support is far superior. Just keep in mind that it's still a Beta release.

---

### Post by psyoptic on 2008-10-20
Thanks for the sysinfo tip, eternal. That did the trick. 

@Victor: I meant to say that I marked the boxes. Sorry about the confusion lol.

Anyways, I tried installing the driver manually, but I got this error message
[IMG]http://i33.tinypic.com/sb5638.png[/IMG]

---

### Post by psyoptic on 2008-10-20
> **Victormd said:**
> BTW, hardy is still a bit sticky with newer graphics cards. You might want to try downloading Intrepid Beta as the hardware support is far superior. Just keep in mind that it's still a Beta release.

I don't mind that it's still a beta, I've heard really good things about it. Do you know how I'd be able to upgrade to Intrepid?

And I never downloaded the CD image, I just installed Ubuntu through WUBI so I wasn't sure. Sysinfo says that I have the 64 bit version though.

---

### Post by starcannon on 2008-10-20
Installing video drivers manually is not recommended for a new user; that said, if for whatever reason your finding no joy with the [System]->[Administration]-[Hardware Drivers] menu option heres what your going to need to do (assuming you have tried no other video driver install attempts).


[LIST=1]
[*]Print this out for later you'll need it once your in CLi Mode.
[*]know the location of the driver file, default will be your desktop.
[*]CTRL-ALT-F1 (this will take you into pure CLi)
[*]Log in with user name and password at the text prompt.
[*]sudo /etc/init.d/gdm stop (this stops the Gnome Desktop Manager)
[*]sudo apt-get install build-essential (installs stuff for the driver to work might be plural so if it don't work that way add an "s" to the end I never remember lol)
[*]cd ~/Desktop (moves your command line into the Desktop directory)
[*]chmod a+x ./ati-driver*.run (makes the file executable)
[*]sudo ./ati-driver*.run (executes the file)
[*]Follow on screen prompts, allow it to configure a new xorg.conf if it asks.
[*]sudo /etc/init.d/gdm start
[/LIST]
That is the basics, I generally run Nvidia myself. GL

---

### Post by psyoptic on 2008-10-20
> **starcannon said:**
> Installing video drivers manually is not recommended for a new user; that said, if for whatever reason your finding no joy with the [System]->[Administration]-[Hardware Drivers] menu option heres what your going to need to do (assuming you have tried no other video driver install attempts).


[LIST=1]
[*]Print this out for later you'll need it once your in CLi Mode.
[*]know the location of the driver file, default will be your desktop.
[*]CTRL-ALT-F1 (this will take you into pure CLi)
[*]Log in with user name and password at the text prompt.
[*]sudo /etc/init.d/gdm stop (this stops the Gnome Desktop Manager)
[*]sudo apt-get install build-essential (installs stuff for the driver to work might be plural so if it don't work that way add an "s" to the end I never remember lol)
[*]cd ~/Desktop (moves your command line into the Desktop directory)
[*]chmod a+x ./ati-driver*.run (makes the file executable)
[*]sudo ./ati-driver*.run (executes the file)
[*]Follow on screen prompts, allow it to configure a new xorg.conf if it asks.
[*]sudo /etc/init.d/gdm start
[/LIST]
That is the basics, I generally run Nvidia myself. GL

Yeah, I'm seeing a lot of users have trouble installing this card. Oh well, guess I'll just try your method. Thanks for the info.

---

### Post by starcannon on 2008-10-20
Oh, hey this is definitely worth a read for you:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That will have a better method, sorry I didn't look for that sooner.

GL

---

### Post by Victormd on 2008-10-21
> **psyoptic said:**
> Yeah, I'm seeing a lot of users have trouble installing this card. Oh well, guess I'll just try your method. Thanks for the info.

I'm curious to know if this worked... let us know how you solved it.

---

