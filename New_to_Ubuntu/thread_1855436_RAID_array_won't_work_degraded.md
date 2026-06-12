---
title: "RAID array won't work degraded"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by sailingboyLLB on 2011-10-06
I'm getting some hardware and building a NAS system and decided to grab 4 drives, load ubuntu and do RAID 5.  I haven't used raid before and I'm a little nervous about tying data to a RAID system or even a non-windows usable format (ext4).  So I decided to do a little test in a virtual machine.  I followed the instructions here [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) and successfully installed, booted, and tested some basic file operations and I was pretty pleased.  I wanted to see how easy/hard it would be recover from a failure.  So I tested it out by removing each one of the drives one at a time.

drive 1:
sda1 boot partition
sda3 data partition
sda5 swap partition

drive 2:
sdb1 boot partition
sdb3 data partition
sdb5 swap partition

drive 3:
sdc1 data partition

drive 4:
sdd1 data partition

all 4 data partitions are in RAID 5
the swap and boot partitions are each in their own RAID 1
  The actual drive letter changes when a drive is removed.

Removing drive 1 the system boots degraded without any issue.  If I shutdown add the drive back and boot, I can re-add it to the array and then the arrays are fine again.
   
  Removing drive 2 has the same result as removing drive 1
   
  Removing drive 3 the RAID 5 array won’t assemble automatically, and no amount of mdadm commands I’ve tried will fix it.  I examine the 3 drives in the array and they all look good, record the array device number, and try to assemble it, in the right order, using assemble.  I usually get an error saying that one of the devices is busy and doesn’t have a superblock.  I tried creating a new superblock and it says the device is not suitable for any style of array.  It hasn’t been mounted by the OS.  Dmsetup table does not list any devices as active.  The OS will boot, however.  Cat/proc/mdstat shows the array as inactive, but lists all 3 devices it needs to run degraded with a (S) next to each of them, I’m not sure what that means.  Shutting down, putting the drive back in, and starting up, everything works fine without additional effort.
   
  Removing drive 4 has the same result as removing drive 3
   
  I tried the usual suspects for help and couldn't find anything specific enough in the forums.  What’s going on here?

---

### Post by ubun2geek on 2011-10-06
You might want to post this in a more advanced section?
Just a thought. Best wishes! :)

---

### Post by sailingboyLLB on 2011-10-06
I didn't think this qualified as an advanced by linux standards.  in any event, i took your advice

new thread here for anyone following: [http://ubuntuforums.org/showthread.php?p=11317136](http://ubuntuforums.org/showthread.php?p=11317136).

---

### Post by sailingboyLLB on 2011-10-07
solution posted:
[http://ubuntuforums.org/showthread.php?t=1855708](http://ubuntuforums.org/showthread.php?t=1855708)

---

