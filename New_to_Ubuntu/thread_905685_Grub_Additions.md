---
title: "Grub Additions"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-08-30
I use Qgrub editor to mess with anything.
I've got the Ubuntu Hardy Heron, and I used Disk Director to resize the ext3 partition so I could copy a backup over to the NTFS partition I resized the ext3 to create.
The NTFS is primary, Not quite sure what the steps would be to enter this into the Grub menu as an addition with Qgrub.

Any pointers would be wonderful.

---
So far I've tried reinstalling Grub, and that doesn't work. I'm not quite sure what to be pointing to. It's the second partition, and I've pointed grubloader to that but when I click on Windows to startup from the grub menu it errors. Something about a filepath.

---

### Post by Elephantman5 on 2008-08-30
I really don't know what to do.

Now it says Error 13: Invalid or unsupported executable format

---

### Post by caljohnsmith on 2008-08-30
If you can't boot into Ubuntu at all at this point, boot your Live CD and do the following in a terminal:
```
sudo fdisk -lu
```
Find your Ubuntu partition in the form /dev/sdX, and use that:
```
sudo mount /dev/sdX /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output of all the above commands, and we can go from there.

---

