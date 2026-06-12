---
title: "Cold start requires restart"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by bwiggs on 2008-06-05
Greetings from a Ubuntu (and Linux) newbie.  I've successfully downloaded and installed 8.04 LTS on a machine devoted entirely to Ubuntu.  After installing off the cd, I reset my BIOS to boot off the hard drive.  I typically shutdown the machine and turn off its power after I'm through for the day.  When I cold start the machine the next day, I see a brief message about GRUB, then I get the Ubuntu logo splash screen with the horizontally oscillating gauge--but that's it: it just sits there like that.  After waiting 15 minutes I hit the reset switch.  That worked: in short order it went through GRUB, then the splash screen, then presented the login screen.  I logged in any everything was fine, as far as I can tell.  This happens every time I shutdown.  Is this the design behaviour, or do I need to change something?

---

### Post by starcannon on 2008-06-05
That is not normal behavior no.

With the little information given I'm going out on a limb and guessing:

fsck is running and taking its sweet time

or the box is trying to connect to the network and hanging, then on second boot since its established an address it just jumps right in.

My best 2 guesses

---

### Post by st33med on 2008-06-05
Could you hit Ctrl-Alt-F1 while it is booting and post back here with what it is saying? Just write it down, you have about fifteen minutes :).

---

### Post by st33med on 2008-06-05
Ok, yeah, that could be fsck checking your disk. It checks every thirty boots, so, this is after thirty days, I am assuming. It checks the disk so there is no unseen errors and such.

However, it is faster than defraging the disk ;).

---

### Post by ByteJuggler on 2008-06-05
> **st33med said:**
> Ok, yeah, that could be fsck checking your disk. It checks every thirty boots, so, this is after thirty days, I am assuming. It checks the disk so there is no unseen errors and such.

However, it is faster than defraging the disk ;).

It also typically doesn't take 15mins...

---

### Post by st33med on 2008-06-05
> **ByteJuggler said:**
> It also typically doesn't take 15mins...

On an old or slow machine, it could. I had Gutsy Gibbon previously take ten minutes to check.

---

### Post by bwiggs on 2008-06-05
Thank you all very much for your suggestions.  I am not at the machine now (it's @ home, I'm @ work).  I will analyze the situation tonight, as suggested.  I'll start by letting it run longer before I try a reset.  I'll post back later.  Thanks again.

---

### Post by mister_pink on 2008-06-05
Hmm, fsck should say its running the test on the screen, it wont do it in the background. Also the pattern of the problem doesn't make sense for that - why would it try every other go.

I'd have a peak through your system logs in System, admin, system logs to see if anything is obviously amiss and post it here. Not really sure under which section you're most likely to find something useful I'm afraid, so there's a lot to wade through. Hopefully someone can point you more in the right direction, although you can use the time stamps to help if you know when it crashed.

---

### Post by cariboo on 2008-06-05
Sounds like a hardware problem. Pull the side off your computer and check all your connections, make sure all your peripherals are plugged in securely.

Jim

---

### Post by bwiggs on 2008-06-05
After getting home I switched the machine on and waited.  Same behaviour as per my original post, except that it eventually switched from the splash screen to a bare terminal screen running "BusyBox".  I let that run for 2.5 hours before I gave up & hit the restart switch (which brought up the Ubuntu login screen reasonably quickly).  While running, BusyBox spewed forth many screens full of what I take to be error messages, mostly "exception Emask" and "Buffer I/O error" messages.  Many of the messages appear to relate to logical partition sda8.

I shutdown then rebooted & hit Ctrl-Alt-F1 as suggested by st33med.  That produced many messages having the same format as the BusyBox messages, one example being:

[   46.382033] ata1.00: exception Emask 0x0 Sact 0x0 Serr 0x0 action 0x2 frozen

FWIW, the machine is an old P4 with 1GB RAM (newly installed), one 40GB & one 4GB drive.  I initially installed Ubuntu using what appeared to be the easiest option offered by the cd: 'let Ubuntu have the entire disk'.  Subsequent reading made me think I'd be better off partitioning my drives, so I reinstalled Ubuntu and while doing so I used the partitioning feature to yield this:

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e014932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux		<-- /boot
/dev/sda2              13         741     5855692+  83  Linux		<-- /
/dev/sda3             742        4267    28322595    5  Extended	
/dev/sda5             742        1470     5855661   83  Linux		<-- /usr
/dev/sda6            1471        1713     1951866   83  Linux		<-- /var
/dev/sda7            1714        1835      979933+  83  Linux		<-- /tmp
/dev/sda8            1836        4267    19535008+  83  Linux		<-- /home

Disk /dev/sdb: 4325 MB, 4325529600 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x107a1079

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   82  Linux swap / Solaris

I'm inclined to think that I have hardware problems as some of you have suggested, but I'm mystified because once I login the machine seems fine.  I do not yet have any plans for the machine except using it to learn about Ubuntu, linux, etc.  I thought that a mothballed machine would be ideal but it may be that the machine is defective in some manner.  Should I run System/Administration/Hardware Testing?

---

### Post by cariboo on 2008-06-06
The reasoning behind why it might work when it's been running for a while, it that everything has had time to warm up allowing things to expand and if  there are bad connections the may tighten up after warmup.

Jim

---

### Post by Golem XIV on 2008-06-06
I had a similar problem once with a drive that was ready to fail.  It wouldn't spin up quickly enough, so I had to enter BIOS setup at boot and wait for a minute, then exit the BIOS setup and let the system boot normally.

Give it a try, and if it is indeed what's happening I'd advise to back up and replace the failing drive ASAP.

Good luck!

---

