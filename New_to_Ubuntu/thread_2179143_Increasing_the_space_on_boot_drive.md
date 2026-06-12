---
title: "Increasing the space on boot drive"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by blueboy1 on 2013-10-06
I would like to increase the space on my boot drive to prevent any recurrance of maxing out and causing other related problems. 
I was stuck with a synaptic package system broken error  for many days because I maxed out on my memory, even though I had extra drives with additional capacity.  I would like to divy up the memory in the system to prevent such recurrance.

---

### Post by Bashing-om on 2013-10-06
blueboy1; Hey !

Let's look at this in another light.
If the partition were to be increased, that only prolongs the time until that larger partition is also filled up. The package manager will not remove old kernels when a new kernel is installed; Because the package manager is not going to second guess you as to what/when an older kernel might be wanted. It is part of housecleaning to remove old unwanted kernels.

Lets look at what the situation is presently and see if indeed drastic surgery is in order.
```

df -h
df -i
dpkg -l | grep linux-image
dpkg -l | grep linux-headers
ls -la /boot

```
Perhaps do some trimming and all will be good (??)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
This is what we have:

```
alrick@Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        97G  9.7G   83G  11% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  1.3M  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G  412K  3.7G   1% /run/shm
/dev/sda1       324M   82M  225M  27% /boot
/dev/sda4       1.2T  122G  967G  12% /home
/dev/sda5       128G  733M  121G   1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde

```

```
alrick@Home:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda2       6447104 360530  6086574    6% /
udev             952601    663   951938    1% /dev
tmpfs            954803    583   954220    1% /run
none             954803      3   954800    1% /run/lock
none             954803      8   954795    1% /run/shm
/dev/sda1         85680    276    85404    1% /boot
/dev/sda4      76324864 244307 76080557    1% /home
/dev/sda5       8511488   8468  8503020    1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde

```


```
alrick@Home:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-49-generic                                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-50-generic                                3.2.0-50.76                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP

```

```
alrick@Home:~$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-49                                      3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                              3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-50                                      3.2.0-50.76                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-50-generic                              3.2.0-50.76                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                                      3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic                              3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                                      3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                              3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54                                      3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic                              3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.2.0.54.64                             Generic Linux kernel headers

```

```
alrick@Home:~$ ls -la /boot
total 67928
drwxr-xr-x  5 root root     5120 Oct  5 20:14 .
drwxr-xr-x 26 root root     4096 Aug  5 22:53 ..
-rw-r--r--  1 root root   795365 Jun 18 14:20 abi-3.2.0-49-generic
-rw-r--r--  1 root root   795365 Jul  9 15:44 abi-3.2.0-50-generic
-rw-r--r--  1 root root   795365 Jul 26 13:08 abi-3.2.0-52-generic
-rw-r--r--  1 root root   140622 Jun 18 14:20 config-3.2.0-49-generic
-rw-r--r--  1 root root   140629 Jul  9 15:44 config-3.2.0-50-generic
-rw-r--r--  1 root root   140629 Jul 26 13:08 config-3.2.0-52-generic
drwxr-xr-x  3 root root     1024 Oct  4 18:06 extlinux
drwxr-xr-x  3 root root     8192 Oct  4 18:06 grub
-rw-r--r--  1 root root 14246449 Jun 27 00:08 initrd.img-3.2.0-49-generic
-rw-r--r--  1 root root 14245881 Jul 24 13:13 initrd.img-3.2.0-50-generic
-rw-r--r--  1 root root 14246978 Oct  5 20:14 initrd.img-3.2.0-52-generic
drwx------  2 root root    12288 Apr 30  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2893287 Jun 18 14:20 System.map-3.2.0-49-generic
-rw-------  1 root root  2893555 Jul  9 15:44 System.map-3.2.0-50-generic
-rw-------  1 root root  2893555 Jul 26 13:08 System.map-3.2.0-52-generic
-rw-------  1 root root  4978416 Jun 18 14:20 vmlinuz-3.2.0-49-generic
-rw-------  1 root root  4978672 Jul  9 15:44 vmlinuz-3.2.0-50-generic
-rw-------  1 root root  4978224 Jul 26 13:08 vmlinuz-3.2.0-52-generic
alrick@Home:~$ alrick@Home:~$ df -h
alrick@Home:~$: command not found
alrick@Home:~$ Filesystem      Size  Used Avail Use% Mounted on
Filesystem: command not found
alrick@Home:~$ /dev/sda2        97G  9.7G   83G  11% /
bash: /dev/sda2: Permission denied
alrick@Home:~$ udev            3.7G  4.0K  3.7G   1% /dev
No command 'udev' found, did you mean:
 Command 'udv' from package 'ncbi-tools-x11' (universe)
 Command 'udav' from package 'udav' (universe)
 Command 'udevd' from package 'udev' (main)
udev: command not found
alrick@Home:~$ tmpfs           1.5G  1.3M  1.5G   1% /run
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
alrick@Home:~$ none            5.0M     0  5.0M   0% /run/lock
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
alrick@Home:~$ none            3.7G  412K  3.7G   1% /run/shm
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
alrick@Home:~$ /dev/sda1       324M   82M  225M  27% /boot
bash: /dev/sda1: Permission denied
alrick@Home:~$ /dev/sda4       1.2T  122G  967G  12% /home
bash: /dev/sda4: Permission denied
alrick@Home:~$ /dev/sda5       128G  733M  121G   1% /media/a40d396c-78c0-41d2-9cef-c0974ff5abde
bash: /dev/sda5: Permission denied

```

