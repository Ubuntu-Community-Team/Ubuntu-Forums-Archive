---
title: "Ubuntu fails to launch"
date: 2023-08-28
forum: New to Ubuntu
---

### Post by vermiou on 2023-08-28
Hello :)

I have a dual boot Windows 11 / Ubuntu 22.01 and it's been working fine until just now.

When  I boot the PC, I can select Windows 11 or Ubuntu. Windows still launches, but Ubuntu doesn't. Instead, here is what happens when I select Ubuntu:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292652&stc=1[/IMG]

**1st possible cause:**

Last time I used Ubuntu (so this morning), I played a bit with the linux commands in the terminal, as a way to learn them. The commands I played with were part of the commands shown on this page: [URL="https://ubuntupit.com/best-linux-commands-to-run-in-the-terminal/"]https://ubuntupit.com/best-linux-commands-to-run-in-the-terminal/
[/URL]Here is a list of commands that may have broken things (but I don't know them well so it's totally possible they are harmless):
[LIST]
[*]lsblk
[*]df
[*]uname
[*]ps
[*]kill
[/LIST]

**2nd possible cause:**

A few days ago I reduced the size of the Windows partition. I also tried to increase the size of the Ubuntu partition but didn't succeed. However I didn't use any commands; instead I used the Disk Manager on Windows (to reduce the Windows partition) then the software EaseUS Partition Master on Windows (to try to increase the Ubuntu partition, but it turned out I couldn't do anything without a paid version). So, since I didn't use any command, I don't see how this event could have broken things, especially considering that I could still launch Ubuntu after that. But maybe I'm wrong

**Other possible causes:**
Of course the cause may be something else that I didn't think of!

Thank you very much for your help! :)

---

### Post by jsdata on 2023-08-28
I guess that you found the cause in the '[B]2nd possible cause'

[/B]It is dangerous to play around with partitions and it is definitely 2x more dangerous to play around with partitions in dual boot setup.

---

### Post by Rubi1200 on 2023-08-28
First steps:

Go to BIOS and check the following:
1. fast startup is disabled
2. TPM is disabled
3. secure boot is disabled

Does this resolve the issue and can you get into Ubuntu?

If yes, great.

If not, go to step 2. below

Then after that use a liveUSB and boot and choose to Try Ubuntu. Then run the boot info script in my signature and post the report here. Do not try and repair anything, just the report please.

As far as the commands you "played" around with, I don't think any of them could have caused this though we don't know what parameters you used with them.

---

### Post by vermiou on 2023-08-28
@jsdata Okay thank you for the information, I'll remember

@Rubi1200 Okay thank you for your help! I managed to disable Secure Boot but I don't find the options for TPM and Fast Startup. Options include : UBB Boot, PXE Boot to LAN, IPV4 PXE First, EFI, AMD Platform Security Processor, Clear AMD PSP Key, Device Guard, Reset to Setup Mode, Restore Factory Keys, Wireless LAN, Graphics Device, UMA Frame Buffer Size, ADM V (TM) Technology, BIOS Back Flash, Fool Proof Fn Ctrl, Always On USB, Charge in Battery Mode, Disable Building-in Battery, Flip to Boot, Instant Boot (maybe that's the Fast Boot option?), Advanced thermal optimization, Restore Default Overclocking

I'll follow your instructions, but just to let you know: keeping the Windows partition smaller is not important to me, so if necessary we can increase its size back to normal. Anyway I'll follow your instructions in any case :) Thank you again, by the way!

---

### Post by MAFoElffen on 2023-08-28
It looks like, from the last boot message posted, that is is getting stuck, while checking the integrity of the filesystem.

If you go to a rescue menu from Advanced Options of the Grub2 Boot menu, what happens when you select 'fsck'?

---

### Post by vermiou on 2023-08-28
@MAFoElffen Thank you for your response :) So I went in the Advanced Options, selected "Ubuntu . . . (recovery mode)" (I supposed it was the "rescue menu" you mentionned), then selected fsck, and now here is what is displayed:

"Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab.
Do you wish to continue?
<Yes>     <No>"

