---
title: "Windows 8 13.10 boot repair error but working fine?"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by Evan_Hart on 2014-01-19
Hello I installed Ubuntu 13.10 on my Sony Vaio Flip 13a that came with pre-installed Windows 8 that I upgraded to 8.1
I used boot repair to deal with the EFI issue following "Recommended Repair"
There was an error but everything seems to be working fine (?).
I got paste.ubuntu.com/6782610
 Also it said "don't forget to create [something/I/cant/remember/]shimx64.[somefileextention] file!"
Should I try boot repair again? Or should I just leave it because everything is working?
Thanks

---

### Post by oldfred on 2014-01-20
Messages can be important.
But I think Boot-Repair was suggesting that you go into UEFI menu and choose the ubuntu entry which is the shim file with secure boot on.

Line 1379 in link.
> Please do not forget to make your BIOS boot on sda3/EFI/ubuntu/shimx64.efi file!


You have run the 'buggy' UEFI rename. That is only required is you cannot boot an ubuntu entry in UEFI as vendors may modify UEFI to only boot Windows. With the rename both Windows and ubuntu entry in UEFI boot to grub and you only can boot Windows from grub menu's /EFI/Microsoft/Boot/bkpbootmgfw.efi.

If you can boot ubuntu entry in UEFI menu:
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Also if you do not undo it, or have buggy UEFI and cannot undo it, be careful on Windows updates as those may overwrite bootmgrw.efi and then you only boot Windows. And the backups saved by Boot-Repair may become older versions, or you get out of sync.

---

