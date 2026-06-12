---
title: "No bootable device"
date: 2019-04-12
forum: New to Ubuntu
---

### Post by kekefi on 2019-04-12
Hello.

I wanted to install a light OS for an old laptop my mom uses mostly for Skype and browsing the internet/Youtube. The laptop's USB ports are busted (all of them), so I had to get an adapter that's SATA to USB and use my computer to install Lubuntu on the laptop's HDD, which worked fine. Upon turning the laptop on, however, I get the message there's no bootable device. I've tried to research a couple of things and see if I can get it fixed with [https://itsfoss.com/no-bootable-device-found-ubuntu/](https://itsfoss.com/no-bootable-device-found-ubuntu/) but the error persists. 

I can run the HDD with Lubuntu installed on my PC just fine, but the laptop doesn't want to budge. It's a Packard Bell EasyNote TE69KB series.

Any help would be appreciated as I'm not too familiar with Linux.

---

### Post by TheFu on 2019-04-12
Can you not install using an optical disk? Online specs say it has a DVD drive.

---

### Post by kekefi on 2019-04-12
This laptop was bought back in 2014 I believe, and it never came with a DVD drive.

---

### Post by TheFu on 2019-04-12
> **kekefi said:**
> This laptop was bought back in 2014 I believe, and it never came with a DVD drive.

I haven't seen a Packard Bell anything since around 2005. At the time, they were a little non-standard, used incompatible PSUs in their desktops. Laptops are always a little incompatible, so besides telling the BIOS to boot from the correct device I haven't a clue.  


2nd thought ... when you did the install, did you disconnect all your storage devices in YOUR computer and only have the USB install flash and her HDD connected?  Could grub/uefi have been installed onto your storage and not hers?

---

### Post by kekefi on 2019-04-12
> **TheFu said:**
> I haven't seen a Packard Bell anything since around 2005. At the time, they were a little non-standard, used incompatible PSUs in their desktops. Laptops are always a little incompatible, so besides telling the BIOS to boot from the correct device I haven't a clue.  


2nd thought ... when you did the install, did you disconnect all your storage devices in YOUR computer and only have the USB install flash and her HDD connected?  Could grub/uefi have been installed onto your storage and not hers?

It was a very cheap laptop back then and worked fine all this time, however I wanted to get rid of Windows 8.1 since it was extremely slow and broken. 

I'm not exactly sure what do you mean by that second thing. Few months back when I was testing Linux on my system it worked perfectly fine with no issues. Maybe I'm missing something during the partitioning? The installation doesn't allow me to "erase" the disk and install, it forces me to do a manual partition.

---

### Post by oldfred on 2019-04-12
Do not know if Packard Bell has UEFI updates, but best to check.
How much RAM?

If installed from another system, how you boot install media UEFI or BIOS is then how it installs.
And then system needs to be set to boot in that boot mode. UEFI or BIOS/CSM/Legacy.

It says Packard Bell is a subsiduary of Acer.
Acer has required "trust" setting  in UEFI for the .efi boot files. Is unique to Acer (and then maybe your system?).
Yours may then also be using similar UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
Old thread with Packard Bell. Boot-Repair now does the copy of shimx64, but grub also now installs another copy to /EFI/Boot/bootx64.efi. So if you have hard drive boot entry or fallback entry that may boot.
       Packard Bell Easynote manually renamed bootx64.efi, but best not to rename Windows efi boot file. Windows will overwrite that with updates anyway.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

If all USB ports not working, it may just be a setting in UEFI. 
With UEFI Secure boot using USB port to boot is not secure. So they have a separate setting for allow USB boot and/or USB port use. 
Check your UEFI settings.

---

### Post by kekefi on 2019-04-12
> **oldfred said:**
> Do not know if Packard Bell has UEFI updates, but best to check.
How much RAM?

If installed from another system, how you boot install media UEFI or BIOS is then how it installs.
And then system needs to be set to boot in that boot mode. UEFI or BIOS/CSM/Legacy.

