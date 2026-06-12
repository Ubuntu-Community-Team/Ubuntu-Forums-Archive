---
title: "installing Ubuntu and windows"
date: 2016-09-24
forum: New to Ubuntu
---

### Post by time.zone on 2016-09-24
Hello everyone,
 I am a potential day-one Ubuntu user and I have very little tech knowledge.
Is it possible to install Ubuntu on only one of my SSDs while keeping Windows10 on my other and choosing which one I want to use at startup?
I am asking because I want to try out/get familiar with Ubuntu first, and of course make sure all of my necessary programs (Adobe AI/PS; and some on line games) will be compatible with Ubuntu, before making the switch, if I do. 

 Also, what is a realistic level of tech knowledge that one should have if trying to install programs, drivers, etc on Ubuntu as compared to Windows?

 Any info would be greatly appreciated!

---

### Post by oldfred on 2016-09-24
Is hardware UEFI or BIOS?

Is Windows installed in UEFI or BIOS boot mode?
Generally best to keep Ubuntu install in same boot mode as Windows.

If UEFI, may want to start with link in my signature. It is a lot of info so ask if you do not understand.

---

### Post by grahammechanical on 2016-09-24
> Also, what is a realistic level of tech knowledge that one should have  if trying to install programs, drivers, etc on Ubuntu as compared to  Windows?

As part of a default installation of Ubuntu we get a default set of applications that suit most people's needs. Among other things there is a web browser and an office suite. There is a large range of other applications in the Ubuntu repositories and they can be installed through the app store (Ubuntu Software) by clicking an icon.

We update/upgrade the OS by running Software Updater. That works by doing a couple of mouse clicks. Most hardware drivers are installed as part of the installation process. We also have a utility called Additional Drivers that will install proprietary video drivers for us with just a mouse click. But the default open source video driver will often work very well.

Ubuntu is Linux and that means we can do all things by using Linux commands if we want to but one of the intentions of the Ubuntu developers is to produce an OS that does not require too much technical knowledge to use. I think that Ubuntu meets this intention very well.

Regards.

---

### Post by time.zone on 2016-09-24
Hi, and thanks for the info links.
 I ran system info and it states UEFI value next to BIOS MODE in the item column; so it looks like my hardware is UEFI.  I am not sure what boot mode I have;  I ordered the computer from a local business.  Is there an advantage to having BIOS.
I should have added in my original post that I have two SSDs, but only use one; the other is completely 'empty.'
Thanks for the link too, I will spend a night doing some research!

---

### Post by time.zone on 2016-09-24
Great! This looks like what I am looking for with a switch from Windows.  After a bit more research into the programs that I use it looks like Adobe does not run on Ubuntu.  Are you aware of a "list" of non Linux-compatible programs; or is my program-by-program search the way to go?
Thanks again!

---

### Post by Impavidus on 2016-09-25
Much commercial software doesn't work on Linux; you have to find alternatives. This is a place to start: [http://www.linuxalt.com/](http://www.linuxalt.com/)
I suggest you have a look at Inkscape and GIMP. They can be installed on Ubuntu in a few mouse clicks.

---

### Post by mastablasta on 2016-09-25
> **time.zone said:**
> Great! This looks like what I am looking for with a switch from Windows.  After a bit more research into the programs that I use it looks like Adobe does not run on Ubuntu. 

if you are using Adobe at work and if it has to be Adobe, then i suggest you stay on Windows. you will have a lot less issues to solve.
you also mentioned online games, which no doubt work on windows. on linux the issue is if they donot have a linux version - eventhough they might work, the online games are patched often. and each patch has a chance to break what little compatibility there is.

in short if you are using windows programs and games stay on windows.

if you want to explore Ubuntu (or in this case better one of it's lighter derivatives), learn about it and to use it for some very safe internet browsing then i would suggest you look into installing in it virtualbox. it is very easy to do. here is an example tutorial made for an older version but it is still valid: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

if you ask me the path of less painfull move from windows to linux leads through using Opensource programs on widnows. once you get used to using them switching to Linux is very easy. i was using Gimp, Inkscape, Filezilla, Firefox, Openoffice (now Libre Office) and many other opensoruce apps since almost their start on windows. and still do. then i just installed linux on a PC (first was on an inherited PC with "unregistered" XP). install itself was trivial and it was easy to use it since it had the same apps. the only issue i have is hardware is a bit strange and not really full compatible. but works for the most part.

---

### Post by time.zone on 2016-09-25
Wow! Thanks for the link.  I did not know so many open source programs were available for Linux;  I have actually used many of these programs in the past.
Thanks again!

---

### Post by time.zone on 2016-09-25
Thank you mastablasta, it looks like dual boot is what I was looking for to familiarize myself first with Ubuntu.  I might be able to get this done today!

---

### Post by Herber on 2016-09-25
I am getting to the conversation late here, but I recommend a SATA switch in your desktop.  Then you can select which drive you want to boot from and avoid any potential changes to the wrong drive.

---

### Post by time.zone on 2016-09-26
OK, it looks like the SATA switch is what I am looking for, that way I can keep all my OSs on separate SSDs.  Thanks for the help!

---

