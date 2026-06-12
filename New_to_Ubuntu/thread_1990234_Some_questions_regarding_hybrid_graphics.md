---
title: "Some questions regarding hybrid graphics"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Aldo93 on 2012-05-29
Hello there everyone,

I'm thinking of making the switch from Windows to Linux as I've ran into so many problems with windows and quite frankly I'm sick of it, I just have a few questions before I make the switch so I'm clear on a few things.

My laptop has hybrid graphics cards with an Intel and AMD GPU. I've done a bit of research and I've noticed that Linux distros don't support hybrid graphics very well, with the usual scenario being both cards turned on. 

I know there is VGAswitcheroo to get around this but I've noticed that you must enter command lines every time you boot your PC to turn off your discreet card, is this right? Furthermore I also got the impression that with hybrid graphics under linux, you completely lose the functionality of your discreet GPU, is this correct? I do a fair bit of HD video streaming, so I could really use the functionality of my AMD card if possible.

Also, typing out command lines to turn off one of your cards seems a little tiresome, so is it possible to create a script that would automatically execute upon loading the OS to save time doing it the manual way?

I'm no stranger to computers as I'm an IT technician, but I have little to no experience with Linux, and the only thing that's really stopping me making the switch is potentially losing the functionality of my AMD card, and having to type out command lines every time I boot up, if there was a way to automate the process that would be great.

Many thanks in advance and sorry it was rather long.

---

### Post by anonymous5 on 2012-05-29
> **Aldo93 said:**
> Hello there everyone,

I'm thinking of making the switch from Windows to Linux as I've ran into so many problems with windows and quite frankly I'm sick of it, I just have a few questions before I make the switch so I'm clear on a few things.

My laptop has hybrid graphics cards with an Intel and AMD GPU. I've done a bit of research and I've noticed that Linux distros don't support hybrid graphics very well, with the usual scenario being both cards turned on. 

I know there is VGAswitcheroo to get around this but I've noticed that you must enter command lines every time you boot your PC to turn off your discreet card, is this right? Furthermore I also got the impression that with hybrid graphics under linux, you completely lose the functionality of your discreet GPU, is this correct? I do a fair bit of HD video streaming, so I could really use the functionality of my AMD card if possible.

Also, typing out command lines to turn off one of your cards seems a little tiresome, so is it possible to create a script that would automatically execute upon loading the OS to save time doing it the manual way?

I'm no stranger to computers as I'm an IT technician, but I have little to no experience with Linux, and the only thing that's really stopping me making the switch is potentially losing the functionality of my AMD card, and having to type out command lines every time I boot up, if there was a way to automate the process that would be great.

Many thanks in advance and sorry it was rather long.

If your integrated GPU is the Intel HD 3000, then you don't have to worry because it's quite powerful if you're not going to play heavy games. Like you mentionned you can switch OFF the discrete GPU with vgaswitchroo. I've done it and the only noise I can hear now is that of the hdd. 
Of course you can make the script execute at startup and forget about it. Just place it in /etc/init.d/ and make it executable. Then run "update-rc.d name_of_the_script defaults".

---

### Post by CrocoDuck on 2012-05-29
Hi. Of course, you can automatize everything you need with a script. You can also make it load on startup.

> **anonymous5 said:**
>  
Of course you can make the script execute at startup and forget about it. Just place it in /etc/init.d/ and make it executable. Then run "update-rc.d name_of_the_script defaults".

I've installed ubuntu 11.10 on a friend's laptop that have the hybrid graphic card you said. It worked very good with proprietary drivers, we had only an issue with audio port switching (solved simply editing a configuration file). You could make an ubuntu bootable usb stick using unetbootin and then load the system without installing. Once, in a terminal:

```
sudo apt-get install mesa-utils
```

(if I'm not wrong). And then probe video performances with

```
glxinfo
```

and

```
glxgears
```

It will say you about of basic video performances with linux and you can also test something before install (and all without touching your previous installation, you know).

---

### Post by mastablasta on 2012-05-29
have you seen this thread?: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
certian combos of intel&AMD are now supported by proprietary drivers.

additionally you can boot linux into a live OS (put itself into RAM), try it out, see if it all works install drivers etc  and then it is all lost on reboot with nothing left behind and no changes to your system. it is recommended to try it out first ebfore installing it. if you wish to save some settings or driver you can use USB stick to boot and then add a persistance file to it.  note booting from liveCD or USB is much slower than real install. since computer reads faster from hard disk than from CD or USB media. 

use unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) or linuxliveusb ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)) to easilly create a bootable USB and add a persistance file to it (if you think it would be good to have it).


additionally there are plenty of desktop environemnts and windows managers if you do not like the default Unity+Gnome3. Nowadays you have Gnome classic, Cinamonn, Gnome shell (all on Gnome), a windows look &feel alike KDE (Kubuntu), XFCE with old gnoem2 look (Xubuntu) and the win98 look alike and very light option - LXDE (lubuntu) and many many more...

---

