---
title: "fedora 9"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by stunningman on 2008-08-27
i was having windows xp(sda1) on my system later on i dual booted it with ubuntu 8.04(sda3) then i installed fedora 9(sda12) now the problem is the grub loader of fedora shows windows option and boots as well but the ubuntu thing is not shown,so i reformatted the fedora thing and again installed it.this time while installing fedora it asked of other OS and i added ubuntu 8.04(sda3) to it,now it shows ubuntu thing in grub option but do not load it,showing some chained error .what is the problem.please help

---

### Post by mellowd on 2008-08-27
some chained error?

It would help if you put the full error here

---

### Post by stunningman on 2008-08-27
yes error no 13

---

### Post by stunningman on 2008-08-28
i have earlier installed fedora 9 with windows xp and i can see both option pretty well on grub.now i installed ubuntu 8.04 in a new partition the grub loader shows ubuntu 8.04 and windows xp,but the fedora 9 option is missing from the grub list.my fedora partition is still there on my harddisk but no fedora booting option can be seen on system start.please help

---

### Post by cariboo on 2008-08-28
What happened is that by installing Ubuntu grub defaults to the that installation, so you will probably have to edit your /boot/grub/menu.lst manually to add Fedora. One other option is to install Startup Manager, and add Fedora to your start up list. You can install startupmanager using Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by stunningman on 2008-08-28
how to edit and what to write in /boot/grub/menu.lst please explain in detail.
thanx

---

### Post by WRDN on 2008-08-28
To edit the menu.lst file, open the Terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

I believe that you need to add the entry for Fedora 9 after the "### END DEBIAN AUTOMAGIC KERNELS LIST" line near/ at the bottom of the file.

The entry for Fedora should look like this:

> 
title Fedora 9
[B]root (hd0,5)
kernel /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=e6672330-aade-4730-b266-f00b8113da3d ro quiet splash
initrd /boot/initrd-2.6.25-14.fc9.i686.img[/B]
quiet


You will probably need to edit the lines in bold.

To find the device Fedora is located on, type:

```
sudo blkid
```

You can now change "root (hd0,5)" to the appropriate disk and partition. The 0 in the line above refers to the first disk, and the 5 refers to the fourth partition (you start counting from 0).
When you enter the "sudo blkid" command, the output will contain the devices, in the format: /dev/sdaN or /dev/hdaN (where N represents a number). The letter "a" in sda/hda refers to the first disk, "b" would refer to the second disk etc. The number after is refers to the partition.

Once you have found the correct partition, you may want to mount it:

```
sudo mkdir /media/fedora
```

Then:

```
sudo mount /dev/[device] /media/fedora
```

Now, navigate to the boot directory, and change the name of the kernel/ initrd images accordingly. The UUID must also be changed- this information is given in the blkid command.

---

### Post by stunningman on 2008-08-28
asking this last time........... please help adding fedora 9 to grub list showing ubuntu 8.04 and windows xp on my system startup.i am unable to boot fedora.
i am fed up with this community nobody is willing to help open heartedly.

---

### Post by stunningman on 2008-08-28
please explain this

Code:

sudo mkdir /media/fedora

Then:

Code:

sudo mount /dev/[device] /media/fedora

Now, navigate to the boot directory, and change the name of the kernel/ initrd images accordingly. The UUID must also be changed- this information is given in the blkid command.
__________________

"my fedore partition is on sda12"

---

### Post by phidia on 2008-08-28
Sorry that you have had bad experiences here.

When you installed fedora how did you have it install the boot loader or did you opt not to?

You can open /boot/grub/menu.lst with a text editor you're comfortabel with and add the correct title and boot entries. You didn't give your partition specifics but there are menu.lst examples [here]("http://www.syrlug.org/contrib/grub-examples.txt"). 

You could also get the [super grub disk]("http://www.supergrubdisk.org/") and use that to update the grub you have.

---

### Post by WRDN on 2008-08-28
> **stunningman said:**
> please explain this

Code:

sudo mkdir /media/fedora

Then:

Code:

sudo mount /dev/[device] /media/fedora

Now, navigate to the boot directory, and change the name of the kernel/ initrd images accordingly. The UUID must also be changed- this information is given in the blkid command.
__________________

"my fedore partition is on sda12"


Sure.

This creates a folder as the mount point. When you mount the partition, you navigate to this folder to view the files.

```
sudo mkdir /media/fedora
```

If you have other partitions mounted (other than the Filesystem), then you can navigate to /media in Nautilus, and view the folders that act as mount points. (click Places > Computer > Filesystem and open the "media" folder).

