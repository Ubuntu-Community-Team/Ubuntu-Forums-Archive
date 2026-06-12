---
title: "Trouble installing ubuntu 12.04 and 11.10 from thumb drive 2 gig size"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by GiantSpider on 2012-05-27
I noticed when attempting to install 11.10 I got a message like 2/1.88 gigs and something about failure. I'm pretty sure my thumb drive is too small.

My 12.04 dvd works though burned from the same .iso. Btw I sum checked both .iso. So at least I'm getting to try ubuntu 12.04. The thumb drive is a Philips. Formatted to fat32 and I tried both .iso with usb pen  drive linux program, has a penguin holding a flash drive. Note I can't get Ubuntu 12.04 nor 11.10 to even try option let alone install.

Here's a link:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) 

Sorry if no links allowed didn't read everything.

---

### Post by Bucky Ball on 2012-05-27
Maybe silly question, but the USB is empty before you try this? FAT32 or formatting are not the issue. It will be reformatted when you install the ISO to the USB with UNetbootin or whatever other app you use anyhow. Linux = EXT* (2,3,4).

---

### Post by GiantSpider on 2012-05-27
Was the first time, the 2nd time it had 12.04 when I use the above program to put 11.10 on the flash drive. I assumed the data was erased.

---

### Post by Bucky Ball on 2012-05-27
Perhaps you should try UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I think it is in the repositories.

---

### Post by GiantSpider on 2012-05-27
Okay, I tried the above software, Unetbootin from the link and I first deleted all the contents of the flash drive tried 12.04, tried to boot twice from the flash drive and simply got a black screen "

verfying dmi pool....

boot error
"
I used ctrl+alt+del to reboot, tried 11.10 on the same flash drive and the same thing happened.

I'm able to boot back just fine from the hard drive btw. :) My Dvd rom works great on my other comp, I tried to install but got nervous about unmounting the file systems or something and aborted. 

 The reason I want to use a flash drive is I don't have a Dvd-rom drive on this computer, its a bottom mount PSU and the cord isn't long enough. I still have Jaunty from when I used Daemon tools last time. Just wanted to try a different approach.

---

### Post by GiantSpider on 2012-05-27
Ok I tried on a different computer install from usb and said 
boot error I hit escape, 
loading from cd/dvd room drive boot error (btw no dvd was in the drive)
I hit escape then it booted and did a forced fsck then it said to do a manual fsck. I had no clue what I wa doing so I just typed in fsck and hit y at all the prompts. 

Now it said says something about 9.04 Jaunty when I'm trying to install 11.10 or 12.04. Now I'm confused. 

Now on a screen with a blue outline and gray back ground its displayed "Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart the GDM when the problem is corrected.

 a red button with ok

Ubuntu 9.04 and something about login.

---

### Post by GiantSpider on 2012-05-27
Ok, I messed around trying to repeat the same thing and I couldn't. The usb drive says boot error then DVD rom drive error and then it just starts Grub and I can pick Ubuntu or Vista.

 Btw my Ubuntu got a graphical error awhile ago, and what I did in the reply above was the closest I got to logging in. I restarted my computer and had my login info ready and blam graphical error. 

  What I want to do is simple, retrieve the data I put on the ubuntu side of the computer, and then install the new Ubuntu, 12.04. I've given up on installing from USB. 

  So I think if I log in without graphics I can log in attach my external hard drive and retrieve the data, its been so long I can't remember if there is anything important or not.

---

### Post by anewguy on 2012-05-27
Do you know what the video adapter is?

When you ran unetbootin - did it complete ok?

Normally, if you just run unetbootin, it will erase all on the flash drive and install the ubuntu environment to it.

---

### Post by GiantSpider on 2012-05-28
Love your icon btw.

 I have a VGA to DVI adapter. The graphics card is a 4890 HD. The computer boots Vista just fine. Monitor is VGA graphics card is DVI. I plugged the monitor into the adapter and the adapter into the DVI slot of the graphics card. 

Yes "When you ran unetbootin - did it complete ok?"

---

### Post by anewguy on 2012-05-28
Another couple of questions:

- is this a laptop?

- do you have a wireless adapter, and is it by chance based on a Broadcom chipset?

thanks for the comment on the icon - I wanted to do something that looked like Bill the cat from the old Bloom County strip, and added a distraction ("DOG!!") after seeing the dog in the movie "Up".

Dave ;)

---

### Post by GiantSpider on 2012-05-29
Desktop, the internet connection is hardwired, my router's wireless is turned off.

---

