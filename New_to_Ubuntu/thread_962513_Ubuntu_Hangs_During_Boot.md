---
title: "Ubuntu Hangs During Boot"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by gimbal on 2008-10-29
I have an HP Pavillion dv2000 laptop that I have used as a dual boot Windows XP/Ubuntu computer for over a year now and things have generally been good.

Recently, I experienced a hardware failure that required the Main Logic Board to be replaced by HP.

Now, Windows boots fine, but Ubuntu now hangs at seemingly random spots during boot.  This is true for both the regular boot and recovery mode.  Once, recovery mode actually completed boot, and everything worked fine.  Subsequent reboots (a dozen or so) have failed.  GRUB seems to work fine.

I tried booting from the 7.10 Ubuntu installation CD, and the same thing happens.  I did a memory check and the BIOS hard drive check and both pass.

Does anyone have any suggestions?

---

### Post by Thelasko on 2008-10-29
What kind of Mother Board is it?  [Foxconn]("http://linux.slashdot.org/article.pl?sid=08/07/25/1150218&tid=190") boards have issues.

---

### Post by gimbal on 2008-10-29
Offhand I don't know - the trouble resolution form from HP only gives a part number.  To the extent it matters, I have always gotten a "BIOS Bug #----- detected" during startup, and it never seemed to matter before the board was replaced.

---

### Post by Thelasko on 2008-10-29
> **gimbal said:**
> Offhand I don't know - the trouble resolution form from HP only gives a part number.
So, it's a replacement board from HP then?  I was wondering if you purchased something else.

---

### Post by gimbal on 2008-10-29
> **Thelasko said:**
> So, it's a replacement board from HP then?

Yep.  On the bright side, it was covered by warranty, so the price was right.

---

### Post by Thelasko on 2008-10-29
What's the part number?

From [this page:]("http://izanbardprince.wordpress.com/2008/07/27/list-of-confirmed-foxconn-sabotaged-motherboards-that-cannot-run-linux-well/")
> Manufacturer: Hewlett-Packard
Product Names: HP Pavilion dv62xx/63xx (RJ637AV) (Also sold as d6230br), HP Pavillion D2762TX (will reportedly not only NOT work with Linux, but XP as well!)

If you are using any of these motherboards/computer systems, please contact the company that sold it and demand either (1) A BIOS fix. or (2) A full and complete refund or exchange.

---

### Post by gimbal on 2008-10-30
I've got an RD140AV.  I've got the BIOS information off the HP website.  Hopefully, that combined with an Ubuntu upgrade will fix the problem.

---

### Post by Thelasko on 2008-10-30
[This says]("https://wiki.kubuntu.org/LaptopTestingTeam/HPDV2000Z") that board should work.

---

### Post by gimbal on 2008-10-30
A good sign, to be sure.  However, the BIOS version listed (F.13) is a bit old, and I'm pretty sure I got an 'upgrade' with the new board.  In principle, I should be able to revert to an earlier BIOS if I need to.

---

### Post by Thelasko on 2008-10-30
I don't recommend flashing a BIOS unless it's absolutely necessary.  There is always a chance you will fry it.

---

### Post by gimbal on 2008-10-31
That's what I figured.  I have BIOS F.3C now, for what it's worth.

I'm struggling with some logistical issues now.  All of the instructions I can find for upgrading from 7.10 to 8.04 assume you are downloading 8.04 while running 7.10.  I'm assuming you can also upgrade from CD, but haven't found any specific instructions.

However, the real problem I've been having is my ISP at home is too unreliable to get through the entire download.  I can download at work, but the PC 'upgrade' they gave me two weeks ago doesn't have a CD burner :mad:.

---

### Post by gimbal on 2008-10-31
As an aside, I can occasionally get through boot up using recovery mode.  In the case that I need to do a complete new installation, where can I find the commands to mount a USB drive or the Windows partition drive so I can move a small number of personal files that aren't backed up?

---

### Post by sdowney717 on 2008-10-31
use ntfs-3g
this site shows you how.

[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

with ibex, this is already configured.

Why not back up your home folder and do a full install of Ibex?

---

### Post by gimbal on 2008-10-31
> **sdowney717 said:**
> use ntfs-3g
this site shows you how.

[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

with ibex, this is already configured.

Why not back up your home folder and do a full install of Ibex?

Unfortunately, all I've got in recovery mode is command line functionality.  So, I need to mount another drive via command line, do the backup, and then install.  I think I've found the instructions to do this now.

But first, I'm going to see if I can startup either Hardy or Ibex from CD.  If I can't, then I may just move the files and wait for the next release or something.

---

### Post by sdowney717 on 2008-10-31
[http://ubuntuforums.org/showthread.php?t=964988](http://ubuntuforums.org/showthread.php?t=964988)

I found out how to restore home into even a new user name.
Yes, try a live CD and if you can boot then
I would back up home and then wipe and install new.

---

### Post by gimbal on 2008-11-01
OK, I booted up with 8.04 from CD and everything seemed to work fine.  So, now I can boot 8.04 from CD and occasionally boot 7.10 in recovery mode.

I've got the alternate CD for 8.04, and I'm trying to figure out how to do an upgrade from 7.10.  

Unfortunately, the upgrade instructions assume you have 7.10 fully running, which I don't.  

Is there any upgrade path from 7.10 in recovery mode, or do I need to save my data to a USB drive and do a complete new install?

---

### Post by Thelasko on 2008-11-03
I would go the reinstall route myself.  It's really useful to have a separate /home partition for such a situation.

---

### Post by gimbal on 2008-11-07
Final resolution update:

I did a new install of 8.10 and everything is working fine.

The only problem I have run into is I forgot to backup my email, #-o so I lost a couple months there.  Nothing critical though.

In the final analysis, I had an incompatibility between the HP BIOS (F.3C) and Ubuntu 7.10, which is resolved with Ubuntu 8.04.

Thanks to everyone who helped.

---

