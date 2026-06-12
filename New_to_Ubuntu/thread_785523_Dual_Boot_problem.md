---
title: "Dual Boot problem"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by BlackSwordD2 on 2008-05-07
simply put i can't

Ubuntu runs great but XP will not boot. it displays no error messages, it just locks up after i select whether to boot ubuntu (8.4) or xp (a black screen with only the line "Starting" and will not continue to "loading please wait. . . "

i tired asking earlier but the thread died before anything could be solved so i will copy over what was asked of me before.

the contents of my /boot/grub/menu.lst file are as follows:

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, kernel 2.6.20-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1




the output of the code "sudo fdisk -l" is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

Device Boot Start End Blocks Id System
/dev/sda1 * 1 17545 140930181 7 HPFS/NTFS
/dev/sda2 17546 19371 14667345 83 Linux
/dev/sda3 19372 19457 690795 5 Extended
/dev/sda5 19372 19457 690763+ 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x207a4a15

Device Boot Start End Blocks Id System
/dev/sdb1 1 38913 312568641 7 HPFS/NTFS





i've also had errors in Wine where it cant fully find the contents of my C drive, so its been suggested that i need to mount my drive. but it is mounted...maybe thats the problem?

any help would be great, it really sucks being able to only use half of my computer

---

### Post by bumanie on 2008-05-07
I suspect you have a corrupted mbr that is stopping windows loading. You will firstly have to fix the mbr through recovery console. This overwrites grub and thus you will have to reinstall grub via an ubuntu live cd.
To fix windows (assuming you have an xp disk), boot with that and go into recovery console. Choose the number your Win OS is designated as (most likely 1) and hit enter. Answer the questions (Admin. password etc)
Then type FIXBOOT --> enter and answer yes --> enter. The FIXMBR --> enter answer yes --> enter Then exit --> enter
(I think they are the steps and I think to reboot xp one puts in exit rather than reboot)
To fix grub, boot with live cd. Go to terminal and type > sudo grub > root (hd0,1) > setup (hd0) > quit
Now windows and grub should work as expected if mu suspicion is correct. You can try the above or wait for other ideas.

---

### Post by BlackSwordD2 on 2008-05-07
it sounds good, and thanks for the step by step. unfortunatly i have neither disks seeing as i lent my ubuntu to a friend fro him to install and my xp disk is somewhere with my parents a few states away

i've heard that a few people have this error after installing compiz and other eye candy features to ubuntu maybe an error along the way there?

---

### Post by bumanie on 2008-05-07
Could be right re compiz etc. I had a friend who had a similar problem with xp only partially booting and stopping. What I suggested to you is how I fixed his computer. You could try and fix the xp mbr with super grub disk or test disk, (they can both do this) after you get your ubuntu disk back from your friend. Of course if it is compiz etc. you should try disabling that first.

---

### Post by BlackSwordD2 on 2008-05-07
disable as in uninstall or disable as in turn off? and if turn off...how?

---

### Post by bumanie on 2008-05-07
It depends on which desktop effects you have going. You can go into synaptic and remove compiz - don't choose the complete removal option though, in case you want to reinstall easily later. Never done it so not sure exactly what will happen. But I think it would revert to the 'standard' gnome desktop. However, if I went down this path, I would remove one thing at a time and see what effect it was having. Personally, I think it is more likely a corrupt xp mbr causing your problem rather than compiz etc. mucking up xp.

---

### Post by BlackSwordD2 on 2008-05-07
seeing as im not as tech savvy as i'd like to be, what is the xp mbr?

---

### Post by lswest on 2008-05-07
before you try any of that, do this first:
```
sudo gedit /boot/grub/menu.lst
``` and edit the entry for your windows partition so it reads:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map (hd0)
savedefault
makeactive
chainloader +1
``` fixed the error for my PC upstairs (admittedly it was a dual-drive setup, but it might work for your single drive system)

---

### Post by BlackSwordD2 on 2008-05-07
> **lswest said:**
> before you try any of that, do this first:
```
sudo gedit /boot/grub/menu.lst
``` and edit the entry for your windows partition so it reads:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map (hd0)
savedefault
makeactive
chainloader +1
``` fixed the error for my PC upstairs (admittedly it was a dual-drive setup, but it might work for your single drive system)

well it didn't like that much

 it gave me the error message 

Error 11: unrecognized device string

---

### Post by lswest on 2008-05-07
hmm, and if you leave out the map bit? Also, be sure to tab the (hd0) bit out so it's in line with the rest of the entry.

---

### Post by BlackSwordD2 on 2008-05-07
it was the same situation as in the begining, so no error message just locks up

---

### Post by lswest on 2008-05-07
> **BlackSwordD2 said:**
> it was the same situation as in the begining, so no error message just locks up

hmm, only other options i can suggest is ```
map (hd0)(hd0)
``` or ```
map (hd0)(hd1)
map (hd1)(hd0)
```
but i don't think those will work, maybe give the other suggestions a try then.

---

### Post by BlackSwordD2 on 2008-05-07
> **lswest said:**
> hmm, only other options i can suggest is ```
map (hd0)(hd0)
``` or ```
map (hd0)(hd1)
map (hd1)(hd0)
```
but i don't think those will work, maybe give the other suggestions a try then.

well thanks anyway

---

