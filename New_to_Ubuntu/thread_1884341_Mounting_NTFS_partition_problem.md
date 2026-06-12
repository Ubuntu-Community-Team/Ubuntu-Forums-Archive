---
title: "Mounting NTFS partition problem"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by BillaSong on 2011-11-21
Hello,

first of all I'm total beginner at linux (I've had it with windows so I give a try with ubuntu 11.10). Now I have one problem. When I had windows, I had two partitions (system and storage), so I've formatted system partition with ubuntu and installed it on that 100Gb partition. But everything important I have is on storage disk which is NTFS (windows 7) partition. And I have troubles with seeing that partition.

So I've tried few things by searching forums (installing something 3G and disk utility, but there i can not see my partition). In terminal is seen, there is copy from terminal:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968497151   484247552   83  Linux
/dev/sda2       968499198   976771071     4135937    5  Extended
/dev/sda5       968499200   976771071     4135936   82  Linux swap / Solaris


So my NTFS partition is /dev/sda2... I've tried changing fstab, but it always says that I don't have administration permissions (but I am admin =/). So any help please, cuz' I have been searching forums for two whole days and nothing worked =/.

My fstab content if it helps:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4aaf5a15-6a45-49ae-a9d2-6f028d554dc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a851edc-7840-4453-80e8-0e531bff9dda none            swap    sw              0       0

P.S. Sorry for my bad english =).

---

### Post by buntudawg on 2011-11-21
Hi and welcome.

What is the output of:

```
sudo blkid
```

---

### Post by BillaSong on 2011-11-21
Output code is:

/dev/sda1: UUID="4aaf5a15-6a45-49ae-a9d2-6f028d554dc1" TYPE="ext4" 
/dev/sda5: UUID="0a851edc-7840-4453-80e8-0e531bff9dda" TYPE="swap"

I don't know why, but there is no /dev/sda2, which should be my NTFS partition =/

---

### Post by buntudawg on 2011-11-21
Hmmm.

I don't know where it is either.

To me it appears there isn't an ntfs drive or partition on your system, but someone else may be able to help.

At least this will bump you.

---

### Post by raja.genupula on 2011-11-21
Look at my signature you will found something like bootinfoscript 
run it and paste the out of that here.

---

### Post by fantab on 2011-11-21
> **BillaSong said:**
> Output code is:

/dev/sda1: UUID="4aaf5a15-6a45-49ae-a9d2-6f028d554dc1" TYPE="ext4" 
/dev/sda5: UUID="0a851edc-7840-4453-80e8-0e531bff9dda" TYPE="swap"

I don't know why, but there is no /dev/sda2, which should be my NTFS partition =/

I am afraid but I think you don't have NTFS Partition, according to the above output.
The Extended Partition you created is /dev/sda2 the subsequent logical partitions will always be numbered 5,6,7 and so on. 

Your Primary Partition is /dev/sda1
Your Extended Partition is /dev/sda2
Your SWAP Partition is /dev/sda5


Create another thread asking Help to recover Lost NTFS Partition.

Good Luck.

---

### Post by BillaSong on 2011-11-21
> **raja.genupula said:**
> Look at my signature you will found something like bootinfoscript 
run it and paste the out of that here.

