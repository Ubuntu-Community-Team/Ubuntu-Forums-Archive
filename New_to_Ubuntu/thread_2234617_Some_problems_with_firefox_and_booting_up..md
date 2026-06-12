---
title: "Some problems with firefox and booting up."
date: 2014-07-15
forum: New to Ubuntu
---

### Post by jack91 on 2014-07-15
Hello, I just installed Linux today and I am dual booting it with windows 7[U]

Booting Up[/U]
It is quite slow to boot up, as well as it defaulting to the ubuntu boot menu _[http://imgur.com/RdA7Epo](http://imgur.com/RdA7Epo)_ which is ok but I want it to default to the windows 7 boot menu seen here _[http://imgur.com/KIgOn3N](http://imgur.com/KIgOn3N)_.

_Firefox_
While watching youtube videos it will do 3 things, when maximising videos it only widens horizontally not vertically leaving two big black bars above and below the video _[http://i.imgur.com/yIk0oLt.png](http://i.imgur.com/yIk0oLt.png) _(ignore the white space, i had to crudely crop out my skype). 

Secondly if i pause a video the sound will carry on for about a second and then stop, it seems to sync up with the video when i start it again but still it is odd. 

Thirdly videos will clip and when scrolling down many copies of the video will appear vertically in a row. It looks something like this _[http://i.imgur.com/QTisiCV.jpg](http://i.imgur.com/QTisiCV.jpg)_ (had to do this in gimp as i couldn't time it correctly)

Another thing it will do while watching videos not on youtube is full screen them on my 2nd screen. _[http://i.imgur.com/f6ILXm4.jpg](http://i.imgur.com/f6ILXm4.jpg)_ which I don't want.


I'm thinking it is some kind of graphical issue with my hardware. My friend who uses debian said it might be a problem with unity, either way I don't really know whats wrong with it and i was hoping you could tell me, cheers in advance.

Jack.

---

### Post by mooreted on 2014-07-15
For one thing, Adobe stopped support for Adobe Flash Player in Linux years ago. FireFox uses an old plugin 11.2. For this reason I have moved to the official Google Chrome browser, not the Chromium browser in the software center. There is an open-source flash player for FireFox, but it doesn't seem to work very well.

I'm sure others will have suggestions, but mine would be to switch to the official Google Chrome browser.

---

### Post by Frogs Hair on 2014-07-15
I see by one of the images that you have installed with the unsupported Windows installer. Wubi installs Ubuntu inside the Windows partition and uses the Windows boot loader. [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by jack91 on 2014-07-15
How can you tell i've used an unsupported windows installer? Because the image of the ubuntu boot loader I just got off google images. Does this mean I have to install ubuntu again?

---

### Post by sammiev on 2014-07-15
> **jack91 said:**
> How can you tell i've used an unsupported windows installer? Because the image of the ubuntu boot loader I just got off google images. Does this mean I have to install ubuntu again?

Wubi is no longer supported and in post #3 Frogs Hair directed you to the link.

You will need to install along side of Windows or a few other options.

---

### Post by jack91 on 2014-07-15
Hi, I think theres some confusion I didn't take the image of the linux boot screen I just found it on the internet, I installed linux by partitioning my hard drive and then copying it onto a usb by using this [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/). I didn't use WUBI to install linux.

---

### Post by yancek on 2014-07-15
> How can you tell i've used an unsupported windows installer? Because the  image of the ubuntu boot loader I just got off google images. Does this  mean I have to install ubuntu again

I believe what he is referring to is not the Ubuntu Grub menu with the purple background but the second image you refer to as the windows 7 boot menu.  Windows doesn't boot Linux.  You need third party software to do that and wubi will create an entry in the boot menu of windows.  It looks just like what you have posted.  You can also use other third party software to do this.

Maybe if you posted more information on exactly how you downloaded the ubuntu iso, how you created a bootable medium and installed it you could get more specific advice but if you used wubi it's going to be problematic as explained above.

---

### Post by jack91 on 2014-07-15
Ah sorry I hadn't even heard of wubi before creating this thread so i definitely didn't use it. I created a 100gb partition in windows, downloaded ubuntu 64 bit version off the official website, put it onto a usb with _[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)_ and then installed Linux using this guide _[https://www.youtube.com/watch?v=PvP_4J2MUEc](https://www.youtube.com/watch?v=PvP_4J2MUEc)_ (I'd skip a minute into it as the 1st part of the video is showing how to partition a hard drive)

I also didn't take either picture of the boot menus (sorry for the confusion)

---

### Post by sammiev on 2014-07-15
> **jack91 said:**
> Ah sorry I hadn't even heard of wubi before creating this thread so i definitely didn't use it. I created a 100gb partition in windows, downloaded ubuntu 64 bit version off the official website, put it onto a usb with _[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)_ and then installed Linux using this guide _[https://www.youtube.com/watch?v=PvP_4J2MUEc](https://www.youtube.com/watch?v=PvP_4J2MUEc)_ (I'd skip a minute into it as the 1st part of the video is showing how to partition a hard drive)

I also didn't take either picture of the boot menus (sorry for the confusion)

Sounds like you installed it correctly then. Have you taken all the updates and also selected 3rd party add-ons?

---

### Post by jack91 on 2014-07-15
I've updated everyhing, but I don't know anything about selecting 3rd party addons.

---

### Post by sammiev on 2014-07-15
> **jack91 said:**
> I've updated everyhing, but I don't know anything about selecting 3rd party addons.

Look for "Software & Updates" Look at the first two tabs and the last tab. Run a few updates and make sure you reboot afterwards.

---

### Post by jack91 on 2014-07-16
ok, thank you

---

### Post by Frogs Hair on 2014-07-16
You would see this with a WUBI installation and is the Windows boot-loader . [URL="http://imgur.com/KIgOn3N"]http://imgur.com/KIgOn3N


[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[/URL]

---

### Post by yancek on 2014-07-16
If you want Grub to default to booting windows, you can count down to the windows entry in the boot menu then edit this file in Ubuntu:  /etc/default/grub
Open a terminal with a text editor with root privileges.  If you use gedit do:  sudo gedit /etc/default/grub  That will open the file and near the top of the file you will see this entry:

> GRUB_DEFAULT=0

To set windows as the default boot, enter the number of the windows entry from the menu minus one since in this case Grub counts from zero rather than one.

---

