---
title: "Creating a bootable DVD for Ver. 12.04"
date: 2019-12-02
forum: New to Ubuntu
---

### Post by jim-holloman on 2019-12-02
I want to create a bootable DVD to install Ubuntu on a 32-bit, Intel P4 computer with a new 500 GB HDD.

I downloaded the Ver. 12.04 .iso file and used a Windows 7 PC to create (burn) a DVD.

The DVD is not bootable.

I found an old Ver. 7.4 CD and it will boot on the same machine.

The directory of the Ver. 12.04 DVD is:

 Volume in drive V is Ubuntu 12.04.3 L
 Volume Serial Number is 0FB2-ABE3

08/20/2013  01:10 PM    <DIR>          .disk
08/20/2013  01:10 PM    <DIR>          boot
08/20/2013  01:10 PM    <DIR>          casper
08/20/2013  01:10 PM    <DIR>          dists
08/20/2013  01:10 PM    <DIR>          install
08/20/2013  01:10 PM    <DIR>          isolinux
08/20/2013  01:10 PM    <DIR>          pics
08/20/2013  01:10 PM    <DIR>          pool
08/20/2013  01:10 PM    <DIR>          preseed
08/20/2013  01:10 PM               134 autorun.inf
08/20/2013  01:10 PM             3,693 md5sum.txt
08/20/2013  01:10 PM               233 README.diskdefines
08/20/2013  01:10 PM         2,503,528 wubi.exe
               4 File(s)      2,507,588 bytes
               9 Dir(s)               0 bytes free

The wubi.exe file is executed via the autorun.inf file. But, without an existing OS, there is no program to read and process the autorun.inf file.

The Ver. 7.04 CD does not use an autorun.inf file. It has a start.exe program.

TIA, Jim Holloman

---

### Post by CatKiller on 2019-12-02
12.04 has been unsupported for 2½ years.

---

### Post by Skaperen on 2019-12-02
do you have a specific reason for installing version 12.04?  will this machine be connected to the internet?

---

### Post by SeijiSensei on 2019-12-02
The most recent version for 32-bit systems with long-term support is 16.04: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

Have you tried installing to a USB device?  On Windows, use [Rufus]("https://rufus.ie/"). 

See: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)

Also WUBI has not been used for years.

---

### Post by mörgæs on 2019-12-02
Within the Buntu family the latest offer for 32 bit systems is Lubuntu 18.04.3. It will give you medium-long support through april 2021.

---

### Post by crip720 on 2019-12-02
Seeing that 12.04 is no longer supported, doing this would be just for fun, there will be no updates.  lubuntu or xubuntu should run on a p4, it does on mine. Do you need to use wubi or want to do a full install?   DVDs disks have been known to be bad.

---

### Post by GhX6GZMB on 2019-12-02
I understand the reason for the OP's wish for 12.04.
I had the same misconception, which comes from the Win world. People think that old hardware is no longer supported in new distributions (which is Win-think).

@jim-holloman: there's no reason to go back to old distributions. All hardware, once supported, work on newer versions. Go with 18.04.3

---

### Post by jim-holloman on 2019-12-02
My reply 191202-1445 EST (-5 GMT)

Many thanks for all the replies.

Per the information from SeijiSensei, I D/L'ed ubuntu-16.04.6-desktop-i386.iso (1,638,400 KB) and created a DVD on a PC using Roxio Creator NXT 6 --> Burn Disc Image.

The DVD created would not boot; "Non-System disk or error". I have the ROM-BIOS set to boot from the DVD Drive and can boot from a old LinuxMint disc and an old Ubuntu 7.04 disk.

I am unable to try a USB device because the ROM-BIOS on the target computer does not allow booting from a USB device; only floopy disk, optical disc, and hard disk.

--------------------------------------
The directory of the DVD is:

 Volume in drive V is Ubuntu 16.04.6 L
 Volume Serial Number is DA75-6495

02/27/2019  05:15 AM    <DIR>          .disk
02/27/2019  05:15 AM               229 README.diskdefines
02/27/2019  05:15 AM    <DIR>          boot
02/27/2019  05:15 AM    <DIR>          casper
02/27/2019  05:15 AM    <DIR>          dists
02/27/2019  05:15 AM    <DIR>          install
02/27/2019  05:15 AM    <DIR>          isolinux
02/27/2019  05:15 AM             3,648 md5sum.txt
02/27/2019  05:15 AM    <DIR>          pics
02/27/2019  05:15 AM    <DIR>          pool
02/27/2019  05:15 AM    <DIR>          preseed
               2 File(s)          3,877 bytes
               9 Dir(s)               0 bytes free

Ubuntu used 1.56 GB of space.
--------------------------------------

