---
title: "GRUB overwrites the MBR on my internal hard drive"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by stevsurf on 2008-10-09
My BIOS cannot boot an external USB disk.

I have installed Ubuntu 8.04 on a USB external drive and created a bootable CDROM containing GRUB. 

Unfortunately, every time I use the CDROM to boot Ubuntu, GRUB over writes the MBR on my internal Hard disk, which should boot to Windows XP.

How can I prevent the MBR of my internal hard disk from being overwritten when the CDROM is used to boot Ubuntu on the USB external disk?

---

### Post by Het Irv on 2008-10-09
So wait, let me get this straight...

You have a CD containing GRUB that you boot to when you want to go to Ubuntu, and one of the entries points to your external drive.

The problem is when you use the CD it Overwrites your internal hard Drive's MBR, making it so that you cannot boot into Windows.

Did I get that right?
Where Did you get the GRUB CD?

---

### Post by vanadium on 2008-10-09
That is normal behaviour. I am not sure whether you can specify during the installation where to put the grub master boot record. What does work, certainly, is to physically disconnect your primary hard disk during your attempt to install Ubuntu on an USB.

---

### Post by WWSmith36 on 2008-10-09
By default grub installs itself to the MBR of the primary drive.  If you use the ubuntu alternate install CD, you will be allowed a choice of where you want to install grub.  Therefore you can choose to install it to your external drive instead.

If you have already installed ubuntu then,

You can restore windows MBR to your internal drive by booting windows install CD to Recovery Console and using the fixmbr command.
Then you can use the Ubuntu LiveCD to install grub to your external drive.
This will make it so that your internal drive is ¨untouched¨ by linux, and also allow to boot linux from you external.

Hope this helps

---

### Post by Nepherte on 2008-10-09
You should be able to put grub somewhere else than the MBR of the first disk during the installation process. Ideas that come to mind: other disks, floppy, usb stick, ...

---

### Post by issih on 2008-10-09
I'm confused, lets see if we can clarify things

You have installed ubuntu onto an external usb drive.
Presumably you have windows on your internal drive.

Unfortunately your bios is not capable of booting a usb drive, in which case installing grub on the external drive is of no use to you.

You state you have created a bootable cd, what do you mean by this? are you talking about the ubuntu live cd iso, because if its that you are not booting the install that exists on the usb drive at all, and you are actually just booting the live cd distribution of ubuntu, if you then went through the installation steps I can see how your internal disks mbr would be getting over writen, as that is the ubuntu installers default behaviour.

If you mean you have properly created a boot cd (i.e. one containing the standalone eltorito specification of grub and a copy of the linux kernel so that the kernel can be booted to the cd and then redirect the filesystem to the usb drive with the booted kernel handling the usb subsystem) then I have no idea how you grub can be doing anything like that.

Please clarify exactly what is installed where, and what exactly this boot cd is. Also what happens if you boot the computer normally with out the usb drive and without a cd?

---

### Post by stevsurf on 2008-10-10
> **Het Irv said:**
> So wait, let me get this straight...

You have a CD containing GRUB that you boot to when you want to go to Ubuntu, and one of the entries points to your external drive.

The problem is when you use the CD it Overwrites your internal hard Drive's MBR, making it so that you cannot boot into Windows.

Did I get that right?
Where Did you get the GRUB CD?

Yes That is correct.

