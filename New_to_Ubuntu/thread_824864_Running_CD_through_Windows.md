---
title: "Running CD through Windows"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Grendel336 on 2008-06-10
I got my free Ubuntu CD in the mail yesterday. :grin:

I figure the safest way to break in is to run the CD from Windows via the CD-rom. 

Are there any limitations when doing this? Will there be things I can't do this way? 

Should I just go ahead and create a dual-boot system, or is learning off the CD and through windows gonna accomplish the same thing? 

I'm excited to learn a new OS that's not Windows or Mac. This will be my very first exposure to Linux/Ubuntu. 

Thanks in advance

---

### Post by avtolle on 2008-06-10
Puzzled by your post. You won't be able to "run" Ubuntu through Windows from the CD. You may, however, reboot the computer with the CD in the drive, and, if the BIOS boot order is set, boot from the Live CD and check it out. You may, if you desire, install through Windows using the Wubi installer, or you may partition your hard drive and install Ubuntu there for a "true dual boot". HTH.

I used the Wubi installer to install Ubuntu as a directory (folder) under Vista, allocating 15 GB of the HDD for the necessary virtual disk, and have been running 8.04 this way since, updating things as they show up, and, so far, so good. I'm aware of a bug with the newer kernels that, should you decide to go this way, could cause you a problem if your Windows install HDD is formatted anything but "pure" NFTS. See the Wubi Forum for more information on this.

---

### Post by TeoBigusGeekus on 2008-06-10
There is no way to "run the cd from windows". 
Either you run the live version of Ubuntu (boot up with the live cd and use ubuntu, though with limited performance) or go ahead and create a dual boot - the best way to my opinion.

---

### Post by forestpixie on 2008-06-10
I guess you are talking about the wubi thing - never used it, but have seen that it is slower than a real installation.

Have a play around, get to know the system and if you like go for the dual boot - it's how a good many have done it, including me.

There is a wubi forum which might be worth a look [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by wolfen69 on 2008-06-10
remember that running off the live cd is slower than a real install. cd access time is much more than hard disk. but you can install and tweak just like a real install, but will lose everything once you reboot.

---

### Post by issih on 2008-06-10
As I understand things you have the following options.

1) Boot from the cd and choose to try ubuntu without installing. This will run the live cd environment, you will be able to play about, but any changes you make are lost when you reboot, as everything runs from the cd and ram.

2) Boot from the cd and do a dual boot install, actually install ubuntu to your hard drive making new partitions and resizing windows etc. (N.B. This can be dangerous if you don't know what you are doing)

3) From windows run the cd and install using wubi. I haven't used this, but as I understand it, it basically creates the equivalent of a dual boot machine, but the actual files are installed within the windows file structure. You can therefore remove the installation treating it as a normal windows program.

In order to use the wubi installation you reboot, and select ubuntu from the options.

Limitations are that you can't hibernate the pc and that the ubuntu filesystem is more susceptible to errors if you perform a hard reset.
(this according to [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))) 

If you are new to it all then wubi seems like a good bet, I'd have gone for it if I had the option when I started.

Hope it works out well :)

---

### Post by Grendel336 on 2008-06-10
Sorry for the confusion. Here's what the instructions on the CD say:

> Put the CD in the drive while Windows is running and select "Install Inside Windows". 

---

### Post by avtolle on 2008-06-10
> **Grendel336 said:**
> Sorry for the confusion. Here's what the instructions on the CD say:
That is referring to use of the Wubi installer. FYI, performance is good, about the only difference from an actual installation in a dedicated partition is slightly slower hard drive access. As I said, I've used this to get used to 64 bit 8.04, and have had no troubles. I feel it is one way to get used to the software, play around, etc., and learn. Others have had difficulties. You might want to take a look at the Wubi Forum here to read the various threads, which range from "It's Great!" to "How Do I Get Rid of It?" and all intermediate steps. Good luck, regardless of how you decide to go.

EDIT: [http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=234](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=234) is link to the Wubi Forum.

---

### Post by Grendel336 on 2008-06-10
I just discovered I have a 32 bit system, even though it's a Vista OS and a Core2 Duo Intel chip. 

But I got the 64 Bit Ubuntu CD.


My guess is that's a small problem. ](*,)](*,)

Guess I'll work the download over the weekend. 

The CD did boot up but I was unable to connect to internet once Ubuntu got rolling. 

I have a Dell Inspiron E1505 laptop.

---

### Post by mgmiller on 2008-06-10
You will have a much easier time if you use the 32 bit ubuntu CD.

If you do decide to do a dual boot, it is strongly recommended that you defrag your windows drive first.  In fact, do it a few times to make sure it's really clean.  The second or third defrags run very quickly.

I just converted 3 of the computers in my office to dual boot and if I don't defrag them first, I get all kinds of errors on trying to install ubuntu.  After defragging, all went smooth as silk, so just defrag before trying to insatall.

You will never have to defrag the ubuntu partitions on the drive.  The ext3 file system does not fragment the way ntfs does.

Good luck and welcome to the ubuntu forums.

---

