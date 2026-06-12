---
title: "[SOLVED] external usb ntfs hdd will not mount"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-12
Hi I have an external 320Gb USB HDD formatted in NTFS
When I plug it into my computer, I get the following message (attachment)
As you can see, the HDD is recognised automatically and in fact I have USB stick in FAT32 that mounts no problem.

I have tried to use NTFS config tool but to be completely honest, I did not know how to use it and it what I did try did not work.
I also tried the advice in the error message to no avail.

Can someone please help this newb :(

---

### Post by rampageoberon on 2008-08-12
You need to fix this in windows. So do a clean Safely remove hardware. or just shut down windows properly with the drive plugged in and running. That should hopefully fix things

---

### Post by NewDisciple on 2008-08-12
As the error msg from your screenshot indicates: you have your external usb hdd formatted as ntfs.  Linux can't read it.  You need to format it ext3, etc.  If you dual boot with windows then you will want to format as fat32 or fat16.  If you have data on it that you want to save, back it up on a windows machine.  Then you can use the partion editor of your choice to reformat it.

Forget what I just said.  See this thread: [http://ubuntuforums.org/showthread.php?t=886960]("http://ubuntuforums.org/showthread.php?t=886960")

---

### Post by balaknair on 2008-08-12
I had the same issue twice with my ext hdd(now formatted as ntfs). the disk would mount with Windows but not ubuntu. I'd accidentally unplugged the drive's power supply while it was mounted(in Windows) before the PC had completely shut down. If you have a Windows machine(or dual boot), plug the ext hdd into Windows and use the 'Safely remove hardware' function to unmount it(or simply shut down Windows with the drive plugged in). Usually this will work and the drive will then mount properly with Ubuntu. In my case the first time around, the drive had been formatted as FAT32(by the manufacturer), and the steps above didn't work, so I had to mount the drive in Windows, move all files on it to the PC HDD and then format the drive(this time as NTFS). When I made the same mistake the second time round, I just had to mount and 'Safely remove' under Windows to fix the problem. The external HDD with ext3 seemed to work without any issues throughout. You might consider formatting it with ext3 if you ever need to format it again(to access it within Windows use fs-driver [http://www.fs-driver.org/](http://www.fs-driver.org/) )

Hope this is helpful

---

### Post by bumanie on 2008-08-12
It should work fine once removed via 'safely remove device' in windows. Also the above post is correct, but I would advise sticking with the ntfs format as ntfs-3g (read/write to ntfs from linux)is more stable than fs-driver.

---

### Post by tarps87 on 2008-08-12
Although correctly unmounting the drive should work, if it does not try a program called Ntfs-Config for Ubuntu which will enable ntfs support for internal and external devices. This programs is in synaptic, just type ntfs in the search box.

---

### Post by nothingspecial on 2008-08-12
This fixed mine -


```
sudo apt-get install ntfsprogs
```

Then

```
sudo ntfsfix /dev/*where your drive is*
```

You can check where your drive is using

```
sudo fdisk -l
```(as in the letter L not number 1)

---

### Post by adambh on 2009-03-05
I had the same problem, safely remove drive in Windows fixed it for me, Thanks! :D

---