I'm afraid haha! Should I click "yes"?

---

### Post by vermiou on 2023-08-28
By the way, when I click "resume" instead of "fsck", Ubuntu launches! But it's abviously not a nice way to launch Ubuntu

---

### Post by yancek on 2023-08-28
I agree that the commands you mention are unlikely to have caused the problem as the first for are used to output information and the kill command kills or stops some process.  I suppose you could have problems depending upon any parameters you used.

Attempting to modify partitions is the likely culprit.  I'm wondering why you used Easus when you have the Linux GUI partition manager (GParted) on the Ubuntu install USB?

Use the Ubuntu install USB as suggested above to run boot repair as that is probably going to get the most detailed information to share with members here to help you.

---

### Post by vermiou on 2023-08-28
Okay so here is the Boot Info Summary:

```
boot-repair-4ppa2056                                              [20230828_2054]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p5: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.2 LTS on nvme0n1p4
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA104M [GeForce RTX 3070 Mobile / Max-Q] EFI VGA from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: GKCN58WW(1.58) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0003,0004,0000,2001,2002,2003
Boot0000* Linpus lite    HD(2,GPT,f45e2fa1-c5a6-4d79-876d-c8245af921e0,0x95f864,0x2754)/File(\EFI\Boot\grubx64.efi)RC
Boot0001* EFI PXE 0 for IPv4 (88-A4-C2-5E-5C-80)     PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(88a4c25e5c80,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* EFI PXE 0 for IPv6 (88-A4-C2-5E-5C-80)     PciRoot(0x0)/Pci(0x2,0x1)/Pci(0x0,0x0)/MAC(88a4c25e5c80,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* ubuntu    HD(1,GPT,13f37f8b-20f0-4acc-8d7c-1ae590947af5,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* Windows Boot Manager    HD(1,GPT,13f37f8b-20f0-4acc-8d7c-1ae590947af5,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...-................
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

64349b3622c65f495a99dbf6102496e3   nvme0n1p1/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/Boot/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
e8ff23a00deb497b7c2810724c12b886   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
ffede7b36c5c8710ef9560a03f5c7948   nvme0n1p1/Microsoft/Boot/bootmgr.efi
b8796e68099026aabcebb8fcf75b21f6   nvme0n1p1/Microsoft/Boot/cbmr_driver.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 71908121-8964-4B5B-BA6F-95304AE76275
              Start        End   Sectors   Size Type
nvme0n1p1      2048     534527    532480   260M EFI System
nvme0n1p2    534528     567295     32768    16M Microsoft reserved
nvme0n1p3    567296  637716479 637149184 303.8G Microsoft basic data
nvme0n1p4 637718528  996118527 358400000 170.9G Linux filesystem
nvme0n1p5 996118528 1000214527   4096000     2G Windows recovery environment
Disk sda: 7.24 GiB, 7776239616 bytes, 15187968 sectors
Disk identifier: F45E2FA1-C5A6-4D79-876F-C8245AF921E0
        Start      End Sectors  Size Type
sda1       64  9828451 9828388  4.7G Microsoft basic data
sda2  9828452  9838519   10068  4.9M EFI System
sda3  9838520  9839119     600  300K Microsoft basic data
sda4  9842688 15187904 5345217  2.5G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:7776MB:scsi:512:512:gpt:Kingston DataTraveler 3.0:;
1:32.8kB:5032MB:5032MB::ISO9660:hidden, msftdata;
2:5032MB:5037MB:5155kB::Appended2:boot, esp;
3:5037MB:5038MB:307kB::Gap1:hidden, msftdata;
4:5039MB:7776MB:2737MB:ext4::;
nvme0n1:512GB:nvme:512:512:gpt:SAMSUNG MZALQ512HBLU-00BL2:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:327GB:326GB:ntfs:Basic data partition:msftdata;
4:327GB:510GB:184GB:ext4::;
5:510GB:512GB:2097MB:ntfs:Basic data partition:hidden, diag;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660  2023-08-08-01-19-05-00                                                    Ubuntu 22.04.3 LTS amd64 
&#9500;&#9472;sda1      iso9660  2023-08-08-01-19-05-00               f45e2fa1-c5a6-4d79-876e-c8245af921e0 Ubuntu 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sda2      vfat     F7DB-4D56                            f45e2fa1-c5a6-4d79-876d-c8245af921e0 ESP                      Appended2
&#9500;&#9472;sda3                                                    f45e2fa1-c5a6-4d79-876c-c8245af921e0                          Gap1
&#9492;&#9472;sda4      ext4     56979374-2424-4753-953f-abeba470d4fa c53af19b-320e-184b-a605-81fb17f12a75 writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     E04B-9111                            13f37f8b-20f0-4acc-8d7c-1ae590947af5 SYSTEM                   EFI system partition
&#9500;&#9472;nvme0n1p2                                               5f456263-b83c-4148-9851-5a332a151420                          Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     625C4E1B5C4DE9FD                     574ae9a7-d36d-48ce-91ea-909d5f0ed3aa Windows-SSD              Basic data partition
&#9500;&#9472;nvme0n1p4 ext4     272d4380-0d72-4177-b30d-d499ab3c3dde 20b136cc-ec11-47a9-8ffd-46183ec9a7be                          
&#9492;&#9472;nvme0n1p5 ntfs     9A584ECE584EA8B9                     4d5c866e-b4cd-4b0e-b72d-5177d535bccd WinRE_DRV                Basic data partition

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-08-28.1/crash]   2.3G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-08-28.1/log]     2.3G   0% /var/log
/dev/nvme0n1p1                                                217.6M  15% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                                                 96.7G  68% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                102.3G  34% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5                                                  1.2G  39% /mnt/boot-sav/nvme0n1p5
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 272d4380-0d72-4177-b30d-d499ab3c3dde root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p4/boot/grub/grub.cfg (filtered) ====================

Ubuntu   272d4380-0d72-4177-b30d-d499ab3c3dde
Ubuntu, with Linux 6.2.0-26-generic   272d4380-0d72-4177-b30d-d499ab3c3dde
Ubuntu, with Linux 5.19.0-46-generic   272d4380-0d72-4177-b30d-d499ab3c3dde
Windows Boot Manager (on nvme0n1p1)   osprober-efi-E04B-9111
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p4/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p4 during installation
UUID=272d4380-0d72-4177-b30d-d499ab3c3dde /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=E04B-9111  /boot/efi       vfat    umask=0077      0       1

==================== nvme0n1p4/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p4: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 362.936256409 = 389.699837952  boot/grub/grub.cfg                             1
 404.327274323 = 434.143105024  boot/vmlinuz                                   2
 381.583644867 = 409.722318848  boot/vmlinuz-5.19.0-46-generic                 2
 404.327274323 = 434.143105024  boot/vmlinuz-6.2.0-26-generic                  2
 381.583644867 = 409.722318848  boot/vmlinuz.old                               2
 441.837886810 = 474.419818496  boot/initrd.img                                4
 352.968528748 = 378.997071872  boot/initrd.img-5.19.0-46-generic              1
 441.837886810 = 474.419818496  boot/initrd.img-6.2.0-26-generic               4
 352.968528748 = 378.997071872  boot/initrd.img.old                            1

=================== nvme0n1p4: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p4,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

---

### Post by Rubi1200 on 2023-08-29
I would suggest running the liveUSB again and this time follow the boot repair recommendation to reinstall GRUB in the right place.

Hopefully that will fix the booting into Ubuntu problem.

Now you also know not to try and use Windows tools to manipulate Linux filesystems. Best graphical tool for that is GParted, which comes on the live media by default but not once the system is installed.

---

### Post by vermiou on 2023-08-29
Thank you your response :)

So I did the boot repair. An error occured, here is the pastebin given by the program: [https://paste.ubuntu.com/p/WNfRt5KcsS/](https://paste.ubuntu.com/p/WNfRt5KcsS/)

Should I send an email to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL], as suggested by the program?

Thank you again for your precious help!

---

### Post by tea for one on 2023-08-29
From the boot-repair report:- [COLOR="#0000FF"]grub-install: warning: You will have to complete the GRUB setup manually[/COLOR]
Let's try the procedure manually.

Power off PC
Boot into a live session 
Open a terminal and mount the root partition (/) of the device containing your OS.        
```
sudo mount /dev/nvme0n1p4 /mnt
```
You can verify that this device contains your root partition (/) by doing an &#8220;ls&#8221; on the directory you mounted
```
ls /mnt
bin  boot  dev  etc  home  initrd.img  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var  vmlinuz

