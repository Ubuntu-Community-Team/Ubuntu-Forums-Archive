---
title: "Problem booting with windows 7 laptop but works on windows xp"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by benbrockn on 2011-11-19
Hi, So I'm still new to Ubuntu so bare with me please.

I bought a new Seagate goflex 1TB external harddrive

Made 4 partitions:

1) /boot (100mb primary ext4)
2) swap (6gb logical)
3) / (10gb primary ext4)
4) NTFS (~970gb primary)

Installed Ubuntu 10.04.3 LTS

Loads up fine on my old HP tablet tc4200 (Windows XP), takes about 12 secs after selecting from Grub menu)

Will not load on my new HP Pavilion dv6 (Windows 7)

After choosing Ubuntu from GRUB it loads and about 2 seconds in it stops at

**2.82...  usb 3-5 configuration #1 chosen from 1 choice**


and then it gives the error:

"[B]Gave up waiting for root device. Common problems...etc etc.. 
ALERT! /dev/disk/by-uuid/xxxx not found dropping to a shell![/B]"

I tried **rootdelay=50**, didn't work on win 7
I tried **rootdelay=130**, didn't work on win 7 (both still worked on xp)

When you edit the boot via GRUB this is what it has:

[B]recordfail
insmod ext2
set root='(hd1,1)'
search --nofloppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a03\fd1
linux /vmlinuz-2.6.32-33-generic root=UUID=xxxx ro   rootdelay=130
initrd /initrd.img-2.6.32-33-generic
[/B]
I have no idea what any of this means . I'm thinking that maybe if I **set root=** something else it might help?

I'm confused and frustrated.

---

### Post by oldfred on 2011-11-19
Can you boot a Ubuntu liveCD or liveUSB from the Windows 7 computer? If so run this. If you can boot on the XP computer, the boot stanza should be correct. Script may not show anything as it may be a BIOS setting as that now is the only real difference.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk
Is able to search LVM partitions if the LVM2 package is install

---

