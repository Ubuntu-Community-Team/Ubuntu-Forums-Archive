---
title: "Failed Install, Trying to recover. From Win XP to Ubuntu 14"
date: 2015-09-27
forum: New to Ubuntu
---

### Post by SRG_tech on 2015-09-27
Hi,

I have an old laptop running XP and i wanted to replace it with Ubuntu. I used boot from USB to install Ubuntu with help from plop [https://www.plop.at/en/bootmanager](https://www.plop.at/en/bootmanager) to recognise the USB drive during boot. 

I managed to set-up the install process and started the install. After I got a blank screen with "ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command." being printed every few minutes. I figured that the install had gone wrong so i closed down my laptop thinking i could go through the process again, boot from usb, start the install again. 

Here's my problem i think...I used plop to recognise the USB drive but it has been wiped off my harddrive ( i chose not to keep XP ). Without plop i cant boot from USB and so cant go through the install process again! If i start the laptop with the usb stick that has ubuntu plugged in i just get bios setup and then a blank screen.

Any ideas how to recognise my USB drive now that i have a laptop with only BIOS!

---

### Post by tristan16 on 2015-09-27
You need to configure your computer to boot from the USB drive instead of trying to use the main hard drive. When you first turn your computer on, you should see BIOS before anything else. It's different for every computer, but you can try pressing F4 or F8 to enter BIOS.

When you get into BIOS, you need to find the boot settings. You need to tell the computer to check for a bootable USB drive *before *checking the hard drive. Again, this is different for every computer.

Once you have this set up, you should be able to reboot from the USB drive. It's probably a good idea to change the boot order back to the original settings after you successfully install Ubuntu.

If you could specify your computer brand and model, I might be able to provide more detailed instructions.

---

### Post by mörgæs on 2015-09-28
Another option is to install from CD/DVD.
Always use wired internet access while installing. Wirefree comes later.

---

### Post by mastablasta on 2015-09-28
what other media can you use? plop can be used on floppy or CD. I guess there is no CD or it is not working so the only option then would be floppy drive if you have it.

---

### Post by kurt18947 on 2015-09-28
It seems that Tristan16 has it right. There should be no need for any additional boot helper. Some laptops have a key that goes directly to "press this key to change the boot drive one time" and offers a list of available boot devices. The machines I have use either F9,  F11 or F12, it varies by manufacturer. I too have found CD/DVD most reliable but slower than USB booting.  I don't know if this is still the case but at one time, it worked better to select 'try now' instead of install. Once the live session is running, establish a network connection - ethernet is usually easier than wifi - then install. You're not dual booting so it should be simple.

There is one thing to be aware of with Ubuntu-only install. If you want to add Windows later, you can do so after creating a Windows partition manually but after installing Windows, Ubuntu will have 'disappeared'. Windows bootloader doesn't play well with others. A boot-repair disc has set things right for me in the past.

---

### Post by Geoffrey_Arndt on 2015-09-28
Also, if the laptop is indeed old . . . ubuntu proper may be too much for it (exceeding hw requirements).

The odds that another Ubuntu flavor such as _Ubuntu-Gnome_ or _Linux Mint Mate_ will install much smoother and without side door issues are considerably better.

PS:   on the odd chance your old laptop is an all Intel machine (i.e., intel graphics and intel wireless), then it should still install ubuntu  - - but just run a bit slower than the other flavors mentioned above.

---

### Post by mastablasta on 2015-09-29
> **kurt18947 said:**
> It seems that Tristan16 has it right. There should be no need for any additional boot helper. .

has he? I have an old Compaq with win XP on it. while it has USB ports it can not boot from them. It can boot from CD, but the drive reading doesn't work well (often produces errors) and even if I manage to boot from it, it will be very, very slow. not to mention that install might fail since the drive is not reading well. the floppy drive works well though and can be used with a boot loaded on floppy to boot the PC from USB.

---

### Post by tristan16 on 2015-09-29
> **mastablasta said:**
> has he? I have an old Compaq with win XP on it. while it has USB ports it can not boot from them. It can boot from CD, but the drive reading doesn't work well (often produces errors) and even if I manage to boot from it, it will be very, very slow. not to mention that install might fail since the drive is not reading well. the floppy drive works well though and can be used with a boot loaded on floppy to boot the PC from USB.

Yes, I forgot to mention that older computers cannot boot from USB. I've never experienced this personally, so I wouldn't know how to get around this. Ubuntu us too big for a standard CD, so you would need to burn a DVD or, like you said, use a boot helper.

---

### Post by kurt18947 on 2015-09-29
> **tristan16 said:**
> Yes, I forgot to mention that older computers cannot boot from USB. I've never experienced this personally, so I wouldn't know how to get around this. Ubuntu us too big for a standard CD, so you would need to burn a DVD or, like you said, use a boot helper.

Or use a distro that will fit on a CD.  I don't know when PCs became capable of booting reliably from a USB device, perhaps mid 2000s? I've always had good success with booting from an optical disc, even though it's slow and cannot have persistence. I've had better luck with MX14 non-PAE kernel on older equipment than *buntu variants. MX14's default UI is a little Unique, but it's recognizably XFCE based.

---