```
Mount the /dev/nvme0n1p1 partition as that is your efi partition and do an &#8220;ls&#8221; to check
```
sudo mount /dev/nvme0n1p1 /mnt/boot/efi

```
```
ls /mnt/boot/efi
EFI
```

Mount the rest of the directories that GRUB needs to use to check for other operating systems, etc.
We can do this one at a time with multiple commands like this: 
```
sudo mount -B /dev /mnt/dev
sudo mount -B /dev/pts /mnt/dev/pts
sudo mount -B /proc /mnt/proc
sudo mount -B /sys /mnt/sys
```

Or we can do this much easier in one command with the help of a &#8220;for loop&#8221;:
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```

Chroot into your environment 
```
sudo chroot /mnt
```
Terminal prompt changes to root@ubuntu:/# (originally ubuntu@ubuntu:~$)

Fix grub
```
grub-install /dev/mvme0n1
grub-install --recheck /dev/nvme0n1
update-grub
```

Now you can exit the chroot environment
```
exit
```

Power off and reboot.

---

### Post by oldfred on 2023-08-29
Seen several systems with "locked NVRAM" issues.
Some seem to resolve themselves. Some have specific UEFI settings 
Several links with some suggestions:
Locked NVRAM
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked UEFI/BIOS setting: Lenovo UEFI screen, other vendors may have similar setting somewhere:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

