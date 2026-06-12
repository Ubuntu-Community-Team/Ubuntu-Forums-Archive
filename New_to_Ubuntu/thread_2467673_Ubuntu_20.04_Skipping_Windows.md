---
title: "Ubuntu 20.04 Skipping Windows"
date: 2021-10-04
forum: New to Ubuntu
---

### Post by hkarthi on 2021-10-04
I am using Ubuntu 20.04 and dual booting Windows 10. 

I have three HDD:

1. SSD: Windows 10
2. 1 TB HDD: Ubuntu
3. 2 TB HDD: Data disk (no OS)

Everything was working fine and I was installing few things in Ubuntu. I changed the desktop manager in Ubuntu from GNOME to KDE to see which I like better. Everything was fine. 

Then I had to go into Windows and so I rebooted. It just rebooted to Ubuntu without showing the grub screen to choose the OS. 

I tried a few things like installing Grub boot repair kit and ran the tool. I got the error saying that your BIOS is in UEFI mode and I should change it to CMS/Legacy mode. My BIOS has been in legacy mode all this time.

So I am not sure why I am getting this error and why I cannot boot into Windows.

Any help will be appreciated. 

Thank you!

---

### Post by hkarthi on 2021-10-04
Just a quick update, here is the message I get when I try to run boot-repair:

LegacyWindows detected. Please enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB).

---

### Post by Impavidus on 2021-10-04
Boot-Repair can create a boot info summary, giving you a link to share on the forums. Can you give us that link? That will give some more information.

Windows 10 is usually installed in UEFI mode. Dual booting Ubuntu with Windows 8 and up in legacy mode is rather fragile. Fortunately, you've installed them on different drives, so maybe it helps if you change boot order.

---

### Post by yancek on 2021-10-04
>   I changed the desktop manager in Ubuntu from GNOME to KDE to see which I like better 

Is there any particular reason you did not install Kubuntu rather than Ubuntu as that is the primary difference between the 2?

>  It just rebooted to Ubuntu without showing the grub screen to choose the OS. 
 

Common scenario when Grub sees only one OS.

> I tried a few things like installing Grub boot repair kit and ran the tool. 

Mistake.  Did you not pay any attention to the boot repair page, linked below.  You can see near the very top of the page in bold text indicating it will create a pastebin link so thata "experienced" members can assist you.  Rather than do that, you tried to repair something you obviously don't know how to do so run boot repair again with the Create BootInfo Summary option and paste the link here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

>   I got the error saying that your BIOS is in UEFI mode and I should change it to CMS/Legacy mode.

You got that message because your windows 10 is installed in Legacy mode which it usually is not unless someone chose to install it that way or it is an update from an unsupported Legacy install.  In addition, you have mistakenly booted and installed Ubuntu in UEFI mode. GRub installed UEFI will boot another Linux installed in Legacy mode or UEFI mode but will NOT boot windows installed in Legacy mode.  Grub installed in Legacy mode will boot an EFI install of Linux but will not boot an EFI install of windows.  Windows of course, won't boot Linux in either mode.

Run boot repair and post the link here.  The link below to the Ubuntu documentation explains how to covert Ubuntu to Legacy mode.  You can either try that or reinstall Ubuntu.

---

### Post by hkarthi on 2021-10-04
Here is the boot-repair information:

