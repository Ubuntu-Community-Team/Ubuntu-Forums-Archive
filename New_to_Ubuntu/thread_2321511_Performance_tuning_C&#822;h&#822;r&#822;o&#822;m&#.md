---
title: "Performance tuning C&#822;h&#822;r&#822;o&#822;m&#822;i&#822;u&#822;m&#822; (actually *ALL* suspect Processes ) help needed."
date: 2016-04-22
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2016-04-22
Hi, thanks for reading. 

Question. (Now become desperate enough to ask for help as I've tried all the Google "Performance Tune" advice (aka syscontl.conf, et.al. NO HELP). 

I have a "decent" CPU (dual core Pentium, 4-GB RAM) 

I'm a former Windows XP "refugee" (VERY HAPPY) to be a 100% Linux user now. EXCEPT, I can't isolate what is causing HORRIBLE performance issues with my Linux Install. 
(other than what was "normal FUD for Win XP lag---at it's "best lag", was never close to a "normal--"HORRIBLE" lag with Linux. 

```
(yes, all the 101-201 questions. I've reinstalled, I've even purchased a new drive, to install a fresh on that drive, etc.etc.). 

I've partitioned out each (available) mount point (/usr /usr local /home /root ,,etc). 

```
To prove my patience---Applications/ Web Browsing I can count in *MINUTES" to "render" a page, open a program, etc. (not "seconds" but MINUTES). 

```

]My CPU (IS ALMOST ALWAYS--actually "always" according to xfce-taskmanager---at 100%)

---via looking at Task Manager---Running at full bore 100% Process. (yet, looking at the list of running CPU at the time, 
the "Math" does not add up. (and does not always agree with "Glances") aka xfce4-taskmanager 
(I look at both root and non-root command prompt to try to find anything "hiding"---nothing I have yet to find). 

All the rkit, etc. stuff I try (find nothing). 

I use cpulimit. Yet (guess "FUD"??) but closing CPU (reboot, etc.) it does not keep; those limits, thus not an ideal tool. 

AND, even if I find a Process either "Red lining" won't thrash down (on it's own)----even using cpulimit an app won't always respect the limit 
(aka--Firefox I"ll limit to 20---and it will run in the high 20's as a "norm"--then will Thrash into the 90's "routinely" (as does Chromium, etc). 

```

I've attached a series of screen shots

If you note (this is about a 5-minute window of time (back to back shots during that)----nothing shows a "usual suspect".
 (also, fyi--intentionally fired up CrashPlan in the middle of test to see if it would thrash and be "a leading cause"---it does not appear to be)
--of course, have pinged CPP support for any CPP questions. 

But, see what I mean by nothing seems "consistent"-
---AND (using Glances is when I can only see a "true" load. AKA--if you notice XFCE-Taskmanager (in both normal and root)---don't "agree with" Glances (in Root mode)----a top cpu thread. 

THANK YOU!!!

---

### Post by TheFu on 2016-04-23
Why the code tags?  Don't see **any** output inside them.

Could be anything. Bad networking, misaligned disk partitions, too much graphics with a low-end GPU, too many bloated processes running, some failing hardware or a combination of all or any of them.  For example, a failing, but not failed SATA cable could do all these things.

I would ask that you run a script [http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information](http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information) and capture all the important details about your system, then most the URL it makes back here. That way, we don't have to ask for details on everything.

If you kill off the java, firefox, chrome/chromium processes and use a straight network connection (not VPN), how much faster is it?

---

### Post by samue2 on 2016-04-28
Due to your lower end cpu and system, I would recommend a few basic trouble shooting steps for a slow pc- such as...

1. Clear your CMOS
2. Check the BIOS to see if the cpu is throttling / performing with a lower clock speed
3. Check all programs running on boot
4. Finally- if all else fails from above and here- clean your pc case! also, as a side note- try disabling every single process that would be graphically intensive- and try lower your resolution to reduce strain on cpu / gpu.

---

