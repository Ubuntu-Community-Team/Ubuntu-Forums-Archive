---
title: "Compatibility issues with Xubuntu+Radeon 7770?"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by doom-ws508 on 2013-09-09
Hey, I'm a new Linux user who's switched over from windows a little while ago. Since I made the jump though, one thing that sadly nobody told me about, struck me pretty hard:
It's not *easy* to fix problems on this OS.
You apparently have to rely on the community.
But the thing is, from my current observation; Said community never agrees on anything ever.
There isn't a clear solution to anything.
Now I know that this is normal, and that being an ex-windows user this takes some getting used to and whatnot... But I can't get to fix anything but simply doing research.
So I figured I would have to start... *shivers* actually asking people, to see if I could get some sort of consensus on the issue at hand..

It's a little bit disorienting to have to actually write about issues in detail instead of just ''looking it up'' and being done with it. 
So forgive me if I'm unclear, this is pretty foreign to me.

Here goes;

So... I've been exclusively a windows user for my entire life, but altough it has served me well many a times,
I've sort of grown tired of this relationship between him and me. Windows is my drunk husband who despite being a complete mess somehow manages to bring food to the table.

Well I've had enough of that, and decided to make the jump to GNU/Linux.
I've installed mint 15 (dual boot alongside win7, in case I decided to chicken out) on my laptop 2 weeks-ish ago, 
and altough the wireless connection is having a bit of a tough time (which is apparently a common issue), I'm pretty okay with it. 
Familiar enough, about as easy to organize as windows, but most importantly: Fast.

So, filled with good intents and hopeful thoughts I decided to go for it on my desktop too.
It's a gaming desktop, but I wasn't really using it anymore (consoles took over me...), so I thought maybe installing a new OS would make me dust it off and start gaming again.
I wanted to use it mostly for gaming (most games I play happen to be linux compatible) and maybe some quick browsing, and some recording too (guitarist), with perhaps some
movies thrown in there.

But after quite a few bumps in the road I think I've realised I don't know what I'm doing...

I installed Xubuntu 12.04 on it and I've been having quite a few issues since.

