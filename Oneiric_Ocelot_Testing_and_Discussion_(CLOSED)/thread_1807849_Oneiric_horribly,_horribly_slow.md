---
title: "Oneiric horribly, horribly slow"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SveinT on 2011-07-19
Hi,

just tried out Oneiric on my system, and while Natty is a bit slow, Natty is usable in contrast to Oneiric. Oneiric is so slow that the system goes to a crawl after a short while. Opening a terminal window takes about 7 seconds. Opening Firefox maybe twice that, and the system generally doesn't respond much, Weird thing is that there's nothing unusual in top or iotop. CPU is at about 15% and almost no IO. Memory is about 500MB used of 1GB. Invoking a metacity --replace makes the system go very fast, so there's something with Unity acting up. Any ideas for further investigation?

My computer is a Core 2 Duo 1.6Ghz laptop with Intel GMA945 graphics.

---

### Post by fjgaude on 2011-07-19
Sounds like you are disk swapping out. Are you sure the RAM is not being hogged by an application?

---

### Post by sgage on 2011-07-19
> **SveinT said:**
> Hi,

just tried out Oneiric on my system, and while Natty is a bit slow, Natty is usable in contrast to Oneiric. Oneiric is so slow that the system goes to a crawl after a short while. Opening a terminal window takes about 7 seconds. Opening Firefox maybe twice that, and the system generally doesn't respond much, Weird thing is that there's nothing unusual in top or iotop. CPU is at about 15% and almost no IO. Memory is about 500MB used of 1GB. Invoking a metacity --replace makes the system go very fast, so there's something with Unity acting up. Any ideas for further investigation?

My computer is a Core 2 Duo 1.6Ghz laptop with Intel GMA945 graphics.

On my Dual Pentium 2.0 GHz Oneiric is snappy as could be. I wonder what you have going on, because it ain't normal...

---

### Post by Harry33 on 2011-07-19
> **SveinT said:**
> Hi,
...
Invoking a metacity --replace makes the system go very fast, so there's something with Unity acting up. Any ideas for further investigation?

My computer is a Core 2 Duo 1.6Ghz laptop with Intel GMA945 graphics.

Seems to me that the problem is Compiz and 3D.

---

### Post by SveinT on 2011-07-19
The disk swapping seems to be the problem. After testing some more I see (contrary to my first post, I looked in the wrong place) a lot of IO on all applications, especially kswapd0 (99.8% almost all of the time). Right now my memory is filled at 58% (580MB) and swap at 22% (223MB) according to system monitor. Why there's things in swap at all I don't know. The thing is that I have plenty of RAM left when it starts writing to disk like crazy.

Killing a lot of the apps do lessen the problem, which support that it is an memory issue. But still, opening a new web page (normal news site), makes it go 0.5-1 FPS, so basically unresponsive. You could of course say that my computer is insufficient to run Oneiric, but why could I run the same programs on Natty and experience much less of an issue? And if I run metacity things run better as I mentioned (I know compiz use memory, but seriously, is it that bloated?). Unity 2D is even worse, so it's basically unusable, but that's another story...

Thanks for all the quick replies by the way, I'm impressed! :)

---

### Post by collisionystm on 2011-07-19
Oneiric was slow on my machine as well. Just installed / removed it today. Seems to be a good delay in launching applications, and I found several bugs trying to use xterminals. Obviously it wont be stable for quite some time, but it was interesting none the less!

---

### Post by SveinT on 2011-07-19
Ok, did some more testing. I disabled the swap partition (not a long term solution I know) and things run very smooth. So then that's nailed.

As for memory usage, I am indeed out of memory it seems. At least top reports having about 80-60MB left, which is nothing. But the weird thing is taht system monitor, which I've been using without thinking to inspect actual MB usage in top, shows that I'm only using half! Any idea why?

