---
title: "[SOLVED] las few questions before trying Ubuntu"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by mal_conductor on 2008-07-12
Hello All,

I had tried Linux (a Red Hat distribution) a few years ago, but went back to Windows because I found Linux difficult to work with.  I have read very good things about this board being very helpful; so, I hope to make a go of it this time around.

I do have some final questions before taking the plunge:
(Please respond to any or all of the questions below)

1)	I like to keep minimize software on my hard drive.  I hear that Linux has lots of programs, and many of them do the same or similar things.  With the “out of the box” install are there redundant applications i.e. more than one program to do text documents, more than one program to do spreadsheets?  So even if I don’t install the  redundant applications they are still taking hard drive space

2)	Do I still have to “mount” USB ports?!!!!  Why can they just work?!!!! This is one of the reasons I went back to Windows

3)	I had problems with the Openoffice Spreadsheet.  When I did conditional formatting on cells the application went bunkers.  Has anyone else encountered this?

4)	Is Open Office similar to MSOffice?   I ask because at work I need to be very skilled with MS Office.  I hope the skills acquired, from time invested into learning Open Office, are applicable in MS Office.

5)	Can programs written for Windows only run on Linux?  I work with some Windows-only applications.  I have read about WINE and WM but I am still not clear on a few things.
a.	What is the practical rule of thumb with WINE.  Most stuff works, or most simple applications work, complex applications don’t work, or maybe only the applications listed on [www.winehq.com](www.winehq.com) work?
b.	How does VM work?!!! I read you have to half start with a windows install CD then finish up the software installation with VM.  Sounds awkward!!!

6)	Do all radio stations play with Linux software.  Web based Radios typically offers winamp, Windows Media, Itunes and others.  Is there on one alternative software for each of these formats?  Does one Linux application support ALL or some of these formats?  What’s the practical verdict on this?

7)	Why does LTS say it’s supported for 3 years?!!! What happens after 3 years.  Do I have to pay for support, a new version is released, other?

8)	The vendor I want to but Ubuntu from offers a DCROM and a DVD version.  Do these have same or different information?  i.e. The DVD format holds more info therefore I get more stuff or is the same on both?

Thank you,  I look forward to your answers before committing to Linux

---

### Post by Sealbhach on 2008-07-12
You're not buying it - you won't get a warranty. Why don't you get a free Live CD and try it out?

That way, you see what works and what doesn't without changing anything on your computer.


.

---

### Post by appi2012 on 2008-07-12
1.) In ubuntu, there is are only one application per common tasks. The entire install is around 4 gbs by default, but installing extra applications increases that.

2.)Usb drives are mounted when you plug them in.

4.)OpenOffice is fairly similar to MSOffice, but not exactly the same.

5.) Test your apps on wine, if the don't work, you can use a VM. VMs basically run the entire operating system inside another. You install windows as a virtual machine so that you can laod it inside ubuntu. The ubuntu live cd installer makes it really easy to dual boot windows and linux too, so that's another option.

7.) 3 year support means that there will be updates to your system that will fix bugs for 3 years, after that you'll have to upgrade if you want more bug fixes and updates (which are good)

Hope that helps!

---

### Post by alienexplorers on 2008-07-12
Only the programs you load to your computer are on your computer.  The rest are held on servers in the various repositories.

---

### Post by nothingspecial on 2008-07-12
> **mal_conductor said:**
> 
6)	Do all radio stations play with Linux software.  Web based Radios typically offers winamp, Windows Media, Itunes and others.  Is there on one alternative software for each of these formats?  Does one Linux application support ALL or some of these formats?  What’s the practical verdict on this?


I`ve never had a problem with radio,  but I will say that although BBC iPlayer works with Ubuntu, ITV & Channel 4`s versions do not yet.

(Excuse me if you`re not from the uk and don`t care)

---

### Post by YaroMan86 on 2008-07-12
> **mal_conductor said:**
> Hello All,

I had tried Linux (a Red Hat distribution) a few years ago, but went back to Windows because I found Linux difficult to work with.  I have read very good things about this board being very helpful; so, I hope to make a go of it this time around.



This is a common experience. I first tried Linux in 2002, then 2004 and didn't like it for the same reason, mostly because I didn't know the first thing about how to use BASH and using Windows had spoiled me into wanting a GUI to run at boot-up.

