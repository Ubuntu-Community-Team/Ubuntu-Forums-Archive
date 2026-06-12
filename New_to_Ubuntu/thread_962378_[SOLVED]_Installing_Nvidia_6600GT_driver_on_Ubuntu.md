---
title: "[SOLVED] Installing Nvidia 6600GT driver on Ubuntu"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-10-29
Hiya I am new to ubuntu and have a problem getting the graphics driver to work on my Nvidia 6600GT.

I have asked for advice on this issue with a previous thread, partial command line success though I couldnt make it all the way through the commands. I get to the point of installing outside the X window enviroment then the command to install seems to fail.

I have the NVidia driver (the .run one) but my Ubuntu refuses to install it when the command line or the terminal.

Thanks to the help of another user "aktiwers", I have overcome my fear of the command line, and think this may be the way forward. 

*The package manager is not an option available for me as I am using another PC to download the files needed to use it, as mine has no internet connection*

Thanks For Your Help

---

### Post by bumanie on 2008-10-29
Go to System --> Aministration --> Hardware Drivers and click the box to enable the card. The driver will download  and install automatically. You should not need the one off the nvidia site.

---

### Post by igknighted on 2008-10-29
> **bumanie said:**
> Go to System --> Aministration --> Hardware Drivers and click the box to enable the card. The driver will download  and install automatically. You should not need the one off the nvidia site.

He has no internet connection.  And Hardware Drivers uses the package manager to install them.

