---
title: "Several issues with 12.04 (hardware specific)"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Fajfi Pri on 2012-05-15
Hey guys, I'm new to Ubuntu and the Forums.

A couple weeks ago I download Ubuntu 12.04 and installed it on my laptop (Dell Inspiron M5030).  I have had quite a few hardware specific issues, and I was hoping that someone could help me out a bit.

The first, is neither my graphics or wireless card would work properly at first.  After changing the boot parameters to acpi=off (or noapic, I honestly can't remember), they started working.  Does this change anything else important?

I have a Logitch M305 wireless mouse (laser, I think).  It "works" as in it moves around very jittery, and can click.  It was too much of a pain to use to bother.  It jittered around far too much.  Anything I can do about this?

Overall, I just found the system rather clunky.  I'm sure once I get used to it, it will be fine, so this isn't really an issue.  I currently have Windows 7 installed (I installed this over the Ubuntu installation) and would love to try Ubuntu again, with a partitioned disk this time.  If you have any advice, I would love it.

Thanks,

Fajfi Pri

---

### Post by bodhi.zazen on 2012-05-15
Please identify your hardware. What graphics card ? What wireless ?

Sometimes there is a fix, sometimes it is best to obtain compatible hardware.

---

### Post by Fajfi Pri on 2012-05-20
I'm not actually sure . . . 

Anyway, I fixed the issues.  I installed Ubuntu today, and by setting the acpi=off and nomodeset boot parameters, and everything works now.  Setting thread as solved.

---

### Post by wildmanne39 on 2012-05-20
Hi, you need to be aware that acpi=off may turn off many features which may include fans, wireless and many others.

After you booted with acpi=off did you check to see if you have a graphics card driver in additional drivers that can be installed or that may need to be uninstalled like the nividia driver, it is default in 12.04 if you have an internet connection at the time of install of ubuntu and it has been causes issues so you may be better off with nouveau if you have a nvidia card.
Thanks

---

### Post by Fajfi Pri on 2012-05-21
Yes, I do have a graphics driver.  The regular driver and a post-release update.  I will try to install this and remove acpi=off and report back on how it works. 

Thanks for the suggestion!

---

### Post by Fajfi Pri on 2012-06-18
Update: Neither driver actually installs.  I'm not really sure what hte problem is, because this was around a month ago, but I might re-install Ubuntu again, and try to replicate the issue to get more information.  Any advice is greatly appreciated.

I'm going to un-mark this thread as solved.

---

### Post by StefanU on 2012-09-13
Hello,
I have the same laptop. Mine works with the video driver installed from jockey and for making the usb work I had to add irqpoll as boot parameter and erase acpi=off.
Hope this works for you.

---