---

### Post by tea for one on 2023-08-29
From Post no.4, I see that you have some Security options in your UEFI settings:-
Perhaps disable any which may prevent Grub being re-installed correctly e.g. 
AMD Platform Security Processor
Device Guard
Instant Boot

May or may not help, let's see...........

---

### Post by vermiou on 2023-08-29
@tea for one

Thank you so much for your answer! It's so clear and detailed! :)

I've disabled the things you suggested to disable (AMD Platform Security Processor, Device Guard, Instant Boot). Then I rebooted but Ubuntu still didn't work. So I opened a live session of Ubuntu ("Try Ubuntu") then entered the commands you suggested. Things were okay until the 3rd command appearently:

```
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p4 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
boot  dev    home  lib32  libx32  media       opt  root  sbin  srv   tmp  var
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1 /mnt/boot/efi
mount: /mnt/boot/efi: /dev/nvme0n1 already mounted or mount point busy.
ubuntu@ubuntu:~$
```

Do you have any idea of what to do?

Thank you very much @tea for one!



@oldfred Thank you for your response! :) I'm going to check the posts you mentionned

---

### Post by oldfred on 2023-08-29
You posted this:
sudo mount /dev/nvme0n1 /mnt/boot/efi
But ESP is on this partition nvme0n1p1
nvme0n1 is the drive, nvme0n1p1 is a partition.

---

### Post by vermiou on 2023-08-29
@olfred Thank you very much! Your correction makes @teaforone code work! So here is what happened on the terminal of the live ubuntu session:

```

ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p4 /mnt
ubuntu@ubuntu:~$ ls /mnt
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
boot  dev    home  lib32  libx32  media       opt  root  sbin  srv   tmp  var
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p1 /mnt/boot/efi
ubuntu@ubuntu:~$ ls /mnt/boot/efi
'$RECYCLE.BIN'   BOOT   EFI  'System Volume Information'
ubuntu@ubuntu:~$ sudo mount -B /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -B /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount -B /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -B /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/mvme0n1
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck /dev/nvme0n1
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
root@ubuntu:/# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

```

I then powered off the PC, then rebooted it. Unfortunately, Windows disappeared as an option. So now there are only two options:
[LIST=1]
[*]Ubuntu 
[*]Advanced Options for Ubuntu 
[/LIST]

