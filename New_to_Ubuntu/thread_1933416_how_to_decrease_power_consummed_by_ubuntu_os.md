---
title: "how to decrease power consummed by ubuntu os??"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-02-29
my battery gets discharged very soon if i use ubuntu when compared to windows-7 .
how can i reduce power consumed by ubuntu?????

---

### Post by collisionystm on 2012-02-29
> **rishiar4 said:**
> my battery gets discharged very soon if i use ubuntu when compared to windows-7 .
how can i reduce power consumed by ubuntu?????

Try Jupiter.

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by mastablasta on 2012-02-29
> **rishiar4 said:**
> my battery gets discharged very soon if i use ubuntu when compared to windows-7 .
how can i reduce power consumed by ubuntu?????
 
 
you didn't give any system specifications. particulary graphics card (hybrid or only one?! it iwll be difficult to give any advise without that.
 
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Mark Phelps on 2012-02-29
> **rishiar4 said:**
> my battery gets discharged very soon if i use ubuntu when compared to windows-7 .
how can i reduce power consumed by ubuntu?????

Another problem to consider is overheating.  If your CPU is running at nearly full speed under Ubuntu, and you are NOT able to slow it down, then it's likely overheating the laptop as well.

You could try installing lm-sensors to monitor the CPU temps -- at least that way, you will be able to see if it is overheating.

But ... if it IS oveheating and you are unable to slow it down, you need to consider NOT running Ubuntu.  I wouldn't have suggested this route, but I read a thread recently where someone mentioned burning up two laptops with this overheating problem.

---

### Post by cortman on 2012-02-29
Whatever happens don't burn up your computer. I don't know if a lighter weight desktop would make a difference, but you could try running lubuntu or xubuntu instead. If it's drivers or coreutils making it overspeed (and Jupiter doesn't fix it for you), you may be out of luck as far as Ubuntu is concerned.

---

### Post by Tyggna on 2012-02-29
Try jupiter first, and if that doesn't give you what you want, here's some relevant information:

Nothing better than monitoring your power usage and behavior.  It might just be a matter of using Linux a bit different than you utilize windows.

Generally, the three areas of power consumption that you want to optimize are memory usage, graphics card usage, and cpu usage -- in approximately that order.

RAM takes huge amounts of power.  Back in 2004 the recommendation was 10W per 128MB in use.  Today, it's about 15W/gig actively used.  RAM is used by having a lot of programs opened at once.
Graphics cards, specifically their mobile versions, can take about 40W of power when fully utilized (something that will certainly happen if you're running external monitor(s) on battery, playing games, or utilizing some of the prettier window manager effects).
Lastly, laptop processors should use about 15W when idle if speed stepping is enabled and used, and up to 80W when pegged.  On average, for web-browsing and normal business applications, plan on using about 20-30W on average.

A good size battery (9 cell LiOn) should last about eight hours with a computer idled, and about two hours at max usage.  If it is not lasting that long idled, then look at speed stepping and RAM utilization.  

Hopefully that information helps if the above suggestions don't get you the results you want.

---

### Post by audiomick on 2012-02-29
I read something here recently about a bug in some kernels causing some laptops to run at full CPU speed all the time. I don't remember where it was, but there have been several mentions of it. Try searching the forums for it.

---

### Post by Kantis on 2012-02-29
I use the CPUFreq Indicator panel applet for this, works better on my netbook than Jupiter. Here's some instructions: [http://www.webupd8.org/2010/12/cpu-frequency-scaling-appindicator.html](http://www.webupd8.org/2010/12/cpu-frequency-scaling-appindicator.html)

---

### Post by fuduntu on 2012-02-29
> **Kantis said:**
> I use the CPUFreq Indicator panel applet for this, works better on my netbook than Jupiter. Here's some instructions: [http://www.webupd8.org/2010/12/cpu-frequency-scaling-appindicator.html](http://www.webupd8.org/2010/12/cpu-frequency-scaling-appindicator.html)

This just isn't possible.  CPUFreq appindicator does not tune your kernel, it just changes the CPU scalar.

---

