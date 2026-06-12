---
title: "Woes: single-user maintenance vs. booting ISO images (10.04)"
date: 2010-06-06
forum: Programming Talk
---

### Post by sdaau on 2010-06-06
Hi all, 

Well, very often, especially after a new install, I bump into some sort of a non-fatal hard disk problem; "non-fatal" meaning that the system can still boot, but OS/programs can recognize something being wrong with the disk. 

Then, the usual next step is to check the root partition with **fsck**; and the usual way to do it is to run [fsck on next boot](http://ubuntuforums.org/showthread.php?t=1024771); however, then fsck runs as a part of the boot process, and as such, the user does not really have many options to intervene in the fsck process (and I still haven't figured out in which file are the results of the fsck logged, when it runs as part of boot process). 

Then, especially if you're an old Windows convert, the next logical step would be to "boot to DOS" :) or, in Ubuntu's case, use the ["maintenance mode"](http://ubuntuforums.org/showthread.php?t=857486) or ["Single User Mode"](http://www.uluga.ubuntuforums.org/showthread.php?p=909978) or ["recovery mode"](http://ubuntuforums.org/showthread.php?t=384482): for systems with legacy grub, one would press Esc at boot -  and for Grub 2, one would press [Shift](http://art.ubuntuforums.org/showthread.php?t=1320180) - and then choose the appropriate option in the Grub menu. 

However, in this case we have a sort of a chicken-and-egg situation; even single-user mode must mount the root partition and boot from it - and fsck can only run safely on unmounted partitions :) And so, it is reasonable to think that even in "single-user" mode, it would be unsafe to run fsck on root partition, as discussed in [Is it safe to fsck the / partition from single user mode/recovery mode?](http://ubuntuforums.org/showthread.php?t=1039698) and [how to go in single user mode in ubuntu and how to fsck ?](http://ubuntuforums.org/showthread.php?t=785219). 

Since it is not safe to run fsck on a mounted partition, the next suggestion is usually to boot from a "live" medium, such as a LiveCD or a live USB; in that case the usual root partition will not be mounted, and so fsck can be run on it. *However*, as it goes with Murphy's Law, usually when you *do* need to run fsck on the root partition, one of the following turns out to be true:
[LIST]
[*]You have a LiveCD or LiveUSB, but the version of the live OS does not match version of installed OS
[*]You have a LiveCD, but no CD-ROM drive (think netbooks)
[*]You have a LiveUSB, but the BIOS won't recognize it
[*]You do not have a LiveCD or LiveUSB, and it is not possible to obtain one quickly on the spot (no Internet access, no available media). 
[/LIST]
or in other words - *no way you'll get a live medium booted when you need it* (especially if its purpose is to run fsck) :)

At this point, I start remembering that the [GRUB for DOS](http://gna.org/projects/grub4dos/) bootloader actually had the capability to  [boot ISO images in RAM](http://partedmagic.com/documentation/124-grub4dos-iso-booting.html); the only other bootloader I know of that can do the same is Grub2 ([boot an ISO via Grub2](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)).

__________________________________________________________________

With that in mind, it makes sense to me to spend, say, 50 MB of the root harddisk on a scaled down Linux ISO, that I could boot from the hard-disk into RAM - an in that way leave the root partition free for fsck'ing (in case of non-fatal problems).

So, now I ended up having that situation with a new netbook, with Ubuntu 10.04 installed, which by default installs GRUB2, and formats the root partition as ext4 - so I decide to give this method a try; and below are the results. 

__________________________________________________________________


First of all, I start thinking - there must be some Ubuntu ISO which represents a minimal command-line system. If you want to install an **Ubuntu CLI system** there are basically two options:  
[LIST]
[*] [Alternate installer CD](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate) - this has an option to install both CLI and desktop ubuntu systems; has copies of packages included and so image size is about 600 MB 
[*] [Minimal CD Image](https://help.ubuntu.com/community/Installation/MinimalCD) - same as Alternate installer, except packages are downloaded from the net and so image size is about 15 MB
[/LIST]
Note, for one, that these images [cannot be used as LiveCd/Usb](http://help.ubuntu.com/community/LiveCD). In addition, they are  *installer* images: so even if we boot, say, the minimal ISO to RAM, we'd get an installer - *_not_* a shell that would allow us to run fsck :) However, unlike the LiveCD, they would allow the CLI version of Ubuntu to be installed on a target system.

So after some searching, I find an unofficial **[Ubuntu Mini Remix](http://www.crealabs.it/ubuntu-mini-remix/)** ISO image, 155 MB in size - that simply boots into a command-line installation of Ubuntu. A bit more that the 50 MB I hoped for, but the heck with it - I give it a try; and 
[LIST]
[*]Good thing is that there is 10.04 version (so the tools should be compatible with the root OS)
[*]Bad thing is - grub2 cannot boot it (fails with "*stdin: error 0*" and "*Unable to find a meduim containing a live file system*")
[/LIST]

Duhhhh...... :-?  As it says in [HOWTO to boot Feisty from an isoimage saved on the harddisk (fromiso patch)](http://ubuntuforums.org/showthread.php?t=457318) (via [Boot ISO from HD using GRUB2?](http://ubuntuforums.org/showthread.php?t=1357942)):

> **Jose Catre-Vandis said:**
> _I can see it working with Live Cds, but it would be different with alternate Ubuntu CDs as there is no casper._ I have tried some editing within initrd.gz on alternates but the installation stalls on bootstrap-base, giving errors about release names. Can't see where this is looking though, as it finds the release and cd name earlier on.

Well, since this points that it could end up quite difficult rolling out a Ubuntu CLI image that would be bootable directly from Grub2, I thought I'd better see if I get luckier with some other distros....

__________________________________________________________________

....
[SIZE="1"]The first bump I had here, was due to the change to Grub2: in legacy Grub, one would edit [menu.lst](http://www.gnu.org/software/grub/manual/grub.html#Configuration) (and the same goes for [Grub4dos](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)); in Grub2, there is "[no longer Grub's familiar menu.lst. The main Grub 2 instruction file is now grub.cfg. This file is produced by various scripts run when either the 'update-grub' or 'update-grub2' command is executed.](http://wiki.ubuntu.com/Grub2#Grub%202%20Files%20&%20Folders)."

That means, to add additional boot options for Grub2, you need to create a script (which would then output lines corresponding to old menu.lst into the config file, when update-grub is ran). The script I used (with plenty of commented failures :) ) is included below.. [/SIZE]
...

__________________________________________________________________


As start for other distro search, I find the blog post **[10 Best Minimal / Low-Footprint Linux distros](http://blog.taragana.com/index.php/archive/10-best-minimal-low-footprint-linux-distros/)** from Feb 2010, so I decide to give this list a try.

In brief: from those 10 offered, I tried only 5 (that I found would be theoretically bootable) - and from those, only 2 (*slitaz* and *tinycore*) actually can boot. 

[LIST=1]
[*] DamnSmallLinux [FONT="Courier New"]dsl-4.4.10[/FONT] (50M) - just reboots if loaded with 'linux'; with 'linux16' it starts booting but kernel panics during mount of root system; same behaviour for normal or initrd iso, or for embedded zip.  
[*] Puppy Linux [FONT="Courier New"]lupu-501.iso[/FONT] (129M) - Fails with "*lupu-501.sfs not found*"
[*] [FONT="Courier New"]microcore_2.11.2.iso[/FONT] (6,3M) - Fails with "*Cannot open root device <NULL> or unknown -block(0,1) ... Please append a correct root= boot option; here are the available partitions: sda1, sda2.... Kernel panic - unable to mount rootfs..*"
[*] [FONT="Courier New"]slitaz-3.0-3in1.iso[/FONT] (30M) - _boots fine_ to cli (user 'tux', no password) - running 'su' first, then entering 'root' as root password, allows for 'fdisk -l' to work.. but there is _no fsck_ in the installation (and it also fails booting the GUI part)
[*] [FONT="Courier New"]tinycore_2.11.2.iso[/FONT] (11M) - _boots fine_ to GUI, fdisk -l runs, there is no fsck but there is fsck.ext2 and fsck.ext3 
[/LIST]

So, in my context of 10.04 ext4, the following can be said of the only two working images:
[LIST]
[*] [FONT="Courier New"]slitaz[/FONT] does not offer fsck at all
[*] [FONT="Courier New"]tinycore[/FONT] does not offer fsck for ext4
[/LIST]

... or in other words - *none* of these images are usable for purposes of running fsck on a root partition of Ubuntu 10.04, which is ext4 !

Duhhhh...... :-?  not really luckier with other distros 

__________________________________________________________________


To **conclude**: Currently, there seem to be *no viable options* for booting a command-line Linux ISO directly to RAM from Grub2, for the purposes of fsck'ing an ext4 root partition of Ubuntu 10.04. 

Of course, if anyone knows better than that conclusion, I'd love to hear about it! :) 

The only thing remaining, is for one to try, and roll out their own customized ISO, that represents a command-line Ubuntu system; noting that there are different guides, depending on what kind of Ubuntu ISO one is customizing (see [LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)). [Ubuntu Customization Kit](https://launchpad.net/uck) should help with rolling your own customized ISO, but I didn't find anything that would facilitate making a command-line 'live' ISO like [Ubuntu Mini Remix](http://www.crealabs.it/ubuntu-mini-remix/) (*Ubuntu Customization Kit* seems to be focused around localization stuff from the usual Live CDs). 


However, as noted above, there could be other obstacles for creating a live CLI version.. Which is why, eventually, I'm very hopeful about [this](http://www.murga-linux.com/puppy/viewtopic.php?p=311535#311535):

> **floborg said:**
> 
...
the forthcoming woof-Puppy is supposed to support booting from the ISO directly.
...


where '[woof](http://puppylinux.org/wikka/Woof)' would be:

[quote=http://puppylinux.org/wikka/Woof]
'For a long time I have dreamt of a "magical script" that could download packages of some other distro, cut them right down to Puppy-size, then build a Puppy Linux live-CD -- and do all of this totally automatically.'
Woof, the Puppy builder
[/quote]

Now, if that ends up working - also for Grub2 booting the ISO of a command-line Ubuntu system - that would, indeed, rock ! [noparse]:D[/noparse]

Ah well, I guess that is it - I will appreciate any comments on the topic; additionally, the grub2 script for testing the ISOs I used can be found below. 


Cheers! 


__________________________________________________________________


Save the below as file [FONT="Courier New"]/etc/grub.d/11_ubuntu_ramdisk[/FONT] (and then, you might have to [FONT="Courier New"]chmod +x[/FONT] it first, and afterwards run [FONT="Courier New"]sudo update-grub[/FONT]):
```

### BEGIN /etc/grub.d/10_linux ###
# taken from /boot/grub/grub.cfg
#~ menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	#~ recordfail
	#~ insmod ext2
	#~ set root='(hd0,1)'
	#~ search --no-floppy --fs-uuid --set ccd52b25-16c1-4aec-9be5-1283ed1c9507
	#~ echo	'Loading Linux 2.6.32-21-generic ...'
	#~ linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ccd52b25-16c1-4aec-9be5-1283ed1c9507 ro single
	#~ echo	'Loading initial ramdisk ...'
	#~ initrd	/boot/initrd.img-2.6.32-21-generic
#~ }
#
# the below message shows only when running "sudo update-grub2"
echo "Adding Custom - Ubuntu Ramdisk ISOs" >&2
#
# for ubuntu, see also
# [http://ubuntuforums.org/showthread.php?t=457318&page=6 HOWTO to boot Feisty from an isoimage saved on the harddisk (fromiso patch) - Page 6 - Ubuntu Forums]
#
#
# NOWORK:
#~ cat << EOF
#~ menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery RAMDISK)' --class ubuntu --class gnu-linux --class gnu --class os {
	#~ recordfail
	#~ insmod ext2
	#~ set root='(hd0,1)'
	#~ search --no-floppy --fs-uuid --set ccd52b25-16c1-4aec-9be5-1283ed1c9507
	#~ echo	'Loading Linux 2.6.32-21-generic ...'
	#~ linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ccd52b25-16c1-4aec-9be5-1283ed1c9507 ro single load_ramdisk=1
	#~ echo	'Loading initial ramdisk ...'
	#~ initrd	/boot/initrd.img-2.6.32-21-generic
#~ }
#~ EOF

# this one boots - but is just an installer, has no shell to speak of.
#~ cat << EOF
#~ menuentry 'Ubuntu 10.04 mini ISO (recovery RAMDISK)' --class ubuntu --class gnu-linux --class gnu --class os {
	#~ recordfail
	#~ insmod ext2
	#~ set root='(hd0,1)'
	#~ echo	'Loading Ubuntu 10.04 mini ISO ...'
	#~ loopback loop (hd0,1)/boot/mini1004.iso
	#~ linux	(loop)/linux iso_filename=/boot/mini1004.iso boot=cli load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
	#~ echo	'Loading initial ramdisk ...'
	#~ initrd	(loop)/initrd.gz
#~ }
#~ EOF

# boot=live fails here, even though the default in the isolinux/text.cfg in the image is actually labeled live.
# boot=casper starts booting, but fails with "stdin: error 0" and "Unable to find a meduim containing a live file system"
cat << EOF
menuentry 'Ubuntu 10.04 mini remix ISO (cli RAMDISK)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading Ubuntu 10.04 mini ISO ...'
	loopback loop (hd0,1)/boot/ubuntu-mini-remix-10.04-i386.iso
	linux	(loop)/casper/vmlinuz iso_filename=/boot/ubuntu-mini-remix-10.04-i386.iso boot=casper toram nopersistent load_ramdisk=1 prompt_ramdisk=0 --
	echo	'Loading initial ramdisk ...'
	initrd	(loop)/casper/initrd.lz
}
EOF
# for other linux ISOs
#dsl-4.4.10.iso -
#[all variants] Boot ISO from HD using GRUB2? - Ubuntu Forums - http://ubuntuforums.org/showthread.php?t=1357942
# "Like, i managed to boot ubuntu 9.10,9.04,8.04, Puppy linux 4.21, Qimo(ubuntu again), but dsl just refuses to boot."
#~ cat << EOF
#~ menuentry 'dsl-4.4.10.iso (just reboots)' {
	#~ recordfail
	#~ insmod ext2
	#~ set root='(hd0,1)'
	#~ echo	'Loading dsl-4.4.10.iso ...'
	#~ loopback loop (hd0,1)/boot/dsl-4.4.10.iso
	#~ linux	(loop)/boot/isolinux/linux24 iso_filename=/boot/dsl-4.4.10.iso ramdisk_size=100000 init=/etc/init BOOT_IMAGE=knoppix lang=us apm=power-off vga=normal
	#~ echo	'Loading initial ramdisk ...'
	#~ initrd	(loop)/boot/isolinux/minirt24.gz
#~ }
#~ EOF
#
#DSL-initrd - http://www.damnsmalllinux.org/wiki/index.php/Maintenance_Toram_Install
#  direct iso also reboots again if using linux
# with linux16 - http://phorum.study-area.org/index.php?topic=58984.0 - starts booting, complains of root= missing
# VFS: Cannot open root device "" or 03:02 ; Please append a correct "root=" boot option ; Kernel panic: VFS: Unable to mount root fs on 03:02 (also RAMDISK driver initialized: 16 RAM disks)
# for root=/dev/ramdisk or root=/dev/ram - FAT: bogus logical sector size 0 ; Kernel Panic: VFS: Unable to mount root fs on 01:00
# also: http://www.damnsmalllinux.org/f/topic-3-5-6503-5.html "I think I have had similar problems too - unable to mount root on fs 03:01.  Im not sure what fixed it but I think it was that i changed the harddisk in the BIOS from LBA to standard/normal and then remade the partitions using fdisk in cyclinder mode. I remember all using fdisk to rewrite a dos FAT."
# also: http://www.linuxquestions.org/questions/damnsmalllinux-42/help-with-hikarunix-dsl-509759/: "your trying to install it locally on a usb or HDD and have not made a linux partion for it or not using an embeded version of DSL (or the mod doesnt support embeding)"
cat << EOF
menuentry 'dsl-4.4.10-initrd.iso (kernel panic)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading dsl-4.4.10-initrd.iso ...'
	loopback loop (hd0,1)/boot/dsl-4.4.10-initrd.iso
	linux16	(loop)/boot/isolinux/linux24 iso_filename=/boot/dsl-4.4.10-initrd.iso ramdisk_size=100000 init=/etc/init ro lang=us toram noeject frugal ramdisk_start=0 load_ramdisk=1 prompt_ramdisk=1 nomce noapic apm=power-off BOOT_IMAGE=knoppix --
	echo	'Loading initial ramdisk ...'
	initrd	(loop)/boot/isolinux/minirt24.gz
}
EOF
#
# with unpack as in http://www.damnsmalllinux.org/wiki/index.php/Maintenance_Toram_Install
# ...xcept used /boot as dst here...
# ...xcept it still (just reboots): "Uncompressing linux... ok, booting the kernel - similarly, disappears before you can read it, and the computer reboots." [all variants] DamnSmall fails to boot after GRUB auto setup - Ubuntu Forums - http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1394944
# linux16 - http://phorum.study-area.org/index.php?topic=58984.0 - starts booting, complains of root= missing
cat << EOF
menuentry 'dsl-4.4.10-initrd.iso unpack (kernel panic)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading dsl-4.4.10-initrd.iso ...'
	linux16	/boot/dsl/boot/isolinux/linux24 ramdisk_size=100000 init=/etc/init ro lang=us toram noeject frugal
	echo	'Loading initial ramdisk ...'
	initrd	/boot/dsl/boot/isolinux/minirt24.gz
}
EOF
# DSL embed zip: cd /boot/dsl; unzip ../../*embedded.zip
# BOOT_IMAGE=KNOPPIX/KNOPPIX - Kernel Panic: VFS
# root=KNOPPIX/KNOPPIX
cat << EOF
menuentry 'dsl-4.4.10-embedded.zip unpack (kernel panic)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading dsl-4.4.10-initrd.iso ...'
	linux16	/boot/dsl/linux24 ramdisk_size=100000 init=/etc/init ro lang=us toram noeject frugal root=/boot/dsl/KNOPPIX/KNOPPIX --
	echo	'Loading initial ramdisk ...'
	initrd	/boot/dsl/minirt24.gz
}
EOF
#lupu-501.iso
#http://murga-linux.com/puppy/viewtopic.php?p=424116&sid=b3a6ae09078ff94a0cc0e89aa5a57b87 ... pmedia=cd psubdir=puppy ramdisk_size=100000 load_ramdisk=1 pfix=ram psubdir=(loop)/ iso_filename=/boot/lupu-501.iso
# Booting Puppy from iso using Grub2 - http://www.murga-linux.com/puppy/viewtopic.php?t=43104
# set root='(hd0,1)'
# http://www.linuxquestions.org/questions/puppy-71/cant-get-puppy-to-work-with-grub2-805371/ "me thinks he is trying to boot an hard drive iso using grub2 .. In which case you may like to peruse..... http://sidux.com/index.php?module=Wikula&lang=en&tag=Grub2isofrom"
#~ cat << EOF
#~ menuentry 'lupu-501.iso' {
	#~ recordfail
	#~ insmod ext2
	#~ echo	'Loading lupu-501.iso ...'
	#~ loopback loop (hd0,1)/boot/lupu-501.iso
	#~ linux	(loop)/vmlinuz
	#~ echo	'Loading initial ramdisk ...'
	#~ initrd	(loop)/initrd.gz
#~ }
#~ EOF
cat << EOF
menuentry 'lupu-501.iso unpack (lupu-501.sfs not found)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading lupu-501.iso unpack ...'
	linux	/boot/lupu-501/vmlinuz pfix=ram psubdir=boot/lupu-501
	echo	'Loading initial ramdisk ...'
	initrd	/boot/lupu-501/initrd.gz
}
EOF
#microcore_2.11.2.iso
# for root=/dev/ram0, getting "No filesystem could mount root, tried: ext3, ext2, cramfs iso9660 fuseblk; Kernel Panic..."
# else: "Cannot open root device <NULL>" or unknown -block(0,1) . Pease append a correct root= boot option; here are the available partitions: sda1, sda2.... Kernel panic - unable to mount rootfs.."
cat << EOF
menuentry 'microcore_2.11.2.iso (Kernel panic;unable to mount rootfs)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading microcore_2.11.2.iso ...'
	loopback loop (hd0,1)/boot/microcore_2.11.2.iso
	linux	(loop)/boot/bzImage iso_filename=/boot/microcore_2.11.2.iso root=/dev/ram0 ramdisk_size=100000 max_loop=256
	echo	'Loading initial ramdisk ...'
	initrd	(loop)/microcore.gz
}
EOF
#slitaz-3.0-3in1.iso
cat << EOF
menuentry 'slitaz-3.0-3in1.iso slitaz3 (u:tux,rp:root)' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading slitaz-3.0-3in1.iso ...'
	loopback loop (hd0,1)/boot/slitaz-3.0-3in1.iso
	linux	(loop)/boot/bzImage iso_filename=/boot/slitaz-3.0-3in1.iso ramdisk_size=100000 rw root=/dev/null vga=normal autologin
	echo	'Loading initial ramdisk ...'
	initrd	(loop)/boot/rootfs3.gz
}
EOF
#tinycore_2.11.2.iso
cat << EOF
menuentry 'tinycore_2.11.2.iso' {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	echo	'Loading tinycore_2.11.2.iso ...'
	loopback loop (hd0,1)/boot/tinycore_2.11.2.iso
	linux	(loop)/boot/bzImage iso_filename=/boot/tinycore_2.11.2.iso ramdisk_size=100000 max_loop=256
	echo	'Loading initial ramdisk ...'
	initrd	(loop)/boot/tinycore.gz
}
EOF
# some testing remains (ignore): sudo apt-get remove uck lupin-casper qemu
### END /etc/grub.d/10_linux ###

```

---

### Post by pete_m on 2010-06-10
Interesting stuff . . I've had some joy with grub 2 booting from USB - both iso's n upacked LiveCDS . .tho no luck with Ubuntu or Mint nor my own remastersys image that V'box had liked
( iwhile Vbox had not liked the Lucid one for what it may be worth )

the grub on my main drive i allowed to be over-written when attempting an upgrade - but cld post my grub.cfg from the stick if the loopback n such cmds might be useful.  .

i'm a bit out of my depth n the problem seems to be round casper as far as booting the ubuntu-based iso's
tiny core works fine from sio and i can see all my disks -
writing this on a Sid-based eb4 system booted from the stick . .

 is ext4 so essential ? - it may be the default for lucid 
but lucid seemd happy enough to use the existing partition when i did a subseuently aborted install from the ubuntu tools and didn't moan bout filesystms during tthe upgrade . .

i giess the problem of single user running fsck on root drive remains anyway - perhaps there is some classic Unix technique for dealing with just that problem 
( p'haps a temporary unmount - while single fsck process executes ). .in which case the approriate ext4 code won't be there n you'd have to roll yr own.  .

---

### Post by curaga on 2010-07-11
Couple points on Tiny Core:

- it boots to ram natively anyway, no need to use tricks like that
- the 3.x series supports ext4, 3.0 rc1 just out

Extract bzImage and tinycore.gz from the iso, add a normal grub entry, voila. :)

---