---

### Post by Bashing-om on 2013-10-06
blueboy1; Hey ..
I agree that:
> 
/dev/sda1       324M   82M  225M  27% /boot

is a might tight. However, we need to address why the kernel images for these headers are not installed.
> 
ii  linux-headers-3.2.0-53                                      3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                              3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54                                      3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic                              3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic 


What kernel are you booting presently ?
```

uname -r

```
and see what we can do about getting you booting the latest kernel.

In preparation to enlarge the sda1 /boot partition. Let's see an overall picture, prior to looking at the disks with ubuntu's partition editor "GParted".
```

sudo fdisk -lu
sudo parted -l

```
Just because I want to be sure of what we are working with.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
Bashing-om; I really love it your are the eternal optimist, or you really know this stuff. We definitely will get it done. 

```
alrick@Home:~$ uname -r
3.2.0-52-generic

```

```
alrick@Home:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  2930277167  1465138583+  ee  GPT

```

```
alrick@Home:~$ sudo parted -l
Model: ATA WDC WD1502FAEX-0 (scsi)
Disk /dev/sda: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  350MB   350MB   ext4
 2      350MB   106GB   106GB   ext4
 3      106GB   110GB   4505MB  linux-swap(v1)
 4      110GB   1361GB  1251GB  ext4
 5      1361GB  1500GB  139GB   ext4


Error: /dev/zram0: unrecognised disk label                                

Error: /dev/zram1: unrecognised disk label                                

Error: /dev/zram2: unrecognised disk label                                

Error: /dev/zram3: unrecognised disk label                                


```

---

### Post by Bashing-om on 2013-10-06
blueboy1; Life is good.

Firstly; resize-ing sda1 // We are looking at a disk that is partitioned using GPT partitioning. I have no experience with this more modern partitioning scheme, and will have to do some home work to see what tools we have to employ. Will do tomorrow.
We will be shrinking the "/" partition to make room to expand /boot.
There is always always the risk of data loss when performing this operation, though the risk is slightly less when that movement is to the right ( as in our case ) - moving the meta data for those partitions -that exist at the start of the partition, is not overwritten in the process . It is easy to get corruption for no real reason. It is strongly advised to back up your data, and you have a lot of data to back up. Moving partitions is risky business. 
You also use a virtual ram drive, which I have no experience with, but I can not see how the ram usage could affect moving partitions about.

Immediate; kernels:
Let's try this:
```

sudo apt-get purge linux-headers-3.2.0-{53,54}-generic
sudo apt-get purge linux-headers-3.2.0-{53,54}
sudo apt-get dist-upgrade

```
Which I hope will bring in and install the latest kernel.

Straight up, I speak what I know.
However, I am often taken aback by what I do not know, and it happens I get taken aback by what I thought I knew, but was in error.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-06
This is it;

```
alrick@Home:~$ sudo apt-get purge linux-headers-3.2.0-{53,54}-generic
[sudo] password for alrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.2.0-53-generic* linux-headers-3.2.0-54-generic*
  linux-headers-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 22.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 329451 files and directories currently installed.)
Removing linux-headers-3.2.0-53-generic ...
dpkg: warning: while removing linux-headers-3.2.0-53-generic, directory '/lib/modules/3.2.0-53-generic' not empty so not removed.
Removing linux-headers-generic ...
Removing linux-headers-3.2.0-54-generic ...
dpkg: warning: while removing linux-headers-3.2.0-54-generic, directory '/lib/modules/3.2.0-54-generic' not empty so not removed.
```

```
alrick@Home:~$ sudo apt-get purge linux-headers-3.2.0-{53,54}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  winetricks
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.2.0-53* linux-headers-3.2.0-54*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 113 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 313148 files and directories currently installed.)
Removing linux-headers-3.2.0-53 ...
Removing linux-headers-3.2.0-54 ...

```

