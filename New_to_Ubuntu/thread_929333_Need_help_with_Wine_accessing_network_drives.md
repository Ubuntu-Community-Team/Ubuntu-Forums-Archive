---
title: "Need help with Wine accessing network drives"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by jimtanis on 2008-09-24
Hi;

I was on the wineHQ forums and have been trying to set up Wine so I can access a windows computer with an external 2tb USB raid drive on it.  

I was told I have to mount the drive first.  I can see the drive listed in the Places, but the /mnt folder has no listings in it.  I have Samba installed, but am not sure how to set it up to mount the drive, and then how to set up wine to access it once it's mounted.  

I am using Ubuntu Hardy Heron .  

Help!  From a newbie!

Thanks!  Jim NX0R

---

### Post by AndrewTheArt on 2008-09-25
Neither Samba nor Wine will help you mount your drive.

> Wine is a [software application]("http://en.wikipedia.org/wiki/Software_application") which aims to allow [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") computer [operating systems]("http://en.wikipedia.org/wiki/Operating_system") on the [x86 architecture]("http://en.wikipedia.org/wiki/X86_architecture") to execute _**programs**_ written for [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows").> Samba is a popular freeware program that allows end users to access and use files, printers, and other commonly shared resources on a company's [intranet]("http://searchwindevelopment.techtarget.com/sDefinition/0,,sid8_gci212377,00.html") or on the [Internet]("http://searchwindevelopment.techtarget.com/sDefinition/0,,sid8_gci212370,00.html"). Samba is often referred to as a [Network File System]("http://searchwinit.techtarget.com/sDefinition/0,,sid1_gci214121,00.html") and can be installed on a variety of [operating system]("http://searchcio-midmarket.techtarget.com/sDefinition/0,,sid183_gci212714,00.html") [platform]("http://searchservervirtualization.techtarget.com/sDefinition/0,,sid94_gci212797,00.html")s, including: [Linux]("http://searchenterpriselinux.techtarget.com/sDefinition/0,,sid39_gci212482,00.html"), most common [Unix]("http://searchenterpriselinux.techtarget.com/sDefinition/0,,sid39_gci213253,00.html") platforms, [OpenVMS]("http://whatis.techtarget.com/definition/0,,sid9_gci212711,00.html"), and [OS/2]("http://whatis.techtarget.com/definition/0,,sid9_gci212721,00.html").In other words, Wine lets you run many Windows software packages, and Samba is an implementation of protocols that provides interoperability between Linux/Unix servers and Windows-based clients. Neither will help you mount your hard disk drive, which is a relatively low-level hardware task handled by the included HAL (hardware abstraction layer).

To mount the drive in question, go to your Places and simply double click on the drive. It should mount to** /media.** To actually open it, either find the folder it's mounted under in /media or double click on it's entry in Places again.

---

### Post by jimtanis on 2008-09-25
Ok, I guess I didn't tell the whole story.  I can browse the drive in question fine from Ubuntu, it shows up in the places, I even created a bookmark for it, but I need to be able to access the drive from Wine.   

Example, I have Quicken installed in Wine, and I can't get to the drive in a wine explorer window even tho I can browse to it fine in Nautilus.

I have been working on winecfg and don't know what to put in there to find the drive.  

When I browse to the drive in Nautilus the path shows up as smb://nx0r/my%20book%20(g)/  .  And after I do so, it shows up in the places as (without the quotes)  "my book (g) on nx0r"  

Here is a screen shot of some of the stuff I am talking about.  [http://www.agapesbc.org/Screenshot.png](http://www.agapesbc.org/Screenshot.png) .  

It's probably something really simple I am overlooking, or a term I am not understanding.  

Thanks!  Jim NX0R

---

### Post by curl3y on 2008-10-20
One of first posts to the forums.

I am also experiencing the same problem with a shared folder on a win xp machine, i can map drives everywhere in wine as long as it is local. 

I even tried setting the network drive as a local hard drive and CD rom drive with the same results.

I am however running Ubuntu VMWare virtual machine, i thought this might have been this issue, but i am guessing not.

Did anyone find a solution to this, or someone can poke the newb (ie me) in the right direction it would be much appreciated.

---

