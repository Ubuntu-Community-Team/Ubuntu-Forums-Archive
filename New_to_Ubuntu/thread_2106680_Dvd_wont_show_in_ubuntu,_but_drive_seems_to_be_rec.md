---
title: "Dvd wont show in ubuntu, but drive seems to be recognised."
date: 2013-01-19
forum: New to Ubuntu
---

### Post by jckiik on 2013-01-19
Hi, I am not sure if i'm placing this question in the right section since it is my first post to the ubuntu forum, but i'll give it a shot. I'm having trouble reading a 32-bit Windows 8 dvd from my Matshita uj-860s drive, even after scowering the net and ubuntu forum for solutions. It simply wont mount or show up in ubuntu 12.04, even though i've installed ubuntu-restricted-extras, added the medibuntu repositories, installed libdvdread4 and tried regionset (with an error: "ERROR: Could not open disc "(null)"!")  

sudo lshw also lists the drive:

```
*-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-860S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

```

Thanks in advance! Jean-Claude

---

### Post by sudodus on 2013-01-19
What do you want to do with the Windows DVD? Do you want to 'look at it', the files and folders? Or do you want to install Windows?

Have you tried to boot from it?

---

### Post by MadmanRB on 2013-01-19
Are you trying to see if the disk is still in good condition?
Maybe a virtual install?
In any case seems to be an odd issue as I was able to install windows in virtualbox just fine, disk runs fine.
Perhaps its a bad disk?
Or a bad drive?
Did you try out other DVD media?

---

### Post by jckiik on 2013-01-19
@sudodus: All i want to do is make an iso of it so i then can create a bootable usb for a friend who's got a netbook without a cd-drive, so i'm not looking to install it myself. Tried booting from it on the laptop with ubuntu that i'm working on, but doesnt want to boot up from the drive, even when its first in the boot order. Havent had any problems with the drive until fresh installing ubuntu 12.04, the drive worked fine in windows 7 about 3 days ago, which is why i'm thinking its ubuntu related.

@MadmanRB: Just trying to create an iso, so not trying to install. Cant be a bad disk, since i managed to create the bootable usb from a windows 7 environment on another stationary computer with the same disk two days ago. Just frustrating me that I cant seem to fix it in ubuntu. Wrote about the drive in the previous paragraph, so I dont think its a bad drive either, since i managed to rip and burn cds and dvds a few days back.

Thanks for the quick reply by the way!

---

### Post by sudodus on 2013-01-20
> **jckiik said:**
> @sudodus: All i want to do is make an iso of it so i then can create a bootable usb for a friend who's got a netbook without a cd-drive, so i'm not looking to install it myself. Tried booting from it on the laptop with ubuntu that i'm working on, but [COLOR="Red"]doesnt want to boot up from the drive[/COLOR], even when its first in the boot order. Havent had any problems with the drive until fresh installing ubuntu 12.04, the drive worked fine in windows 7 about 3 days ago, which is why i'm thinking its ubuntu related.

@MadmanRB: Just trying to create an iso, so not trying to install. Cant be a bad disk, since i managed to create the bootable usb from a windows 7 environment on another stationary computer with the same disk two days ago. Just frustrating me that I cant seem to fix it in ubuntu. Wrote about the drive in the previous paragraph, so I dont think its a bad drive either, since i managed to rip and burn cds and dvds a few days back.

Thanks for the quick reply by the way!
I think that there is something wrong, that is not related to Ubuntu, because when booting from the Windows CD, Ubuntu should not be involved at all.

The CD could be bad, or the CD drive, or you might have some setting in the BIOS, that won't work with Windows.

You need to test in different ways to find out what works, and what does not work:

- Try to boot another computer from the Windows 8 CD
- Try to boot your computer from another boot CD
- Try to mount and look at another CD disk in your computer (a data cd or an audio cd)

---

### Post by jckiik on 2013-01-22
I started realising something was off with my drive since it didnt boot from the dvd, tried booting on another computer and it worked fine, then I tried an audio cd and it worked fine, realised that my drive is experiencing a "common" issue, it reads cd's but not dvd's, even though it has support for all types of dvd's. Read other forums and have seen that other people have experienced the same issue. So, it wasn't ubuntu related after all. Now i gotta start looking at firmware updates or just get an external drive if i need to read dvd's.

Thanks for the tips!

---

### Post by sudodus on 2013-01-22
You are welcome :-)

I'm glad you sorted it out :KS

---

