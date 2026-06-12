---
title: "Reading CD drive in C"
date: 2009-04-06
forum: Programming Talk
---

### Post by Firestom on 2009-04-06
Welcome!

I have been looking trough API's to read CDRom drives, and have found none that works fine or suits my needs. I have then decided to try myself to read those CD drives.

Trough the command line I have tried:

```
cd /dev
ls -l | grep cdrom

```

And it returned:

```

lrwxrwxrwx  1 root   root           4 2009-04-06 16:36 cdrom -> scd0
brw-rw----+ 1 root   cdrom    11,   0 2009-04-06 16:36 scd0
crw-rw----  1 root   cdrom    21,   1 2009-04-06 16:36 sg1

```

I have to assume my CDRom drive is device scd0 and it is a block device.
Through basic C file management I have tried to read it with fgetc() and it returned EOF (-1) on scd0 and nothing in sg1. Good start.

I have then tried looking for documentation on the net, but they tend to explain in a very confusing. I can't even know what langauage are the codes for and which includes I need to make.

How can I read a block device using C (or C++) standard library?

---

### Post by cabalas on 2009-04-06
Assuming that the cd has been auto-mounted, why don't you just use /media/cdrom as the base path for all of your files?

---

### Post by Firestom on 2009-04-06
/media/cdrom is only a path to the device, and I can't access the CD data using this path. I'm looking into making it the usual, reading from scd0.
This will also allow to make much more operations using the device, not only reading files.

---

### Post by dwhitney67 on 2009-04-06
Look at the OSS for the 'dvdrecord' app (... and yes, this app works with CDs too).

The package is either 'wodim' or 'cdrtools', depending on the Linux distro that you use.

---

### Post by Firestom on 2009-04-06
I have looked through it, but these apps allows only to write on the CD drive, not read from it. I have not found any good libraries to read CDRoms or how to read the myself.

---

### Post by benj1 on 2009-04-07
have you looked at sdl
[http://www.libsdl.org/](http://www.libsdl.org/)

its got libraries for read cds, its more aimed at music from what ive seen but it could be of some use.

---

### Post by soltanis on 2009-04-07
Have you seen libcdio?

[http://www.gnu.org/software/libcdio/](http://www.gnu.org/software/libcdio/)

---

### Post by Firestom on 2009-04-08
> **benj1 said:**
> have you looked at sdl
[http://www.libsdl.org/](http://www.libsdl.org/)

its got libraries for read cds, its more aimed at music from what ive seen but it could be of some use.

You found the exact reason why I wanted to learn the most low-level functions for reading CDs.

> **soltanis said:**
> Have you seen libcdio?

[http://www.gnu.org/software/libcdio/](http://www.gnu.org/software/libcdio/)
No I have not, I'll look into it! Thanks!

---

### Post by lensman3 on 2009-04-08
I use the following command to prove that a Linux distribution was written correctly to the cd.

readcd dev=/dev/hdc  sectors=0-`isosize -d 2048 /dev/hdc` retries=0  f=- | md5sum

I then compare the md5sum to the iso I just wrote.  

Seems that readcd and isosize might be part of you answer.  These commands would work in a shell script.

---

