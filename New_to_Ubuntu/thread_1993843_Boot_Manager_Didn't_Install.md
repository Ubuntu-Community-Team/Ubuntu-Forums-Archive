---
title: "Boot Manager Didn't Install"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by JerryC on 2012-06-02
Tried to install 12.04 beside Win7 on my Dell laptop from USB.  At the end of the install I got an error about the boot manager not installing and it gave me some other choices to try (scsia, scsia1, etc.) and I tried all choices; none worked.  My laptop now only bootd to windows as I would expect.  Is there some way to install boot manager after the fact?  Or do I start over and try again?

Full Disclosure.  I had been running 12.04 for a few days with a wubi install but I had uninstalled this from windows.  The dual boot worked with that method.

JC

---

### Post by wilee-nilee on 2012-06-02
> **JerryC said:**
> Tried to install 12.04 beside Win7 on my Dell laptop from USB.  At the end of the install I got an error about the boot manager not installing and it gave me some other choices to try (scsia, scsia1, etc.) and I tried all choices; none worked.  My laptop now only bootd to windows as I would expect.  Is there some way to install boot manager after the fact?  Or do I start over and try again?

Full Disclosure.  I had been running 12.04 for a few days with a wubi install but I had uninstalled this from windows.  The dual boot worked with that method.
JC

Download the bootscript extract it to your desktop, and run the command.  copy and paste the results.txt . Highlight all the text in the reply  and click on the # in the reply panel.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by JerryC on 2012-06-02
> **wilee-nilee said:**
> Download the bootscript extract it to your desktop, and run the command.  copy and paste the results.txt . Highlight all the text in the reply  and click on the # in the reply panel.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

I don't know what "click on the # in the reply panel" means, but here is the output of bootscript.

Thank you for your time.

