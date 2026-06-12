---
title: "boot from cd ok, but from disk : (initramfs)?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by infoanalysis on 2008-05-09
amd 64 dual core 3800 with 2048 mg ram
8.04 for amd 64
boots ok from cd but when I installed it on the 250 gig hardrive in any of the options guided or manual as per the softpedia directions for 8.04 lts, it always come up with initramfs prompt. I have tried the safe mode as well to no effect.

I have tried many variations of partition sizes, any advice appreciated

At first I tried to dual boot with XP then when that failed I formated the entire disk, still no luck

John

---

### Post by Fenris_rising on 2008-05-09
hi there

i had this  problem as have a few others. there are, it seems, various reasons. for me i had to add 'pci=nomsi' without quotes to the boot up string. hit esc at boot up to get the 'grub boot  menu' up 'e' for edit and add the above argument to the end of the string as follows;

/boot/vmlinuz-2.6.20-15-generic root=UUID=aa801caf-6244-45c8-972a-8f5c25eb31b8 ro quiet splash pci=nomsi

press enter then b for boot.

this may sort you out but there are other solutions depending on why your system is playing up. if this does work you will need to edit the 'menu.lst'
which is in /boot/grub/ add the argument to the same line as you did in the boot string and save (you will need to be root) there are plenty of other alternative answers on here if you need them.

---

### Post by infoanalysis on 2008-05-10
Thanks for you're help, but it did not change a thing still comes up initramfs

---

### Post by ahmedh on 2008-05-10
I have the same problem too, but I used Wubi to install and it worked perfectly for about a month. Now all I see in bootup is the intramfs prompt. Help anyone?

---

### Post by infoanalysis on 2008-05-10
I still have this problem. I tried the alternative cd and added pci=nomsi on the boot up string as directed. Any Help?

---