```
sudo mount /dev/[device] /media/fedora
```

This is the code for mounting the disk. To find the device, type "sudo blkid" or "sudo fdisk -l" in the Terminal.

When I type "sudo fdisk -l", this is my output:

> Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93109310

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13212   106125358+   7  HPFS/NTFS
/dev/sda3           13213       14946    13928355    5  Extended
**/dev/sda5           13213       14791    12683254+  83  Linux**
/dev/sda6           14792       14855      514048+  82  Linux swap / Solaris
/dev/sda7           14856       14946      730926   83  Linux


If I wanted to mount /dev/sda3 in the fedora folder, I would type:

```
sudo mount /dev/sda3 /media/fedora
```

"/dev/sda3" is the partition to mount, and "/media/fedora" is the mount point.

Once the partition Fedora is installed on has been mounted, you can navigate to the mount point (/media/fedora, or select the partition in Places > Computer). Now, navigate to the boot folder (/media/fedora/boot). In here, you will find the kernel and initrd images. Now, change the menu.lst entry for Fedora to suit. 

Here is example information that may be found for Fedora:

- Partition = /dev/sda3
- Kernel image = vmlinuz-2.6.24-19-generic
- Initrd image = initrd.img-2.6.24-19-generic
- UUID = 90ea8561-1dc6-4bb6-86bf-4ec61513e6cc

The UUID is found using the "sudo blkid" command in the Terminal.

Using this information, the entry you placed in the menu.lst file would look like this:

> title Fedora 9
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=90ea8561-1dc6-4bb6-86bf-4ec61513e6cc ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet 

---

### Post by Irony on 2008-08-28
Well, it would help if you wrote in a concise manner rather pidgin.

First post your current grub menu.lst.

All you do is add to your current entries like this;

```
timeout 20
color black/cyan yellow/cyan
default 0

title		Heron sda5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Fedora sdb2
root		(hd1,1)
kernel		/boot/vmlinuz-1.1.11-fedora root=/dev/sdb2 ro splash
initrd		/boot/initrd.img-1.1.11-fedora
quiet

title		Windows XP hda1
root		(hd0,0)
makeactive
chainloader	+1
```

To determine the actual entry rather than my example entry you will have to navigate your way to the /boot folder in Fedora and write down the actual link. You would also have to determine where you have installed Fedora. In this example Fedora is installed in sdb2, i.e. my second hard disk partition 2.

---

### Post by bobnutfield on 2008-08-28
If you will mount your Fedora partition in Ubuntu, navigate to the Fedora /boot directory, and make a note of the EXACT name of the file vmlinuz and the EXACT name of the initrd.img file, then exit the Fedora mount and open a terminal in Ubuntu and type:

> sudo fdisk -l

and post this information back, I will give you the exact entry to add to your /boot/grub/menu.lst file to get Fedora to boot.  The vmlinuz file will look something like the following:

vmlinuz-2.6.25.14-108.fc9.i686

and the initrd will look something like:

initrd-2.6.25.14-108.fc9.i686.img

To be able to give you the exact entry, this information must be correct.

---

### Post by stunningman on 2008-08-28
after doing what you said i restarted the system it showed "error no.17 cannot mount the partition"

---

### Post by WRDN on 2008-08-28
Please post the output of "sudo fdisk -l", "sudo blkid" and the entry you added to the menu.lst file.

---

### Post by stunningman on 2008-08-28
output of sudo fdisk -l:-


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbdffbdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       34347   234934560    f  W95 Ext'd (LBA)
/dev/sda3           34348       38415    32676210   83  Linux
/dev/sda4           38416       38913     4000185   82  Linux swap / Solaris
/dev/sda5            5100        8754    29358756    b  W95 FAT32
/dev/sda6            8755       12409    29358756    b  W95 FAT32
/dev/sda7           12410       16064    29358756    b  W95 FAT32
/dev/sda8           16065       19719    29358756    b  W95 FAT32
/dev/sda9           19720       23374    29358756    b  W95 FAT32
/dev/sda10          23375       27029    29358756    b  W95 FAT32
/dev/sda11          27030       30688    29390886    b  W95 FAT32
/dev/sda12          30689       30701      104391   83  Linux
/dev/sda13          30702       34347    29286463+  8e  Linux LVM


