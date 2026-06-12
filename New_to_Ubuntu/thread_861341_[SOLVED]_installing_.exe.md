---
title: "[SOLVED] installing .exe"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by cgault9 on 2008-07-16
is it possible to install .exe files on ubuntu? if so what package managers or programs/settings need to be in place to do so?

---

### Post by snowpine on 2008-07-16
> **cgault9 said:**
> is it possible to install .exe files on ubuntu? if so what package managers or programs/settings need to be in place to do so?

Yes, you can use a program called Wine to install many (but not all) Windows applications.

We have an entire sub-forum dedicated to Wine, check it out!
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by OffAxis on 2008-07-16
and here's the community docs for it:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by OutOfReach on 2008-07-16
You can download WINE [here]("http://www.winehq.org/site/download-deb") , just follow the instructions

---

### Post by rockin_goliath on 2008-07-16
While you can install .exe files with Wine, which is a "Windows emulator", I would not recommend it, simply because you can Wine is unstable, may not work with the particular application you want to install, and is generally just overkill for the task at hand.

Perhaps you can tell us the name or the nature of the program you want to install? The Ubuntu repositories are full of a bunch of great applications that can usually fit the bill. Most o the popular Windows applications have open source replacements that run in Ubuntu (Photoshop - The GIMP, Microsoft Outlook - Evolution Mail, etc.) Unless you have a program that does something really specific, check the repositories first.

I'll give you an example. I used to use a flash card program called Stash, which was originally written for Windows 3.1. since it was so old, it ran pretty well in Wine, but it took forever to start, and I had to go through this huge process every time I wanted to install it. When I decided to browse the repos for an alternative, I found Kwordquiz, which I found to be leaps and bounds better.

---

### Post by halitech on 2008-07-16
never mind, got you confused with another user I was helping with wireless problems

---

### Post by fatality_uk on 2008-07-16
> **rockin_goliath said:**
> which is a "Windows emulator"
WINE stands for **Wine Is Not an Emulator**
In most cases, WINE is stable. As of the point 1 release, it is even more so. It has been in development since about 1993

You are correct in saying that it may not work, but a link to [http://appdb.winehq.org/](http://appdb.winehq.org/) will soon allow the OP to find out.

---

### Post by cgault9 on 2008-07-17
> **rockin_goliath said:**
> While you can install .exe files with Wine, which is a "Windows emulator", I would not recommend it, simply because you can Wine is unstable, may not work with the particular application you want to install, and is generally just overkill for the task at hand.

Perhaps you can tell us the name or the nature of the program you want to install? The Ubuntu repositories are full of a bunch of great applications that can usually fit the bill. Most o the popular Windows applications have open source replacements that run in Ubuntu (Photoshop - The GIMP, Microsoft Outlook - Evolution Mail, etc.) Unless you have a program that does something really specific, check the repositories first.

I'll give you an example. I used to use a flash card program called Stash, which was originally written for Windows 3.1. since it was so old, it ran pretty well in Wine, but it took forever to start, and I had to go through this huge process every time I wanted to install it. When I decided to browse the repos for an alternative, I found Kwordquiz, which I found to be leaps and bounds better.

Wine worked great for installing my hypothetical torrent program however my original issue was with installing Windows Media plyr 11. I have since tried it with wine but am not able to install it since I cannot 'Validate' my copy of windows.. Is there a way around this? Or is WMP11 simply not compatible.. mind you I am new to this :)

---

### Post by eentonig on 2008-07-17
Is it possible? Yes it's possible.

Is it wise, best idea? No, I wouldn't recommend it. When I first started using Linux, I explored the Wine route myself and got utterly frustrated with 'how poor Linux was designed' and how much effort it took to get the most stupid programs to work on it. Later on, I realised that I was appraoching this from the wrong angle. 

In stead of porting my familiar windows apps to this new Linux environment, it's smarter, easier, more stable to analyse why you want that window program. And then ask/search/check if there are native Linux programs available that suit your needs.

---

### Post by nothingspecial on 2008-07-17
You don`t need wmp to stream media with Ubuntu.
Use mediatomb, search in synaptic.

ps it`s not the done thing to have 2 threads on 1 subject simultaneously. ;-)

