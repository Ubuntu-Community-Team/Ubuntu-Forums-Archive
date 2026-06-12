---
title: "[SOLVED] reinstall grub"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by chazn85 on 2008-11-11
ok so heres the problem i needed to reinstall vista so i have done and i am now trying to reinstall grub to boot both partitions.  Vista resides in hd0 and ubuntu in hd1.

Ive tried a sudo grub, root (hd1,0) setup (hd1) on the live CD, but it still boots directly to windows.  Do i need to install grub on hd0?

Thanks all

---

### Post by bumanie on 2008-11-11
> **chazn85 said:**
> ok so heres the problem i needed to reinstall vista so i have done and i am now trying to reinstall grub to boot both partitions.  Vista resides in hd0 and ubuntu in hd1.

Ive tried a sudo grub, root (hd1,0) setup (hd1) on the live CD, but it still boots directly to windows.  Do i need to install grub on hd0?

Thanks all

You need to setup (hd0). Doing as you have done has got grub looking for vista on the same drive as ubuntu is on.

---

### Post by chazn85 on 2008-11-11
so i have done a root (hd,0,0), setup (hd0) and i get cannot mount selected partition!

---

### Post by bumanie on 2008-11-11
No it is > sudo grub > root (hd1,0) > setup (hd0) This gets grub set to boot from the first partition of your second drive and grub knows to look for an OS on the first hard drive. When it finds vista on (hd0) it hands the booting of vista over to vista's bootloader.

---

### Post by YaroMan86 on 2008-11-11
Okay, here's the complete procedure. I think you've been fed insufficient info.

1. Run the LiveCD and choose to run the LiveCD (NOT the install option.)
2. Open up the terminal.
3. Type: ```
sudo grub
```
4. Type: ```
find /boot/grub/stage1
```
5. It will output something like (hd0,0) Remember the code.
6. Type: ```
root (hdx,y)
``` where x and y are the numbers you got.
7. Type: ```
setup (hdx)
``` To install GRUB to that hard disk's MBR.
8. Type: ```
quit
``` to exit GRUB.
9. Type: ```
sudo shutdown -r now
``` to restart our computer.

Hope that helps.

---

### Post by chazn85 on 2008-11-11
ok so i did that and i do now get a grub boot menu only i cant boot into it error is

cannot mount partition

---

### Post by bumanie on 2008-11-11
Post output of > sudo fdisk -luThis command works from a live cd.

---

### Post by chazn85 on 2008-11-11
i think what i need is to get grub to boot from the first disk but look for an OS on the second hard drive, these are the times you know you hate windows unfortunatly i cant dial into work without it currently a virtual machines wont allow me to due to firewall settings

---

### Post by chazn85 on 2008-11-11
output is 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   625139711   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3af0f4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   195318269    97659103+  83  Linux
/dev/sdb2       195318270   585938744   195310237+  83  Linux
/dev/sdb3       585938745   601586054     7823655   82  Linux swap / Solaris

---

### Post by karrank% on 2008-11-11
would supergrub work? or have you tried it? worked for me last time I had an os disappear from a dualboot...

---

### Post by chazn85 on 2008-11-11
> **karrank% said:**
> would supergrub work? or have you tried it? worked for me last time I had an os disappear from a dualboot...

Unfortunatly it doesnt seem as though you can burn a CD in the live CD so to speak

---

### Post by YaroMan86 on 2008-11-11
Try switching your disks in the boot order in your BIOS. That actually solved a problem I had similar to yours.

---

### Post by bumanie on 2008-11-11
That code should have worked - don't know why it can't mount the partition. Were trying to boot into vista or ubuntu when you got that message? If it was vista, that could indicate that vista was not shutdown cleanly - linux won't mount filesystems that it sees as 'dirty', as in not shutdown properly.

---

### Post by chazn85 on 2008-11-11
> **YaroMan86 said:**
> Try switching your disks in the boot order in your BIOS. That actually solved a problem I had similar to yours.

Will give that a try stranger things have happened!

---

### Post by chazn85 on 2008-11-11
> **bumanie said:**
> That code should have worked - don't know why it can't mount the partition. Were trying to boot into vista or ubuntu when you got that message? If it was vista, that could indicate that vista was not shutdown cleanly - linux won't mount filesystems that it sees as 'dirty', as in not shutdown properly.

I was trying to boot into ubuntu

---

### Post by bumanie on 2008-11-11
Sorry, I have to go now, but there are plenty of others who visit the forum who can help.

---

### Post by chazn85 on 2008-11-11
> **YaroMan86 said:**
> Try switching your disks in the boot order in your BIOS. That actually solved a problem I had similar to yours.

totally fixed it cant believe i was so stupid!!  my sincerest apologies and thanks to you 

PS and all that helped

---

