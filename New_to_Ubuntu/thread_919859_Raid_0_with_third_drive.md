---
title: "Raid 0 with third drive"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by nuubun2user on 2008-09-14
I have just went through a several day process of trying to get ubuntu installed on my system.  As of last night I finally have it running, I tell you this so that you know I am completely new and slightly overwhelmed.

So here is the situation. I have 2 sata 250 gig hard drives that run as a raid 0.  I have a third drive that is an IDE drive that I have installed Ubuntu on (750 gigs). If I configure the bios to boot into my raid drive, I will get the option to select ubuntu or windows however if I select ubuntu I get several errors.

Here is my guess as to why. My raid is a software raid, ubuntu doesn't recognize the software raid and is looking to either install or run ubuntu from SDA1 (what I think is my first hd in the raid). Of course this doesn't work and it just lets me time in commands  (which I don't know how to use so I just reboot and boot into windows).

So from what I can guess it seems like I need to get the boot loader to point to my third harddrive rather than looking to boot from the raid. Also the boot loader that appears, seems to be one off the install CD. So it's not the same screen as the one that you get when you press esc at the start of ubuntu (the one that shows something about editing the kernal etc).  That screen doesn't have an option to boot to windows either.

So long story short the only way I can get ubuntu to load is by making the third drive the drive that boots within the bios and there is no way into windows and vice versa.

I saw a post of someone who had a similar problem but I am not advanced enough to be able to take his command line and apply it to my situation nor am I advanced enough to really know if the situations are similar.

Here is the link [http://ubuntuforums.org/showthread.php?t=861917&](http://ubuntuforums.org/showthread.php?t=861917&)

If anyone needs any ideas.  What I would ideally like to happen is be able to boot into my raid drive... and then when I select ubuntu have it boot into my third drive (the ide drive). If nothing else though I am okay with booting into the IDE drive and then being able to boot from the raid through menu.lst if that is possible.



Here is my fdisk information
> 
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x814b4de8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 90445 726499431 83 Linux
/dev/sda2 90446 91201 6072570 5 Extended
/dev/sda5 90446 91201 6072538+ 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c42a8f0

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 52390 420822643+ 7 HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table


Here is my menu.lst info
> 
# ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=8ab4f44b-0928-466e-b139-5d740cd232df ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8ab4f44b-0928-466e-b139-5d740cd232df ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8ab4f44b-0928-466e-b139-5d740cd232df ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by Efros on 2008-09-14
Not a very elegant solution would be to go into your BIOS and change the preferred drive for booting. 

I think I had a similar problem and solved it by getting into the grub menu and changing the hd entry for ubuntu in the boot menu. When I got into Ubuntu I then changed the menu.lst file to reflect the temporary changes I had made on boot. I would try hd1, hd2 etc until you hit the one needed.

---

### Post by nuubun2user on 2008-09-14
> **Efros said:**
> Not a very elegant solution would be to go into your BIOS and change the preferred drive for booting. 

I think I had a similar problem and solved it by getting into the grub menu and changing the hd entry for ubuntu in the boot menu. When I got into Ubuntu I then changed the menu.lst file to reflect the temporary changes I had made on boot. I would try hd1, hd2 etc until you hit the one needed.

How would I go about doing this? How do you get into the grub menu, is that menu.list?

Also I should note that I once installed the grub boot loader on /dev/sda3 (which would be the location of the third drive, if I boot the raid first,I think) as opposed to (hd0,0) and that didn't seem to make any change at all.

---

### Post by Efros on 2008-09-14
You get into grub during the boot phase there should be an onscreen message about Grub, hit esc and you will end up in a menu. Select the OS you want to boot and hit the F6 key you should then change hd0 to hd? where ? is your desired disk. Then press enter and boot using that entry in the menu. Nothing will be permanently changed, that's why you have to go into menu.list once you have ubuntu booted to change the target disk. I'm doing this from memory, so hopefully my memory is good.

---

### Post by nuubun2user on 2008-09-16
> **Efros said:**
> You get into grub during the boot phase there should be an onscreen message about Grub, hit esc and you will end up in a menu. Select the OS you want to boot and hit the F6 key you should then change hd0 to hd? where ? is your desired disk. Then press enter and boot using that entry in the menu. Nothing will be permanently changed, that's why you have to go into menu.list once you have ubuntu booted to change the target disk. I'm doing this from memory, so hopefully my memory is good.

That's part of the problem when I hit esc there is no option to boot into windows... I will try the f6 and see if it gives me an option to change the drive but will the change still be in effect after altering the bios entry? I'lll just have to try it and see. Thanks!

---

