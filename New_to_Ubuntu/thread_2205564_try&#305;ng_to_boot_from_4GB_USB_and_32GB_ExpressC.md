---
title: "try&#305;ng to boot from 4GB USB and 32GB ExpressCard"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by Phil_Buckley on 2014-02-14
Hi Team,
Excuse my limited knowledge of Linux jargon. 
I have a Lat&#305;tude XT laptop on which the HD died. 
I was hoping to install Lubuntu 13.10 to boot from a 4GB USB st&#305;ck with the main file system on a 32 GB ExpressCard SSD. (The Bios does not support booting from the ExpressCard slot)
I booted a live disc session using a second (2gb) usb stick.
I installed using the Advanced Partitioning Tool and created a ext4 partition on the SSD (currently /dev/sdb1 from a Live Disc) a Swap drive (/dev/sdb2) and selected the USB (/dev/sdc1) for the boat loader. All went well.

However the boot process hangs with a message I am shortening to: 

ALERT! /dev/disk/by-uuid/[COLOR=windowtext][FONT=Calibri]230cae17-5b48-411c-be5a-08469f94e7fb[/FONT][/COLOR] does not exist

and drops to a shell.  

I suspect that either:
1. when I remove the the second (2GB) stick that the device names change and that I need to change something in /etc/fstab (or another file which contributes to /grub/grub.cfg) or
2. I need to add something to the boot routine which initiates and/or mounts the ExpressCard SSD
but now I am stuck!

I tried boot-repair but it did not solve the issue. [Here is the report it generated]("http://paste.ubuntu.com/6931792/"). 

Below I append what I hope is relevant info...it feels like I am a short step away from achieving what I set out to do!

TIA for any help

Phil

These are the results of sudo blkid

