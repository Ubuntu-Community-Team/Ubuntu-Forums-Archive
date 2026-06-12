---
title: "New tobuntu"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by walkerstone on 2011-12-02
Hi All,

I'm new here I know! Hi.. thanks, love you'all!

I've just installed Ubuntu server 10.4 for the first time (I've played with a few liveCD's (fedora & the sort) in the past and decided finally to give a real server install a go!

The installation was a hellish process which took a lot of troubleshooting and I think got me somewhere. At least I now have a working'ish server. Who needs Putty or Webmin right?! :P

My original goal was to set it up as a headless server for my home entertainment etc but after some DIY it now has a head (my living room tv).

I'm having some teething issues though I think - Ubuntu refuses to start up unless I go through the boot options and select the liveUSB to run.

I've read a number of threads during troubleshooting that advise users to use a particular command to output current install status and allow the elite, hopefully such as you, to understand where prats like me went wrong!

If you could help me with this I'd be eternally grateful.

Also please save the hostility to another noob undoubtedly repeating the same question a million before me have asked, I have every intention of becoming an active member of the ubuntu/linux community and spreading the experience I gain and any like you impart along the way. If there's a thread like this that you know exists point me to it - that's enough :) don't waste your energy just telling me it exists.

Thank you.

:popcorn: < isn't that something...

Dan

---

### Post by papibe on 2011-12-02
Hi walkerstone. Welcome to the forums!

I think you have to get into your BIOS, and set a different boot order. Set the USB device as primary.

After that, your machine should always boot from that USB interface.

Hope it helps,
Regards.

---

### Post by walkerstone on 2011-12-02
Hi, thanks for your reply.

The thing is it's supposed to be installed on the local system - I don't want to have to boot from the USB every time - that's not what I went through the headlong process for.

I've just installed the gnome desktop and am not operating (here) from there if that helps anyone?

Any suggestion how I can heck the state of my local install to see if there are any errors?

Also how can I modify my install to boot up into GUI straight away as pose to the terminal?

Many thanks,

Danagram

---

### Post by papibe on 2011-12-02
You could install several GUIs on top of the server edition, but if you feel more comfortable with a GUI, I would advice you to install a Desktop Edition. For example, Ubuntu Desktop, Xubuntu or Lubuntu.

Regards.

---

### Post by walkerstone on 2011-12-02
Thanks,

I hear what your saying but I'd rather understand the problem and master it than be it's slave.

The only reason I've installed a GUI is to quench the thirst of the media display on the TV and other remote devices(ps3)

Primarily I'd like to understand as much of the core command line functionality than anything - if anything I'm fear stricken from zombihood,
I also really want the freedom to expand the system as its needs be and not be stuck to the classic "Sorry - Windows is like your nan and still can't operate the multi-direction function of double glazed windows so please sit back and watch what we do with windows 7"

Maybe that was a little off track but you kow what I mean : Linux = Freedom : Me = Want



Gorillaz:- Clint Eastwood /- SOAD Sugar

---

### Post by walkerstone on 2011-12-02
Sorry - I got a bit distracted there.

What I mean is we're getting distracted from the real gold I'm looking for:

Linux wont work without ubunto kickstart (is this Grubs fault?!) How do I check? If no Grub xio who>!! How do I make it boot cleanly - run Winamp on the crnjob I created which seem to have disapeared, run the putty server which I installed and seems to have disapeared, run the gui and be my bitch?

Gratzie

DanILie


Eminem - Kim

---

### Post by mikewhatever on 2011-12-02
Use the boot_info script and post its output.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I thought you were going to do it in post #1, but there is nothing there.

---

### Post by lechien73 on 2011-12-02
It sounds like the bootloader has been installed to your USB stick, rather than your hard drive.

If you download the boot info script, as mikewhatever says, then we can help you. The details can be found at the link he gave you.

