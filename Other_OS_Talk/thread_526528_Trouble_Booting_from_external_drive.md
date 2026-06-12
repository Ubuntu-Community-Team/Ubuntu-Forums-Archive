---
title: "Trouble Booting from external drive"
date: 2007-08-15
forum: Other OS Talk
---

### Post by happysmileman on 2007-08-15
I just installed Gentoo on my external drive and can't get it to boot.

I ran grub-install /dev/sda (my external drive) and when I load it up it flashes something like ```
Grub stage 1.5

Loading, please wait
```

then immediately goes to the boot menu on my hard-drive (the internal drive with ubuntu and Windows on it)

My grub.conf is:
```

#By default load first option
default 0

#Load after 30 seconds if not selected
timeout 30

#Splash image to load
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz


#The settings for Gentoo
title=Gentoo Linux 2.6.22-r2
root (hd0,0)
kernel /boot/kernel-2.6.22-gentoo-r2 root=/dev/sda3

```

I have a feeling it may be to do with the fact that I used (hd0,0) for it, but didn't know what else to do...

When I go into the command line of GRUB it says I can boot from hd0, fd0 or fd1.

But I have no idea how to do this or which one it is.

Any idea, I didn't put this in the Gentoo forum because it's happened before to me with LFS, but I assumed I did it wrong and just gave up on it and reformatted, so it doesn't appear to be a Gentoo problem, ity appears to be a problem with GRUB or my BIOS or me making a mess of things

---

### Post by miggols99 on 2007-08-16
I think you have to change the root to fd0 or fd1 depending on which is your root partition. So change:

root (hd0,0)

to

root (fd0,0)

or

root (fd1,0)

So does this mean you have 3 hard drives?

---

### Post by happysmileman on 2007-08-16
> **miggols99 said:**
> I think you have to change the root to fd0 or fd1 depending on which is your root partition. So change:

root (hd0,0)

to

root (fd0,0)

or

root (fd1,0)

So does this mean you have 3 hard drives?

Nope, I have 2, and internal and an external, but in my "device.map" file it says that hd1 is /dev/sda, however when booting it doesn't appear to have a hd1.

I've tried editing the grub.conf file to both fd0 and fd1 and the exact same thing happens.

And when i go to the GRUB command line and try it I get an error 25 trying to root () one of them, the other gives no error then but says can't mount the drive when i try load the kernel.

---

### Post by happysmileman on 2007-08-16
Oh and my boot order in BIOS is:

```
DVD drive
USB FDD
SCSI device
First Hard Drive
```

It doesn't mention the external drive but I get the "loading stage 1.5" message when my external drive is plugged in so I'm assuming it's able to detect it

---

### Post by happysmileman on 2007-08-20
Anybody?

---

### Post by init1 on 2007-08-20
fd* is for floppy disks. Try hd1. Better yet, when the other grub loads, press "C". This will give you the command line. Then type:
```

root (hd

```
and then press tab. Post what happens.

---

### Post by happysmileman on 2007-08-21
> **init1 said:**
> fd* is for floppy disks. Try hd1. Better yet, when the other grub loads, press "C". This will give you the command line. Then type:
```

root (hd

```
and then press tab. Post what happens.

That's what i did and it only has hd0, fd0 and fd1, does this mean my BIOS just won't support it?
It lists fd0 and fd1 but I only have 1 floppy drive, so I thought maybe it for some reason recognises it as a second Floppy drive?

---

### Post by Keen101 on 2007-08-27
I just bought the UBUNTU HACKS book from B&N.

on page 39 on hack #10 (Install Ubuntu on an External Drive)

it say's:

Unfortunately this sort of install does not automatically work without some tweaking....

-By default, the initrd (initial ram disk) file that Ubuntu uses does not contain all of the drivers you need to boot from a removable drive. Your BIOS will find the drive fine, but once the kernel loads, Linux won't be able to see or mount the drive to continue the boot process.

-Even if the initrd has the appropriate drivers, it takes a few seconds for the kernel to load these modules and detect your removable drive before it tries to use it. During this time, the system will likely try to boot and will not be able to find the removable drive because it hasn't finished loading the modules.

.....it goes on.... make sure grub is installed to the MBR of the external and NOT to the internal......then use chroot.....


-Next, complete the Ubuntu installation up until when it prompts you to reboot the system.... hit Alt-F2 to switch to the console... and hit ENTER to activate...

# mount -t proc /target/proc

...now you can use the chroot tool to turn the /target directory into the effective / partition on the system.....

# chroot /target

...tweak initrd....

edit the configuration files....
3 vim /etc/mkinitramfs/modules

...move to the bottom of the file... and add the following lines:

ehci-hcd
usb-storage
scsi_mod
sd_mod

... if your removable drive is connected via IEEE1394, also add:

ieee1394
ohci1394
sbp2


...with the correct modules configured, the next step is to set up a initrd so that it will wait a number of seconds before continuing to boot. That way Linux has time to detect and configure the removable drive.

Open /etc/mkinitramfs/initramfs.conf

in a text editor....

Now add a new configuration option to the very top of the file so that Linux will wait....

WAIT=10

..in our experience 10 seconds works fine. (you can increase or decrease as you like)

now re-create an initrd file that has the new settings:

# mkinitramfs -o /boot/initrd.img-2.6.15-16-386 /lib/modules/2.6.15-16-386

Change the initrd.img and /lib modules paths to match the kernel version included in your Ubuntu install CD.

...bla .. it goes on to say that you may need to edit grub. (it gives instructions)

but, I don't think you need to do that...

hope this helps. (I wan't to hear how it goes, because I'm planning to do the same soon)

-keen101

---

### Post by happysmileman on 2007-08-28
Sounds useful, but I'm installing Gentoo onto external drive... And "/etc/mkinitramfs/initramfs.conf" doesn't exist on it

Ok found the equivalent file but the correct modules aren't in the /lib/modules/<kernelversion/ folde ror any subfolders... or are they just included by default... very few things are modules on my kernel, but I'm r=pretty sure I included anything to do with external drives etc. by default

---

### Post by Keen101 on 2007-08-28
hmm... we'll it does say... Even if the initrd has the appropriate drivers, it takes a few seconds for the kernel to load these modules and detect your removable drive before it tries to use it. During this time, the system will likely try to boot and will not be able to find the removable drive because it hasn't finished loading the modules.


So, see if you can make it slow down a little....


I couldn't really tell you.


But, good luck. hope you get it going,

-keen101

---

### Post by init1 on 2007-08-28
> **happysmileman said:**
> That's what i did and it only has hd0, fd0 and fd1, does this mean my BIOS just won't support it?
It lists fd0 and fd1 but I only have 1 floppy drive, so I thought maybe it for some reason recognises it as a second Floppy drive?
GRUB doesn't recognize my USB drive. So it's GRUB at fault, not you BIOS. Try booting your external drive with Syslinux. It will run on any device. 
```

sudo apt-get install syslinux mtools

```

---

