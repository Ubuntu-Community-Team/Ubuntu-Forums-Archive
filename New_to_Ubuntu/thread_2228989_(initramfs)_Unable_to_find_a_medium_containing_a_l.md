---
title: "(initramfs) Unable to find a medium containing a live file system - old sony vaio"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by gizmo1990 on 2014-05-20
Hi guys, first post here.

I've an old p3 256mb sony vaio that I'd like to get linux on. This will be my first foray into linux and from what I've read the flavour should be lubuntu for such old hardware?

My problem is that I can't boot from usb nor from dvd since I don't have a CF dvd drive. Can anyone suggest a way I can get Lubuntu onto my laptop?

The only way I can think is if Lubuntu can be installed via a setup file from within winxp? And then delete the xp partition and installation later?

Any advice greatly appreciated.

---

### Post by grahammechanical on 2014-05-20
I would not describe what you want to do as "absolute beginners" stuff. I have never tried it.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)

> [COLOR=#333333][FONT=Ubuntu]This HOWTO describes one way to do a Netboot install of Ubuntu by booting from files on a hard disk.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]You need to have [/FONT][/COLOR]grub[COLOR=#333333][FONT=Ubuntu] or [/FONT][/COLOR]grub2[COLOR=#333333][FONT=Ubuntu] already installed and bootable in order to use this method. It is therefore suitable for installing Ubuntu over an existing GNU/Linux installation.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Download the appropriate **initrd.gz** and **linux** files for your architecture and distribution from[FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit][http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]2.- Or from [archive.ubuntu.com/]("http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/current/images/netboot/") in case you're looking for the development version.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Save them somewhere that grub can read from. Inside /boot is a fine place. (These files are quite small, under 10MB for either architecture.)[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]2. Reboot your computer and press ESC if necessary to enter the grub menu (press Shift if you use grub2). Now we will get grub to boot from the files you just downloaded.[/FONT][/COLOR]


Like I said, not absolute beginners stuff.

Regards.

---

### Post by Bucky Ball on 2014-05-20
Welcome. 

Your other option is a minimal install. That will fit on a CD. ;)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Once you have the minimal installed, you would simply install lubuntu-desktop via Synaptic Package Manager (keeping it minimal) and you would have Lubuntu.

The minimal install installs just the kernel, you reboot to the terminal/CLI with the login prompt. At that point you login 'sudo apt-get install the-apps-you-want'. In your case, 'sudo apt-get install lubuntu-desktop' would pretty much do it I think.

Also not absolute beginner's stuff, but straightforward enough.

The install is text based rather than disco bells and whistles, but apart from that, the same things pretty much.

---

### Post by kansasnoob on 2014-05-20
Both the desktop and alternate Lubuntu images are CD size:

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

---

### Post by Bucky Ball on 2014-05-20
> **kansasnoob said:**
> Both the desktop and alternate Lubuntu images are CD size:

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

That's what I was thinking to start with. I've never installed it, but I can imagine as much. :-k

Xubuntu is now DVD size so I had to do the minimal install method on an old computer just the other day.

---

### Post by gizmo1990 on 2014-05-20
Thanks for the advice guys. I didn't know there was a cd sized iso. :( I'll have a good look through the options provided.

---

### Post by Bucky Ball on 2014-05-20
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Standard_PC)

694Mb. That will fit.

There's also this:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Your machine would fly. It's pretty much a version of what I explained earlier. In a round about way.

---

### Post by sudodus on 2014-05-20
> **gizmo1990 said:**
> Hi guys, first post here.

I've an old p3 256mb sony vaio that I'd like to get linux on. This will be my first foray into linux and from what I've read the flavour should be lubuntu for such old hardware?

My problem is that I can't boot from usb nor from dvd since I don't have a CF dvd drive. Can anyone suggest a way I can get Lubuntu onto my laptop?

The only way I can think is if Lubuntu can be installed via a setup file from within winxp? And then delete the xp partition and installation later?

Any advice greatly appreciated.

Although the previous advice is correct, I did not find anything about the a big problem because of low RAM. With only 256 MB RAM, you can 'use a shoe-horn' and install Lubuntu, but it will not be really useful with less than 512 MB RAM.

An alternative is to ***get more RAM***, upgrade to at least 512 MB (1 GB would make a big difference). But before doing that you should ***tell us more about the computer***. If the processor or graphics card are also problems, it is not worthwhile to add RAM sticks.

