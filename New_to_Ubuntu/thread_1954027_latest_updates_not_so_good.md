---
title: "latest updates not so good"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by lwalper on 2012-04-07
I just installed the recommended updates. Everything good so far -- but on restart my computer hangs on a blank screen immediately following the POST. It's been like that for a couple of hours and I have tried to restart a couple of times.

Is there any way to go back to something that works? or do I need to scratch it and re-install the OS from the beginning?

---

### Post by bodhi.zazen on 2012-04-07
What version of Ubuntu, what updates? did you upgrade to 12.04 ? 

Sounds as if your graphics card is not working, what hardware do you have ?

There is no easy way to downgrade, you would be looking at backing up your data and doing a fresh install, but you would be stuck unable to upgrade.

---

### Post by lwalper on 2012-04-07
Well, actually, the screen is not completely "blank" - there is a cursor blinking in the upper lefthand corner and the POST with HP logo does appear in the restart process. Don't think it's a graphics card problem.

OS is 11.10 - didn't realize there was an 12.04 out. I've just been updating the 11.10.

---

### Post by bodhi.zazen on 2012-04-07
Now it sounds as if the computer is not booting at all. where in the boot process are you ?

does it get to the bios ? grub ? 

It it is not getting to grub, most likely a hardware problem.

If it is getting to grub, boot an older kernel.

---

### Post by lwalper on 2012-04-07
So, I restarted the system, POST displays normally, then to the "blank" screen where things get hung up. I pop out my empty CD tray and the system starts normally. Curious??

I check my BIOS boot order settings (1. USB, 2. CD, 3. HDD). Unchanged from prior startups; burn a ISO image of 12.04 beta2 to CD. Now the CD will not boot - actually the CD drive does not read the newly created bootable CD. (I suppose it's bootable?).

Since I was unable to start this Ubuntu machine I first burned the ISO to disk on a WinXP machine. Everything seemed to go OK, but when I stick the disk in the Ubuntu machine it tells me the disk I just burned on the Win machine is blank. So, after starting Ubuntu sucessfully I burn the ISO to disk - get all messages that everything is OK, burn successful, but the disk does not boot.

Bad CD player perhaps? or bad disk? or ... ???

---

### Post by bodhi.zazen on 2012-04-07
Sounds like a bad .iso or bad burn. Also sounds as if you are able to boot Ubuntu, so not sure where you are going with this thread.

---

### Post by anewguy on 2012-04-07
Does it say the disk is blank, or does it say no boot media found?  If you just burned the ISO FILE to a disk it doesn't work - you have to select the option of burn from an image, then supply the path to the ISO.

It also sounds to me like you have an ubuntu-only machine - no other OS's.  I'm not sure if you would get a grub boot screen at that point. So:

- does it go so far, show an orange/brown screen and then you get the blank screen with the blinking cursor?

- are you using a nVidia video card?

I suspect you need to keep pressing F6 as the system is booting and get to the boot screen where you'll need to add nomodeset to the boot line.

This is just a suspicion, based on what I assume is actually happening versus how you are reporting it.

Dave ;)

---

### Post by lwalper on 2012-04-09
Thanks for everyone's suggestions. I've installed 12.04 from a memory stick and everything now seems to be working OK. Go figure??

---

