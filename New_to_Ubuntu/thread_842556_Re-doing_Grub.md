---
title: "Re-doing Grub"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Law506 on 2008-06-27
Recently updated my Windows XP side to Service Pack 3 and the thing crashed in a beautiful array of flames and agony.  Fixed that side of the computer, but my Ubuntu 8.04 side, installed on separate HDD, wont load up GRUB anymore.  Computer just goes straight to XP.

I have read through the forums and tried the LiveCD.
I mounted and navigated to the mount point on my HDD
Opened a terminal and typed
sudo chroot .

then,

sudo update-grub

this is where the problem lies, it gives me on the first two lines a creating failed error in regards to /dev/null, permission denied.

then the last line of the process says /dev/null, permission denied.

is there something in those step that I missed or is there another method of getting GRUB back online that someone else knows?

Thanks.

---

### Post by Duck2006 on 2008-06-27
From the live cd open the terminal and type

sudo grub

find /boot/grub/stage1 "with what this gives you use in the next step"

root (hdx,y)

setup (hd0)

quit

some reading on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Law506 on 2008-06-27
Awesome, I am stuck at work right now, but when I get home I will try it and do some reading.

Thanks.

---

### Post by elmer_42 on 2008-06-27
[This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is the guide I used after I had to re-install Windows. The first method worked perfectly for me, and in less than 10 minutes from the re-install's end, I was back in Ubuntu.

---

### Post by jryprt on 2008-06-27
Here is a great guide [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kansasnoob on 2008-06-27
To me the hardest part of this the first time I had to do it was understanding what numbers needed to replace the x and y in {root (hdx,y)}.

Well, actually the first time was easy because I had only one hard drive and a totally "out-of-the-box" Ubuntu set up that I added XP to as my first dual boot, so my root was (hd0,0), but life got more complicated since then.

Anyway the section "Overwriting the Windows bootloader" in the link provided by Elmer_42 makes it pretty much foolproof, that's why I added a "Thank You" for his helpful post:)

Also Hermanzone's  Quick Guide to GRUB's Numbering System was a big help to me:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

