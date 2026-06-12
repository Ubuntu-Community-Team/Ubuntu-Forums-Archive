---
title: "Ubuntu heating up my laptop"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2012-02-28
hello all.. 
I have an HP Pavilion laptop(model TX1004), with 4gig memory, 640 gig HDD, 1 GB ATI Radeon video card(6740M), running on an i5 proc (2nd Gen)
 
i am currently running my laptop on Windows 7, and Ubuntu 11.10, on a dual boot basis. When i am on Windows, my laptop works perfectly fine, and does not heat up very much. On the contrary, while i am on Ubuntu, it heats up a LOT, as a result consumes my battery. I can also head the fan running wildly (i am assuming it is the graphic card fan), while i am in Ubuntu. Honestly, i despise Windows. So i am focusing more on Ubuntu now. Is there any way i could fix the overheating issue with my laptop?
 
Any help is greatly appreciated.
 
and FYI: My internet is currently down, so if the troubleshooting steps involve internet access i am doomed! :(
 
Cheers,
Nikhil Kenvetil

---

### Post by Gremlinzzz on 2012-02-28
My computer had the same reaction to 11.10.
so i installed Linux Mint 12 and everything was normal,no over heating or loud fan. may be a hardware thing:popcorn:

---

### Post by Nikhil Kenvetil on 2012-02-28
> **Gremlinzzz said:**
> My computer had the same reaction to 11.10.
so i installed Linux Mint 12 and everything was normal,no over heating or loud fan. may be a hardware thing:popcorn:
so.. is teh UI, and the purpose of Mint 12, same as Ubuntu. i haven't tried Mint yet.. i mean i don't want to take out Ubuntu and install Mint (or anything else) until i have tried out all possible ways..

---

### Post by Mark Phelps on 2012-02-28
> **Nikhil Kenvetil said:**
> i am currently running my laptop on Windows 7, and Ubuntu 11.10, on a dual boot basis. When i am on Windows, my laptop works perfectly fine, and does not heat up very much. On the contrary, while i am on Ubuntu, it heats up a LOT, as a result consumes my battery. I can also head the fan running wildly (i am assuming it is the graphic card fan), while i am in Ubuntu. Honestly, i despise Windows. So i am focusing more on Ubuntu now. Is there any way i could fix the overheating issue with my laptop?
Sorry, but the overheating is a known kernel bug that affects recent Ubuntu versions.  The only fixes that have been published involve either backporting to an OLD kernel version (which involves a LOT of work, including Internet access to get the older versions), or installing Jupiter (which also requires Internet access to download the app) to be used to throttle-back the CPU.

Don't know why Mint would not have the same problem, since it's a spin-off from Ubuntu.

But no, there is no solution I know of that does not involve Internet access.

---

### Post by Gremlinzzz on 2012-02-28
Mint work for me but might not work for everyone. you can try it.but i wouldn't ruin my computer over a system.

---

### Post by Gremlinzzz on 2012-02-28
> **Gremlinzzz said:**
> Mint work for me but might not work for everyone. you can try it.but i wouldn't ruin my computer over a system.

found a example 

Linux Mint ... Overheating and fan going nuts on laptop 

[http://mybroadband.co.za/vb/showthread.php/402661-Linux-Mint-Overheating-and-fan-going-nuts-on-laptop](http://mybroadband.co.za/vb/showthread.php/402661-Linux-Mint-Overheating-and-fan-going-nuts-on-laptop)

---

### Post by asifnaz on 2012-02-28
Backport older kernel .Or try some other DE

---

### Post by craig10x on 2012-02-28
kernel 3.2.5 (which is in ubuntu 12.04) is supposed to have the patch that was developed by a Red Hat developer which solves the power regression problem (which has been in all linux distros since kernel 2.3.8 which causes some (not all) laptops and desktop computers to have a very large increase in power consumption and making the fans come on frequently or all the time...

When i had my old computer (toshiba with amd) i could not run ANY os with kernel 2.3.8 or later, be it ubuntu or mint or whatever....my brand new Toshiba (with intel) doesn't have the problem...

The problem was that starting with kernel 2.3.8 it was causing the power management system on some computers to be shut off...the patch is supposed to make it so that doesn't happen anymore...I get the impression that the power problem was more prevalent on laptops that use AMD because my old one did but my new Intel doesn't seem to have the problem...

You might want to run a live iso of the new ubuntu 12.04 beta when it comes out on March 1 st and observe if you still have the problem...that would be a clue as to whether the new patch is going to eliminate the problem for you....if it does, perhaps someone here can guide you on how to put that kernel into your ubuntu 11.10 installation...

---

### Post by Sonsum on 2012-02-28
While the power regression bugs are being fixed, the intel i-series (such as your Sandy Bridge processor) still have a problem. Fortunately, as of now, the problem has been finally fixed by intel and will be coming in Precise's kernel as well as kernel 3.4 for everyone else.

I've been able to knock about 15 degrees off of my idle temp of my fresh install of 11.10 by running the 3.2.8 kernel however. I would recommend trying that.

---

### Post by Mark Phelps on 2012-02-28
To the OP:  it's nice that folks are offering you suggestions ...

I didn't because (apparently) I'm the only person who read your original comment:

> FYI: My internet is currently down, so if the troubleshooting steps involve internet access i am doomed!

All of these other suggestions require that you download SOMETHING, and most probably, from the Internet.

---

### Post by S2UIRR3L on 2012-02-28
I've been reading everyone's comments and what not...

Will my computer run the same way weather it's reading from the hard drive or a live disc? In other words, is it possible that my computer will run fantastic while reading from the live disc... But could my laptop react differently if it's actually installed to the hard drive?

As of now, I'm running 10.04 Lucid Lynx (64-bit) on my Fujitsu Desktop. There's no other operating system on it. It's running flawlessly (I got REAL lucky).

I'm in the process of updating my Fujitsu Laptop. Bought some new RAM and a new bare hard drive. I'm going to try a live disc before installing to hard drive.

Up until last week, I was running XP (which came with it) and Jaunty Jackalope 9.04 (both 32-bit because the laptop doesn't support 64-bit)... NO PROBLEMS

**MY MAIN POINT - WILL A LIVE CD ACT DIFFERENT FROM AN ACTUAL INSTALL?**

Thanks a million everyone!

---

### Post by craig10x on 2012-02-28
> **Sonsum said:**
> While the power regression bugs are being fixed, the intel i-series (such as your Sandy Bridge processor) still have a problem. Fortunately, as of now, the problem has been finally fixed by intel and will be coming in Precise's kernel as well as kernel 3.4 for everyone else.

I've been able to knock about 15 degrees off of my idle temp of my fresh install of 11.10 by running the 3.2.8 kernel however. I would recommend trying that.

thanks for that update :)

as for the Op...yes...all the solutions involve an internet connection, unfortunately...i don't think there is anything anyone will be able to suggest that doesn't...

---

### Post by Sonsum on 2012-02-28
> **Mark Phelps said:**
> To the OP:  it's nice that folks are offering you suggestions ...

I didn't because (apparently) I'm the only person who read your original comment:



All of these other suggestions require that you download SOMETHING, and most probably, from the Internet.

Actually, pretty much any solution requires you to download something off of the internet.

While these solutions will not fix the problem now, at least they do provide an actual solution that will help the problem if the OP does get internet again or decides to take their laptop to an internet cafe or something.

I fell that it is better to share solutions that may be inconvenient for the user, rather than nothing at all. (especially if someone who does have internet comes here from Google or something. It's very frustrating to have the top 5 results from your query all be unanswered threads.)

---

### Post by Mark Phelps on 2012-02-29
> **Sonsum said:**
> Actually, pretty much any solution requires you to download something off of the internet.

Correct ... a point I already made in the last line of my post -- way back in #4.

What the OP needs to know is that unless he CAN get internet access, he's NOT going to be able to fix his problem.

---

### Post by craig10x on 2012-02-29
Nikhil needs to know that ubuntu 12.04 beta 1 (out thursday) will have the power regression patch activated for the intels like i have on mine and he has on his laptop (the intel cores) it was not on previous 12.04's (alpha 1 alpha 2 and the daily builds)...

so....if somehow he can get internet access (or have someone do it for him) he should download the 12.04 beta 1 on thursday when it comes up on the mirrors and run it on the live dvd and see how it goes with the power consumption/fan business...I just read about this on the ubuntu notes page for it...the isos aren't up yet though...

i will be doing that myself ;)

I noticed my fan was coming on while testing isos previously of 12.04...but i did NOT know that the patch wasn't turned on for sandy bridge (intel icore) processors...the release notes say it is as of beta 1...

---

### Post by Nikhil Kenvetil on 2012-03-01
> **craig10x said:**
> Nikhil needs to know that ubuntu 12.04 beta 1 (out thursday) will have the power regression patch activated for the intels like i have on mine and he has on his laptop (the intel cores) it was not on previous 12.04's (alpha 1 alpha 2 and the daily builds)...

so....if somehow he can get internet access (or have someone do it for him) he should download the 12.04 beta 1 on thursday when it comes up on the mirrors and run it on the live dvd and see how it goes with the power consumption/fan business...I just read about this on the ubuntu notes page for it...the isos aren't up yet though...

i will be doing that myself ;)

I noticed my fan was coming on while testing isos previously of 12.04...but i did NOT know that the patch wasn't turned on for sandy bridge (intel icore) processors...the release notes say it is as of beta 1...
Thank you Craig, for that information.. Appreciate it. I will try that out and let you know if it all goes well.. But one more question.. is it alright to go ahead with the 12.04 beta right now? because, what really bothers me is if it doesn't work, I'd have to wipe out my Ubuntu partition, and reinstall everything, unless, of course, there is an easier way to go back from 12.04 to 11.10.

---

### Post by Nikhil Kenvetil on 2012-03-01
> **Sonsum said:**
> While the power regression bugs are being fixed, the intel i-series (such as your Sandy Bridge processor) still have a problem. Fortunately, as of now, the problem has been finally fixed by intel and will be coming in Precise's kernel as well as kernel 3.4 for everyone else.

I've been able to knock about 15 degrees off of my idle temp of my fresh install of 11.10 by running the 3.2.8 kernel however. I would recommend trying that.
Hey.. a couple of questions: within Ubuntu or otherwise, is there a way to check what is the temperature, my laptop is mounting on?

Also, how do i check what kernel i am on now.. because from what i understand, 11.10 has v3.0.0 (3.0.0-12.20)

thnx

---

### Post by Sonsum on 2012-03-01
> **Nikhil Kenvetil said:**
> Hey.. a couple of questions: within Ubuntu or otherwise, is there a way to check what is the temperature, my laptop is mounting on?

Also, how do i check what kernel i am on now.. because from what i understand, 11.10 has v3.0.0 (3.0.0-12.20)

thnx

This guide is a little out of date, but all of the terminal sensor information should be still good (the only problem with all of the applets mentioned are that they are for gnome 2, not unity). [https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

I usually check my kernel info from "gnome-system-monitor" which should be under your menu as System Monitor

---

### Post by craig10x on 2012-03-01
Yes... please let us know how it works out when you try 12.04...

Checking kernel you have installed:  bring up "system monitor" and click the section that says "system" that shows what you are running including the kernel number...

Checking temperature...on the live session, install a program called:  psensor...
It's what i am using on my live run of 12.04....

Although they hadn't posted the iso for the beta on the mirrors yet when i checked this morning, i decided to download the daily build for today instead....it should be identical to the beta snapshot that's going up on the mirrors...

I'm in it right now...power management is working and seems to be doing a very good job, so definitely worth your checking out :D

my kernel is:  3.2.0-17  which is the one that has the patch activated for the intels...

---

### Post by soumadeep on 2012-05-04
I installed Ubuntu 12.04 on my HP Pavilion dv6 TX-6144.750 GB HDD.4 GB RAM.1 GB Graphics card from ATI Radeon.Problem is Overheating.My laptop fan is running like hell and therefore consuming a lot of battery.Whereas it works fine on Windows.I do have a working Internet connection and can download softwares and updates from the net.Please help even if it requires a regular internet access....

---

### Post by TenPlus1 on 2012-05-04
This may help:

[http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/](http://cisight.com/switch-off-ati-vga-in-dual-vga-with-intel-on-ubuntu-to-solve-overheat-problem/)

---

