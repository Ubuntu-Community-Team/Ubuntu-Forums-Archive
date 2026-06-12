---
title: "Missing ANG2?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by mlplatt on 2012-07-19
I have been away for a couple of weeks. Prior to my departure Ubuntu was working well. On my return it doesn't work at all. When I select it on start up (I run it as an alternative to Vista) I get a scroll of text the gist of which is *'Cannot find ang 2 in all drives'.*

Can anyone advise please? 

Malcolm

---

### Post by z3nhakr on 2012-07-19
when and where does this happen? can you attach a screenshot/photo

---

### Post by mlplatt on 2012-07-20
Hi.

When I boot up the computer I have a choice of Vista or Ubuntu. I choose Ubuntu and click on it,. The screen immediately lists a series of message lines with a conclusion that it 'Cannot find ang 2 in all drives'. It then gives me the option of restarting by pressing Crtl+Alt+Del. This I do and it takes me back to the choice between Vista and Ubuntu. Clicking on Vista brings that up without any difficulty. 

I can't provide a screenshot because I am not in any OS at that stage. Or if there is a way of doing it it is beyond my competence which is admittedly very slight. 

If it would help I can transcribe the individual message lines if that would help although they are fairly repetitive and just relate to the missing ang 2, (or ANG 2)

Regards,

Malcolm

---

### Post by coffeecat on 2012-07-20
> **mlplatt said:**
> 'Cannot find ang 2 in all drives'.

Googling for that error brings up only this thread, and googling for ang2 or "ang 2" is also unrewarding, so I wonder if it was saying something else. Do you have a digital camera? If so, take a picture of the monitor when the messages come to a halt and post it. Perhaps that may help.

---

### Post by mlplatt on 2012-07-20
O.K. Herewith photo. I hope it is legible 

Thanks,

Malcolm

---

### Post by coffeecat on 2012-07-20
I have to admit that I've never heard of the expression "ang2" so I'm mystified at the moment. However, several of the lines in your photo have references to partitions the way grub expresses them: (hd0,0) and so on. Not only that, but "(hd0,0)" would suggest legacy grub. So it would be useful to get an overview of your system with the boot info script.

Do you have a live Ubuntu CD or USB available? If so, boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Please note that there is currently an error in the instructions on that page. The script file is now called bootinfoscript, and if moved to your desktop the command should be 'sudo bash ~/Desktop/bootinfoscript'.

The output of the boot script should tell us anyway, but what version of Ubuntu are you running and is this a wubi installation?

---

### Post by mlplatt on 2012-07-27
Hi Coffeecat,

I do apologise for not replying earlier. I am afraid other events have crowded in on me and I have had no time to follow your instructions yet. At my level of competence they would take some time and will have to wait until next week when things have otherwise quietened down. 

In the meantime ... I did have some difficulty originally in installing Ubuntu and it is quite possible some shards of past attempts still lurk somewhere.  It is a partitioned programme from an Ubuntu 11.10 CD. Later I updated by download to the latest 12. 

So the only disc I have is for the 11.10 version. would that matter? 

The partition and installation were eventually done using the EasyBCD programme. Could the ang2 be connected to that? 

I hope to have more time to take this further at the beginning of next week. 

Until then thanks for your help.

Regards,

Malcolm

---

### Post by coffeecat on 2012-07-27
The live CD for 11.10 will be just fine.

Interesting that you are booting with EasyBCD. The messages with "ang2" in them appear to be grub ones, but not grub messages that I have seen. As far as I understand, having never used it myself, Easy BCD uses Windows boot code for the OS selection menu and then chainloads to grub in the root partition of your Linux system if you choose Linux at the boot menu. Anyway, hopefully the output of the boot script will reveal something useful. It is much easier to use than might appear.

---

### Post by mlplatt on 2012-08-02
I have fallen at the first fence in that I can't get it to boot up from the disk of Ubuntu 11.10. The computer with the disk loaded just goes straight into Vista without offering a selection when I try. 

To try and get round this I looked again at the EasyBCD programme. I was tempted to try to reload the CD through this but on reflection thought that, not having the faintest understanding of possible consequences I might just add to the litter swilling around. What I did do was to try the 'Recreate/Repair Boot Files' in the Management options. This was not successful however on rebooting the information has changed from the original one that I posted. 

It is now as the thumbnail attached. 

