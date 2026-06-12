---
title: "USB 3.0 speed &lt; USB 2.0"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by jalirious on 2013-06-18
Hello, I've a ux32a 12.04 laptop (all USB 3.0) 

I bought a sony micovault USB 3.0.
I have a sony microvault USB 2.0.

Both 8GB. Both FAT32.

The USB 2.0 copied a file at 34 mb/s.
Same (1.1GB) file for 3.0, only 17 mb/s.

Anyone know why?

---

### Post by hamishmb on 2013-06-18
Perhaps FAT32 doesn't support USB 3, as it's from around 2000, when USB 2 was just coming out? I'm not entirely sure if that's right, but perhaps trying EXT4 or NTFS would work better :)

---

### Post by jalirious on 2013-06-19
Hi Hamish, I just think the write speed is just ridiculously bad for this product. The default was FAT32, so it should work ok with that.

Thanks anyway :)

---

### Post by kurt18947 on 2013-06-19
It may also be that the USB3 chipset/driver combo is not optimum.  I think USB3 support in Linux is a little hit & miss still.  You could try the latest kernel or distro or enable backports to get the latest USB drivers if you're so inclined.  I had one 'USB 2.0' hard drive enclosure that would not sustain transfer speeds greater than 1.5 MB./sec, maybe running at USB 1.1 speeds?   I put the same drive in a different enclosure and attached it to the same machine.  Transfer speeds quadrupled or better.

---

### Post by Rebelli0us on 2013-06-19
Get USB 3.0 card reader (like Transcend RDF5) **and** UHS-I flash drive, it will read at 75 MB/sec.

---

### Post by sudodus on 2013-06-19
As stated in the previous posts, there are several reason why different USB drives can be so different: hardware as well as software  or firmware and the hand-shaking between the different parts of the chain to transfer data from one place to another place. There are good products and bad product, even products that are not according to the specification.

It also makes a big difference if there are many small files or a few big files. Many USB pendrives are very slow transferring  many small files. So if you plan to transfer a lot of data via USB, it often helps to make a compressed library or image before transferring (for example a tarball, zipfile or compressed image of a partition). It has also the advantage, that you can use a checksum to make sure that the transfer was good.

There is a factor of 4 between my first USB 3 pendrive and my USB 3 SSD, and there is a newer USB 3 pendrive in the middle. My first USB 3 pendrive is similar to today's fast USB 2 drives, but I was happy with it, because I had no USB 3 port anyway, and it was much better than my previous pendrives.

The flash memory can be very different, and often it is slower than the USB transfer chain for USB 2 as well as USB3. I suggest that you browse the internet when you plan to buy the next USB drive. Get one with read and write speed specified, and remember that the market is changing quickly, so use new information :-)

---

### Post by Alex_Gayer on 2013-08-15
I'm glad this topic is getting some attention.  In an effort to not start a new thread, I would like to express an issue I'm having regarding USB 3.0 in Ubuntu.  I'm not using thumb drives; they can be slow no matter where you use them.  Instead, I'm using a WD My Book, with a 3.5" SATA drive inside, NTFS formatted partition, USB 3.0 ready.  I'm also not working with small files, files are 250 MB or greater.  The issue is this:  I can write these files to the drive all day long in Windows at 120-130 MB/sec.  Not a bad speed.  I can copy files off the drive at 120-130 MB/sec too.  Looking good.  I mount the same disk in Ubuntu (on the very same machine), and start reading from the drive.  Again, I'm getting about 130 MB/sec.  This is great.  Then I turn around and start moving the files back to the USB drive and all of a sudden, I can't seem to get any more than 15-35 MB/sec.  Initially, I was using 64-bit Server Precise 12.04.2 LTS.  Tried updating everything to the latest.  Didn't help.  Then, I replaced my installation with the newer 64-bit Server Raring 13.04, and along with it came a newer kernel.  Same deal here too.  I was trying to move the data around on my disks so I could empty the external disk and upgrade it, but it's looking like an 1.5 hour backup will turn intIo a 6 hour restore.  This very same hardware (Motherboard, USB controller, hard disks, cables, etc) works as expected in Windows,  The OS is the only variable that has changed.  It seems as though I can read at USB 3.0 speeds, but only write at USB 2.0 speeds.  Is this documented anywhere?  Could it be a driver issue with my USB controller?  I would like to get this straightened out as I run a Gigabit Ethernet and have many users saving data to this disk.  I've saved data to the drive before over the Ethernet (SMB shares) and got speeds of 120 MB/sec, but I was running Windows at the time.  I would hate for this to be the bottleneck that slows everything down.  If I don't solve this problem, I may be cracking open the enclosure and mounting the drive as internal SATA.  But wait: Is there a limit to the speed you can write to an NTFS partition in Ubuntu or Linux in general?  Then mounting inside won't help...  I am tempted to try repartitioning the disk with multiple file systems and experimenting, but wanted to ask the forums first.  Any ideas?

Thanks in advance,
Alex

---

### Post by sudodus on 2013-08-15
Welcome to the Ubuntu Forums**[COLOR=#000000] [/COLOR]***Alex_Gayer  *:-)


Don't be afraid to start a new thread! It is almost always better than to add your questions to a new thread. In this case the thread has been sleeping for a couple of months.

My experience is that the linux drivers for ***NTFS*** are much slower than those for the own filesystems of linux. I would recommend ***ext4***.

There might also be problems with the speed writing to USB 3 drives, although I have good experiences with a USB 3 HDD.

---

### Post by Alex_Gayer on 2013-08-16
Thanks for your input.  I was thinking about changing over the file system since I don't move the drive anywhere; it stays attached to one specific computer.  I even have a custom mount point for it in fstab.  I am afraid that I will have to find a place to put my nearly 2 TB of data while I reformat, though I hear that Parted Magic might make life easier by performing a file system conversion for me.  I am already actively using ext4 on all of my other partitions, I guess maybe its just time to let go of NTFS.  I will try to take care of it in the coming days; I'll post my results.

---

### Post by Alex_Gayer on 2013-08-28
I couldn't find the tool in Parted Magic that was supposed to convert between filesystems.  And I didn't like the scary messages when I was about to shrink my NTFS partition to make room for a new ext4 partition, and move data over.  So, I bit the bullet, backed up my data, deleted my USB external hard drive partitions, and created a new ext4 partition in gparted.  I am now moving my data back over to the new volume and WOW.  It works so much better.  I can read and write at 160 MB/sec.  Thank you, sudodus!

---

### Post by sudodus on 2013-08-28
> **Alex_Gayer said:**
> I couldn't find the tool in Parted Magic that was supposed to convert between filesystems.  And I didn't like the scary messages when I was about to shrink my NTFS partition to make room for a new ext4 partition, and move data over.  So, I bit the bullet, backed up my data, deleted my USB external hard drive partitions, and created a new ext4 partition in gparted.  I am now moving my data back over to the new volume and WOW.  It works so much better.  I can read and write at 160 MB/sec.  Thank you, sudodus!

You are welcome :-)

---

