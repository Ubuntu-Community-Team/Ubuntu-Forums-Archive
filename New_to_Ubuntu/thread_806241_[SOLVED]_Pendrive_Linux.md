---
title: "[SOLVED] Pendrive Linux"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by KingTermite on 2008-05-24
I followed the instructions on [-this page-]("http://www.pendrivelinux.com/2008/02/18/pendrivelinux-2008-install-from-linux/") to try to install Pendrive Linux onto a new pen drive (preformatted with FAT32).

My computer won't boot into pen drive, even though I've set BIOS order to DVD->USB->Hdd.

It seems I did everything right. I see files on the pen drive. However, when I reboot it goes immediately to GRUB and wants to load Ubuntu/Windows.

Before I set BIOS to move USB ahead of Hdd, I did boot to a LiveCD earlier and had no issues. So I'm sure the boot order is working correctly.

Does it matter which usb port I use perhaps? It's a laptop and has two USB ports on side and two in back.

Any suggestions?

---

### Post by saj0577 on 2008-05-24
Easy way to solve the does it matter which port. Is try them all.

Have you tried testing it in a VM or anything to test that you made it bootable and it was completely set up properly.

You have another computer you can try it on so can test if its the computer or the pendrive?

Saj

---

### Post by Sarah L on 2008-05-24
Hi,

I'm glad to see that you're interested in booting from a USB key. I've been dabbling with them as well. As a matter of a fact, I just created a bootable pen drive earlier today! I used the Kubuntu Gusty tutorial from the same site and the drive worked (almost) perfectly.

The important part in getting your drive to boot is the syslinux step. From your tutorial, that's step 4: ```
syslinux -sf /dev/sdx1
```

This should make your pen drive recognizable as a bootable device. Try running this step again and test if your drive works. If it still doesn't, make sure that all of your USB ports are functional by plugging a mouse or even your pen drive itself into it and seeing if it works/lights up. If both are true, then you might have a faulty BIOS. Check to see if your motherboard manufacturer has created any updates for your BIOS.

Good luck and have fun!
-Sarah

---

### Post by meierfra. on 2008-05-24
It seems to me that you have to fix the MBR of your external drive. Try this

[http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/]("http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/")

---

### Post by yogo on 2008-05-24
Set your bios to only boot from USB.

---

### Post by KingTermite on 2008-05-25
> **Sarah L said:**
> This should make your pen drive recognizable as a bootable device. Try running this step again and test if your drive works. If it still doesn't, make sure that all of your USB ports are functional by plugging a mouse or even your pen drive itself into it and seeing if it works/lights up. If both are true, then you might have a faulty BIOS. Check to see if your motherboard manufacturer has created any updates for your BIOS.

Good luck and have fun!
-Sarah

I did do this multiple times to try to ensure it was being set as bootable. The command never produced any output to let me know if it worked correctly or not, though I did see the file it copied to it, so think it worked ok.

However, I did notice in the man page that it says the syslinux command will not work on a FAT32 file system (which this pen drive has). I tried to convert it to FAT16 which it says you should use, but 8Gb is too much to address with FAT16.

Should I partition it in to two partitions and format one in FAT16 to try syslinux you think?

---

### Post by KingTermite on 2008-05-25
> **saj0577 said:**
> Easy way to solve the does it matter which port. Is try them all.

Have you tried testing it in a VM or anything to test that you made it bootable and it was completely set up properly.


I'm sure the ports are fine. Half of them are used regularly (right now), the other two are used frequently. Unfortunately, I don't have a VM set up as yet, but I plan to soon. If I don't have it worked out by then, I'll try that.


> **yogo said:**
> Set your bios to only boot from USB.
Good idea. Tried it - no bootable devices found.


> **meierfra. said:**
> It seems to me that you have to fix the MBR of your external drive. Try this

[http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/]("http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/")

I had high hopes for this....but didn't seem to help anything either. :(

---

### Post by bumanie on 2008-05-25
I had the same issue, the pendrive boots some computers without a problem, but others it won't boot. Thus I know the pendrive is bootable and **does boot**. It does not seem to matter how the bios is set, ie the computer it boots on is set to boot from cd-rom, but if the pendrive is inserted prior to boot, it boots that. I know that shouldn't be the case in theory, but that's how this particular computer works. I have not worked out a solution of how to boot on all computers, but it works on the computer I really need it for, so I haven't bothered delving into solutions too much.

---

### Post by KingTermite on 2008-05-25
OK....I got it.

Although all USB ports work fine, it apparently DOES MATTER which one its plugged in to. I moved it from the back ports to the side ports and it worked. I'm replying this now from Pendrivelinux. :)

Thanks for all the help and suggestions everybody.

---

### Post by Crimson_Wake on 2008-09-29
I have a different issue.  I can't boot into PDL because it says I have an incorrect key.  I also have a USB keyboard and mouse combo (wireless) and an external HDD.

I can QEMU into PDL while IN windows, but I want to boot directly to PDL and see what I can do.

Any suggestions on how to boot into it?

Thanks!

---

