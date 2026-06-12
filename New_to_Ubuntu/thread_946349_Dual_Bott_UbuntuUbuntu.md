---
title: "Dual Bott Ubuntu/Ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by AnxietyDrive on 2008-10-13
Hi All
I had two PC's running Ubuntu.
I have now taken the drive from one and put it in the other. 
So that I can run both Ubuntu installs separately on the one machine I'll need Dual Boot.
How do I do this?
Ta
AD

---

### Post by itix on 2008-10-13
You'll have to add the new hard drive to /etc/fstab. You'll also have to get grub to recognize the new hard drive as a bootable one. I'm not very good at either though.

---

### Post by Orange_and_Green on 2008-10-13
I'm assuming the two PCs are identical (or that, at least, the two motherboards have the same chipset. If this is not the case, strange things might happen when you boot the second OS. If in doubt, a clean reinstall to the second disk might be an easier option in the long run... anyway...)

could you please post the output of 
```
sudo fdisk -l
```?

Also, I wonder if I may ask you why you need to dual-boot from the same OS twice?

---

### Post by handydan918 on 2008-10-13
> **AnxietyDrive said:**
> Hi All
I had two PC's running Ubuntu.
I have now taken the drive from one and put it in the other. 
So that I can run both Ubuntu installs separately on the one machine I'll need Dual Boot.
How do I do this?
Ta
AD

If you simply reinstall GRUB, it should autodetect both installations. Indeed, as previously noted, why would you want to identicall O/S's? If all you want to do is to access your data, you can just mount the partition, edit fstab to make it stick, and away you go.

---

### Post by AnxietyDrive on 2008-10-13
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8f3f8f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35724   286952998+  83  Linux
/dev/sda2           35725       36481     6080602+   5  Extended
/dev/sda5           35725       36481     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1554111

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2398    19261903+  83  Linux
/dev/sdb2            2399        2491      747022+   5  Extended
/dev/sdb5            2399        2491      746991   82  Linux swap / Solaris



The reason for two separate bootable drives is a matter of increased security. One drive have sensitive and valuable data, the other is used to access the internet. Only data that has been heavily screened can pass from the 'Net' drive to the 'Main' one. If the Net drive is compromised in any way..... it is deleted and a fresh install placed!

I tried re-installing grub to no effect.

I installed a grub editor - but its double dutch to me.

I can select either drive via the bios setup and selectively boot that way, but would much rather have an easier method!

AD

---

### Post by handydan918 on 2008-10-13
> **AnxietyDrive said:**
> 
The reason for two separate bootable drives is a matter of increased security. One drive have sensitive and valuable data, the other is used to access the internet. Only data that has been heavily screened can pass from the 'Net' drive to the 'Main' one. If the Net drive is compromised in any way..... it is deleted and a fresh install placed!

AD

You have my sympathy. The post-traumatic effects of having been victimized by the many Windows security issues often leaves users trembling in a small corner of the battlefield. 
Running linux is a little like driving around in an Abrams. Sure, it can be hit, but not easily. You won't casually pick up viruses like you used to with Windows. If you are so concerned about data security, you might look into full disk encryption, as an alternative.
And try to relax....:)

---

### Post by C.S.Cameron on 2008-10-13
You should be able to get your choice of hard drives at startup by just adding something like this at the bottom of boot/grub/menu.lst

title  HDD No 2
root   (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1


Oops, forget above, it is for a second HDD with windows.

I think the second HDD needs to be identified in menu.lst similar to the first, with correct kernel, UUID and root ().
I recall I copied this from menu.lst on the second hard drive and pasted it to the bottom of menu.lst on the first hard drive and changed the root to (hd1,0) 
If you do a new install with both disks attached, menu.lst will include an option for the second drive automatically.

---

### Post by Orange_and_Green on 2008-10-15
Hi :) Here I am again.

While C.S. Cameron is perfectly correct that reinstalling will automatically solve the problem, there is actually a much easier and quicker way to do this. If you can selectively boot from either of the two disks that's great, it will simplify our task enormously.

Please boot from your "secondary" disk first (the one you'll be using less). Open up a terminal and type:
```
ls /boot/vmlinuz*
```

This will give you a list of all the kernels on that installation. Make a note of the exact name of any one of your choice (I'd suggest the latest kernel , so the one with the highest trailing number).

Then, type:

```
ls /boot/initrd.img*
```
And make a note of the exact name of the file that matches the number of the kernel you wrote down before (take the one without the ".bak" at the end.)

I hope this was clear enough, if it wasn't, please ask again.

Next, reboot from the other, "main" installation. Then, do:
```
gksu gedit /boot/grub/menu.lst
```

Scroll down the text and add these lines at the bottom:

```
title Alternate Ubuntu
root (hd1,0)
kernel		/boot/INSERT_THE_FIRST_FILE_NAME_HERE root=/dev/sdb1 quiet splash
initrd		/boot/INSERT_THE_SECOND_FILE_NAME_HERE
```

And save.

Finally, do this:

```
gksu gedit /boot/grub/device.map
```
And make sure it reads:

```
(hdo) /dev/sda
(hd1) /dev/sdb
```

(If it doesn't, then edit it accordingly.)
Reboot and now you should be able to choose either installation.
Tell us how it went, and good luck :KS

---

### Post by C.S.Cameron on 2008-10-15
Thanks for a better guide, I sorta went brain dead on the above post.

I find that I need to add savedefault, boot to get it to work, however I did not modify device.map.
What works for me is:

title        Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (on /dev/sdb1)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.27-5-generic root=UUID=487c08ce-be53-4f38-8484-13652f6c7271 ro quiet splash
initrd       /boot/initrd.img-2.6.27-5-generic
savedefault
boot

or 

title        Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (on /dev/sdb1)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.27-5-generic root=/dev/sdb1 ro quiet splash
initrd       /boot/initrd.img-2.6.27-5-generic
savedefault
boot

---

