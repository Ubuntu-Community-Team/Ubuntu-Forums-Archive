---
title: "Ubuntu Install won't recognize Windows 8.1"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by avidhunter2 on 2014-07-05
I'm a kneu B trying to install Ubuntu onto an ACER laptop which already has Windows 8.1 installed.  I want this to be a dual boot computer.  The process I'm using is to boot from a live Ubuntu DVD and then run install.  Every attempt has brought up a screen which says there are no other operating systems detected and provides the option to erase the entire hard drive or other.  I do note that ubuntu did mount all four of the partitions created by the OEM installation of win 8.1. How do I get Ubuntu to recognise the existence of win 8.1 so I can create a dual boot machine.

---

### Post by sotiris2 on 2014-07-06
If I understand correctly you have not installed Ubuntu yet. Is there free/unallocated space on the disk? I don't mean having 100gb free on your C:\ partition but rather your four partitions being a total of 400gb on an actual 500gb drive. 

Running Gparted from the cd (select I want to try Ubuntu instead of Install Ubuntu when prompted) and posting a screenshot would be great. In fact a screen of your Windows disk management utility would do as well.

If you have to shrink partitions do it from WINDOWS and do boot to Windows a couple of times. 
Read [this](https://help.ubuntu.com/community/WindowsDualBoot) and [this](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions) as well.

---

### Post by Impavidus on 2014-07-06
This may also be good to read: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

BTW, you confused me for a moment with your uncommon spelling of noob. Kneu, pronounced as /knø:/, is the dutch name for the common linnet, a bird.

---

### Post by avidhunter2 on 2014-07-08
Here is the gParted screen shot;

well that didn't work so how do I post a screen shot?

---

### Post by sandyd on 2014-07-08
Clicking on manage attachments should allow you to attach a screenshot.

---

### Post by avidhunter2 on 2014-07-08
Ok lets try this screen shot;
[ATTACH=CONFIG]254567[/ATTACH]

---

### Post by westie457 on 2014-07-08
Take a look at the links in this post. [http://ubuntuforums.org/showthread.php?t=2216732&p=12986474#post12986474](http://ubuntuforums.org/showthread.php?t=2216732&p=12986474#post12986474)

They should help you.

---

### Post by yancek on 2014-07-08
With windows 8, you are dealing with UEFI rather than master boot record, GPT partitioning plus microsofts attempt at security;  Secure Boot.  You will have to check into these as well as FastBoot or something similarly named which deals with hibernating.  You have a number of partitions which look a little unusualy but then I have not used windows 8 on an actual machine.  460MB Recovery partition seems a bit small, don't know?  The boot partition seems the appropriate size, don't know what sda3 (unknown) is but can't be much on it.  What is referred to as sda4 is your primary windows system partition which is probably what you need to shrink to make room for Ubuntu.  There is no place to install it currently with out overwriting one on your windows partitions.   You have a small diagnostic partition - sda5, not sure what that is then you have sda6 which is labelled "Push Button Reset" and is nearly 16GB.  Don't know what that is but seems the right size for a recovery partition.    

Not knowing what all these partitions are, the only thing I would suggest is as suggested above; to resize (shrink) the main windows partition from WITHIN windows and create another partition for Ubuntu.  If you are unfamiliar with this process, a little reading is in order.

---

### Post by avidhunter2 on 2014-07-12
I made a mountain out of a mole hill with your suggestions.  However, here is where I stand now. From within windows 8.1 I repartitioned the primary partition and created a 100GB unallocated partition.  Now when I try to install Ubuntu it still won't recognize the existence of windows but under the "other" option I can format the new partition.  The questions now becomes what do I format it to? and If I install Ubuntu on it how do I set up a boot record so that I can still boot in windows?

westie457 -- I fail to understand how the information on the referenced link applies to this issue...what am I missing?

---

### Post by Vladlenin5000 on 2014-07-12
The links tell you how to disable fastboot and hibernation in Windows 8. Those steps are needed in order for the NTFS partitions to be recognized. The installer can't see hibernated systems, apparently...

You need also to read and understand the specifics of dual-booting in a UEFI system: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

