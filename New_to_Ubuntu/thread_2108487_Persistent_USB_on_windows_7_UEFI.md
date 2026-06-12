---
title: "Persistent USB on windows 7 UEFI"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by ACorder on 2013-01-24
I am not completely new to linux but definitely a beginner. I've installed and uninstalled Ubuntu many times on several systems. I just like to play around with it sometimes and try to learn. This being said it would be really nice if I could manage to make a persistent live USB but to have more than just the few GB the installers allow. I tried for 3 days by piecing together information from several sources as I could not find anything that related specifically to my system. I have an Alienware X51 running Windows 64bit in UEFI not legacy. Most of the tutorials I saw for creating a persistent live USB were older and related to old BIOS systems, not the new UEFI. Perhaps I overlooked one somewhere but I could not manage to get it right. It would always just load the live version, I could never get persistence. If anyone has any solutions or links to solutions it would be greatly appreciated. Or if it can even happen at all. I know there's a 64bit live iso that works with UEFI, I could just never get the persistent side of things. 

I have a 16gb USB thumb drive. I know I could just install ubuntu directly onto it but I tried that and it was just extremely slow at everything. I also do not want to install it alongside Windows as I always end up removing Ubuntu anyways and always run into trouble in regards to restoring the MBR and removing grub. The persistent live USB is just the right thing for me if I can get it working.

---

### Post by ACorder on 2013-01-24
Also I should mention that I tried 12.04 and 12.10. My profile info says Edubuntu but that was back when i created the profile and I can't change it.. if the version matters at all

---

### Post by black veils on 2013-01-25
from what i can understand of your post, you just want to create a persistent live usb stick.. its simple. on your Windows system, install [**unetbootin**]("http://unetbootin.sourceforge.net/"), at the bottom section of the application, select your ubuntu .iso file etc. as for choosing how much space to save data, you cant use more than 4gb because all this is done on the fat32 filesystem which has a 4gb file size limit. see image for where to change amount (there are 1000mb to 1gb).

---

### Post by C.S.Cameron on 2013-01-25
If you are happy with a Persistent install, except for the size of the persistent casper-rw file, you can make persistent casper-rw and home-rw partitions of any size.

Following is a step by step using "Startup Disk Creator":

Boot Live CD.
Plug in flash drive.
Start Partition Editor, (gparted).
Create 1.5 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use any extra space for file transfers and storage)
Create a 4 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Startup Disk Creator", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finishes,
Select disk and deleted the casper-rw file.
Shutdown, remove CD, reboot.

---

### Post by C.S.Cameron on 2013-01-25
The above is getting a little dated, following is an update:

Boot Live CD or Live USB.
Plug in flash drive.
Start Partition Editor.
Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).
Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:
```

    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

### Post by ACorder on 2013-01-25
> **black veils said:**
> from what i can understand of your post, you just want to create a persistent live usb stick.. its simple. on your Windows system, install [**unetbootin**]("http://unetbootin.sourceforge.net/"), at the bottom section of the application, select your ubuntu .iso file etc. as for choosing how much space to save data, you cant use more than 4gb because all this is done on the fat32 filesystem which has a 4gb file size limit. see image for where to change amount (there are 1000mb to 1gb).


As I said I've tried the installers themselves but I would like to be able to use more than 4gb...kind of a waste to only use 4 of 16. And I know there are ways to make it work but all the ones I had found applied to systems several years ago on legacy boot systems.. Mine being uefi caused me problems.

---

### Post by ACorder on 2013-01-25
> **C.S.Cameron said:**
> The above is getting a little dated, following is an update:

Boot Live CD or Live USB.
Plug in flash drive.
Start Partition Editor.
Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).
Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:
```

    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

Thank you I will try this as soon as I get home from work and see if it works. Hopefully it does.

---

### Post by oldfred on 2013-01-25
I regularly link to previous post by C.S.Cameron for those wanting either persistent or full installs on a liveCD.

But if UEFI you may want to partition differently so you can boot from UEFI and not have to change to BIOS mode to boot.

