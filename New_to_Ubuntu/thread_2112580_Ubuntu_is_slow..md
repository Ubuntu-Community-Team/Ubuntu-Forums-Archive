---
title: "Ubuntu is slow."
date: 2013-02-05
forum: New to Ubuntu
---

### Post by DaveGiant on 2013-02-05
I have a good computer and Windows 8 is lightning fast. Ubuntu is sluggish. It takes a second or so to display the search box when I press the windows key. If I start up the computer and do the following.

Windows Key -> Spot -> Enter [Launch Spotify]
Press Skype Icon in Dock
Press Chrome Icon in Dock

It takes about 5+ seconds to launch everything. On windows it takes like 1 second.

Now.. Windows8 is installed on an SSD but all Windows apps are on a standard HDD so I don't understand why general system performance is so slow compared to Windows.

Does anyone have any ideas?

---

### Post by LiamOS on 2013-02-05
Is it a full install on the hard drive?

---

### Post by DaveGiant on 2013-02-05
Yes. I put in the disc, rebooted my computer and ran the installation. it isn't running from a live CD.

---

### Post by Filipek on 2013-02-05
> **DaveGiant said:**
> 
Now.. Windows8 is installed on an SSD but all Windows apps are on a standard HDD ...

Maybe a silly question but does that mean that the Ubuntu installation is not on SSD drive? That would explain quite a lot.

---

### Post by snowpine on 2013-02-05
A few suggestions in no particular order:

1. Check you have correct graphics drivers installed.
2. Use lightweight [Xfce desktop]("http://www.psychocats.net/ubuntu/xfce").
3. Install [preload]("http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html")
4. Switch to [a faster distro]("http://distrowatch.com/dwres.php?resource=major"). (I personally use & recommend Debian.)
5. Use the "lightning fast" Windows 8.

---

### Post by 3rdalbum on 2013-02-05
The Unity Dash uses semi-transparency which requires decent 3D.

What graphics card do you have, and have you installed a proprietary driver for it?

Also, check System Monitor to be sure that there's no buggy program in the background eating your CPU time.

As a measure, the first time I open the Dash it probably takes a second or so to open and fill up. Subsequent times, it's about a quarter of a second; near instant. This computer is a Core 2 Duo with Nvidia GTX260 on the proprietary Nvidia driver. One hard disk for programs, the other for files; no SSD.

---

### Post by DaveGiant on 2013-02-05
> **Filipek said:**
> Maybe a silly question but does that mean that the Ubuntu installation is not on SSD drive? That would explain quite a lot.

Could you elaborate please.

Ubuntu runs worse on my £1k 6/mo desktop PC than Windows 7 runs on my 2 year old £300 netbook... 

I was expecting Windows 8 to run faster than Ubuntu as that occupies the SSD but Ubuntu isn't just slower. It is unacceptably slow.

I would say performance is equal, perhaps marginally worse than my 6 year old iMac.

---

### Post by offgridguy on 2013-02-05
I haven't found ubuntu to be very fast on any computer, so i mainly use Lubuntu,
much faster.

+1 to the reply by snowpine.  I also have windows 8 on an SSD laptop, Very fast.

---

### Post by Warren Hill on 2013-02-05
There are two key points here

1.  Windows on SSD, Ubuntu on HHD
     Solid State drives are much faster than Hard Disk Drives

2.  The desktop.
     The default Unity desktop is not particularly fast.  Ubuntu does not promote its self as being a particularly 'fast' distribution.

If you want a light weight fast distribution take a look at xubuntu.

You could try it on a live CD.  Download is here
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

If you like it there is no need to do a full install.  Just change the desktop see here:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by TheFu on 2013-02-05
MS-Windows has an area called "Prefetch" where it stores often used programs. This is on your SSD, so the fact that programs are installed elsewhere really doesn't matter, the prefetch is on the SSD too.

SSDs are vastly quicker than spinning disks.  If you want a far comparison, create a 10G partition on your SSD and install Ubuntu there.  Please /home on the spinning disks, but put the main OS on the SSD partition.  You will be surprised at how much quicker Ubuntu is over Windows.

If you want to see the fastest GUI on Linux, try **TinyCore**.  It will blow away any version of Windows on any hardware.  **TinyCore **with a GUI is small - 12MB last time I checked. It is great for special use needs, like online banking where only a web browser is needed. It doesn't have every program available that Ubuntu does, but the most popular 100 programs or so are available.

---

### Post by varunendra on 2013-02-05
Nice info there TheFu, the prefetch being on SSD maybe a factor.

However, I'm more inclined towards *snowpine* and *3rdalbum*'s suggestion about graphics driver. One bad driver can make everything crawl.

The current driver for graphics can be confirmed by -
```
sudo lshw -C display
```

All the drivers currently in use can be listed by -
```
lsmod
```

---

### Post by SailorTears on 2013-02-10
i suspect it is a design flaw in Ubuntu. don't really know.

---

### Post by TheFu on 2013-02-10
> **SailorTears said:**
> i suspect it is a design flaw in Ubuntu. don't really know.

