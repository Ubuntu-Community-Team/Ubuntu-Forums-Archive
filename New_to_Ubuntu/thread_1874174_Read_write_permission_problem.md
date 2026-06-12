---
title: "Read write permission problem"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by rimibchatterjee on 2011-11-02
I have a rather odd problem. many years ago, my old windows install was infected with some sort of USB drive boot virus. This did nothing, and could be removed by going to dos prompt, finding autorun.inf on the usb drive and deleting it. However, by some means I'm not entirely sure I fathom, the virus would then reset the permissions for the USB drive to read only. You then had to fix this using the attr coimmand (if I recall correctly) with the appropriate arguments. 
So now I've upgraded to Ubuntu 11.10. I plugged in my USB 1TB flash drive and lo and behold, it had a suspicious-looking autorun.inf on it. I deleted the file, but then found the file system had been converted to read only, confirming my suspicions. I went to comand prompt and did ls -l and got the list of permissions for the drive, which was dr-x------
Nothing daunted, I set about researching the Linux equivalent of attr. I foudn it was chmod, in the form chmod ugo+rw [Drive Name]. However this did not work. Neither did chmod 777 [Drive Name]. These got me the message 'changing permissions for [Drive Name]. Read only file system.' However ls -l showed no change.
The disk is NTFS and I want to continue using it with both WIndows and Linux. I suppose I could schlep all the files over to the system hard drive, format the damn disk and schlep it all back again. But surely Linux must have a better way?

---

### Post by ledzepp817 on 2011-11-02
I had an issue sort of similar to this when I was adding my USB external HDD.
 
It wasn't a chmod that fixed it, it was a mounting issue.  I think I fixed it by umounting the usb drive then mounted it again by 
 
sudo mount -t ntfs-3g -o uid=1000,gid=1000,umask=0022 /dev/sd# whatever [mountpoint]
 
 
I may be off with what you are looking to do but just my two cents.

---

