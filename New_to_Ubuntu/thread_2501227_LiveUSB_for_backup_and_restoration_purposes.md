---
title: "LiveUSB for backup and restoration purposes?"
date: 2024-09-28
forum: New to Ubuntu
---

### Post by lyn-axe on 2024-09-28
I'm a returning user to Ubuntu not having used it for about 10 years. In fact now I'm using Tuxedo, an Ubuntu-based system. I have the following query. Is it possible to create a LiveUSB containing my personal data and configuration files? I would use it for backup purposes and disaster recovery. I know that this can be done fairly easily in MX Linux, probably other distros too.

Failing this, I'm thinking of creating a backup of my personal data and configuration files and use them in addition to a Tuxedo installation .iso file. The disadvantage of this is that I would have to reinstall any programs that I had installed in addition to the base system.

---

### Post by yancek on 2024-09-28
What you are referring to is a remastered rather than live system if you want your own personal configuration files on it.  Do an online search for remastered Ubuntu or something similar.  There have been a variety of programs to do this on Ubuntu over the years but I'm not familiar with current ones so do an online search to include the words 'remaster' and 'ubuntu' and include the release version of ubuntu

Doing regular backups of personal data and of changes to configuration files would be another option.

---

### Post by oldfred on 2024-09-28
If only need a minor change or two, it is a persistent type install. The ISO itself cannot be modified, but you can have a writable space on flash drive to store data. 

But if more than just a bit of additional changes, better to just do a full install. Flash drives are slow writing, so better to use a lightweight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie

While I have multiple flash drives with full installs, I now use external SSD with Kubuntu as then almost as fast as an internal SSD.
Kubuntu is more mid-weight, but worked on my 2006 laptop that would not install Ubuntu as it was too much. 

Persistent  install
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent) & 
[https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi](https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi)

---

### Post by tea for one on 2024-09-28
Here’s an alternative for consideration.
Example PC details below.
```
redact@gmktec:~$  lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT
nvme0n1     232.9G disk                       
&#9500;&#9472;nvme0n1p1     1G part vfat       1% 1015.8M /boot/efi
&#9500;&#9472;nvme0n1p2    40G part ext4      52%   16.8G /
&#9500;&#9472;nvme0n1p3    30G part ext4      41%   15.7G /home
&#9492;&#9472;nvme0n1p4   100G part ext4      89%    6.6G /mnt/381ee381-e1af-4ca4-9a8d-fcccf
redact@gmktec:~$ 
```
_Prerequisites_
A bootable usb disk for a live Ubuntu session
A target disk equal in size or larger than your installed system.

_Operation_
Boot into a “Try Ubuntu” live session.
Attach your target disk with, at least, a partition table (GPT is ideal)
Open Gparted
Copy partition no.1 and paste it into the free space on your target disk
Repeat for each partition, keeping the partition sequence identical
Close Gparted and power off when complete

De-activate, isolate or physically remove your internal (i.e. source) disk
Attach your target disk with the copied partitions (even if it’s external)
Boot and examine – it should be identical.

The distinct advantage is that you can check everything without restoring.

---

### Post by lyn-axe on 2024-09-28
> **yancek said:**
> Doing regular backups of personal data and of changes to configuration files would be another option.

Most of the suggestions given appear to me to be quite sophisticated and possibly take some time to implement, especially for the likes of me who doesn't have much experience with Linux. Admittedly I didn't read the possible answers in depth and I'll do so as soon as is feasible, but for the time being maybe the above suggestion is the most practical one and would satisfy my limited requirements.

---

### Post by TheFu on 2024-09-28
There are many ways to solve this.  Remastering isn't very flexible, since it ties the backups to the hardware. While Linux at boot is pretty good about dynamically handling different hardware, that breaks if you install proprietary drivers for networking, RAID, or GPUs.

For end users that want a point-n-click answer to system recovery, there are easy to use tools for these things available that should work on any default Debian-based install.

Steps for total system backups
[LIST=1]
[*]OS backups
[*]Personal file backups
[/LIST]

Both require an external "data" storage device to hold the backups. A single device can be used, if it has enough storage.  If you don't include large media files or entire virtual machine files, the amount of storage needed really should be minimal while supporting many versioned backups.

For the OS backups, the "pretty" answer is **Timeshift**.  This tool is used by default on Linux Mint and creates periodic "snapshots" though they aren't volume manager snapshots like ZFS or LVM support, they are workable.  Make a new snapshot before you patch your system weekly and you have a way to get back to the prior setup with just a reboot.

For personal file backups, there's a program called **Back-In-Time** that uses the Linux file system Hardlink capabilities to create "snapshots" hourly to the backup storage.  Rather than write a book about it, this link [=detailed&q=Explain+how+Back-In-Time+versioning+works+on+Linux"]uses an AI tool to explain it clearly.]("https://iask.ai/?mode=question&options[detail_level)

The method used by Back-in-Time, hardlinking versions, has been used on Unix for over 3 decades. It is proven.  If you buy any general administration Unix book for $0.50 at a used book store, you'll find a script in the appendix that does backups using hardlinks.  **rsnapshot** is the modern version of that script. It is in the repos, but doesn't have a GUI.  [https://manpages.ubuntu.com/manpages/noble/man1/rsnapshot.1.html](https://manpages.ubuntu.com/manpages/noble/man1/rsnapshot.1.html)  There are lots of how-to guides for using it.  But on a desktop, Back-In-Time, also in the repos, and is just much easier.

As for restoring with either of these backup tools, use your Ubuntu ISO that you used to install the OS. Just boot into "Try Ubuntu" mode, install backintime and timeshift, then when you click the restore, it will as where the target is and Timeshift is likely to find the source and ask which snapshot to restore.  No special flash drive needed.  Just the "Try Ubuntu" ISO.  Back-in-Time backups are easily laid out so a monkey can figure out which version of which file is where, so you can restore everything, a subsection of a directory or a single file as desired.  My 80+ yr old mother was able to figure it out.  Of course, Mom was smart, but she wasn't a computer nerd by any stretch of anyone's imagination.  She loved the hourly snapshots that disappeared over time.
I asked an AI tool for an explanation of timeshift restores [=detailed&q=Explain+how+timeshift+restore+works+on+Linux"] is the result]("https://iask.ai/?mode=question&options[detail_level) that appears to handle complex situations.

Just a few weeks ago at a LUG meeting, a full demo of what I've described above was shown.  I was surprised at how easy the initial setup was. The hardest part was formatting an external disk to EXT4.  Everything else really had a wizard or was obvious what needed to be done next.  Then we did restores of both the timeshift and the back-in-time data.  It worked. No surprises at all.  A few of the LUG members stated they'd been using both tools in the same way described above and never had any issues.  They'd gotten into the habit of making a Timeshift snapshot before they did anything even slightly dangerous with their OS settings.  They couldn't imagine NOT having those snapshots anymore.

Anyway, that's my recommendation for people who aren't server nerds ... er ... like me.

If you are a server nerd, there are better options.

---

### Post by lyn-axe on 2024-09-28
You've made my day!:guitar: I'm so pleased to read your posting. I mentioned that I have some experience with MX Linux and I used both Back In Time and Timeshift with it even though it has its native program doing something like this, called "snapshot". I'm familiar with the programs and I used them as my other course of action should a snapshot burned to a USB stick not work.

Your description of the restore procedure was very useful to me and it will be archived for future reference!

---