And unfortunately Ubuntu still doesn't boot.

Here is the Boot Info Summary: [https://paste.ubuntu.com/p/CxzVYy3gDX/](https://paste.ubuntu.com/p/CxzVYy3gDX/)

But we're gonna make it I'm sure :) And there is a good news: I can still use Ubuntu when I go in Advanced Options -> Ubuntu (recovery)

---

### Post by tea for one on 2023-08-29
In my post 12, I inadvertently made a typo error
```
sudo mount /dev/nvme0n1 /mnt/boot/efi [COLOR="#FF0000"]incorrect[/COLOR]
sudo mount /dev/nvme0n1p1 /mnt/boot/efi [COLOR="#0000FF"]correct[/COLOR]
```
Thanks to oldfred for the correction.

I've edited post 12 for the sake of accuracy.

---

### Post by tea for one on 2023-08-29
> **vermiou said:**
>  And there is a good news: I can still use Ubuntu when I go in Advanced Options -> Ubuntu (recovery)
Boot into Ubuntu via Advanced Options, open a terminal and enter
```
sudo grub-install /dev/nvme0n1
```
We might get lucky?

Also, to see if Grub can find the Windows Boot Manager, run
```
sudo update-grub

```

---

### Post by MAFoElffen on 2023-08-29
[COLOR=#ff0000]**Important before you do anything**...[/COLOR]

Recheck your BIOS Settings boot mode.

Am I the only one who saw this? This is the error you got:
```

ls: cannot access '/sys/firmware/efi/vars': No such file or directory

```
I have posted a short little query here to this forum, which many use to indicate whether they are booted as UEFI or Legacy. It is based on the results of that (above). If there is nothing found with that, then it was booted as Legacy/CSM mode. If there are results, then it was booted as UEFI.

Sometimes, you can rarely get an error like that booted a UEFI if the efivar module is not loaded to the kernel, but that is very rare.

---

### Post by vermiou on 2023-08-30
> **tea for one said:**
> Boot into Ubuntu via Advanced Options, open a terminal and enter
```
sudo grub-install /dev/nvme0n1
```
We might get lucky?

Also, to see if Grub can find the Windows Boot Manager, run
```
sudo update-grub

```

Thank your for your response! I did what you said, here is what happened on the terminal:
```
theo@theo-Legion-5-17ACH6H:~/Documents/l2info/s4$ sudo grub-install /dev/nvme0n1
[sudo] password for theo: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
theo@theo-Legion-5-17ACH6H:~/Documents/l2info/s4$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
theo@theo-Legion-5-17ACH6H:~/Documents/l2info/s4$ 
```

After that, I rebooted the PC. Windows Boot Manager is now selectable (!) but Ubuntu still doesn't boot unfortunately, here is the Boot Info Summary: [https://paste.ubuntu.com/p/kb5RZ9TjfC/](https://paste.ubuntu.com/p/kb5RZ9TjfC/)


> **MAFoElffen said:**
> [COLOR=#ff0000]**Important before you do anything**...[/COLOR]

Recheck your BIOS Settings boot mode.

Am I the only one who saw this? This is the error you got:
```

ls: cannot access '/sys/firmware/efi/vars': No such file or directory

```
I have posted a short little query here to this forum, which many use to  indicate whether they are booted as UEFI or Legacy. It is based on the  results of that (above). If there is nothing found with that, then it  was booted as Legacy/CSM mode. If there are results, then it was booted  as UEFI.

Sometimes, you can rarely get an error like that booted a UEFI if the  efivar module is not loaded to the kernel, but that is very  rare.


Thank you for your response! I've just checked (both on the Ubuntu partition and on the live Ubuntu session) and the following command:
```
~$ ls /sys/firmware/efi
```
works.
On the Ubuntu partition it displays this:
```
~$ ls /sys/firmware/efi
config_table  esrt              fw_vendor      runtime      systab
efivars       fw_platform_size  mok-variables  runtime-map
```



Thank you all for helping me. Without you I'd be lost! Thank you

---

### Post by tea for one on 2023-08-30
> **vermiou said:**
> After that, I rebooted the PC. Windows Boot Manager is now selectable (!) but Ubuntu still doesn't boot unfortunately
When you power on your PC, the Grub menu always appears?
Does Windows boot successfully from Grub?
Ubuntu still boots from Advanced Options?

For Ubuntu, which option do you select?

---

### Post by vermiou on 2023-08-30
> **tea for one said:**
> When you power on your PC, the Grub menu always appears?
Does Windows boot successfully from Grub?
Ubuntu still boots from Advanced Options?

For Ubuntu, which option do you select?

Thank you for your response!

Yes, when I power on my PC, the Grub menu always appears
Yes, Windows boots successfully from Grub
Yes, Ubuntu still boots successfully from "Advanced options for Ubuntu". It doesn't boot from "Ubuntu" but instead stays on a black screen with some white indications (see attached image).

To boot Ubuntu form "Advanced options", here is what I have to do :
[LIST=1]
[*]I go to "Advanced Options" > "Ubuntu, with Linux 6.2.0-31-generic (recovery mode)", then the recovery mode appears (see attached image) 
[*]I click on "Resume", then a kind of warning appears (see attached image) 
[*]I click on "OK", then Ubuntu boots successfully 
[/LIST]

---

### Post by tea for one on 2023-08-30
I notice that you have Nvidia Graphics and I wonder if this is a problem selecting the 6.2.0-31 kernel.
Can you try Advanced Options again and select your previous kernel 5.19.0-46-generic?

---

### Post by vermiou on 2023-08-30
There isn't such advanced option unfortunately. The advanced options are:
- "Ubuntu, with Linux 6.2.0-31-generic"
- same but with "(recovery mode)" at the end
- "Ubuntu, with Linux 6.2.0-26-generic"
- same but with "(recovery mode)" at the end

---

### Post by tea for one on 2023-08-30
That's odd because boot-repair report 20230830_0641 (30 August 2023) shows:-
[COLOR="#0000FF"]Line 199[/COLOR] - Ubuntu, with Linux 5.19.0-46-generic   272d4380-0d72-4177-b30d-d499ab3c3dde

Have you upgraded today and a previous kernel was removed automatically?

---

### Post by vermiou on 2023-08-30
No I didn't upgraded Linux today, at least not to my knowledge. But I'm a noob so it's totally possible I upgraded without knowing it :/ I'm sorry if I did

Here is a pastebin I did just now: [https://paste.ubuntu.com/p/FKyHGZJy9V/](https://paste.ubuntu.com/p/FKyHGZJy9V/)
It seems like it now indicates the newer version (line 159)

Thank you for your fast and consistent help @tea for one!

---

### Post by oldfred on 2023-08-30
At the recovery mode terminal/command line:

#What is installed
dkms status
Probably will not show the nVidia driver.

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade

f you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by vermiou on 2023-08-30
@oldfred Thank you for your response!

I ran the commands you suggested then rebooted the PC. Now Ubuntu boots successfully! And Windows still boots successfully too! So problem solved :)

Thank you everyone for your help, I'm very grateful! I will remember not to manipulate partitions from Windows. So, do you recommand using GParted on Ubuntu?

---

### Post by oldfred on 2023-08-30
Standard rule is to use Windows tools for Windows & Linux tools for Linux.
I use gparted, but you can only use it on unmounted partitions. Often then you have to use live installer.

Best to keep one flash drive as Windows repair/recovery flash drive and have Ubuntu live installer on another. Be sure to update them if you update installed version.
That is separate from your normal backups.

---

### Post by vermiou on 2023-08-31
Okay, so:
- to change the size of the Windows partition -> Windows Disk Manager
- to change the size of the Ubuntu partition -> GParted from a live Ubuntu session (or the command line but it's harder and requires more mastery)

Is that right?

---

### Post by tea for one on 2023-08-31
Yes to both questions.
Gparted is fine for regular home users.
Parted (cli version) does require extra effort.

After using Windows Disk Management, it is often useful to reboot Windows and run chkdsk.

---

### Post by vermiou on 2023-08-31
Alright, thank you very much!

---

