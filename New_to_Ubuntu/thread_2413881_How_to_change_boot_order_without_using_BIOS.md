---
title: "How to change boot order without using BIOS ?"
date: 2019-03-03
forum: New to Ubuntu
---

### Post by julesian974 on 2019-03-03
I have Ubuntu 16.04 on my acer computer and I'd like to change the boot order but I forgot the password....I want to boot my USB Drive first (with windows).
I found some topics about that but when I type 'efibootmgr' in a terminal, I get this :   efibootmgr: EFI variables are not supported on this system.
Can you help me please ?

---

### Post by Dennis N on 2019-03-03
It would help to see the system's partitions to verify the type of installation. Run the command: 
```
 sudo parted -l
```
and post the resulting output.

---

### Post by oldrocker99 on 2019-03-03
If you have forgotten your password, you can follow these directions to enter a new one:[https://itsfoss.com/how-to-hack-ubuntu-password/](https://itsfoss.com/how-to-hack-ubuntu-password/), or you can reinstall, which is a lot faster than using those directions, and which I strongly recommend. **BACKUP YOUR FILES FIRST!**

And pick a password that is second nature to remember. If you are the only person who is using your PC, there's no real need to have a complicated one. I use a 4-digit password on my own laptop. It's still highly unlikely that anyone could guess it.

---

### Post by yancek on 2019-03-03
> when I type 'efibootmgr' in a terminal, I get this :   efibootmgr: EFI variables are not supported on this system

If you post the requested output of parted it will tell whether you have EFI, which apparently you do not.  If you want to boot a windows install usb, you should be able to chainload it from the install Ubuntu Grub2 menu if you know the device and uuid.

---

### Post by richard378 on 2019-03-03
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

You can change the defualt boot order or default boot OS by editing the GRUB config files.  I have done it in the past.  Please look at the above link and go through it for details.

---

### Post by grahammechanical on 2019-03-03
What password? The password into Ubuntu? Or, the password into the BIOS? If like me you have a BIOS motherboard and not a UEFI motherboard then the instructions in my motherboard user guide might be useful.

"If you forgot your BIOS password, you can clear it by erasing the CMOS Real Time Clock (RTC)."

On my motherboard the RTC can be erased by changing a motherboard jumper. Or by removing the CMOS battery. You will need to enter the BIOS utility to set a time & date as well as setting the boot order as this action in effect resets the motherboard to it default settings.

If you have an UEFI, then I can offer no help. Perhaps you can download a PDF copy of your machine's motherboard guide.

Regards.

---

