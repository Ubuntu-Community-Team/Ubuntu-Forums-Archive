---
title: "Boot Problem  Grub Rescue"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by trekguy on 2013-06-04
Hp Laptop dual boot 12.04  with Windows 7.  On start up, nothing appears til error: partition not found  grub rescue

IF, you tap the down arrow during startup, the boot/grub menu appears (although very small), then you can select the os.

In Synaptic, I notice both grub and grub2 are installed....issue??

---

### Post by MidnightGrey on 2013-06-04
(edit: i think your default  boot-up partition is a broken link)
Try typing the following in your terminal and see if that fixes it:
$ sudo update-grub

Also take note of the output and paste it here if your problem is not solved.

---

### Post by trekguy on 2013-06-04
Still have to hit arrow down to show boot options.... no error message this time.



tony@tony-laptop:~$ sudo update-grub
[sudo] password for tony: 
Sorry, try again.
[sudo] password for tony: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-2.6.32-45-generic
Found initrd image: /boot/initrd.img-2.6.32-45-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda3
done
tony@tony-laptop:~$

---

### Post by MidnightGrey on 2013-06-04
What happens when it boots without you hitting any keys?
Does it just boot into linux without issue?

edit: also do you really have two copies of Windows 7 installed on 2 seperate partitions? (sda1/sda2) / I ask because the 'ghost' Windows7 tends to show up on botched win7 installs.

edit2: if your computer boots into linux fine with no keys pressed. type 'cat /etc/default/grub' and paste the output.

---

### Post by trekguy on 2013-06-04
If I don't hit a key, it just sits on black screen.

Don't know why there's two Win 7...... brother-in-law's laptop....I was just setting up a new printer and noticed the boot prob.... annoys me.  ;-)

---

### Post by trekguy on 2013-06-05
tony@tony-laptop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]trekguy; Hi !

