---
title: "CANT ACCESS LIVE USB @ BOOTUP-- (only after, within Windows)"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by iamthemooseking on 2013-11-21
Hi.  I've got a very strange problem going on, I'm not sure how to diagnose it.
I've recently inherited a PC that I'm trying to fix.  It's running Windows XP, but it's lagged down with a virus that I can't seem to locate in any of the regular places in Windows file directories (rootkit?).  That's not my concern anyhow (perhaps?).  My plan is just to fix it by putting Ubuntu on it.
The problem is that it won't read my Live USB drive until windows has started up.

If I allow it to boot-up naturally, or bring it into safemode, that works fine, but puts me in no position to install the os.
However, if I specify USB as primary startup drive in the BIOS, it just freezes up.  I've tried a couple different things but it won't boot off the Live USB at startup.

It reads it fine once Windows is up... but unless I can install ubuntu from command line or something, it's not really helpful.

I'm going to try Sophos Rootkit Tool, and see if that has any effect, but I'm doubtful.
Any suggestions or insights would be very appreciated.
Thank you,
Ryan

---

### Post by electrohandyman501 on 2013-11-21
How did you creat the USB. Can you boot a LiveCD instead?
Depending on how old the hardware, it may not reconize a bootable flashdrive.

---

### Post by iamthemooseking on 2013-11-22
It won't recognize the dvd-player either...
So now I'm going to try to make a bootable USB for my mac, and install Ubuntu at boot-up onto a removable drive.  I'll then just put that drive into the PC tower and if everything goes well it will boot Ubuntu.
However, I'm not too sure if the Mac installer will create a boot environment that the PC hardware will be unable to recognize.  I'll find out soon I guess.

---

### Post by iamthemooseking on 2013-11-22
Disregard that.  I've been awake for a really long time.  I'll try your idea and let you know.

---

### Post by DuckHook on 2013-11-23
Please answer electrohandyman501's first question: how did you create the USB? Also, please provide full HW specs. These answers are important.

Given lack of info, this is just a guess, but I suspect that your USB is either not bootable or not fully bootable. This is commonly caused by wrong USB creation process, corrupted GRUB, corrupted boot image, or improper drivers. Did you use unetbootin? How did you download the initial ISO? Did you checksum the ISO? What version are you installing?

Another possibility is that your HW is so old that Ubuntu actually won't boot on it. There can be many issues, but an example would be trying to install Ubuntu on a laptop with a Pentium 'M' CPU. Modern Ubuntus will not boot on such HW and a special kernel has to be used, although GRUB will usually start even if Ubuntu won't, so it shouldn't lead to a 'freeze'. Can't make heads or tails of this possibility until you post your HW specs.

PS: The Apple work-around won't fly.

---