It says Packard Bell is a subsiduary of Acer.
Acer has required "trust" setting  in UEFI for the .efi boot files. Is unique to Acer (and then maybe your system?).
Yours may then also be using similar UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
Old thread with Packard Bell. Boot-Repair now does the copy of shimx64, but grub also now installs another copy to /EFI/Boot/bootx64.efi. So if you have hard drive boot entry or fallback entry that may boot.
       Packard Bell Easynote manually renamed bootx64.efi, but best not to rename Windows efi boot file. Windows will overwrite that with updates anyway.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

If all USB ports not working, it may just be a setting in UEFI. 
With UEFI Secure boot using USB port to boot is not secure. So they have a separate setting for allow USB boot and/or USB port use. 
Check your UEFI settings.

USB ports have been busted for a while already, the system just doesn't detect anything.

I tried this whole "trust" thing, but the same issue persists. When I try to do it again, I get "FILE is exist". With UEFI on, Secure Boot on/off I still get default boot device missing. When I set it to Legacy, I get the same issue but in black and white (instead of that bright blue window).

P.S.- The laptop has 4 GB of RAM.

---

### Post by TheFu on 2019-04-12
> **kekefi said:**
> It was a very cheap laptop back then and worked fine all this time, however I wanted to get rid of Windows 8.1 since it was extremely slow and broken. 

I'm not exactly sure what do you mean by that second thing. Few months back when I was testing Linux on my system it worked perfectly fine with no issues. Maybe I'm missing something during the partitioning? The installation doesn't allow me to "erase" the disk and install, it forces me to do a manual partition.

There are 2 computers here.
A == yours
B == hers

When you did the install on A, did you disconnect all the storage devices except the flash install USB and her HDD?  If not, the boot files may have been installed onto another storage device in A.  When you move the HDD to B, there aren't any boot files.  Make sense now?

I don't have any special knowledge about installing onto Packard Bell UEFI systems.  There are lots and lots of settings in UEFI BIOSes. Always worth checking for new firmware.

I didn't google for "ubuntu {packard bell model} install", but that could be useful to see if anyone else has already found any boot options required.

In all the UEFI BIOSes I've seen, there is a boot-browser that let's me navigate different storage devices, then select the shimx64 or bootx64.efi as a boot choice.  My UEFI experience is highly, highly, limited. I've only seen 3 computers using it. Is this not an option on most UEFI setups?

---

### Post by oldfred on 2019-04-12
Do you have a hard drive entry or something in UEFI to boot as fallback.

UEFI installs grub to ESP partition on drive, but adds boot entries in UEFI inside UEFI on system.
If you move drive to another system it will not have the entry in UEFI to boot install and will not automatically find it.
But it should let you boot a hard drive entry in UEFI mode.

Also in UEFI do you see the /EFI/ubuntu folder and can add the shimx64.efi to boot options? And set trust on it?
You may need UEFI secure boot on, and UEFI password. Never lose UEFI password, or reset to blank when done.

---

### Post by vinayakmadiwalar9 on 2019-04-15
> **kekefi said:**
> Hello.

I wanted to install a light OS for an old laptop my mom uses mostly for Skype and browsing the internet/Youtube. The laptop's USB ports are busted (all of them), so I had to get an adapter that's SATA to USB and use my computer to install Lubuntu on the laptop's HDD, which worked fine. Upon turning the laptop on, however, I get the message there's no bootable device. I've tried to research a couple of things and see if I can get it fixed with [https://itsfoss.com/no-bootable-device-found-ubuntu/](https://itsfoss.com/no-bootable-device-found-ubuntu/) but the error persists. 

I can run the HDD with Lubuntu installed on my PC just fine, but the laptop doesn't want to budge. It's a Packard Bell EasyNote TE69KB series.

Any help would be appreciated as I'm not too familiar with Linux.


Dear sir/madam, 

Better U can use Ubuntu mate 32 bit its very good OS it will support all PC's link:  [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)
Thank you,

---

