---
title: "[SOLVED] Grub menu disapeared"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by obscur156 on 2008-07-06
Hi guys,like the title said my grub menu disapeard.So my computer keeps on rebooting in a loop all the time because it does not see the grub menu.

I have windows and hardy.The only way i can boot to an OS is to pop in a ubuntuCD and select the option "boot from fist hard disk".
I have even tried this [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
Even if it says suceed in the terminal ,i still have no grub menu.

Hoping some power user can help.
Thanks in advance,best regards.

---

### Post by ibutho on 2008-07-06
If you can boot into your Ubuntu installation, try Applications -> Accessories -> Terminal
```
sudo grub-install /dev/sda
```
Change /dev/sda to the name of your hard disk if it isn't /dev/sda.

---

### Post by obscur156 on 2008-07-06
Thanks ibutho for the quick reply but still no luck.I still have no grub menu at boot.
I am sure thatdev sda is correct.

ob@liberty:~$ sudo grub-install /dev/sda
[sudo] password for ob: 
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
ob@liberty:~$ 

Any idea ?

---

### Post by caljohnsmith on 2008-07-06
Which is your Ubuntu partition? Please post the output of "sudo fdisk -l".

---

### Post by obscur156 on 2008-07-06
Ok i finally found the problem.

It looks like the boot order in the bios have changed even if i did not touched it for months :-k.

It was trying to boot from the second HDD where there is only data on it.
I found out because when i was using the UBUNTU CD and using the option "boot from first hard disk"my grub menu was there.So i got in the bios and found out that it was trying to boot from the second HDD.

Best regards,have a nice day.

---

### Post by obscur156 on 2008-07-06
Thanks caljohnsmith,problem solved ;)

---

