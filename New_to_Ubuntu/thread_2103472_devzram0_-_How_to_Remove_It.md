---
title: "/dev/zram0 - How to Remove It?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by mapes12 on 2013-01-10
Running Ubu 12.04 LTS. My machine has been behaving oddly just lately. On furth investigation I've discovered that there is a swap file in memory known as /dev/zram0. I've Googled for a removal solution but found nothing that describes the uninstallation in simple English. It appears that Casper may have something to do with why this /dev/zram0 has been created. Also, I've been connecting a FLIP video recorder to the machine periodically to move some video clips ontp my HDD. Some have suggested that this may have been part of the problem as well.

I've attached a scrrenshot.

Can anyone tell me how to get rid of this please?

Mark

---

### Post by Paqman on 2013-01-10
Generally you don't touch anything in /dev, these are the kernel's way of representing hardware (everythin in Linux is a file, even devices).

Have you been able to pin down exactly when this pops up? Zram is a RAM compression system. Is it there right after you boot? Or does it only pop up after you plug your Flip in?

---

### Post by mapes12 on 2013-01-10
> **Paqman said:**
> Have you been able to pin down exactly when this pops up? Zram is a RAM compression system. Is it there right after you boot? Or does it only pop up after you plug your Flip in?I have no peripheral devices attached and the /dev/zram0 remains as previously stated. Even when I reboot it stays there. I'm not sure if it's related but I also have a /proc file being reported at 140.7TB. The HDD is only 250GB. Screenshot attached. This came to light the other day when I tried to backup my system with Remastersys. Clearly, Remastersys fell over when it found that file.

---

### Post by dannyboy79 on 2013-01-10
your first picture clearly shows it under the USB, Firewire, periphial device. Not sure what's going on IF you don't have anything plugged in. Maybe it didn't unmount properly. You say you rebooted?

Proc is always going to be there and I'd leave it alone but I am not sure why it's stating it's TB in size when your HDD is only 250GB

you could try
```
swapoff /dev/zram0
```

---

### Post by grahammechanical on 2013-01-10
Now here is a strange thing. When I look at the properties of the proc folder for the Ubuntu install that I am at present using it says:

56,393 items, totaling 140.7TB. I guess that 'proc' = processess. Perhaps 140.7TB is a theoretical limit to the size of the file system that Linux processes can run in and the processes are not limited except by that theoretical limit.

I found this.

> /proc is very special in that it is also a virtual filesystem. It's sometimes referred to as a process information pseudo-file system. It doesn't contain 'real' files but runtime system information

> The most distinctive thing about files in this directory is the fact that all of them have a file size of 0, with the exception of kcore, mtrr and self. A directory listing looks similar to the following:

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/proc.html]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/proc.html")

And this

> Like all other files below /proc the kcore file is only a virtual file. It contains the RAM the kernel _can_ allocate. Therefore this should not be touched or read. It is nothing to worry about. This file doesn't use actual disk space and only exists virtually.

Note: On 64-bit systems the size of /proc/kcore is even 128TB because that's the absolute limit of what 64-bit systems can allocate.