- CPU (model and frequency GHz)
- graphics chip/card (name and model)
- wifi chip/card (name and model)

Another alternative is to download and install a really tiny linux version, for example ***Wary Puppy, Tiny Core or DSL***. But do not expect much in terms of browsing the internet with only 256 MB RAM.

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
[/URL]
*Edit*: In two recent threads I was able to help, in one case with DSL, in another case with Wary Puppy. And I like Tiny Core, so they are all worth trying.

---

### Post by LastDino on 2014-05-20
> **sudodus said:**
> Although the previous advice is correct, I did not find anything about the a big problem because of low RAM. With only 256 MB RAM, you can 'use a shoe-horn' and install Lubuntu, but it will not be really useful with less than 512 MB RAM.

An alternative is to ***get more RAM***, upgrade to at least 512 MB (1 GB would make a big difference). But before doing that you should ***tell us more about the computer***. If the processor or graphics card are also problems, it is not worthwhile to add RAM sticks.

- CPU (model and frequency GHz)
- graphics chip/card (name and model)
- wifi chip/card (name and model)

Another alternative is to download and install a really tiny linux version, for example ***Wary Puppy, Tiny Core or DSL***. But do not expect much in terms of browsing the internet with only 256 MB RAM.

See this link for more details [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")


I would +1 this any day. Given the amount of your current RAM, I would suggest you to stick with the options suggested above. While Lubunt is great minimal distro, it is still quite advanced and once you install something like webbrowser (this alone can shoot your ram consumption in 200+MB with just one or two tabs open), you'll be in for ride and lot of disappointment due to slowness. IMO, getting at least 1gb more RAM would do you world of good. I've personally never faced any issues regarding processor or graphics. (I've p4 3.0Ghz single core with on board graphics and 4GB RAM)

---

### Post by QIII on 2014-05-20
You might try Bodhi Linux.  It is based on Ubuntu, but uses the Enlightenment window manager instead of a full-blown Desktop Environment.

---

### Post by Terry of Astoria on 2014-05-20
I agree with most of what is said here so far. You probably ought to try the lubuntu install. Do check for compatibility of your hardware, and don't waste your time banging your head against the wall, trying stuff every which way until the cows come home(although that's how I learned.) With a machine that old, things WILL go slowly, and probably with difficulty. And then even set up properly, its capabilities will be limited.

I suggest you pick up one of those old Dell Dimensions, you know the grey and black towers with Pentium 4s and a GB of RAM. Something like that is usually twenty bucks at a garage sale or thrift shop. Here is the US we have this place called Goodwill where they sell all kinds of computers. My boss picked up a Dell Inspiron notebook 1GB RAM for twenty bucks. It has XP on it and works fine! (EDIT: The Dells from that era support linux very well mostly.)

---

### Post by gizmo1990 on 2014-06-10
Hi guys,

I'm trying to install lubuntu on a very old sony vaio laptop, its specs are a p3 600mhz with 256mb ram.

I've burnt 14.04 to a cd and proceeded to boot from the laptops external pcmcia cd drive. Unfortunately, when I attempt to do a 'tryout of Lubuntu without installing' I get the following error,

(initramfs) Unable to find a medium containig a live file system

Now, I've visited other threads based around this error and done what most suggest. I've checked the MD5 Sum which checks out ok and I've also selected the 'Check disc for defects' which it appears to pass as well. I say appears because it simply goes to the installing lubuntu screen again and then ends in the initramfs error again??

Considering the age and make of my latop I thought the solution might be something specific and so created a new thread. Could anyone suggest how I deal with this error? I should also point out that I can't boot from USB with my laptop, its motherboard does not support that feature.

Any help much appreciated.

---

### Post by gizmo1990 on 2014-06-12
I'm trying to install Lubuntu on my old Sony Vaio but without success. I can't get past a initramfs(?) problem via cd installation and my bios doesn't support booting from usb.

Could someone tell me if it is possible to install Lubuntu from my vaios XP desktop? I still have XP installed so wondered if there was a distribution I could simply install directly from the OS?

Any help greatly appreciated.

---

### Post by Bucky Ball on 2014-06-12
Not a Ubuntu-based distro that I know of ...

You might have more luck posting a thread dealing with the error(s) you are getting when trying to install from CD (more detail regarding the 'initramfs(?) problem' would be a start) and letting us try to help you out with that. ;)

---

### Post by mörgæs on 2014-06-12
Your three threads regarding the same Sony have been merged. 

Please stick to this one.

---

