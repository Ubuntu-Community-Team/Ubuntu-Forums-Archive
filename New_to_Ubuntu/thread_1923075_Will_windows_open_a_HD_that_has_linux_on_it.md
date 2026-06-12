---
title: "Will windows open a HD that has linux on it?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by wzfreeman on 2012-02-09
I installed Ubuntu 11.10 on a new SSD (Corsair Force Series 3 120GB) about a week ago. This was my first experience with linux (and thus far I am quite happy) so in my ignorance I payed little attention to where things were installing. Now that I have a better understanding of the how the file system on linux works I would like to wipe the drive and start over, and do thing more cleanly this time.

When I plug the SSD into my desktop, which is running windows 7, I am unable view any files on the HD despite the fact that it shows up in the device manager. 

I would greatly appreciate any help with this problem, or alternate solutions. 

Thank you.

---

### Post by sammiev on 2012-02-09
You should be able to share some folders with windows but likely that would be just about it. Windows is NTS and Linux is other. Apples and Oranges can share a basket but never taste the same. :)

---

### Post by Bartender on 2012-02-09
Windows will not recognize Linux partitions.

If you just want to wipe the drive, I'd suggest going to [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and making a bootable CD.  Boot from the CD, so that you're not using Windows, and wipe the drive.

From there you've got multiple options.  The simplest thing to do is format the drive as one big primary ext4 partition.  Then it'll be ready for a Linux install.

---

### Post by Cheesemill on 2012-02-10
Why do you need to access it from Windows?

If you are just going to re-install Ubuntu on the entire drive just boot from a Live CD and select 'Use entire drive' during the installation process.

---

### Post by catlover2 on 2012-02-10
If for some reason you do want to access EXT2/3 partitions from windows, ext2fsd has worked well for me.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by forrestcupp on 2012-02-10
[Ext2Read](http://sourceforge.net/projects/ext2read/) can read ext4 filesystems in Windows.

---

### Post by d4m1r on 2012-02-10
> **forrestcupp said:**
> [Ext2Read]("http://sourceforge.net/projects/ext2read/") can read ext4 filesystems in Windows.

Yes it can. Basically without it, your Windows partition won't even realize you have another partition with Ubuntu installed.

The only catch with Ext2Read is that it is exactly that, read-only access to your linux files from Windows (so you can copy/paste from it, but not to it).

---

### Post by catlover2 on 2012-02-11
> **forrestcupp said:**
> [Ext2Read]("http://sourceforge.net/projects/ext2read/") can read ext4 filesystems in Windows.


Ext2fsd includes a utility to mount assign drive letters to EXT partitions, so they can be used like a natively supported file system. It even has write support.

---

### Post by Jagoly on 2012-02-11
Just thought I might add, OS reinstalls aren't the best things for an SSD's Lifespan, so try to limit them

-------------------------------------
Proud owner of a force series 3 60gb

---

### Post by mastergkage on 2012-02-11
> **Cheesemill said:**
> Why do you need to access it from Windows?

If you are just going to re-install Ubuntu on the entire drive just boot from a Live CD and select 'Use entire drive' during the installation process.

Maybe he just need to see what the files looks like from a windows points of view:P

---

### Post by forrestcupp on 2012-02-11
> **catlover2 said:**
> Ext2fsd includes a utility to mount assign drive letters to EXT partitions, so they can be used like a natively supported file system. It even has write support.

I used to use that a long time ago, and I loved it. But I didn't think it supported ext4, which is the default now. Does it support ext4 now?

---

### Post by Cheesemill on 2012-02-11
> **forrestcupp said:**
> I used to use that a long time ago, and I loved it. But I didn't think it supported ext4, which is the default now. Does it support ext4 now?

By default ext4 support is read only but you can force read/write support if you want to (although it's not recommended).

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by catlover2 on 2012-02-11
> **Cheesemill said:**
> By default ext4 support is read only but you can force read/write support if you want to (although it's not recommended).

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)
Never had any problems with writing to EXT4 partitions myself.

---