In just pass'n by ...I do not notice anything out-of-ordinary in the grub file....but here is a mere maybe, with so many kernels; is the boot partition full and the system has no operating room ???
quick looksee; terminal code:
```
df -h
```
[/COLOR][INDENT=3][COLOR=#000000]
just a thought

[/COLOR][/INDENT]

---

### Post by MidnightGrey on 2013-06-05
trekguy,

type **gksu gedit /etc/default/grub** to open a text editor.
then change **GRUB_HIDDEN_TIMEOUT_QUIET=true** to **false**.
Save and exit the file, and do **sudo update-grub** again.
See if that fixes your problem.

Cheers.

Also, you may want to remove the 'ghost' windows7, I suspect that was what was originally causing the 'partition not found' error.

---

### Post by trekguy on 2013-06-05
> **Bashing-om said:**
> [COLOR=#000000]trekguy; Hi !

In just pass'n by ...I do not notice anything out-of-ordinary in the grub file....but here is a mere maybe, with so many kernels; is the boot partition full and the system has no operating room ???
quick looksee; terminal code:
```
df -h
```
[/COLOR][INDENT=3][COLOR=#000000]
just a thought

[/COLOR][/INDENT]


tony@tony-laptop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        93G  6.9G   81G   8% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           712M  840K  711M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   76K  1.8G   1% /run/shm
tony@tony-laptop:~$

---

### Post by trekguy on 2013-06-05
> **MidnightGrey said:**
> trekguy,

type **gksu gedit /etc/default/grub** to open a text editor.
then change **GRUB_HIDDEN_TIMEOUT_QUIET=true** to **false**.
Save and exit the file, and do **sudo update-grub** again.
See if that fixes your problem.

Cheers.

Also, you may want to remove the 'ghost' windows7, I suspect that was what was originally causing the 'partition not found' error.


Did not fix it.  Other observations... when it does not boot, there's a line bottom left of black screen "press esc for boot menu".  If you press esc during power up, it will go to boot menu.... cd drive or hard drive are the usual choices.  Do save/exit from there gets the rescue grub thing again.

Which one is the ghost windows 7?  To run gparted, I need a live disk... the last one I have is 10.04.... do I need a 12.04 disk to run gparted?

---

### Post by Mark Phelps on 2013-06-05
Neither is likely to be the "ghost Windows".  In  preinstalled Win7 PCs, Win7 actually occupies two partitions -- a small "boot" partition and a larger "OS" partition. Since pieces of the Windows boot loader are in both partitions, os_prober presumes there are two "copies" of Win7 Loader and creates and entry for each.  Usually, the first entry is the one that works, but in some cases, os-prober gets confused, and it is really the second entry that works.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]trekguy; Still continue with you;

See Mark's last  (seems I follow Mark a lot !)
Boot stages -- real over simplified ...
turn on computer-> bios loads and checks things out
all good and bios hands off to the boot loader (grub in our case) -> grub pulls stuff together to build the ram image
ram image file system starts init ...the 1st process that controls starting everything else...

so the question is ... where are you in that boot process that fails ?
You have to get to the grub menu to manually manipulate that portion of the boot process or is bios not able to find the bootloader code and thus not able to hand off ?
Is grub not able to find the remainder of the booting code ? and thus no image is built ?

What results when you obtain the grub menu and arrow down in that selection menu to an older kernel version (press enter to try and boot) and attempt to boot ? -- still not forgotten we may not have head room in the /boot partition -- Trying to rule out that the kernel that you have been booting up is not "bad".


GParted: Version 10.04 will serve fine just to have a looksee at the partitioning layout;
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]Terminal commands -from the liveCD:[/COLOR][COLOR=#000000]
[/COLOR]```

sudo fdisk -lu ##from live CD<-disk info
sudo parted -l ##from live CD<-disk info
sudo parted /dev/sda unit s print ##from liveCD<-disk info

```[COLOR=#000000] will reveal additional info.
[/COLOR][INDENT=2][COLOR=#000000]
why it is called a "booting" process, don't cha know[/COLOR][/INDENT]

---

### Post by trekguy on 2013-06-05
The thing is, there just isn't much to go on.  If I just push the power button, and do nothing else...not much happens.  A few seconds of nothing, then the error message appears, and it's done.

When I repeat-press the down arrow immediately after pushing the power button, nothing much happens again, then out of nowhere, the grub list appears.  It looks different...there are colors, and it's quite a bit smaller.  On my personal Ubuntu machine, I get a couple of screens of "stuff" happening... checks, etc.... then the Grub list appears...10 seconds later, it boots the top item on the list.

I read that Grub legacy and Grub2 do not get along, and shouldn't be installed at the same time.  Synaptic shows grub(common) installed, and also grub2(common).  Could that be the problem?  I hesitate to do anything without asking because I have gotten into trouble just trying stuff.  :-)   

??

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]trekguy; Shhessh ... not much as you say to go on....

let us "presume" that bios can not hand off to grub, because grub is either corrupted or non existent... 
I have a try for fix for that situation.... need to know _.
How many hard drives are installed on the box -
what is the hard drive that is set as 1st boot priority and is that disk the same disk as ubuntu is insalled on -
And Now a biggy, we will need a liveDVD for the version of installed ubuntu (we gonna install grub onto the hard drive from that DVD)
and yeah, let us not mix versions !

Do you need directions for acquisition of the .iso file and howto burn as an image; to get a liveDVD ? (see the links at the top of "absolute beginners" forum for detailed guidance)
[/COLOR][INDENT][COLOR=#000000]
ubuntu + liveDVD + BackUps; we are invincible 

[/COLOR][/INDENT]

---

### Post by VMC on 2013-06-05
@[COLOR=#000000]trekguy,[/COLOR]

[COLOR=#000000]Try downloading bootinfoscript, and shows us the results so we can see all all your partitions, grub , mbr look. It will tell us a lot. See my link to acquire bootinfoscript.[/COLOR]

---

### Post by trekguy on 2013-06-05
> **Bashing-om said:**
> [COLOR=#000000]trekguy; Shhessh ... not much as you say to go on....

let us "presume" that bios can not hand off to grub, because grub is either corrupted or non existent... 
I have a try for fix for that situation.... need to know _.
How many hard drives are installed on the box -
what is the hard drive that is set as 1st boot priority and is that disk the same disk as ubuntu is insalled on -
And Now a biggy, we will need a liveDVD for the version of installed ubuntu (we gonna install grub onto the hard drive from that DVD)
and yeah, let us not mix versions !

Do you need directions for acquisition of the .iso file and howto burn as an image; to get a liveDVD ? (see the links at the top of "absolute beginners" forum for detailed guidance)
[/COLOR][INDENT][COLOR=#000000]
ubuntu + liveDVD + BackUps; we are invincible 

[/COLOR][/INDENT]


Laptop... one hard drive.  The last live disk I did was 10.04... back when they were still liveCDs lol!  I can do that... gonna take a while... my internet is sloooooooow.

---

### Post by trekguy on 2013-06-05
> **VMC said:**
> @[COLOR=#000000]trekguy,[/COLOR]

[COLOR=#000000]Try downloading bootinfoscript, and shows us the results so we can see all all your partitions, grub , mbr look. It will tell us a lot. See my link to acquire bootinfoscript.[/COLOR]

Ugh... feeling so stupid right now.  I have the bootinfoscript on the desktop.... but I don't know what to do with it. :oops:  I did select "run in terminal".... terminal flashed briefly, that's it.

---

### Post by VMC on 2013-06-05
From a terminal type the following:

```
sudo ./bootinfoscript
```

It will put the results in  a file named, **RESULTS.txt**

---

### Post by trekguy on 2013-06-05
> **VMC said:**
> From a terminal type the following:

```
sudo ./bootinfoscript
```

It will put the results in  a file named, **RESULTS.txt**


Command not found

?

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]trekguy;
bootinfoscript, GOOD way to go !
You must execute that command from the same directory as bootinfoscript is downloaded (located) in.

else. hunt up the directions to download it and use it --on this forum.
[INDENT=2]
hope this helps

[/INDENT]


[/COLOR]

---

### Post by VMC on 2013-06-05
> **trekguy said:**
> Command not found

?
Make sure your pointing to the Desktop, where you stated bootinfoscript is located. Open terminal, cd Desktop, ls, should give bootinfoscript file.

---

### Post by Dabo Ross on 2013-06-05
Just as another thing, have you tried running [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? I don't know if it will help, but it can help with most booting problems.

Also, on my system I have two windows partitions which will both boot, and both boot into the same Windows OS.

And if you can get into Ubuntu, I would suggest running 'grub-install' and 'update-grub'.

As for the packages, my system has both 'grub2-common' and 'grub-common' installed by default.
```
daboross: ~\ $ dpkg --get-selections | grep grub
grub-common					install
grub-gfxpayload-lists				install
grub-pc						install
grub-pc-bin					install
grub2-common					install
```

You can get into grub by hitting a key, but if you don't it goes into grub rescue? Do you know if you have multiple layers of grub chainloading?

---

### Post by trekguy on 2013-06-05
> **VMC said:**
> Make sure your pointing to the Desktop, where you stated bootinfoscript is located. Open terminal, cd Desktop, ls, should give bootinfoscript file.

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   733,001,727   732,592,128   7 NTFS / exFAT / HPFS
/dev/sda3         937,801,728   968,450,047    30,648,320   7 NTFS / exFAT / HPFS
/dev/sda4         733,003,774   937,801,727   204,797,954   5 Extended
/dev/sda5         733,003,776   929,384,447   196,380,672  83 Linux
/dev/sda6         929,386,496   937,801,727     8,415,232  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        60A8421FA841F456                       ntfs       SYSTEM
/dev/sda2        364AFC624AFC2073                       ntfs       
/dev/sda3        4EA808ABA808939D                       ntfs       Recovery
/dev/sda5        47e3e59e-4c1c-43f8-bee7-29050438ed47   ext4       
/dev/sda6        f9dfcf87-6d33-46b6-9ec7-5e0b8555eb68   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
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
menuentry 'Ubuntu, with Linux 3.2.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-45-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-45-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-45-generic ...'
    linux    /boot/vmlinuz-3.2.0-45-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-45-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-44-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-44-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-44-generic ...'
    linux    /boot/vmlinuz-3.2.0-44-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-44-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-43-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-43-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-43-generic ...'
    linux    /boot/vmlinuz-3.2.0-43-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-43-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-41-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-41-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-41-generic ...'
    linux    /boot/vmlinuz-3.2.0-41-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-41-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-40-generic ...'
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-39-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-39-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-39-generic ...'
    linux    /boot/vmlinuz-3.2.0-39-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-39-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-38-generic ...'
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-37-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-37-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-37-generic ...'
    linux    /boot/vmlinuz-3.2.0-37-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-37-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-36-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-36-generic ...'
    linux    /boot/vmlinuz-3.2.0-36-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-35-generic ...'
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-34-generic ...'
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-45-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux    /boot/vmlinuz-2.6.32-45-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.32-45-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    echo    'Loading Linux 2.6.32-45-generic ...'
    linux    /boot/vmlinuz-2.6.32-45-generic root=UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-45-generic
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
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 47e3e59e-4c1c-43f8-bee7-29050438ed47
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 60A8421FA841F456
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 364AFC624AFC2073
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 4EA808ABA808939D
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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
UUID=47e3e59e-4c1c-43f8-bee7-29050438ed47 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f9dfcf87-6d33-46b6-9ec7-5e0b8555eb68 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 373.657333374 = 401.211506688  boot/grub/core.img                             1
 421.718742371 = 452.817051648  boot/grub/grub.cfg                             1
 358.401268005 = 384.830431232  boot/initrd.img-2.6.32-45-generic              2
 359.410003662 = 385.913552896  boot/initrd.img-3.2.0-33-generic               1
 350.324661255 = 376.158240768  boot/initrd.img-3.2.0-34-generic               4
 430.575450897 = 462.326870016  boot/initrd.img-3.2.0-35-generic               3
 431.103282928 = 462.893625344  boot/initrd.img-3.2.0-36-generic               3
 374.613143921 = 402.237800448  boot/initrd.img-3.2.0-37-generic               1
 350.286960602 = 376.117760000  boot/initrd.img-3.2.0-38-generic               3
 375.152194977 = 402.816602112  boot/initrd.img-3.2.0-39-generic               2
 410.904521942 = 441.205370880  boot/initrd.img-3.2.0-40-generic               2
 431.628734589 = 463.457824768  boot/initrd.img-3.2.0-41-generic               3
 412.195312500 = 442.591346688  boot/initrd.img-3.2.0-43-generic               2
 399.919349670 = 429.410131968  boot/initrd.img-3.2.0-44-generic               2
 350.848175049 = 376.720359424  boot/initrd.img-3.2.0-45-generic               2
 349.978397369 = 375.786442752  boot/vmlinuz-2.6.32-45-generic                 2
 358.512439728 = 384.949800960  boot/vmlinuz-3.2.0-33-generic                  1
 350.191406250 = 376.015159296  boot/vmlinuz-3.2.0-34-generic                  2
 430.067127228 = 461.781061632  boot/vmlinuz-3.2.0-35-generic                  2
 430.836662292 = 462.607343616  boot/vmlinuz-3.2.0-36-generic                  2
 374.332756042 = 401.936736256  boot/vmlinuz-3.2.0-37-generic                  1
 410.754631042 = 441.044426752  boot/vmlinuz-3.2.0-38-generic                  1
 374.465568542 = 402.079342592  boot/vmlinuz-3.2.0-39-generic                  2
 410.367916107 = 440.629194752  boot/vmlinuz-3.2.0-40-generic                  2
 430.473384857 = 462.217277440  boot/vmlinuz-3.2.0-41-generic                  2
 412.078853607 = 442.466299904  boot/vmlinuz-3.2.0-43-generic                  1
 349.867916107 = 375.667814400  boot/vmlinuz-3.2.0-44-generic                  2
 350.434322357 = 376.275988480  boot/vmlinuz-3.2.0-45-generic                  2
 350.848175049 = 376.720359424  initrd.img                                     2
 399.919349670 = 429.410131968  initrd.img.old                                 2
 350.434322357 = 376.275988480  vmlinuz                                        2
 349.867916107 = 375.667814400  vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
```

---

### Post by trekguy on 2013-06-05
> **Dabo Ross said:**
> Just as another thing, have you tried running [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? I don't know if it will help, but it can help with most booting problems.

Also, on my system I have two windows partitions which will both boot, and both boot into the same Windows OS.

And if you can get into Ubuntu, I would suggest running 'grub-install' and 'update-grub'.

As for the packages, my system has both 'grub2-common' and 'grub-common' installed by default.
```
daboross: ~\ $ dpkg --get-selections | grep grub
grub-common					install
grub-gfxpayload-lists				install
grub-pc						install
grub-pc-bin					install
grub2-common					install
```

You can get into grub by hitting a key, but if you don't it goes into grub rescue? Do you know if you have multiple layers of grub chainloading?


Tried Boot Repair... no go.  Multiple layers of grub chainloading???   :shock:

---

### Post by QIII on 2013-06-05
Hello, trekguy!

Please enclose long string of code in code tags (click the pound sign and place your cursor between them, then paste your text).

Thanks and best wishes getting this sorted out!

---

### Post by Dabo Ross on 2013-06-05
I was just thinking that because it seemed that Grub worked if you pressed a button to get into it, but if you didn't you ended up in grub rescue.
The only times I have ever had grub rescue are when grub isn't loading, but I guess it will do that if something else isn't loading either.
I was thinking that maybe grub was booting into another grub which was failing, but with your partition scheme I guess that isn't the case.

I don't know what would be causing this, but when it has this error, is 'grub rescue' a prompt?
If you press 'tab' does it show a list of commands?

---

### Post by trekguy on 2013-06-06
> **QIII said:**
> Hello, trekguy!

Please enclose long string of code in code tags (click the pound sign and place your cursor between them, then paste your text).

Thanks and best wishes getting this sorted out!

Oops.  :oops:

---

### Post by trekguy on 2013-06-06
Ok, new developments.  It now seems, after a number of tests, that it will successfully boot up from a powered down state.  However, a restart results in a black screen hang.... sometimes there is the grub rescue prompt, and sometimes nothing but blank screen.  Weird. ?

---

### Post by Bashing-om on 2013-06-06
[COLOR=#000000]trekguy; Totally weird !

Try this for the heck of it...
power back down and shut all down ... unplug from the power source ...yeah unplug !... wait 5 minutes or so and plug up and power up.

See if clearing cmos had any effect.[/COLOR][INDENT=6][COLOR=#000000]a shot in the dark

[/COLOR][/INDENT]

---

### Post by trekguy on 2013-06-06
> **Dabo Ross said:**
> I was just thinking that because it seemed that Grub worked if you pressed a button to get into it, but if you didn't you ended up in grub rescue.
The only times I have ever had grub rescue are when grub isn't loading, but I guess it will do that if something else isn't loading either.
I was thinking that maybe grub was booting into another grub which was failing, but with your partition scheme I guess that isn't the case.

I don't know what would be causing this, but when it has this error, is 'grub rescue' a prompt?
If you press 'tab' does it show a list of commands?

Yes. it is a prompt... tab does nothing.  I can type... but don't know what to try.

---

### Post by trekguy on 2013-06-06
> **Bashing-om said:**
> [COLOR=#000000]trekguy; Totally weird !

Try this for the heck of it...
power back down and shut all down ... unplug from the power source ...yeah unplug !... wait 5 minutes or so and plug up and power up.

See if clearing cmos had any effect.[/COLOR][INDENT=6][COLOR=#000000]a shot in the dark

[/COLOR][/INDENT]

Did that just now.  Powered up fine from cold, and booted properly.  Restarted a couple of times ok... and a couple of times ended with grub rescue prompt.  ?

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]trekguy;
Other things precluded, just now getting back on this.
Bear in mind =what I do not know fills a BIG book... but, to me what we are looking at is a race condition in that the grub process is not initializing faster than that of other processes ....this is something that has "bothered" me for a spell - how to see that boot process --

I just do not have any good answers ! All I know right now to do is examine the log files and see what errors are listed in any of several log files; unfortunately there is no way to log the actual boot messages. That process now happens before there is any process started that can log it .

Else, have there been any changes to any of the files located in /etc/grub.d/ ?
```
ls -la /etc/grub.d/
``` the file date and file size will give a strong indication of "edited" files. These files (scripts) are a big part of building /boot/grub/grub.cfg . I continue to learn what happens when this file is parsed in that boot process.

I am open to any thoughts ->[INDENT=2]
where there are solutions, there are no problems[/INDENT]

[/COLOR]

---

### Post by VMC on 2013-06-07
> **trekguy said:**
> Did that just now.  Powered up fine from cold, and booted properly.  Restarted a couple of times ok... and a couple of times ended with grub rescue prompt.  ?

Is there any other information before that grub prompt. Something else above the prompt?

---

