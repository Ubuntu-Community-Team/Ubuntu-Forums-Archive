---
title: "filesystem?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by cjxc92 on 2008-11-04
So I was trying to upgrade from 8.04 to 8.10 but the upgrader told me that I don't have enough space on "/".  I'm not familiar with the ubuntu file structures, when I click on "computer" I see the cd drive, "filesystem" and another partition with nothing in it.  How can I get more space on "/" to upgrade to 8.10?

---

### Post by taurus on 2008-11-04
Open a terminal and post the output of this command to see how much space you have left on /--root filesystem.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Paqman on 2008-11-04
Try some of these:
```

sudo apt-get clean
sudo apt-get autoremove

```

If that doesn't work, try uninstalling a big package like Open Office. That will free up something like 300MB. You can always reinstall it after upgrading.

---

### Post by cjxc92 on 2008-11-04
Filesystem         Size    Used  Avail  Use%  Mounted on
/host/ubuntu/disks/root.disk
                   3.6G    2.6G  812M   77%   /
varrun             1.5G    104K  1.5G   1%    /var/run
varlock            1.5G       0  1.5G   0%    /var/lock
udev               1.5G     40K  1.5G   1%    /dev
devshm             1.5G    192K  1.5G   1%    /dev/shm
lrm                1.5G     44M  1.5G   3%    lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon   3.6G    2.6G  812M   77%   /home/*********/.gvfs

---

### Post by taurus on 2008-11-04
> **cjxc92 said:**
> Filesystem         Size    Used  Avail  Use%  Mounted on
/host/ubuntu/disks/root.disk
**[COLOR="Blue"]                   3.6G    2.6G  812M   77%   /[/COLOR]**
varrun             1.5G    104K  1.5G   1%    /var/run
varlock            1.5G       0  1.5G   0%    /var/lock
udev               1.5G     40K  1.5G   1%    /dev
devshm             1.5G    192K  1.5G   1%    /dev/shm
lrm                1.5G     44M  1.5G   3%    lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon   3.6G    2.6G  812M   77%   /home/*********/.gvfs

You don't have a whole lot of space available on /, only 812MB!  You need to do some house cleaning first to free up some space before you can upgrade it.

---

### Post by cjxc92 on 2008-11-04
What can I clean up?  I just recently installed ubuntu, I don't have any documents or files.

---

### Post by Paqman on 2008-11-04
> **cjxc92 said:**
> What can I clean up?  I just recently installed ubuntu, I don't have any documents or files.

You can try my suggestions above. Installing localepurge will also clear out all the stuff for languages you don't use.

Of course, the other option is to expand you root partition in Gparted. That will probably be very slow, and isn't risk free. Make sure to back up before trying.

---

### Post by taurus on 2008-11-04
The thing is, Ubuntu (desktop version) will take up about 2.5GB and you only give yourself 3.6GB.  Therefore, there is not a whole lot of space left for anything else.  You can clear out the apt-get cache with, as Paqman suggested

```

sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by cjxc92 on 2008-11-04
I did both of those, but it only cleared up about 100 megabytes of space.  How would I go about expanding my root partition?

---

### Post by malleus74 on 2008-11-04
Why not try 8.10 as a live cd, and if it works for you, just backup your home directory and install new? It'd probably be simpler for you, too.

---

### Post by cjxc92 on 2008-11-04
Yeah I might do that, considering my internet connection is horrible

---

### Post by malleus74 on 2008-11-04
Trust me, I've seen the horror of a hybrid 8.04 /8.10 when my upgrade went bad. ;) Whatever makes it simpler for you is probably the better way, especially if you're already close to a "standard" install.

---

### Post by cjxc92 on 2008-11-05
Ok well here's my basic problem:  I have 2 partitions on my disk, one is 140GB (for windows) and one is 8GB (for ubuntu, in theory).  I assume that when ubuntu shows two disks in "computer" it is referring to these two partitions (except it calls one "filesystem" and the other "media".  However, the 8GB partition is empty, and although there should be 90GB free on the larger partition (In the folder "host" in "filesystem" it says there is the missing 90GB, but this doesn't appear in the "filesytem partition as a whole), ubuntu says there is only 800MB free.  Why the discrepancy?

---

### Post by cjxc92 on 2008-11-05
anyone?

---

### Post by faraz_k86 on 2008-11-05
The "/" drive is the one one which ubuntu is installed, if you some how messed up the installation you can always re install since you say that this is your fresh instll. 

But this time on the 8 GB partition use "/" as the mount point

---

