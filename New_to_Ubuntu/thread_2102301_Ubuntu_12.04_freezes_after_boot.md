---
title: "Ubuntu 12.04 freezes after boot"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by tbrann on 2013-01-06
After installing Ubuntu 12.04 from a CD on to my Toshiba Satellite laptop, there was a message from the tool menu that I needed to install upgrades. So I did, then restarted the computer as directed, and now it freezes when the desktop comes up and neither the mouse nor the keyboard will work. I have to do a hard reboot.

I tried to reinstall from the CD, but it stops during installation. I tried to just run the OS from the CD, but it still freezes.

System info:
TOSHIBA Satellite C655D
Processor:AMD E-300 APU with Radeon HD Graphics 1.3GHz 2 Core(s), 2 Logical Processors
Display: AMD Radeon HD 6310 Graphics
RAM: 2.00 GB

I apologize for the repetition, this was previously posted under the wrong prefix and I could not find a way to correct it.


The CD installed the 32 bit version.

---

### Post by fdrake on 2013-01-06
> **tbrann said:**
> 

I tried to reinstall from the CD, but it stops during installation. I tried to just run the OS from the CD, but it still freezes.

The CD installed the 32 bit version.
check the cd for possible errors at the boot menu!
In which part of the installation prosses the crash happens?

---

### Post by tbrann on 2013-01-06
OK I inserted the disk and clicked the option to 

check the disk for errors
No errors found. 

The problem is in the laptop, not the CD

When I tried to install, it let me select a language (English) . Then the CD drive started whirring & shifting as if it were installing. Then it just froze at the screen that says ubuntu with the five orange dots underneath.

---

### Post by fdrake on 2013-01-06
maybe there is a problem with the cd drive. Do you have a usb drive , Can you make a Live Usb drive system with another pc?

---

### Post by tbrann on 2013-01-06
I don't think the problem is the CD drive. As I said, the first installation went fine and I was able to get on the internet etc. Then 
I doI downloaded all the updates as instructed & restarted to install them. That's when the problem started. There is something that got downloaded that is messing things up. A bad driver, maybe.

Similar problems happened to me last summer when I got Ubuntu from the internet and downloaded it onto a partition. Things froze up then too. 

At that time I had Windows 7 on the other partition. Eventually I had some type of disk error that couldn't be fixed, so I replaced the hard drive and installed Ubuntu fresh from a CD, with no partitioning.

---

### Post by fdrake on 2013-01-06
when you boot (from hhd not cd) do you still have grub or was wiped off by the installation? Can you go into recovery mode and run "fsck"?

---

### Post by tbrann on 2013-01-06
Yes if I hold down SHIFT I can get to Recovery Mode option. I can select fsck Check all file systems and it says:

fsck from util-linux 2.20.1
/dev/sda1: 229462/19431424 files (0.2% non-contiguous), 2480198/77722880 blocks
_

---

### Post by fdrake on 2013-01-06
> **tbrann said:**
> Yes if I hold down SHIFT I can get to Recovery Mode option. I can select fsck Check all file systems and it says:

fsck from util-linux 2.20.1
/dev/sda1: 229462/19431424 files (0.2% non-contiguous), 2480198/77722880 blocks
_
it's very hard to say only from fsck if is the hhd the problem or not, But that is not a positive message. Installing "smartmontools"  might tell us more but you need a live section or a stable system to install it from the net.

 I presume that you are not able to boot from an old kernel from the grub menu?(is it still there? Did you try before any errors?

---

### Post by tbrann on 2013-01-07
No, from the GRUB menu I can go into this one installation or recovery mode or check memory. That's it, and I have already checked the memory (no errors).

---

### Post by fdrake on 2013-01-07
it is quite strange that the live cd that before used to work now it is not working properly. It suggests the possibility of hardware failure, but before that I' dtry with a different ubuntu releas or even a version of linux mint... Sorry out of ideas since we have no live sections to use in order to check what's wrong, we are very limited with possibilities.

---

### Post by tbrann on 2013-01-07
I am willing to wipe the hard drive and try to re-install, but I need to know what to do if the problem arises again.

As I have said, the freezes happened with the old hard drive when I installed from an internet download, and they also happened when I got a new hard drive and installed from a CD. In both cases there were updates installed.

This is a new HD, so I am not losing any valuable data if I wipe the HD. I just want to get this OS up and running by any means necessary, and as soon as possible. I would rather not have to wait another year or two for Ubuntu to release a version that's less buggy.

---

### Post by tbrann on 2013-01-07
So at this point, if I were to wipe the hard drive and start over,

1) is there a command I could use in the root (in Recovery Mode) that would reformat the hard drive?

And
2) If I do re install, what should I install to stop this from happening again?

Or is there some other alternative way to get Ubuntu to work?

Maybe some kind of error log that would tell me what's going wrong?

---

### Post by tbrann on 2013-01-08
OK thanks everyone! The problem is solved!

I reformatted my hard drive and redid the installation, but did not install any updates or proprietary drivers this time!

I used to use Windows where we had to regularly install updates and worry about avoiding viruses. With Ubunu, there's less risk from viruses, you just need to avoid some of the updates! LOL! 

Thanks for your help everyone. I just need to find advice about what updates/ drivers to avoid, but I guess that's a topic for a different thread.

---

