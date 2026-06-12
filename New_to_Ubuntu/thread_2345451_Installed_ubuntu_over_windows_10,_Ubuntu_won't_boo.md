---
title: "Installed ubuntu over windows 10, Ubuntu won't boot"
date: 2016-12-04
forum: New to Ubuntu
---

### Post by thepontifex on 2016-12-04
I recently installed Ubuntu over windows 10 on my old laptop.
When I start up the laptop ubuntu does not boot, instead I can choose to either trouble-shoot or start BIOS set-up.
I already tried to use boot-repair but that did not solve the problem. Here are the details [http://paste2.org/XtI0fKhI](http://paste2.org/XtI0fKhI)
I tried to google this problem but did not find a solution yet! I hope someone can help me.

---

### Post by oldfred on 2016-12-04
You say old laptop, but it is UEFI which to me is newer.

What brand/model system. Some in UEFI mode only boot entry that says "Windows Boot Manager". That is a violation of UEFI spec, but there are many work arounds.

Systems still boot the fallback or hard drive entry which is /EFI/Boot/Bootx64.efi. Windows systems often have bootx64.efi as a copy of the Windows .efi boot file. And if only booting Ubuntu we can make the Windows entry be the boot of Ubuntu/grub's .efi file.

Boot-Repair will copy shimx64.efi to bootx64.efi if you check in advanced options "Use the Standard efi file".

And it looks like your Windows entry has already been changed to use bootx64.efi, so if Boot-Repair copies shimx64.efi to bootx64.efi, then your Windows entry will boot Ubuntu/grub.

With only one system installed you will not normally get grub menu. You have to press escape key perhaps several times, just after UEFI/BIOS screen but before grub has started boot process.

---

### Post by thepontifex on 2016-12-04
Hi, thanks for your answer.
My laptop is about 4 years old, it's a vaio S.

I reinstalled ubuntu and ran in the same problems again. 
When I start the laptop I get the error messages
"Failed to open \EFI\BOOT\MokManager.efi Not Found
Failed to load image \efi\boot\MokManager.efi Not Found
Filed to start MokManager: not found" 

Then I end up in the menu "GNU GRUB   version 2.02~beta2-36ubuntu3"
there I have the options
"Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects"

If I press esc I can enter some commands, but I don't really know what to do from there.

---

### Post by thepontifex on 2016-12-04
Also here is the boot file again [http://paste2.org/j2819W92](http://paste2.org/j2819W92)

---

### Post by oldfred on 2016-12-04
You should not get mokmanager, that is the UEFI secure boot key manager.
Do you have Secure boot off?

Did you run Boot-Repair and check the "Use the Standard efi file", you are not showing the backup it creates when it copies the shim file to bootx64.efi.

You now show three Windows Boot Managers.

 BootOrder: 0005,0006,0008,0007
Boot0005* Windows Boot Manager	HD(1,GPT,8e9ed3a0-76fe-466b-bc14-7c719e9ae619,0x800,0x100000)/File(EFIBoot[COLOR=#ff0000]bootx64.efi[/COLOR])
Boot0006* Windows Boot Manager	HD(1,GPT,8e9ed3a0-76fe-466b-bc14-7c719e9ae619,0x800,0x100000)/File(EFIMicrosoftBootbootmgfw.efi)
Boot0007* UEFI: KingstonDataTraveler 2.0PMAP	PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x4294967248,0x800,0x3a26e80)..BO
Boot0008* Windows Boot Manager	HD(1,GPT,8e9ed3a0-76fe-466b-bc14-7c719e9ae619,0x800,0x100000)/File(EFIMicrosoftBootbootmgfw.efi) 

Sony may automatically add Windows entries by finding the /EFI/Microsoft/Boot/bootmgw.efi file.

You can houseclean extra or duplicate entries.

 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
man efibootmgr 

You may have to delete all the current Windows entries, to know which is which in UEFI boot menu.
      
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by thepontifex on 2016-12-04
I have secure boot off. Should I turn it on or off?

---

### Post by thepontifex on 2016-12-04
The box "Use the Standard eti file" was ticked I also ticked an extra this time "backup and rename windows EFI files" (solves the [hard-coded-efi] error]" but that didn't solve the problem
[http://paste2.org/X6JCOevV](http://paste2.org/X6JCOevV)

I used the "sudo efibootmgr -v" command: the response I get is
"BootOrder: 0000,0005,0006,0007"
Bootorder 0005*...
Bootorder 0006*...
Bootorder 0007*..."
I don't have the 0008 option

---

### Post by thepontifex on 2016-12-04
I followed this advice:
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
and now it seems to be working!
Thanks a lot for your help

---

### Post by oldfred on 2016-12-04
It looks like Boot-Repair redid some UEFI boot entires.

Can you boot any of the Windows Boot Manager entries?

This is what Boot-Repair should have done, older threads users had to manually copy files.

 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

---

