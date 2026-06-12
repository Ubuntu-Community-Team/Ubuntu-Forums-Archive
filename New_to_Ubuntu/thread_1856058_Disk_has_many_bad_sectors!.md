---
title: "Disk has many bad sectors!"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by johnuk on 2011-10-07
I've been having bad sector messages too.

I've been using this desktop for a few years on unbuntu with zero disk issues.

Last night, I plugged a 3TB external drive into the USB port to partition it for the TV.

When I tried booting the computer, it halted after the bios screen - absolutely nothing happening. Monitor is displaying 'no signal' and the power button is back in on/off with no delay.

I left it for half an hour thinking it might be struggling with the 3TB disc, came back, nothing.

I unplugged the external drive and switched it back on.

Nothing. Left it for an hour. Still nothing.

I got out the LiveCD and booted it through that.

Once back in the OS, I could see both the external drive and the normal internal drive. The internal drive seemed fine. All the partitions were still there, as normal, all the files and it was still marked as boot - but seems to be refusing to do so.

I downloaded Hirens disc and ran the bad sector tool.

After about an hour, it hit the last 2% of the disc and started bleeping as it bumped into bad sectors, but seemed to managed to fix the 120 odd it found.

I tried booting again without any discs in. Still nothing.

I've never received these sector warnings until plugging the external drive in. It could be coincidence it's found them at that exact moment, but it wasn't even booting to find them in the first place.

I am kind of at a loss as to what's happening. I don't think it's bad sectors, the partitions are still there, the drive is still readable and marked as bootable, but all that happens is I see 'Packard Bell, press xxx to enter', then black screen and no signal.

If I had an error message I could do some googling, but nothing on monitor beyond it's own 'no signal' message. And nothing going on with the drives.

---

### Post by oldos2er on 2011-10-07
Post moved to its own thread. Please try not to post in threads more than a year old, also state which version of Ubuntu you're using.

---

### Post by Mark Phelps on 2011-10-08
From what I've read, 3TB drives can not just be plugged into SATA ports and be recognized properly.  They're too large for some SATA drivers to understand correctly.

---

### Post by egalvan on 2011-10-08
> **johnuk said:**
> 

I've been using this desktop for a few years on unbuntu with zero disk issues.

 I plugged a 3TB external drive into the USB port to partition it for the TV.
 but all that happens is I see '[COLOR="Red"]Packard Bell[/COLOR], press xxx to enter', then black screen and no signal.



Exactly HOW old is that machine? I haven't seen a functioning Packard Bell in a coon's age..  :eek:

---

### Post by Lisiano on 2011-10-08
> **egalvan said:**
> Exactly HOW old is that machine? I haven't seen a functioning Packard Bell in a coon's age..  :eek:

[http://www.packardbell.co.uk/pb/en/GB/content/home](http://www.packardbell.co.uk/pb/en/GB/content/home)
They still exist.


> **johnuk said:**
> I am kind of at a loss as to what's happening. I don't think it's bad sectors, the partitions are still there, the drive is still readable and marked as bootable, but all that happens is I see '_**Packard Bell**_, press xxx to enter', then black screen and no signal.
I think thats a disk name and mount is asking what to do with it since it can't find it (UUID Change probably for some magical reason). Grab a LiveCD, open a terminal and type
```
sudo blkid -c /dev/null
```
Now compare the line with /dev/sda (Or sdb) with the line for / in /etc/fstab
```
cat /media/disk/etc/fstab
```
Where /media/disk is where the disk is mounted at.
If the UUID match, then I don't know what it might be. If they don't, note down the old one (Or comment it by putting a # (Hash) in front of the line) and replace the UUID.
```
sudo nano /etc/fstab
```
So it looks something like this
```
# / was on /dev/sdd5 during installation
# UUID=<Old UUID> /               ext4    errors=remount-ro 0       1
UUID=<New UUID> /               ext4    errors=remount-ro 0       1
```
Now reboot and see if the error persists, if not, glad it helped. If it persists, undo the UUID change in /etc/fstab

---