The settings as shown on EasyBCD are as follows if they give any clue. 

[CODE] _**Overview**_
 

 There are a total of 2 entries listed in the bootloader.
 

 Default: Microsoft Windows  Vista
 Timeout: 10 seconds
 EasyBCD Boot Device: C:\
 

 Entry #1
 Name: Microsoft Windows  Vista
 BCD ID: {current}
 Drive: C:\
 Bootloader Path: \Windows\system32\winload.exe
 

 Entry #2
 Name: NeoSmart Linux
 BCD ID: {05711a60-dcae-11e1-8219-001d0983711d}
 Drive: C:\
 Bootloader Path: \NST\AutoNeoGrub1.mbr
 

 _**Detailed (Debug Mode)**_
 

  Windows Boot Manager
  --------------------
  identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
  device                  boot
  description             Windows Boot Manager
  locale                  en-US
  inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
  default                 {288f9bab-d5b1-11e1-8083-001d0983711d}
  resumeobject            {b2a4493a-d5b1-11e1-a9b5-806e6f6e6963}
  displayorder            {288f9bab-d5b1-11e1-8083-001d0983711d}
                          {05711a60-dcae-11e1-8219-001d0983711d}
  toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
  timeout                 10
  resume                  No
  displaybootmenu         Yes
  

  Windows Boot Loader
  -------------------
  identifier              {288f9bab-d5b1-11e1-8083-001d0983711d}
  device                  partition=C:
  path                    \Windows\system32\winload.exe
  description             Microsoft Windows  Vista
  locale                  en-US
  osdevice                partition=C:
  systemroot              \Windows
  resumeobject            {b2a4493a-d5b1-11e1-a9b5-806e6f6e6963}
  

  Real-mode Boot Sector
  ---------------------
  identifier              {05711a60-dcae-11e1-8219-001d0983711d}
  device                  partition=C:
  path                    \NST\AutoNeoGrub1.mbr
  description             NeoSmart Linux
  [/ CODE]


Thanks,

Malcolm

---

### Post by coffeecat on 2012-08-02
> **mlplatt said:**
> I have fallen at the first fence in that I can't get it to boot up from the disk of Ubuntu 11.10.

You need to adjust the BIOS settings to boot from the optical drive first. 

> **mlplatt said:**
> The computer with the disk loaded just goes straight into Vista without offering a selection when I try. 

<snip>

This was not successful however on rebooting the information has changed from the original one that I posted. 

It is now as the thumbnail attached. 

Those are legacy grub messages. I'm confused here now. You say that the system is now booting into Vista, but you are getting these grub messages? I can't reconcile the two, except that entry #2 in your BCD menu (which you say you are not seeing) refers to Linux and grub, and what looks like the UUID for a Linux filesystem formatted partition. To make sense of all this the output of the boot script would help, and adjusting your BIOS settings should allow you to boot the Ubuntu CD.

---

### Post by mlplatt on 2012-08-02
Sorry. I didn't explain properly. The computer boots directly into Vista only when I have the Ubuntu CD in the CD drive.

When I start up normally it does give me the choice between Vista and Ubuntu and the photo depicts the screen when I choose the latter.

I am afraid you have lost me when you talk of adjusting the BIOS settings. Whet are they and how can I adjust them?

Regards,

Malcolm

---

### Post by coffeecat on 2012-08-03
When you first switch on the computer, you will see a manufacturer's splash screen or a POST (power-on self-test) screen telling you about aspects of your hardware. If that is a purchased pre-assembled desktop rather than one you assembled yourself, or a laptop, you will most likely see a manufacturer's splash. To enter the BIOS you need to press a certain key at that point, but which key depends on the make of machine. It's often DEL or F2 but it can be almost anything. Have a look in the manual, or try googling for BIOS key <your make and model of machine>. What make and model is it?

Once you've got into the BIOS, you will need to find your way around to where the boot device order priority is and set the optical drive before the internal hard drive.