```
alrick@Home:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Shucks,
Disappointed with that it did not install latest kernels, so ->

```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```

Any means that leads to a good end.

[INDENT][INDENT]more than 1 way
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
```
alrick@Home:~$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic
  linux-image-3.2.0-54-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic
  linux-headers-generic linux-image-3.2.0-54-generic linux-image-generic
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.6 MB/51.3 MB of archives.
After this operation, 218 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main linux-image-3.2.0-54-generic amd64 3.2.0-54.82 [38.6 MB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main linux-image-generic amd64 3.2.0.54.64 [2,264 B]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main linux-generic amd64 3.2.0.54.64 [1,720 B]
Fetched 38.6 MB in 11s (3,474 kB/s)                                           
Selecting previously unselected package linux-image-3.2.0-54-generic.
(Reading database ... 285383 files and directories currently installed.)
Unpacking linux-image-3.2.0-54-generic (from .../linux-image-3.2.0-54-generic_3.2.0-54.82_amd64.deb) ...
Done.
Selecting previously unselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_3.2.0.54.64_amd64.deb) ...
Selecting previously unselected package linux-headers-3.2.0-54.
Unpacking linux-headers-3.2.0-54 (from .../linux-headers-3.2.0-54_3.2.0-54.82_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-54-generic.
Unpacking linux-headers-3.2.0-54-generic (from .../linux-headers-3.2.0-54-generic_3.2.0-54.82_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.54.64_amd64.deb) ...
Selecting previously unselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_3.2.0.54.64_amd64.deb) ...
Setting up linux-image-3.2.0-54-generic (3.2.0-54.82) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-54-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-54-generic...
P: Writing config for /boot/vmlinuz-3.2.0-52-generic...
P: Writing config for /boot/vmlinuz-3.2.0-50-generic...
P: Writing config for /boot/vmlinuz-3.2.0-49-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-50-generic
Found initrd image: /boot/initrd.img-3.2.0-50-generic
Found linux image: /boot/vmlinuz-3.2.0-49-generic
Found initrd image: /boot/initrd.img-3.2.0-49-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.2.0.54.64) ...
Setting up linux-headers-3.2.0-54 (3.2.0-54.82) ...
Setting up linux-headers-3.2.0-54-generic (3.2.0-54.82) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-54-generic /boot/vmlinuz-3.2.0-54-generic
Setting up linux-headers-generic (3.2.0.54.64) ...
Setting up linux-generic (3.2.0.54.64) ...

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Looking good.

reboot and let's see what is:
```

uname -r
df -h

```

[INDENT]gets any brighter, will have to put on shades
[/INDENT]

---

### Post by blueboy1 on 2013-10-07
Any darker for me, will have to go to bed.

```
alrick@Home:~$ uname -r
3.2.0-54-generic

```

```
alrick@Home:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        97G  9.8G   83G  11% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  1.2M  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G  232K  3.7G   1% /run/shm
/dev/sda1       324M  104M  203M  34% /boot
/dev/sda4       1.2T  122G  967G  12% /home
none            3.7G  2.2M  3.7G   1% /tmp/guest-aeCWSN

```

---

### Post by Bashing-om on 2013-10-07
blueboy1; Well.
Got your sunglasses on ?

You now have 4 kernels that occupies only 34 percent of the /boot partition. Now ask yourself - as you now know how to remove no longer needed kernels - is the risk to enlarging the /boot partition worth the gain ?

[INDENT][INDENT]if it ain't broke, don't fix it
[/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
Does that mean I have more issues? Or is my partition now have a more balanced distribution of disc space? I guss I am still in the dark.

---

### Post by Bashing-om on 2013-10-07
blueboy1; What I am saying is;
The issue with a full /boot partition is resolved. Your system is fully functional in all respects less the Wine issue in another thread, that does not effect us here. Only 2 kernels are needed to be kept, the one you are booting with and a backup in the event of need.
You may now remove the 2 earlier kernels if so desired but with 56 % - still leaving operating overhead - remaining unused in /boot there is no hurry. House cleaning to remove old kernels must be done no matter the size of the /boot partition and you now know to watch your /boot partition and you know how to take affirmative action.
If it were me, I would not mess with (re-)sizing partitions but rather pay attention to the size of /boot on occasion; and do the house cleaning.

I detest loosing my data ! Furthermore I see no need now to risk loosing your data. 

That is my thoughts, what is yours

[INDENT][/INDENT]it ain't broke !
[INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
I concur, well said, my only reservation is that I would need specific instructions as to how to check my drive and deleted kernels. I love simple step-by-step  instructions.

---

### Post by Bashing-om on 2013-10-07
blueboy1; Sure,

Just like we have been doing.
Run the terminal command:
```

df -h

```
And if that capacity should reach 85%, it is time to take action and remove the old kernels that will not be used.
One may use the GUI application synaptic to remove these images and headers, I do prefer the command line method, more verbose in the event of any errors.
Command line method:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-
uname -r
sudo apt-get --purge remove linux-image-<versions>
sudo apt-get --purge remove linux-headers-<versions>

```
Remember that the command "uname" yields the kernel you are presently booting .. do not remove it !

That is all there is to general housecleaning.

[INDENT][INDENT][INDENT]piece of cake, and ubuntu is happy too 
[/INDENT][/INDENT][/INDENT]

---

### Post by blueboy1 on 2013-10-07
Fabulous, with all this info I definately will be maintaining. I take it I am safe if I keep the last two more recent kernel. Will do.

---

### Post by Bashing-om on 2013-10-07
blueboy1; Yep.

You are safe at this point and in time.
If you are satisfied with this as a solution. Please also mark this thread as solved.

[INDENT][INDENT]movin' on to other things ?
[/INDENT][/INDENT]

---