Here are results from bootinfoscript:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   968,497,151   968,495,104  83 Linux
/dev/sda2         968,499,198   976,771,071     8,271,874   5 Extended
/dev/sda5         968,499,200   976,771,071     8,271,872  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4aaf5a15-6a45-49ae-a9d2-6f028d554dc1   ext4       
/dev/sda5        0a851edc-7840-4453-80e8-0e531bff9dda   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4aaf5a15-6a45-49ae-a9d2-6f028d554dc1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4aaf5a15-6a45-49ae-a9d2-6f028d554dc1 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4aaf5a15-6a45-49ae-a9d2-6f028d554dc1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4aaf5a15-6a45-49ae-a9d2-6f028d554dc1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a851edc-7840-4453-80e8-0e531bff9dda none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  7b 4e b8 8a 2e 01 57 85  f9 82 0b 63 b4 cf 0b 7b  |{N....W....c...{|
00000010  e1 26 1b f8 58 22 24 c2  f2 11 0b 7e fa 7b af 6b  |.&..X"$....~.{.k|
00000020  26 3b 49 fc 6b 34 d1 b6  b9 c5 b6 6f 92 7d 42 5d  |&;I.k4.....o.}B]|
00000030  d5 9b cf 3e 71 f3 50 7d  ce 09 f9 c3 a7 d3 4e 13  |...>q.P}......N.|
00000040  3d 33 bb d4 01 f6 14 50  f2 59 39 11 aa 62 85 75  |=3.....P.Y9..b.u|
00000050  e3 38 90 a5 6c 1c 66 93  3f 18 08 b5 15 3e 2f a9  |.8..l.f.?....>/.|
00000060  ab af d9 fd ba d8 a3 f0  bc bc 8c 86 d6 65 15 88  |.............e..|
00000070  69 71 a2 d9 d1 73 92 5a  2c 81 48 0d ac d2 f5 22  |iq...s.Z,.H...."|
00000080  08 fb 66 29 db 4b a9 10  29 26 d5 d6 93 bb b0 3b  |..f).K..)&.....;|
00000090  3a b2 48 74 9d 94 42 28  f4 eb e9 42 40 c3 e5 de  |:.Ht..B(...B@...|
000000a0  81 5b a7 0c 1c 39 71 d4  af 66 4e 7d 53 4e 76 c9  |.[...9q..fN}SNv.|
000000b0  7c e0 6a 8b 3e 83 b1 9b  00 aa 97 20 f7 2a 3b 45  ||.j.>...... .*;E|
000000c0  64 84 54 0d 79 a9 91 86  02 32 cf dd 3b 4c 50 27  |d.T.y....2..;LP'|
000000d0  52 bb c5 d5 1b 5f 39 54  6e 5c 4e 60 f4 c7 cc 06  |R...._9Tn\N`....|
000000e0  b7 bd 0f 0a 6c 70 97 1f  f4 d8 1b e3 6a 95 be d3  |....lp......j...|
000000f0  6d 60 0e ad 95 a2 40 7d  dd 97 99 3f 70 60 b4 9c  |m`....@}...?p`..|
00000100  ce 55 af 33 51 cc c7 35  d8 a8 98 02 b0 cc 87 b3  |.U.3Q..5........|
00000110  ef 00 28 39 82 22 80 b1  fa e1 75 60 c5 6e cb 40  |..(9."....u`.n.@|
00000120  74 d0 20 88 13 1d 90 aa  e8 49 10 d1 93 96 39 6d  |t. ......I....9m|
00000130  4a 84 32 90 99 63 8e 60  29 ba 59 57 e8 ba c3 ef  |J.2..c.`).YW....|
00000140  80 bf 3a 77 8c 3d 4d f2  ee 03 91 db 76 3d a8 c5  |..:w.=M.....v=..|
00000150  87 fd 37 17 1c 41 ed 2d  54 c7 38 aa 0a e5 4c 0e  |..7..A.-T.8...L.|
00000160  86 89 5e 65 a4 43 34 39  3a c9 bf de 4b 37 57 0f  |..^e.C49:...K7W.|
00000170  3f ba 40 33 13 32 11 8b  31 2a d4 9f 6f e2 97 5e  |?.@3.2..1*..o..^|
00000180  98 98 1f 65 8e d2 e4 33  78 95 47 48 f5 66 43 90  |...e...3x.GH.fC.|
00000190  cb bd 66 b2 df a6 f6 5f  4a 05 ce e3 00 d8 a5 db  |..f...._J.......|
000001a0  29 dc 8b 8c 0d e3 8b 57  36 da dc dc bf 48 23 02  |)......W6....H#.|
000001b0  23 eb cd 1e a3 d4 03 fb  48 28 0b 92 ee 12 00 fe  |#.......H(......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 38 7e 00 00 00  |...........8~...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by BillaSong on 2011-11-21
But there is my NTFS partition as "/dev/sda2         968,499,198   976,771,071     8,271,874   5 Extended"... If there is no other way, I may try with hierens boot cd, recover my files and then format that partition with ubuntu?

---

### Post by coffeecat on 2011-11-21
> **fantab said:**
> 
An Extended Partition always takes the partition number 4 for instance /dev/sda4 or /dev/sdb4 and the subsequent logical partitions will numbered 5,6,7 and so on.

Point of information: an extended partition can be assigned the number 1,2,3 or 4 - usually the next number up from the highest-numbered primary partition. This is because an extended partition is simply a type of primary partition whose sole purpose is to act as a container for one or more logical partitions, numbered, as you say, 5 or upwards. The OP's extended partition is sda2. 

> **fantab said:**
> Create another thread asking Help to recover Lost NTFS Partition.

@BillaSong, you can do that if you prefer, linking back to this thread, or you can continue on in this thread, and I can rename this thread if you want. In the meantime, do not use that system. The more you use it the more likely you are to over-write your data.

Do you have any backups?

---

### Post by raja.genupula on 2011-11-21
Hey ....open disk utility . That will display entire Hard disk structure . by that you can have complete Idea   about your hard disk and partitions .

---

### Post by mikewhatever on 2011-11-21
You don't seem to have any NTFS partitions, and running the bootinfo script is not gonna change that. Hope you had a backup.

---

### Post by BillaSong on 2011-11-21
> **raja.genupula said:**
> Hey ....open disk utility . That will display entire Hard disk structure . by that you can have complete Idea   about your hard disk and partitions .

Ok I've checked that, but if you see on screen shot it sais that ubuntu gave all partitions together, cuz' my disk has 500Gb and there says that ext4 has 496Gb... Probably i have to find a way to recover my ntfs partition...

[[IMG]http://www.shrani.si/t/45/6s/otaKMSs/screenshot-at-2011-11-21.jpg[/IMG]]("http://www.shrani.si/?45/6s/otaKMSs/screenshot-at-2011-11-21.png")

---

### Post by coffeecat on 2011-11-21
> **BillaSong said:**
> Ok I've checked that, but if you see on screen shot it sais that ubuntu gave all partitions together, cuz' my disk has 500Gb and there says that ext4 has 496Gb... Probably i have to find a way to recover my ntfs partition...

Indeed you do, but neither disk utility nor the boot script is telling us anything relevant than we could gather from the information you posted in post #1 and #3. I hate to have to repeat myself, but... 

> **coffeecat said:**
> In the meantime, **do not use that system**. The more you use it the more likely you are to over-write your data.

Do you have any backups?

Testdisk *might* recover your ntfs partitions, but the chances are that the ext4 partition has already overwritten some of the two ntfs filesystems. Files in ext3/4 filesystems are spread throughout the partition.

You might find this helpful:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by fantab on 2011-11-21
> **fantab said:**
> I am afraid but I think you don't have NTFS Partition, according to the above output.
An Extended Partition always takes the partition number 4 for instance /dev/sda4 or /dev/sdb4 and the subsequent logical partitions will numbered 5,6,7 and so on.

Your Primary Partition is /dev/sda1
Your Extended Partition is /dev/sda4
Your SWAP Partition is /dev/sda5

Create another thread asking Help to recover Lost NTFS Partition.

Good Luck.

> **coffeecat said:**
> Point of information: **an extended partition can be assigned the number 1,2,3 or 4 - usually the next number up from the highest-numbered primary partition.** This is because an extended partition is simply a type of primary partition whose sole purpose is to act as a container for one or more logical partitions, numbered, as you say, 5 or upwards. The OP's extended partition is sda2. 


Thank you coffeecat for the correction....

---

### Post by Mark Phelps on 2011-11-21
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by BillaSong on 2011-11-22
Hey guys,

I'm sorry for late reply. I've used hieren's boot cd and found my ntfs partition. So I was coping my files for a day =) but a have recovered my files... Thank you all for helping me with this problem... I will now format whole disk and make 2 seperate partitions (system and storage). I have only one more question, can I make 2 partitions and what do you recommend to choose (tipe and other) while doing that, so I can accomplishe that?

Thank you again

---

### Post by fantab on 2011-11-22
> **BillaSong said:**
> Hey guys,

I'm sorry for late reply. I've used hieren's boot cd and found my ntfs partition. So I was coping my files for a day =) but a have recovered my files... Thank you all for helping me with this problem... I will now format whole disk and make 2 seperate partitions (system and storage). I have only one more question, can I make 2 partitions and what do you recommend to choose (tipe and other) while doing that, so I can accomplishe that?

Thank you again

I am glad that you were able to recover your lost partition. 

I am assuming that you want to dual boot ubuntu with Windows. 

Use [**Gparted LiveCD**]("http://gparted.sourceforge.net/livecd.php") for Hard Disk management. It is very good tool to have separately on a CD. Also this method of Partitioning from boot Cd is recommended

As for partitioning I will tell you what I have done on one of my desktop with 500gb HDD.
I used the above recommended tool


[LIST]
[*]**/dev/sda1** 20-25 GB Primary NTFS Windows_C
[*]**/dev/sda2** 50 GB Primary NTFS Windows_D
[*]**/dev/sda3** 15-20 GB Primary EXT4 Ubuntu "/"
[*]**/dev/sda4 **Extended Partition
[*]**/dev/sda5** All the remaining GB Logical EXT4 My_DATA (I personally don't use "/Home" -you can make this /home)
[*]**/dev/sda6** 4 GB SWAP Logical
[/LIST]
This is just to give you an idea. Take a note of the fact that Linux will read and write to NTFS Partitions but Windows cannot read or write Linux Partitions. So Plan in advance.

Install Windows First.

When installing Ubuntu use "something else" option to allocate space. This will give you control to select and assign mountpoints to partitions of your choice.

Remember: Make sure to Install GRUB to /dev/sda

---

### Post by BillaSong on 2011-11-22
Oh my bad, I forgot to say that I don't want dual boot with windows (I've had it with it =), just clean install with linux ubuntu 11.10. So i have 500Gb disk (in laptop), and I want 100Gb for system and other cca. 366Gb for storage. And I see that you preffere 4Gb for swap (is that enough or should i give it more?).

Spec. for my laptop (if that help) are:

Lenovo G770
Intel i5 2410M
4Gb ddr3 1333Mhz
Radeon HD6650m

And what is GRUB and how do I install it (if I need that since it is not dualboot).

Oh yes and it is x64 =)

---

### Post by BillaSong on 2011-11-22
Hey,

alright, I've done it =)... @fantab I've made partitions as you said (except ntfs) and it works well =)... Thank you all for fast responds and helping me with my partition...

---