The script produces a file called results.txt. Copy the contents of this and paste them here between CODE tags (the **#** button in the toolbar), which will make it more readable.

Thanks

---

### Post by walkerstone on 2011-12-02
Thank you folks, P1 was asking for this exact directive. 

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 7788 of /dev/sdc1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

Orion-root': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

Orion-swap_1': _________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

Orion-Data': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   488,396,799   488,394,752  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758   156,301,311   155,799,554   5 Extended
/dev/sdb5             501,760   156,301,311   155,799,552  8e Linux LVM


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1029 MB, 1029701632 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2011136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     1,992,059     1,991,997   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2 MB, 2097152 bytes
1 heads, 4 sectors/track, 1024 cylinders, total 4096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/Orion-root c1f9fc27-3ef8-4956-a345-d6312aeb0019   ext4       
/dev/mapper/Orion-swap_1 87d0d72f-4fb8-4778-98f1-63d3ff29872e   swap       
/dev/sda1        679f7e5d-06ad-494f-a358-a76db4847db1   ext3       
/dev/sdb1        30263f71-4c55-41d5-9bbf-7f57ea6b8333   ext2       
/dev/sdb5        rjWCbi-ML4F-5XF2-rG03-H0b5-hXT4-rE8hy6 LVM2_member 
/dev/sdc1        1CDB-3E40                              vfat       PENDRIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
Orion-Data
Orion-root
Orion-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/Orion-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/Data              ext3       (rw)
/dev/sdb1        /boot                    ext2       (rw)


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
insmod lvm
insmod ext2
set root='(Orion-root)'
search --no-floppy --fs-uuid --set c1f9fc27-3ef8-4956-a345-d6312aeb0019
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
search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
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
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    linux    /vmlinuz-2.6.32-36-generic root=/dev/mapper/Orion-root ro noapic nolapic  splash quiet
    initrd    /initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /vmlinuz-2.6.32-36-generic root=/dev/mapper/Orion-root ro single noapic nolapic
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    linux    /vmlinuz-2.6.32-34-generic root=/dev/mapper/Orion-root ro noapic nolapic  splash quiet
    initrd    /initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /vmlinuz-2.6.32-34-generic root=/dev/mapper/Orion-root ro single noapic nolapic
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-34-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 30263f71-4c55-41d5-9bbf-7f57ea6b8333
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.216913223 = 0.232908800    grub/core.img                                  2
   0.212528229 = 0.228200448    grub/grub.cfg                                  1
   0.025666237 = 0.027558912    initrd.img-2.6.32-34-generic                  37
   0.032141685 = 0.034511872    initrd.img-2.6.32-36-generic                  36
   0.008663177 = 0.009302016    vmlinuz-2.6.32-34-generic                     17
   0.015381813 = 0.016516096    vmlinuz-2.6.32-36-generic                     17

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  5d c2 04 00 cc cc cc cc  cc cc cc cc cc cc cc cc  |]...............|
00000010  55 8b ec 51 89 4d fc 8b  45 fc 83 78 08 00 74 35  |U..Q.M..E..x..t5|
00000020  8b 4d fc 8b 51 08 8b 42  10 c1 e8 0f 83 e0 01 85  |.M..Q..B........|
00000030  c0 74 22 8b 4d fc 8b 51  08 8b 45 08 83 e0 03 c1  |.t".M..Q..E.....|
00000040  e0 0d 8b 4a 08 80 e5 9f  0b c8 8b 55 fc 8b 42 08  |...J.......U..B.|
00000050  89 48 08 eb 19 8b 4d 08  83 e1 03 c1 e1 06 8b 55  |.H....M........U|
00000060  fc 8b 42 04 24 3f 0b c1  8b 4d fc 89 41 04 8b e5  |..B.$?...M..A...|
00000070  5d c2 04 00 cc cc cc cc  cc cc cc cc cc cc cc cc  |]...............|
00000080  55 8b ec 51 89 4d fc 8b  45 fc 83 78 7c 00 74 24  |U..Q.M..E..x|.t$|
00000090  8b 4d fc 8b 51 7c 8b 82  bc 00 00 00 c1 e8 0c 83  |.M..Q|..........|
000000a0  e0 01 85 c0 74 0e 8b 4d  fc 8b 51 7c 8b 82 1c 01  |....t..M..Q|....|
000000b0  00 00 eb 06 8b 45 fc 8b  40 20 8b e5 5d c3 cc cc  |.....E..@ ..]...|
000000c0  55 8b ec 51 89 4d fc 8b  45 fc 83 78 7c 00 74 2a  |U..Q.M..E..x|.t*|
000000d0  8b 4d fc 8b 51 7c 8b 82  c0 00 00 00 c1 e8 04 83  |.M..Q|..........|
000000e0  e0 01 85 c0 74 14 8b 4d  fc 8b 51 7c 8b 82 20 01  |....t..M..Q|.. .|
000000f0  00 00 c1 e8 04 83 e0 01  eb 0c 8b 45 fc 8b 40 24  |...........E..@$|
00000100  c1 e8 04 83 e0 01 8b e5  5d c3 cc cc cc cc cc cc  |........].......|
00000110  55 8b ec 51 89 4d fc 8b  45 fc 83 78 7c 00 74 24  |U..Q.M..E..x|.t$|
00000120  8b 4d fc 8b 51 7c 8b 82  c8 00 00 00 83 e0 01 85  |.M..Q|..........|
00000130  c0 74 11 8b 4d fc 8b 51  7c 8b 82 28 01 00 00 83  |.t..M..Q|..(....|
00000140  e0 01 eb 09 8b 45 fc 8b  40 2c 83 e0 01 8b e5 5d  |.....E..@,.....]|
00000150  c3 cc cc cc cc cc cc cc  cc cc cc cc cc cc cc cc  |................|
00000160  55 8b ec 51 89 4d fc 8b  45 fc 83 78 7c 00 74 21  |U..Q.M..E..x|.t!|
00000170  8b 4d fc 8b 51 7c 8b 82  cc 00 00 00 83 e0 01 85  |.M..Q|..........|
00000180  c0 74 0e 8b 4d fc 8b 51  7c 8b 82 2c 01 00 00 eb  |.t..M..Q|..,....|
00000190  06 8b 45 fc 8b 40 30 8b  e5 5d c3 cc cc cc cc cc  |..E..@0..]......|
000001a0  55 8b ec 51 89 4d fc 8b  45 fc 83 78 7c 00 74 24  |U..Q.M..E..x|.t$|
000001b0  8b 4d fc 8b 51 7c 8b 82  f4 00 00 00 83 e0 00 3b  |.M..Q|.........;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 50 49 09 00 00  |...........PI...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on Orion-root'