```
boot-repair-4ppa130                                              [20211004_1929]

============================== Boot Info Summary ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.
 => No known boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd


================================ 2 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.3 LTS CurrentSession on sdb3
OS#2:   Windows 8 or 10 on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.11.0-37-generic root=UUID=c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65 ro quiet splash vt.handoff=7


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0001,0002,0000,0003
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* Hard Drive	BBS(HD,,0x0)..GO..NO........o.S.a.m.s.u.n.g. .S.S.D. .8.5.0. .E.V.O. .5.0.0.G.B....................A...........................>..Gd-.;.A..MQ..L.2.S.A.R.B.N.J.0.1.4.1.5.1.7. .A. . . . ........BO..NO........o.T.O.S.H.I.B.A. .D.T.0.1.A.C.A.1.0.0....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . .3. .R.7.T.0.K.G.S.F........BO..NO........o.S.T.2.0.0.0.D.M.0.0.5.-.2.C.W.1.0.2....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .F.Z.4.L.Z.3.C.Y........BO..NO........k.S.a.n.D.i.s.k....................A.......................>..Gd-.;.A..MQ..L.4.C.5.3.0.0.0.1.1.1.0.3.1.3.1.1.5.1.0.5........BO
Boot0002* CD/DVD Drive	BBS(CDROM,,0x0)..GO..NO........o.H.L.-.D.T.-.S.T. .D.V.D.R.A.M. .G.H.2.4.N.S.D.1....................A...........................>..Gd-.;.A..MQ..L.E.K.G.W.K.A.5.A.1.1. .7. . . . . . . . ........BO
Boot0003* Pop!_OS 21.04	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* ubuntu	HD(1,GPT,4494b26a-5fc5-4592-8b18-2307451c2b43,0x800,0x1dc000)/File(\EFI\UBUNTU\SHIMX64.EFI)

85fa9d77b929ec4231aba29476574eb6   sdb1/BOOT/fbx64.efi
469e608783843a701d172242f016c79c   sdb1/BOOT/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sdb1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sdb1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sdb1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sdb1/BOOT/BOOTX64.efi
ae8af199ef80311f9cee9de104a15496   sdd1/boot/bootx64.efi
1309af23db7b4cdd16bb29b41d6975e5   sdd1/microsoft/boot/cdboot.efi
ba914e4bb811a1b27220f020d2672167   sdd1/microsoft/boot/cdboot_noprompt.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdb	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdc	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	34 sectors * 512 bytes
sdd	: notGPT,	no-BIOSboot,	has-noESP, 	liveusb,	not-mmc, no-os,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdb3	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sda3	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdb1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb4	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdc2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdd1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

sdb3	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot
sda2	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdc2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdd1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot

Partitions info (3/3): _________________________________________________________

sdb3	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sdb
sda1	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda2	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda3	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sdb1	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdb
sdb4	: maybesepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdb
sdc2	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdc
sdd1	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdd

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x6237bdb1
      Boot     Start       End   Sectors   Size Id Type
sda1  *         2048    104447    102400    50M  7 HPFS/NTFS/exFAT
sda2          104448 975726701 975622254 465.2G  7 HPFS/NTFS/exFAT
sda3       975728640 976769023   1040384   508M 27 Hidden NTFS WinRE
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 3535E0CB-D8B8-4B5E-A1F6-15676E232550
          Start        End    Sectors   Size Type
sdb1       2048    1951743    1949696   952M EFI System
sdb2    1951744   31248383   29296640    14G Linux swap
sdb3   31248384  226557951  195309568  93.1G Linux filesystem
sdb4  226557952 1953523711 1726965760 823.5G Linux filesystem
Disk sdc: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 32628C0B-12BA-48DE-A97A-9B202B298110
      Start        End    Sectors  Size Type
sdc1     34      32767      32734   16M Microsoft reserved
sdc2  32768 3907026943 3906994176  1.8T Microsoft basic data
Disk sdd: 28.66 GiB, 30752000000 bytes, 60062500 sectors
Disk identifier: 0x0019ed44
      Boot Start      End  Sectors  Size Id Type
sdd1  *     2048 60062499 60060452 28.7G  7 HPFS/NTFS/exFAT

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:msdos:ATA Samsung SSD 850:;
1:1049kB:53.5MB:52.4MB:ntfs::boot;
2:53.5MB:500GB:500GB:ntfs::;
3:500GB:500GB:533MB:ntfs::msftres;
sdb:1000GB:scsi:512:4096:gpt:ATA TOSHIBA DT01ACA1:;
1:1049kB:999MB:998MB:fat32::boot, esp;
2:999MB:16.0GB:15.0GB:linux-swap(v1)::swap;
3:16.0GB:116GB:100GB:ext4::;
4:116GB:1000GB:884GB:ext4::;
sdc:2000GB:scsi:512:4096:gpt:ATA ST2000DM005-2CW1:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
sdd:30.8GB:scsi:512:512:msdos:SanDisk Ultra:;
1:1049kB:30.8GB:30.8GB:ntfs::boot;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                       
&#9500;&#9472;sda1 ntfs     3C24BC6824BC26B4                     6237bdb1-01                          System Reserved 
&#9500;&#9472;sda2 ntfs     C23CCA403CCA2EEB                     6237bdb1-02                                          
&#9492;&#9472;sda3 ntfs     24C4DFC0C4DF9282                     6237bdb1-03                                          
sdb                                                                                                       
&#9500;&#9472;sdb1 vfat     C812-BFA4                            4494b26a-5fc5-4592-8b18-2307451c2b43                 
&#9500;&#9472;sdb2 swap     bca6de80-c139-4d37-9d7c-e79a7d91783f c6cfd5ab-b3fb-4131-804a-c5acb3643a96                 
&#9500;&#9472;sdb3 ext4     c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65 8dd63ff4-649f-42ed-84b6-540d530be334                 
&#9492;&#9472;sdb4 ext4     4b21ae45-23f4-473b-9bf7-c553c38b1f06 2a52fc58-ebe8-4288-8334-96c9d7401699                 
sdc                                                                                                       
&#9500;&#9472;sdc1                                               e6820bfa-166a-4ca0-a17f-dcea2f87d939                 Microsoft reserved partition
&#9492;&#9472;sdc2 ntfs     6836D5BE36D58D86                     47a3ae54-3c38-4515-8148-ef9d26b4cbcc Data Disk       Basic data partition
sdd                                                                                                       
&#9492;&#9472;sdd1 ntfs     649C82659C82321A                     0019ed44-01                          Windows10       

df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda1      23M  54% /mnt/boot-sav/sda1
sda2     337G  28% /mnt/boot-sav/sda2
sda3      79M  84% /mnt/boot-sav/sda3
sdb3    72.9G  15% /
sdb4   744.4G   3% /home
sdc2     1.5T  16% /mnt/boot-sav/sdc2
sdd1    24.3G  15% /mnt/boot-sav/sdd1

Mount options: __________________________________________________________________

sda1   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda2   ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda3   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sdb3   rw,relatime,errors=remount-ro
sdb4   rw,relatime
sdc2   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sdd1   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

===================== sdb1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65 root hd1,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdb3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65
Ubuntu, with Linux 5.11.0-37-generic   c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65
Ubuntu, with Linux 5.8.0-43-generic   c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sdb3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=c49e9ad1-8687-4f3e-bedb-d0fe53f7ed65 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=C812-BFA4  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb4 during installation
UUID=4b21ae45-23f4-473b-9bf7-c553c38b1f06 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=bca6de80-c139-4d37-9d7c-e79a7d91783f none            swap    sw              0       0

======================= sdb3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sdb3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  85.166137695 = 91.446444032   boot/grub/grub.cfg                             2
  77.402011871 = 83.109777408   boot/vmlinuz                                   1
  77.402011871 = 83.109777408   boot/vmlinuz-5.11.0-37-generic                 1
  17.759761810 = 19.069399040   boot/vmlinuz-5.8.0-43-generic                  2
  17.759761810 = 19.069399040   boot/vmlinuz.old                               2
  84.935859680 = 91.199184896   boot/initrd.img                                2
  84.935859680 = 91.199184896   boot/initrd.img-5.11.0-37-generic              2
  84.735084534 = 90.983604224   boot/initrd.img-5.8.0-43-generic               1
  84.735084534 = 90.983604224   boot/initrd.img.old                            1

===================== sdb3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18151 Aug 12 14:48 10_linux
-rwxr-xr-x 1 root root 42359 Jan 13  2021 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jan 13  2021 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jan 13  2021 30_os-prober
-rwxr-xr-x 1 root root  1424 Jan 13  2021 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13  2021 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2021 41_custom


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown MBR on /dev/sdd

00000000  41 4b 45 4f fc 31 c0 fa  8e d0 bc 00 7c fb 89 e6  |AKEO.1......|...|
00000010  89 e7 1e 06 8e d8 bb 13  04 8b 07 48 89 07 c1 e0  |...........H....|
00000020  06 2d c0 07 8e c0 b9 00  02 f3 a4 50 68 30 7c cb  |.-.........Ph0|.|
00000030  8e d8 66 31 db 8e c3 41  ba 81 00 e8 89 00 72 6d  |..f1...A......rm|
00000040  bb be 7d b9 04 00 26 80  3f 00 7c 09 75 05 83 c3  |..}...&.?.|.u...|
00000050  10 e2 f3 eb 58 be 94 7d  e8 da 00 e8 ca 00 ba 5a  |....X..}.......Z|
00000060  7d be 6e 7d e8 a0 00 b4  01 cd 16 75 3d b4 02 cd  |}.n}.......u=...|
00000070  16 24 04 75 38 80 3e 93  7d 00 7f 0b be b4 7d e8  |.$.u8.>.}.....}.|
00000080  b3 00 c6 06 93 7d 12 80  3e 92 7d 00 75 d9 e8 89  |.....}..>.}.u...|
00000090  00 c6 06 be 7d 81 68 80  00 ba 72 7d be 7e 7d e8  |....}.h...r}.~}.|
000000a0  65 00 5a 07 1f ea 00 7c  00 00 e8 6d 00 e8 78 00  |e.Z....|...m..x.|
000000b0  bb be 7d 8b 17 52 b2 80  8b 4f 02 66 8b 5f 08 e8  |..}..R...O.f._..|
000000c0  05 00 73 d5 07 1f cb 60  b4 41 bb aa 55 cd 13 72  |..s....`.A..U..r|
000000d0  2c 81 fb 55 aa 75 26 f7  c1 01 00 74 20 61 1e 66  |,..U.u&....t a.f|
000000e0  31 c0 8e d8 66 50 66 53  50 68 00 7c 40 50 6a 10  |1...fPfSPh.|@Pj.|
000000f0  89 e6 b4 42 cd 13 9f 83  c4 10 9e 1f c3 61 bb 00  |...B.........a..|
00000100  7c b8 01 02 cd 13 c3 fa  8b 1c 26 66 8b 07 66 89  ||.........&f..f.|
00000110  04 26 89 17 26 8c 4f 02  fb c3 fa bb 20 00 66 a1  |.&..&.O..... .f.|
00000120  6e 7d 26 66 89 07 fb c3  b4 01 cd 16 74 06 b4 00  |n}&f........t...|
00000130  cd 16 e2 f4 c3 ac 3c 00  74 09 b4 0e bb 07 00 cd  |......<.t.......|
00000140  10 eb f2 c3 50 2e a0 be  7d 80 fa 80 75 04 88 c2  |....P...}...u...|
00000150  eb 06 38 c2 75 02 b2 80  58 c3 fa 2e 80 3e 92 7d  |..8.u...X....>.}|
00000160  00 74 0a 2e fe 0e 93 7d  2e fe 0e 92 7d ea 20 00  |.t.....}....}. .|
00000170  00 00 9c 2e fe 06 91 7d  75 03 e8 c7 ff 9a 4c 00  |.......}u.....L.|
00000180  00 00 9c 2e fe 0e 91 7d  79 03 e8 b7 ff 9d ca 02  |.......}y.......|
00000190  00 ff 49 12 0d 0a 50 72  65 73 73 20 61 6e 79 20  |..I...Press any |
000001a0  6b 65 79 20 74 6f 20 62  6f 6f 74 20 66 72 6f 6d  |key to boot from|
000001b0  20 55 53 42 2e 00 00 00  44 ed 19 00 00 00 80 20  | USB....D...... |
000001c0  21 00 07 fe ff ff 00 08  00 00 24 73 94 03 00 00  |!.........$s....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


