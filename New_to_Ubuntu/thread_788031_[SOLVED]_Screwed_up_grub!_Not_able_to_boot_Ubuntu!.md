---
title: "[SOLVED] Screwed up grub! Not able to boot Ubuntu!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by mrdosa on 2008-05-09
I have a 40 GB, 4 partitioned HDD. With WinXP on 1st partition followed by a FAT32 partition followed by Ubuntu and then finally another FAT32 partition.

I recently installed kubuntu on my last partition. The boot menu showed ubuntu 8.04
ubuntu 8.04 [recovery]
memtest +86

other op sys:
windows xp
ubuntu 8.04 [on sda 6]
ubuntu 8.04 [recovery] on sda6

and so on.

Well, I then unintentionally formatted the last drive [having kubuntu] using windows partition manager.

When I restarted I got a grub error 17.

I panicked and used the windows disk and ran fixmbr!

I thought I could use the live cd to reinstall grub.

But when I ran find /boot/grub/stage1 on live cd, instead of getting (hd0,5) [i am damn sure ubuntu is here] i got a message saying (hd0,4)

nevertheless I tried setting it up.
This time when I restarted i got the grub menu, but whn i choose ubuntu I again get error 17


I tried Live CD again, to mount the drives my self using
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root


But it said unable to mount sda6, either its already mount or /mnt/root is busy

Please help me get ubuntu back!!!:confused:

---

### Post by aspen_dv on 2008-05-09
once you boot with your CD, what fdisk -l says?

---

### Post by mrdosa on 2008-05-09
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb68fb68f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1218        3713    20049120    f  W95 Ext'd (LBA)
/dev/sda3            3714        4865     9253440    b  W95 FAT32
/dev/sda5            2434        3651     9775048+  83  Linux
/dev/sda6            3652        3713      497983+  82  Linux swap / Solaris
/dev/sda7            1218        2433     9767457    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by newbuntuxx on 2008-05-09
I just had the same problem.

When the grub loader loads at bootup, press e. You will see the drives that are to be mounted. You will probably see: hd0,5. Edit them for: hd0,4 and then press b. 

If ubuntu starts, got to: /boot/grub/menu.lst and make the changes there as well. find the lines with: hd0,5 and change them to: hd0,4

hope this helps.

---

### Post by mrdosa on 2008-05-09
> **newbuntuxx said:**
> I just had the same problem.

When the grub loader loads at bootup, press e. You will see the drives that are to be mounted. You will probably see: hd0,5. Edit them for: hd0,4 and then press b. 

If ubuntu starts, got to: /boot/grub/menu.lst and make the changes there as well. find the lines with: hd0,5 and change them to: hd0,4

hope this helps.


Well to try that will have to reboot. I am online on LIVE CD. 
Will let you know how it works out to be.

---

### Post by aspen_dv on 2008-05-09
Looks like your reformat the wrong partition. What mount command say? 
Can you mount /dev/sda5 somewhere and see if you can recover you data. 
Then I guess, reinstall ubuntu.

---

### Post by mrdosa on 2008-05-09
> **aspen_dv said:**
> Looks like your reformat the wrong partition. What mount command say? 
Can you mount /dev/sda5 somewhere and see if you can recover you data. 
Then I guess, reinstall ubuntu.

Well, I didnt reformat the wrong partition. That I am sure of, as from live CD I could explore my ubuntu home files.

:confused:

---

### Post by mrdosa on 2008-05-09
> **newbuntuxx said:**
> I just had the same problem.

When the grub loader loads at bootup, press e. You will see the drives that are to be mounted. You will probably see: hd0,5. Edit them for: hd0,4 and then press b. 

If ubuntu starts, got to: /boot/grub/menu.lst and make the changes there as well. find the lines with: hd0,5 and change them to: hd0,4

hope this helps.

Thats sexy buddy!
It has solved my problem.
Can someone explain why this happened?? 

BTW, now I dont seem to get that ubuntu loading animation. Instead get text!

Well, I certainly didnt have to re-install!!
Thanks guys!!:)

---

### Post by Prestige08 on 2008-05-09
Usually the best thing to do is just reinstall Kubuntu on the fourth partition.  I had a similar experience where I had two systems on two partitions, and I had accidentally wiped Ubuntu using XP's disk manager.  I wet in on the live CD and reinstalled Ubuntu, and after that, it worked fine.

---

