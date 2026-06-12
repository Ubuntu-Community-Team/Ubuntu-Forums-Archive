---
title: "Trouble installing Ubuntu alongside Windows 10"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by laurynas_miseviciu on 2016-01-31
I urgently need help, I've spent about 3 hours trying to figure it out and try different methods online. I've partitioned my drive on windows 10, so there's enough to install Ubuntu on my SSD. I'm using an ASUS laptop, and I need ubuntu for my project work.
I've used Rufus to burn the ISO onto my USB. And my BIOS is Legacy mode.
Whenever I try install it, it doesn't detect my operating system, so I dont get the option to boot along side it. Also the "something else" option I failed to get working.

Please please help people please :(

---

### Post by Vladlenin5000 on 2016-01-31
Hi and welcome.

1. Don't go legacy unless you installed Windows 10 the same way; any factory installed Windows 10 is UEFI.
2. In Windows disable fastboot; shutdown.
3. Boot the USB installation media in the exact same way Windows is installed - as mentioned before -.

---

### Post by grahammechanical on 2016-01-31
> I've partitioned my drive on windows 10, so there's enough to install Ubuntu

Did you create partitions or create unallocated space for Ubuntu? If you created partitions were they in the Ext4 format or a Windows format? Run the Ubuntu live session. Open GParted and take a screen shot of what GParted shows as your partitions and post the image in this tread. You can also do this in Windows 10 is you like.

Regards.

---

### Post by laurynas_miseviciu on 2016-01-31
The windows 10 isn't exactly legitimate...sorry, and I cant change the legacy mode to UEFI or anything :/

Its as unallocated, and 69gb of it. How do I assign the ext4 or whatever?

I changed the parition and named it ubuntu and edited it on the live session, to ext4 journaling file system, and put the mount point as /home
I try to install and says no root file system is defined, but im using the "something else" option.
It doesnt detect my windows

OKay ill try that out now

---

### Post by Vladlenin5000 on 2016-01-31
> **laurynas_miseviciu said:**
> The windows 10 isn't exactly legitimate...sorry, and I cant change the legacy mode to UEFI or anything :/

You shouldn't have mentioned it and it doesn't matter... Again, what matters is how it was installed in the first place and if you did the installation then you must know your hardware (whether or not it is UEFI capable) and how you installed it (UEFI or Legacy). Just boot and install Ubuntu the same way.


> Its as unallocated, and 69gb of it.

Good.


> How do I assign the ext4 or whatever?
You don't. It's a file system like any other so you make a partition (or more) and _format_ it to EXT4. You can and should do it with the "Something Else" option: Create one new partition for root (/) using the whole unallocated space minus what you need for the swap partition (some 2GB should be enough if you don't intend to hibernate - and you shouldn't -; the same as RAM otherwise).


There are some basic stuff you need to know in order to install operating systems otherwise an unbootable system is almost certain.

---

### Post by Vladlenin5000 on 2016-01-31
> **laurynas_miseviciu said:**
> I changed the parition and named it ubuntu and edited it on the live session, to ext4 journaling file system, and put the mount point as /home
I try to install and says no root file system is defined, but im using the "something else" option.
It doesnt detect my windows

That's exactly what I meant with the last paragraph of my previous post...

You need two partitions for Ubuntu (or any other Linux)... The second one (swap) is debatable... Neither are /home.
You can have /home as a separated partition but you must have / (root). That's what the error message was complaining about.
Usually in this day and age people don't have a separated /home because there are no compelling reason for the added complexity.
Again,
Partition 1: / (/home lives inside /)
Partition 2: swap (no mount point)

---

### Post by laurynas_miseviciu on 2016-01-31
So, from what I understand, I have to shrink the unallocated partition to make another unallocated partition for the swap?

---

### Post by Vladlenin5000 on 2016-01-31
No, geez...

There's NO such thing as an "unallocated partition" (really?). Unallocated _space_ is what it is, EMPTY, it isn't a partition and has no partitions otherwise it would be ALLOCATED!
Moving on... In that unallocated space you need to _create_ just two partitions as mentioned before (again, Something Else option) and by doing that the space will no longer be unallocated (you just allocated it, entirely or partially, to one or more partitions).

---

### Post by yancek on 2016-01-31
> So, from what I understand, I have to shrink the unallocated partition to make another unallocated partition for the swap? 				

In the Installation Type window, you should see your partitions and the unallocated space.  Click unallocated space to highlight it then click Add or the + button and you should then see and Edit partition window.  Select the mount point: /, which is the symbol for the root filesystem.  In the size, do not use all of the unallocated space but leave 2-4GB or whatever you want for the swap partition and repeat the process.  There is a 'swap' option in the Mount point drop down under Mount point.

---

### Post by Geoffrey_Arndt on 2016-01-31
Here's a good video tutorial . . . make using gparted simpler for the new user.

[https://www.youtube.com/watch?v=O5kh_-6e4kk](https://www.youtube.com/watch?v=O5kh_-6e4kk)

---

### Post by laurynas_miseviciu on 2016-02-01
Yeah, So I've installed Ubuntu over windows, But i have windows10 on my usb,and have 61gb free partition for fat32 on it

---