Have a look:
[http://dl.dropbox.com/u/100344/mem_problem.png](http://dl.dropbox.com/u/100344/mem_problem.png)

---

### Post by ajgreeny on 2011-07-19
```
free -m
``` is much better for showing memory use.  System-monitor seems to use a lot of resources, and in my opinion is best avoided if possible.

---

### Post by SveinT on 2011-07-19
I can't believe how fast the system runs now with swap off :) Sadly things get killed if I launch too many things (naturally).

That said, I am wondering whether my system uses an unusually high amount of memory? From cold boot, with no applications running, I am using around 750MB (launching top adds an extra 30?). And I can't seem to account for the applications which are supposed to use this memory. Please see attached picture.

Edit:

After reading up on memory management in linux I understand that this is normal.

---

### Post by ajgreeny on 2011-07-19
You are only using 278MB ram not the 750 as you suggested.  Linux manages ram very differently to windows and keeps things in ram until more is needed or the application is closed.  It works on the principal that empty ram is wasted ram.

The important figure is the +- buffers/cache which is showing the 278 true figure.

---

### Post by fjgaude on 2011-07-19
It would seem you simply don't have enough memory to have many apps loaded all at once. My netbook has one gig and I try to have loaded only the apps I am using at present.

---

### Post by ayates on 2011-07-19
Read  this bug report, I think it's your problem: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

Oops. Wrong video card. Ignore this.

---

### Post by SveinT on 2011-07-20
> **fjgaude said:**
> It would seem you simply don't have enough memory to have many apps loaded all at once. My netbook has one gig and I try to have loaded only the apps I am using at present.

Well, but the thing is, I can do that fine on Windows (even Vista!) or earlier versions of Ubuntu. So something's not as it's supposed to  be I think. Also we're not talking many applications here, but having a couple of browser windows open.

Also I'm wondering then, seeing the memory explainations from last page, why it starts swapping when my memory is half full?

---

### Post by fjgaude on 2011-07-20
Swapping, yes... there is something wrong... don't know what to suggest other than a fresh install. And of course, wait as updates come.

---

### Post by tekstr1der on 2011-07-20
> **ajgreeny said:**
> Linux manages ram very differently to windows and keeps things in ram until more is needed or the application is closed.  It works on the principal that empty ram is wasted ram.

Window operates on the exact same principle FYI:

[[img]http://s3.postimage.org/adgqt5c4/freemem.jpg[/img]](http://www.postimage.org/)

---

### Post by jerrylamos on 2011-07-20
Well I just added Lucid Lynx LTS because Oneiric Grub2 keeps screwing up the boot menu choices, even sticks in entries for partitions long since deleted.

Lucid LTS jumps!  Oneiric Ocelot O.K., a bit slower on downloads & updates.  All this is on my test pc's, a netbook, a notebook, and a fast tower.

Compiz overhead on Unity 3D is certainly measurable even when I'm running full screen applications which don't need any shading or 3D or anything else Compiz does.

I do have Unity 2D Oneiric Ocelot on a notebook that won't do 3D.  I have no measurements but my feel is 2D is definitely more crisp than the shading fading overlapping whatever that Compiz does.

I do run Oneiric Ocelot "out of the box" because that's what I'm testing, what most future Ubuntu users will see.

Jerry

---

### Post by ubername on 2011-07-20
Hmm...

I was going to suggest using swapd, which dynamically creates a swap file when you need one, but I note from the man pages 
[http://manpages.ubuntu.com/cgi-bin/search.py?q=swapd](http://manpages.ubuntu.com/cgi-bin/search.py?q=swapd)
that it isn't available for Oneiric, which makes me think STUFF must be happening to the way swap is managed.

---

### Post by SveinT on 2011-07-23
I just reinstalled Natty as Oneiric wasn't usable, and the change is just incredible. Natty is literally flying compared to Oneiric, everything responds at once and I experience very little lag.

So of course that's a good thing, but I am now worried what's wrong with Oneiric and whether it will be fixed for the official release. Memory usage is much less after boot in Natty, so I guess that's where the performance increase comes from.

---

### Post by garvinrick4 on 2011-07-23
I am having the gnome shell difficultys as expected but Unity runs like a dream for me.
And firefox the difference between 10.04 and 11.10 is unbelievable the jpegs and page
in general are just beautiful, sharp and crisp. I use Unity as my
main interface, I like using key commands as much as possible. 
## If anyone is short on RAM, like 150 meg to a gig maybe less. You should give lubuntu a shot and LXDE. 
Set it up right and you can use web, play music on radio and open whatever you want and I never get 
over 350 meg of Ram usage and I like it. Make top panel, bottom panel, side panel or any combination of. 
Not to many key commands to learn and quick, fast and lean. Running 3.0 rc7 kernel gives me better iwlagn driver.
## Have not had any speed problems in any 11.10 interface but do have plenty of RAM
and dual core processor. I imagine running Flash will use all of older cpu's resources and
RAM is RAM more the better.
## Going to go out on a limb and say older processors and short RAM will make some of
the newer versions of gnome interfaces slow a machine down with flash running everywhere
and lots of Apps open.

---

### Post by svegress on 2011-09-29
Same problems with the speed of Oneiric beta 2.  
Although it is getting more stable with each daily release, it is getting horrifically slow/
I did go from 60 to 10 on the swappiness which seems to have  stopped the disk led from being an almost continuous glow.
 Running Firefox is just passable but add Thunderbird and the performance tumbles. Then add LibreOffice and your are waiting minutes for key strokes to register---and don't even think about Gwibber--that can take over an hour.  
Meanwhile, the start-up menu where I use to be able to change to 2D has disappeared and if I leave the machine for a few minutes and the screen saver kicks in, it won't revive and I am forced to reboot.

Hoping that all this is cleared before the release because Oneiric is functionally superior to any other version.

---

### Post by LinuxFan999 on 2011-09-29
1 Gigabyte is not very much memory when running Ubuntu 11.10 + Unity. Try upgrading it to at least 2 Gigabytes.

---