I only have BIOS, but did create a gpt 16GB flash drive, so I know that will work. But with UEFI you need a FAT32 or  FAT16(on removeable) partition for the UEFI boot files.

While I now only have BIOS, I hope to soon build a new system that will have UEFI, so I create new drives with both a future efi partition at the beginning of the drive and a bios_grub for current BIOS use with grub2. Most live installs use syslinux and that still can be installed to the protective MBR with gpt. With that partitioning you then have a lot of flexibility on how you install. And you might want to make it a full UEFI install.

My newest 32GB flash, efi only needs to be 200MB, bios_grub should be 1MB unformated.
```
Model:   (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys

```

---

### Post by ACorder on 2013-01-25
> **oldfred said:**
> I regularly link to previous post by C.S.Cameron for those wanting either persistent or full installs on a liveCD.

But if UEFI you may want to partition differently so you can boot from UEFI and not have to change to BIOS mode to boot.

I only have BIOS, but did create a gpt 16GB flash drive, so I know that will work. But with UEFI you need a FAT32 or  FAT16(on removeable) partition for the UEFI boot files.

While I now only have BIOS, I hope to soon build a new system that will have UEFI, so I create new drives with both a future efi partition at the beginning of the drive and a bios_grub for current BIOS use with grub2. Most live installs use syslinux and that still can be installed to the protective MBR with gpt. With that partitioning you then have a lot of flexibility on how you install. And you might want to make it a full UEFI install.

My newest 32GB flash, efi only needs to be 200MB, bios_grub should be 1MB unformated.
```
Model:   (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys

```


Yeah that's where I kept running into problems...no one has steps on making a persistent live USB on UEFI since it's still so new. Especially dealing with linux since it doesn't exactly require the most up to date hardware to install. I had followed several "tutorials" many times and none of which would stay persistent. Of course me not knowing a whole lot especially about the real details of Ubuntu, just simple things, it didn't work out when I tried to just piece things together myself to make it work with UEFI and I would just rather not have it than have to switch to BIOS every time i wanted to use Ubuntu.. I will try the earlier mentioned and see if it works out. I did try a full UEFI install on the USB but it was really slow because of the slow read/write on USB drives i guess? Regardless I will continue to try different methods and I'm sure it won't be too much longer before someone has published a for sure method for UEFI live persistence.

---

### Post by oldfred on 2013-01-25
I have a full install in my 16GB flash. While not speedy it is functional. Linux caches activity into RAM so if you are reusing the same apps it does not matter where it originally came from. You do have to change a few settings to reduce writes.

---

### Post by ublondie on 2013-05-18
Hi ..

I love this info you have provided because I have been having troubles making a persistent LiveUSB with the various LiveUSB programs. The 'live' option works, but none of them are persistent. So your suggestion of making up a LiveUSB from within Ubuntu sounded perfect.

But... it's not working  :(

I am using the latest Ubuntu 13.04 desktop iso, so I don't know if that's making a difference?  I am running it from the liveUSB that I have made (that is not persistent) and I am making another LiveUSB from within Ubuntu on another flash drive.

Anyway, I am using a 16G usb flash drive for the new LiveUSB. I erased everything on it and set up the partitions as per your instructions. ...all good

You then wrote to 'unmount and re-mount' flash drive, which I did, but I couldn't create the startup disk due to an error. I unmounted the flash drive and was able to create the startup disk. ...all good

Now, you then write "go to the root folder of the LiveUSB, and enter the syslinux directory (or root directory)". Problem is that neither of these exist! ...subsequently, there also is no syslinux.cfg file (that I can find).

After some brief reading it seems that grub is used instead of syslinux (there is a 'grub' directory in the 'boot' directory of the new LiveUSB), so I'm unsure of what to do and hoping you (or somebody) might be able to help please?

I did try changing the 'grub.cfg' contents what you suggested for the syslinux.cfg file, but it didn't work. (actually wasn't expecting it to, but thought I'd give it a try anyway).

