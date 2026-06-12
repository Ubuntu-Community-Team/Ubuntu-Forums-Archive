---
title: "Ubuntu won't delete from boot option"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by DRatJr on 2013-04-26
I deleted the partition I had from windows for ubuntu, and went into my USB recovery media for windows and did the following commands:

bootrec /fixmbr
bootrec /fixboot

then I rebooted. Ubuntu is still in my boot options. How can I fix this? I want to completely remove all traces of it. I installed alongside, and I am on windows 8 so I didnt use Wubi. I also have 2 options for ubuntu in boot options, both identicle names, but neither is deleted from runnung those commands that "work". Help?

---

### Post by oldfred on 2013-04-26
Those are BIOS repair commands, not UEFI commands. Hopefully those commands did not corrupt the Windows install.
You have Windows 8 pre-installed with secure boot. You need a Windows 8 repairCD or may just need to go into UEFI menu and remove Ubuntu entries. UEFI has its own memory and saves the entries.

Not sure if when running Boot-Repair, did you run the rename files function? If so you need to rename back first or restore the Windows efi file.
 If you did this, then run the second part.
 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

      
 Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.

I gather you never got Ubuntu to dual boot correctly?

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by bcbc on 2013-04-26
Edit: didn't notice, no wubi

---

### Post by DRatJr on 2013-04-26
Fred I don't understand your instructions. You say do second part but I have no clue what that means. Can you re format your response please? I'm really noob

---

### Post by DRatJr on 2013-04-26
Boot info summary: [http://paste.ubuntu.com/5605794/](http://paste.ubuntu.com/5605794/)

About to choose ubuntu. One sec

---

### Post by DRatJr on 2013-04-26
When I choose both options for Ubuntu in the boot menu I get this:

error: unknown filesystem
grub rescue>

That's what I get for both. What do I do now?

---

### Post by oldfred on 2013-04-26
It looks like you have deleted the Linux partition, so grub which is in efi to start booting, but reads grub menu from Linux partition has no Linux partition to read.

You have to in UEFI change to boot Windows as default not ubuntu. And in UEFI menu edit out the ubuntu entries, so you will not see those.

---

### Post by DRatJr on 2013-04-26
How do I edit them out? I can boot from windows, I just don't want any trace of ubuntu left. I don't want grub on my computer at all.

---

### Post by DRatJr on 2013-04-26
I have the issue solved of booting in windows. Windows works fine. I just want to get the two options for ubuntu off of there, and remove grub and everything that is on there from the ubuuntu installation.

---

### Post by oldfred on 2013-04-26
You have to boot into UEFI not Windows and edit out the entries there.

You can also delete in the efi partition the Ubuntu folder, but do not touch the Windows folder.

---

### Post by DRatJr on 2013-04-26
How to I edit them out?

And where is it located? And if I do delete the file, will it remove grub completely?

---

### Post by oldfred on 2013-04-26
You have to go into UEFI to remove menu items.
Microsoft posted this on how to get into UEFI/BIOS.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)



This is where it is from Boot-Repair, not sure if you can even see it from Windows?
[COLOR=#ff0000]
[/COLOR][COLOR=#ff0000] sdb2[/COLOR]: ___________________________________

       File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI[COLOR=#ff0000]/ubuntu/grubx64.efi [/COLOR]
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

---

### Post by DRatJr on 2013-04-26
Ok so I can load up my ubuntu USB and do it from there. Would that be better?

---

### Post by oldfred on 2013-04-26
That should work for the ubuntu folder in the efi partition.

But you still have to houseclean the UEFI. It has its own memory on the motherboard and saves things to speed up booting. You should have a maintenance entry somewhere. I posted above on users explanation of how he got into his UEFI and edited entries.

---

### Post by DRatJr on 2013-04-27
Could you  please give some steps on how to do this stuff / whee to find it? I am lost.

---

### Post by oldfred on 2013-04-27
Do you have screens like these posted by another user? I do not have UEFI, but every vendor's UEFI is somewhat different, but functions as basically the same.
First shows delete boot option. Others may just say maintenance or something similar.

---

### Post by DRatJr on 2013-04-27
No, I only have the option to disable a boot slot, like I can make it to where I can only select two boot items, but if I enable them, ubuntu is still in 3 and 4.

---

### Post by oldfred on 2013-04-27
It may be on a different UEFI page, but it should be there. If not you may have to talk to your system vendor and see what maintenance utilities they suggest.
Intel has a set of UEFI tools that you can download, but no idea how to run them and I do not think they are for new users.
 Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by DRatJr on 2013-04-27
Nah I checked everywhere in UEFI, no delete boot option option. Those don't look very user friendly. Do you think if I called samsung they would guide me through it?

Also, if I delete these from the boot menu will grub be gone? If now how do I do it? I'd need some steps so thanks!

---

### Post by DRatJr on 2013-04-27
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

Will this work? If so, I still want grub gone completely.

---

### Post by oldfred on 2013-04-28
I think that is a bit better explanation of the UEFI shell I posted above. It cannot hurt trying it.

---

### Post by DRatJr on 2013-04-28
Also, that will only remove the option. How do I delete grub completely. Where do I go in windows and what files do I delete?

---

### Post by DRatJr on 2013-04-28
One of the entries deleted, one won't. Ive done the command on it multiple times. Shows it deleted when I boot ubuntu from usb, but dont stick wen I reboot into UEFI. Is this because grub files still exist? Where do I go and what do I delete to get rid of them?

---

### Post by oldfred on 2013-04-28
If looking at files from live installer they may not be mounted at the same location as an install.

 All linux distro installers (Ubuntu included) assume EFISYS partition to be mounted at /boot/efi.

      
 /boot/efi/EFI/ubuntu/grubx64.efi

But since you have a "temporary" mount. It just may be in /media? You should be able to use Nautilus, the file browser and find it by clicking on the efi partition in the efi panel. It may not be seen as efi, but just as 200MB or whatever size your efi partition is.

---

