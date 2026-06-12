---
title: "Amiga Fast File System--Help Por Favor"
date: 2008-12-15
forum: Programming Talk
---

### Post by codemonkey_also on 2008-12-15
Hello all,

This is my very first post! Very glad to be amongst a tight knit group of folks. 

I've got a question though: A friend of mine (who is not a coder but is an Ubuntu user) has tasked me (vice versa, respectively) to write something that will make sense of an old Amiga drive lying around. 

He's given me a hexdump of the drive in its entirety. My goal is to create a program that will run through the drive and construct a directory tree much like you would find in graphic-driven OSes. But first, I need to know how to even read the drive. 

Has anyone had any experience with the Amiga Fast File System that can lead me to some information about extracting the data? 

Thanks kindly for your time,
Michael Fritzius

---

### Post by cyberdork33 on 2008-12-15
I think you have posted to the wrong forum ;)

---

### Post by Billsey on 2008-12-15
He is looking for help in porting the version of Amiga Fast Filesystem that is included in the Linux kernel (thus his reason for joining and posting here) to function on another platform (MacOSX in this case; yes I know him and what he is talking about). If there is help to be found in doing this with the Linux kernel version, I would think that a Linux forum would be the proper forum to post in, and this is, after all, Ubuntu LINUX, right?

---

### Post by cyberdork33 on 2008-12-15
> **Billsey said:**
> He is looking for help in porting the version of Amiga Fast Filesystem that is included in the Linux kernel (thus his reason for joining and posting here) to function on another platform (MacOSX in this case; yes I know him and what he is talking about). If there is help to be found in doing this with the Linux kernel version, I would think that a Linux forum would be the proper forum to post in, and this is, after all, Ubuntu LINUX, right?
I actually meant posting in the Apple Users support forum. This forum is really for helping with installation of Ubuntu on Apple hardware. You seem to be seeking help with creating a filesystem driver for OSX...

You might try the "Programming Talk" forum or even the linux kernel mailing list ([http://lkml.org/](http://lkml.org/)) since you are trying to port kernel code.

Also, just hint, it might be easiest for the end users to create a module for MacFUSE instead of an actual OSX kernel driver.

Good Luck!

---

### Post by bapoumba on 2008-12-15
Moved to PT. Hardware could do it too?

---

### Post by Leslie Viljoen on 2008-12-15
> **codemonkey_also said:**
> Has anyone had any experience with the Amiga Fast File System that can lead me to some information about extracting the data? 


Some info is here: [http://wiki.osdev.org/FFS_(Amiga](http://wiki.osdev.org/FFS_(Amiga))

Is this an exercise? Because if you wanted the data you could just mount it under Linux and copy the data off.

If you look at the mount command under Linux, you'll see there's support for AFFS, which is the file system you are looking for. So you should be able to directly mount the file as a loop device.

Something like this:
sudo mount ~/source_image /mnt/target -t affs -o loop=/dev/loop3


Les

---

### Post by khelben1979 on 2008-12-15
I'm an old Amiga user and I've actually run Linux on an Amiga 4000 a few years ago.

I had no problems in reading data from an partition which was formatted with the Fast File System.

Just make sure your kernel has the FFS installed in the kernel or as a module or else you won't be able to do this, to my knowledge.

---

### Post by Billsey on 2008-12-15
> **cyberdork33 said:**
> I actually meant posting in the Apple Users support forum. This forum is really for helping with installation of Ubuntu on Apple hardware. You seem to be seeking help with creating a filesystem driver for OSX...

You might try the "Programming Talk" forum or even the linux kernel mailing list ([http://lkml.org/](http://lkml.org/)) since you are trying to port kernel code.

Also, just hint, it might be easiest for the end users to create a module for MacFUSE instead of an actual OSX kernel driver.

Good Luck!
Ah, I see. What he's looking to do wouldn't actually be a kernel driver, though, as OSX keeps the filesystem drivers as separate files, just like AmigaOS used to do. By the way, the drive in question is a SCSI drive, so the system doing the reading would have to have SCSI support. The current state of affairs is that the drive is mounted to a (MacOSX) system that sees the drive, and can access the drive, but has no filesystem with which to make sense of it. Thus the project porting the filesystem over to MacOSX.

By the way, the Mac involved is a 400MHz G4 with a GB of RAM and an added in SCSI controller card (Which Dapper doesn't seem to see. Darn).

---

