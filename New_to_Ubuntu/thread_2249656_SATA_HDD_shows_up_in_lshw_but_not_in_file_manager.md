---
title: "SATA HDD shows up in lshw but not in file manager"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by nick155 on 2014-10-23
Hi everyone,

I'm a pretty big Ubuntu and Linux rookie here so this might be a quick and obvious answer that I just don't know about yet.

I'm running Ubuntu 12.04 LTS off of a USB thumb drive. I'm trying to access a physical HDD on the computer via the file manager to pull some data off of it. I've done this exact process before on another computer with great success (it automatically added the physical HDDs to the file manager). But this time it's refusing to show the physical HDD.

I ran "sudo lshw -C disk" and the drive in question does show up:

*-disk
    description: SCSI Disk
    physical id: 0.0.0
    bus info: scsi@3:0.0.0
    logical name: /dev/sda
    size: 931GiB (1TB)

How can I access this drive? 

Thanks for reading my post, it's probably a really elementary question but I'm totally new to Ubuntu and Linux :(

---

### Post by oldfred on 2014-10-23
You do not mount disks but partitions.

Post this from terminal in Ubuntu:

sudo parted -l

If it is Windows 8 and hibernated (fast boot) or needs chkdsk, the Linux NTFS driver will not mount it by default. It does not want to let you damage it, so chkdsk could then maybe not be able to fix it.

There is a way to force mount in read-only mode. But better to make sure hibernation is off and chkdsk not needed first.

---

### Post by nick155 on 2014-10-23
Fred,

Thanks for the response. That command gave me the following output:

"Error: /dev/sda: unrecognized disk label"

The reason I'm trying to access this disk is that it is giving me a SMART error on bootup and will not boot into Windows (it hangs indefinitely on the Windows loading screen). What I'm trying to do is pull off all of the important data before trashing the disk. I've done this method once before to pull data off of a corrupted Windows install and it worked beautifully. Could it simply be possible that the HDD in the current scenario is too far gone to salvage any data off of?

---

### Post by oldfred on 2014-10-23
Did you look at Disks or Disk Utility. With Disks now you click on the icon in the upper right corner for more tasks and can select Smart Disk to see status.

If BIOS will not mount drive there is no way to recover data. Is BIOS seeing drive?

       sudo mkdir /media/windows
sudo mount ntfs-3g -o rw /dev/<device-name> /media/windows
if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount
But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows

Another user did this to remount. 

 mkdir /media/win
sudo ntfs-3g -o ro /dev/sda1 /media/win
# remount read only This worked for my mp3 player that default mount would not write to
# sudo mount ntfs-3g /media/PEARL -o remount,rw,noatime

---

### Post by whitesmith on 2014-10-23
If the data on this drive is *really* important you might investigate SpinRite. It isn't FOSS by any manner of means. I believe the current price is around $75, but it's worth every penny if you're drowning. I could be wrong but SpinRite  doesn't seem to require more than a BIOS that can boot Free DOS. That way it can handle HDDs formatted to accomodate virtually any OS--Linux, Windows, OS/2 (!), and even some games. The product is simply unbelievable. The manufacturer is a small company still operated by the original developer, Steve Gibson. Check it out! If there's data there SpinRite will find it.

---

