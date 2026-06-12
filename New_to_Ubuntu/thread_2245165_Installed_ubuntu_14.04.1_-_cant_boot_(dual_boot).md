---
title: "Installed ubuntu 14.04.1 - cant boot (dual boot)"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by marius_wiik on 2014-09-21
Hi.

This is my first attempt at a linux-install and I used this guide : 

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

In short I want to dual boot Win 8.1 and ubuntu. I booted from a live CD and installed it according to the guide.
After installation I didnt get any choices for OS during POST. 
I followed the guide and everything went as the guide predicted, minus the part where it worked. 

I tried this guide aswell: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
basically the same thing, and it said that if it didnt work I could ask here for help :) 
The boot-repair made a log that can be found here: [http://paste.ubuntu.com/8398271/](http://paste.ubuntu.com/8398271/)

I really hope someone can help me :)

Edit: I can see ubuntu when going to advanced startup options but when I select it it reboots into windows

---

### Post by oldfred on 2014-09-22
What brand/model system? What video also?

Configuration looks correct, and 14.04 in most cases now works better than the older versions refered to in links below. Is it just going to black screen or giving error that incorrect boot device? Some vendors are modifying UEFI to only boot Windows and we have to copy grub to bootx64.efi and boot hard drive entry.
Best to backup  both Windows & efi partition before making any changes.
Lots of general info & links in the link in my signature.

You also show a lot of Centos entries in UEFI. UEFI has its own NVRAM and remembers entries. You have to manually delete those.

 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

      
 # from liveDVD or flash and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by marius_wiik on 2014-09-22
Hello and thanks for the reply.

Its a Toshiba Portegè Z930. Came with Win 8 from factory. 
The videocard is a nvidia HD4000.

It does not give any error, but just boots straight into windows without prompting me with any options.
The centOS entries comes from me having installed CentOS briefly. This did however work fine with dual boot. 
But when I tried to uninstall CentOS I could not get rid of the dual boot (it always asked me if I wanted to boot into CentOS or Windows even though I uninstalled it).
So I formatted the HDD and reinstalled Windows. I thought this would delete the EFI-partition and the entries with it. How do I go about deleting them?

But heres a weird thing: when I came home from work just now and opened the computer (I did not shut it down before leaving, just closed it) I came straight into a black screen with options where I could choose Ubuntu or windows. I chose ubuntu, booted into it and it worked fine. I then pressed reboot and the computer booted straight into windows and nothing was closed. As if the computer hadnt rebooted. If I try to close the computer now it does not do the same thing. Really weird...
This does however tell me that ubuntu is installed properly.

Most of the links you provided are issues I am not facing; like "cant boot from CDrom/flash" and "Windows does not boot". My problem is just that I cant get into linux :)

Do you have any tips on other options I can choose in the boot-repair application? It says not to touch them without guidance, hehe :)
I am really at a loss

---

### Post by oldfred on 2014-09-22
I do not like Boot-Repairs fix for "buggy" UEFI. It used to be the only thing we knew worked and was ok, but it renames the Windows efi file, so you can only boot Windows from grub menu. And Windows updates overwrite the renamed file and you are back to only booting Windows.

Windows likes to reset UEFI so it is always first.

You can remove folders from UEFI to houseclean old installs, but then must also use efibootmgr as posted above to remove the entries from UEFI's NVRAM.

These are a bunch of the alternatives that have worked. Some work better with one computer or the other. Some also find using f12 or UEFI directly does boot Ubuntu, but you cannot change the default even with efibootmgr from Windows. Either UEFI is permanently set to only boot Windows or Windows 8.1 automatically resets itself to be first in UEFI boot order.

I prefer the rename of bootx64.efi as first to try. Others have found rEFInd to work but it adds some complications.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

   **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. Windows updates will cause issues and require redoing.
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

    Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
**d2**:  Disable Windows in UEFI and only boot from rEFInd or grub. If Windows is #1
sudo efibootmgr -A -b 0001

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

