---
title: "Unregister Windows Product Key from Ubuntu"
date: 2017-06-16
forum: New to Ubuntu
---

### Post by waldxn on 2017-06-16
Hello, I plan on resetting my pc to factory settings, and would like to know If I can unregister my windows 10 product key from my ubuntu OS. I ask this because I dual-Booted my computer with Ubuntu and can no longer access Windows. I wish to reset to factory settings and reinstall windows 10 using the same product key. Please help!

---

### Post by QIII on 2017-06-16
First:  what happens when you try to boot Windows?

---

### Post by waldxn on 2017-06-16
When selecting windows boot managaer from my UEFI menu it just does nothing. When selecting the sata option it boots straight to ubuntu

---

### Post by QIII on 2017-06-16
The answer to your initial question is "No."  You can't do that.

However, I think you can still download .isos from DigitalRiver (legitimate copies, but you have to have a key to register them.  You won't need to.  You won't be installing.).

Burn that to disk, boot from it and select "Repair system" or similar.  That should give you the option to restore the MBR.  You can use a live session of Ubuntu to delete your Linux partitions, boot back into Windows and resize your Windows partitions.  That way you would not need to blow away your Windows and all your files on it.

Any detailed questions would likely best be answered on a Windows forum.

---

### Post by oldfred on 2017-06-16
Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