> **mal_conductor said:**
> 

I do have some final questions before taking the plunge:
(Please respond to any or all of the questions below)



I should be able to do this.

> **mal_conductor said:**
> 
1)	I like to keep minimize software on my hard drive.  I hear that Linux has lots of programs, and many of them do the same or similar things.  With the “out of the box” install are there redundant applications i.e. more than one program to do text documents, more than one program to do spreadsheets?  So even if I don’t install the  redundant applications they are still taking hard drive space


After you install Ubuntu, I recommend running Synaptic Package Manager (**System -> Administration -> Synaptic Package Manager**) or Add/Remove Programs (I don't use this, I think its in **Applications -> Add/Remove Programs**) and removing everything in there you think you don't want.

CAUTION: Be very careful what you DO remove. Basically, if it lists a lot of things that it also wants to remove as a result of removing the program, you might want to turn back.

There are very few, if any, "ambiguous" programs installed with Ubuntu. You have options to install more, but the devs are pretty good at keeping unneeded multiples off the disk.

> **mal_conductor said:**
> 
2)	Do I still have to “mount” USB ports?!!!!  Why can they just work?!!!! This is one of the reasons I went back to Windows


Ubuntu mounts just about any USB volumes you connect, thanks to sch things as hot-plugging support and I also believe GNOME has something to do with it as well. Short answer: It is usually automatically mounted.

> **mal_conductor said:**
> 
3)	I had problems with the Openoffice Spreadsheet.  When I did conditional formatting on cells the application went bunkers.  Has anyone else encountered this?


I never encountered this problem... but since OOo is frequently updated and worked on (OOo 3 is in the works) I imagine this is likely to have been addressed.

> **mal_conductor said:**
> 
4)	Is Open Office similar to MSOffice?   I ask because at work I need to be very skilled with MS Office.  I hope the skills acquired, from time invested into learning Open Office, are applicable in MS Office.


I'd say its like MS Office 2003 and older. This is a Good Thing. Have you ever used Office 2007?

> **mal_conductor said:**
> 
5)	Can programs written for Windows only run on Linux?  I work with some Windows-only applications.  I have read about WINE and WM but I am still not clear on a few things.
a.	What is the practical rule of thumb with WINE.  Most stuff works, or most simple applications work, complex applications don’t work, or maybe only the applications listed on [www.winehq.com](www.winehq.com) work?
b.	How does VM work?!!! I read you have to half start with a windows install CD then finish up the software installation with VM.  Sounds awkward!!!


WINE has reached version 1.1.1 at the time of my assaulting you with my text here. In my experience, it supports most Windows apps with a little configuration. It all depends on the app. And no, not only the applications listed on WineHQ's AppDB work, its just a good guide to start with. The only way to really know is to try.

Virtualization is a snap with Ubuntu. I prefer Virtualbox. It's lean and fast, but it doesn't skimp on quality. All the installation is painless, and you don't need to "partially" reinstall Ubuntu to get it set up.

> **mal_conductor said:**
> 
6)	Do all radio stations play with Linux software.  Web based Radios typically offers winamp, Windows Media, Itunes and others.  Is there on one alternative software for each of these formats?  Does one Linux application support ALL or some of these formats?  What’s the practical verdict on this?


Amaork and Rhythmbox offer good web radio support. You'll probably need restricted codecs installed, but that is also insanely easy to do. If those fail, there's very VERY little VLC cannot play or stream.

> **mal_conductor said:**
> 
7)	Why does LTS say it’s supported for 3 years?!!! What happens after 3 years.  Do I have to pay for support, a new version is released, other?


LTS stands for Long Term Support. This means it is given updates and official support from Canonical longer than other versions. Once it goes off support, essentially most updates are finished, nothing new is added, and Canonical doesn't accept support calls on its commercial lines for it anymore.

You only have to pay for commercial support.

> **mal_conductor said:**
> 
8)	The vendor I want to but Ubuntu from offers a DCROM and a DVD version.  Do these have same or different information?  i.e. The DVD format holds more info therefore I get more stuff or is the same on both?


Are you sure you want to *buy* what you can download for free from [www.ubuntu.com?](www.ubuntu.com?) I'm not sure what would be on DVD editions of Ubuntu.

> **mal_conductor said:**
> 
Thank you,  I look forward to your answers before committing to Linux

And I hope I answered them.

