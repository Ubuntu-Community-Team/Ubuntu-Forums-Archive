---
title: "Impossibly Slow ZFS RAIDZ (350KB/s) Brand New Install"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by liam5 on 2014-01-05
Until recently I had been using mdadm with four drives, with each pair in a RAID1 configuration. These drives were 2x2TB, and 2x3TB, however as free space was very short, I purchased another 2x3TB drives with the intention of using mdadm and RAID5.

Upon building the RAID5 array, the initial sync was apparently going to take 11000 minutes to complete at a very slow 4500KB/s speed. I was advised that perhaps ZFS was the best way to go.

So, I installed a minimal version of ubuntu 13.04 and created my ZFS RAIDZ pool using all four 3TB drives (they are all Seagate ST3000DM001 drives), then created a dataset and attempted to copy a file to it... At a whopping 350KB/s!

The machine is a HP Microserver N40L with 8GB of RAM.

I have tested the drives with Windows installed on the same machine and get speeds of ~160MB/s per individual drive (same results in ubuntu using hdparm). I then tried FreeNAS on the machine and set up a ZFS RAIDZ pool using the web interface. I was only connected to a 100mb LAN connection at the time, but the file transfer saturated this connection as expected.

ubuntu-zfs was installed from the ppa:zfs-native/stable repository.

I used the following command to create the pool (serials omitted) ```
sudo zpool create -o ashift=12 datapool raidz scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001
```

I really hope someone can help me out here, as I don't know why performance is so poor. I have seen online other people that have used the same hardware as me without this sort of issue.

---

### Post by TheFu on 2014-01-06
TL;DR.

ZFS rocks if ....
* using the kernel module, NOT the FUSE version.
* enough RAM is provided - I think 2G of RAM for every 1TB of storage is the recommendation. More if dedup is enabled.
* enough CPU is available for the settings. People do use Atom-based CPUs for pure storage devices.

So, if you didn't build the kernel module for ZFS, then assume it is the extremely slow, FUSE version. I think FUSE drivers are 10-100x slower than kernel drivers.

Why did FreeNAS work better?  Kernel ZFS driver, not FUSE.

ubuntu-zfs might not be a FUSE install.  There was a different package **zfs-fuse** that was clear about being FUSE. You'll have to research to determine if the package you installed is or is not FUSE.

I bought a few of those specific seagate drives last year without doing my research first. Be certain you have the latest firmware. Seems there were/are some important issues to be resolved. Sometimes a cheap drive is a cheap drive for very good reasons. I'm still using those 2 drives RAID1, but will not buy anymore.

For a storage server, actually any Ubuntu production machine, I'd stay on 12.04 LTS until about June 2014.  Non-LTS releases are not for me.

---

### Post by liam5 on 2014-01-06
Thank you for the reply.

According to the [ubuntu wiki page](https://wiki.ubuntu.com/ZFS) ubuntu-zfs is a "native kernel module".

Drives are updated to the latest firmware. I know they are cheap, but they are just being used for a simple home setup, nothing critical, and given their individual performance I cannot see why using them in this configuration would be an issue - they worked perfectly in the RAID1 array, and a software RAID5 array in Windows Server. Speed is not my top priority, if I only get 20MB/s, it's not ideal, but I can live with it.

I'm positive the CPU is up to the task as many people use this exact machine in this way, again, if I'm not seeing 200MB/s transfer speeds, I'm really not fussed. Likewise with the RAM, if 8GB isn't enough for maximum performance, I'm not fussed as long as it works without issues.

I do not mind which version of ubuntu I use, if you recommend 12.04, I am happy to use that, but do you think it will have any effect on the transfer speeds?

Given that FreeNAS ran so smoothly, and with decent transfer speeds (I may reinstall it to run a test over the gigabit network as this will be the main type of transfers I will be doing), surely the issue I am experiencing can only be down to software-based configurations rather than hardware limitations.

---

### Post by TheFu on 2014-01-07
Spent the last hour doing research on this issue.  No clear answer found.

How does the RAM utilization appear?
Found this [http://forums.overclockers.com.au/showthread.php?t=1011181&page=12](http://forums.overclockers.com.au/showthread.php?t=1011181&page=12) an 8G box performed poorly, but adding 16G made everything work well. ZFS was starved for RAM it seems.

---

### Post by liam5 on 2014-01-07
RAM usage is only ~7%.

Having a look at the link you sent, the guy still appears to be getting 50MB/s with full RAM, that speed would be fine for me. But I am only getting 350KB/s with empty RAM.

---

### Post by liam5 on 2014-01-08
No one have any idea why I am seeing such poor speeds? Any tips or advice on how to set up ubuntu-zfs from scratch?

---

### Post by liam5 on 2014-01-10
I'm still not having any luck with this.

Any suggestions or advice people can offer would be greatly appreciated.

---

### Post by bapoumba on 2014-01-12
Thread continued here : [http://ubuntuforums.org/showthread.php?t=2199185](http://ubuntuforums.org/showthread.php?t=2199185)
Closing this one.

---

