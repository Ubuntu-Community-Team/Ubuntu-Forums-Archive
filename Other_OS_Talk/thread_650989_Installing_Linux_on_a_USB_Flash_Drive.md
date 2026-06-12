---
title: "Installing Linux on a USB Flash Drive"
date: 2007-12-27
forum: Other OS Talk
---

### Post by Bionic Apple on 2007-12-27
I need everyone's expertise on a little project I have been doing (not really a project, but read on).  I want to do the following:

1. Split my 8 gb drive into 3 gb and a 5 gb partitions.

2. Put the most complete USB-based Linux into the 3 gb partition.

3. Let Windows use the 5 gb partition for data storage.

Sounds simple, right?  Well, I tried to do those steps with Flash Linux and it went horribly wrong.  When trying to boot Flash Linux all I that was displayed was "Grub _"  in the BIOS.  Then, I tried to use the other 5 gb (pre-formatted into FAT32) in Windows XP.  It totally ignored my 5 gb partition and told me I had to reformat the whole drive into FAT32.  I haven't done it yet.

What I was thinking: I selected Flash Linux from [[COLOR="Navy"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Live_USB") under the "Full Linux installations" section.  I used the guides over at [[COLOR="Navy"]http://flashlinux.org.uk[/COLOR]/]("http://flashlinux.org.uk/") for the Linux Installation and then used Gparted to resize it to 3 gb and make a 5 gb FAT32 partition.

Help would be appreciated!

P.S.  I posted this in here because there are no forums at the website for Flash Linux and I used Ubuntu for the installation.  Plus, I don't know which Linux to get so I posted this in the General OS Talk.

---

### Post by icheyne on 2007-12-27
Maybe first try using the [gparted livecd]("http://gparted-livecd.tuxfamily.org/") to set the partitions up and then use [Puppy Linux]("http://www.puppylinux.org/") - that's by far the best Live distro I have tried.

---

### Post by DenisTheinert on 2007-12-27
install your ubuntu  and then 

find -x / | cpio -pmd /mnt/usb

also i installed freebsd on a usb stick with this command
im not sure how it is with linux but the command should not be so diffrent ;)

it might work good luck and let me know if it works ;)

---

### Post by Bionic Apple on 2007-12-28
Well, now I have a new problem.  Everytime I format my USB drive to be ext3 or fat32 (regardless if that partition is the only one) Puppy Linux doesn't see that I have formatted it.  It still stays it detects no MBR and no partition to work with, so it tells me I need to format the whole entire drive.  Of course, that is not an option.

---

### Post by Bionic Apple on 2007-12-30
What should I do?

---

### Post by new2*buntu on 2007-12-30
> **icheyne said:**
> Maybe first try using the [gparted livecd]("http://gparted-livecd.tuxfamily.org/") to set the partitions up and then use [Puppy Linux]("http://www.puppylinux.org/") - that's by far the best Live distro I have tried.

I agree with this post that Puppy is the best Live distro. But I don't think that you will need the GParted Live CD since GParted is in Puppy. Actually, I am typing this from Puppy, booted from a USB. Puppy even includes a "universal installer" which makes it easy to install to any kind of removable media or the hard drive. Just my 2cents

---

### Post by init1 on 2007-12-30
I recommend booting your pendrive with Syslinux, because it allows you to use a fat32 filesystem. This way you only need one partition. The tutorial here is really easy.
[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)
If you prefer a pre made system, try these images.
[http://live.debian.net/cdimage/etch-builds/current/i386/](http://live.debian.net/cdimage/etch-builds/current/i386/)
Copy them over to your pendrive with this
```

dd if=/path/to/the/image/you/want.img of=/dev/yourpendrivedevice

```
This will write over a portion of your pendrive, so any important data should be backed up. 
Make sure that use your pendrive device and not your hard drive device. 
You will probably want to expand the partition after using one of the Debian Live images 
There are many other good pendrive Linux distributions but they many be a bit harder to setup.
[http://www.finnix.org/](http://www.finnix.org/)
[http://grml.org/](http://grml.org/)
[http://www.mcnlive.org/](http://www.mcnlive.org/)

Also, I never use Puppy, mainly because it doesn't support my laptop's NIC.

---

### Post by Bionic Apple on 2008-01-26
All of that sounds a little complicated, init1.  Plus, I prefer Puppy ever since I tried the Live CD.  But, I will consider those options if all else goes wrong.  Regarding Puppy though, I still don't know why Puppy won't detect my ext3 partitions I make for it.

---

### Post by wolfen69 on 2008-01-26
why not put ubuntu on it?  [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
i did it, and it's awesome. i also have another flash drive with mint on it.

btw, how can anyone say puppy is the best live cd? the mint live cd has all codecs, flash, java, auto mounting of drives, open office, amarok, etc. does puppy have all that? what can the puppy cd do that mint cant? (besides run on a computer with little memory)

---

### Post by smartboyathome on 2008-01-26
I use puppy because it has tons of stuff which does the same functions as the corrisponding Mint programs, but is very small in size. It doesn't need open office, amarok, flash, java, or codecs, as they can be installed after (very easily), and needs to be small. I find that if I install either Mint or Ubuntu on my USB drive, I have very little space for anything else.

---

### Post by wolfen69 on 2008-01-27
> **smartboyathome said:**
>  I have very little space for anything else.

that is easily solved by getting a bigger drive. :cool:

---

### Post by Bionic Apple on 2008-01-27
I simply want a Linux Distribution which will run well on every PC I will encounter while completely saving my data.  Puppy Linux seems exactly suited for that job.

---

### Post by init1 on 2008-01-27
> **Bionic Apple said:**
> I simply want a Linux Distribution which will run well on every PC I will encounter while completely saving my data.  Puppy Linux seems exactly suited for that job.
I doubt such a distro exists. That's why I have several live USB pen drives that I carry around. Puppy works on most of the computers I've tried it on but not all.

---

### Post by Antman on 2008-01-27
> **wolfen69 said:**
> that is easily solved by getting a bigger drive. :cool:

That's Microsoft logic..... The beauty of small yet functional distros is that you can use your **existing** hardware.:guitar:

---