Having said all that, if the machine is behaving differently with the Ubuntu CD in the drive (I cannot explain why it boots into Vista with the CD in the drive - that's odd) then it sounds as though the machine may be set to boot from the CD drive first. In which case something would be wrong with your CD.

Question. Is this a conventional dual-boot system where you installed Ubuntu to its own partition using a live CD (in which case it would have booted up once), or did you install a wubi system? A wubi system is one where you download a small file called wubi.exe and run this from inside Windows. From what you've already said, I think it's the former, but it would be helpful to be sure.

---

### Post by mlplatt on 2012-08-03
Just passing through ... I have had no time today to spend on the computer.

I will revert to your advice later. 

In the meantime the computer is a Dell Inspiron and the installation was a dual boot one with the partition organised by EasyBCD as mentioned earlier.

I will have a go at changing the BIOS when I have a few free moments


Regards.

Malcolm

---

### Post by mlplatt on 2012-08-09
I am afraid i have been called away and only got back yesterday.

I am afraid that, doubtless due to  incompetence, I am having difficulty with the Boot Info Script. Thanks to your advice I have managed to boot up the computer using the Ubuntu installation CD. However It doesn't take me into the existing Ubuntu programme but gives me a choice of either installing Ubuntu or running a demonstration. 

I thought that to install it again would probably mean having yet another partition and so ran it as a demonstration. I downloaded the Boot Info Script and opened a terminal but my keyboard doesn't seem to correspond correctly to the demonstration programme. The ~ mark translates as | and so I cannot follow the Boot Info Script Instructions which requires me to type *sudo bash ~/ etc.* Nor can I find the ~elsewhere.

As it is the instruction results in a message saying it cannot find the downloaded Boot_Info_Script.

Would it just be better to start again and reinstall Ubuntu . If so how do i uninstall the previous version which must still be lurking in there somewhere? And of course there is the question of the existing partition.

Regards,

Malcolm

---

### Post by coffeecat on 2012-08-09
Yes - finding the ~ key in the live session can be difficult depending on your geographical localisation. I live in the UK and use a UK keyboard and it's a drawback of the live session for me that it defaults to a US keyboard (which is somewhat different).

Boot up the live CD and choose "try Ubuntu" to get to the demonstration, as you call it. Download the bootinfoscript-061.tar.gz file and open the Downloads folder which you will find in the home folder. Unpack the downloaded bootinfoscript-061.tar.gz file by double-clicking on it and choosing "extract". The bootinfoscript file will be found in the bootinfoscript-061 folder which itself will appear in the Downloads folder. Copy or move the "bootinfoscript" file to the desktop. You can then run it from the terminal with:

```
sudo bash /home/ubuntu/Desktop/bootinfoscript
```

Or:

```
sudo bash Desktop/bootinfoscript
```

---

### Post by mlplatt on 2012-08-10
OK I think that I have got it.  Thanks for the explanation re the keyboard. I am in the UK too. 

The download was presaged with the warning -

```
    	 	 	 	 	 	  gawk could not be found, using busybox awk instead. This may lead to unreliable results.
  
```

The result was -

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 397770752.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

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

/dev/sda1                  63       112,454       112,392   6 FAT16
/dev/sda2             112,640    21,084,159    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,084,160   691,147,929   670,063,770   7 NTFS / exFAT / HPFS
/dev/sda4         691,148,798   976,771,071   285,622,274   5 Extended
/dev/sda5         691,148,800   972,601,343   281,452,544  83 Linux
/dev/sda6         972,603,392   976,771,071     4,167,680  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   397,769,752   397,769,690   c W95 FAT32 (LBA)
/dev/sdb2         397,770,750   488,396,799    90,626,050   5 Extended
/dev/sdb5         397,770,752   484,225,023    86,454,272  83 Linux
/dev/sdb6         484,227,072   488,396,799     4,169,728  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D8-0308                              vfat       DellUtility
/dev/sda2        32FE2052FE2010A1                       ntfs       RECOVERY
/dev/sda3        5A8EB5ED8EB5C235                       ntfs       
/dev/sda5        56da761e-53ce-4e0b-bd77-e64d87468170   ext4       
/dev/sda6        59485a5d-4618-434c-8944-e53695001613   swap       
/dev/sdb1        7B05-602B                              vfat       My Book
/dev/sdb5        7388-1E5A                              vfat       New Volume
/dev/sdb6        be457892-1357-4ed5-99b7-10a7ff940f0d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/My Book           vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdb5        /media/New Volume        vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=56da761e-53ce-4e0b-bd77-e64d87468170 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=56da761e-53ce-4e0b-bd77-e64d87468170 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=56da761e-53ce-4e0b-bd77-e64d87468170 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    echo    'Loading Linux 3.0.0-19-generic ...'
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=56da761e-53ce-4e0b-bd77-e64d87468170 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-19-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 56da761e-53ce-4e0b-bd77-e64d87468170
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 5A8EB5ED8EB5C235
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=56da761e-53ce-4e0b-bd77-e64d87468170 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=59485a5d-4618-434c-8944-e53695001613 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-19-generic               2
               =                boot/initrd.img-3.2.0-24-generic               3
               =                boot/vmlinuz-3.0.0-19-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  8b 41 08 85 c0 74 0e 3b  71 0c 73 09 8b 14 f0 8b  |.A...t.;q.s.....|
00000010  44 f0 04 eb 04 33 c0 8b  d0 89 44 24 18 8b cd b8  |D....3....D$....|
00000020  1f 00 00 00 d3 e0 c1 ea  05 23 c2 25 ff ff 0f 00  |.........#.%....|
00000030  d3 e8 eb 02 33 c0 f6 44  24 1c 01 0f 84 16 01 00  |....3..D$.......|
00000040  00 8b cf ba 01 00 00 00  d3 e2 8b 4c 24 24 85 d1  |...........L$$..|
00000050  0f 84 01 01 00 00 83 f8  13 74 09 83 f8 15 0f 85  |.........t......|
00000060  f3 00 00 00 8b 53 28 8d  4c 24 14 51 c7 44 24 18  |.....S(.L$.Q.D$.|
00000070  00 00 00 00 8b 42 0c 6a  01 50 8b cb e8 8f 58 04  |.....B.j.P....X.|
00000080  00 50 6a 25 e8 a7 cb 0a  00 83 c4 14 a8 01 89 44  |.Pj%...........D|
00000090  24 1c 0f 84 ba 00 00 00  8b 43 28 8b 54 24 14 8b  |$........C(.T$..|
000000a0  6a 5c 8b 5a 4c 8b 52 68  8b 5c 9d 00 8b 88 00 06  |j\.ZL.Rh.\......|
000000b0  00 00 8b 80 d8 05 00 00  89 0c 9a 8b 54 24 14 8b  |............T$..|
000000c0  5a 44 8b 6a 50 8b 52 34  8b 5c 9d 00 89 0c 9a 8b  |ZD.jP.R4.\......|
000000d0  4c 24 20 ba 01 00 00 00  d3 e2 8b 4c 24 14 8b 49  |L$ ........L$..I|
000000e0  28 6a 01 89 11 8b 4c 24  18 8b 51 50 8b 49 34 8b  |(j....L$..QP.I4.|
000000f0  12 89 04 91 8b 4c 24 18  e8 e3 b2 0a 00 8b c7 83  |.....L$.........|
00000100  e0 03 8d 14 85 00 00 00  00 0b d0 03 d2 03 d2 0b  |................|
00000110  d0 03 d2 03 d2 0b d0 8b  44 24 14 8b 48 54 89 11  |........D$..HT..|
00000120  8b 44 24 14 8b 50 4c 8b  40 60 c7 04 90 08 00 00  |.D$..PL.@`......|
00000130  00 8b 4c 24 14 51 8b 4c  24 50 8d 54 24 44 52 e8  |..L$.Q.L$P.T$DR.|
00000140  7c 5b 06 00 8b 00 8b 6c  24 28 8b 5c 24 34 89 44  ||[.....l$(.\$4.D|
00000150  24 1c 83 44 24 20 01 83  c5 05 83 c7 01 83 fd 14  |$..D$ ..........|
00000160  89 6c 24 28 0f 82 86 fe  ff ff 8b 6c 24 30 83 c6  |.l$(.......l$0..|
00000170  01 3b 75 0c 0f 86 5b fc  ff ff 8b 44 24 48 8b 4c  |.;u...[....D$H.L|
00000180  24 1c 5f 5e 5d 89 08 5b  83 c4 34 c2 08 00 cc cc  |$._^]..[..4.....|
00000190  8b 44 24 0c 83 e8 02 53  55 8b 6c 24 18 56 57 8b  |.D$....SU.l$.VW.|
000001a0  f1 bb 01 00 00 00 74 09  2b c3 74 5e bb 02 00 00  |......t.+.t^....|
000001b0  00 f6 c3 01 0f 84 61 01  00 00 8d 54 24 20 00 fe  |......a....T$ ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a0 c6 10 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a0  c6 10 00 a0 3f 00 00 00  |............?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 8a 00  |.Z.MSWIN4.1..@..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  da 7b b5 17 a6 bd 00 00  00 00 00 00 48 03 00 00  |.{..........H...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 2b 60 05 7b 4e  4f 20 4e 41 4d 45 20 20  |..)+`.{NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 49 6e  76 61 6c 69 64 20 73 79  |...'..Invalid sy|
00000190  73 74 65 6d 20 64 69 73  6b ff 0d 0a 44 69 73 6b  |stem disk...Disk|
000001a0  20 49 2f 4f 20 65 72 72  6f 72 ff 0d 0a 52 65 70  | I/O error...Rep|
000001b0  6c 61 63 65 20 74 68 65  20 64 69 73 6b 2c 20 61  |lace the disk, a|
000001c0  6e 64 20 74 68 65 6e 20  70 72 65 73 73 20 61 6e  |nd then press an|
000001d0  79 20 6b 65 79 0d 0a 00  49 4f 20 20 20 20 20 20  |y key...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

Unknown BootLoader on sdb2

00000000  66 00 44 0a e5 b9 e7 1c  75 ef 4c 91 de 47 88 c7  |f.D.....u.L..G..|
00000010  99 9d 83 19 e5 0b c9 3f  c4 58 b1 e7 1c 0f c6 a9  |.......?.X......|
00000020  3b 3b 94 9d 9d c4 93 70  26 15 2e 81 9c 19 55 24  |;;.....p&.....U$|
00000030  e0 e2 a4 93 86 97 7c af  23 30 cc 1f 27 ca 00 03  |......|.#0..'...|
00000040  ef 13 fa 56 4a 13 3a 94  e4 e1 7b 11 33 11 18 db  |...VJ.:...{.3...|
00000050  6e a1 97 23 ce da 00 23  1c 0e 3a f7 eb 51 83 24  |n..#...#..:..Q.$|
00000060  0b 34 6c a1 5a 78 e3 25  64 03 72 80 41 18 f4 ce  |.4l.Zx.%d.r.A...|
00000070  05 5a 69 9c 82 85 2f e6  49 ba 15 50 a7 78 24 06  |.Zi.../.I..P.x$.|
00000080  e3 9c 8a 7c ce ca bb d8  86 57 68 d5 64 56 07 24  |...|.....Wh.dV.$|
00000090  8e 00 f5 e3 ad 5f 24 b9  2e 2e 65 7b 17 d3 6b 82  |....._$...e{..k.|
000000a0  fe 54 93 2c 48 59 88 8f  2b 8f 4f 94 e7 a6 79 aa  |.T.,HY..+.O...y.|
000000b0  a3 6a 24 d6 d6 f2 37 96  e1 40 91 48 24 20 23 00  |.j$...7..@.H$ #.|
000000c0  67 38 e4 0e 7a d7 55 14  e7 45 a3 3a 7a 36 89 55  |g8..z.U..E.:z6.U|
000000d0  d6 24 45 69 4a ef 50 62  94 c8 15 d5 fa 72 0f e7  |.$EiJ.Pb.....r..|
000000e0  9e f4 e4 8f 6c 45 dd 96  55 57 20 97 1c 93 db 38  |....lE..UW ....8|
000000f0  e8 7f c2 b9 2a c3 92 57  27 de 92 bf 99 57 32 45  |....*..W'....W2E|
00000100  2c 52 46 30 56 41 99 49  03 68 1c e7 9f c2 ad 22  |,RF0VA.I.h....."|
00000110  30 8a 51 75 23 cb 24 a7  29 34 6d 94 63 92 49 63  |0.Qu#.$.)4m.c.Ic|
00000120  d7 a7 4f 7a 52 6d 44 dc  84 79 52 47 28 6d df 34  |..OzRmD..yRG(m.4|
00000130  5f ba 50 9f 2e 47 55 6c  8f 4e fe b5 5e 35 69 11  |_.P..GUl.N..^5i.|
00000140  53 e6 88 9e 66 50 e3 e7  53 c3 67 23 3d c7 4a 12  |S...fP..S.g#=.J.|
00000150  50 41 cd c8 9b 63 a5 f9  4b 2b b8 44 95 b2 91 ed  |PA...c..K+.D....|
00000160  07 8e 80 03 f9 d2 3c 4b  1c 4a b9 0a 17 24 22 e3  |......<K.J...$".|
00000170  83 d7 91 db 35 4e 2e 24  46 71 9a 2b 99 08 51 34  |....5N.$Fq.+..Q4|
00000180  cd 1e d6 38 48 dd f6 b1  3d b1 ce 6a c2 4b 06 cf  |...8H...=..j.K..|
00000190  9a 14 81 9d 70 1a 6c 12  40 3d bd 33 8a d6 14 5c  |....p.l.@=.3...\|
000001a0  a3 79 0a 77 8c 34 00 e8  80 34 51 c6 c5 5c 80 09  |.y.w.4...4Q..\..|
000001b0  ca 93 9f 9b a7 d4 d3 1b  ca 8d 64 8e 42 ac 00 fe  |..........d.B...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 27 05 00 fe  |...........0'...|
000001d0  ff ff 05 fe ff ff 02 30  27 05 00 a8 3f 00 00 00  |.......0'...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
 
```

Does this help?

 Many Thanks,

Malcolm

---

### Post by coffeecat on 2012-08-10
> **mlplatt said:**
> 
Does this help?


Indeed it does, but it needs some digesting and I need to go over the whole thread again to re-acquaint myself with all the details of your situation. I probably won't have time for this until tomorrow, but I will give it some time then. It certainly throws up some puzzling and interesting things, not least of which is the earlier messages you saw were legacy grub ones, but I can see no signs of legacy grub in the boot script output. It shows evidence of your Ubuntu installation originally being a 11.10 (Oneiric) one but now upgraded to 12.04, neither of which use legacy grub. Intriguing, and I shall get back to you.

---

### Post by mlplatt on 2012-08-11
Thanks a lot. There is no hurry as I myself am finding life more than somewhat hectic generally as you have no doubt gathered. 

I am afraid that I probably complicated things badly when I originally tried to install Ubuntu and then switched to EasyBCD when I was unsuccessful. And of course I again tried to rectify the position with EasyBCD after the first message. I mentioned earlier that the original message changed at that point.

I am very grateful for all your efforts.

Yours,

malcolm

---

### Post by coffeecat on 2012-08-14
Sorry to take some time, but first:

> **mlplatt said:**
> The computer boots directly into Vista only when I have the Ubuntu CD in the CD drive.

Can you confirm that this is still so? Without a CD in the optical drive, your system should boot to the EasyBCD menu and then boot Vista when you choose that from the EasyBCD menu. I can see no reason why you should need a CD in the CD drive, which seems very odd.

Next - the output of the boot script is very useful and tells us various things that we might need to know. The most important being that you have Ubuntu on its own partition and not as a wubi installation, and that Windows code is in the mbr, therefore EasyBCD *should* be working. 

I've had a chance now to do some reading up on EasyBCD and your problems with booting into Ubuntu would appear to be due to a mis-configured EasyBCD. It seems that EasyBCD uses neogrub for booting Linux, and neogrub is based on legacy grub. Those screenshots you posted are errors from EasyBCD. Unfortunately, I have no experience of EasyBCD, and I would guess very few forum members would either. Most prefer to use grub for multi-booting purposes. Do you have a GUI for configuring EasyBCD? Are you able to adjust settings for the EasyBCD boot options?

Also - it seems that EasyBCD uses a legacy grub type menu.lst file for booting Linux systems. It might be possible to edit that to get Ubuntu booting properly. Have a look for a file called C:\NST\menu.lst in your Windows partition. If you can find it, post the contents between [noparse]```
 and 
```[/noparse] tags.

I have some other ideas we could pursue, one being to re-install grub to the mbr so that grub can control booting, but let's see if we can get EasyBCD to work properly first.

---

### Post by mlplatt on 2012-08-22
Success! I am posting this from Ubuntu.

Firstly though to again apologise for the delay... Between work and visitors the home computer has been out of bounds of late. 

As you suggested I went back to the EasyDCD which does indeed allow for adjustment of options. For booting Linux it lists -

Grub (Legacy)
Grub2
LILO/eLILO
FreeBSD/PC-BSD
Wubi
SysLinux
 
 As you mentioned that that most prefer grub, I removed the Grub ( Legacy) and installed Grub2 as the boot option. I had originally used  Legacy  as the option of choice because it was listed first and  I just presumed it was OK. 

The result was that I was that on the restart the Linux selection on the menu brought me straight here. 

Again my heartfelt thanks.

Regards,

Malcolm

---

