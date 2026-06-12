---
title: "[SOLVED] Ubuntu 8.10 - How do I set up the Nvidia Driver?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-10-30
Hiya Everyone

I have the new Ubuntu 8.10 (Final) on CD, I previously had problems with My Nvidia 6600GT Graphics card on the previous ubuntu and gave up & migrated to another distro of Linux (Mandriva) which did it automatically for me.

I wish to use the "propriety" Nvidia 173* driver with it and have downloaded the .deb file:
nvidia-173-kernel-source_173.14.12-0ubuntu3_i386 

Is this the correct file for what i want? If so how would i install it correctly into my linux system? I am not afraid of using the command line if this is required to set up correctly.

[COLOR="Red"]*I am not connected to the internet, I am using a secondary Windows PC which is, so the package manager is not an option for me (apart from manual use)*[/COLOR]

Thanks again

Sharkster 2007

---

### Post by kk0sse54 on 2008-10-30
If you have the right package just right click it in nautilus and select install with deb installer (or something to that effect :)). Otherwise if Ubuntu is auto detecting your card you can try out Envy although I've never used it with a nvidia card so I can't give you much help there.

---

### Post by sharkster2007 on 2008-10-30
Thanks cloud

I am avoiding EnvyNG as I installed it before it went on and didn't display any menu or icon to use it with (and may have broke the installer)

Does the file I stated sound like the correct package? 

I am exercising extreme caution this time after rushing headlong at it like I did before (probably breaking several parts of ubuntu without realising it).

I think i may need to use sudo aptitude on the command line to install and set up but I am unsure how to do it. Does anyone have an How to on this?

---

### Post by perlluver on 2008-10-30
That is the right version, or the newer 177, version might work better for that card.  That seems to be a newer card.

---

### Post by kk0sse54 on 2008-10-30
Here's a link from another person with a similiar problem except in this case they had an internet connection. I believe however though that you have correctly downloaded the right driver package

[http://www.neowin.net/forum/index.php?showtopic=672294](http://www.neowin.net/forum/index.php?showtopic=672294)

---

### Post by sharkster2007 on 2008-10-30
Thanks perlluver

For confirming the package for me, so if i just double click on the .deb file I have, the package manager should install it for me, without further modifications, or command line alterations?

---

### Post by Landara on 2008-10-30
EnvyNG has always worked flawlessly for me, I'd at least try it :)

---

### Post by kk0sse54 on 2008-10-30
> **sharkster2007 said:**
> Thanks perlluver

For confirming the package for me, so if i just double click on the .deb file I have, the package manager should install it for me, without further modifications, or command line alterations?

Yes it would install the package through the deb installer :), So no extra command line typing needed to install

---

### Post by sharkster2007 on 2008-10-30
Thanks Cloud

I just want it to be as stress free as possible this time LOL, last time it annoyed me so much trying to get it to work, I gave up and migrated to Mandriva Linux One 2009 instead. 

(I was working on the official Nvidia .run file installation though. I never want to see a .run file ever again!) LOL

If I hadn't have seen it in use I would have believed it impossible before, I really want to run Ubuntu though and I am hoping 8.10 Will make this easier. ;-)

---

### Post by sharkster2007 on 2008-10-31
I have recently installed 8.10 (went without a hitch)

But when i double clicked on the .deb file the package manager reported:

"Error: Dependancy is not satisfied: dkms"

I am trying to use the .deb files for the Nividia 173 or 177 drivers, i take it this means i need another .deb file so satisfy this is this correct? Does anyone know what it should be called?

EDIT- I now have [COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu2_all[/COLOR] package is this what I need or I am i barking up the wrong tree again?

[COLOR="Red"]*I am not connected to the internet, I am using a secondary Windows PC which is, so the package manager is not an option for me (apart from manual use)*[/COLOR]

Thanks again sharkster2007

---

### Post by sharkster2007 on 2008-10-31
Hello again

I have now found [COLOR="SeaGreen"]http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source[/COLOR] on the internet if i install all the dependancy packages (red) and Nvidia Driver (green) should this solve this problem once and for all? I believe I have the right file but is a "dependancy hell" problem, I am unsure whether or not I am correct though and wish to exercise caution

---

### Post by sharkster2007 on 2008-10-31
STATUS REPORT

I have installed [COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu_all.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb[/COLOR] as these are the only parts required by 8.10 the other dependancies are already installed as standard.

I now assume that my driver is installed and in place but when I go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS and select NVIDIA ACCELERATED GRAPHICS DRIVER (VERSION 173)and click enable, it seems to want to go to the internet (which i haven't got) but i don't know why as the driver and its dependancies are installed already.

It fails to enable the driver, what am I doing wrong here? is there a command line to enable the driver manually? I feel most of the hard work has been done if i could activate the driver this solution should be completed.

Can Anyone please help with this?

[COLOR="Red"]PS (I have no internet connection I am dependant on files downloaded from a PC which is a Windows one)[/COLOR]

---

### Post by sharkster2007 on 2008-10-31
I know that the 6600GT Nvidia is supported by Linux as it is in use with Linux Mandriva One 2009 and have witnessed desktop effects in action, sadly i want to use Ubuntu this is proving to be a major pain in the butt.

I wish to resolve this problem as it drove me away from using ubuntu 8.04LTS an do not wish any other new Linux user to have to go through all this unguided again.

---

### Post by sharkster2007 on 2008-10-31
Greyarea2 seem to have a similar problem on his tread to
[http://ubuntuforums.org/showthread.php?t=965741](http://ubuntuforums.org/showthread.php?t=965741)

I too thought bug testing was supposed to remove issues like this?

---

### Post by sharkster2007 on 2008-11-01
Greyarea2 has the internet connected solution [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741")
and now I've added my sharkster2007 manual one for none internet connected users.

---

### Post by sharkster2007 on 2008-11-06
6th November 2008 I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up located here.

[http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia)

Sharkster2007

---

