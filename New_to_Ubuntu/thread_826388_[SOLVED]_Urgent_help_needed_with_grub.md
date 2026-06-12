---
title: "[SOLVED] Urgent help needed with grub"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Zacariaz on 2008-06-11
Well, I deleted a ntfs partition with fdisk and now all I get when trying to boot is an error 17 (i think)

I using a live cd right now, but have no idea how to fix the problem. all the various linux partitions seems to be there when using fdisk -l, so what do I do?

Thanks

---

### Post by drs305 on 2008-06-11
Try this link:
[How to restore Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Duck2006 on 2008-06-11
In the terminal from the live cd type.

sudo grub

find /boot/grub/stage1 "with what it comes back use in the next step"
root (hdx,y)
setup (hd0)
quit

This may help.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Yuki_Nagato on 2008-06-11
[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

This people also were getting the Error 17, but were apparently fixing it by changing the configuration of the hard drives in the BIOs settings.

[http://users.bigpond.net.au/hermanzone/p15.htm#17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

A little more help on Error 17.

---

### Post by Zacariaz on 2008-06-11
Well, now I get to the grub menu, but when I try to boot I get:
Error code 17: Cannot mount selected partition.

I'll try to do some more reading, but if anyone knows how to solve it, I would be gratefull for a quick fix.


One issue which has come to my attention is that s lot of free space is included in my extended partition, apperently, when I first installed xubuntu, on of my ntfs partitions was included in the extended partition. I don't see how this could be the problem though.

Gpsrted states that I have a 91.78 GiB extended partition (sda2) including an ext3 (sda5) 19.13 GiB, a linux-swap (sda6) 894.21 MiB and 71.78 GiB unallocated space.

---

### Post by meierfra. on 2008-06-11
In addition to reinstalling grub, you will also have to edit the file "/boot/grub/menu.lst" on the ubuntu partition. 

This is what happened:  Say Ubuntu used to be the fourth partition on the hard drive.  Then it will  now be the third partition. But grub is still looking on the fourth partition for the files "stage2" and "menu.lst". For this reason grub needs to be reinstalled. drs305 and duck2006 already gave you instruction for that. Once you  reinstalled  grub, the Grub Menu will appear. But when you select Ubuntu you still will get error 17. Because the grub  menu still contains references to partition 4.

So once the grub menu appears do this:

Select Ubuntu, but do not press enter. Press  "e" instead. At the new screen press "e" again. Change

"root (hd0,3)" to "root (hd0,2)"

of course the numbers might be different,  Do not change to first number, but lower the second number by 1. (After you changed it, it should be the same as the output from "find /boot/grub/stage1".

Press "enter" and then "b" to boot.

This should boot you into ubuntu.  Once you booted into Ubuntu, you still need to make this change permanent:

Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```
(l is a lowercase L)

change

#groot (hd0,3)

to

#groot (hd0,2)

(that is lower the second number by 1)

Save the file. In the terminal type

```
sudo update-grub
```

For any additional help, please post the output of

```
sudo fdisk -l
```
(again l is a lowercase L)

---

### Post by meierfra. on 2008-06-11
Didn't see you last post before a posted mine. Anyway that should solve your problem.

---

### Post by Zacariaz on 2008-06-11
I did boot ubuntu and I'm confidend I'll be allright now.

Thanks a lot for all your help.

---

### Post by Zacariaz on 2008-06-11
Just in case anyone should have a solution for the earlier mentioned issue with a lot of unallocated space in the sda2 exended partition, here is the output from fdisk:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f3440d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14592    96237382+   f  W95 Ext'd (LBA)
/dev/sda5            2612        5108    20057089+  83  Linux
/dev/sda6            5109        5222      915673+  82  Linux swap / Solaris
```

edit:
it would also be nice if I somehow could fix the fact that fdisk/gparted shows sda5/6 with wrong designations.

---

### Post by meierfra. on 2008-06-11
> I somehow could fix the fact that fdisk/gparted shows sda5/6 with wrong designations.

???? I don't see  anything wrong.


> Just in case anyone should have a solution for the earlier mentioned issue with a lot of unallocated space in the sda2 exended 

You have various possibilties:

1) Increase the size of your ubuntu partition.

2) Create a /home partition

3)  Create a Data partition.

4)  Increase the size of the Windows partition.

5)  Any subset of the above.

6)  Do nothing. Just wait until you run out of space somewhere

7)  Install a different OS:[ http://www.distrowatch.com/]("http://www.distrowatch.com/")

Just let us know what you would like to  to do.

I personally would suggest a Data partition, but I would guess you'll  find more people recommending a  /home partition. Either of whose makes upgrading and/or reinstalling easier.

---

### Post by Zacariaz on 2008-06-11
> **meierfra. said:**
> ???? I don't see  anything wrong.
What I meant to say was that sda5/6 should be sda3/4, at least thats the numbers grub goes by.

As for the unallocated space I am planning to install another OS, however, I thought that I might run into trouble with this configuration, but if you say that isn't a problem, I'll believe that.

Once again, thanks.

---

### Post by meierfra. on 2008-06-11
> What I meant to say was that sda5/6 should be sda3/4, at least thats the numbers grub goes by.

Grub starts counting at zero. So grub numbers are always one less than one would think.

For example (hd0,4) really means:  fifth partition on the first hard drive.

>  but if you say that isn't a problem

That is exactly what I'm saying.

---

