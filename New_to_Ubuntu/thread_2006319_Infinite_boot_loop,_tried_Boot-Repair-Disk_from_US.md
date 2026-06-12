---
title: "Infinite boot loop, tried Boot-Repair-Disk from USB"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by tsizzle on 2012-06-19
Hey there,
     So to start from the beginning, even though I'm not sure that all things listed here are directly related, yesterday my laptop started to randomly shut down. I've been running it without the battery and everything seems fine in regards to power. Today I was going to boot in Windows 7 to watch some netflix and I accidentally accessed the recovery mode from Samsung listed under GRUB. There was an "x" to close the window which I clicked and selected the option "restart system." Then I ended up in a boot loop where I don't even see the "grub loading" text unless I hold shift during the boot process. eithe way the screen goes black and then looks like it's going to load over and over again. I downloaded the boot repair disk iso and used the Lili usb creator and ran it. After the updates and diagnostics and a failed attempt at doing the "recomended repairs" this message showed up:
"The boot of your PC is in EFI mode, but no EFI partition was detected.you may want to retry after creating a EFI partition (FAT32,>200Mo, start of the disk,boot flag)
The boot of your PC is in EFI mode you may want to retry after changing it to Bios-legacy mode"

The most recent report the Boot repair disk generated can be found here:
paste.ubuntu.com/1048521 

I'm running a Samsung NP300V5A
Thanks in advance for any help you can give me

---

### Post by tsizzle on 2012-06-19
I didn't realize I could edit posts. Is there a way I can delete this one now that I've included more info in my original?

---

### Post by YannBuntu on 2012-06-19
Hello
> **tsizzle said:**
> The most recent report the Boot repair disk generated can be found here:
paste.ubuntu.com/1048521

Sorry, there is a bug in Boot-Repair's PPA today, i'm working on it.

Please reboot on your Boot-Repair-Disk, DON'T update the software from PPA, click "Recommended repair".
If any problem, indicate the new URL that will appear.

---

### Post by tsizzle on 2012-06-19
Thanks, I accidentally discovered that this morning. I'm really glad that it wasn't something that was going to require a lot of work I'm not knowledgeable to perform. Thanks a million though.
-T

---

