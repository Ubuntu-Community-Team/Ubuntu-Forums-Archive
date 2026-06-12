---
title: "disk/  dev/ loop what is this?"
date: 2018-06-29
forum: New to Ubuntu
---

### Post by kastorboy on 2018-06-29
hello,
I'm new in ubuntu  ,well after installing Ubuntu overwriting windows (i don't wont it anymore ) i find this command for watching my partition disc < sudo fdisk -l >, what are this 11 loop is there any thing wrong with my installation, can i delete this loops,or discover what are this'. 

```
XXXXX@XXXXX:~$ sudo fdisk -l
[sudo] password for arber: 
Disk /dev/loop0: 14,5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 2,3 MiB, 2428928 bytes, 4744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 3,7 MiB, 3813376 bytes, 7448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 139,5 MiB, 146276352 bytes, 285696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 3,3 MiB, 3411968 bytes, 6664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 86,9 MiB, 91115520 bytes, 177960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 140 MiB, 146841600 bytes, 286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223,6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x41b413b4

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 468860927 468858880 223,6G 83 Linux




Disk /dev/loop8: 12,2 MiB, 12804096 bytes, 25008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 1,6 MiB, 1691648 bytes, 3304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 86,6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 21 MiB, 22003712 bytes, 42976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
XXXX@XXXXX:~$
```

---

### Post by Holger_Gehrke on 2018-06-29
'/dev/loop??' are loopback devices which allow treating files containing a filesystem-image as if they were block-devices. snap packages are set up that way, so the used loop devices are probably snaps.

Holger

---

### Post by sudodus on 2018-06-29
I think you are running Ubuntu 18.04 LTS and **snaps** that are loop mounted. I can verify it, if you run the following commands,

```

sudo lsblk -f
df -h

```

[hr][/hr]
- Snaps are programs that are packaged in another way than the classical way with packages that are installed via 'apt' and integrated with libraries etc.

- Snaps are containerised software packages that are simple to create and install on all major Linux systems without modification.

See more details at [https://snapcraft.io/](https://snapcraft.io/)

---

### Post by kastorboy on 2018-06-29
```
XXXX@XXXX:~$ sudo lsblk -f
NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
loop0  squashf                                            /snap/gnome-logs/37
loop1  squashf                                            /snap/gnome-characters
loop2  squashf                                            /snap/gnome-calculator
loop3  squashf                                            /snap/gnome-system-mon
loop4  squashf                                            /snap/gnome-3-26-1604/
loop5  squashf                                            /snap/gnome-system-mon
loop6  squashf                                            /snap/core/4830
loop7  squashf                                            /snap/gnome-3-26-1604/
loop8  squashf                                            /snap/gnome-characters
loop9  squashf                                            /snap/gnome-calculator
loop10 squashf                                            /snap/core/4486
loop11 squashf                                            /snap/gnome-logs/25
sda                                                       
&#9492;&#9472;sda1 ext4          40c15c3b-eb53-47fc-b198-1c80f4bfd1a5 /
sr0                                                       

```
```
XXXX@XXXX:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2,9G     0  2,9G   0% /dev
tmpfs           591M  1,8M  590M   1% /run
/dev/sda1       220G  7,4G  201G   4% /
tmpfs           2,9G   26M  2,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           2,9G     0  2,9G   0% /sys/fs/cgroup
/dev/loop0       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop1       13M   13M     0 100% /snap/gnome-characters/101
/dev/loop2      2,4M  2,4M     0 100% /snap/gnome-calculator/178
/dev/loop3      3,8M  3,8M     0 100% /snap/gnome-system-monitor/45
/dev/loop4      140M  140M     0 100% /snap/gnome-3-26-1604/64
/dev/loop5      3,4M  3,4M     0 100% /snap/gnome-system-monitor/36
/dev/loop6       87M   87M     0 100% /snap/core/4830
/dev/loop7      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop8       13M   13M     0 100% /snap/gnome-characters/69
/dev/loop9      1,7M  1,7M     0 100% /snap/gnome-calculator/154
/dev/loop10      87M   87M     0 100% /snap/core/4486
/dev/loop11      21M   21M     0 100% /snap/gnome-logs/25
tmpfs           591M   20K  591M   1% /run/user/120
tmpfs           591M   32K  591M   1% /run/user/1000
XXXX@XXXXX:~$ ^C
```

---

### Post by sudodus on 2018-06-29
*Yes, those are snaps, that are loop mounted.*

The output of those commands will be easier to read, if you render it as 'code':

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by kastorboy on 2018-06-29
```
xxxx@xxxx:~$ output

Command 'output' not found, but can be installed with:

sudo apt install yagiuda

xxxxx@xxxx:~$ sudo apt install yagiuda 

```


i installed it but now i don't now what to do exactly . this is what i see now .

```

xxxx@xxxxx:~$ output

Yagi-Uda antenna analysi program output, version 1.19
Written by Dr. David Kirkby Ph.D. G8WRB (email:david.kirkby@onetel.net)

USAGE: output [-cehps] [-E E_max -H H_max -r min -R max -Z Zo] filename 

 -c  Calculate sidelobe levels (slows program considerably).
 -e  Suppress calculation of 3dB E-plane BW.
 -h  Suppress calculation of 3dB H-plane BW.
 -p  Put data into filename.freq, filename.glog and filename.glin for gnuplot
 -s  Suppress diagnostic output.
 -E  Max angle to find the 3dB point. Min=90, max=180  (default = 179 degrees)
 -H  Max angle to find the 3dB point. Min=0, max=90    (default = 60 degrees)
 -r  Set minimum range on the radial gnuplot log graph (default = -50 dB)
 -R  Set maximum range on the radial gnuplot lin graph (default = 20 dB)
 -Z  Set characteristic impedance                      (default = 50 Ohms)

```

it look ther is smth strange .......

---

### Post by oldfred on 2018-06-29
Please use code tags.

Sudodus' use of output was whatever your terminal has outputted should be between codes tags.
(did not even know there was an application called output. And that is not related to loop mounts.)

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

You may or may not want snaps.
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)

I see usefulness for those cases where dependencies do not match your install. Or running an older version of software, running a newer version of software than in default install, or perhaps having multiple versions?

Some that do not use snaps, just uninstall them.

to see list of snaps

snap list

---

