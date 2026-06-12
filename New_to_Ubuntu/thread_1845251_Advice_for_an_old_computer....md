---
title: "Advice for an old computer...?"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by labyangel on 2011-09-16
The pc I was using died so I pulled an old system out of my closet. It has an Intel d845glad motherboard, processor is a Intel Celeron Pentium 4 2.00 ghz and 128 mb ram. I'm willing to upgrade the memory if it will be worth it. I want it mostly for internet and watching hulu and netflix. 

I wanted to know if it was powerful enough to stream video and what version of linux would be best for it.

---

### Post by kr0n1x on 2011-09-16
> **labyangel said:**
> The pc I was using died so I pulled an old system out of my closet. It has an Intel d845glad motherboard, processor is a Intel Celeron Pentium 4 2.00 ghz and 128 mb ram. I'm willing to upgrade the memory if it will be worth it. I want it mostly for internet and watching hulu and netflix. 

I wanted to know if it was powerful enough to stream video and what version of linux would be best for it.

I think you would have problems even with Xubuntu (which is the Ubuntu for old hardware systems).
Streaming websites (like youtube) use flash player... which at the moment is slow also on normal systems :lolflag:
Also, old RAM costs more than the current versions...

But trying doesn't hurt:P Try Xubuntu (download the alternate version, it has no gui during the installation but maybe it's necessary due to your low memory). Pay attention when you select the partitions... backup your important data :)

---

### Post by Joreus on 2011-09-16
Just a heads up about the Netflix and Hulu. I'm fairly certain you will be unable to watch them. I know Netflix flat out won't support a machine not running Windows or Mac OS.

As of yet I know of no work around for this.

---

### Post by haqking on 2011-09-16
You wont be watching netflix unless you install a virtual machine with Windows etc

And for virtualisation you would need more RAM again and improved graphics .

There are plenty of Distros which you can get to run on it though.

most will run if you dont add a DE/GUI to it ;-)

---

### Post by walt.smith1960 on 2011-09-16
I would definitely recommend a memory upgrade. Here is what your system takes:
[http://www.crucial.com/store/listparts.aspx?model=D845GLAD&Cat=RAM](http://www.crucial.com/store/listparts.aspx?model=D845GLAD&Cat=RAM)
As kr0n1x says, new old model memory costs more than the same thing in current production machines.  if you're feeling lucky, you can look on Ebay for DDR memory.  It looks like you could hold upto 2 Gb. although 1 Gb. would likely work okay for what you're wanting to do.  It looks like you need PC-2700 non-ECC desktop (not laptop or SODIMM) modules.  If you go the Ebay route, make sure 1) you can return the memory if it fails memtest 2)have a copy of memtest86 available.  It's found on most Linux LiveCD's among other places. Let it run for at least a couple hours, more is better.

I had a desktop machine that was an AMD but similar to your machine.  It worked okay for normal web browsing but certain sites that featured Flash videos like sports sites -ESPN, NFL team sites etc- would bring it to its knees. 1 Gb. memory was plenty but the CPU would run 90%+ with an ATI Radeon 9500 GPU. I think flash has gotten somewhat better on Linux so I'll leave flash performance on that vintage machine to those running a similar machine today.

---

