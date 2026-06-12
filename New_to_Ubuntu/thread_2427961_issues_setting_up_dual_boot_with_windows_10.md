---
title: "issues setting up dual boot with windows 10"
date: 2019-09-27
forum: New to Ubuntu
---

### Post by zmkur on 2019-09-27
Hello all I am sure there have been posts like this before, i will try to do my best to include all the details i can. As stated i am attempting to set up Ubuntu along side my windows but i am unable to get the usb to boot, at first i thought this was an issue with my UEFI settings but i have cleared and disabled the secure boot settings, though i am not sure if there is more i have an ASUS ROG Rampage VI extreme MB, this was originally a gaming computer but i am mostly using it for developing now and am tired of Windows. so anyway i cant seem to find the usb there or in the boot menu when i launch it, the bios is weird and there is not a typical boot order tab just boot overrides but all that is there is windows and back up that launches in som ekind of safe mode it seems. so now i am wondering if the problem is my USB, I have tried to burn the ISo file downloaded form Ubuntu using Universal-USB-Installer, Rufus, and Etcher so far none have worked. i downloaded MobalLiveCD to see if the drive was bootable and have had various degrees of success with each burn but none have been able to boot on the system, and the one from etcher failed to boot in the virtual environment from Mobal saying no bootable device, the one from Universal USB loaded a screen with the try Ubuntu install scree, the rufus version did not make it past the logo screen and just freezes there, again this is all in the virtual environment.  so I am not sure what i am doing wrong it appears the first issue is the USB, and fixing that might fix the computer not finding it during boot. thank you for any help you can give much appreciated

---

### Post by yancek on 2019-09-28
Have you downloaded their manual and taken a look there, link below?

 [https://www.asus.com/us/Motherboards/ROG-RAMPAGE-VI-EXTREME/HelpDesk_Manual/](https://www.asus.com/us/Motherboards/ROG-RAMPAGE-VI-EXTREME/HelpDesk_Manual/)

---

### Post by zmkur on 2019-09-28
Not yet, but that did help a bit thank you . i found where the boot order is. heres where it gets weird, the usb shows up there the first time I went to that page of the BIOS but has not shown up again, i attempted to boot from it in Mobal again and it said no bootable device. So i re burned the ISO to the usb, and tried it again, still not showing up. which makes me think i am doing something wrong when creating the usb but all i am doing is downloading the ISO from ubuntu and burning on the drive with a Fat32 format. should i be trying something else?

---

### Post by yancek on 2019-09-28
Did you verify your download of the UBuntu iso file before trying to use the software you mention to put it on a usb?  This process is expalined it detail at the Ubuntu site below.  Rufus, Etcher and the other software you mention generally work on a good iso.  Also FAT32 is the standard filesystem type for this prupose.

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

I'm not familiar with the hardware you are using but most BIOS's will show a usb/flash drive listed under HD/hard drive option.

---

### Post by zmkur on 2019-09-28
i will try to follow those instructions, I downloaded the desktop iso from the Ubuntu website, i then have tried various writing programs to attempt to create a bootable usb so far i have not been able to boot the usb. I know where the boot priority is located now but there is no usb option visible there. I did get the usb to show in that list one time not sure what was different that time but even then it did not boot from the usb. I tried to reboot and repeat the process with the same usb and it was no longer in the list. thats where i am at now

---

### Post by r_widell on 2019-09-28
What Yancek was asking was if you had verified that the .iso had downloaded properly by confirming the file hash. My personal preference in Windows is HashTab. After installing that application there will be an additional "hashes" tab when you right-click the .iso file and select "properties". You can paste the hash shown with/near the download link and HashTab will confirm/deny the integrity of the downloaded file. Even after that, I always like to verify that the .iso was written correctly to the boot media by selecting that option upon booting from the media prior to installation.

Good Luck,
ron

---

