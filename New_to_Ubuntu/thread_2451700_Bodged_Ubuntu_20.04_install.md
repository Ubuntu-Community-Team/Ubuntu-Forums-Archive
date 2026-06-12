---
title: "Bodged Ubuntu 20.04 install"
date: 2020-10-09
forum: New to Ubuntu
---

### Post by danielbrookes on 2020-10-09
Hi everyone.

I suspect I may have done something stupid installing 20.04.

I selected the option "erase disk and install" rather than "erase 18.04 and install". 

Now when the installation is complete, nothing loads up. It says Boot Agent cannot be found.

Two questions with more urgency on the former

i. How do I fix this?
ii. What is the use of this option if it, as it appears to have, erases an entire disk?

Best
Dan

---

### Post by danielbrookes on 2020-10-09
Specifically, it says "no boot device found".

---

### Post by Frogs Hair on 2020-10-09
What type of installation media did you use , dvd or usb ?  The option is _supposed to _ erase the  entire disk and install the Ubuntu operating system.

---

### Post by danielbrookes on 2020-10-09
Hi Frogs Hair - I made a bootable USB stick using the 18.04 installer.

---

### Post by Frogs Hair on 2020-10-09
Have you tried to run the installer using the install Ubuntu option. I'm afraid what ever files you had on disk are gone.

---

### Post by danielbrookes on 2020-10-09
> **Frogs Hair said:**
> Have you tried to run the installer again ?

Yes, I've made a couple of attempts. 

Ran diagnostic on the laptop. All tests passed.

---

### Post by danielbrookes on 2020-10-09
Fortunately I did save the files before I attempted the install.

---

### Post by ActionParsnip on 2020-10-09
If Ubuntu is the only OS on the disk and that OS doesn't boot then I'd just wipe all partitions from the disk and install Ubuntu from scratch (preferably Ubuntu 20.04)

---

### Post by danielbrookes on 2020-10-09
> **ActionParsnip said:**
> If Ubuntu is the only OS on the disk and that OS doesn't boot then I'd just wipe all partitions from the disk and install Ubuntu from scratch (preferably Ubuntu 20.04)


Ubuntu is the only OS on the disk and it seems as though what I did was wipe the partitions. I'll try and create a different bootable USB. If that doesn't work then I'm officially stumped.

---

### Post by danielbrookes on 2020-10-09
I found an older bootable USB with 18.4 on just to see if I could get anything loading and it wouldn't even go along with the pretence of trying to install it. . Just said it was corrupted and refused.

I'm now attempting to install 20.4 one more time. It plays ball all through the install. Finished...nope, same as before.

Just noticed PXE-E61 Media Test Failure in the boot screen so going to see what that is.

---

### Post by danielbrookes on 2020-10-09
Completely stumped. I played with the boot order and unticked the integrated NIC and that made it so nothing would happen at all. Reticked the box and it's back as it was. No cables are loose. It basically seems that after I installed 20.4 it can't read the HD. Sorry if I'm using the terminology incorrectly. Absolutely clueless now.

---

### Post by sudodus on 2020-10-09
Please tell us about the computer:

- brand name and model of the computer itself (or if home built, of the motherboard)

- brand name and model of the graphics card/chip

---

### Post by danielbrookes on 2020-10-09
It's a Dell Latitude. Not sure on graphics card.

---

### Post by Frogs Hair on 2020-10-09
> PXE-E61 Media Test Failure This could be bios and boot order related from what I can find out so far.

---

### Post by sudodus on 2020-10-09
Which version number of Latitude?

(I have a Latitude E7240 with Intel i5-4200U and built-in graphics, no separate graphics chip/card.)

If you can boot into the USB boot drive, you can run the command line

```

sudo lshw | less

```

and scroll to look for

-cpu

and

-display

---

### Post by sudodus on 2020-10-09
Is there any reason to think that the internal drive is damaged? You can check according to the following link,

[S.M.A.R.T. information of HDD and SSD](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983)

---

### Post by danielbrookes on 2020-10-09
OK it's a Latitude E5450 and it has an Intel Core i3-5010U.

I've no reason to think the internal drive is damaged. I was using it in work this morning as fine as it has been for years, and through a few OS changes. Theoretically it could be but a diagnostic scan seemed to register the existence of the HD.

I ran the gnome-disks command and it said disk is ok. 

I did as much of the 
sudo e2fsck -cfk /dev/sdxnas I could understand. It seemed to have major issues with sda4. Here's what it said:

ubuntu@ubuntu:~$ sudo e2fsck -cfk /dev/sda4
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
Error reading block 60850175 (Invalid argument).  Ignore error<y>? yes
Force rewrite<y>? yes
Superblock has an invalid journal (inode 8).
Clear<y>? yes
*** journal has been deleted ***

The filesystem size (according to the superblock) is 121833472 blocks
The physical size of the device is 131328 blocks
Either the superblock or the partition table is likely to be corrupt!


An old post on Askubuntu seemed to think that installing and choosing 'something else' and partitioning would work, but I don't really know how to do that without an idiot's walkthrough.

I'm in over my head here.

---

### Post by yasha312 on 2020-10-09
I would run the check disk for error option on the boot disk. If it passes, look in your computers settings for a S.M.A.R.T. test. Or any other hard drive testing software.  If that passes, make sure your not trying to do something like install x64 on an older pc. Last ditch effort. Take out anything the computer can run without, gfx card, wifi adaptors, extra ram, anything then try to boot again. If all else fails, try a different flash drive

On your boot menu does your live disc show up as a legacy device?
What is the brand of your flash drive?
Is this a laptop?

---

### Post by danielbrookes on 2020-10-11
OK - I'm peering about on the laptop (it's a laptop) using the Try Ubuntu rather than installing it again. It can read the hard drive.

I clicked 'properties' in the home file and it said the whole thing is only 2GB. I then looked in 'other locations' and across sda3/sda4 there's another 1GB and then sda5 seems to have all of the space remaining (498GB).

I did C+Alt+T to try sudo smartctl -i /dev/sda and it said smartctl command not found.

The laptop can handle 64 bit just fine.

---

### Post by danielbrookes on 2020-10-11
OK. Through Try Ubuntu I downloaded Elementary OS and made a bootable USB with it in the second USB drive. Attempted to install it - erased disk and installed over everything - and I write from it now. Worked fine. I guess it was a corrupted install, then?

---

### Post by sudodus on 2020-10-11
I think you are right. Congratulations to a successful install :KS

---

### Post by Paulgirardin on 2020-11-02
> **danielbrookes said:**
> OK. Through Try Ubuntu I downloaded Elementary OS and made a bootable USB with it in the second USB drive. Attempted to install it - erased disk and installed over everything - and I write from it now. Worked fine. I guess it was a corrupted install, then?

I'm not sure if this is relevant,but I installed Ubuntu 20.04 on an Acer E15 laptop recently and could not get it to boot until I manually pointed the UEFI software at the correct EFI boot file.

---

