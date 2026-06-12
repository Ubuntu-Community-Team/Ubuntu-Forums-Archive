---
title: "CLI based distro?"
date: 2008-02-29
forum: Other OS Talk
---

### Post by Yes on 2008-02-29
Is there any Linux distro that's just a command line?  I know of the server edition of Ubuntu and Slackware, but it's got to be very lightweight (It'll be on a laptop with 8 MB of ram and a 486 CPU).  It's also either got to be able to either fit on a floppy(s), or be able to boot from an iso on the hard drive (I have a "live floppy" of Linux, so I can wget the iso).

Is there anything like this?  I looked in the "Distros for old computers" sticky, but most of the smaller ones don't work (one gave a kernal panic error, another wouldn't install to the floppy right, things like that).

Thanks!

---

### Post by Dr Small on 2008-02-29
Like this?
[http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/](http://kmandla.wordpress.com/2007/11/29/miniubuntu-710-at-last-a-command-line-ubuntu-live-cd/)

---

### Post by mali2297 on 2008-02-29
How about [ttylinux]("http://www.minimalinux.org/ttylinux/")?

---

### Post by Yes on 2008-02-29
Kind of, but I need something that can be installed to the hard drive.

e:  ttylinux looks promising, I'll look into it.

---

### Post by seanc7 on 2008-02-29
I think pretty much any distro can be installed as command line only. 

Especially Debian or Fedora Core or Ubuntu. You just need to get the Ubuntu Minimal ISO CD image.

---

### Post by LinuxGuy1234 on 2008-03-01
I prefer either Slackware (installing just the A, AP and Y sets), Debian (use install tasks="standard") or Ubuntu (use alternate CD, choose to install a command-line system).

---

### Post by Yes on 2008-03-01
The problem is, I need to be able to install it with a floppy, either from the floppy or from the hard drive via floppy.  I don't think any of the bigger distros will have that, will they?

ttylinux doesn't seem to have a way to boot from a floppy :(

---

### Post by p_quarles on 2008-03-01
[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

---

### Post by LinuxGuy1234 on 2008-03-01
I think Debian "can" be installed form floppies, and maybe Slackware.

---

### Post by Hevoos on 2008-03-01
BasicLinux - [http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/) . I guess you'll have to use the DOS version.

---

### Post by Yes on 2008-03-01
I tried the method p_quarles gave me, and I'm running into some problems.  Does anyone know what the error

```
__alloc_pages: 0-order allocation failed (gfp=0x1d2/0)
VM: killing process *
Killed
Kernel panic: Attempted to kill init!
```

*was a bunch of different programs (echo, umount, mount, cp, etc.).  Does anyone know what the problem is?  I seems like it's to do with the memory, but I'm not sure what the problem would be.

e:  Do you think I can get the iso on the hard drive and then use [SmartBootManager](https://help.ubuntu.com/community/SmartBootManager) to boot from it?  It's supposed to boot from a CD, but it seems like it should also be able to boot from a hard drive.  Is ther any more documentation on it other than that article?

e2:  If I did download an iso and boot from it with SmartBootManager, what would I do?  I assume I can't just download the normal versions, right?

---

### Post by init1 on 2008-03-02
> **Hevoos said:**
> BasicLinux - [http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/) . I guess you'll have to use the DOS version.
Basic Linux is a good option. I've booted it with loadlin and FreeDOS. 
[www.freedos.org](www.freedos.org)
> **mali2297 said:**
> How about [ttylinux]("http://www.minimalinux.org/ttylinux/")?
That was the first thing I thought of when I read the thread title. TTY is an awesome distro. The problem is though that it cannot be installed with floppies

---

### Post by Yes on 2008-03-02
So the DOS version of BasicLinux would install to the hard drive, and I would start it from FreeDOS like you start Windows 3.0 from MS-DOS?

---

### Post by stream303 on 2008-03-03
> **Yes said:**
> Is there any Linux distro that's just a command line?  I know of the server edition of Ubuntu and Slackware, but it's got to be very lightweight (It'll be on a laptop with 8 MB of ram and a 486 CPU).  It's also either got to be able to either fit on a floppy(s), or be able to boot from an iso on the hard drive (I have a "live floppy" of Linux, so I can wget the iso).

How about Tom's root-boot:

[http://www.toms.net/rb/](http://www.toms.net/rb/)

I remember using that and having a lot of fun with just a floppy.  I kind of sat back in amazement that such a thing was possible...

---

### Post by init1 on 2008-03-05
> **Yes said:**
> So the DOS version of BasicLinux would install to the hard drive, and I would start it from FreeDOS like you start Windows 3.0 from MS-DOS?
Sorta. There's a .bat file that you would run (I think) to start it up.

---

### Post by Yes on 2008-03-14
Ok, I got BaseLinux running =D

Unfortunatly, I can't start the X server, and I can't find the right network drivers for my Xircom CreditCard PS-CE2-10 card.  Does anyone know where I can get that?

---

### Post by mali2297 on 2008-03-14
> **Yes said:**
> Ok, I got BaseLinux running =D

Unfortunatly, **I can't start the X server**, and I can't find the right network drivers for my Xircom CreditCard PS-CE2-10 card.  Does anyone know where I can get that?

I thought you wanted a pure CLI distro. :-s

---

### Post by Yes on 2008-03-14
Meh.  I really just want to anything installed, but if it has a GUI I figured I might as well figure it out.

I think I need the if_xe driver.  Unfortunatly, I'm having trouble finding it.  All the ones I can find are for BSD o_O.  Once I compile the driver, I'll get a .o file (is that an object file), right?

e:  I'm trying to install it to the disk.  But the problem is I need to make a ext2 partition, while /dev/hda1 is still mounted... because that's where BasicLinux is running off of.  So of course I can't delete that partition to make a new one.

I'm lost :-(

---

### Post by PoopSlayer on 2008-03-14
I don't know if basiclinux does this, but you may be able to make a new partition by using an unallocated space to install to.

---

### Post by Yes on 2008-03-14
Can you do that in fdisk?

What would you normally do that with (from the CLI, of course).

---

### Post by chris4585 on 2008-03-16
why not just use the gparted livecd to partition it... gparted ftw

---

### Post by mali2297 on 2008-03-16
> **chris4585 said:**
> why not just use the gparted livecd to partition it... gparted ftw

For this system, I think plain [Parted]("http://www.gnu.org.ua/software/parted/") would be better. Perhaps one can use [PAUD]("http://paud.sourceforge.net/").

---

