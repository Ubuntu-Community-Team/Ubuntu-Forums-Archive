---
title: "Can't copy a directory to Windows drive with Ubuntu in memory, not loaded..."
date: 2021-11-01
forum: New to Ubuntu
---

### Post by Erik The Pope on 2021-11-01
I'm trying to copy a directory with important files from my M.2 boot drive to a drive that I use for Windows, which will not boot. I booted from a CD with Ubunto 21 but did not install it so it's just in memory.

I put up the two drives in Files & tried several ways to copy the directory. The permissions on the Windows drive say "Create & delete files" on both drives but it won't let me copy, the icon just goes back to the M.2 drive.

How do I make it copy to the Windows drive??? I can't find anyway to make the copy & I'm definitely an Ubuntu newbie.

Can somebody tell me what do to do to make it copy???

Thanks!

Erik The Pope

---

### Post by psychohermit on 2021-11-01
Can you copy it to a usb stick?  --glenn

---

### Post by ActionParsnip on 2021-11-02
I suggest you boot to a Windows CD and run a chkdsk on your NTFS partition. If the data is important then you'll have a backup... Right?

---

### Post by Impavidus on 2021-11-02
My guess is that the Windows "drive" (filesystem on a partition on a drive, really) was mounted read-only. Since Windows 8, Windows no longer properly closes its filesystems on shutdown, which means that Ubuntu can only mount it in read-only mode. There is a Windows setting to fix that (disable fast startup), but that makes Windows boot slower. You should be able to use Ubuntu to copy the files to a usb drive or a network location.

---

### Post by Erik The Pope on 2021-11-04
Well I tried using a USB thumb drive as psyhcohermit (and my brother) suggested & it worked for what I wanted, which was to save some important files. When I tried to copy a whole directory, I got a lot of msgs about "can't do symbolic links" due to Ubuntu's rules. I think that the reason it would copy to the USB but not the mechanical drive I started to copy to was that the USB was formatted in FAT32 but the drive was NFTS. Apparently Impavidus was correct about mounting read only. I do have backups of these files but the ones I copied from the M.2 drive were more up to date. Thanks to everyone!

---

