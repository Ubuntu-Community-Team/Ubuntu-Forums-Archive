---
title: "What happen killed laptop monitor"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by crip720 on 2013-10-09
Hi last night I was using Firefox with three tabs open.  I finished with one tab and went to close it, I made a misake and click the mouse wheel instead of the right bottun.  The laptop monitor seem to competly turn off.  Only doing a reisub seem to work.  Firefox window was near 99% max, computer temps were normal.  Think I have some Hot coners enable, but I do not know of any that will turn off a monitor.  Any ideas on what happened?  Thank you Colin

---

### Post by crip720 on 2013-10-11
Hi, was using the laptop this morning, had firefox opened, moved the mouse around some and I think the workspace changed and lost Unity launcher and cario-dock.  I had some desktop icons left, but when I click on the home shortcut icon Xsensors came up and all icons dissappeared.  Only had wallpaper[custom] xsensors, and mouse cusor.   Back to reisub.  I am using Ubuntu 13.04 64b on an Acer aspire 5536 laptop with AMD Athion 64 X2 CPU and Radeon HD3200 graphics.  I do not know what is happening, but if you can show me where to look, I can post it here.  I have been using Ubuntu since 10.04 on this computer and this is the first time I had this problem.  I am thinking maybe there is a problem in my Xorg[?] on 13.04 since I do not seem to have this problem on my other partitions running Windows or Linux OSs.  Thank you.  Colin

---

### Post by tgalati4 on 2013-10-11
Open a terminal:

```
dmesg | more
```

Look for errors.  Spacebar to move forward, "q" to quit.

Sounds like a hardware problem.  Bad battery, bad power supply, loose RAM, thermal halt due to dust in heat sink.  It could be anything.

---

### Post by crip720 on 2013-10-11
I do not think it is hardware related, because it only happens when I am using the partition with 13.04 64b on it.  I am on 13.10 64b right now on a diffrent partition,and everything is working well.  Is there a way to read the error messages on the other partition.  I ran dmesg on the 13.10 partition and did not see any 'error' messages, PICe aspm was disable and sp5100 -tco was giving up.  ata1 & 2 softretest fail, but it look like it got it going on the retry.  I have the dmesg report still in terminal if you want it.  I am unsure how long I can use 13.04, before it stops working for me,this morning it only lasted 5 minuets,  but I do have this one and other partitions that are working well.  This problem only started this week, before that 13.04 was working well.

---

### Post by crip720 on 2013-10-12
Back on 13.04 today and first thing I did was to open Unity tweak and disable all Hot corners and other tweaks dealing with the edges.  Has been good all day, except that Unity launcher will not show unless I use the Windows key to bring up Dash or turn off auto hide.  Problem must be connected with Unity tweaks and Hot corners, edges.

---

### Post by tgalati4 on 2013-10-12
You might want to add Unity hot corner issue to the title to get some more useful hits.  I don't use Unity, so I can't really help.

---

