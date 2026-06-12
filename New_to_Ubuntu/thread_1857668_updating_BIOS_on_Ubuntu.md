---
title: "updating BIOS on Ubuntu"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by wolfman21 on 2011-10-10
how do you run BIOS updater in Ubuntu i downloaded the update for my system and it says that Ubuntu cant run it any ideas.

---

### Post by thatguruguy on 2011-10-10
What type of system do you have?

And you're right, Ubuntu probably can't run the bios update program, if it was written for Windows.

---

### Post by wolfman21 on 2011-10-10
I have a acer power fh

---

### Post by papibe on 2011-10-10
There are several options. In general all involve to create a bootable CD or USB stick, with a minimal compatible software like FreeDOS.

Here's more information:
[LIST]
[*][HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789").
[*][How to flash motherboard BIOS from Linux]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html").
[*][HP USB Disk Storage Format Tool]("http://forum.xbmc.org/showthread.php?t=68653&highlight=zotac+update+bios") (from the XBMC forums)
[/LIST]
I hope that helps,
Regards.

---

### Post by wildmanne39 on 2011-10-10
Hi, it is also worth mentioning that unless you have to upgrade your bios because of an issue that can be solved by doing so, it it better to leave it alone.

I have seen people that flashed there bios for no good reason, then it quit working and there is nothing you can do if you burn out the bios in the process.
Thank you

---

### Post by Mark Phelps on 2011-10-10
> **wildmanne39 said:**
> Hi, it is also worth mentioning that unless you have to upgrade your bios because of an issue that can be solved by doing so, it it better to leave it alone.

+1

Nothing can "brick" your PC like messing up a BIOS upgrade.  If you don't know what you're doing, and it clearly sounds like you don't, you should really leave it alone.

---

### Post by KingYaba on 2011-10-10
> **wildmanne39 said:**
> Hi, it is also worth mentioning that unless you have to upgrade your bios because of an issue that can be solved by doing so, it it better to leave it alone.

I have seen people that flashed there bios for no good reason, then it quit working and there is nothing you can do if you burn out the bios in the process.
Thank you

I agree but I've had to update the BIOS on my motherboard and having a Windows partition (now a whole hard drive) proved quite useful for that. OP might have a CPU upgrade and needs new firmware.

---

### Post by mastablasta on 2011-10-11
in the old days you could stick the update programme onto dos boot disk. perhaps something similar can be done now using USB stick and maybe freedos.

---

### Post by Mark Phelps on 2011-10-11
OK ... if you're determined to do this ...

First, you can't do it from Ubuntu, or from any other Linux distro.  So, forget that approach.

Second, most modern motherboards (2 yrs old or less) have a feature that allows you to boot into a utility that will do BIOS updates.  Check the documentation on your motherboard to see what it supports.

Third, the first thing to do when you start this is to save off your current BIOS so that it can be recovered. If you can't do that, then flashing your BIOS is asking to "brick" your machine.

Also, some motherboards now have dual-BIOS, meaning, they have two BIOS chips.  So, if one gets corrupted, you can switch to using the other.

Again, your motherboard documentation is the place to go to find out the details.  If you don't have any, then find out the make and model (Model, especially Version, is very important) and go to the motherboard manufacturer's site to see what they have in terms of BIOS updating information.

---

### Post by thatguruguy on 2011-10-11
> **Mark Phelps said:**
> OK ... if you're determined to do this ...

First, you can't do it from Ubuntu, or from any other Linux distro.  So, forget that approach.

Second, most modern motherboards (2 yrs old or less) have a feature that allows you to boot into a utility that will do BIOS updates.  Check the documentation on your motherboard to see what it supports.

Third, the first thing to do when you start this is to save off your current BIOS so that it can be recovered. If you can't do that, then flashing your BIOS is asking to "brick" your machine.

Also, some motherboards now have dual-BIOS, meaning, they have two BIOS chips.  So, if one gets corrupted, you can switch to using the other.

Again, your motherboard documentation is the place to go to find out the details.  If you don't have any, then find out the make and model (Model, especially Version, is very important) and go to the motherboard manufacturer's site to see what they have in terms of BIOS updating information.

I went to Acer's site and downloaded the utility to flash the BIOS for the Acer Power FH. The "new" bios in the package is from 2007, which suggests this is a fairly old (much more than 2 years old) system.

I question whether any perceived benefit from flashing this BIOS is worth the risk.

---

### Post by Mark Phelps on 2011-10-11
> **thatguruguy said:**
> I question whether any perceived benefit from flashing this BIOS is worth the risk.
I don't challenge the belief that flashing any BIOS is risky, for as I said, it's one of the easiest ways to "brick" a PC.

But with recent motherboards, I've noticed vendors including BIOS utilities that don't require you booting into any OS to do the flash.

Plus, with the new dual-BIOS boards, changing from one to the other is often very easy to do.

So, I think there's less risk now than there was when folks used to boot into Windows do to this.

---

### Post by eriktheblu on 2011-10-11
My new ASUS board has the no-OS bios update. It's pretty nice.

---

### Post by SirDrexl on 2011-10-11
I thought the prevailing wisdom was that updating BIOS from within Windows was much more risky than doing it in DOS or the built-in utility.  BIOS updates was the last thing I kept a floppy drive for, until I got USB flash booting working.

---

### Post by thatguruguy on 2011-10-11
> **Mark Phelps said:**
> I don't challenge the belief that flashing any BIOS is risky, for as I said, it's one of the easiest ways to "brick" a PC.

But with recent motherboards, I've noticed vendors including BIOS utilities that don't require you booting into any OS to do the flash.

Plus, with the new dual-BIOS boards, changing from one to the other is often very easy to do.

So, I think there's less risk now than there was when folks used to boot into Windows do to this.

Perhaps. But as I mentioned, the OP's system apparently does not have a recent motherboard.

---