================================= User choice ==================================

Is sdb (ATA TOSHIBA DT01ACA1) a removable disk? no

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to remove grub-efi) and reinstall the grub2 of
sdb3 into the MBRs of all disks (except live-disks and removable disks without OS).
Grub-efi would not be selected by default because: legacy-win no-win-efi 
Additional repair would be performed: unhide-bootmenu-10s      

Blockers in case of suggested repair: __________________________________________

LegacyWindows detected. Please enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB). GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Final advice in case of suggested repair: ______________________________________


Please do not forget to make your BIOS boot on sdb (ATA TOSHIBA DT01ACA1) disk!
The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
```

---

### Post by hkarthi on 2021-10-04
Yes, I did know there was KUbuntu but I was not sure which one I would prefer. I read that it would be easy to install both on Ubuntu and tweak a bit to get the desired effect. I thought if I like KDE, I would simply continue to use Ubuntu with KDE or removed KDE and go with GNOME. 

> **yancek said:**
> Is there any particular reason you did not install Kubuntu rather than Ubuntu as that is the primary difference between the 2?


This is my second re-install of Ubuntu. The first time I installed Ubuntu, everything was working fine until I upgraded to 21.0 when everything went kaput and I had to reinstall Ubuntu. So this time I decided not to upgrade to 21. And it was working fine till yesterday. Today morning when I started the machine, it just went straight to Ubuntu instead of showing me the screen to choose. 


> **yancek said:**
> Common scenario when Grub sees only one OS.

I have pasted the result from the boot-repair. Thank you for the explanation. 

> **yancek said:**
> Mistake.  Did you not pay any attention to the boot repair page, linked below.  You can see near the very top of the page in bold text indicating it will create a pastebin link so thata "experienced" members can assist you.  Rather than do that, you tried to repair something you obviously don't know how to do so run boot repair again with the Create BootInfo Summary option and paste the link here.

You got that message because your windows 10 is installed in Legacy mode which it usually is not unless someone chose to install it that way or it is an update from an unsupported Legacy install.  In addition, you have mistakenly booted and installed Ubuntu in UEFI mode. GRub installed UEFI will boot another Linux installed in Legacy mode or UEFI mode but will NOT boot windows installed in Legacy mode.  Grub installed in Legacy mode will boot an EFI install of Linux but will not boot an EFI install of windows.  Windows of course, won't boot Linux in either mode.

Run boot repair and post the link here.  The link below to the Ubuntu documentation explains how to covert Ubuntu to Legacy mode.  You can either try that or reinstall Ubuntu.

I get the distinct feeling I have to reinstall. If so, what should I do? Change my BIOS to EFI or Legacy before reinstalling?

Thank you for helping me!

---

### Post by oldfred on 2021-10-04
Do not post Summary Report here, post the link to the summary report as Boot-Repair suggests.

If you do post longer terminal output or text, you need to use code tags which are easy to add with Forum's advanced Editor. 
Highlight text & click # icon.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

If UEFI hardware, we suggest UEFI installs and gpt partitioning. Note that changing to gpt from MBR will erase drive, so have good backups.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012.

A few users still like old BIOS/MBR, but that is available more for very old systems. But if just Ubuntu on a drive, better to use gpt, not MBR. MBR(msdos) now only required for BIOS install of Windows.
I started using gpt with my BIOS install in 2010. And every new drive or repartitioned drive is gpt. Even my 2006 XP laptop was converted to gpt with BIOS kubuntu boot.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Impavidus on 2021-10-04
It appears that Windows is in legacy mode and Ubuntu in UEFI mode, on separate drives. The Windows drive has a Windows bootloader, the Ubuntu drive has an EFI partition with Ubuntu bootloader.

The quick "fix": change UEFI to legacy mode and put the Windows drive first in boot order to boot Windows, change to UEFI mode and put the Ubuntu drive first in boot order to boot Ubuntu. Yes, that's inconvenient.

When dual booting Ubuntu and Windows 10, it's best to keep both in UEFI mode. But Windows is already in legacy mode and can't be converted without reinstalling Windows. So, best to install both in legacy mode. Dual booting Ubuntu and Windows 10 in legacy mode is fragile, but doable if both are in separate drives (as in your case).

---

### Post by hkarthi on 2021-10-04
Thank you for sharing the tips. I will make sure to use the tags correctly next time.

---

### Post by hkarthi on 2021-10-04
Thank you. Let me try to quick fix. If that doesn't work, I guess I am back to reinstalling. 

But if I am to reinstall, is this what I should? 

Step 1: Install Windows in EFI mode. 

Step 2: Install Ubuntu in EFI mode (in a different drive)

That should solve this problem right?

> **Impavidus said:**
> It appears that Windows is in legacy mode and Ubuntu in UEFI mode, on separate drives. The Windows drive has a Windows bootloader, the Ubuntu drive has an EFI partition with Ubuntu bootloader.

The quick "fix": change UEFI to legacy mode and put the Windows drive first in boot order to boot Windows, change to UEFI mode and put the Ubuntu drive first in boot order to boot Ubuntu. Yes, that's inconvenient.

When dual booting Ubuntu and Windows 10, it's best to keep both in UEFI mode. But Windows is already in legacy mode and can't be converted without reinstalling Windows. So, best to install both in legacy mode. Dual booting Ubuntu and Windows 10 in legacy mode is fragile, but doable if both are in separate drives (as in your case).

---

### Post by grahammechanical on 2021-10-04
This is the protocol. Windows and Ubuntu must be installed in the same boot mode. The boot mode we load the Ubuntu live/install session in will be the boot mode that Ubuntu is installed in.

Set the Ubuntu drive to have boot priority because the Ubuntu boot loader (Grub) will give an option to load Windows. If it does not do that then run this command in Ubuntu

```
sudo update-grub
```

If you are re-installing Windows you may wish to do that first and then disconnect the Windows drive when you install Ubuntu. Then reconnect the Windows drive and load Ubuntu and run that command.

Regards

---

### Post by hkarthi on 2021-10-04
So the process is this:

Step 1: Change BIOS mode from legacy to EFI 

Step 2: Install Windows

Step 3: Physically disconnect the Windows HDD (is this really required?)

Step 4: Install Ubuntu in the other HDD

Step 5: Reconnect Windows HDD

Step 6: Reboot PC and Grub will load with options to boot into Windows. 

Please correct me if I am wrong. I have already installed Ubuntu and Windows twice. This would be my third time reinstalling it. So want to get it right this time. 

> **grahammechanical said:**
> This is the protocol. Windows and Ubuntu must be installed in the same boot mode. The boot mode we load the Ubuntu live/install session in will be the boot mode that Ubuntu is installed in.

Set the Ubuntu drive to have boot priority because the Ubuntu boot loader (Grub) will give an option to load Windows. If it does not do that then run this command in Ubuntu

```
sudo update-grub
```

If you are re-installing Windows you may wish to do that first and then disconnect the Windows drive when you install Ubuntu. Then reconnect the Windows drive and load Ubuntu and run that command.

Regards

---

### Post by tea for one on 2021-10-05
> **hkarthi said:**
> Step 3: Physically disconnect the Windows HDD (is this really required?)
Not essential, however, it is [COLOR="#0000FF"]very good advice[/COLOR] to eliminate human error.
If your UEFI firmware allows it, you may be able to isolate or de-activate the drive without physically removing it.
> **hkarthi said:**
> Step 4: Install Ubuntu in the other HDD
Double check that you have booted in UEFI mode with this command in the terminal
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted (Windows 10 should automatically create GPT on its own disk)
> **hkarthi said:**
> Step 5: Reconnect Windows HDD
Reboot into Windows 10 (probably via UEFI boot menu) and check as much as possible
Then reboot into Ubuntu and run
```
sudo update-grub
```

---

### Post by yancek on 2021-10-05
The simplest or easiest solution is what is posted in post 8 above and quoted below.  If you do this, you will not need to reinstall or change drive types (GPT,MSDOS).  The inconvenience is taking 5-10 seconds to access your BIOS firmware each time you want to change the OS to boot to.  Since you are new to all of this, that might be the easiest thing to do.

> The quick "fix": change UEFI to legacy mode and put the Windows drive  first in boot order to boot Windows, change to UEFI mode and put the  Ubuntu drive first in boot order to boot Ubuntu. Yes, that's  inconvenient. 

>  Step 6: Reboot PC and Grub will load with options to boot into Windows. 

THe quote above is from your earlier post.  Do you see why that will not work?  The step you need before you will see windows in the Grub bootloader is to run the command:  sudo update-grub
Do you understand why this is necessary?  You had your windows drive disconnected and therefore Grub would have no way of knowing that another OS existed!  Duly corrected.

I'm not sure if this has been ansered above but the primary reason for disconnecting the windows drive while installing Ubuntu is that the Ubuntu developers have seen fit to have the installer write the EFI files to the first EFI partition it finds and in most cases, windows is installed and has an EFI partition so Ubuntu will install its EFI files to that partition and not to the EFI partition on the drive on which ubuntu is intalled.

If you want windows and Ubuntu both UEFI, the link below is the official Ubuntu documentation on how to do that.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

