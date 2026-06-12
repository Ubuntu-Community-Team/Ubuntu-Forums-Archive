---
title: "Ubuntu Studio Boot Options Problems"
date: 2018-11-06
forum: New to Ubuntu
---

### Post by o0okrishnao0o on 2018-11-06
I installed Ubuntu studio (bionic 18.04)  on to an external usb drive and placed the boot loader onto the internal drive (with windows 10). My intention was to connect the drive when I wished to boot ubuntu and disconnect it to boot windows.

I have run into two problems with this that I need fixing

1) The boot loader freaks out if the ubuntu drive isn't connected. How do I change this so it boots into windows 10 as intended (automatic is preferred, but a typed command will do)?

2) The default (automatic) boot selection is ubuntu low latency, how do I change it to the regular kernel?

Thanks in advance for your help <3

Love and light
Krishna
-x-

---

### Post by yancek on 2018-11-06
You would have been better off installing the Ubuntu Grub bootloader to the external drive, either to the MBR or by creating a separate EFI partition on that drive during the install.  Boot Ubuntu and from a terminal run the command below and post the output here:

```
sudo efibootmgr
```

---

### Post by oldfred on 2018-11-06
As yancek suggests you want grub on external drive.

If BIOS relatively easy, as you just reinstall Windows BIOS boot loader to MBR of internal drive, and then install grub to MBR of external drive. Install grub first as Windows will not boot Ubuntu. Then in BIOS set external as first in boot order, if not found it should then boot Windows from internal drive.

If UEFI, bit more complicated. 
And you really need to partition in advance with an ESP - efi system partition (FAT32) on external drive.
UEFI only boots from ESP and /EFI/Boot/bootx64.efi. But grub normally installs to ESP on internal drive. 
Then you have to copy all of /boot/efi/EFI/ubuntu twice from ESP on internal drive to external drive's ESP. Once to /EFI/ubuntu and once to /EFI/Boot, but then rename shimx64.efi to bootx64.efi in copy in /EFI/Boot. You need the  copy in /EFI/ubuntu as full install expects other files in fixed /EFI/ubuntu path.

---

### Post by wildmanne39 on 2018-11-06
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by o0okrishnao0o on 2018-11-07
> **yancek said:**
> You would have been better off installing the Ubuntu Grub bootloader to the external drive, either to the MBR or by creating a separate EFI partition on that drive during the install.  Boot Ubuntu and from a terminal run the command below and post the output here:

```
sudo efibootmgr
```

EFI variables are not supported on this system.

Bootloader has to be on the internal drive, there is no option of putting it elsewhere.

---

### Post by o0okrishnao0o on 2018-11-07
> **oldfred said:**
> As yancek suggests you want grub on external drive.

If BIOS relatively easy, as you just reinstall Windows BIOS boot loader to MBR of internal drive, and then install grub to MBR of external drive. Install grub first as Windows will not boot Ubuntu. Then in BIOS set external as first in boot order, if not found it should then boot Windows from internal drive.

If UEFI, bit more complicated. 
And you really need to partition in advance with an ESP - efi system partition (FAT32) on external drive.
UEFI only boots from ESP and /EFI/Boot/bootx64.efi. But grub normally installs to ESP on internal drive. 
Then you have to copy all of /boot/efi/EFI/ubuntu twice from ESP on internal drive to external drive's ESP. Once to /EFI/ubuntu and once to /EFI/Boot, but then rename shimx64.efi to bootx64.efi in copy in /EFI/Boot. You need the  copy in /EFI/ubuntu as full install expects other files in fixed /EFI/ubuntu path.

BIOS isn't an option. External drives are lost in the boot order if they are disconnected (unfortunately). Similarly the boot manager has to be on internal drive, as BIOS will revert to boot from this drive first.

---

### Post by oldfred on 2018-11-07
What brand/model system?

UEFI does remove boot entries when a drive is disconnected, but not one configured for external boot.
With UEFI you configure grub to be like booting the installer. Windows & Ubuntu installers all boot in UEFI mode from an ESP (FAT32) with boot flag and /EFI/Boot/bootx64.efi. You can do that with a full install and the UEFI will boot external.

---

### Post by o0okrishnao0o on 2018-11-12
> **oldfred said:**
> What brand/model system?

UEFI does remove boot entries when a drive is disconnected, but not one configured for external boot.
With UEFI you configure grub to be like booting the installer. Windows & Ubuntu installers all boot in UEFI mode from an ESP (FAT32) with boot flag and /EFI/Boot/bootx64.efi. You can do that with a full install and the UEFI will boot external.

It's a custom buit laptop. BIOS is American megatrends V 2.15.1236
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Notebook                        
    Product Name: W65_67SR                        
    Version: Not Applicable                  
    Serial Number: Not Applicable                  
    Asset Tag: Tag 12345
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Not Applicable
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0



Enabling UEFI stops me from getting past BIOS with an error message asking me to insert a boot medium. With UEFI enabled all boot options are gone from BIOS.

---

### Post by oldfred on 2018-11-12
If UEFI Secure Boot on, normally all other boot options are disabled. And you usually have a separate entry to allow USB boot as that otherwise would not be secure.
On my motherboard the Secure boot setting is really "Windows" or "Other" and fine print says to use "Other" if installing Windows 7 as it does not support Secure Boot.
Not then sure about your UEFI/BIOS.
Do you have latest UEFI from vendor? Many have had to update for         mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

