---
title: "Windows dual boot problem"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by simon30 on 2014-04-14
Hi, I'm a new user and have done a very, very silly thing and need help already!

I wanted to try Ubuntu now that Windows XP is stopping support so I followed the instructions and created a USB bootable 13.10 Ubuntu to try.  I liked and went to the next step of creating a partition on my hard drive and adding Ubuntu so that I can dual boot.
All good so far!  However I was finding that some things didn't work with 13.10 and the videos and help all referred to 12.04 so I decided to "downgrade"

I discovered that this wasn't possible so decided to format the new partition and then boot from the USB stick and re-install.
DISASTER!  As you no doubt know (I didn't) the dual boot option screen (Grub?) happens before my PC looks for any boot devices so all I get now is the Grub Rescue screen.

Is there anything I can do?  

The only thing I can think of is to borrow another PC and put my HD in it and re-install Ubuntu, which hopefully would then boot on my own PC, but I prefer a simpler way if possible.


I know I am an idiot BTW, so don't necessarily feel the need to tell me!!

Simon

---

### Post by stalkingwolf on 2014-04-14
shut your computer off. wait for a count of 10. plug your usb stick in and reboot.  hit the key that will bring up your optional boot menu.  select your usb drive.  once it boots
proceed with the install. when you get to the partitioning part select manual.  then select the partition you want and select change.   if you have any problems ask here or message me.

---

### Post by Impavidus on 2014-04-14
The grub menu shows up after the bios looks for booting devices. You must be able to hit some key (which one varies amongst hardware) to enter the bios and select the boot device.

Most instructions aimed at 12.04 also work on 13.10. The differences aren't too large.

---

### Post by simon30 on 2014-04-14
Many thanks both of you.  I feared that Grub might be written pre-boot as (I thought) I had tried to boot from the USB stick.  I must have done something wrong because it's all fine now.



Regards  Simon

---

### Post by aeyeaws on 2014-04-14
dont be afraid of reinstalling windows, if you have a product code go for it , winsnows needs to be reinstalled every 3 months , honest.

---

### Post by squakie on 2014-04-15
> **aeyeaws said:**
> dont be afraid of reinstalling windows, if you have a product code go for it , winsnows needs to be reinstalled every 3 months , honest.You did catch it was XP - no longer supported?  Also, if you know what you are doing there is no need to reinstall any OS, Windows included, every 3 months.  Some of us have run the same Windows install for years, but we know how to clean up after ourselves and keep the system tuned.

At any rate, your post doesn't contribute to the problem the OP has posted.  Please refrain from posting into a thread unless your reply concerns the problem at hand ("I have the same problem, doing xxxx", "here'my solution", "we need more information", etc.).

You see, even my reply to you does nothing for the thread.   Your post just dilutes the discussion.

---

