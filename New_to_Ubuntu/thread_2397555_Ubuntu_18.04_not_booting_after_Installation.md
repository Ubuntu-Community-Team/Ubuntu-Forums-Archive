---
title: "Ubuntu 18.04 not booting after Installation"
date: 2018-07-31
forum: New to Ubuntu
---

### Post by garcon129 on 2018-07-31
Hello,
I have installed Ubuntu 18.04 on my acer aspire-es1-331, but it does not boot.  

The Output of sudo efibootmgr -v looks like this:
```
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 2001,0001,2002,2003
Boot0000* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Linpus lite    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\BOOT\BOOTX64.EFI)RC
Boot0002* Unknown Device:     HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0003* USB HDD: TOSHIBA TransMemory    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,MBR,0x642f7,0x800,0x1cdec00)RC
Boot0004* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0007* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0008* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0009* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000A* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000B* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000C* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000D* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000E* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000F* ubuntu    HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC



```

Here is the output of boot-repair: [http://paste.ubuntu.com/p/yypMGq6RvP/](http://paste.ubuntu.com/p/yypMGq6RvP/)

I don´t know what to do and am really thankfull vor any kind of help.

Jan

---

### Post by oldfred on 2018-07-31
If an Acer then the solution is relatively easy. Acer has a unique requirement of setting UEFI password and enabling trust.
You also need to update UEFI from Acer. And many with new SSD need firmware update also.
Best to delete duplicates in UEFI boot menu before hand.

Several threads where users explain details, some explain better than others.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074) 

You may also have too many duplicate entries in UEFI. 
First set of listing shows many ubuntu entries. But last one only shows ubuntu & unknown with otherwise are the same?
sudo efibootmgr -v

If still duplicates see 
man efibootmgr
sudo efibootmgr -b XXXX -B
  where XXXX is entry you want to delete.
You can also delete the Linpus entry:
Boot0001* Linpus lite	HD(1,GPT,ec4db40e-0203-46ff-bc2b-41291d267ea5,0x800,0x100000)/File(EFIBOOTBOOTX64.EFI)RC

[URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by oldrocker99 on 2018-07-31
My experience has always been that if you don't boot the live disk in Legacy mode, but in UEFI mode, the installation will fail, since grub will not install, making the system unbootable. That's what I learned from some frustrating installation attempts.

---

### Post by oldfred on 2018-07-31
I have never had it not install, but it always installs to the wrong drive, sda where I have my main working install as default.

I do always partition in advance with both and ESP - efi system partition and a bios_grub partition as first two partitions on every drive. UEFI suggests ESP be first, but Windows often makes it second or third, but still near beginning of drive.

---