output of sudo blkid:-
/dev/sda1: UUID="6690086090083957" TYPE="ntfs" 
/dev/sda3: UUID="7df69c8f-0c18-49bf-bb9e-58bfc827b001" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="18b46175-4c11-4e39-840b-e89f3da0c58c" 
/dev/sda5: LABEL="GAMES" UUID="8870-3DCF" TYPE="vfat" 
/dev/sda6: LABEL="SOFTWARE" UUID="6087-6975" TYPE="vfat" 
/dev/sda7: LABEL="MUSIC" UUID="708A-D019" TYPE="vfat" 
/dev/sda8: LABEL="MOVIE" UUID="C09E-362D" TYPE="vfat" 
/dev/sda9: UUID="9CB0-393E" TYPE="vfat" 
/dev/sda10: UUID="4CBC-EAE2" TYPE="vfat" 
/dev/sda11: UUID="BF26-79E5" TYPE="vfat" 
/dev/sda12: LABEL="/boot" UUID="65e64752-d28a-41f7-a8ea-b01d71962ca1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: UUID="P2JKMB-rAHa-ezzp-vvbM-8iHE-psP1-FlyAnK" TYPE="lvm2pv" 

fedora is in /dev/sda12
and ubuntu in /dev/sda3

---

### Post by stunningman on 2008-08-28
the entry on menu.lst
title           Fedora 9
root            (hd0,12)
kernel          /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=65e64752-d28a-41f7-a8ea-b01d71962ca1 ro quiet splash
initrd          /boot/initrd-2.6.25-14.fc9.i686.img
quiet

---

### Post by WRDN on 2008-08-28
Please could you post the contents of the /boot folder on the Fedora partition. To do this, just open the Terminal, navigate to the boot folder (cd /media/fedora/boot) and type "ls". Then post the output here. Thanks.

---

### Post by WRDN on 2008-08-28
> **stunningman said:**
> the entry on menu.lst
title           Fedora 9
root            (hd0,12)
kernel          /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=65e64752-d28a-41f7-a8ea-b01d71962ca1 ro quiet splash
initrd          /boot/initrd-2.6.25-14.fc9.i686.img
quiet

Change "root (hd0,12)" to "root (hd0,11)" and it should boot properly. You must start counting from 0, so the first drive (sd[COLOR="RoyalBlue"]a[/COLOR]) is "0" and the 12th partition is "11".

---

### Post by Herman on 2008-08-28
:) Hello stunningman,
You had GRUB error 13 because you tried to chainload Ubuntu by the boot sector but Ubuntu's boot sector is empty.
You should install Ubuntu's GRUB to the first sector of your Ubuntu partition (boot sector) - [Grub error 13]("http://users.bigpond.net.au/hermanzone/p15.htm#13").

I'm not sure exactly what commands you'll need to use in Fedora, but in Ubuntu we would use,
```
sudo grub
``````
find /boot/grub/stage1
``````
root (hdx,y)
``````
setup (hdx,y)
``````
quit
```Where: x = the hard drive number in GRUB's numbering system (counting from 0), and y = the partition number for Ubuntu, also counting from 0).

Here is a link you might find informative on the subject of multi booting, [Operating System Entries for Multiple Booting More Linux Systems.]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards, Herman :)

---

### Post by stunningman on 2008-08-28
cd /media/fedora 
syscore@syscore-desktop:/media/fedora$ dir
config-2.6.25-14.fc9.i686      lost+found
efi			       System.map-2.6.25-14.fc9.i686
grub			       vmlinuz-2.6.25-14.fc9.i686
initrd-2.6.25-14.fc9.i686.img

there is no /boot folder as you can see above

---

### Post by WRDN on 2008-08-28
Have you tried changing the root line, as outlined in post 12?

---

### Post by stunningman on 2008-08-28
yes but it is mounting my vfat partition

---

### Post by stunningman on 2008-08-28
please tell what could be the problem

---

### Post by stunningman on 2008-08-28
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7df69c8f-0c18-49bf-bb9e-58bfc827b001 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7df69c8f-0c18-49bf-bb9e-58bfc827b001 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7df69c8f-0c18-49bf-bb9e-58bfc827b001 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Fedora 9
root            (hd0,11)
kernel          /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=65e64752-d28a-41f7-a8ea-b01d71962ca1 ro quiet splash
initrd          /boot/initrd-2.6.25-14.fc9.i686.img
quiet 

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by cariboo on 2008-08-28
> title Fedora 9
root (hd0,12)
kernel /boot/vmlinuz-2.6.25-14.fc9.i686 root=UUID=65e64752-d28a-41f7-a8ea-b01d71962ca1 ro quiet splash
initrd /boot/initrd-2.6.25-14.fc9.i686.img
quiet

