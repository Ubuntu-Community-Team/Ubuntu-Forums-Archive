---
title: "Ubuntu booting directly, could not see boot options to select Ubuntu or Win8.1"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by veeraeka175 on 2014-01-11
[COLOR=#070F14][FONT=Verdana]Hi i bought Acer Aspire V5 Laptop with Windows 8 Pre installed. Upgraded to Windows 8.1. I have two partitions C and E. I have used disk management to shrink E to form an unallocated space and Restarted the Laptop twice.Then i went to UEFI and disabled secure boot. After that i have inserted Bootable Ubuntu 12.04 LTS DVD and installed Ubuntu in the space un allocated. But when i start the Laptop, boot menu is not shown and directly ubuntu is loaded. I tried with Boot Repair in ubuntu, but it showed Repair failed with URL [/FONT][/COLOR][http://paste.ubuntu.com/6732706/](http://paste.ubuntu.com/6732706/).  Please help me.Thanks

---

### Post by squakie on 2014-01-12
Have you tried the following after booting linux:

sudo update-grub

Does update-grub return errors?  If so, select all the output including the sudo update-grub line, copy it to the clipboard, then reply back and paste the output between code tags.

---

### Post by fantab on 2014-01-12
I suspect that your Windows is hibernating. Have you [disabled 'FastStartup"]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")?
Because Windows is NOT detected by the OS prober.... after disabling 'Fast Startup' try Boot-Repair again.

---

### Post by oldfred on 2014-01-12
How did you get grub legacy installed to MBR?
I did not think Boot-Repair even worked with grub legacy, but it seemed to just reinstall it. And I did not think grub legacy worked with UEFI and gpt partitioning, part of reason for changes to grub2.

New systems seem to work better with 13.10 as it has a lot of UEFI updates. Also you should have updated vendor UEFI so it is most current version. UEFI has lots of changes/fixes. The new 12.04.4 this month will also have the latest fixes.

Best to make sure Windows is not hibernated or fast boot is off. Usually better to have secure boot off. And use Boot-Repair in UEFI mode to uninstall all versions of grub and install the correct grub-efi.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by veeraeka175 on 2014-01-13
I am very much Thankful for your Responses. Finally i could boot into ubuntu and windows 8, may be Technically i do not understand what i did. The problem is Boot menu options have increased. You can know this from this URL [http://paste.ubuntu.com/6745775/](http://paste.ubuntu.com/6745775/).  When i select "Windows 8 UEFI Bootloader", i am able to boot into Win 8. Also every time i start the Laptop
[COLOR=#000000]I get an error message below.[/COLOR]

[COLOR=#000000]"string descriptor 0 read error: -22". [/COLOR]
 
Please suggest me for any improvements in the Booting Process. I hope i am using Grub EFI instead of Grub 2.

---

### Post by oldfred on 2014-01-14
From UEFI menu can you boot the ubuntu entry or does it only work with or offer the Windows entry? 
It looks like you have run the rename for 'buggy' UEFI where UEFI has been modified to only boot Windows. With rename booting Windows from UEFI menu also boots grub and you only can boot Windows (renamed) efi file from grub menu.
If you can boot ubuntu entry best to undo rename. And always undo rename before updating Windows as Windows will overwrite the renamed shim file with a new version of bootmgfw.efi. And Boot-Repair may have backed up the older copy and restore after update may create version issues.

Is error message after grub boot of Ubuntu? Is that message in log file? 
You may have log file viewer or look in  /var/log and look at dmesg. It is long, so just post the few commands with the error.

---

