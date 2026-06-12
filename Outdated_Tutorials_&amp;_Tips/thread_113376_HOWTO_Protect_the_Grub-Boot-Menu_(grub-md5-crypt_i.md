---
title: "HOWTO: Protect the Grub-Boot-Menu (grub-md5-crypt is broken)"
date: 2006-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Stroganoff on 2006-01-06
Hello,

maybe you want the user to enter a password in order to boot the Recovery Mode or your secondary OS. You have to set that password in the /boot/grub/menu.lst - for higher security you should crypt your password with md5.

The usual way does not work in Breezy: In a terminal run grub-md5-crypt, enter your desired password twice and copy the generated crypt-hash into the menu.lst, for example:```
title		Kubuntu (Kernel 2.6.12-9-386) - Recovery Mode
password --md5 $1$HSX1$JYNyfBY0pVizk5kyMQOqn/
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot
```Now reboot and try to start the protected boot-option, enter your password and you'll see: "Authentication failure".

grub-md5-crypt seems to have a bug in Breezy. You need to take a different approach to generate the crypt-hash of your desired password.
Reboot your machine and enter the grub-menu. Now press the "C"-key on your keyboard to enter the command line of grub. Type:```
md5crypt
```Enter your desired password and take some pen/paper to write the generated hash down. Now boot up Ubuntu, edit /boot/grub/menu.lst and paste the new hash into the correct line.

That's it. I would like to thank [Joe Smith](http://lists.debian.org/debian-user/2005/09/msg00177.html).

---

### Post by kais0r on 2006-04-29
Thanks Strog, now I can deactivate my bios-based system passwd. :)

---

