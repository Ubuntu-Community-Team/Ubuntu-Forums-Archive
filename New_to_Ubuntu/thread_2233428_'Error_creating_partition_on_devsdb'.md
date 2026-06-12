---
title: "'Error creating partition on /dev/sdb'"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by Miikka on 2014-07-08
Hello everyone, I am in need of some assistance. This is a long-ish story, so bear with me.

Few days ago I bought a new harddrive, and the physical installation went just fine. After the installation I booted up Win7 and went to format the newly installed disc, but somehow I accidentally misclicked and Windows decided to partition the whole harddrive as MBR. I quickly canceled it and restarted my computer only to find out that it wouldn't boot anymore.

I have tried changing the boot order from BIOS, but it doesn't seem to help at all. After fighting with Windows installation discs, Idecided to try Ubuntu via a USB stick, to see if I could format the drive that way. For some reason, it just won't work, here's the error message:

Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)

I have tried repartitioning the drive, but that won't work either, here's the error message for that:

Error creating partition on /dev/sdb: Command-line `parted --align optimal --script "/dev/sdb" "mkpart primary ext2 1MiB 2000398934015b"' exited with non-zero exit status 1: Error: You requested a partition from 1049kB to 2000GB.
The closest location we can manage is 1048kB to 1048kB.
 (udisks-error-quark, 0)

Can anyone help me with this?

I can, of course, provide more information if that's needed.

---

### Post by Bucky Ball on 2014-07-08
Welcome. It would help if you could tell us how you are trying to do this. You would generally boot from a LiveDVD/USB (the install media), Try Ubuntu option, once at a desktop launch Gparted (partition manager). Is that what you are doing? If not, please give more detail about your process ...

---

### Post by sudodus on 2014-07-08
I suggest that you try wiping the first megabyte of the new drive. Often a clean first megabyte makes the drive look clean (like you had not started to make an MBR system on it.

You can use ***mkusb*** to make that operation rather safe and convenient. See these links.

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

[http://phillw.net/isos/linux-tools/m...art-manual.pdf]("http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf")

---

### Post by Miikka on 2014-07-08
Bear with me, as I'm not very familiar with Ubuntu, but I'll try to explain. I made a bootable ubuntu USB stick with the directions provided by the Ubuntu site. Then I booted up Ubuntu, and chose the Try Ubuntu option. At desktop, I opened the search window from the upper left corner, and typed in disk. That took me to a window showing all the disks in my computer.

I have not used anything called Gparted, I guess I should try that then?

---

### Post by Bucky Ball on 2014-07-08
First, read and try sudodus's suggestion. Have a look in Gparted, though, and that will let you know what is still on that disk (as far as existing partitions). You'll know whether you've wiped it accidentally or not then and can take the appropriate course of action ...

---

### Post by Miikka on 2014-07-08
I tried launching Gparted, but it seems to turn up with an error after scanning for a long time. Here's the error;

Input/output error during read on /dev/sdb

This is very odd, something seems to be very wrong in the harddrive as nothing seems to be able to do anything about it... I'm thinking of removing the harddrive and then installing everything, and adding the harddrive again after that.


 Before I try messing around with mkusb, I'd like to make this clear, I want to format every harddrive on my computer. I'm going to do a clean install of Win7 on top of that. It's just that I need help doing that, as I can't access Win7.

---

### Post by sudodus on 2014-07-08
I think the 'Input/output error during read on /dev/sdb' is concerning your boot drive (the USB stick). It is configured in a special way, that gparted does not understand. If you have no problem with the internal drive, which is probably /dev/sda, all might be fine.

Is there any reason to think, that there are [other] problems with your computer? I mean not only this hard disk drive? What do you mean by 'as I can't access Win7'?

If you intend to format every harddrive, you need not be afraid to format the wrong one and wipe valuable information :-)

---

