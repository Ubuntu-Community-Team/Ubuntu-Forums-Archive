---
title: "Trouble getting dual boot working"
date: 2020-12-15
forum: New to Ubuntu
---

### Post by stonelaughter on 2020-12-15
Before I begin; this is not a Windows question; it's a UEFI/EFI question... please read through before "just saying no".

I have a Windows 10 system which I wish to install Ubuntu on as a second OS. I know this is hard but my research has so far yielded zero *effective* help. Here's the state of the system so far:

Boot Environment is EFI/GPT
Secure Boot is OFF in the BIOS.
the C: drive is NOT encrypted.
FastBoot is OFF.
Windows Partition has been resized 26.6GB smaller using Partition Master.
100MB FAT32 partition has been created and named "EFI".
1GB FAT32 partition has been created and named "SWAP".
the rest of the unallocated space has been formatted as EXT4.

I booted from an Ubuntu 20.10 USB stick and selected "Try Ubuntu". I connected to the internet. I ran the install Ubuntu icon. English (UK). Normal install. Then selected "Something Else". I set up the relevant partitions (/dev/nvme01p4,5 & 6) as EFI, SWAP and ROOT as per the instructions I have, and told it (as instructed) to install GRUB on /dev/nvme0n1p6.

The install went all the way through and then failed on installing GRUB. "This is a fatal error".

When I tried to boot, it didn't even list the new Ubuntu install as an option when I press "ESC" - it just showed Windows and the USB stick.

So: I have used BCDEDIT in Windows and EasyUEFI to try to get the bootloader to start Linux. Long story short, the result is now that I have copied bootx64.efi from /EFI/Boot on the USB stick to the existing EFI partition, and called it "ubuntu.efi": then used BCDEDIT to create the following EFI Configuration:

```

Windows Boot Manager--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume1
path                    \EFI\Boot\ubuntu.efi
description             Ububtu Boot Manager
locale                  en-GB
inherit                 {globalsettings}
isolatedcontext         Yes
default                 {bootmgr}
resumeobject            {4d69132b-1bc1-11eb-841f-bc8d911d31cc}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             Windows 10
locale                  en-GB
inherit                 {bootloadersettings}
recoverysequence        {4d69132d-1bc1-11eb-841f-bc8d911d31cc}
displaymessageoverride  Recovery
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {4d69132b-1bc1-11eb-841f-bc8d911d31cc}
nx                      OptIn
bootmenupolicy          Standard

```

The case in the pathname is correct for what's on the EFI partition.

Ubuntu install has NOT copied anything to the new EFI partition I created earlier. I don't know how to use GRUB as my bootloader, and I now don't know where to go to put my system "right" in terms of moving forward. If you need commands running in Ubuntu to get more info, please let me know; I'm not scared of the shell, but I don't know which output will be useful to give all the information needed to diagnose this. I'll be booting from the "Try Ubuntu" USB stick.

Here's some more info:

```

**ubuntu@ubuntu:~$ sudo fdisk -l**
Disk /dev/loop0: 1.98 GiB, 2125537280 bytes, 4151440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 62.09 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 50.67 MiB, 53133312 bytes, 103776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 30.94 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 217.89 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 55.32 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
The backup GPT table is not on the end of the device.

Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: INTEL HBRPEKNX0202A                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A9169AB4-2402-4A0F-986E-C3A1A7D29D4E

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  940951551 940384256 448.4G Microsoft basic data
/dev/nvme0n1p4 940951552  941156351    204800   100M Microsoft basic data
/dev/nvme0n1p5 941156352  943253503   2097152     1G Microsoft basic data
/dev/nvme0n1p6 943253504  996927487  53673984  25.6G Microsoft basic data
/dev/nvme0n1p7 996927488 1000204287   3276800   1.6G Windows recovery environment

Disk /dev/nvme1n1: 27.25 GiB, 29260513280 bytes, 57149440 sectors
Disk model: INTEL HBRPEKNX0202AO                    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 114.56 GiB, 123010547712 bytes, 240254976 sectors
Disk model: Ultra Fit       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000343d0

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 240254975 240252928 114.6G  c W95 FAT32 (LBA)

```

