---
title: "'grub rescue'"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by FAXJdxK on 2013-10-23
Hi everyone, first of all I'm italian, so I apologize for my bad english.

Second, i have a big problem. I have a new Sony Vaio Pro 13 (so, it's an ultrabook WITHOUT the CD drive), which had Windows 8 pre installed. I needed to install Ubuntu in dual boot for university purposes. So, i shrinked the win partition and created a new partition, and from a bootable usb stick i created a swap partition and an ext4 partition, and installed ubuntu. Due to several failures, i used the Boot-repair tool, which installed the grub 2 bootloader, from which i could start ubuntu and windows. Anyway ubuntu didn't start, it showed me an error, but this is not the problem. The problem is that, due to this error, i decided to try again (because maybe i did something wrong), so i logged into windows and deleted the two linux partitions, creating an unallocated space, and rebooted with the usb stick on.
But i got stuck in the "grub rescue".

I looked in the internet, but i found nothing, becase_
- the booting order is FIRST the ssd drive and second the usb stick (when i installed ubuntu before, i loaded the usb stick from a Sony Uefi-like menu, which had 4 options, and one of them was "boot fom usb");
- i don't have a cd/dvd drive, because the laptop is an ultrabook;
- i don't have linux installed on the drive anymore (because as i said above, i deleted the partitions).

What can i do? In some days i have an university exam and i need to get to my documents as soon as i can..

---

### Post by fantab on 2013-10-23
First of all, Boot with Ubuntu USB and opt to "Try Ubuntu without Installing", once you have the desktop ready open Terminal [Ctrl+Alt+T]. In the terminal run the following commands and post its output here:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by FAXJdxK on 2013-10-23
Thanks for your answer. The problem is that i can't even boot in usb, because as i wrote above the boot order is:
1 - Internal Drive
2 - External Drive
So, it will anyway boot first the Internal SSD and get stuck into the grub rescue :(

---

### Post by fantab on 2013-10-23
Whend booting with USB at the BIOS/UEFI screen you have to select F12 or F10 or some other key to select the boot device... then choose the USB, on some machines its USB-HDD.

---

### Post by FAXJdxK on 2013-10-23
Thanks again. But, on the start screen, i only see the "Sony" logo, for 1-2 seconds, no other words/keys! And it does't matter which key i press (i don't know which is the ley to press to enter the bios, and i even don't know if there's one, due to the EFI/UEFI bios) i get the grub rescue screen.

---

### Post by fantab on 2013-10-23
I don't know what key Sony uses. Search the forum or WWW or contact Sony... ask them how you can enter bios boot menu or how you can set your USB as first boot device.

---

### Post by FAXJdxK on 2013-10-23
I solved the problem!

For those who has a Sony Vaio Pro 13: there's an "Assist" button on the top of the keyboard. Press it while the laptop is off, and it will turn on loading a completely dedicated loader and partition. From there, you can access bios settings, load from usb, and do other stuffs that will help you getting out of your problem. Well done sony, well done.

---

### Post by oldfred on 2013-10-23
Another thread OP posted this as the instructions he used with his Sony.
Sony Vaio UEFI info
 [http://www.slideshare.net/Tinydile/vaio-pro13-win8ubuntu1310uefi](http://www.slideshare.net/Tinydile/vaio-pro13-win8ubuntu1310uefi)

---

### Post by FAXJdxK on 2013-10-24
Thank you oldfred! This was exactly what I needed and couldn't find! I'll take a look ;)

p.s. I already marked the post as [SOLVED]

---

