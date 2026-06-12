---
title: "Error No Such Device grub rescue"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Joerice50 on 2012-12-04
Hi All

Wubi install of Ubuntu 12.10 64bit on a separate drive has left computer with no access to windows XP or Ubuntu

error: no such device: 171ac798-94c6-4085-a564-cdae6a99a2b6. grub rescue

I tried the grub rescue disk to see if it recovers and fixes grub but no option to repair grub is available see 
[http://paste2.org/p/2561339](http://paste2.org/p/2561339)

Note I tied different setting for my disk controller i.e. RAID and ACHI to no avail and so returned to a standard SATA mode

I can see drives from the grub rescue so disks are viewable dont know about writing to them to fix grub though.

I have read some of the other posts and tried:
ls (hd0,1)/ 
The result:
error unknown filesystem

Any help appreciated to get something running

Cheers

Joe

---

### Post by COMECON on 2012-12-04
Have you tried Super Grub Disk 2? Try downloading it, burning on a CD, and booting. Then select **Detect Any OS**, and if Ubuntu is listed there, try to boot it. If you can boot it, try running this on a Terminal:
** $ sudo grub-install /dev/sda **
(If your MBR isn't on /dev/sda, change it).
Catbuntu

---

### Post by oldfred on 2012-12-04
Boot-Repair did not even see a drive other than the one it was running from???

Does BIOS show drive?

If you look in Disk Utility from liveCD and can see drive what does Smart Status show? All I know is green is good, but it can run tests.

---

### Post by Joerice50 on 2012-12-04
I have had this problem before on this machine and I recall an all forgiving sudo apt get command that got ubuntu to recognise the disk drives if only I could remember it. 

I will need to look back over my history to see if I can recover it

But I will try the second grub fix you recommended

Cheers

Joe

---

### Post by Joerice50 on 2012-12-05
> **COMECON said:**
> Have you tried Super Grub Disk 2? Try downloading it, burning on a CD, and booting. Then select **Detect Any OS**, and if Ubuntu is listed there, try to boot it. If you can boot it, try running this on a Terminal:
** $ sudo grub-install /dev/sda **
(If your MBR isn't on /dev/sda, change it).
Catbuntu

This detected windowsXP on the first drive and let me boot windows all other options to detect grub or Ubuntu failed.

Booted windows and disk management shows 3 disks now Wubi has created drive d
see drive details from XP[IMG]https://picasaweb.google.com/lh/photo/S6Cyar0cu8Gc2HwAlXAnj9MTjNZETYmyPJy0liipFm0?feat=directlink[/IMG] *Try opening the image in a new tab as it doesn't display in the body of the text *

Any info on how to restore the WinXP normal boot in the first instance appreciated. Note windows restore fails and cannot restore to an earlier date, plus on drive E there is an uninstall wubi icon any advice appreciated before I hit the uninstall button. 

I think the basis of the problem maybe the disk controller, in that windows can see all drives Ubuntu cannot see any' I think I added ""pci=nomsi"" plus some other commands to my prior boot load to get Puppy Linux to recognise the SATA drives advice on how I do this in Ubuntu would be appreciated.

 
Cheers

Joe

System Info follows:
```
Overall 
General  
    Operating System    Microsoft Windows XP Professional 
    Central Processor    AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 
    User Name    Joe 
Graphics  
    Video Adapter    NVIDIA GeForce 8500 GT 
    Video Memory    512.00 MB 
    Screen Resolution    1280 x 960 
Storage  
    Total Memory    1023.17 MB 
    Free Memory    392.41 MB 
    Total Hard disk    1164.39 GB 
    Free Hard disk    889.32 GB 
I/O  
    Mouse    Microsoft PS/2 Mouse 
    Keyboard    Standard 101/102-Key or Microsoft Natural PS/2 Keyboard 

Top  Operating System 
Computer System  
    Computer Name    JOE-DESKTOP1 
    User Name    Joe 
    Organization    N/A 
Operating System  
    OS Name    Microsoft Windows XP Professional 
    OS Version    5.1.2600 
    Service Pack    3.0 
    Product ID    76487-770-1897926-22684 
    System Up Time    05/12/2012 12:21:32 
    Internet Explorer Version    8.0.6001.18702 
    Microsoft DirectX Version    4.09.00.0904 
    OpenGL Version    5.1.2600.5512 (xpsp.080413-0845) 
Registry  
    Maximum Size    54 MB 
    Current Size    8 MB 
    Status    OK 

Top  Processor MainBoard 
Central Processor  
    CPU Name    AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 
    Code Name    Model 11, Stepping 2 
    Manufacturer    AuthenticAMD 
    Current Clock Speed    2600 Mhz 
    Max Clock Speed    2600 Mhz 
    Voltage    1.5V 
    External Clock    200 Mhz 
    Serial Number    178BFBFF00060FB2 
    CPU ID    x86 Family 15 Model 107 Stepping 2 
    Socket Designation    CPU 1 
    L1-Cache    256 KB 
    L2-Cache    1024 KB 
    L3-Cache    0 KB 
Motherboard  
    Model    MI-A78S-8209 
    Manufacturer    XFX 
    Serial Number    To be filled by O.E.M. 
    BIOS Name    BIOS Date: 06/06/08 15:06:34 Ver: 08.00.15 
    BIOS Vendor    American Megatrends Inc. 
    SMBIOS Version    080015  
    BIOS Date    06/06/2008 
BIOS Features  
    ISA is supported    Yes 
    PCI is supported    Yes 
    Plug and Play is supported    Yes 
    APM is supported    Yes 
    BIOS is Upgradable (Flash)    Yes 
    BIOS shadowing is allowed    Yes 
    ESCD support is available    Yes 
    Boot from CD is supported    Yes 
    Selectable Boot is supported    Yes 
    BIOS ROM is socketed    Yes 
    EDD (Enhanced Disk Drive) Specification is supported    Yes 
    Int 13h - 5.25 /1.2MB Floppy Services are supported    Yes 
    Int 13h - 3.5 / 720 KB Floppy Services are supported    Yes 
    Int 13h - 3.5 / 2.88 MB Floppy Services are supported    Yes 
    Int 5h, Print Screen Service is supported    Yes 
    Int 9h, 8042 Keyboard services are supported    Yes 
    Int 14h, Serial Services are supported    Yes 
    Int 17h, printer services are supported    Yes 
    Int 10h, CGA/Mono Video Services are supported    Yes 
    ACPI supported    Yes 
    USB Legacy is supported    Yes 
    LS-120 boot is supported    Yes 
    ATAPI ZIP Drive boot is supported    Yes 

Top  Memory Device 
Memory Resource  
    Total Memory    1023.17 MB 
    Used Memory    625.25 MB 
    Free Memory    397.91 MB 
    Memory Usage    61% 
Physical Memory  
    Memory Bank    BANK0 
    Description    Physical Memory 0 
    Device Locator    DIMM0 
    Capacity    1.00 GB 
    Speed    333 Mhz 
    Manufacturer    NULL 
    Data Width    64 bit 
    Memory Type    Unknown 
    Form Factor    DIMM 

Top  Drives 
Disk Drives  
    Name    Hitachi HDT721075SLA360 
    Media Type    Fixed hard disk media 
    Capability    698.64 GB 
    Interface Type    IDE 
    Partitions    1 
    Total Cylinders    91201 
    Total Heads    255 
    Total Sectors    1465144065 
    Total Tracks    23256255 
    Tracks Per Cylinder    255 
    Bytes Per Sector    512 
    Sectors Per Track    63 
    S.M.A.R.T Support    Yes 
    Current Temperature    0C (32F) 
Disk Drives  
    Name    ST3500418AS 
    Media Type    Fixed hard disk media 
    Capability    465.76 GB 
    Interface Type    IDE 
    Partitions    1 
    Total Cylinders    60801 
    Total Heads    255 
    Total Sectors    976768065 
    Total Tracks    15504255 
    Tracks Per Cylinder    255 
    Bytes Per Sector    512 
    Sectors Per Track    63 
    S.M.A.R.T Support    Yes 
    Current Temperature    0C (32F) 
CD-ROM Drive  
    Name    COMBO-52X16C 
    Drive    D: 
    Transfer Rate    NULL 
    Status    OK 
IDE Controller  
    Name    Standard Dual Channel PCI IDE Controller 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 
IDE Controller  
    Name    Primary IDE Channel 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 
IDE Controller  
    Name    Secondary IDE Channel 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 
IDE Controller  
    Name    Standard Dual Channel PCI IDE Controller 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 
IDE Controller  
    Name    Primary IDE Channel 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 
IDE Controller  
    Name    Secondary IDE Channel 
    Manufacturer    (Standard IDE ATA/ATAPI controllers) 
    Status    OK 

Top  Display 
Video Adapter  
    Name    NVIDIA GeForce 8500 GT 
    Video Processor    GeForce 8500 GT 
    Manufacturer    NVIDIA 
    Video Architecture    VGA 
    DAC Type    Integrated RAMDAC 
    Memory Size    512.00 MB 
    Memory Type    Unknown 
    Video Mode    1280 x 960 x 4294967296 colors 
    Current Refresh Rate    60 Hz 
    Driver Version    6.14.11.6218 
    Driver Date    28/06/2007 16:43:00 
Monitor  
    Name    Plug and Play Monitor 
    Screen Height    960 
    Screen Width    1280 
    Status    OK 

Top  Network 
Local Area Connection  
    Product Name    Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller 
    Service Name    yukonwxp 
    Manufacturer    Marvell 
    MAC Address    00:E0:61:16:5E:BF 

Top  Other Device 
Sound Device  
    Name    Philips 680 USB Camera Mic 
    Manufacturer    Philips 
    Status    OK 
Mouse  
    Name    Microsoft PS/2 Mouse 
    Manufacturer    Microsoft 
    Buttons    5 
    Status    OK 
Keyboard  
    Name    Standard 101/102-Key or Microsoft Natural PS/2 Keyboard 
    Description    Enhanced (101- or 102-key) 
    Function Keys    12 
    Status    OK 
USB Controller  
    Product Name    Standard OpenHCD USB Host Controller 
    Manufacturer    (Standard USB Host Controller) 
    Protocol Supported    Universal Serial Bus 
    Status    OK 
USB Controller  
    Product Name    Standard Enhanced PCI to USB Host Controller 
    Manufacturer    (Standard USB Host Controller) 
    Protocol Supported    Universal Serial Bus 
    Status    OK 
USB Controller  
    Product Name    Standard OpenHCD USB Host Controller 
    Manufacturer    (Standard USB Host Controller) 
    Protocol Supported    Universal Serial Bus 
    Status    OK 
USB Controller  
    Product Name    Standard Enhanced PCI to USB Host Controller 
    Manufacturer    (Standard USB Host Controller) 
    Protocol Supported    Universal Serial Bus 
    Status    OK 
 
```

Joe

---

### Post by oldfred on 2012-12-05
Added code tags. Please use code tags for any long post to make it easier to review & preserve formatting.

Windows uses disks for both drives & partitions. So when you say 3 disks you mean three partitions on one drive?

You can just reinstall the Windows boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
And normally Boot-Repair would see drive and offer to install syslinux boot loader which works just like Windows boot loader in the MBR.

You can also install lilo's boot loader which also works like Windows boot loader.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by YannBuntu on 2012-12-05
Maybe Boot-Repair-Disk failed to see the HDD because of its old (Debian-stable) drivers.
You may want to try Boot-Repair from a [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") disc. (which contains newer drivers)

---

### Post by Joerice50 on 2012-12-07
> **YannBuntu said:**
> Maybe Boot-Repair-Disk failed to see the HDD because of its old (Debian-stable) drivers.
You may want to try Boot-Repair from a [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") disc. (which contains newer drivers)

Dear all 
Thanks for all the advice I managed after a lot of different attempts to get back to square-1 using windows console and the fixmbr tool to restore a normal boot function to windows.

Now I have a boot menu that provides options for:

1 XP repair console
2 Windows XP
3 Ubuntu

Now I just need to get Ubuntu to run on these drives and with this XFX controller.
 
A new topic I think

Cheers

Joe Rice

---