I made the GRUB CDROM by following the instructions:
Booting the kernel from a bootable CD on this web page
[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

---

### Post by stevsurf on 2008-10-11
> **issih said:**
> I'm confused, lets see if we can clarify things

You have installed ubuntu onto an external usb drive.
Presumably you have windows on your internal drive.

Unfortunately your bios is not capable of booting a usb drive, in which case installing grub on the external drive is of no use to you.

You state you have created a bootable cd, what do you mean by this? are you talking about the ubuntu live cd iso, because if its that you are not booting the install that exists on the usb drive at all, and you are actually just booting the live cd distribution of ubuntu, if you then went through the installation steps I can see how your internal disks mbr would be getting over writen, as that is the ubuntu installers default behaviour.

If you mean you have properly created a boot cd (i.e. one containing the standalone eltorito specification of grub and a copy of the linux kernel so that the kernel can be booted to the cd and then redirect the filesystem to the usb drive with the booted kernel handling the usb subsystem) then I have no idea how you grub can be doing anything like that.

Please clarify exactly what is installed where, and what exactly this boot cd is. Also what happens if you boot the computer normally with out the usb drive and without a cd?

Yes, the GRUB CDROM contains eltorito and was created using the instructions: 
Booting the kernel from a bootable CD on this web page
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

After using the boot CDROM my computer will not boot with or without the USB drive and I have to use a floppy disk to boot to Windows and re-create the MBR in my hard drive.

---

### Post by Keen101 on 2008-10-11
That is a weird situation.

a possible solution might be to copy the /boot folder from your external drive to your internal drive, then install the GRUB bootloader on your internal one, and edit the copied /boot/grub/men.lst file to boot Windows (by default), and also boot the external Ubuntu.... but, i've never done anything like that before... it should be possible...

---

### Post by stevsurf on 2008-10-12
> **Keen101 said:**
> That is a weird situation.

a possible solution might be to copy the /boot folder from your external drive to your internal drive, then install the GRUB bootloader on your internal one, and edit the copied /boot/grub/men.lst file to boot Windows (by default), and also boot the external Ubuntu.... but, i've never done anything like that before... it should be possible...


I am reluctant to put GRUB on my Windows hard disk.  
The whole idea of a CDROM booting Ubuntu on a USB drive was that it was portable to any computer without affecting the boot up of the operating system already on it.

---

### Post by hellion0 on 2008-10-12
Since your machine doesn't want to boot from the external drive, GRUB may be a neccesary evil. You can edit it to work silently, however... a keypress will allow you to select the OS (if the external is hooked up), and if there's none, it'll just boot to Windows after a few seconds.

I think, anyway. Your scenario is one I've never tried.

---

### Post by meierfra. on 2008-10-12
Could you post  the file "menu.lst" from your boot cd?

---

### Post by stevsurf on 2008-10-12
> **meierfra. said:**
> Could you post  the file "menu.lst" from your boot cd?

Here is my menu.lst

```
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
timeout		10

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
# kopt=root=UUID=3cbfb8da-d650-4f59-bd11-6e5d6ab393ad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 
root		(cd)
kernel		/boot/vmlinuz root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img
quiet

title		Ubuntu Recovery Mode
root		(cd)
kernel		/boot/vmlinuz root=/dev/sdb1 ro single
initrd		/boot/initrd.img


### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by issih on 2008-10-12
First of all, assuming you have fixed the mbr so that windows bootloader should be in place, can you then boot windows as normal? Just want to be sure that the mbr has actually been repaired, and that you aren't just managing to boot windows via a floppy/cd, but never actually repairing the mbr.


Assuming that you have already checked that, my best guess is that as you have copied the whole of menu.lst from the normal ubuntu install, somehow the updategrub script is being run, although I still can't see how that would install grub...I thought it just modified the menu.lst file.

---

### Post by meierfra. on 2008-10-12
menu.lst looks fine. I still cannot believe that your MBR actually gets overwritten.

 Can you tell us  exactly what happens when you try to boot XP after you booted from CDrom drive? 
Does the grub menu appear? 
If yes, is it the grub menu from the CDrom drive?
Do you get any error messages? 
Are you trying to boot XP, while the Boot CD is in CD drive?

---

### Post by stevsurf on 2008-10-12
> **meierfra. said:**
> 
 Can you tell us  exactly what happens when you try to boot XP after you booted from CDrom drive? 


If the USB hard disk is turned on when the computer is booted without the Ubuntu boot CDROM in the drive, the black window with the Windows XP logo displays. The screen then goes completely black and the light on the USB disk flashes for well over a minute. Eventually, the disk light on the internal hard drive begins to flash and Windows boots!

So, it does work after all and the hard disk MBR is not overwritten after all!.:):)

It all arises from my being impatient!  As you will have gathered my computer is old, which is why it won't boot a USB disk. But, not only that, the USB ports are USB1.1 and the External USB disk can work from a USB 2 port.

If I make sure that the USB external disk is switched off when the computer boots, Windows boots at the usual speed.

Thank you everyone for trying to help a newbie like me.  Also, it was a comfort to know that my menu.lst file was OK.

I am now a great Ubuntu fan!

---

