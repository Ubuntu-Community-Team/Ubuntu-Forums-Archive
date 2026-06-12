---
title: "Incorrect disc size"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by clide890 on 2020-02-15
I'm new to Ubuntu so try to go easy on me. I installed Ubuntu server LTS via as a virtual machine via ESXI on a 500gb drive. I also stuck an 8tb in there, the main purpose of ubuntu is to run it as a Plex media server. The hard part was learning how to mount it, partition, and making the HD into a shared drive. After trial and error I was able map the 8tb to windows. My issue is that it is showing the incorrect space. ESXI shows 7.27tb available when adding the drive but windows is showing only 7.21tb out of 7.21tb. 

I also have the same 8tb installed on my windows PC that has all my media and it does show 7.27tb. I've partitioned 3 times and still the same issue. I've used the "Recoverlostdiskspace" wiki and unfortunately I still couldn't figure it out.

---

### Post by oldfred on 2020-02-15
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
More confusion?
[http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release](http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release)
1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
Chart with more conversions -  JKyleOKC
[http://ubuntuforums.org/showthread.php?t=2240118&p=13101706#post13101706](http://ubuntuforums.org/showthread.php?t=2240118&p=13101706#post13101706)
160 GB (gigabytes) = 149.01 GiB (gibibytes) 

Post this:
sudo parted -l unit GB print

---

### Post by clide890 on 2020-02-16
> [COLOR=#000000]Post this:[/COLOR]
[COLOR=#000000]sudo parted -l unit GB print[/COLOR]

Model: VMware Virtual disk (scsi)
Disk /dev/sda: 107GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  107GB   107GB   ext4




Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 7993GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  7993GB  7993GB  ext4         primary

---