JC

                 ```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /DELLBIO.BIN /DELLRMK.BIN 
                       /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 108288 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2              81,920    30,801,919    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3    *     30,801,920   507,035,695   476,233,776   7 NTFS / exFAT / HPFS
/dev/sda4         507,039,742   976,771,071   469,731,330   f W95 Extended (LBA)
/dev/sda5         507,039,744   781,824,158   274,784,415   7 NTFS / exFAT / HPFS
/dev/sda6         781,826,048   969,062,399   187,236,352  83 Linux
/dev/sda7         969,064,448   976,771,071     7,706,624  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        1EF86B58F86B2CE9                       ntfs       RECOVERY
/dev/sda3        72F46D86F46D4E03                       ntfs       OS
/dev/sda5        B400D65100D619E6                       ntfs       New Volume
/dev/sda6        ea00a29c-2f4c-4279-a38c-0932699ff15f   ext4       
/dev/sda7        7fbb7a98-47a6-465d-bda0-bec904859b2f   swap       
/dev/sdb1        20BD-11AD                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ea00a29c-2f4c-4279-a38c-0932699ff15f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7fbb7a98-47a6-465d-bda0-bec904859b2f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.2.0-23-generic               3
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  33 00 38 00 2d 00 34 00  33 00 65 00 32 00 2d 00  |3.8.-.4.3.e.2.-.|
00000010  38 00 62 00 66 00 34 00  2d 00 64 00 33 00 33 00  |8.b.f.4.-.d.3.3.|
00000020  32 00 35 00 65 00 36 00  32 00 64 00 31 00 63 00  |2.5.e.6.2.d.1.c.|
00000030  64 00 2e 00 33 00 2e 00  78 00 6d 00 6c 00 00 00  |d...3...x.m.l...|
00000040  d7 43 00 00 00 00 02 00  70 00 5a 00 00 00 00 00  |.C......p.Z.....|
00000050  d6 43 00 00 00 00 02 00  7c ff 60 0f ca 17 cb 01  |.C......|.`.....|
00000060  7c ff 60 0f ca 17 cb 01  7c ff 60 0f ca 17 cb 01  ||.`.....|.`.....|
00000070  7c ff 60 0f ca 17 cb 01  00 10 00 00 00 00 00 00  ||.`.............|
00000080  42 08 00 00 00 00 00 00  20 20 00 00 00 00 00 00  |B.......  ......|
00000090  0c 02 43 00 45 00 45 00  46 00 43 00 43 00 7e 00  |..C.E.E.F.C.C.~.|
000000a0  31 00 2e 00 58 00 4d 00  4c 00 00 00 00 00 00 00  |1...X.M.L.......|
000000b0  d8 43 00 00 00 00 02 00  88 00 78 00 00 00 00 00  |.C........x.....|
000000c0  d6 43 00 00 00 00 02 00  7c ff 60 0f ca 17 cb 01  |.C......|.`.....|
000000d0  7c ff 60 0f ca 17 cb 01  7c ff 60 0f ca 17 cb 01  ||.`.....|.`.....|
000000e0  7c ff 60 0f ca 17 cb 01  00 00 00 00 00 00 00 00  ||.`.............|
000000f0  00 00 00 00 00 00 00 00  20 20 00 00 00 00 00 00  |........  ......|
00000100  1b 01 52 00 65 00 63 00  6f 00 6d 00 6d 00 65 00  |..R.e.c.o.m.m.e.|
00000110  6e 00 64 00 65 00 64 00  5f 00 4d 00 61 00 69 00  |n.d.e.d._.M.a.i.|
00000120  6e 00 74 00 65 00 6e 00  61 00 6e 00 63 00 65 00  |n.t.e.n.a.n.c.e.|
00000130  2e 00 67 00 69 00 66 00  00 00 00 00 00 00 00 00  |..g.i.f.........|
00000140  10 00 00 00 02 00 00 00  a9 6b 54 1e 00 00 00 00  |.........kT.....|
00000150  60 6b 54 1e 00 00 00 00  60 6b 54 1e 00 00 00 00  |`kT.....`kT.....|
00000160  80 00 00 00 00 00 00 00  01 00 00 00 18 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  05 00 06 00 28 00 58 00  |............(.X.|
00000180  80 00 00 00 18 00 01 00  b0 01 00 00 04 00 02 00  |................|
00000190  f5 10 00 00 00 00 00 00  f5 10 0c 00 00 00 00 00  |................|
000001a0  90 00 00 00 58 00 00 00  00 04 18 00 00 00 06 00  |....X...........|
000001b0  38 00 00 00 20 00 00 00  24 00 49 00 33 00 00 fe  |8... ...$.I.3...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 9f e0 60 10 00 fe  |............`...|
000001d0  ff ff 05 fe ff ff a1 e0  60 10 61 07 29 0b 00 00  |........`.a.)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

---

### Post by wilee-nilee on 2012-06-02
You are missing all of the needed grub files in the sda6 partition, except for the fstab, easiest way to fix this would be to use the purge before installing grub in the boot-repair tool advanced section-grub options, here is a link.

You have 3 options with running this tool, from a live cd, or a Ubuntu install, or downloading its cd to boot.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If the tool seems not to be what you want, I could just post a bunch of commands to chroot to the install from a live cd as well.

---

### Post by JerryC on 2012-06-02
I finally got boot-repair installed and working.  I've run it about three times and it appears to do a purge as a standard thing.  Then it get to a window that wants you to run 3 chroot commands.  When I try the second one:

"sudo chroot "/mnt/boot-sav/sda6" dpkg-configure -a"

it gives the error:

"chroot: failed to run command `dpkg-configure': No such file or directory"

I tried "sudo apt-get install dpkg-configure" and that brought the error:

"E: Unable to locate package dpkg-configure"

Any ideas?  Why does linux have to be so complicated?

JC

---

### Post by wilee-nilee on 2012-06-02
> **JerryC said:**
> I finally got boot-repair installed and working.  I've run it about three times and it appears to do a purge as a standard thing.  Then it get to a window that wants you to run 3 chroot commands.  When I try the second one:

"sudo chroot "/mnt/boot-sav/sda6" dpkg-configure -a"

it gives the error:

"chroot: failed to run command `dpkg-configure': No such file or directory"

I tried "sudo apt-get install dpkg-configure" and that brought the error:

"E: Unable to locate package dpkg-configure"

Any ideas?  Why does linux have to be so complicated?

JC

No biggie we can fix this I think, post the bootinfo summary that the boot-repair tool gives you the http address for. Not the original bootscript a new one, the tool makes one automatically.

Just post the http address.

Did you use the quotes ("  ")in the commands or is this just a example?

---

### Post by wilee-nilee on 2012-06-02
I think what happened on the install was the usb/flash you were installing with got set as the internal hard drive=sda, this happens on occasion with usb drives so grub was not installed correctly.

Best way to avoid this is to use custom installs, the something other option at the gui asking where and how you want ubuntu installed in the install gui.

Ubuntu in general is the closest to a plug and play Linux distro, probably.

