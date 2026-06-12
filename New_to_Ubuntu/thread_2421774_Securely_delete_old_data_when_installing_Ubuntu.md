---
title: "Securely delete old data when installing Ubuntu"
date: 2019-06-26
forum: New to Ubuntu
---

### Post by jhdxmqz on 2019-06-26
I have a dual-boot laptop with Windows 10 and Linux Mint 19.1. The disk is SSD. I am going to replace this with Ubuntu 18.04 with full disk encryption. It is very important that any data from Windows and Linux Mint are securely deleted and not retrievable by any means. Is this possible?

---

### Post by QIII on 2019-06-26
You are talking about Secure Erase.  The best way I have found to do exactly what you ask can be found [here]("https://wiki.archlinux.org/index.php/Solid_state_drive/Memory_cell_clearing") on the Arch forum.  I've use that guide a number of times.

You will likely have to have the side of your case removed so that you can hot plug the device.  Read the steps carefully a couple of times.  Then print the instructions off and have them handy.  Proceed cautiously and deliberately.

If you have even the slightest doubt, please ask for clarification here before you start.

---

### Post by jhdxmqz on 2019-06-27
Thank you. I read the guide and entered "# hdparm -I /dev/sdX | grep frozen" into the terminal in Linux Mint but nothing happens.

---

### Post by jhdxmqz on 2019-06-28
Ignore last post, I realized that sdX should be replaced with the actual partition designation. It seems like I have one Linux Mint partition and numerous Windows partitions (labeled as "Windows recovery environment", "Microsoft reserved" and "Microsoft basic data") I guess I should erase all of these? Also, there is one partition called "EFI System". What is this and should I keep it or erase it? I am planning to install Ubuntu after the erasure and I don't want to destroy something that is essential to install Ubuntu.

---

### Post by yancek on 2019-06-28
If you plan to install Ubuntu as the sole OS with full disk encryption, it should overwrite the other partitions (Mint/windows) and should leave the EFI partition which you should use.  Mint/windows files will remain on the EFI partition which can easily be deleted as they will be useless after installing only Ubuntu.  Some detailed information on UEFI at the Ubuntu documentation site below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