I posted in your other thread (please, only one thread per issue in the future... it helps you because advice doesn't get scattered and it keeps the forum neater) recommending a distro that comes with nvidia's driver preinstalled.  If you really want Ubuntu, you should go to packages.ubuntu.com and download the packages nvidia-glx-new (i think that's the one that supports your card) and the appropriate kernel module package for the kernel version you are running (type uname -r into a terminal to find this out.  You can put these all on a flash drive or what not and install them by double clicking once on your ubuntu install.

---

### Post by sharkster2007 on 2008-10-29
Thanks igknighted

I have all the Nvidia packages in .deb format on my flash drive and the .run one.

I don't understand the term "appropriate kernel module package" though.

Could anyone tell me the web site address form "packages.ubuntu.com" and the "ubuntu security" one as I am using a web browser to download my files?

Sorry for the duplication another user started to ask about an ati card and didn't want to get things mixed up. Is there anyway to close the other and leave this one open?

---

### Post by sharkster2007 on 2008-10-29
Sorry 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Is the website address for the Ubuntu packages LOL, I said I was new :-)

---

### Post by igknighted on 2008-10-29
Try installing the .deb for nvidia-glx-new in the terminal using this command (normally a double-click would do, but this lets us see any error messages):

```
sudo dpkg -i path/to/nvidia-glx-new*
```

EDIT: Added sudo, that's needed

---

### Post by igknighted on 2008-10-29
[http://packages.ubuntu.com/hardy/nvidia-glx-new](http://packages.ubuntu.com/hardy/nvidia-glx-new)

These packages with a red dot are required as well.  Many you will already have installed, but 'linux-restricted-modules-common' you might not.  I would also recommend you install nvidia-settings as well, as it will give you a control panel to adjust settings like in windows.

---

### Post by sharkster2007 on 2008-10-29
I tried the above the .deb file is on my desktop, cd Desktop, then dir states its there, i ran sudo dpkg -i path/to/nvidia-glx-new*.

The outcome was no such file or directory exists

Also the update arrow had gone grey, (from previous attempts to install) on clicking this i got two error messages saying something like "ssl black listed" 

I don't understand any of this stuff, can anyone help? I want to run Ubuntu but this is a pain would i just be better waiting for Ubuntu 8.10 as this is rumoured to auto set up desktop effects on some reviews and is due for release tommorow?

---

### Post by igknighted on 2008-10-29
sorry, path/to/ was there for you to put your path in.  If you have already cd'd to the directory, then the path to would just be nvidia-glx-new*, or ./nvidia-glx-new*

---

### Post by igknighted on 2008-10-29
Yes, this is a pain on computers with no internet.  Intrepid (8.10) won't be any easier, because it's "auto-setting-up" involves being online to download packages.  Hardy can do the same, if it is online.

Linux really is designed to be online most, if not all the time.  There are ways around it, but as you are finding out, it is not terribly easy.  There are distro's (like Mandriva One 2009, for example) that have the nvidia proprietary driver pre-installed.  If you don't have internet connection, it might make your life much easier.

---

### Post by sharkster2007 on 2008-10-29
Same thing happens "no such file or directory", Thanks for your help on this matter but I to think Ubuntu needs to get their act together on this one. 

This makes windows look good, why can't all the none restricted parts be made available in one compiled deb archive, that would be much easier to use. 

The setup.exe system on windows, needs a rival on linux to compete this is too much hard work for a new user to undertake, and the point where many no doubt give up!

I thought we were supposed to be competing with Windows as an open source alternative not letting them win the OS wars :-(

---

### Post by igknighted on 2008-10-29
> **sharkster2007 said:**
> Same thing happens "no such file or directory", Thanks for your help on this matter but I to think Ubuntu needs to get their act together on this one. 

This makes windows look good, why can't all the none restricted parts be made available in one compiled deb archive, that would be much easier to use. 

The setup.exe system on windows, needs a rival on linux to compete this is too much hard work for a new user to undertake, and the point where many no doubt give up!

I thought we were supposed to be competing with Windows as an open source alternative not letting them win the OS wars :-(

Believe me, linux has completely one up-ed setup.exe... it's apt-get install.  The caveat is you need to be online.

A neat terminal trick... you can hit the tab key and it will auto-complete for you.  So once you cd into the directory the file is in, you can type 'sudo dpkg -i ' and then hit tab and it should give you suggestions.  Now you can start typing the name and hit tab and it will finish it for you.

Oh, another thought... are you adding in the star/asterisk i put at the end of that filename?  That's a wildcard, it means there other characters in the filename but i'm too lazy to type them, so install everything that starts like that.

Also remember that linux is case-sensitive.  So Desktop/filename is not the same as desktop/filename.

EDIT: We're not trying to be 'open source windows'.  There are so many things wrong with the way windows does things (yes, even the .exe thing to install), so linux just does its own thing, and if people like it, great.  If they have ideas they are welcome to implement them and offer them to others and see if they catch on.  But we are not trying to put a linux OS on every desktop, just make software that works.

EDIT2: It's not all in one package, because all the different pieces aren't just used for nvidia drivers.  It's a beautiful system the way the packages fit together, and very complex algorithms like those in apt figure out how they fit together.

---

### Post by sharkster2007 on 2008-10-29
Sorry I didn't mean an "open source windows" I meant as a rival operating system that could topple the Windows domination if only it was "user friendly".

I guess "built by hackers, for hackers" was true, a great system maybe the answer a lot of windows users are looking for but as yet not "user friendly" enough for basic users.

I have tried Linux in various flavours in the past and seen it evolve greatly (GUI, OS installers, partitioning & set-up) maybe when its evolved more (maybe opensource alternatives to ATI/NVIDIA will be the answer when they are perfected)it will be time to return. 

Good luck and thanks to you all its been a blast, thanks for trying to help me! :-(

I will return to linux eventually I may just be another distro or a future version of Ubuntu, your ideals are second to none and your helpfulness a credit to your platform.

---

### Post by sharkster2007 on 2008-10-29
Thank you igknighted , Knix and the others

I have now migrated to Mandriva Linux One 2009, I find it's hardware support excellent, just what I wanted. 

Now I can explore linux without that blasted 3D effects prob (It even worked from the livecd before I installed it).

I now dual boot Windows Xp SP3 and Linux Mandriva Linux One 2009 and I am very pleased with my new Linux distro.  I did think of abandoning Linux full stop, but as I said before something keeps bringing me back to it. 

Thanks for the command line help and the Mandriva Linux One suggestion I am over the moon and still using Linux too.

Thanks to all who helped (& tried to help me) happy Linux computing to you all

Best wishes Sharkster2007

---

### Post by sharkster2007 on 2008-11-01
Edit: I returned to Ubuntu (with 8.10) on 31/10/08 & solved this problem together with further help from the Ubuntu community & Greyarea2.

Greyarea2 has the internet connected solution [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741")
and now I've added my sharkster2007 manual one for none internet connected users.

Thanks to all who helped me again it s good to be back on Ubuntu and this blasted Nvidia problem now resolved. 

I appologise for losing my patience with Ubuntu before, this problem has haunted me through; Red Hat, Fedora, Suse, Linux Mint and other distros.

I found the forum community much better on Ubuntu and .deb files easier to obtain too.

---

### Post by sharkster2007 on 2008-11-06
6th November 2008 - I am now quite happy with ubuntu 8.10 thanks to your help.

I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up

Hope it helps others :-)

---

### Post by sharkster2007 on 2008-11-06
6th November 2008 I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up located here.

[http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia)

Sharkster2007

---