### Post by ajgreeny on 2011-11-02
In your situation you would need to use ```
sudo chmod .....
```The drive will also not be able to be changed with a ```
chmod 777 /dev/sdx
``` command but will need the mountpoint folder name.  It is therefore worth labeling the partition on the disk so that it always mounts to the same mountpoint, /media/*labelname*

---

### Post by coffeecat on 2011-11-02
> **rimibchatterjee said:**
> 
Neither did chmod 777 [Drive Name]. 

...

The disk is NTFS

NTFS is a Microsoft filesystem which has an entirely different permissions system than Linux, so chmod will not work on it. The only way to change permissions of NTFS drives (or FAT32) in Linux is to change the mount options. However....

If you are plugging a NTFS drive into 11.10 and it is being automounted read-only, the most likely explanation is that you have lost the package ntfs-3g. This is going missing when users mistakenly install the ntfsprogs package, which is no longer needed in 11.10. Or possibly ntfs-3g is being lost in a bad update, but I'm not so sure about that.

Whatever, check that you have ntfs-3g installed and, if not, install it. You cannot mount a NTFS filesystem read-write without it.

---

### Post by rimibchatterjee on 2011-11-02
Some clarifications.
My drive worked fine until I deleted autorun.inf
The mount point was always /media/Expansion\ Drive
After trying unsuccessfully to change the permissions, I copied all of my stuff to the hard drive and formatted the USB disk. However it was still read only! I then ported it into a windows system checked for viruses (none found) and formatted it by quickformat as NTFS on windows. When I tried to mount it on my Linux system again, it said Cannot mount volume format unrecognised. I am formatting it again on Windows without using quick format to see if that works. 
One weird thing is, when I ported the blank formatted disk on windows, it detected 9 files

---

### Post by rimibchatterjee on 2011-11-03
I have installed ntfs-3g, thank you for that. One step closer to a solution. I found a bunch of commands including blkid, etc to use in another thread, and ran them to get info on my disks as follows:
  	 	 	 	 	rimi@rimi-Lenovo-G560:/media/Seagate$ sudo blkid  /dev/sda1: UUID="9fdeba66-91b6-45bf-8e91-519d7f7bc55f" TYPE="ext4"  
 /dev/sda5: UUID="0dac5390-2b82-4a84-be02-54da5c326a51" TYPE="swap"  
 /dev/sdb1: LABEL="Seagate" UUID="508005CC2C9D7BD1" TYPE="ntfs"  
 rimi@rimi-Lenovo-G560:/media/Seagate$ sudo cat /etc/fstab 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sda1 during installation 
 UUID=9fdeba66-91b6-45bf-8e91-519d7f7bc55f /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=0dac5390-2b82-4a84-be02-54da5c326a51 none            swap    sw              0       0 
 rimi@rimi-Lenovo-G560:/media/Seagate$ sudo fdisk -l # 
  
 Disk /dev/sda: 640.1 GB, 640135028736 bytes 
 255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x0009ea61 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *        2048  1244252159   622125056   83  Linux 
 /dev/sda2      1244254206  1250263039     3004417    5  Extended 
 /dev/sda5      1244254208  1250263039     3004416   82  Linux swap / Solaris 
  
 Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x000cd67c 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1            2048  1953523711   976760832    7  HPFS/NTFS/exFAT 
 
The next step in the process described in the other thread was editing fstab, but the parameters were different. i'm not sure if I copy what was in that thread verbatim I will get the right results. Could someone look at my info above and tell me what the correct edit should be to turn my sdb1 into a read write disk from a read only disk?:confused:
This is really beginning to bug me

---

### Post by coffeecat on 2011-11-03
> **rimibchatterjee said:**
> The next step in the process described in the other thread was editing fstab,

You only need bother to do that if you want the drive mounted with special mount options. For 99+% of the time, simply plug the external NTFS drive in and it will be mounted read-write automatically. That's so long as you have ntfs-3g installed, and so long as you haven't installed any package in the repos that allegedly help with automounting - they mostly hinder. All the functionality you need is built into a default install of Ubuntu.

---

### Post by rimibchatterjee on 2011-11-03
My drive is still mounting as read only. this is the content of my fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9fdeba66-91b6-45bf-8e91-519d7f7bc55f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0dac5390-2b82-4a84-be02-54da5c326a51 none            swap    sw              0       0

should that errors=remount-ro thing be there? And I don't see sdb1 at all.

---

### Post by coffeecat on 2011-11-03
> **rimibchatterjee said:**
> My drive is still mounting as read only. this is the content of my fstab

Forget fstab for now. That will just complicate things. If your NTFS drive is being automounted read only by the system, something is wrong. Off the top of my head, one or more of these:

1 - ntfs-3g is missing, We can discount that. You say you've re-installed it.

2 - The filesystem is damaged, in which case Ubuntu will mount it read-only.

3 - You've changed udev configuration rules.

4 - You've installed a 3rd party application (for example usbmount) that interferes with - well - USB mounting (in GUI systems).

I'm sure there are other causes. Are you getting an error message? Let the system automount the drive and post the terminal output of:

```
mount
```

---

### Post by rimibchatterjee on 2011-11-03
no error message on mounting. any attempt to write a file to the disk or delete an existing file gets Unable to perform function, disk is read only

This is what i got out of mount
etc/fstab
rimi@rimi-Lenovo-G560:/media/Seagate$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rimi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rimi)
/dev/sdb1 on /media/Seagate type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

---

### Post by coffeecat on 2011-11-03
Well - here's your problem:

> **rimibchatterjee said:**
> This is what i got out of mount

....

/dev/sdb1 on /media/Seagate type [COLOR="Red"]ntfs [/COLOR]([COLOR="Red"]ro[/COLOR],nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

ro= read-only. Also type = ntfs suggests it's using the kernel read-only ntfs driver. Double-check that ntfs-3g has installed properly.

Just to compare, I've just plugged a USB drive formatted NTFS into this Ubuntu 11.10 system. My external NTFS partition is also sdb1. Here's the equivalent line of my mount output:

```
/dev/sdb1 on /media/Fujitsu120 type [COLOR="Red"]fuseblk[/COLOR] ([COLOR="Red"]rw[/COLOR],nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

type fuseblk is what you would expect to see with the ntfs-3g driver and rw=read-write.

I'll have a think and look around and see if I can find something else relevant for you.

---

### Post by coffeecat on 2011-11-03
> **coffeecat said:**
> I'll have a think and look around and see if I can find something else relevant for you.

I tried an experiment. I uninstalled ntfs-3g, plugged my NTFS USB drive in and mount gave me:

```
/dev/sdb1 on /media/Fujitsu120 type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
```

Identical (except for the mountpoint) to what you are getting. Mounted read-only. Then I unmounted the drive, re-installed ntfs-3g, plugged the drive in again, and this time mount gave me:

```
/dev/sdb1 on /media/Fujitsu120 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Identical to what I got before - mounted read-write.

I know you said you installed ntfs-3g, but you need to re-check this. It works with ntfs-3g; read-only without.

By the way, I know I've already said this but it bears repetition. Do not try to install ntfsprogs. I don't know whether this is the problem here, but you don't need it (all the functionality previously supplied by ntfsprogs in earlier versions of Ubuntu is included in ntfs-3g now) and it removes ntfs-3g.

---

### Post by fredric_ on 2011-11-03
Try this:

sudo umount /dev/sdb1
sudo mkdir /media/Fujitsu120
sudo mount -o defaults /dev/sdb1 /media/Fujitsu120

---

### Post by rimibchatterjee on 2011-11-04
Fredric_
I have no idea what you did, But i tried these three lines of code and I can now copy to my disk! 
YAYAYAY!:guitar:
Except now it shows as Seagate on Nautilusbut but when I copy it says copying *.* to "Fujitsu120". Not that I care, But is it a good idea ot fix it, and if so, how? Edit fstab?
Thanks

---

### Post by rimibchatterjee on 2011-11-04
I now seem to have a writable disk, except it thinks it is called Fujitsu120 :)
I tried running sudo apt-get install ntfs-3g and got this message
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
I expected to be told it was already installed. So maybe there is a problem with ntfs-3g. How do I uninstall? type sudo apt-get uninstall ntfs-3g?

---

### Post by fredric_ on 2011-11-04
The commands are to remount the partition using default options that are rw, suid, dev, exec, auto, nouser, and async.

I don't know why it shows as Seagate. But to make it permanent you can do this:
$ sudo blkid /dev/sdb1
$ sudo gedit /etc/fstab

Add this new line to the file:
UUID=(the one that you get from blkid) /media/Fujitsu120 ntfs-3g defaults 0 0

And then you won't need to remount again and again. :)

---

### Post by Miljet on 2011-11-04
> I now seem to have a writable disk, except it thinks it is called Fujitsu120

The reason your disk thinks it is a Fujitsu120 is because fredric had you create a mount point named Fujitsu120 and that is where your Seagate drive is now mounted. That is easily corrected by running the commands that fredric gave you but substituting Seagate everywhere he used Fujitsu120.

The error messages you got when trying to use sudo apt-get install usually means that you have another package manager open at the same time you are trying to use apt-get. In other words the Software Center or Synaptic Package Manager is open. If you know that they are not open, a reboot will usually fix this.

---

### Post by coffeecat on 2011-11-05
> **Miljet said:**
> The error messages you got when trying to use sudo apt-get install usually means that you have another package manager open at the same time you are trying to use apt-get. In other words the Software Center or Synaptic Package Manager is open. If you know that they are not open, a reboot will usually fix this.

Which makes me wonder whether you did not have ntfs-3g installed when you thought you had. Your whole problem originally was down to not having ntfs-3g installed. Look at my two previous posts - at the output of mount when you ran it and when I ran it with and without ntfs-3g. That is unequivocal evidence that you did not have ntfs-3g installed when you ran mount.

Miljet is quite right in saying that the reason your NTFS system shows as "Seagate" is because "Seagate" is the partition label for your NTFS partition. The system will show the partition label in preference to the mountpoint when this is different. Why fredric told you to use "Fujitsu120" is slightly beyond me - "Fujitsu120" is the partition label and mountpoint for the drive I used for illustration purposes. Perhaps fredric was looking at the wrong post when suggesting Fujitsu120 as a mountpoint. 

The manual method of mounting your NTFS drive that fredrik posted will only work read-write if ntfs-3g is installed, so it must have been installed when you ran it. If you are still unable to automount your NTFS drive without the manual commands, something is still wrong.

Whatever you do...

[quote="rimibchatterjee"]So maybe there is a problem with ntfs-3g. How do I uninstall? type sudo apt-get uninstall ntfs-3g? [/quote]

**Do not uninstall ntfs-3g**.

---

### Post by rimibchatterjee on 2011-11-05
Thanks coffee cat. NTFS-3g now appears to be installed and working fine. I can read and write to my disk. I did get a kernel panic at unmount a while ago but no harm seems to have been done. Just a little housekeeping left: have to change the name of the mount point, but other than that all is well. 
Whew!

---

### Post by coffeecat on 2011-11-05
> **rimibchatterjee said:**
> I did get a kernel panic at unmount a while ago but no harm seems to have been done.

I've seen that as well. It's a known bug in Oneiric, and quite unnerving when it happens. :)

I believe this might be fixed in a forthcoming kernel update, but in the meantime it might be prudent to avoid this by manually unmounting your NTFS partition with:

```
sudo umount /dev/sdb1
```

---

