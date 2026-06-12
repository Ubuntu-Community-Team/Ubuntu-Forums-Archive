---
title: "windows asking for disk"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by sirvinniei on 2011-09-26
hey,

yesterday i downloaded and installed ubuntu next to Windows 7 and everything seemed  to work untill i tried to start up windows 7
when i try to boot via windows 7 its says it cant be run due to  a recent change to hardware of software and it says i have to insert my windows 7  CD which i dont have because i bought the pc with windows already installed or contact the ditruber of  the pc
I probably  think this is because of the partitions because the first time i tried to install ubuntu there wasnt an install next to windows 7 option  and i selected  others instead then i got to the partition thingy window and got really confused so i first made new partitions and then shut down my PC
can someone plz explain ways to fix this in language even a beginner to ubuntu can understand.

---

### Post by Gone fishing on 2011-09-26
You resized your Windows partition using gparted? this can be the course of this problem - if you can resize in Windows it can be better. 

However, this should tell you how to fix the problem [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by CarlosFerreira on 2011-09-26
My computer had the same issue (partitioned using the Windows 7 partition tool) and I got so fed up of not getting Win7 to work, I ended up clearing the whole thing are running only ubuntu.

---

### Post by sirvinniei on 2011-09-26
> **Gone fishing said:**
> You resized your Windows partition using gparted? this can be the course of this problem - if you can resize in Windows it can be better. 

However, this should tell you how to fix the problem [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
the problem is: I  don  have a windows 7  Cd
> **CarlosFerreira said:**
> My computer had the same issue  (partitioned using the Windows 7 partition tool) and I got so fed up of  not getting Win7 to work, I ended up clearing the whole thing are  running only ubuntu. I love to that, but I still have all my music files on my windows account

---

### Post by Gone fishing on 2011-09-26
If you don't have a Windows cd then you could borrow one or I think you can download one from Neosmart 

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)

---

### Post by sirvinniei on 2011-09-27
> **Gone fishing said:**
> If you don't have a Windows cd then you could borrow one or I think you can download one from Neosmart 

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)
thanks dude

how big do you need to resize it?

---

### Post by oldfred on 2011-09-27
Neosmart used to be a free download, now it is $10.

If you know someone with the same Windows 7 (64 or 32bit):

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Post this to see your configuration from a liveCD. Windows often use all four primary partitions, so we need to see what you changed.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by sirvinniei on 2011-09-27
> **oldfred said:**
> Neosmart used to be a free download, now it is $10.
 
If you know someone with the same Windows 7 (64 or 32bit):
 
Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
 
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
 
Post this to see your configuration from a liveCD. Windows often use all four primary partitions, so we need to see what you changed.
 
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
 ok, so I have the windows 7 repair cd now

but I don't get what you mean by viewing your configuration
as I said I'm totally new to ubuntu an don't really know much about partitions either
please don't get mad for asking this but can you please speak in very clear langueage and steps so I know exactly what to do

---

### Post by oldfred on 2011-09-27
The boot script is a file that runs a lot of command and outputs a report of all your system configuration. It saves us from having to ask you to run many different commands to see what you have where. 

The link I posted has instructions, read the instructions, and click thru to download script. It is now a zip file, which you have to unzip to get the boot_info_script.sh file to run.

my system downloads to the Downloads folder. If in Nautilus file browser you double click on it, it should give you the option to extract. You then have the script in Downloads.

Open a terminal:

fred@fred-MavericDT:~$ cd Downloads
fred@fred-MavericDT:~/Downloads$ sudo bash boot_info_script.sh
[sudo] password for fred: 

It shows it running, mine has a lot of partitions.

and it tells you where the file is, yours will be different than mine.

Finished. The results are in the file "RESULTS.txt"
located in "/mnt/data/Downloads/".

Back in Nautilus open it and copy and paste in code tags here.

---

### Post by CarlosFerreira on 2011-09-28
> **sirvinniei said:**
> the problem is: I  don  have a windows 7  Cd
 I love to that, but I still have all my music files on my windows account

Mmmm, I wonder if you can run a Linux LiveCD session and access the partition with Windows in. I think I managed that. Proceed to back-up all your music, at least.

---