---

### Post by stonelaughter on 2020-12-15
p.s. I don't really care whether I select Ubuntu from a GRUB loader or from the Windows Boot loader... I just want to be able to boot either by choice.

---

### Post by ajgreeny on 2020-12-15
I suspect you complicated things by creating a second EFI partition; you really should not need to do that if one already exists for the Windows 10 installation.

However, tell us more about your hardware, its make and spec as far as you can. I note you have an nvme SSD drive and they can sometimes require firmware updates.
It will be helpful to see the output of ***inxi -Fzx*** run from the live usb if you can as that will show hardware details.

---

### Post by yancek on 2020-12-15
The official Ubuntu documentation on dual booting with windows on a UEFI system is at the link below.  Apparently, you missed that in your search.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As pointed out above, there was no need to create an EFI partition as you already have one with your windows install.  Ubuntu will install its own files in that partition and will NOT affect or overwrite the windows EFI boot files.

No need to create a swap partition as newer releases of Ubuntu use a swap file.  If you do create a swap, don't format it with a windows filesystem (FAT32).

>  Then selected "Something Else". I set up the relevant partitions  (/dev/nvme01p4,5 & 6) as EFI, SWAP and ROOT as per the instructions I  have

If those are the Ubuntu partitons, your fdisk output should show them as "Linux filesystem" rather than "Microsoft basic data".

> and told it (as instructed) to install GRUB on /dev/nvme0n1p6.

That's not correct.  You need to install it to the device not a partition.  Installing to the partition will not put any Ubuntu EFI/Grub files on the EFI partition and thus you will be unable to boot.  The installer should show you the option to install to /dev/nvme0n1.  Since you indicate you did not do this, that is why you see the error "When I tried to boot, it didn't even list the new Ubuntu install as an  option when I press "ESC" - it just showed Windows and the USB stick."

Read the info at the link I posted above as it should answer most if not all of your questions.
"

---

### Post by stonelaughter on 2020-12-15
```


ubuntu@ubuntu:~$ inxi -Fzx
System:    Kernel: 5.8.0-25-generic x86_64 bits: 64 compiler: gcc v: 10.2.0 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Laptop System: ASUSTeK product: ZenBook UX434FQ_UX434FQ v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: UX434FQ v: 1.0 serial: <filter> UEFI: American Megatrends v: UX434FQ.300 date: 05/26/2020 
Battery:   ID-1: BAT0 charge: 50.3 Wh condition: 50.3/50.0 Wh (101%) model: ASUSTeK ASUS Battery status: Not charging 
           Device-1: hidpp_battery_0 model: Logitech K350 charge: 70% (should be ignored) status: Discharging 
           Device-2: hidpp_battery_1 model: Logitech Wireless Mouse MX Master charge: 100% (should be ignored) 
           status: Discharging 
CPU:       Info: Quad Core model: Intel Core i7-10510U bits: 64 type: MT MCP arch: Kaby Lake rev: C L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 36799 
           Speed: 800 MHz min/max: 400/4900 MHz Core speeds (MHz): 1: 800 2: 800 3: 801 4: 800 5: 800 6: 800 7: 800 8: 800 
Graphics:  Device-1: Intel UHD Graphics vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GP107M [GeForce MX350] vendor: ASUSTeK driver: nouveau v: kernel bus ID: 02:00.0 
           Device-3: IMC Networks USB2.0 HD IR UVC WebCam type: USB driver: uvcvideo bus ID: 1-5:7 
           Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa resolution: 1: 1920x1080~60Hz 
           2: 1080x2160~60Hz 
           Message: Unable to show advanced data. Required tool glxinfo missing. 
Audio:     Device-1: Intel vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           Sound Server: ALSA v: k5.8.0-25-generic 
Network:   Device-1: Intel Wireless-AC 9462 driver: iwlwifi v: kernel port: 4000 bus ID: 00:14.3 
           IF: wlo1 state: up mac: <filter> 
Drives:    Local Storage: total: 618.75 GiB used: 2.95 GiB (0.5%) 
           ID-1: /dev/nvme0n1 vendor: Intel model: HBRPEKNX0202A size: 476.94 GiB 
           ID-2: /dev/nvme1n1 vendor: Intel model: HBRPEKNX0202AO size: 27.25 GiB 
           ID-3: /dev/sda type: USB vendor: SanDisk model: Ultra Fit size: 114.56 GiB 
RAID:      Hardware-1: Intel Device driver: ahci v: 3.0 bus ID: 00:17.0 
Partition: ID-1: / size: 7.72 GiB used: 203.6 MiB (2.6%) fs: overlay source: ERR-102 
Swap:      Alert: No Swap data was found. 
Sensors:   Missing: Required tool sensors not installed. Check --recommends 
Info:      Processes: 326 Uptime: 20m Memory: 15.44 GiB used: 1.71 GiB (11.1%) Init: systemd runlevel: 5 Compilers: gcc: N/A 
           Packages: 1829 Shell: Bash v: 5.0.17 inxi: 3.1.07 
ubuntu@ubuntu:~$ 

```

