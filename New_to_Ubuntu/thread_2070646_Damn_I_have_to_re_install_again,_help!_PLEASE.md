---
title: "Damn I have to re install again, help! PLEASE"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by mikee55 on 2012-10-13
Hello all, I purchased a motherboard, CPU RAM and psu and case from a shop last year, put it all together to run 11.04. As time passed I found myself having to re install everything every now and then. I could never get to the bottom of it. After deciding it must be the hard ware, guarantee is out of date. Had a power outage this morning, my bios is set to reboot after power failure. Once again, nothing happens past post. I need to know what causes this random problem, if its logged anywhere and then see if a solution can be found. I'd only just did a reinstall, set my wallpaper and re loaded my Fire Fox bookmarks! At the mo, I haven't touched the system other than to boot 11.04 CD live.
Is there a log file that I can have a sneaky peak at? Natty sits on a 2 year old SSD hard drive, could it be warn out?

great-full as ever for any help, thank you.

Mike

---

### Post by Wim Sturkenboom on 2012-10-13
If **nothing** happens after post, there will not be a useful log file after a power outage.

The liveCD contains memtest (as a boot option); run that for a night. You can also download diagnostic utilities from the website of the manufacurer of the HD and check the HD; alternative can be to run 'badblocks' (I guess it's on the liveCD).

Assuming this is a single OS system, you can press <shift> near the end of the POST. Keep it pressed; do you get a grub menu? If so, the problem is booting the actual OS.

PS Can you please give details of the hardware.

---

### Post by Paqman on 2012-10-13
Definitely hardware. Simple stuff first: power off, open up the machine and check all the connectors are pushed firmly home.

After that, run memtest as Wim suggests. From there you want to try and isolate the exact component that's at fault. Do you have another machine you can swap parts with?

Your SSD won't have worn out, that takes years of very intense punishment.

---

### Post by mikee55 on 2012-10-13
Hi I have an Asrock N68C-GS UCC and a Vertex OCZ 30GB ver 2.0 SSD! 2.9 ghz Semperon single core 64 bit OS Ubuntu only :) of course

Mike

---

### Post by No1Mportnt on 2012-10-13
You might also consider putting a UPS on your system to prevent the hard downs when you lose power.  That is not good on any of your components.  If you have a lot of issues with failures or brownouts this would make a big difference.

---

### Post by oldfred on 2012-10-13
If system is doing anything when you have an abnormal shutdown, you almost always have to run fsck on all the mounted filesystems.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You can use log file viewer. Log files are actually in /var/log. There are a lot of logs.

---

### Post by mikee55 on 2012-10-13
Hi, before I start digging guess what? I thought if I install Natty on my USB stick, it would ru quicker than the live cd. I told Bios first boot USB, it ignored me and booted my SSD???? Go figure!!

So, now here I am back on my OS posting to you! Where do I go from here?

Totaly Baffled, Mike :)

---