Unknown BootLoader on Orion-swap_1'


Unknown BootLoader on Orion-Data'



========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/Orion-root': No such file or directory
hexdump: /dev/mapper/Orion-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/Orion-swap_1': No such file or directory
hexdump: /dev/mapper/Orion-swap_1': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/Orion-Data': No such file or directory
hexdump: /dev/mapper/Orion-Data': No such file or directory


```kID cUDI ~ dOWN & oUT

---

### Post by lechien73 on 2011-12-03
Ok, so that confirms that Grub is installed to the MBR of your USB stick - there is no bootloader on the other disks. Also, it looks like you're using LVM with a separate /boot partition.

Could you confirm your BIOS boot order? Does your computer try to boot from the 250Gb drive or the 80Gb drive first?

---

### Post by walkerstone on 2011-12-03
Hi Thanks very much.

How do I go about installing it in the correct place?

Also I thought Windows would have been erased during the Install? Or is that on the 250?

My current boot order is

1. CD/DVD:3S-ATAPI
2. SATA:4M-ST380815AS (This is the only HDD on the menu)
3. USB:Generic USB SD
4. Network

Also I don't suppose any of this relates to my systems inability to mount the additional 250 HDD or even format it?

I guess I'm making a major mistake somewhere because since rebooting a few weeks ago I lost all putty connectivity and Webmin wont fine up.

Sorry to bundle all these problems up!

Thanks so much for the time you've spent!

Dan

---

### Post by walkerstone on 2011-12-03
It might also be worth noting - 

When I set the USB as primary, instead of launching the Grub all I get is

Invalid Partition Table

If I use the Boot Menu during start-up both HDD are listed and launching the one not in the BIOS just results in the flashing _ dropping 3 lines and flashing away for eternity.

---

### Post by lechien73 on 2011-12-03
Hmmm...seems like a strange one alright.

Assuming that the 80Gb is set for booting, the following command will install Grub to the boot sector:

```
sudo grub-install /dev/sdb
```

You could try that and let us know how it goes? :)

---

### Post by walkerstone on 2011-12-03
That's cracked it :D

You the man!

Starts up fine :)

Now on to the next little challenges..

Anyone have any idea why the HDD's are unmanageable?
The 250GB seems completely useless and I'm unable to do anything with it! Format / Partion / Edit Partition / Unmount nadda. I'll get the error details!

No rush though, Google here I come.

Any thoughts?

Thanks again Matt!!

---

### Post by lechien73 on 2011-12-03
You're welcome...glad it's working.

Is the 250Gb visible if you run GParted? If it's not installed, then you can install it by typing:

```
sudo apt-get install gparted
```

---

### Post by Miljet on 2011-12-03
Perhaps the 250Gb is being mounted upon startup. You cannot format or edit partitions on a disk that is in use.

---