There is no .exe file in the root? Should there be?

Could Ubuntu be packaged as a .zip file that could be unzipped onto a DVD and then be bootable? What mandates the use of a .iso file?

Thanks mörgæs.

I read this article and a couple more and came to the conclusion that the lastest Ver. of Ubuntu to support 32-bit was Ver. 16.04.6. That is also consistent with the reply from SeijiSensei.

Ubuntu is Officially Dropping 32-bit Desktop Images
[https://itsfoss.com/ubuntu-drops-32-bit-desktop/](https://itsfoss.com/ubuntu-drops-32-bit-desktop/)

So, is it TRUE or is it FALSE that Ver. 18.04.3 is suppose to be able to create a bootable DVD for 32-bit computers? It either case, it is confusing.

True. But, shouldn't the .iso file still be able to create a bootable  DVD? Shouldn't I still be able to install it even if it is not  supported?

------------------------------------

> **Skaperen said:**
> do you have a specific reason for installing version 12.04?  will this machine be connected to the internet?

Thanks Skaperen.

I was using Ver. 12.04 to see if I was able to create a Bootable DVD from the .iso file. The process is new to me. 

I see no reason why the Ver. 12.04 .iso should not be able to create a Bootable DVD; supported or not supported.

I suspect I will connect the computer to the Internet later on in order to D/L Updates. For now, I just want to take a look at Ubuntu and learn something about Linux type OS's. There is a lot of new stuff to learn; like ext3, ext4, exFAT, compatibility, etc.

-----------------------------------

It appears that there is a problem with the Forum. My separate replies are being merged together. I also get an Error when I try to Edit some of them (Index is invalid).

---

### Post by jim-holloman on 2019-12-02
I try to follow the instructions here, but my DVD will not boot. The 
computer says "Non-System disk"
[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

---

### Post by mörgæs on 2019-12-02
The 18.04.3 [COLOR=#ff0000]L[/COLOR]ubuntu is available for 32 bit but not [COLOR=#ff0000]U[/COLOR]buntu.

Ubuntu is one of the heaviest distros around and I would not recommend it for a Pentium 4 even if it were supported.

More info in the link in my signature.

---

### Post by Autodave on 2019-12-02
I may have missed it, but are you trying to dual boot this machine with Windows or are you getting rid of Win?

If you have followed the instructions for creating a bootable DVD, then my next guess would be that you got a bad download.

I would suggest that you download Lubuntu 32 bit and start over.

---

### Post by jim-holloman on 2019-12-02
> **mörgæs said:**
> The 18.04.3 [COLOR=#ff0000]L[/COLOR]ubuntu is available for 32 bit but not [COLOR=#ff0000]U[/COLOR]buntu.

Ubuntu is one of the heaviest distros around and I would not recommend it for a Pentium 4 even if it were supported.

Thanks again, mörgæs 

I D/L'ed Lubuntu 18.04.3 and created a DVD. 

Like the others, it will not boot (Non-System Disk)

I see no file on the DVD that would suggest that it is bootable.

I sure miss I knew what I am missing. Numerous web pages state that Ubuntu is easy to install. Thus far it has proven to be impossible to install.

---------------------------------------------------
 Volume in drive V is Lubuntu 18.04.3

08/05/2019  02:19 PM    <DIR>          .disk
08/05/2019  02:18 PM               231 README.diskdefines
08/05/2019  02:19 PM    <DIR>          boot
08/05/2019  02:19 PM    <DIR>          casper
08/05/2019  02:18 PM    <DIR>          dists
08/05/2019  02:19 PM    <DIR>          install
08/05/2019  02:19 PM    <DIR>          isolinux
08/05/2019  02:19 PM             5,633 md5sum.txt
08/05/2019  02:18 PM    <DIR>          pics
08/05/2019  02:18 PM    <DIR>          pool
08/05/2019  02:18 PM    <DIR>          preseed
               2 File(s)          5,864 bytes
               9 Dir(s)               0 bytes free
---------------------------------------------------

---

### Post by CatKiller on 2019-12-02
> **jim-holloman said:**
> There is no .exe file in the root? Should there be?
Why on earth would there be? 

Verify your download and your burn. There are hashes available for each.

---

### Post by jim-holloman on 2019-12-03
The problem has been resolved.

It turned out to be the DVD Drive. It would allow DVD Discs that were created years ago (perhaps on the same drive) to boot but would not allow DVD's that were created yesterday on a newer Windows 7 computer to boot . However, the drive would read any DVD; old or new.

Once I replaced the DVD Drive with a new one, all 7 of the DVD's that were created yesterday would boot.

Thanks for all the help.

---

### Post by mörgæs on 2019-12-03
Good, welcome to the free world.

---

