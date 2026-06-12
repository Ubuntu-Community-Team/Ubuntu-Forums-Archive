---
title: "Installation on 1998 Pentium III"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by CHERRYPOP on 2013-01-19
I am trying to install Ubuntu 12.10 on my very old computer (1998 Pentium III). It does not have an OS on it at the moment so i have already changed the setting (on the blue screen) to boot fronm CD-ROM. Once it boots it gets as far as the main first screen for UBUNTU (Try without installing... and some other options...) this is where i seem to be having difficulties. A dialog box pops up saying...
'you are leaving the graphical boot menu and starting the text mode interface'
And gives 2 options 'OK' & 'Cancel', however the dialog box is flashing and will not allow me to choose an option.
When i press 'Pause/Break' is stops flashing but then restarts flashing when i press any other key.

---

### Post by cottfcfan on 2013-01-19
it's highly unlikely that a modern operating system like Ubuntu 12.10 will install & run on a 15 year old computer.
If you could post the specs of the computer in question this could be verified. But you may get more mileage out of puppy linux, or something similarly lightweight.

---

### Post by GordThompson on 2013-01-19
Give up on trying to install 12.10 on that machine. Even if it did run (which is extremely unlikely) it would be so slow as to be unusable. As cottfcfan said, check out other distributions that are better suited to run on older hardware.

---

### Post by CHERRYPOP on 2013-01-19
> **cottfcfan said:**
> it's highly unlikely that a modern operating system like Ubuntu 12.10 will install & run on a 15 year old computer.
If you could post the specs of the computer in question this could be verified. But you may get more mileage out of puppy linux, or something similarly lightweight.
Thankyou Cottfcfan

Would you please be able to guide me through it. I am totally new to this and am totally lost :-(

---

### Post by CHERRYPOP on 2013-01-19
Thank you GordThompson, but i dont know where to start! :-(

---

### Post by CHERRYPOP on 2013-01-19
> **CHERRYPOP said:**
> Thankyou Cottfcfan

Would you please be able to guide me through it. I am totally new to this and am totally lost :-(
How about WaryPuppy 5.3?? Will that work?

---

### Post by myyk on 2013-01-19
Puppy Linux will run on it, however flash and java may still be too heavy, but give it a try you'll be surprised :D

---

### Post by cottfcfan on 2013-01-19
Do you know how much memory you have? and the hard drive capacity?

---

### Post by grahammechanical on 2013-01-19
From this

> 'you are leaving the graphical boot menu and starting the text mode interface'

I would guess that you do not have enough RAM to run the 12.10 Graphical Installer. You need a text mode installer.

> The minimum memory requirement for Ubuntu 12.10 is 768 MB of memory and 5 GB of disk space for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop")

> The minimum memory requirement for Ubuntu 12.04 is 384 MB of memory for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.

> Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use _the alternate install CD_.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")

Ubuntu 12.10 does not have an alternate (text) install CD but 12.04 does.

[http://releases.ubuntu.com/12.04.1/]("http://releases.ubuntu.com/12.04.1/")

Regards.

---

### Post by CHERRYPOP on 2013-01-19
Right..., i have downloaded Puppy Linux, WaryPuppy 5.3 and am still having a problem.
When it gets to the main screen it will not load to give any options.
Only at the bottom of page = F2 Help   F3 = Advanced Help
It will allow me to do these.
Then, Boot:

???????

Please help Me :-(

---

### Post by cottfcfan on 2013-01-19
What are you booting from cd? usb?
And have you set your computer to boot from whatever medium you're using?
I would have also gone for the latest version of Puppy 5.4 & used Precise puppy from here:
[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

---

### Post by oldos2er on 2013-01-19
Puppy forums are here: [http://murga-linux.com/puppy/](http://murga-linux.com/puppy/)

---

### Post by verymadpip on 2013-01-19
I'd be tempted to try 12.04 non-pae (big assumption on my part there) mini iso & add a window manager, panel & such like afterwards.

It's the method that revived a 2000/2001 TC1000 tablet for me.  Flash performance is spectacularly bad though, & I've not even installed Java.

Non-pae mini iso available on this page:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by CHERRYPOP on 2013-01-19
> **cottfcfan said:**
> What are you booting from cd? usb?
And have you set your computer to boot from whatever medium you're using?
I would have also gone for the latest version of Puppy 5.4 & used Precise puppy from here:
[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)
Booted from CD-Rom in settings.
I only have one disc left to burn now so i will do exactly what you tell me to now.
I thought downloading an older version of puppy would suit the old computer.
I am now downloading Precise Puppy

---

### Post by kurt18947 on 2013-01-19
Puppy is about as light as it gets ,  I think.  I'm running Xubuntu 12.04 on a PIII notebook with 512 MB. RAM.  It works quite well except for flash.  Flash doesn't run at all.  I doubt the more demanding graphics distros like Ubuntu or Mint are going to work.  This doesn't help now but I use DVD-RWs for distro hopping.  Older machines may not boot from a USB drive but most will boot from a DVD-RW in my experience.  Another distro that works pretty well on my old machine is PC LinuxOS but they march to their own drummer.  Lubuntu is light and still in the *buntu family but I had installer problems with Lubuntu 12.04.  Xubuntu installed perfectly.

---

### Post by Jerry N on 2013-01-19
My first use of Ubuntu was to attempt to resurrect old machines like yours.  This was in 2007 and the only version of Ubuntu that provided minimally acceptable performance (acceptable to me, that is) was Xubuntu 6.06.  I never could make it print though.  Damn Small Linux should work and the developer seems to have renewed his interest in it in the last year or so.  DSL is pretty weird in general and its printing is even weirder.  I tried dozens of so called "lite" linux distros and none provided better performance than DSL. I found that old old old Windows 2000 worked far better (on these old machines) than any linux distro but I wouldn't connect to the internet with it. I gave up and scrapped the old machines, except for the 1999 Toshiba laptop with Windows 2000 that I use to control a Ten-Tec short wave receiver.  I was never able to install any version of linux on that Toshiba.

Jerry

---

### Post by quarkhirad on 2013-01-19
hey Cherrypop

Hi i have never tried puppy linux. Though i have tried dsl linux on a pentium p4 with 2X 128mb (i think it was a SD ram and not DDR someone please correct me if i am wrong) from a usb stick. Off course to speed things up i loaded the image onto the ram (i think it is the toram command in the boot options again someone please correct me if i am wrong). It worked very well. Infact the guy who owned the computer gave up his windows and just used dsl. So in general i would agree with jerry and say give the latest version of DSL (damn small linux) a try.

Infact honestly while reading your request (the first post in this thread). My reaction was why ubuntu 12.10 just try dsl. :)
hope it should work. Off course please no offense to ubuntu users. Infact i am currently using firefox browser in ubuntu 12.10 to type this post. LOL ;) :p

---

