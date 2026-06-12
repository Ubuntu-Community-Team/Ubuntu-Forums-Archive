---
title: "Windows xp missing from ubuntu"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by jackswyl on 2012-03-28
Hi everyone I am new to Ubuntu and Im havinh some issues. After I installed Ubuntu 11.10 in dual-boot with windows xp the grub was working perfectly , letting me choose from ubuntu, memtests and windows xp. After an update, the windows menu entry is missing from grub. Another strange fact is, before GRUB2 loads, after startup, it gives me a choise between Windows XP and Ubuntu. If I choose Windows XP the computer resets, and if I choose Ubuntu it loads GRUB without windows xp on the menu entry. when I run the comand 'sudp update-grub' I get the following output:

Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
done

I dont even have windows 7 installed. Can someone help me? Thanks in advance.

---

### Post by forrestcupp on 2012-03-28
So did you install Ubuntu with Wubi? Also, when you choose Windows XP and it resets, does it boot to Windows XP, or does it just go back to that menu?

---

### Post by QIII on 2012-03-28
Give this a read.

I don't use Wubi, but I bet what you are looking for is either here or referenced:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2012-03-28
> **jackswyl said:**
> Hi everyone I am new to Ubuntu and Im havinh some issues. After I installed Ubuntu 11.10 in dual-boot with windows xp the grub was working perfectly , letting me choose from ubuntu, memtests and windows xp. After an update, the windows menu entry is missing from grub. Another strange fact is, before GRUB2 loads, after startup, it gives me a choise between Windows XP and Ubuntu. If I choose Windows XP the computer resets, and if I choose Ubuntu it loads GRUB without windows xp on the menu entry. when I run the comand 'sudp update-grub' I get the following output:

Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
done

I dont even have windows 7 installed. Can someone help me? Thanks in advance.
Do you have a Windows repair disk? (Or the installation DVD)

Can you post the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?

---