---

### Post by Paddy Landau on 2008-07-12
> **mal_conductor said:**
> 3)    I had problems with the Openoffice Spreadsheet.  When I did conditional formatting on cells the application went bunkers.  Has anyone else encountered this?

4)    Is Open Office similar to MSOffice? I ask because at work I need to be very skilled with MS Office. I hope the skills acquired, from time invested into learning Open Office, are applicable in MS Office.

OO is not MS Office.

For me, that's a really, really good thing: I couldn't get my head around the latest Office and I converted to OO long before I converted to Ubuntu. My wife, who's not a techy by any means, also converted to OO and was glad that she did.

If you have problems with OO, ask on the OO forums! They're just as helpful as on this forum.

> **mal_conductor said:**
> 5)    Can programs written for Windows only run on Linux?  I work with some Windows-only applications.  I have read about WINE and WM but I am still not clear on a few things.
The rule-of-thumb is that Linux is not Windows. If you want Windows, don't convert to Linux.

I love it, but not everyone will.

> **mal_conductor said:**
> 8)    The vendor I want to but Ubuntu from offers a DCROM and a DVD version.  Do these have same or different information?  i.e. The DVD format holds more info therefore I get more stuff or is the same on both?
You went to *buy* Ubuntu? Why? It's free!

Download the CD Live from the Internet. Burn it to CD. Back up your Windows (just in case); then run the CD. Your next step (before installing) is to run the self-check on the CD in case the burn didn't work right.

**Big point...** If you're just wanting to dip your toes in to test the water, then [use WUBI]("http://wubi-installer.org/"). I did that, and I'm so glad I did.

[LIST]
[*]It's by far and away the easiest possible way to try out Ubuntu! (Just install it in Windows as if it were another program. No need to burn a CD.)
[*]It's safe, because there's no formatting or partitioning.
[*]If you don't like it, you just uninstall.
[/LIST]
If you want Ubuntu for casual use, then you'll probably stick with WUBI. If you want to choose to migrate from Windows (as I did), then you'll uninstall WUBI and install Ubuntu from the Live CD.

WUBI's website:
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Vivaldi Gloria on 2008-07-12
```
1) I like to keep minimize software on my hard drive. 
``` 

Ubuntu installs one application per task. It's in their philosophy.

```
2)	Do I still have to “mount” USB ports?!!!!  Why can they just work?!!!! 
```

They automatically mount and they just work bar one thing. When you right click on a usb icon and choose unmount then ubuntu gets the usb stick ready to be unplugged but it does not send the "lights off" signal. So after you choose unmount the light is on on the usb stick but it is safe to unplug anyway.


```
5) Can programs written for Windows only run on Linux? 
``` 