[COLOR=#222222][FONT=arial]/dev/loop0: TYPE="squashfs" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sda1: SEC_TYPE="msdos" UUID="B8A1-FD1F" TYPE="vfat" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/zram0: UUID="a6753c92-d13e-4bdb-915f-[/FONT][/COLOR][COLOR=#222222][FONT=arial]36faac7f51e5" TYPE="swap" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/zram1: UUID="cda16c39-69db-425a-a2af-[/FONT][/COLOR][COLOR=#222222][FONT=arial]40caf0abea08" TYPE="swap" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sdb1: UUID="230cae17-5b48-411c-be5a-[/FONT][/COLOR][COLOR=#222222][FONT=arial]08469f94e7fb" TYPE="ext4" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sdb2: UUID="5a14e3bc-6aea-43be-ac90-[/FONT][/COLOR][COLOR=#222222][FONT=arial]2934369b5971" TYPE="swap" [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sdc1: UUID="c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81" TYPE="ext4" 

Here are the contents of etc/fstab
[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]#[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]#[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# / was on /dev/sdb1 during installation[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]UUID=230cae17-5b48-411c-be5a-[/FONT][/COLOR][COLOR=#222222][FONT=arial]08469f94e7fb /               ext4    errors=remount-ro 0       1[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# /boot was on /dev/sdc1 during installation[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]#UUID=c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81 /boot           ext4    defaults        0       2[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]# swap was on /dev/sdb2 during installation[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]UUID=5a14e3bc-6aea-43be-ac90-[/FONT][/COLOR][COLOR=#222222][FONT=arial]2934369b5971 none            swap    sw              0       0[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]UUID=c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81    /boot    ext4    defaults    0    2

[/FONT][/COLOR]

---

### Post by oldfred on 2014-02-14
I know I had issues installing from one flash to another but I have several drives and assumed that was the issue.

The set root command is a default and old way. But then the search by UUID is supposed to override an incorrect set root if drive number or order has changed.

When you boot the boot device is always hd0 and then other drives will be in whatever order BIOS has enumerated them. 

You can try from grub menu change hd1 setting to hd0 and edit out entire search line.
If you do not get grub menu as you only have one install, hold shift key from BIOS until menu appears. 

If you cannot get menu then we may have to edit the file we never are supposed to edit or grub.cfg.

---

### Post by Phil_Buckley on 2014-02-15
Thank you oldfred fo your prompt and useful reply. 

As  I am new to th&#305;s it took me a while to work out what you meant. I guess that you meant to use the "e" option to edit lines during boot as a temporary workaround to see if the names od devices were somehow mixed up. So this is what I did, namely: "grub menu change hd1 setting to hd0 and edit out entire search line". But no joy.
As far as I can tell fstab is pointing to the correct device and, as you say, using a unique identifier should banish the chance of a rogue enumeration.
My guess is that I need to add something (a *module* ? perhaps ) to grub via one of the files that builds grub.cfg to get grub to recognise the ExpressCard because it feels like (although linux kernel can see it) grub cannot see the drive (as it is not listed in the machine's bios).
Can you point me in the right direction.
My lack of familiarity with the correct terms means my searches online are not very helpful!

---

### Post by oldfred on 2014-02-15
I just may be that BIOS does not enumerate Express card, so it cannot be seen until system boots and adds its driver. Or you have a chicken & egg issue.

Is /boot on a drive that BIOS sees. That should work if kernel can load first.

One other way may be plop. But I thought it worked by loading kernel on BIOS available device and then loading rest of system.
 Sometimes plop will work.
[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by Phil_Buckley on 2014-02-16
Sorry for the delay in replying oldfred.
In answer to your question:

No /boot is on the unseen drive. However that folder is empty. 
Just /grub & some system files are on the the 4GB USB drive that boots and gets me into Grub2.

I found this:

[I got Grub2 to recognize my express card by using the --disk-module=ata during install. ]("http://ubuntuforums.org/showthread.php?t=1458718")

Could be this what I need to do. I have no idea how to go  about adding the module. Or into which file and where I should add the  line of code...

Thanks for your continuing patience
P

---

### Post by oldfred on 2014-02-16
Not sure if grub mod file, boot parameter or compile kernel switch.

There is a ata.mod file in /boot/grub, so you can add that to the grub.cfg file with insmod command to load a module.
There also are several usb.mod files for different things. I have never fully understood what each mod file does, but they all are add-ins to grub to make it work with different special configurations.

[http://www.gnu.org/software/grub/manual/html_node/insmod.html#insmod](http://www.gnu.org/software/grub/manual/html_node/insmod.html#insmod)
 [http://blog.fpmurphy.com/2010/06/grub2-modules.html?output=pdf](http://blog.fpmurphy.com/2010/06/grub2-modules.html?output=pdf)

---

### Post by Phil_Buckley on 2014-02-17
Thanks again oldfred.
I'm afraid the concepts you mention "grub mod file, boot parameter or compile kernel switch" are beyond me. Is it bad form to ask in the forum where I saw user [**[COLOR=#000000]LaferriereJC[/COLOR]**]("http://ubuntuforums.org/member.php?u=512729") say that they had achieved [what it is I think I need to do]("http://ubuntuforums.org/showthread.php?t=1458718")?

---

### Post by oldfred on 2014-02-17
At the grub boot stanza when editing with an e, you should see these.

insmod gzio
insmod part_msdos
insmod ext2


I might try adding one or more insmod like this:
insmod ata

Or any of the other modules that may help. It just is I have not found any documentation on all the modules and what exactly each does. Most have names that are self explanatory.

---

### Post by Phil_Buckley on 2014-02-20
I am getting a little warmer, oldfred...

[I found this]("http://www.davidfong.info/suse_notes/node321.html") in which the author seems to have done what I am trying to do. I edited grub.cfg directly (I know you're not supposed to do but I could not work out which file to edit prior to running grub-update AND I didn't know whether that command would update the grub on my live session or the one on my boot d&#305;sc-to-be!

I had noticed that [COLOR=#222222][FONT=arial]*vmlinuz-3.11.0-12* and [/FONT][/COLOR][COLOR=#222222][FONT=arial]*initrd.img-3.11.0-12-generic* were actually on the bootable 4GB drive [/FONT][/COLOR]and that on the root of 27 GB Volume (the one that the kernel can see but that the PC bios & Grub cannot) there were just symbolic links back to the files on the 4GB drive. 

So I altered this bit of grub.cfg to actually look for them on the boot (rather than look for the symbolic link on a drive grub couldn't see). 
The UUID of the 27 GB is: [COLOR=#222222][FONT=arial]230cae17-[/FONT][/COLOR][COLOR=#222222][FONT=arial]5b48-411c-be5a-08469f94e7fb
The UUID of the 4 GB is: [/FONT][/COLOR][COLOR=#222222][FONT=arial]c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81 
I changed one reference to the 27 GB to that of the 4GB [/FONT][/COLOR]([COLOR=#ff0000]marked in red[/COLOR] below)[INDENT][COLOR=#222222][FONT=arial]menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-230cae17-[/FONT][/COLOR][COLOR=#222222][FONT=arial]5b48-411c-be5a-08469f94e7fb' {[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]recordfail[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    load_video[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    gfxmode $linux_gfx_mode[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod gzio[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod part_msdos[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod ext2[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    set root='hd2,msdos1'[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    if [ x$feature_platform_search_hint = xy ]; then[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    else[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]      search --no-floppy --fs-uuid --set=root c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    fi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    linux    /vmlinuz-3.11.0-12-generic root=UUID=[/FONT][/COLOR][COLOR=#ff0000][FONT=arial]c7897920-3a02-4c80-[/FONT][FONT=arial]a232-e7a519d74a81[/FONT][/COLOR][COLOR=#222222][FONT=arial] ro   quiet splash $vt_handoff[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    initrd    /initrd.img-3.11.0-12-generic[/FONT][/COLOR]

Now on boot Grub only shows 1 entry (namely "Ubuntu") (so I have probably broken grub.cfg) with the following commands only:
[/INDENT]
[INDENT][COLOR=#222222][FONT=arial]recordfail[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    load_video[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    gfxmode $linux_gfx_mode[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod gzio[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod part_msdos[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    insmod ext2[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    set root='hd2,msdos1'[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    if [ x$feature_platform_search_hint = xy ]; then[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    else[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]      search --no-floppy --fs-uuid --set=root c7897920-3a02-4c80-a232-[/FONT][/COLOR][COLOR=#222222][FONT=arial]e7a519d74a81[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    fi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    linux    /vmlinuz-3.11.0-12-generic root=UUID=c7897920-3a02-4c80-[/FONT][/COLOR][COLOR=#222222][FONT=arial]a232-e7a519d74a81 ro   quiet splash $vt_handoff[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    initrd    /initrd.img-3.11.0-12-generic[/FONT][/COLOR]
[/INDENT]

It does however seem to starting loading the kernel...it fails at:[INDENT]mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found: Try passing init=bootarg
[/INDENT]
Then drops to a shell..


Thanks for any further help you can give
P
PS Sorry. Should have mentioned that I did try your suggestions (and variations)  in the previous post but to no avail

---

### Post by oldfred on 2014-02-20
When I create custom entries I go the other way and just keep it simple.

        I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

      
 Using 40_custom & Custom menu
[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]https://help.ubuntu.com/community/Grub2/CustomMenus
[/URL]
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]
[/URL]

---