As requested above. Next reply I'll get to when I'm back in Windows.

---

### Post by stonelaughter on 2020-12-15
> **yancek said:**
> The official Ubuntu documentation on dual booting with windows on a UEFI system is at the link below.  Apparently, you missed that in your search.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As pointed out above, there was no need to create an EFI partition as you already have one with your windows install.  Ubuntu will install its own files in that partition and will NOT affect or overwrite the windows EFI boot files.

No need to create a swap partition as newer releases of Ubuntu use a swap file.  If you do create a swap, don't format it with a windows filesystem (FAT32).


Thanks for the link I'll check it out. I tend (being experienced on Windows) to seek out instructions written by geeks rather than by corporations because they tend to be more useful; of course I forgot that Linux is mostly created by geeks(!!!) and would therefore have great docus out there!

> 
If those are the Ubuntu partitons, your fdisk output should show them as "Linux filesystem" rather than "Microsoft basic data".


That's how they are after following the instructions...

> 
That's not correct.  You need to install it to the device not a partition.  Installing to the partition will not put any Ubuntu EFI/Grub files on the EFI partition and thus you will be unable to boot.  The installer should show you the option to install to /dev/nvme0n1.  Since you indicate you did not do this, that is why you see the error "When I tried to boot, it didn't even list the new Ubuntu install as an  option when I press "ESC" - it just showed Windows and the USB stick."

Read the info at the link I posted above as it should answer most if not all of your questions.


I got the instructions from here : [https://www.ubuntubuzz.com/2020/10/how-to-install-ubuntu-2010-groovy-gorilla.html](https://www.ubuntubuzz.com/2020/10/how-to-install-ubuntu-2010-groovy-gorilla.html)

If they're wrong, an army of geeks should fall upon them. I'm learning though and will continue to!

---

### Post by ajgreeny on 2020-12-15
Those instructions are not actually wrong as far as I could see after a very speedy read through; the problem is that they assume, wrongly in your case, that this was a machine with no existing OS, and particularly Windows, already on-disk.

I personally found it less clear than the [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) site, but that could be because 
a) I have done it now so many times that I do not need instructions any more, and 
b) I no longer have Windows, except for a VM I use to update a TomTom SatNav device which is not supported ib any Linux distros.

Certainly worth reading the [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) site which also talks about dual boot systems, unlike the one you used.

---

### Post by stonelaughter on 2020-12-15
OK I've read it so many times and skimmed over it because I didn't recognise the name (and therefore assumed, per one site, that I didn't have it).

I hadn't disabled Intel Smart Technology... because in my BIOS it's called Intel Optane and Remote Storage Technology. Disabled that, and BOOM it's working. I don't know what the impact on my Windows Performance is going to be...?

But here I am logged into Chrome on Ubuntu 20.10 so thanks for pointing me at that official page.

---

### Post by oldfred on 2020-12-15
if you changed to AHCI in UEFI settings, you need the AHCI driver in Windows.
You may need to boot Windows in recovery mode, or temporarily change back from AHCI, until AHCI driver installed.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

---

