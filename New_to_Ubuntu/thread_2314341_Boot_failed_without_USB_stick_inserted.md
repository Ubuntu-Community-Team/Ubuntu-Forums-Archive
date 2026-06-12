---
title: "Boot failed without USB stick inserted"
date: 2016-02-20
forum: New to Ubuntu
---

### Post by Larry_Hale on 2016-02-20
Hello all, I have an Acer Aspire E-15 with a 500 gig drive, 4 gig Ram. Installed Ubuntu from bootable USB stick. Formatted HD prior to install (Had Win 10 previously). UEFI secure boot disabled. Machine come up with message "Default Boot Device Missing or Boot Failed. Insert recovery media and hit any key". If I have the USB stick inserted I don't get the message. When I shut down the machine, it never powers off. Pastebin info follows:

[http://paste.ubuntu.com/15139223/](http://paste.ubuntu.com/15139223/)

Thanks in advance....

---

### Post by yancek on 2016-02-20
You have mixed an MBR install with a UEFI install.  You also have Grub Legacy installed in the master boot record of the drive.  Don't know how that happened as Ubuntu hasn't used Grub Legacy for 6 years.  You have an EFI partition with the Ubuntu boot files.  You need either EFI or MBR.  I don't use EFI myself so I'm not sure how to repair this.  Maybe the suggested repair in the boot repair output would work.   Someone else should be along with more knowledge.

---

### Post by oldfred on 2016-02-20
Your fstab is showing the mount of the efi partition, so I would expect that latest updates have grub in stalled in UEFI boot mode.

But Acer requires you to set a supervisory password and set "trust" on Ubuntu/grub's efi boot files.
       Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

