---
title: "Grub loading error"
date: 2008-12-06
forum: Other OS Talk
---

### Post by ironmagma on 2008-12-06
Hello there,

I have two hard drives on my computer, one of which I have Ubuntu installed on (Gutsy, I believe), and another which has Fedora Core 2 installed (yes, 2).  Whenever I try to boot directly from the second hard disk with FC2 on it, I get Grub Error 15, so I would like to start the machine from the GRUB on disk 1 if possible, but I have no clue how to do this.  What sorts of commands would I put into the boot script on the ubuntu disk to do this?

Thanks in advance :)

---

### Post by caljohnsmith on 2008-12-06
If you first open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
That will pull up your Grub's menu.lst, and at the bottom add:
```
title Fedore Core 2 Grub Menu
configfile (hd1,X)/boot/grub/menu.lst
```
But replace X with the partition Fedora is on, but keep in mind that Grub's numbering starts at 0, not 1, so that:
```
(hd1,0) = 2nd drive, 1st partition
(hd1,1) = 2nd drive, 2nd partition
(hd1,2) = 2nd drive, 3rd partition
...etc.
```
That should then give you a link to your Fedora's menu.lst in your Ubuntu menu.lst, and in your Fedora's menu.lst you should use the same (hd1,X) value as above in all your Fedora entries to get them to work. If you need more specific help, how about posting:
```
sudo fdisk -lu
```
And please identify all your partitions. Otherwise let me know how it goes.

---

### Post by ironmagma on 2008-12-06
Well, I tried that, but when I selected the Grub menu, it gave me another Error 15, which I believe is "File not found".

I think the problem is that (it appears that) there is no /boot/grub/menu.lst file on (hd1,1).  How would I add one / what commands should I put in it?

---

### Post by ironmagma on 2008-12-06
Well, I figured it out... apparently the list was actually in the 0 partition instead of 1 (I knew you had warned me about it, but I sort of assumed that grub would be on the bigger partition) and it was also under /grub/grub.conf or something to that effect.

---