### Post by kr0n1x on 2011-09-16
Also check this forum section: [http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

You could find a better Ubuntu version or even other distro for this purpose.

---

### Post by Frogs Hair on 2011-09-16
Here a couple of distributions that I think will run on your current system , but they won't get you Netflix . 

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

---

### Post by heyho on 2011-09-16
I've revived plenty of systems with used ram from ebay.  It's as cheap as chips (pun intended), as nobody wants 256 modules.  Even with "only" 512mb, you should have no trouble running lubuntu or xubuntu at reasonable speed.

---

### Post by abnordude on 2011-09-16
I think an lxde environment would do.

Why not try lubuntu.

Or as said earlier, use puppy linux.

---

### Post by Rex Bouwense on 2011-09-16
Agree with abnordude.  Lubuntu is probably the way to go with as much RAM as the system will take.

---

### Post by kmsalex on 2011-09-16
+1 for lubuntu 128 mb ram will be plently with a gb swap partion. xubuntu hardly feels like a "light distro anymore"

---

### Post by spcwingo on 2011-09-16
If I'm not mistaken, ChromiumOS supports Netflix natively.

[http://chromeos.hexxeh.net/]("http://chromeos.hexxeh.net/")

---

### Post by lykwydchykyn on 2011-09-16
I'll agree with the RAM sentiments, and add that if you're using the onboard video you might have trouble.  Intel 845 graphics don't do well with the Linux intel driver, usually.

If you have choppy or lo-res video, see if you can pick up an old video card cheap.

---

### Post by Blasphemist on 2011-09-16
This is the sweetest lightweight distro I've seen and it is buntu based. [http://www.bodhilinux.com/](http://www.bodhilinux.com/) I do think there will be the limits already discussed no matter what distro but I like this one.

---

### Post by I2k4 on 2011-09-18
Another vote for Lubuntu, though I'd go with version 10.10 rather than 11.04, as I found the latest much slower and more resource demanding.  

Unfortunately, Lubuntu comes with experimental "Chromium" browser that simply doesn't work on some sites and caused me grief installing Flash.  Best to install either latest FireFox or the stable or beta versions of Chrome - the nice thing about Chrome is it comes with Flash preinstalled. 

Finally, if the system came with only 128mg of RAM, be very careful to confirm exactly what RAM modules it will take.  It may be you are restricted to either 256mg or 512mg of RAM - you can run online streaming video but not at Hi Def.

---

### Post by labyangel on 2011-09-19
Thanks for all the replies. So far the only ones that have worked are damn small linux and puppy. I still need to get the internet working on them. I haven't had the time or patience to figure it out yet.

---

### Post by BBQdave on 2011-09-20
Debian 6 works well on an old desktop of mine: AMD Athlon XP processor with 256 mb of ram.

I run Debian 6 on my laptop (dell inspiron 1100 with 1 gig of ram).  Older processor, but the gig of ram makes it a great system.  So if you can add ram, that will help increase your Linux distro choices.

I am checking out [Edge corp]("http://www.edgetechcorp.com/") to purchase ram for my old desktop.  They seem inexpensive, but I have never purchased from them before.  [Newegg]("http://www.newegg.com/") is inexpensive, and the ram I purchased from them works fine.

As previously posted, I think you are out of luck with Netflix and Hulu.:sad:

---

### Post by 7cardcha on 2011-09-20
Get lubuntu uses half ram/cpu as gnome very lightweight and efficient.

---

### Post by TenPlus1 on 2011-09-20
I would definately recommend upgrading the memory to 512mb or 1gb if you can...  Running Lubuntu will definately make things a lot quicker and as for your Intel gfx that's fine for playing movies and even flash as it's the same chipset on my laptop and all works great from there :)

---

### Post by mörgæs on 2011-09-20
It is unfortunate that Damn Small Linux is still recommended. DSL is an abandoned project which has not received any attention (as in bug fixes) during the last two years. May it rest in peace.

Here are some more light alternatives:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by verymadpip on 2011-09-20
+1 for Lubuntu.
It ran perfectly well on a system with 256 Mb RAM for me.
I've added more RAM since, but that's another story.

---

### Post by lykwydchykyn on 2011-09-20
> **mörgæs said:**
> It is unfortunate that Damn Small Linux is still recommended. DSL is an abandoned project which has not received any attention (as in bug fixes) during the last two years. May it rest in peace.



There are situations where it can still be one of the few (if not the only) option, but those situations generally involve figures like "75MHz" and "16Mb".  

Suggesting it for a pentium 4 that can run any number of modern, general-purpose distributions is, I agree, a nudge in the wrong direction.

---

### Post by theducksfan2010 on 2012-04-01
+1 for Lubuntu! 

Puppy Linux, try Lucid Puppy 5.2.8.

I would definitely say adding RAM would be a positive and cheap off of ebay, I bought mine off of Amazon Market place.

Hulu Plus desktop is also available for Ubuntu, so that would be another plug for going with Lubuntu.

---