### Post by benbrockn on 2011-11-19
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /etc/fstab

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   123,282,809   122,873,210   7 NTFS / exFAT / HPFS
/dev/sda3       1,214,099,456 1,250,050,047    35,950,592   7 NTFS / exFAT / HPFS
/dev/sda4         123,282,810 1,214,096,309 1,090,813,500   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       194,559       192,512  83 Linux
/dev/sdb2             196,606    11,913,215    11,716,610   5 Extended
/dev/sdb5             196,608    11,913,215    11,716,608  82 Linux swap / Solaris
/dev/sdb3          11,913,216    31,444,991    19,531,776  83 Linux
/dev/sdb4          31,455,270 1,953,520,064 1,922,064,795   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        542E95362E9511DA                       ntfs       SYSTEM
/dev/sda2        2614651E1464F26B                       ntfs       
/dev/sda3        5C2442F72442D424                       ntfs       RECOVERY
/dev/sda4        6541B4F25CD7E87F                       ntfs       DATA_HP
/dev/sdb1        ec83558b-1310-4f48-aa6e-c26f75a0efd1   ext4       
/dev/sdb3        5781f533-cd94-499d-8557-8aa0230ece9c   ext4       
/dev/sdb4        528BC586314CFD90                       ntfs       Data_Seagate
/dev/sdb5        24500feb-f854-4f6b-8a4e-7195db6854a3   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ec83558b-1310-4f48-aa6e-c26f75a0efd1 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/5781f533-cd94-499d-8557-8aa0230ece9c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb4        /media/Data_Seagate      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 5781f533-cd94-499d-8557-8aa0230ece9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a0efd1
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a0efd1
    linux    /vmlinuz-2.6.32-33-generic root=UUID=5781f533-cd94-499d-8557-8aa0230ece9c ro   rootdelay=130
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a0efd1
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=5781f533-cd94-499d-8557-8aa0230ece9c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a0efd1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ec83558b-1310-4f48-aa6e-c26f75a0efd1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set B2349031348FF69F
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.022761345 = 0.024439808    grub/core.img                                  1
   0.022954941 = 0.024647680    grub/grub.cfg                                  1
   0.047731400 = 0.051251200    initrd.img-2.6.32-33-generic                   1
   0.016456604 = 0.017670144    vmlinuz-2.6.32-33-generic                      1

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=5781f533-cd94-499d-8557-8aa0230ece9c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=ec83558b-1310-4f48-aa6e-c26f75a0efd1 /boot           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=24500feb-f854-4f6b-8a4e-7195db6854a3 none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  33 a9 3c 2f b9 26 97 ec  8b 9f 96 f3 40 6e cf 03  |3.</.&......@n..|
00000010  2d 01 ad 2e d5 17 ae 19  e7 38 6e ef 26 d5 67 1f  |-........8n.&.g.|
00000020  ca 79 04 b7 8f 86 ce 84  2e 85 6e 82 7e 0f bd 07  |.y........n.~...|
00000030  7d 0d 0d ea 42 1a 0c cd  0d ad 0c ad 0b 6d 0d ed  |}...B........m..|
00000040  21 d5 b7 fd c1 9c c7 70  fb 58 e8 1c e8 2a e8 b7  |!......p.X...*..|
00000050  d0 d3 d0 9f a0 f7 a1 6f  a1 49 ba 92 66 83 96 82  |.......o.I..f...|
00000060  d6 86 c6 42 87 40 27 43  97 41 77 40 2f 42 7f 87  |...B.@'C.Aw@/B..|
00000070  26 eb 46 9a 1b 5a 11 da  12 3a 08 3a 0b ba 0d 7a  |&.F..Z...:.:...z|
00000080  11 fa 12 9a b6 3b 69 71  68 23 e8 00 e8 28 e8 6c  |.....;iqh#...(.l|
00000090  e8 7a e8 01 e8 65 e8 33  a8 a7 07 69 06 68 01 68  |.z...e.3...i.h.h|
000000a0  14 b4 01 b4 33 74 18 74  3a 74 2d f4 10 f4 02 f4  |....3t.t:t-.....|
000000b0  57 e8 3b e8 47 3d 49 73  42 23 a0 0d a1 3d a1 43  |W.;.G=IsB#...=.C|
000000c0  a1 5f 41 57 43 b7 43 4f  42 6f 42 1f 41 f9 a3 2a  |._AWC.COBoB.A..*|
000000d0  b4 1d 68 76 68 61 68 15  68 5d a9 be 7a d3 a2 97  |..hvhah.h]..z...|
000000e0  98 8f d4 8f eb 00 ed 0f  1d 0e 9d 02 5d 04 dd 08  |............]...|
000000f0  3d 0a bd 0a 7d 00 7d 0d  4d da 9b f4 63 68 1e 68  |=...}.}.M...ch.h|
00000100  29 68 75 68 6b 68 0f e8  50 e8 64 e8 7c e8 46 e8  |)huhkh..P.d.|.F.|
00000110  61 e8 0d e8 3b a8 a3 0f  b6 07 2d 05 6d 06 1d 02  |a...;.....-.m...|
00000120  4d 80 ce 80 ae 81 ee 87  fe 08 7d 0c d5 fa 92 a6  |M.........}.....|
00000130  86 e6 82 16 81 46 41 eb  42 5b 43 87 40 27 40 97  |.....FA.B[C.@'@.|
00000140  42 77 40 4f 43 ef 42 9f  42 f5 7e a4 c9 a1 c1 d0  |Bw@OC.B.B.~.....|
00000150  02 d0 28 68 6d 68 07 e8  00 e8 18 e8 7c e8 66 e8  |..(hmh......|.f.|
00000160  21 e8 65 e8 63 a8 fa 09  69 0a 68 18 b4 04 b4 26  |!.e.c...i.h....&|
00000170  b4 25 b4 2b f4 73 e8 1c  e8 d7 d0 13 d0 1b d0 b7  |.%.+.s..........|
00000180  d0 94 fd 49 b3 43 8b 40  ab 42 5b 42 fb 42 c7 41  |...I.C.@.B[B.B.A|
00000190  97 43 f7 42 2f 42 1f 40  8d 01 a4 99 a1 c5 a1 35  |.C.B/B.@.......5|
000001a0  a0 2d a0 7d a1 09 d0 b9  d0 8d d0 63 d0 9f a0 cf  |.-.}.......c....|
000001b0  a1 89 3f 45 bd 82 e6 81  46 40 63 a0 ed a1 00 3c  |..?E....F@c....<|
000001c0  31 0c 82 8f aa e5 02 00  00 00 00 c8 b2 00 00 00  |1...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200





```

Hey Thanks for helping, sorry my post is a little slow.

---

### Post by oldfred on 2011-11-19
Script is not showing any issue, as I would expect if it does work on the XP system.

Sometimes it is a BIOS setting or you need a parameter on the linux line in grub to override something different about the system.

I have saved comments where users fixed issues, something may apply.
Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Or:
You may need a parameter:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by benbrockn on 2011-11-19
There isn't really any bios options to change, and as for updating, I'm pretty sure it doesn't need it since I just ordered late october.

I went down the list and the bios settings were either already applied or weren't applicable because of the lack of bios options.

As for setting the parameters for modules, I looked in my file system under 

**/sys** and there were no files or folders. On my Live CD there were though (which is odd because I installed Ubuntu from the Live CD to the hdd.)

Hmm... I'm not sure what to do next

---

### Post by benbrockn on 2011-11-19
If I re-partitioned my drive so that /boot and / were on the same partition would that work and skip all of this bios-not-loading junk?

Remake my partitions as:

1) / (10gb primary ext4)
2) swap (6gb logical )
3) NTFS (~980gb primary)

???

---

### Post by lolpenguin on 2011-11-20
Empty /sys/ folder? That is strange.

---

### Post by benbrockn on 2011-11-20
> **benbrockn said:**
> If I re-partitioned my drive so that /boot and / were on the same partition would that work and skip all of this bios-not-loading junk?

Remake my partitions as:

1) / (10gb primary ext4)
2) swap (6gb logical )
3) NTFS (~980gb primary)

???


I was thinking either:

1) Copying the contents of **/sys** from the Live CD to the hdd or 

2) Just re-partitioning like this scheme and moving the contents of **/boot** to the **/** directory and when BIOS loads it should load grub automatically. 

Will either of these ideas work?

---

### Post by oldfred on 2011-11-20
I usually recommend that /boot be inside the / (root) for most desktops. But it really does not make any difference. It is just where grub & the kernel files exist on the drive.

Have you tried the parameters on the Linux line in grub? Several posters have had to use timeout and/or acpi or other settings to work with newer computers.

---

### Post by benbrockn on 2011-11-20
ok, so I remade my partitions as:

1) / (10gb primary ext4)
2) swap (6gb logical )
3) NTFS (~980gb primary)

Doesn't run on xp or win7 now, so I have to re-repartition it back to:

1) /boot (100mb primary ext4)
2) swap (6gb logical)
3) / (10gb primary ext4)
4) NTFS (~970gb primary)

So now we know, it's the bios on the win 7, it has nothing to do with not being able to read multiple partitions so it's some sort variable that is restricting the bios from reading root.

As soon as I get back I can try different parameters, and hope that works.

---

### Post by lolpenguin on 2011-11-22
Isn't the kernel in /sys?
It is the compressed kernel image (vmlinuz) that is stored in /boot for use by the bootloader, which then, it is uncompressed and the real kernel booted?
At least that is what I learned from Arch Linux.

---

### Post by benbrockn on 2012-11-21
I do not have this setup any longer since I deployed and forgot about it, but later I will probably try it again and run into the same problem. I'll update this when I get to try it again.

---

