---
title: "Grub is broken after upgrading to Ubuntu 14.04 (Dual boot)"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by tester7 on 2014-04-19
Hi.

After upgrade from ubuntu 13 to 14.04 I'm facing "grub rescue>" screen.
After googe'ling and hitting my head against the wall for a while, I'm able to boot my system finally with some magic like this:

```

insmod linux
insmod efifwsetup
insmod linuxefi
linux (hd2,gpt2)/vmlinuz root=/dev/sdb2 ro
initrd /initrd.img

```

After loading few *efi* modules available in /boot/grub/x86_64-efi/  - I'm getting initrd error "alloc magic is broken" and then my newly upgraded ubuntu starts normally.
- When I'm just trying to "insmod normal", it says: term_highlight_color not found.
- If I'll not load *efi* modules, "linux (hd2,gpt2)/vmlinuz" command says something like "Premature end of file".
- When I'm trying to purge and reinstall grub - or do grub-install with or without --recheck, I'm getting the error:
> Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklistts are UNRELIABLE and their use is discouraged..
grub-setup: error: will not proceed with blocklists.
This is occuring both from LiveUSB and my native system all the time when I'm trying to grub-install, dpkg-reconfigure it.

I have 2 hdd's on my laptop, Windows 7 Enterprise on the first HDD, and the second is for Ubuntu (sdb2).  Here the results of bootinfoscript: [http://paste.ubuntu.com/7288164/](http://paste.ubuntu.com/7288164/)

How can I fix this issue and make GRUB boot normally both Ubuntu and Windows ?

P.S. I've tried all the known solutions from google - no one worked. Please, do not suggest just to reinstall it again, I've tried to install several times grup-pc, grub-common, grub-efi from official repositories - without any success.
P.P.S. Here the results of "lsblk" and some other commands: [http://paste.ubuntu.com/7288322/](http://paste.ubuntu.com/7288322/)

---

### Post by dopecop17 on 2014-04-19
If you have a way to download and burn it supergrub might help you reinstall the grub.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Also are you by chance running a hardware raid card, i had a similar problem with a jacked up raid controller the other day

---

### Post by tester7 on 2014-04-19
Thanks for a response.
No, I have 2 sata drives.

Thanks for a hint about Supergrub. But I'm  booting Ubuntu manually from "grub rescue". And I've tried several times to remove/purge grub completely and reinstall - with dpkg-reconfigure and grub-install. Also I've tried the same from LiveUSB. What else can I do with Supergrub ? It seems to be a tool for booting the system when grub is gone. But I'm able to boot the system, I just want to have grub installed  properly.
It is related to this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

**UPD:** Yeah, it can fix grub issues. I'll try it a bit later, and report results here.

---

### Post by oldfred on 2014-04-20
Possibly related to that bug.

Not sure why, but your efi partition on sdb seems to be corrupted. I might try chkdsk from Windows.
I prefer to have the Windows efi files in the Windows drive and the grub/Ubuntu efi files on the Ubuntu drive.

You have an UEFI system.
But you have installed grub to the protective MBR of sdb (for BIOS boot) and to the sdb2 partition or PBR (which cannot be used). 
Not sure if you originally installed in BIOS boot mode, but install now is UEFI, and you do not install grub to MBR or PBR.

You currently have grub's boot UEFI boot files in the sda1 efi partition. That is ok, but see above.

You also have run the 'buggy' UEFI fix from Boot-Repair. That is only for those systems that have modified UEFI to only boot Windows. 
From UEFI menu, can you boot ubuntu entry? 
You should have both ubuntu & Windows entries and with the rename both take you to grub menu. If you can directly boot ubuntu entry without UEFI giving errors undo the rename.
You must have secure boot off as you have not installed the secure boot version of grub & kernels.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by tester7 on 2014-04-20
Hi again.

**Dopecop,** I was unable to boot with Supergrub or Rescatux from USB.
**Oldfred,** 
Before this I was afraid to run Boot-repair (because it is not added yet to Ubuntu 14 repositiories), the state you see is not the result of Boot-repair. 
About a year ago when I've installed Ubuntu, I remember, that I've tried to install it in Legacy mode. So yes, it is possible that Ubuntu is originally installed in BIOS boot mode.
Now I've tried to install and run Boot-repair from Saucy's repositories. Several times with different options.

It changed the case - instead of getting "grub rescue" screen, now it starts Windows Boot Loader immediately.
No matter if I'm installing grub-efi-amd64 with shim or doing apt-get install "grub-efi linux" during Boot-repair's process.
From this point I can boot into both ubuntu and windows from UEFI menu (pressing F12) (I didn't checked it before).

So, since windows boot manager works, I did from windows Administrator console 
```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```
And now it works perfectly.

But my sdb1 seems to be still broken, grub files are on sda1. Any options to fix sdb1 partition without formatting ? chkdsk and fschk are useless.
Here the results of bootinfoscript: [http://paste.ubuntu.com/7292529/](http://paste.ubuntu.com/7292529/)

Please, check are both Ubuntu and Windows installations in UEFI mode, are there any other issues that will cause problems in future except corrupted sdb1 partition?
Any other suggestions to avoid broken grub on next upgrade?

After your answer I'll mark this thread as solved, thanks a lot for giving very valuable hints!

---