---

### Post by cgault9 on 2008-07-17
> **nothingspecial said:**
> You don`t need wmp to stream media with Ubuntu.
Use mediatomb, search in synaptic.

ps it`s not the done thing to have 2 threads on 1 subject simultaneously. ;-)

noob remember :)
thanks guys



{edit}

i was also trying to install an .msi file for logmein so I can access my pc from work, when I tried with wine the installation went fine until I received a "LogmeIn encountered an error, Installation ended prematurely."  Is this simply an unavoidable compatability issue?

---

### Post by JoshuaRL on 2008-07-17
> **rockin_goliath said:**
> While you can install .exe files with Wine, which is a "Windows emulator", I would not recommend it, simply because you can Wine is unstable, may not work with the particular application you want to install, and is generally just overkill for the task at hand.

Perhaps you can tell us the name or the nature of the program you want to install? The Ubuntu repositories are full of a bunch of great applications that can usually fit the bill. Most o the popular Windows applications have open source replacements that run in Ubuntu (Photoshop - The GIMP, Microsoft Outlook - Evolution Mail, etc.) Unless you have a program that does something really specific, check the repositories first.

I'll give you an example. I used to use a flash card program called Stash, which was originally written for Windows 3.1. since it was so old, it ran pretty well in Wine, but it took forever to start, and I had to go through this huge process every time I wanted to install it. When I decided to browse the repos for an alternative, I found Kwordquiz, which I found to be leaps and bounds better.

I have to disagree with some of this.  Wine is now pretty stable, as it is running on 1.0.  After 15 years in beta, it is now considered by the developers and most users to be stable.  As stable as a program trying to emulate another OS's APIs can really be.  The only other option if you need a specific application for some reason is running a virtual machine, and I would consider that to be the real overkill.

> **fatality_uk said:**
> WINE stands for **Wine Is Not an Emulator**
In most cases, WINE is stable. As of the point 1 release, it is even more so. It has been in development since about 1993

You are correct in saying that it may not work, but a link to [http://appdb.winehq.org/](http://appdb.winehq.org/) will soon allow the OP to find out.

Yep, check the database.  But also, give it a chance.  Some maintainers don't update their applications enough (read: me too.)  But Wine is now considered an emulator.  A couple years ago they added some functionality and it became one.  But they still would you rather call it a compatibility layer instead of an emulator.  After all, usually emulators are piggish things, and Wine is quite excellent.

> **eentonig said:**
> Is it possible? Yes it's possible.

Is it wise, best idea? No, I wouldn't recommend it. When I first started using Linux, I explored the Wine route myself and got utterly frustrated with 'how poor Linux was designed' and how much effort it took to get the most stupid programs to work on it. Later on, I realised that I was appraoching this from the wrong angle. 

In stead of porting my familiar windows apps to this new Linux environment, it's smarter, easier, more stable to analyse why you want that window program. And then ask/search/check if there are native Linux programs available that suit your needs.

Agreed.  First off, try the Linux alternatives.  In many cases, they are better than their Windows versions.  I would suggest AmaroK, Banshee, and Listen instead of WMP.  Also, check out VLC for movies.  It is really nice.

Welcome to Ubuntu!

---

### Post by cgault9 on 2008-07-17
the only problem I have with these alternatives is that I will not be able to use the SYNC feature which is necessary (Thanks to Xbox) to set up a connection between my PC and my 360. This virtualbox or VMware idea that I keep seeing in numerous places sounds interesting, simply, how would one go about doing that and run Microsoft XP in the VM? I currently have my HD partitioned and have both OS' installed so I can tinker around with ubuntu before making the full commitment, would this effect either OS negatively?

---

### Post by nothingspecial on 2008-07-17
Sir, I`ve consulted my good friend google about your xbox issue and she suggested that you try this -

[http://ubuntuforums.org/showthread.php?t=794489](http://ubuntuforums.org/showthread.php?t=794489)

Hope it helps

---

### Post by Sef on 2008-07-17
Locked. [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=861311").

---