(Well here's a good spot for the first question; When I installed Xubuntu, I first wiped out all of my partitions (the original windows ones) by simply
''deleting'' them one by one in Gparted, so as to have a partion-less disk to install xubuntu on.
Did it really erase everything (files etc.) or was I suposed to use some other software to actually empty said partitions and start off with a disk that's basically as brand new?)

The major issue is that I get a lot of weird visual glitches.
Ranging from some text stretching out to cover the entierty of my monitor for a split second,
to images just dissapearing for a second, and sometimes just the entire screen or huge undefined parts of it flashing black or white.
Sometimes even the screen getting dim, as it does when the screensaver is about to come up, but then never getting back to normal lighting no matter what. 
I have to reboot to get it back to normal.
These issues happen at random, no matter what I'm doing or if I'm even touching the computer at all.

Here's one I managed to catch before it went away
[http://postimg.org/image/gcb78lzm9/](http://postimg.org/image/gcb78lzm9/)
The page open on firefox apparently decided to stretch out and merge with my Steam window...

Also, and this lead me to putting the graphics card at fault;
When I try to launch a game on steam (TF2 for instance) I get an error message telling me I have to update Open GL. Could that have something to do with it too?
[http://postimg.org/image/ma5rkplnx/](http://postimg.org/image/ma5rkplnx/)

I've done a bit of googling and it seems as though the problem could stem from my graphics card, which has some known driver compatibility issues (see specs)
But I'm not exactly sure if I have the right driver installed/how to find and install the appropriate one.

Messing around with those: [http://postimg.org/image/x7kd7te0n/](http://postimg.org/image/x7kd7te0n/)  seems to be the only thing I'm able to do.


I tried different ones from the list, but the glitch problem seems to come back no matter what.

Switching around the drivers, at some point I got the game (TF2) to work, but it was incredibly slow and laggy and I couldn't move. So no real improvement there.


So. Instead of keeping on messing around with drivers, not really aware of the impact of the changes that I make to my system, I thought I might as well come here and ask:
What should I do?
Is there a solution to this? Google gives quite a hefty bit of results when searching for info related to Ubuntu's problems with ATI cards, so I thought this would have a clear simple fix.
Or heck, is there a distribution that would be more appropriate for my type of usage, and perhaps be more compatible/stable according to my specs? 
As I said it would be mostly for gaming and basic stuff (watching videos, browinsg etc.)
Altough the programming side of thing fascinates me, I'm not up for the challenge yet. The less I touch the terminal, the better I feel, for now.



Any help is greatly appreciated.
Any additional advices, things I should do first, compatibility issues you know about, extra info, just pour your heart out.
Anything that could help a newbie.
Really.

If *anything* in my post is unclear, please tell, I'll reply with clarifications quickly. 
If you want me to run anything for additional info (like produce html version of my complete specs)
go ahead and ask!


specs:

GA-970A-D3 Gigabyte motherboard

AMD FX(tm)-8120 Eight-core processor

ATI Radeon HD 7770

8GB RAM

RTL8111/8168B PCI Express Gigabit Ethernet

ST33000651AS Seagate 3TB HDD

Antec 620 Power Supply

---

### Post by sena-akada on 2013-09-09
AMD's Catalyst drivers have always been rather poor & buggy on GNU/Linux. I'm currently using a Radeon 6670, and the driver installed through 'Additional Drivers' has been surprisingly solid however, except with Steam. After reading the Steam forums, it appears that about 70-80% of the issues there are posted by people with AMD graphics hardware. 
The easiest & simpliest recommendation I could make would be to switch to a Nvidia based graphics card. Their drivers on GNU/Linux are pretty much on par with Windows in terms of both reliability and speed. If you are serious about switching to Linux, Nvidia is generally considered the way to go! : )

---

### Post by doom-ws508 on 2013-09-09
Uhmmm...
Well are there people working on solutions for this? If there's a workaround for this coming soon I might avoid spending a hundred dollar on a card I might not need

---

### Post by sena-akada on 2013-09-09
Well they are known for being very slow to fix issues and support newer kernels and x.org releases. Linux isn't like Windows sadly, Nvidia's drivers ARE superior on Linux compared to AMD. In 5 years of using Linux I've tried the following AMD cards on Linux; Radeon x1650 Pro, Radeon Xpress Mobility X1200, Radeon 2600 XT, Radeon 3870 x2, Radeon 4870 x2,  Radeon 5570, Radeon 6670. ALL of them except the 6670 (although it has some pretty bad issues with certain Steam games that make them unplayable) have had major issues when using the Catalysts drivers. On the other hand, using various Nvidia cards I've only ever had 1 issue, where for some reason a Nvidia ION won't find my monitors resolution over HDMI, but will over VGA.   

IF you are serious about using Linux as your OS, I really can't stress enough the general difference between the quality of Nvidia's drivers over AMD's. AMD's will most likely leave you wasting hours trying to find fixes for things that you most likely won't be able to.

---

### Post by doom-ws508 on 2013-09-09
Would a good compromise be to install windows on its own small partition, solely for gaming, and linux on the rest of my hard drive for all other purposes? Windows 7 didn't seem to have any problems, I could play pretty much every game. And if so, what distro would you recommend according to those specs, but removing gaming from the equation? Are there any chances this compatibility issue causes me trouble elsewhere than on steam at some point? (As you can see, still not so keen on the idea of buying a new Nvidia card ;P)

---

### Post by sena-akada on 2013-09-09
You have a pretty powerful PC (I only have - AMD FX 4100, 4GB 1333HZ DDR3 RAM, and an XFX Radeon 6670), so you could pretty much run any version. I would stick to Ubuntu based distrobutions however, as others like Fedora/Debian/OpenSuSE etc can be overcomplicated. You could give  Elementary OS a try  [http://elementaryos.org/ ]("http://elementaryos.org/"). It's based on Ubuntu and it's kind of like a cross between Mac OSX and XuBuntu. If you don't want to buy a Nvidia card then yes, installing Windows to play games is by far the best idea. AMD's Windows drivers are generally ok.

P.S. Apart from the Steam issues, I've had no other problems with the post-release driver installed through 'Additional Drivers' in System Settings.

---

### Post by doom-ws508 on 2013-09-09
Alright then, I'll try this. I supose this thread isn't so relevant anymore, so, quick little question before I let it drift off into oblivion; any tips about partitionning? (You can just throw a link to a good tutorial with visuals if one comes to mind, if not I'll be on my way googling)
In any case thanks for the advice!

---

### Post by sena-akada on 2013-09-09
I would format the hard disk, install Windows 7 (have fun with all those incredibly slow to download & install updates : P), then install whichever Linux afterwoods.

---

### Post by BlinkinCat on 2013-09-09
Hi,

Here is some reading info -

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

Don't let that stop you from looking elsewhere as well.

Good luck.

---