Granted that, a few basic skills are helpful to avoid this sort of problem.

Had you known that all you had to do was check how the HD and usb were being seen by the install environment, you would of done a custom install.

One command in a terminal will tell you this information.

```
sudo fdisk -lu 
```Don't forget for what ever trouble you are having you are getting free help at the expense of our time. :)

We are also not paid for this as well.

---

### Post by drs305 on 2012-06-02
> **JerryC said:**
> I finally got boot-repair installed and working.  I've run it about three times and it appears to do a purge as a standard thing.  Then it get to a window that wants you to run 3 chroot commands.  When I try the second one:

"sudo chroot "/mnt/boot-sav/sda6" dpkg-configure -a"

I expect you are being asked to run these as two separate commands:
```
sudo chroot /mnt/boot-sav/sda6
```
This will put you in the 'chroot' environment with a root prompt.
Once there, you are asked to run the second command:
```

dpkg-configure -a
```

---

### Post by wilee-nilee on 2012-06-02
> **drs305 said:**
> I expect you are being asked to run these as two separate commands:
```
sudo chroot /mnt/boot-sav/sda6
```This will put you in the 'chroot' environment with a root prompt.
Once there, you are asked to run the second command:
```

dpkg-configure -a
```

That makes makes sense. :)

---

### Post by JerryC on 2012-06-02
I kept messing with this.  I shut down Ubuntu and rebooted on the USB drive.  I re-installed boot-repair and it ran flawlessly.  I re-booted the laptop and it did come up to the grub menu.  I picked Ubuntu and it got up to the purple splash screen with the five dots.  They scanned forever.  After about 5 minutes I gave up and rebooted.  It did boot into windows but it took a while.

What do I need to do to get Ubuntu to boot?
I'm not opposed to deleting back to a windows machine and starting over.  I'm not sure how to handle the partitions however.

JC

---

### Post by drs305 on 2012-06-02
> **JerryC said:**
> I kept messing with this.  I shut down Ubuntu and rebooted on the USB drive.  I re-installed boot-repair and it ran flawlessly.  I re-booted the laptop and it did come up to the grub menu.  I picked Ubuntu and it got up to the purple splash screen with the five dots.  They scanned forever.  After about 5 minutes I gave up and rebooted.  It did boot into windows but it took a while.

What do I need to do to get Ubuntu to boot?
I'm not opposed to deleting back to a windows machine and starting over.  I'm not sure how to handle the partitions however.

JC

Try rebooting and at the Grub menu select the recovery mode option. Select the failsafe video mode and see if that gets you to the desktop. If it does, try installing your video driver. 

If that option doesn't work, try the repair broken packages option to see if there might be something that needs fixing.

---

### Post by JerryC on 2012-06-02
> **drs305 said:**
> Try rebooting and at the Grub menu select the recovery mode option. Select the failsafe video mode and see if that gets you to the desktop. If it does, try installing your video driver. 

If that option doesn't work, try the repair broken packages option to see if there might be something that needs fixing.

Neither of these options worked.  What's next?

I really appreciate the help you two have provided this evening.  We'll get this whipped.  Thank you for your time.

JC

---

### Post by drs305 on 2012-06-02
I know how grub works but don't know all the reasons Ubuntu hangs at the splash screen. So I can offer two things you can try via Grub that will affect the system booting but don't know if they can help. You don't have boot issues any longer, it is something within the Ubuntu system.

1. At the Grub menu, press 'e' to edit the first menuentry. Cursor to the end of the 'linux' line and remove/backspace "quiet splash" and whatever else follows. Add *nomodeset* and then F10 to boot.  This will attempt to boot without loading drivers.

If unsuccessful, try the same thing but instead of 'nomodeset' try 'text'. This kernel option (Ubuntu tailored) should boot to a login prompt. If it does, log on with your name & pw and then try to start the graphics with:```

sudo service lightdm start
```
If it says it's running, try the same with 'restart'.

---

### Post by JerryC on 2012-06-03
Guys, I thought about it last night and then slept on it, and this morning I decided to start over.  I removed grub with Mbrfix and created an install CD from an ISO file.  I also used Gpartedmagic and deleted the USB installation.  The CD installation went very well and I have installed Chromium and got email and gwibber set up so far.

I want to thank you two so much for all the time you have spent on me.  It gives me the hope that I might make Ubuntu work this time.

Next up is to see if I can make Wine work for 2 or 3 programs.

JC

---