I would really love to get this working, so I'm hoping you might be able to clarify or offer some suggestions.

Thanks

---

### Post by ublondie on 2013-05-18
Sorry, my previous reply was related specifically to C.S.Cameron's earlier post (quoted below) ...


> **C.S.Cameron said:**
> The above is getting a little dated, following is an update:

Boot Live CD or Live USB.
Plug in flash drive.
Start Partition Editor.
Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).
Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:
```

    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

### Post by oldfred on 2013-05-18
Is this with a BIOS or UEFI system?

---

### Post by ublondie on 2013-05-19
With regard to creating the startup disk from Ubuntu, I'm not sure what relevance that has? My question related to the instructions set out by C.S.Cameron for creating the startup USB from within Ubuntu. I hadn't got as far as booting my computer with it yet.

Apart from that, I'm not really sure how to answer your question?

I am able to enter what looks like BIOS settings when I boot my computer (by perssing F2 on Windows 8 machine, and it stated 'SAMSUNG BIOS SETUP' at the tope of the screen). 
It has 'secure boot' option and refers to 'UEFI: Hitachi ..." hard drive in the startup/boot order

Has that given you the information you were after?

---

### Post by oldfred on 2013-05-19
If you have Windows 8 and secure boot with UEFI booting is a lot different. But creating flash drive should not be. Please start a new thread as UEFI booting is a lot different and is just about unique for everyone. Post vendor & model of system and if UltraBook as that adds to the issues.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by C.S.Cameron on 2013-05-19
Hi Ublondie:

Did you use Startup Disk Creator, (USB Creator),  to make the first Live USB? then Startup Disk Creator from within the first USB to make the second?
Does the second drive boot OK and run persistently except for the Try/Install screen?

I just tried the above instructions using 13.04 and here in a screen shot of the directories created by Startup Disk Creator and of the location of syslinux.cfg inside syslinux folder.

Cork

---

### Post by oldfred on 2013-05-19
@C.S.Cameron
I do not have UEFI yet, but if Windows 8 pre-installed system is using UEFI with gpt partitioning. You then have the added choice of booting flash drive in BIOS mode or UEFI mode, or UEFI mode with secure boot. The UEFI modes use the /boot/grub/grub.cfg file to boot. So it depends on how booting flash drive on which configuration file is used.

---

### Post by ublondie on 2013-05-20
Hi ...and thank you for replying.

OK, I have since tried going through the instructions again (a few times actually) and it is working fine except the persistent feature is still not working. 

I have been able to follow your instructions and yes, I am using the Startup Disk Creator from within Ubuntu. ...i have been interchanging two 16G USB flash drives I have. For information, I make up the 2G FAT32 partition, and then I use the remainder of the drive (12G) to make up an ext4 partition for casper-rw. 

I've just seen (from your next reply) that you don't have UEFI, so I guess that could be throwing a spanner in the works, like oldfred is suggesting?  I have disabled what's called 'Fast Startup' in the BIOS and I have turned Secure Boot off (it was previously enabled, but hasn't made any difference).

I have a couple of questions:
- Would it matter that the casper-rw partition is larger than 4G?   (I'm expecing not, but just wanted to check)
- the instructions state to 'make syslinux.cfg writable'. What exactly does that mean?  ...the file has permissions of: -rw-r--r--   I tried changing permissions through terminal using: sudo chmod but I couldn't make any changes. (I tried 666 and even 777 ie, sudo chmod 666 syslinux.cfg). I was however able to change the contents of the file using gedit.
- when I first boot from the drive, I go to make the administrator account, but it states 'account disabled' unless I make up a password. ...minor issue.

Regardless of all that, the liveUSB's work fine, except the persistent feature is still not working  :(

The boot process also doesn't sound like what you suggest it would (should) be?  ...when it starts, I get the usual 4 options: [abbreviated] Try Ubuntu, Install, OEM install, check disk. But maybe, as you say, this is using the GRUB.cfg ??  ..I have just checked the file and these are the options it contains. Interestingly, there is no mention/switch/option for 'persistent' in this file. Here are the contents of that file (I wasn't able to attach the file for some reason?):


```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
```


For info: I am using a SAMSUNG NP535U3C laptop with Windows 8 pre installed.

---

### Post by ublondie on 2013-05-20
Oh my goodness !!    ....I got it working!   :)

Ok, not that it took a whole heap of brain power, but you guys led me to where I needed to look. Thank you.

After posting the code of the 'grub.cfg' file and noting that there was no mention of 'persistent', I thought I would add it. (obviously, there would be no mention of persistent because the instructions for making up the LiveUSB, mention to not select persistent feature (ie, discard on Shutdown).

I added the word 'persistent' in the first option of the menu, after 'boot=casper' and it did the trick:

(I won't label this topic as SOLVED, as it wasn't my original post, but maybe it should be?)

Thank you oldfred and C.S.Cameron :)   (maybe you can provide an update of your instructions C.S.Cameron? I found that it was posted here also [http://ubuntuforums.org/showthread.php?t=2124124](http://ubuntuforums.org/showthread.php?t=2124124) , with reference to Windows 8 and possible UEFI system?  )

```