Could just not paste the above quoted lines into your /boot/grub/menu.lst
and have everything work. If you made a backup of menu.lst first maybe you should use that.

Jim

---

### Post by WRDN on 2008-08-28
I'm not sure if it will make a difference, but try moving the location of the Fedora 9 entry. First, try putting it with the Ubuntu entries (above the "### END DEBIAN AUTOMAGIC KERNELS LIST" line). Otherwise, put it after the entry for Windows XP, at the bottom of the file.

---

### Post by cariboo on 2008-08-28
Did your fedora installation actually work, because from your file listing their doesn't look to be any config or system files.

Jim

---

### Post by caljohnsmith on 2008-08-28
> **stunningman said:**
> cd /media/fedora 
syscore@syscore-desktop:/media/fedora$ dir
config-2.6.25-14.fc9.i686      lost+found
efi			       System.map-2.6.25-14.fc9.i686
[COLOR="Red"]grub	[/COLOR]		       vmlinuz-2.6.25-14.fc9.i686
initrd-2.6.25-14.fc9.i686.img

there is no /boot folder as you can see above
Since you all ready have Grub installed in Fedora, an easy way to load Fedora is to just link to its menu.lst/grub.conf. Just add the following entry to your Ubuntu's menu.lst:
```
Title   Fedora
root    (hd0,11)
configfile /grub/[COLOR="Blue"]menu.lst[/COLOR]
```
You might have to change menu.lst to grub.conf--I don't know which Fedora uses. Just check in that /grub directory that you show in the above quote. Let me know how it goes.

---

### Post by cariboo on 2008-08-28
See this post as it is the same problem by the same poster:

[http://ubuntuforums.org/showthread.php?t=903580](http://ubuntuforums.org/showthread.php?t=903580)

stunningman ou shouldn't double post.

Jim

---

### Post by caljohnsmith on 2008-08-28
Please do not start two threads about the same problem/topic, stunningman. That is not considerate of those who offer their help, because they may be duplicating each others efforts. See your [other thread]("http://ubuntuforums.org/showthread.php?t=903580") for the newest replies, and I encourage anyone else who wants to reply to use the other thread.

---

### Post by bobnutfield on 2008-08-28
The entry above (post #21) should work for you, but if it does not, try this:

> 
title Fedora 9
root (hd0,11)
kernel /boot/vmlinuz-2.6.25-14.fc9.i686 root=/dev/sda12 ro quiet splash
initrd /boot/initrd-2.6.25-14.fc9.i686.img
quiet

I have in the past had difficulties when using UUID's in my menu.lst file when booting multiple distros from the same drive.  I have never had a problem with specifiying the partition

---

### Post by stunningman on 2008-08-28
contents of /boot folder
it came after i typed 
sudo mount /dev/sda12 /media/fedora


/media/fedora/efi
/media/fedora/grub
/media/fedora/lost+found
/media/fedora/config-2.6.25-14.fc9.i686
/media/fedora/initrd-2.6.25-14.fc9.i686.img
/media/fedora/System.map-2.6.25-14.fc9.i686
/media/fedora/vmlinuz-2.6.25-14.fc9.i686

---

### Post by caljohnsmith on 2008-08-28
Stunningman, this is your triple post on the exact same problem. To anyone who cares to help, I would encourage you to use [this thread]("http://ubuntuforums.org/showthread.php?t=903580").

---

### Post by bobnutfield on 2008-08-28
If Fedora is installed on sda12, try the entry I posted above BELOW the line that says END OF DEBIAN in the menu.lst file.  That entry will boot it, or the entry from post #21.

---

### Post by stunningman on 2008-08-28
eureka eureka IT WORKED.
Title   Fedora
root    (hd0,11)
configfile /grub/menu.lst

thanx to everybody who have given time for this problem.

---

### Post by stunningman on 2008-08-28
since fedora9 is running please help me setup a broadnband internet connection.

---

### Post by jpeddicord on 2008-08-28
Merged a whole bunch of threads.

Stunningman: If you need help with Fedora 9, the best place to get help would be at a Fedora forum, not here.
[http://www.fedoraforum.org/](http://www.fedoraforum.org/)

---

### Post by mellowd on 2008-08-29
> **jacobmp92 said:**
> Merged a whole bunch of threads.

Stunningman: If you need help with Fedora 9, the best place to get help would be at a Fedora forum, not here.
[http://www.fedoraforum.org/](http://www.fedoraforum.org/)

Quite possibly he created 5 threads there too...

---

