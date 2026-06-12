---
title: "loop partitions created by ubuntu 18.04 installation"
date: 2018-07-19
forum: New to Ubuntu
---

### Post by gsync on 2018-07-19
Hello,

I recently updated my test VM to the latest Ubuntu 18.04,
and after the installation I noticed some additional partitions created.

```

test@test-VirtualBox:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  1,6M  1 loop /snap/gnome-calculator/154
loop1    7:1    0 86,6M  1 loop /snap/core/4486
loop2    7:2    0  3,3M  1 loop /snap/gnome-system-monitor/36
loop3    7:3    0  140M  1 loop /snap/gnome-3-26-1604/59
loop4    7:4    0 12,2M  1 loop /snap/gnome-characters/69
loop5    7:5    0   21M  1 loop /snap/gnome-logs/25
sda      8:0    0   10G  0 disk 
&#9500;&#9472;sda1   8:1    0  5,6G  0 part /
&#9500;&#9472;sda2   8:2    0    1K  0 part 
&#9500;&#9472;sda5   8:5    0  953M  0 part /home
&#9500;&#9472;sda6   8:6    0  953M  0 part [SWAP]
&#9492;&#9472;sda7   8:7    0  2,6G  0 part 
sr0     11:0    1 1024M  0 rom  

```

Why those 'loopX' partitions were created, and can I remove them ?

---

### Post by Holger_Gehrke on 2018-07-19
Those are not partitions, those are loopback devices used to mount filesystem image files, in this case 'sqashfs' filesystems which are used by snap-packages. So unless you want to replace the (default) snap-packages for gnome-calculator, gnome-system-monitor. gnome-characters and gnome-logs with .deb-packages or go without these programs entirely you should not remove them.

Holger

---

### Post by gsync on 2018-07-19
Thx a lot :)

---

### Post by gsync on 2018-07-20
Ok, but how I can remove those ?

I just saw that on another  machine I have, again with the same version these devices are even more,  because of the updates performed.

```

loop0                   7:0    0   140M  1 loop /snap/gnome-3-26-1604/59
loop1                   7:1    0  12.2M  1 loop /snap/gnome-characters/69
loop2                   7:2    0    21M  1 loop /snap/gnome-logs/25
loop3                   7:3    0  86.9M  1 loop /snap/core/4917
loop4                   7:4    0   1.6M  1 loop /snap/gnome-calculator/154
loop5                   7:5    0  14.5M  1 loop /snap/gnome-logs/37
loop6                   7:6    0 140.9M  1 loop /snap/gnome-3-26-1604/70
loop7                   7:7    0 139.5M  1 loop /snap/gnome-3-26-1604/64
loop8                   7:8    0   2.3M  1 loop /snap/gnome-calculator/180
loop9                   7:9    0    13M  1 loop /snap/gnome-characters/101
loop10                  7:10   0  86.6M  1 loop /snap/core/4486
loop11                  7:11   0  34.7M  1 loop /snap/gtk-common-themes/319
loop12                  7:12   0   3.3M  1 loop /snap/gnome-system-monitor/36
loop13                  7:13   0   3.7M  1 loop /snap/gnome-system-monitor/45
loop14                  7:14   0   3.7M  1 loop /snap/gnome-system-monitor/51
loop15                  7:15   0    13M  1 loop /snap/gnome-characters/103
loop16                  7:16   0   2.3M  1 loop /snap/gnome-calculator/178

```

---

### Post by Holger_Gehrke on 2018-07-20
In theory the Software Application should be capable of removing the snap packages. But since these are packages that got installed by default and that app is not very reliable I'd advise using the command line tool snap. 'man snap' will give you the manual page for it.
```
snap list
``` will list the installed snaps ```
sudo snap remove put-the-name-of-a-package-you-want-to-remove-here
``` will remove a package (if there's multiple revisions of a package on your system, it should remove all of them). To install the .deb package of a program instead of the snap you'd have to do```
sudo apt install package-name
``` after removing the snap.

Don't worry that removing the 'gnome-3-26' snap would remove gnome - gnome is installed twice on your system, once for classic .deb packages and once for snaps, which are restrained from accessing the rest of the system.

Holger

---

### Post by gsync on 2018-07-20
Hello Holger,

Thanks a lot for help.

One last question - I actually removed all the packages which I don't need,
but the core component is refusing to stop and remove:

```

error: cannot remove "core": snap "core" is not removable

```

Is it possible to remove this one as well ?

---

### Post by oldfred on 2018-07-20
After I removed the snaps, I had to unmount the cores, the numbers at end will vary, so you have to list first. Just one of many.

      ```
    56  ls -l /snap/core
   57  sudo systemctl stop snapd
   58  sudo umount /snap/core/4571
   59  sudo snap remove core 


```

---

### Post by Holger_Gehrke on 2018-07-20
AFAIK the only way to get rid of the core-snap completely is to remove snap altogether. It contains libraries and tools that programs distributed as snaps will assume to be available. You can remove old revisions of the core snap by giving the '--revision' option and the revision number to 'snap remove' like so:
```

sudo snap remove --revision 4486 core

```
The current revision of the core snap can't be removed.

Holger

---