menuentry "Try Ubuntu without installing" {     set gfxpayload=keep     linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --     initrd    /casper/initrd.lz 
```

---

### Post by sudodus on 2013-05-20
> **ublondie said:**
> Oh my goodness !!    ....I got it working!   :)
...
I added the word 'persistent' in the first option of the menu, after 'boot=casper' and it did the trick:
...
Thank you oldfred and C.S.Cameron :)   (maybe you can provide an update of your instructions C.S.Cameron? I found that it was posted here also [http://ubuntuforums.org/showthread.php?t=2124124](http://ubuntuforums.org/showthread.php?t=2124124) , with reference to Windows 8 and possible UEFI system?  )
```

menuentry "Try Ubuntu without installing" {
     set gfxpayload=keep
     linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper [COLOR=#ff0000]persistent[/COLOR] quiet splash --
     initrd    /casper/initrd.lz
}
 
```

Congratulations :KS

I'll just add a few tips and comments.

- In a standard USB 2 pendrive, the flash hardware is usually slower than the USB interface. So if you get a USB 3 pendrive, it will be much faster in a USB 3 port, but it will also be significantly faster in a USB 2 port.

- It could be useful to add a menuentry without persistence (everything else being the same) to get a quick-boot basic live system.

- I prefer an installed system (installed into a USB 3 pendrive) to a persistent live system because it can be updated and upgraded like any installed system. Lubuntu has a light foot-print and suits well for this purpose. But persistent live systems are flexible and useful for many situations.

---

### Post by C.S.Cameron on 2013-05-20
Hi Ublondie:

After Oldfred's reply I noticed that the computer I was using was set to Legacy boot, duh.

The latest version of UNetbootin, 583, sets up an UEFI Live system ok.
But as you say it is not Persistent out of the box.

There are several places where adding " persistent" will make the system look for casper-rw and home-rw when booting.
text.cfg, txt.cfg, grub.cfg and syslinux.cfg, depending if the Flash drive was made using Startup Disk Creator or UNetbootin.

Yes, you can make the casper-rw partition as large as the drive will hold and you can also have a separate home-rw partition.
By make writable I meant edit as su.

I will rewrite the step by step as you suggest, and keep my eye out for a new method to remove try/Install, Thanks.

Cork

---

### Post by ublondie on 2013-05-20
> **sudodus said:**
> Congratulations :KS

I'll just add a few tips and comments.

- In a standard USB 2 pendrive, the flash hardware is usually slower than the USB interface. So if you get a USB 3 pendrive, it will be much faster in a USB 3 port, but it will also be significantly faster in a USB 2 port.

- It could be useful to add a menuentry without persistence (everything else being the same) to get a quick-boot basic live system.

- I prefer an installed system (installed into a USB 3 pendrive) to a persistent live system because it can be updated and upgraded like any installed system. Lubuntu has a light foot-print and suits well for this purpose. But persistent live systems are flexible and useful for many situations.

I am using USB 3 pendrives which I think is a good idea.

I did also read about doing a complete install of Ubuntu on the flash drive, but read that it wouldn't be so good for them because of the frequent writing to the memory??

Either way, at least I've got it working now which I'm happy with.

---

### Post by sudodus on 2013-05-20
Yes, a complete install will write more to its root partition than a persistent system will write to its casper-rw file/partition. We should add the mount option [SIZE=3]**[FONT=courier new]noatime[/FONT]**[/SIZE] into /etc/fstab for the root partition in order to reduce wear due to (unnecessary) writing.

It is true, that a flash drive will wear faster than a HDD, [s][COLOR=#696969]and pendrives have no built in methods to spread the wear like SSDs[/COLOR][/s]. So we have an extra reason to make regular backups ;-)

But the flash drives last quite long nowadays. I have not worn out any of mine yet.

-o-

Inspired by your efforts and success *[[COLOR=#000000]ublondie[/COLOR]]("http://ubuntuforums.org/member.php?u=894157")*, I'm starting to figure out a way to make a boot USB pendrive, that should work for most (intel-amd) computers. I'm thinking of a choice with one 32-bit iso file and one 64-bit iso file (the latter for UEFI systems). I don't know enough to tell yet, if it is possible or not. I'm afraid some new computers are too locked for such a system anyway, but I would like a system that can boot most computers without switching from UEFI or other changes in the BIOS menus.

---

### Post by C.S.Cameron on 2013-05-20
Most good flash drives do have wear leveling, see link below.
I figure if you do the math based on a life of 10000 writes at 10MB/s a 16GB drive will last years of normal use.
[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

Following creates a Persistent USB install of *buntu, usable on both Legacy and UEFI systems, Thanks Ublondie:

Boot Live 64 bit CD, (or 64 bit Live USB).
Plug in flash drive.
Start Partition Editor

Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use excess to move files between computers)
Create a 1.5 - 31 GB ext2 partition to the right of this, label it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.

Un-mount and re-mount flash drive.

Start "Startup Disk Creator".
Select "Discard on shutdown".
Press "Make Startup Disk.
When Startup Disk Creator finishes,

Edit Boot/grub.cfg by adding "<space>persistent" as shown below:

```
file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
```

Next

Replace the contents of syslinux.cfg with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```


Shutdown, remove CD/USB, reboot.

---

### Post by sudodus on 2013-05-21
Thank you *[C.S.Cameron]("http://ubuntuforums.org/member.php?u=317145")* for writing up this short tutorial to make  a Persistent USB install of *buntu, usable on both Legacy and UEFI systems.

And the link about levelling in pendrives was nice reading :-)

---

### Post by ubfan1 on 2013-05-26
There is a bug (1159016) which the persistent USB's don't have persistence when booted on a UEFI machine.  There is a workaround in the bug for editing the grub.cfg file's linux lines, adding the word "persistent".

---

### Post by timjavins on 2013-05-26
> **ubfan1 said:**
> There is a bug (1159016) which the persistent USB's don't have persistence when booted on a UEFI machine.  There is a workaround in the bug for editing the grub.cfg file's linux lines, adding the word "persistent".

Are you saying that the bug is fixed by adding "persistent" to grub.cfg in the appropriate place?

---

### Post by C.S.Cameron on 2013-05-26
> **timjavins said:**
> Are you saying that the bug is fixed by adding "persistent" to grub.cfg in the appropriate place?

To get persistence in UEFI mode you need to add the word "persistent" to grub.cfg per post 24 above.

To get persistence in non UEFI mode you can overwrite syslinux.cfg per post 24 above.

---

### Post by sudodus on 2014-03-26
> **C.S.Cameron said:**
> Most good flash drives do have wear leveling, see link below.
I figure if you do the math based on a life of 10000 writes at 10MB/s a 16GB drive will last years of normal use.
[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

Following creates a Persistent USB install of *buntu, usable on both Legacy and UEFI systems, Thanks Ublondie:

Boot Live 64 bit CD, (or 64 bit Live USB).
Plug in flash drive.
Start Partition Editor

Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use excess to move files between computers)
Create a 1.5 - 31 GB ext2 partition to the right of this, label it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.

Un-mount and re-mount flash drive.

Start "Startup Disk Creator".
Select "Discard on shutdown".
Press "Make Startup Disk.
When Startup Disk Creator finishes,

Edit Boot/grub.cfg by adding "<space>persistent" as shown below:

```
file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
```

Next

Replace the contents of syslinux.cfg with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```


Shutdown, remove CD/USB, reboot.

An alternative to a persistent live system is a portable installed system. I made an Ubuntu wiki page describing how to make a
portable installed system that boots in UEFI as well as BIOS mode. See this link

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

This is a portable installed system that boots in UEFI as well as BIOS mode. It can be installed into a USB pendrive and is a good alternative to a persistent live system, because it can be updated and upgraded without limits.

It is uploaded and available at this web page

[http://phillw.net/isos/linux-tools/uefi-n-bios](http://phillw.net/isos/linux-tools/uefi-n-bios)

The method described and the 'final product' as a compressed image file work for me in a Toshiba notebook according to the following specification.

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w)

I don't know how specific or portable it is until tested in other computers with UEFI.

I think the method is more important than the 'final product' in this case, and it will be interesting to find out how portable it is.

---

### Post by nehaljw-kkd1 on 2014-04-27
Using [Win32 DiskImager]("http://http://sourceforge.net/projects/win32diskimager/files/latest/download") is preferred if you have to make the USB live media compatible with both, UEFI and Legacy Modes. 
Proof: [https://www.youtube.com/watch?v=XoINdNWVgYo](https://www.youtube.com/watch?v=XoINdNWVgYo)

---

### Post by oldfred on 2014-04-27
@nehaljw-kkd1
You have a broken link to Win32 DiskImager.
That looks like another way to use Windows to create a standard 64 bit Ubuntu install flash drive. 
The Ubuntu install flash drive is dual boot for either UEFI or BIOS.

Link above by sudodus is for a full install to a larger flash drive, not an installer.

But rather than reformatting the Ubuntu installer, I strongly suggest you keep it as a repair disk or have another DVD or flash drive that is bootable so you can boot if you have hard drive issues.
Same with Windows, it is vital to have a Windows repair flash drive as Windows may not always boot or start to boot and let you into its repair console. Then you really can only easily fix Windows if you have a Windows repair flash drive.

---

### Post by madarada on 2015-03-23
Cameron, your way to fix it do the trick for me.
I now trying desperately to make my casper-rw partition to be encrypted .
impossible to get there.
Ideally I would like to build a Live Usb persistent and encrypted.

I tried to create a partition directly from the console with luks encryption like that:

cryptsetup --verbose --verify-passphrase luksFormat /dev/sdbx
cryptsetup luksOpen /dev/sdbx mount_usb
mkfs.ext3 -L casper-rw /dev/mapper/mount_usb
e2label /dev/mapper/mount_usb casper-rw
cryptsetup luksClose /dev/mapper/mount_usb

the thing is that on the boot Linux just do not ask me the password to open the partition as it is not recognise as the main partition.
(sorry for my poor english. Hope to be clear).
Thanks in advance for the help..! ;)

---

### Post by howefield on 2015-03-24
Hello madarada, you would most likely be better starting your own thread.

---

### Post by sudodus on 2015-03-24
If you want an encrypted system I suggest that you make an installed system with 'Encrypted disk'. 'Encrypted home' is buggy: cryptswap does not work, and normal swap is a security hole.

You can make an installed system in a USB pendrive.

I am not sure if it is possible to make an encrypted persistent live system. But a normal live system is good, because nothing is saved (if no swap is used). Then you can save files in an encrypted folder in a writable partition (but maybe not encrypted casper-rw).

-o-

But I agree with *howefield*, please start an own thread with a good descriptive title and link to it here (so that we find it easily).

---