### Post by sirvinniei on 2011-09-28
here it is
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: onbekende bestandssysteemsoort ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   973,995,852   973,993,805  83 Linux
/dev/sda2         973,996,030 1,953,523,711   979,527,682   5 Extended
/dev/sda5         973,996,032 1,947,762,687   973,766,656  83 Linux
/dev/sda6       1,947,764,736 1,953,523,711     5,758,976  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Schijf /dev/sdb: 3965 MB, 3965190144 bytes
49 koppen, 48 sectoren/spoor, 3292 cilinders, totaal 7744512 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192     7,744,511     7,736,320   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 54846e1d-9fa3-4c48-ae85-ae7d8e47736d   swap       
/dev/sda1        4EA0A14EA0A13CF9                       ntfs       Door systeem gereserveerd
/dev/sda5        59a10da9-6145-462d-8276-cf6b716896ec   ext4       
/dev/sdb1        3634-3033                              vfat       šF5º¬Ô'5ó

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/                 vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
set locale_dir=($root)/boot/grub/locale
set lang=nl_NL
insmod gettext
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
menuentry 'Ubuntu, met Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-11-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, met Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-8-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4EA0A14EA0A13CF9
    chainloader +1
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=59a10da9-6145-462d-8276-cf6b716896ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=62304e79-c77f-4e25-94b0-cfe2aff63e19 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 714.571578979 = 767.265390592  boot/grub/core.img                             1
 476.591037750 = 511.735730176  boot/grub/grub.cfg                             1
 468.414062500 = 502.955769856  boot/initrd.img-2.6.38-11-generic              2
 468.329475403 = 502.864945152  boot/initrd.img-2.6.38-8-generic               1
 467.695621490 = 502.184349696  boot/vmlinuz-2.6.38-11-generic                 1
 714.569805145 = 767.263485952  boot/vmlinuz-2.6.38-8-generic                  1
 468.414062500 = 502.955769856  initrd.img                                     2
 468.329475403 = 502.864945152  initrd.img.old                                 1
 467.695621490 = 502.184349696  vmlinuz                                        1
 714.569805145 = 767.263485952  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by oldfred on 2011-09-28
Please use code tags. I changed it.:)

It looks like you Windows c: is missing. The sda1 is just the boot/reocvery which in Windows is a hidden partition. It looks like you converted sda2 the main Windows install into your extended partition.

It shows also shows partition table issues. sda1 is NTFS but partition table says it is Linux type 83, should be type 07. And I am not sure what the error is but sda6 has an error.

---

### Post by sirvinniei on 2011-09-28
> **oldfred said:**
> Please use code tags. I changed it.:)

It looks like you Windows c: is missing. The sda1 is just the boot/reocvery which in Windows is a hidden partition. It looks like you converted sda2 the main Windows install into your extended partition.