See wine app database [http://appdb.winehq.org/](http://appdb.winehq.org/) to see which programs run in wine.

A windows in VM *IS* a windows installation. So every app runs in it.


```
7)	Why does LTS say it’s supported for 3 years?!!! What happens after 3 years.  Do I have to pay for support, a new version is released, other?
```

It means you get updates for 3 years. Then you should upgrade your ubuntu to a newer version. 

If you mean telephone support from canonical then of course you have to pay. But don't bother with it. Community support is good enough.


```
8) The vendor I want to but Ubuntu from offers a DCROM and a DVD version.  

```

There isn't any difference in the installed sytem. The dvd has some programs in it. So you can install them from dvd rather than installing them from a repository. So it just saves some bandwidth. 

But why bother buying it at all? Download it from

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn it to a cd.

---

### Post by Vivaldi Gloria on 2008-07-12
Also I suggest you download and watch the videos (links below) to get a better feeling for ubuntu. They are for the previous version of ubuntu but still relevant. Especially watch these:

Installing Ubuntu Part 1
Installing Ubuntu Part 2
Tour of the Ubuntu Desktop
Tour of the Ubuntu Applications
Tour of the Places and System Menus
Updating and Upgrading
Installing Applications


These videos are available in different sizes. Goto

[http://screencasts.ubuntu.com/MoS2007](http://screencasts.ubuntu.com/MoS2007)

and the links are on the top right. If you have a fast connection then download the Ogg/Vorbis/Theora - Large videos. They play with vlc player without a problem.

---

### Post by mdsmedia on 2008-07-12
Remember that the answers to your questions here are from users here, and not necessarily experts.

Linux is not Windows, so please don't expect all Windows apps to work in Linux, even in WINE. Lots do, but lots don't too. I'm no expert on WINE, but a lot of programs that some have trouble with have been successfully implemented by others. It can take some playing around and some time and work to get some things working.

Try WUBI and/or use a Live CD to try out Ubuntu before installing. You could try a dual-boot installation, which means installing Ubuntu alongside Windows. I've done that for the last 3 years and I'm studying the possibility of loading Windows in a virtual machine in Linux. There are many options available while you get comfortable with Linux, so you can still run Windows.

There's no need to BUY Ubuntu. Even your local Linux User Group would be happy to give you a copy of Ubuntu.

The DVD contains a lot more packages which are available in the repositories for download. The CD contains the basic install of Ubuntu. Generally people use the CD and then download packages as they require them. The DVD is handy of you don't have internet access or you are limited in access to the internet.

OpenOffice.org is not MS Office. It is compatible with Office and you can open Office documents and save documents in Office formats. It does things slightly differently to Office. The beauty of OOo and other open source projects (including Linux and Ubuntu) is that as updates are available you can get them without having to pay again and again and again for new versions. OOo is continually improving and the improvements are available to you legally and freely.

---

### Post by mal_conductor on 2008-07-12
Thank you all for the incredibly quick responses.

Reply to some of the feed back:

-	Why would I buy Ubuntu?  My ISP charges $10 extra for any thing over 1GB of monthly data transferred.  I come in very consistently clock in at just under 1GB.  If I download Ubuntu I will go over 1GB and it’s actually cheaper to “buy” Ununtu.

I save two dollars, but more importantly the ISP does not get the extra $10.

-	I day trade stocks, and the main reason I want to get away from windows are security and applications keep crashing.  I think it’s because of all the data feeds coming in.  Stock tickers, quotes, market data, radio streaming news etc.  I now use two laptops to prevent applications running on the same box.   I have learned which applications running together make the system crash.

-	The trading software I use is only supported for windows.  If this software does not work on Linux then there is little purpose in migrating my every day to Linux.  The brokers are very closed minded about issuing Linux specific software.

-	Nope, not from the UK, but I love the BBC.  I don’t watch TV but listen to a lot of radio.  CBC mostly (Canadian Broadcasting Corporation) it’s like a BBC who does wonders with a much smaller budget

-	“OO is not MS” “Linux is not Windows”.  This is becoming a cliché, and an easy way out of a discussion.  The reality is that MS is the dominant software out there.  I think the Linux community needs to understand this to help Linux become more mainstream.  There will be discomfort for a few more years, for those who know in their hearts that Linux is better, but one day Linux will debunk Microsoft.  I am living proof; this is my second attempt at running away from the Microsoft shortcomings.  Also, I have little say when my employer decides that Windows and MS Office is the computers are set up at work.
(Disclaimer to MDSMEDIA.  Thank you for a well thought out reply on the “OO vs. MS/Linux is not Windows” topic)

-	MSOffice 2007.  A HUGE step backwards.

---

### Post by aktiwers on 2008-07-12
You can order the Ubuntu CD Free!
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

And it is really free! They also pay for the stamps and everything. I have used it myself, and it works. Only downside is you have to wait between 4-6 weeks properly..

---

### Post by kansasnoob on 2008-07-12
You need only skip to the end:

> 7) Why does LTS say it’s supported for 3 years?!!! What happens after 3 years. Do I have to pay for support, a new version is released, other?

This is a **** message why even reply?

---

### Post by mdsmedia on 2008-07-12
> **mal_conductor said:**
> Thank you all for the incredibly quick responses.

Reply to some of the feed back:

-	Why would I buy Ubuntu?  My ISP charges $10 extra for any thing over 1GB of monthly data transferred.  I come in very consistently clock in at just under 1GB.  If I download Ubuntu I will go over 1GB and it’s actually cheaper to “buy” Ununtu.

I save two dollars, but more importantly the ISP does not get the extra $10.

-	I day trade stocks, and the main reason I want to get away from windows are security and applications keep crashing.  I think it’s because of all the data feeds coming in.  Stock tickers, quotes, market data, radio streaming news etc.  I now use two laptops to prevent applications running on the same box.   I have learned which applications running together make the system crash.

-	The trading software I use is only supported for windows.  If this software does not work on Linux then there is little purpose in migrating my every day to Linux.  The brokers are very closed minded about issuing Linux specific software.

-	Nope, not from the UK, but I love the BBC.  I don’t watch TV but listen to a lot of radio.  CBC mostly (Canadian Broadcasting Corporation) it’s like a BBC who does wonders with a much smaller budget

-	“OO is not MS” “Linux is not Windows”.  This is becoming a cliché, and an easy way out of a discussion.  The reality is that MS is the dominant software out there.  I think the Linux community needs to understand this to help Linux become more mainstream.  There will be discomfort for a few more years, for those who know in their hearts that Linux is better, but one day Linux will debunk Microsoft.  I am living proof; this is my second attempt at running away from the Microsoft shortcomings.  Also, I have little say when my employer decides that Windows and MS Office is the computers are set up at work.
(Disclaimer to MDSMEDIA.  Thank you for a well thought out reply on the “OO vs. MS/Linux is not Windows” topic)

-	MSOffice 2007.  A HUGE step backwards.I agree that the whole "Linux is not Windows" thing is a cliche, but sometimes it needs to be said. I think you have a good understanding of where we're coming from so it sounds like a cliche.....how do you get that little , over the "e" by the way?....

The Linux community DOES understand that MS is the dominant software. Why do you think WINE even exists? The posts were in response to your questions about running MS software in Linux and whether OOo was suitable for your purposes in using MS Office at work. There is no way for us to know what specific things you need to do in MS Office and therefore how they would be done in OOo in comparison.

Try your Windows software in WINE and see if it works. Try working around any problems you might have. Ask questions until you see whether you can/can't use that software in Linux.

I have software which doesn't run in Linux, I'm no expert in using WINE and don't have a lot of time, but gradually I'm learning and migrating more and more to Linux. All the time Linux is my primary OS, but I have to use Windows for some things.

---

### Post by Paddy Landau on 2008-07-13
As running Windows programs is critical for you, you may find PlayOnLinux useful:

[http://wiki.winehq.org/PlayOnLinux](http://wiki.winehq.org/PlayOnLinux)

---

### Post by stalkingwolf on 2008-07-13
You may also find the application Crossoverlinux useful.

---

### Post by Brightbelt on 2008-07-13
Hi, I read through this thread and am not sure if this has been addressed, but I'll mention it just in case....

You can export any Open Office Document in the Microsoft Office format. I know exports are possible in the MS Office 2003 format but I don't think MS Office 2007 exports are possible as yet.

I think this should quell anyone's fears about trying Open Office.

Thanks, Frank B.

---

### Post by yuqin513 on 2008-07-13
[www.Jordan9.com](www.Jordan9.com) discount cheap nike jordan gucci prada shoes lacoste puma trainers at china factory 
Welcome to visit [www.jordan9.com,We](www.jordan9.com,We) are a professional shoes and sneaker Industrialcompany, and as af([www.jordan9.com](www.jordan9.com)) amous nike shoes factory & Stores and wholesale company.([www.google.com](www.google.com)) air force one

---

### Post by Sealbhach on 2008-07-13
> **mal_conductor said:**
>  I think the Linux community needs to understand this to help Linux become more mainstream.  

There are certain barriers in the way - not the fault of the Linux community.

If other software makers keep their source-code hidden - there's not a lot that Linux developers can do about it.

Same problem with hardware vendors.

.

---

### Post by Paddy Landau on 2008-07-13
> **Brightbelt said:**
> You can export any Open Office Document in the Microsoft Office format. I know exports are possible in the MS Office 2003 format but I don't think MS Office 2007 exports are possible as yet.
MS 2007 compatibility is on its way.

There will always be minor (and, occasionally, major) compatibility differences between OO and MS, simply because -- as Sealbhach said -- MS deliberately keeps its format closed. It's not always possible to know just how MS codes its documents.

Theoretically, in the future, this should not be a problem, because MS has signed up to the Open Documents standard (which OO adheres to). However, in practice, as we found out with Java, I wouldn't be surprised if MS "adjusts" its formats to be not-quite-standard. This, and closed formats, are a great marketing strategy for MS, but terrible for the end consumers.

---

### Post by thiebaude on 2008-07-13
Why don't the OP request the free CD from here [https://shipit.ubuntu.com?](https://shipit.ubuntu.com?)

---