Calling something a *design flaw* is harsh. I don't know the details of the design.  The fact that some people have great results tells me that it is not a design flaw. Perhaps just an installer issue or a bug in the specific setup/drivers on the OP box.

Ubuntu is not Unity.  Unity is just a new-ish GUI that is not mature when compared with other available GUIs. Should it be the default GUI installed?  That is a different question.

Ubuntu performs much faster than Microsoft OSes since NT4, IME, provided I don't use Unity.  A slow GUI can be replaced - EASILY - in Linux.  Having an easily replaced GUI with many options available seems like a very smart design choice to me.

---

### Post by drawkcab on 2013-02-10
This sounds like an issue with your video card not having the proper drivers installed.

---

### Post by leclerc65 on 2013-02-10
> **TheFu said:**
> MS-Windows has an area called "Prefetch" where it stores often used programs. This is on your SSD, so the fact that programs are installed elsewhere really doesn't matter, the prefetch is on the SSD too.

Is Preload the same ? I always have it installed first for every new installation.

@OP: I would install Mint Maya Mate (if you don't like Lubuntu or any of the XFCE) on the SSD. If you don't store anything in /home, the install should take about 6, 7G at most. Follow the tweaks here

[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

My system is really flying. The backup is extremely fast too (sub 5 min with Clonezilla). Yes, there are ways to put Thunderbird, Virtualbox ... to the HDD too. My Home folder takes about 600M only. I did this to save wear and tear on the SSD, but I can't believe my eyes of the before/after of the performance improvement with the SSD.

---

### Post by drawkcab on 2013-02-10
Preload is rad, especially on an ssd.

---

### Post by SailorTears on 2013-02-11
> **TheFu said:**
> Calling something a *design flaw* is harsh.

Yes, it is harsh. And I meant it to be be harsh.

I started a redundant thread on this subject, and I have a lot of suggestions on how to cope with this. And I had not considered this before joining this forum but now I am considering a different distro of Linux.

I am running this puppy on a Pentium 4 with a heartbeat of 3.6 gHz - that is 3.6 BILLION times a seconds. And I have 512 mB of RAM - half a BILLION!. I expect bloatware from Microsoft and apologies and justification for that bloatware but I was hoping for so much more from Ubuntu.

As for the distinction between Unity and Ubuntu, I am dual booting WinXP and 12.04 from the same hard drive and all things are equal, all choices default. And is the what I will continue to base my comparisons. Why is a GUI installed that chokes my system as a default?

And least I be considered a troll, I do not plan to post any more on this subject, unless specifically addressed and have something new to say.

Mostly, I am disappointed.

---

### Post by MadmanRB on 2013-02-11
well one thing to keep in mind is that in the end unity is still kind of experimental.
No one is forcing you to use it, its just that Ubuntu and Canonical has its own goals of what it wants to do differently then windows.
Which is both a good and a bad thing.

---

### Post by snowpine on 2013-02-11
> **SailorTears said:**
> I am running this puppy on a Pentium 4 with a heartbeat of 3.6 gHz - that is 3.6 BILLION times a seconds. And I have 512 mB of RAM - half a BILLION!. I expect bloatware from Microsoft and apologies and justification for that bloatware but I was hoping for so much more from Ubuntu.

Here's a chart showing where your 3.6 BILLION pentium 4 CPU stands compared to modern hardware:

[http://www.cpubenchmark.net/common_cpus.html](http://www.cpubenchmark.net/common_cpus.html)

I suggest you do some reading on Moore's Law before you get angry at Canonical that your computer is getting 12 months older each and every year:

[http://en.wikipedia.org/wiki/Moore%27s_law](http://en.wikipedia.org/wiki/Moore%27s_law)

Anyway, you've received **specific advice to help Ubuntu run faster** from experienced forum members, which you chose to ignore/dismiss with "must be a design flaw..."

---

### Post by bantuvez on 2013-02-14
> **TheFu said:**
> MS-Windows has an area called "Prefetch" where it stores often used programs. This is on your SSD, so the fact that programs are installed elsewhere really doesn't matter, the prefetch is on the SSD too.


No. Since Windows 7 prefetch is disabled on SSD drives. On SSD drives prefetch is almost useless, it only reduces SSD lifetime.

---

### Post by tgalati4 on 2013-02-14
I'm running Linux Mint MATE 14 on 4 different machines:  2 laptops, 2 desktops, old and new.  It runs fast in all 4 cases--4 different CPU's, 3 different graphics chips, 2 to 4GB of RAM in all the machines.  32-bit and 64-bit.  I'm satisfied.  

Use the distro that works for you.  If there isn't a simple fix for your performance issue, then choose a distro that runs better on your hardware.  After all, the desktop environment normally just gets in the way of you trying to do something.  It sounds like 5-second load times fits in that category.

---

### Post by oldfred on 2013-02-14
Someone posted this for newer Intel.

       For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

    
I use gnome-panel or fallback on both my laptop with 1.5GB of RAM and my desktop with 4GB RAM and newer SSD. My laptop takes longer to boot and occasionally uses swap if I try to start too many apps at once. But both systems run very quick for 6 year old systems.

---