It shows also shows partition table issues. sda1 is NTFS but partition table says it is Linux type 83, should be type 07. And I am not sure what the error is but sda6 has an error.
sorry, i usaually use spoler tags in forums but couldnt find them.
So what do you think I can do to fix this (if it&#347; fixable at  all)
ow and sda 6 says unknown file type  in dutch

---

### Post by oldfred on 2011-09-28
Code tags are the # symbol in the edit panel.

I do not know why sda6 cannot mount. My swap partition just show as swap with no errors. That could be fixed, but I think the Windows issues may not be easily fixable, if you overwrote the main c: windows partition and it was sda2 which would be the normal case. But if sda1 is the full Windows install the script did not show winload.exe. Is it in sda1? If so you may just be able to change partition table entry from 83 to 07 and see if that solves it with disk utility.

Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

The standard Windows 7 has bootmgr & BCD in a boot/recovery and the winload.exe in the main install. But you may have all in one large partition. Script has missed showing winload in some cases, but I think it is because of other issues in the Windows partition, which often are difficult to repair.

---

### Post by sirvinniei on 2011-09-28
> **oldfred said:**
> Code tags are the # symbol in the edit panel.

I do not know why sda6 cannot mount. My swap partition just show as swap with no errors. That could be fixed, but I think the Windows issues may not be easily fixable, if you overwrote the main c: windows partition and it was sda2 which would be the normal case. But if sda1 is the full Windows install the script did not show winload.exe. Is it in sda1? If so you may just be able to change partition table entry from 83 to 07 and see if that solves it with disk utility.

Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

The standard Windows 7 has bootmgr & BCD in a boot/recovery and the winload.exe in the main install. But you may have all in one large partition. Script has missed showing winload in some cases, but I think it is because of other issues in the Windows partition, which often are difficult to repair.
so your basicly saying my windows is  messed up?
If so, will I still be able to retrieve my  files?
What&#347; best to do now? Buy a windows 7 disc and reinstall?

---

### Post by oldfred on 2011-09-28
Is sda1 a full install or just a boot/recovery partition. Normally windows boot partitions are small only 100MB, yours looks larger, but does not show the winload.exe.

Can you use Ubuntu and mount and browse your sda1 windows install? Does it have the system files and more importantly your personal files. If so I would immediately back them up.

You could try chkdsk from a Windows CD on sda1 to see if that makes some repairs.

---

### Post by sirvinniei on 2011-09-28
> **oldfred said:**
> Is sda1 a full install or just a boot/recovery partition. Normally windows boot partitions are small only 100MB, yours looks larger, but does not show the winload.exe.

Can you use Ubuntu and mount and browse your sda1 windows install? Does it have the system files and more importantly your personal files. If so I would immediately back them up.

You could try chkdsk from a Windows CD on sda1 to see if that makes some repairs.
again,
please don't talk too technical
my technical knowledge is limited
I did try to run the recovery Cd once and try startup (or startup reapair don't know what it&#347; called in english) but that didn't work
and can you explain how to mount the sda1?
and check if it&#347; my personal files or just a boot partition?

---

### Post by oldfred on 2011-09-28
From the liveCD open up the file browser Nautilus or click on places. In the left panel should be your windows, but it may just be called 40GB partition or whatever size it is. Then it is like window explorer as you click on a folder to open it and see what files & folders are there.

---

### Post by sirvinniei on 2011-09-29
> **oldfred said:**
> From the liveCD open up the file browser Nautilus or click on places. In the left panel should be your windows, but it may just be called 40GB partition or whatever size it is. Then it is like window explorer as you click on a folder to open it and see what files & folders are there.
but the ubuntu live c conatains .exe files which ubuntu cant open

---

### Post by oldfred on 2011-09-29
I do not want you to try to run .exe which you cannot (perhaps some work in .wine but that is another issue).

We just want to know if you have these folders in your windows c: which may be sda1 (or was sda2 which is now the extended partition) in Linux.

/Boot
/Windows
/Windows/System32

And do they have files like the essential boot file and many other windows files:
/Windows/System32/winload.exe 

If the files are in sda1 then it may be repairable, if not then you may have to reinstall.

---

### Post by sirvinniei on 2011-09-29
> **oldfred said:**
> I do not want you to try to run .exe which you cannot (perhaps some work in .wine but that is another issue).

We just want to know if you have these folders in your windows c: which may be sda1 (or was sda2 which is now the extended partition) in Linux.

/Boot
/Windows
/Windows/System32

And do they have files like the essential boot file and many other windows files:
/Windows/System32/winload.exe 

If the files are in sda1 then it may be repairable, if not then you may have to reinstall.
So I should boot my pc with the linux disk in it and what  option should i select  then?

btw i did see a "reserved by system" (or something like that  translated from dutch) on my taskbar if you mean that?
it contains: /Boot /Temp /system volume information
and the files "bootmgr" and "BOOTSEKT.BAK"


sorry for my  ignorance

---

### Post by cryptotheslow on 2011-09-29
Yes boot from the LiveCD and use the "Try Ubuntu" option ([COLOR=Red]_**DO NOT**_[/COLOR] choose the Install option).

Open the file explorer (this is called Nautilus) - on the left hand side you will see a list of Places - one should be called something like "500GB Filesystem" - note: the size will probably be different but do not worry.

Just click on it to explore it - if it is your Windows filesystem then you should see the contents of what would be you C: drive in Windows.

[COLOR=Red]_**DO NOT**_[/COLOR] change, move, edit or delete any files on that filesystem.

Then post back here what you find so we can help you further.

---

### Post by sirvinniei on 2011-09-29
> **cryptotheslow said:**
> Yes boot from the LiveCD and use the "Try Ubuntu" option ([COLOR=Red]_**DO NOT**_[/COLOR] choose the Install option).

Open the file explorer (this is called Nautilus) - on the left hand side you will see a list of Places - one should be called something like "500GB Filesystem" - note: the size will probably be different but do not worry.

Just click on it to explore it - if it is your Windows filesystem then you should see the contents of what would be you C: drive in Windows.

[COLOR=Red]_**DO NOT**_[/COLOR] change, move, edit or delete any files on that filesystem.

Then post back here what you find so we can help you further.
wow that took a long time to boot
checked the 499 gb folder and it contained files which looked  like ubuntu  files
almost exactly the same  file  as in "filesystems" on my ubuntu profile

---

### Post by cryptotheslow on 2011-09-29
Were there any other filesystems listed there? If so what do you find in them?

You should be able to get internet access from the LiveCD "Try Ubuntu" to post replies here so avoiding having to reboot the whole time (and yes it can be a bit slow to boot up from CD!).

---

### Post by oldfred on 2011-09-29
You have two larger partitions about the same size sda1 & sda5. If it is your Ubuntu file system you want to look at the other one.

---

### Post by cryptotheslow on 2011-09-29
As you touched on earlier oldfred - it's not making a great deal of sense.

sda1 is ntfs formatted but marked as type 83.

Speculation only here, but I suspect that partition was originally a lot smaller with a second much larger ntfs partition next to it with the Windows install in it. Maybe somehow the installer zapped the second ntfs partition, grew the system reserve partition to 1/2 the disk then slapped the extended partition after it. So theoretically in this scenario it should be possible to correct the type of sda1 and quite possibly rescue some of the files from the zapped partition using e.g. photorec etc.

Do you happen to know if when doing an install if the new partition is actually fully formatted, or does it just create the new partitions and slap a file table in them? If the latter then presumably there may be some recoverables in the empty space in the latter half of the drive as well.

---

### Post by oldfred on 2011-09-29
I have seen the partition table type be incorrect and using disk utility or sfdisk change back to type 07 and system is ok, but that is not always the case.

@sirvinniei
Can you in th live Cd, go to System, Administration, Disk Utility, and click on your sda1 partition. Do not format, but at bottom right click on partition type. Change to HPFS /NTFS (0x07).

---

### Post by cryptotheslow on 2011-09-29
@oldfred
Yeh - I don't expect the system to boot into Windows just by changing sda1 to 0x07 as it appears the main Windows partition has been zapped. But it needs doing none the less. What I am thinking is that sda1 has been grown over the first portion of what was the Windows main install partition. As I understand it, the installer just uses parted to do this - then it's just the partition table that has been rewritten + some file tables for the new partitions in the extended, in the process of which the file table for the Windows main install partition is lost.

If the OP had less than 500GB of 'stuff' in their main Windows partition then logically it is still on the disk contained in the space now occupied by sda1. That presumes Windows doesn't randomly write files all over the place and tries to keep to the data it writes to the beginning of its partition.

OP is going to require a fairly hefty sized external/alternate drive to try to perform an e.g. photorec grab of files as it will recover the Win reserved drive and the Ubuntu install along with the stuff they actually really want to recover.

Glad to see this isn't just being booted out of Ubuntu forums as a "Seek help in a Windows forum". We may be able to get the OP back the files they need from their Win install then guide them on the sane way to do a dual-boot (and hopefully learn how they came to this predicament to start with - be that a buglet in the installer or lack of clarity in the side-by-side walk-through which should avoid this).

---

### Post by sirvinniei on 2011-09-30
I'm reading à lot of Posts, what actuallymis The Next thing i should do? Btw i knowhow this is offtopic but somehow firefox crashes when i try to view the third page on this thread (im using my iPod now) what could i do to view this page

---

### Post by cryptotheslow on 2011-09-30
When booted from the LiveCD, in the file explorer, what other filesystems do you see other than the 500GB one containing the Linux files?

And also:
[quote=oldfred]
@sirvinniei
Can you in th live Cd, go to System, Administration, Disk Utility, and  click on your sda1 partition. Do not format, but at bottom right click  on partition type. Change to HPFS /NTFS (0x07).
[/quote]

Once that is done, reboot with the LiveCD and check in file explorer again and see if any more filesystems have appeared.

And I have no idea why Firefox crashes for you on page 3 of this thread, it works fine for me using Firefox :???:

---

### Post by sirvinniei on 2011-09-30
> **cryptotheslow said:**
> When booted from the LiveCD, in the file explorer, what other filesystems do you see other than the 500GB one containing the Linux files?

And also:


Once that is done, reboot with the LiveCD and check in file explorer again and see if any more filesystems have appeared.

And I have no idea why Firefox crashes for you on page 3 of this thread, it works fine for me using Firefox :???:

When i open disk utility i dont see a sda1 i only see 2 pta host adapter tabs and in the 2nd i see 1 tb harddisk and cd drive  plus NeXT to THE two pata's i also see peripheral devices which had 690 mb drive securedigitaldrive compactflashdrive smartmediadrive and memorystick drive in my file browser i see Next to the 500 gb one another 1 tb hard disk which says: "reserved by system" (translated from dutch)

---

### Post by oldfred on 2011-09-30
Cllick on your 1TB drive and post a screen shot like mine.
Applications, Accessories, take Screenshot. Then upload using paperclip icon in edit panel above a new message.

---

### Post by sirvinniei on 2011-09-30
here you are

door systeem gereserveerd means reserved by system as I already might have told you

---

### Post by oldfred on 2011-09-30
That is very large for a system reserved partition. And it should not be type 83.

From that screen try clicking on edit partition and change type from 83 to  HPFS /NTFS (0x07).

---

### Post by sirvinniei on 2011-09-30
> **oldfred said:**
> That is very large for a system reserved partition. And it should not be type 83.

From that screen try clicking on edit partition and change type from 83 to  HPFS /NTFS (0x07).
should i select ordeselect bootable?

---

### Post by sirvinniei on 2011-09-30
see attachment, this happened when i tried to edit partition (after some  time not directly)

sorry for  double post

---

### Post by oldfred on 2011-09-30
One more try.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

and post PTsda.txt here.

---

### Post by jtpctech on 2011-09-30
Put your Windows 7 Disk in and Boot Goto Repair Your Computer

and Command Prompt

Type

bootrec /fixboot

bootrec /fixmbr


That should fix you

---

### Post by oldfred on 2011-09-30
@jtpctech
That may work if the partition was NTFS, but partition table has it as type 83 even though format is NTFS. Windows only repairs NTFS partition with the boot flag. We need to fix inconsistency first, if we can.

---

### Post by sirvinniei on 2011-10-01
> **oldfred said:**
> One more try.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

and post PTsda.txt here.
hoew do you backup a partition?
oh and how much gb may that be because I don have a backup device

---

### Post by cryptotheslow on 2011-10-01
oldfred is not suggesting you backup an entire partition, only the partition table which is just information about the partitions you have.

The command below will output the table to a small text file that you can then attach to a post here:
```
sudo sfdisk -d /dev/sda > PTsda.txt
```

---

### Post by sirvinniei on 2011-10-01
hmm strange
translation: Warning: extensive partition doesn start with a cylinder boundary.
 DOS and Linux will interpret the content differently

---

### Post by oldfred on 2011-10-01
Ignore warning, copy & post the contents of PTsda.txt.

Hard drives have not used cylinders since they became larger than 8GB. BIOS all have LBA large Block allocation. Since Linux & XP all started at sector 63 it never reported any errors, but now they have changed defaults to accomodate larger drives & SSDs. Error message needs to be updated.

---

### Post by sirvinniei on 2011-10-01
> **oldfred said:**
> Ignore warning, copy & post the contents of PTsda.txt.

Hard drives have not used cylinders since they became larger than 8GB. BIOS all have LBA large Block allocation. Since Linux & XP all started at sector 63 it never reported any errors, but now they have changed defaults to accomodate larger drives & SSDs. Error message needs to be updated.
what do you  mean with ignoring? do you mean that I should imput the code  again or that the file will be written even though it gave me a warning, and where do i find the PTsda.txt file? on my desktop?

---

### Post by oldfred on 2011-10-01
I meant ignore the error on cylinder boundary.

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=973993805, Id=[COLOR=Red]83[/COLOR], bootable
/dev/sda2 : start=973996030, size=979527682, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=973996032, size=973766656, Id=83
/dev/sda6 : start=1947764736, size=  5758976, Id=82
```Make a copy of PTsda.txt and change the 83 to space 7 like the entry for sda2 that has space 5. Make no other changes.

Then restore where PTsda.txt is the edited copy.:
```
sudo sfdisk --no-reread -f /dev/sda -O PTsda.save < PTsda.txt
```"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

---

### Post by sirvinniei on 2011-10-02
> **oldfred said:**
> I meant ignore the error on cylinder boundary.

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=973993805, Id=[COLOR=Red]83[/COLOR], bootable
/dev/sda2 : start=973996030, size=979527682, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=973996032, size=973766656, Id=83
/dev/sda6 : start=1947764736, size=  5758976, Id=82
```Make a copy of PTsda.txt and change the 83 to space 7 like the entry for sda2 that has space 5. Make no other changes.

Then restore where PTsda.txt is the edited copy.:
```
sudo sfdisk --no-reread -f /dev/sda -O PTsda.save < PTsda.txt
```"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

done
```
Schijf /dev/sda: 121601 cilinders, 255 koppen, 63 sectoren/spoor
Waarschuwing: uitgebreide partitie begint niet op een cilindergrens.
DOS en Linux zullen de inhoud verschillend interpreteren.
Oude situatie:
Eenheid = cilinders van 8225280 bytes, blokken van 1024 bytes, tellend vanaf 0

   Apparaat Opst Begin   Einde   #cils   #blokken   ID  Systeem
/dev/sda1   *      0+  60628-  60629- 486996902+  83  Linux
/dev/sda2      60628+ 121601-  60973- 489763841    5  Uitgebreid
/dev/sda3          0       -       0          0    0  Leeg
/dev/sda4          0       -       0          0    0  Leeg
/dev/sda5      60628+ 121242-  60615- 486883328   83  Linux
/dev/sda6     121242+ 121601-    359-   2879488   82  Linux wisselgeheugen
Nieuwe situatie:
Eenheid = sectoren van 512 bytes, tellend vanaf 0

   Apparaat Opst    Begin     Einde  #sectoren  ID  Systeem
/dev/sda1   *      2048 973995852  973993805   7  HPFS/NTFS
/dev/sda2     973996030 1953523711  979527682   5  Uitgebreid
/dev/sda3             0         -          0   0  Leeg
/dev/sda4             0         -          0   0  Leeg
/dev/sda5     973996032 1947762687  973766656  83  Linux
/dev/sda6     1947764736 1953523711    5758976  82  Linux wisselgeheugen
Waarschuwing: partitie 1 eindigt niet op een cilindergrens
De nieuwe partitietabel is succesvol geschreven.

Herinlezen van partitietabel...
BLKRRPART: Apparaat of hulpbron is bezig
Het opnieuw inlezen van de partitietabel is mislukt.
Voer partprobe(8) of kpartx(8) uit, of herstart uw systeem nu,
alvorens 'mkfs' te gebruiken.

Als u een DOS-partitie gemaakt of gewijzigd hebt, stel /dev/foo7,
gebruik dan dd(1) om de eerste 512 bytes nul te maken:
  dd if=/dev/zero of=/dev/foo7 bs=512 count=1  (zie man fdisk(8))

```

---

### Post by oldfred on 2011-10-02
Are those warning messages or error messages?

Can you now see Windows files in the NTFS partition?

---

### Post by sirvinniei on 2011-10-02
> **oldfred said:**
> Are those warning messages or error messages?

Can you now see Windows files in the NTFS partition?
google translate translation:
```
Drive / dev / sda: 121601 cylinders, 255 heads, 63 sectors / track
 Warning: extended partition does not start on a cylinder boundary.
 DOS and Linux will interpret the contents differently.
 Old situation:
 Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

    OPST Device Start End Blocks Id System # # CILS
 / dev/sda1 * 0 + 60628 - 60629-486996902 + 83 Linux
 / dev/sda2 60628 + 121601 - 60973-489763841 5 Extended
 / dev/sda3 0 - 0 0 0 Empty
 / dev/sda4 0 - 0 0 0 Empty
 / dev/sda5 60628 + 121242 - 60615-486883328 83 Linux
 / dev/sda6 121242 121601 + - 359-2879488 82 Linux swap partition
 New situation:
 Units = sectors of 512 bytes, counting from 0

    Device Start End OPST # sectors Id System
 / dev/sda1 * 2048 973995852 973993805 7 HPFS / NTFS
 / dev/sda2 973996030 979527682 1953523711 5 Extended
 / dev/sda3 0 - 0 0 Empty
 / dev/sda4 0 - 0 0 Empty
 / dev/sda5 973996032 1947762687 973766656 83 Linux
 / dev/sda6 1947764736 1953523711 5758976 82 Linux swap partition
 Warning: partition 1 does not end on cylinder boundary
 The new partition table has been successfully written.

 re-reading partition table ...
 BLKRRPART: Device or resource busy
 Re-reading the partition table failed.
 Enter part probe (8) or kpartx (8) off, or restart your system now,
 before 'mkfs' use.

 If you have a DOS partition is created or modified, setup / dev/foo7,
 using dd (1) to the first 512 bytes to zero:
   dd if = / dev / zero of = / dev/foo7 bs = 512 count = 1 (see man fdisk (8))
```"door systeem gereserveerd" still contains the same files, don know about the partitiontype though

---

### Post by oldfred on 2011-10-02
If you look at it with Disk Utility did it change to type 07 or not?

---

### Post by sirvinniei on 2011-10-02
> **oldfred said:**
> If you look at it with Disk Utility did it change to type 07 or not?
its changed to 07 ntfs

---

### Post by oldfred on 2011-10-03
Now can you mount the NTFS partition and see data? 

Or from a Windows repairCD run chkdsk?

---

### Post by sirvinniei on 2011-10-03
> **oldfred said:**
> Now can you mount the NTFS partition and see data? 

Or from a Windows repairCD run chkdsk?
clicked on mound volume.
how do i run chdisk? is it  one of the repair option on the repair disk?

---

### Post by oldfred on 2011-10-03
You have to have a Windows repairCD or full install (not vendor recovery).

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by sirvinniei on 2011-10-04
> **oldfred said:**
> You have to have a Windows repairCD or full install (not vendor recovery).

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

I burned an windows repair  disc  iso on a cd but when i start the repair disk i only get  a few  options, what should i do to insert that script?

---

### Post by sirvinniei on 2011-10-04
> **oldfred said:**
> You have to have a Windows repairCD or full install (not vendor recovery).

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Btw the repairdisk says my Windows partition is 0 mb

---

### Post by oldfred on 2011-10-04
Rerun boot script so we can see where you are at. Be sure to post the newer run.

---

### Post by sirvinniei on 2011-10-05
> **oldfred said:**
> Rerun boot script so we can see where you are at. Be sure to post the newer run.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: onbekende bestandssysteemsoort ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   973,995,852   973,993,805   7 NTFS / exFAT / HPFS
/dev/sda2         973,996,030 1,953,523,711   979,527,682   5 Extended
/dev/sda5         973,996,032 1,947,762,687   973,766,656  83 Linux
/dev/sda6       1,947,764,736 1,953,523,711     5,758,976  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Schijf /dev/sdb: 3965 MB, 3965190144 bytes
49 koppen, 48 sectoren/spoor, 3292 cilinders, totaal 7744512 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192     7,744,511     7,736,320   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 6fc169be-d10b-4634-b955-a81ab3479e40   swap       
/dev/sda1        4EA0A14EA0A13CF9                       ntfs       Door systeem gereserveerd
/dev/sda5        59a10da9-6145-462d-8276-cf6b716896ec   ext4       
/dev/sdb1        3634-3033                              vfat       šF5º¬Ô'5ó

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/                 vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
set locale_dir=($root)/boot/grub/locale
set lang=nl_NL
insmod gettext
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
menuentry 'Ubuntu, met Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-11-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, met Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-8-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=59a10da9-6145-462d-8276-cf6b716896ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 59a10da9-6145-462d-8276-cf6b716896ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4EA0A14EA0A13CF9
    chainloader +1
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=59a10da9-6145-462d-8276-cf6b716896ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=62304e79-c77f-4e25-94b0-cfe2aff63e19 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 714.571578979 = 767.265390592  boot/grub/core.img                             1
 476.591037750 = 511.735730176  boot/grub/grub.cfg                             1
 468.414062500 = 502.955769856  boot/initrd.img-2.6.38-11-generic              2
 468.329475403 = 502.864945152  boot/initrd.img-2.6.38-8-generic               1
 467.695621490 = 502.184349696  boot/vmlinuz-2.6.38-11-generic                 1
 714.569805145 = 767.263485952  boot/vmlinuz-2.6.38-8-generic                  1
 468.414062500 = 502.955769856  initrd.img                                     2
 468.329475403 = 502.864945152  initrd.img.old                                 1
 467.695621490 = 502.184349696  vmlinuz                                        1
 714.569805145 = 767.263485952  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-10-05
Script show partition ok, but does not show /Windows/System32/winload.exe which is part of the main boot and wth the system folders have to be there.

Is the Windows Disks you created a repairCD or a Vendor recovery DVD? Vendor DVDs are just an image of you hard drive as purchased to restore to as purchased state.

Windows sda1 NTFS partition looks like about a third of your drive so it could have lots of data & your system. Normal Windows  7 installs have a small 100MB boot/recovery and then the main NTFS (c:) partition.

You can try this from Ubuntu, but it is not chkdsk.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows, it should run "chkdsk".

---

### Post by sirvinniei on 2011-10-05
> **oldfred said:**
> Script show partition ok, but does not show /Windows/System32/winload.exe which is part of the main boot and wth the system folders have to be there.

Is the Windows Disks you created a repairCD or a Vendor recovery DVD? Vendor DVDs are just an image of you hard drive as purchased to restore to as purchased state.

Windows sda1 NTFS partition looks like about a third of your drive so it could have lots of data & your system. Normal Windows  7 installs have a small 100MB boot/recovery and then the main NTFS (c:) partition.

You can try this from Ubuntu, but it is not chkdsk.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows, it should run "chkdsk".
trying the script right now,

oh and this is offtopic  but still has to do with the topic;
whenever i try to download something with terminal or with softwarecentre
i get this error:
```
Regenerating fonts cache... failed; see /var/log/fontconfig.log for more information.
dpkg: fout bij afhandelen van ttf-wqy-zenhei (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 ttf-wqy-zenhei

```do you know what  to do to fix  this

ow and i added some printsceens of my  door  systeem  gerserveerd folder

---

### Post by oldfred on 2011-10-05
Your screen shot shows no /Windows folder in the NTFS partition. That goes back to an earlier post where something odd must have happened to combine your sda1 & sda2 Windows partitions into one, but that seems to have destroyed your Windows install. It looks like the typical 100MB boot partition for Windows but is much larger. What is in temp?

Did you look at /var/log/fontconfig.log to see exactly what the error messages are. That should help explain how to fix. May have to uninstall or reinstall.

---

### Post by sirvinniei on 2011-10-06
> **oldfred said:**
> Your screen shot shows no /Windows folder in the NTFS partition. That goes back to an earlier post where something odd must have happened to combine your sda1 & sda2 Windows partitions into one, but that seems to have destroyed your Windows install. It looks like the typical 100MB boot partition for Windows but is much larger. What is in temp?

Did you look at /var/log/fontconfig.log to see exactly what the error messages are. That should help explain how to fix. May have to uninstall or reinstall.
this is fontconfig
[CODE][/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 20 dirs
/usr/share/fonts/truetype/aenigma: caching, new cache contents: 465 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: Bus error/CODE]

added a scrrenshot of temp

---

### Post by oldfred on 2011-10-06
You are showing no Windows install or files. Hope you have a good backup.

/usr/share/fonts/truetype/msttcorefonts: Bus error/CODE]

The code tags did not work as yor are missing  [. If you use the # in the edit panel it auto adds code tags.

Some issue with msttcorefonts.

You could try this and see what it says:

apt-get install msttcorefonts

---

### Post by sirvinniei on 2011-10-06
> **oldfred said:**
> You are showing no Windows install or files. Hope you have a good backup.

/usr/share/fonts/truetype/msttcorefonts: Bus error/CODE]

The code tags did not work as yor are missing  [. If you use the # in the edit panel it auto adds code tags.

Some issue with msttcorefonts.

You could try this and see what it says:

apt-get install msttcorefonts
tried to install msttcorefonts but gor the same error:p
and no,I don have a backup (not that I care toomuch cuzthere weren  any important files on my drive)
so  how  shouldI be able toreinstall windows?

---

### Post by oldfred on 2011-10-06
Do you have a full Windows install or did you make the Windows Recovery DVD's from the recovery partition the vendor has on your drive? If not you have to call the vendor & get (may have to pay) a windows recovery disk(s).

---

### Post by sirvinniei on 2011-10-07
> **oldfred said:**
> Do you have a full Windows install or did you make the Windows Recovery DVD's from the recovery partition the vendor has on your drive? If not you have to call the vendor & get (may have to pay) a windows recovery disk(s).
Wont I get any problems with serials?

---

### Post by oldfred on 2011-10-07
You should have the serial number on the bottom of the computer. When you reinstall it will ask for that.

---

### Post by sirvinniei on 2011-10-13
> **oldfred said:**
> You should have the serial number on the bottom of the computer. When you reinstall it will ask for that.

Well thanks for your help but im going back to singlebooting Windows again, all those problems with Ubuntu.

---

