---
title: "Install problems with Ubuntu 13.04"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Doug_Holden on 2013-09-10
I'm having problems installing Ubuntu 13.04 from a CD that I bought from Sir Tanon. (I would contact him but I do not have his email address.)

On 3 computers:

1.   A tower with xp won't install Ubuntu 13.04 at all though the CD boots to the install window (and the screen is so slow, it all but freezes).
2.   Another tower with xp does a nonfunctional install (only wall paper and right-click mouse context menu).  It informs me it cannot find a kernel.
3.   My laptop has windows 8 and it just tells me it needs the kernel.

I am disappointed that my CD cannot simply provide or download what is needed to install Ubuntu 13.04.

---

### Post by SuperFreak on 2013-09-10
I have no idea who Sir Tanon is but Ubuntu is free with donations optional at [UBUNTU WEB SITE]("http://www.ubuntu.com/download/desktop"). Perhaps you have a bad disk

---

### Post by su:bhatta on 2013-09-11
As pointed out by SuperFreak, Ubuntu is free and you do not need to buy a CD from anyone.

You can download Ubuntu 13.04 from here : [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Burn the image to a DVD and try a fresh install. The DVD will come with all the Kernels and drivers.

---

### Post by sudodus on 2013-09-11
> **Doug_Holden said:**
> I'm having problems installing Ubuntu 13.04 from a CD that I bought from Sir Tanon. (I would contact him but I do not have his email address.)

On 3 computers:

1.   A tower with xp won't install Ubuntu 13.04 at all though the CD boots to the install window (and the screen is so slow, it all but freezes).
2.   Another tower with xp does a nonfunctional install (only wall paper and right-click mouse context menu).  It informs me it cannot find a kernel.
3.   My laptop has windows 8 and it just tells me it needs the kernel.

I am disappointed that my CD cannot simply provide or download what is needed to install Ubuntu 13.04.

Welcome to the Ubuntu Forums :-)

If you give us more information, it will be much easier to give good advice. There are several versions and flavours of Ubuntu, some are better for old computers and some are better for new computers. The same version will not work for all three computers (at least not if you want to keep Windows 8 in the newest one, where there is probably UEFI).

1. Please specify each computer: Brand name and model, CPU, RAM size, graphics chip/card

2. Please tell us how you intend to install the Ubuntu flavour:

- as the only operating system (the simplest tast)
- dual boot with the existing Windows.

3. And please tell us how you (or some other end users) intend to use the computers (what kind of tasks).

---

### Post by varunendra on 2013-09-11
Welcome to the forums Doug_Holden !
> **Doug_Holden said:**
> I am disappointed that my CD cannot simply provide or download what is needed to install Ubuntu 13.04.
To add to what has already been said/suggested by others, you should first check your CD/DVD for defects (Ubuntu 13.04 doesn't fit on a CD, so it must be a DVD). 

Unless it is a non-standard CD/DVD, you should be able to bring up the "[Advanced Boot menu]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options")" by pressing any key during the purple splash screen while booting :

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png[/IMG]

In this menu, after selecting the language, you should get options like "Try Ubuntu..", "Install Ubuntu" etc :

[IMG]http://pix.toile-libre.org/upload/original/1354180067.png[/IMG]

Choose the option "Test disc for defects". This will perform a self test of the media and report back if there are any errors found.

You can (and should) also check the MD5SUM of the disc to ensure it is a standard official one ([How to MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM"))
Using a non-standard, unofficial CD/DVD is not recommended unless you can fully trust the source.

---