[http://www.novell.com/support/kb/doc.php?id=7004153]("http://www.novell.com/support/kb/doc.php?id=7004153")

There are ways of counting bytes that would make 128TB = 140.7TB.

Regards.

---

### Post by Paqman on 2013-01-10
Definitely do not go poking around in /proc, there's nothing user-editable in there. Just think of it as a big dark hole full of weird kernel stuff.

---

### Post by mapes12 on 2013-01-10
> **dannyboy79 said:**
> 
```
swapoff /dev/zram0
```Thanks Dannyboy79. I ran that code but the /dev/zram0 is still there per my first post.

Grahammechanical - I've booted from a live CD. The live CD session /proc file appears empty but the HDD /proc file is still there at 140.7TB so I have no idea what's going on there?

---

### Post by MG&amp;TL on 2013-01-10
> **Paqman said:**
> Definitely do not go poking around in /proc, there's nothing user-editable in there. Just think of it as a big dark hole full of weird kernel stuff.

Well...don't go editing anything in there. Some of the files are quite interesting. ;)

---

### Post by tgalati4 on 2013-01-10
Post the output of:

```
free
```

Do you not have a real, hard disk swap partition?  If not, then create one and it will get mounted and possibly not use /dev/zram0.

---

### Post by mapes12 on 2013-01-10
```
free
```
> mark@mark-ubu-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3043884    1333624    1710260          0     113368     573936
-/+ buffers/cache:     646320    2397564
Swap:      5427472          0    5427472

> **tgalati4 said:**
> Do you not have a real, hard disk swap partition?  If not, then create one and it will get mounted and possibly not use /dev/zram0.Yes, It's always had a swap partition:-

> mark@mark-ubu-laptop:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2e85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   172859391    86428672   83  Linux
/dev/sda2       172861438   488396799   157767681    5  Extended
/dev/sda5       480585728   488396799     3905536   82  Linux swap / Solaris
/dev/sda6       172861440   480583679   153861120   83  Linux

Partition table entries are not in disk order




---

### Post by mapes12 on 2013-01-10
Here's fdisk -l in the GUI.

---

### Post by Cheesemill on 2013-01-10
It looks like the zram kernel module is being loaded. What is the output of...
```
lsmod | grep zram
zramconfig /dev/zram0 --stats
```

---

### Post by mapes12 on 2013-01-10
Looks like the second command didn't do anything.

> mark@mark-ubu-laptop:~$ lsmod | grep zram
zram                   18642  1 


> mark@mark-ubu-laptop:~$ zramconfig /dev/zram0 --stats
zramconfig: command not found

---

### Post by Cheesemill on 2013-01-10
You could try installing zramconfig and then using it to turn off the feature.

```
sudo apt-get update
sudo apt-get install zramconfig
sudo swapoff /dev/zram0
sudo umount /dev/zram0
sudo zramconfig /dev/zram0 --reset
```

---

### Post by mapes12 on 2013-01-10
Update went fine then I got:-

> mark@mark-ubu-laptop:~$ sudo apt-get install zramconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package zramconfigWhich repo is it in?

---

### Post by Cheesemill on 2013-01-10
Sorry, that should be zram-config.

---

### Post by mapes12 on 2013-01-10
> mark@mark-ubu-laptop:~$ sudo apt-get install zram-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  zram-config
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 3,078 B of archives.
After this operation, 42.0 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe zram-config all 0.1 [3,078 B]
Fetched 3,078 B in 0s (23.8 kB/s)        
Selecting previously unselected package zram-config.
(Reading database ... 228552 files and directories currently installed.)
Unpacking zram-config (from .../zram-config_0.1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zram-config
E: Sub-process /usr/bin/dpkg returned an error code (1)Then Apport kicked in and fired off an error report.

The above installation error is a known Bug Report in Launchpad and is under investigation. Can't see that there is much more I can do now.

---

### Post by tgalati4 on 2013-01-10
How did /dev/zram0 get installed in the first place?  Is it part of a Virtual Machine installation?

---

### Post by mapes12 on 2013-01-10
> **tgalati4 said:**
> How did /dev/zram0 get installed in the first place?  Is it part of a Virtual Machine installation?I've had Parallels Workstation and Parallels Transporter installed on this machine for ages but never set up a OS within them. As far as I can recall zram has only just started to appear on my system. I'm thinking that perhaps a Kernel upgrade that came through the other week as part of the regular Updates may have had something in it that detected the VM installation capability and initiated the zram configuaration at boot up. I'm guessing here.The plot thickens. If you look at my earlier screenshots you will see zram0 at 1.6GB. It's now morphed itself into zram0 and zram1 both at 779MB each. See attached updated screenshot.

---

### Post by tgalati4 on 2013-01-10
I did a fresh install of 12.10 on my laptop without any VM's and I don't have a zram0.  So I think you are correct, it's associated with Parallels.  Perhaps there is a Parallels removal tool if you are not using it?

---

### Post by mapes12 on 2013-01-11
> **tgalati4 said:**
> I did a fresh install of 12.10 on my laptop without any VM's and I don't have a zram0.  So I think you are correct, it's associated with Parallels.  Perhaps there is a Parallels removal tool if you are not using it?I've come to the same conclusion. I'll have a go at uninstalling Parallels today and see what happens.

After going through this process I've discovered that zram looks like a good thing so I'm not overly concerned about it running anymore. I like to make good state backups of my system using Remasterys but at the moment Remastersys falls over and reports that it's run into a file that's taking it over the 4GB limit. I keep all my data on a separate partition and only have the / files on my first boot partition so I know it's not data overload. That /proc file appears to be the issue which is perhaps a subject for another thread. I'll post again once I've had a go at removing Parallels.

---

### Post by mapes12 on 2013-01-11
Booted up my machine this morning to discover that zram has not loaded. I have made no configuration changes and not run any applications that weren't running the last time I posted screenshots. Most stange :???:

---

### Post by sengerandu on 2013-01-17
Did you do any uninstallation or it automatically disappeared? I am also interested to know what causes the kernel to create such an entry?

---

### Post by vueja on 2013-04-23
The zram0 automatic appear too when install unetbootin and then restart. :KS

---

### Post by Cvetan on 2013-11-10
I had the same problem with zram0. I also got zram1, 2 and 3 when i installed zram-config. 

Had some problems with it also, so i removed the package. Suprisingly all the zrams were gone. :)

---

### Post by Cvetan on 2013-11-12
No it was only until reboot. Zram0 is back :(

---

### Post by heir4c on 2013-11-12
Take a look here:
[http://askubuntu.com/questions/174579/how-do-i-use-zram](http://askubuntu.com/questions/174579/how-do-i-use-zram)

---

