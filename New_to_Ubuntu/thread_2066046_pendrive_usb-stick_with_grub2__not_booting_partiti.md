---
title: "pendrive usb-stick with grub2  not booting partitions on harddrive"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by ubunovice on 2012-10-03
I have a Grub2 multiboot laptop with Ubuntu 10.10 in /dev/sda6 ;  Ubuntu 9.04 in /dev/sda7  and WindowsXP in /dev/sda1 ,
both Ubuntu's and XP are booting fine.
I recently made a Grub2 multiboot usb-stick using the cookbook from pendrivelinux.com "Boot Multiple ISO from USB via Grub2 using Linux"
It works fine and I can boot several iso's that I placed on the usb.
I then tried to expand the grub.cfg on the usb-stick in order to boot the XP and Ubuntu on my laptop harddisk
I copied menuentries from the grub.cfg on my laptop and placed them in the grub.cfg on my usb-stick.
When I boot the usb-stick and select the Ubuntu 9.04 entry grub gives the following error-messages.
error:    no argument specified
error:    no such partition
error:    you need to load the kernel first
Press any key to continue,  afterwhich I am back in the grub-menu of the usb-stick
Booting XP gives similar results

For some reason I cannot boot a partiiton of my harddisk with the grub2 on my usb-stick

I am coming from grub-legacy , new to grub2 and would appreciate some help 
I have inserted the grub.cfg from my usb-stick below:

# This grub.cfg file was created by Lance [http://www.pendrivelinux.com](http://www.pendrivelinux.com)
# Suggested Entries and the suggestor, if available, will also be noted.

set timeout=300
set default=0

menuentry "Ubuntu 10.10 Desktop ISO" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Linux Mint 10 Gnome ISO" {
 loopback loop /linuxmint10.iso
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=/linuxmint10.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "DBAN ISO" {
 loopback loop /dban.iso
 linux (loop)/DBAN.BZI nuke="dwipe" iso-scan/filename=/dban.iso silent --
} 

menuentry "Tinycore ISO" {
 loopback loop /tinycore.iso
 linux (loop)/boot/bzImage --
 initrd (loop)/boot/tinycore.gz
}

menuentry "Memtest 86+" {
 linux16 /memtest86+.bin
}


## ## The following entries are copied from my grub.cfg on my laptop  ##
## ## on my laptop these entries work fine                                        ##

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ecd6-78ae
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 1db9753d-516d-464f-b007-54e19d9b3f61
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=1db9753d-516d-464f-b007-54e19d9b3f61 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}


### END /etc/grub.d/30_os-prober ###

---

### Post by oldfred on 2012-10-03
If UUIDs are correct I do not see anything wrong with your entries. Have you waited a bit to see if it boots. There seems to be a small issue where grub reports an error and then works.

The hd0 will be wrong as the boot drive is always hd0 in BIOS/grub, so then your hard drive is hd1 when using BIOS to boot flash drive. But the search by UUID should then find the correct location and work.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

You can try with hd1, to see if that makes any difference and the above instructions let you have a grub2 boot stanza that does not have to be updated with every kernel changes.

---

### Post by ubunovice on 2012-10-04
Thanks Oldfred

changing  hd0,msdosx   in   hd1,msdosx  solved the problem, I still get 
error:  no argument specified
but after hitting   ENTER    both XP and Ubuntu are booting OK

---

