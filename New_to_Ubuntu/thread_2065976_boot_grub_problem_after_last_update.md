---
title: "boot grub problem after last update"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by s1baker on 2012-10-03
hello,
After the last update I am not able to boot directly into my hard drive.
What I get now is first a black screen with the list of all the kernel versions, from the current one, then the recovery one, then a list with 
all the the previous versions. I can select the top one, or the latest one, and boot in just fine. What do I need to do to fix the grub so that I can boot ?


My system setup when this happened :
(desktop) xubuntu 12.04.01
I had 1 hard drive in the box on a ribbon (IDE) and I had 1 hard drive
outside the box connected with USB. Both hard drives have the same
identical xubuntu 12.04.01 on them, installed separately, so they both
have unique UID numbers. I could boot off of either hard drive by selecting 
the hard drive priority in the BIOS ( Biostar) *and* I was using the USB drive when this happened.


After the update started, in the middle of the update, a box appeared asking if I wanted to install a grub, and there were 3 check boxs for both sdb1 and sda1, so I checked both. So now at boot up, I get the black screen with the boot selections on either hard drive I use to boot up.

---

### Post by grahammechanical on 2012-10-03
If I understand you correctly, you only have one Ubuntu operating system on each hard disk. Correct? No other operating systems?

If we only have Ubuntu then we do not see a Grub menu. If we dual boot with another OS or we install another Ubuntu on another partition then we see a Grub menu.

By updating Grub with both hard disks connected and by ticking to install Grub on sda1 and sdb1, you now have Grub configuration files that see more than one OS and they are on each hard disk. Therefore, you get the Grub menu that you see whatever hard disk you select to boot from in the BIOS.

I do not have this set up. so, I can only make a suggestion.

1) Disconnect one hard disk.
2) Boot into Ubuntu on the remaining hard disk.
3) Open a terminal and run the command

```
sudo update-grub
```

you will be required to enter your password.

4) Test by re-booting to see if you get a Grub menu.

5) Repeat for the other hard disk.

You need to put on each hard disk a Grub configuration file that only sees one Ubuntu operating system. Then when you boot into a hard disk you will not see the Grub menu.

This I think is the way to get things back to as you like.

Regards.

---

### Post by s1baker on 2012-10-03
Thanks grahammechanical

I used grub-update on both HD's and they both boot now.

yes, I have only one OS on each HD, ( both 12.04.01 64 bit )
I have one HD in a HD enclosure that I use on the USB, but
when I disconnect the HD that is on the ribbon that is inside the box,
my BIOS doesn't reconize the external USB drive.
I had to take the USB driveout of the enclosure and connect it to the ribbon inside the box
to get it to boot so that I could do the grub-update.

---

