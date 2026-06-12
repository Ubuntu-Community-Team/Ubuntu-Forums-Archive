---
title: "Swap memory not available"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by BlackchaosTheory on 2013-01-15
Hi, I installed ubuntu 12.04 on a flash drive 8Gb with following partitions : 

[LIST]
[*]1 Gb -> NTFS
[*]1 Gb -> Swap memory
[*]rest -> ext4 mounted as /
[/LIST]
The problem is when I boot into the flash drive and open system monitor, it says that swap memory is not available. Does swap memory can't be installed on flash drive?

Thanks in advance!

---

### Post by Bölvaður on 2013-01-15
You should be able to see the swap partition within this file /etc/fstab. The file should contain something like this
```
# swap was on /dev/sda5 during installation
UUID=1237f085-1709-424e-a469-f40a9ddf5e1c none            swap    sw              0       0

```To enable the swap from this file write the following into the terminal
```
swapon -a
```To know the current status of the swap (in use) type this into the terminal
```
swapon -s
```The output of swapon -s should be something like this
```
$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    7550508    518968    -1

```*added*
Ask yourself if you really need a swap partition. The main reasons for using swap is if you do not have a sufficient amount of ram compared to your peak usage, and also if you hibernate the computer (move everything from ram onto swap until you'll turn the computer on again). If you do not really need a swap partition you should consider merging that partition with one of your other partitions.

---

### Post by NM5TF on 2013-01-15
Is it possible to force a swap partition to be enabled at boot??

When I installed 12.04 from a Live CD it assigned swap to sda5, but
only assigned 8MB to it for some reason....I need to go to gparted
to turn on swap on sda6 which gives me an additional 2GB for swap.

I would like to have sda6 assigned as swap at boot so I don't have
to go thru the additional steps as I only have 1GB of RAM at the 
present & if I forget to assign sda6, then my sys freezes because
of heavy usage...

results of cat /etc/fstab & swapon -s below

TIA,

Tommy


tommy2@tommy-Inspiron-531s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=b6d65084-87db-4eff-b51e-17e13bd8f808 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8ab28302-3d42-49ea-9a00-4d6101a3f1a1 none            swap    sw              0       0



tommy2@tommy-Inspiron-531s:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	7996	7960	-1
/dev/sda6                               partition	2196476	436636	-2
tommy2@tommy-Inspiron-531s:~$

---

### Post by Elfy on 2013-01-15
If you run 

```
sudo blkid 
```

you should then be able to see the UUID for the swap 

then edit /etc/fstab as root and make sure the swap referenced there matches.

If you're not sure then give us the results of

```
sudo blkid
cat /etc/fstab
```

---

### Post by NM5TF on 2013-01-15
> **Elfy said:**
> If you run 

```
sudo blkid 
```

you should then be able to see the UUID for the swap 

then edit /etc/fstab as root and make sure the swap referenced there matches.

If you're not sure then give us the results of

```
sudo blkid
cat /etc/fstab
```


can I just edit /etc/fstab to add the UUID for sad6 to make it
available at boot...is it really that simple???

the cat /etc/fstab result is AFTER I manually turned on sda6
with gparted....

```
tommy2@tommy-Inspiron-531s:~$ sudo blkid
[sudo] password for tommy2: 
/dev/sda5: UUID="8ab28302-3d42-49ea-9a00-4d6101a3f1a1" TYPE="swap" 
/dev/sda6: UUID="87a4586c-7df5-4287-bf2e-af70ffafe7b7" TYPE="swap" 
/dev/sda7: LABEL="Ubuntu 12.04 LTS" UUID="b6d65084-87db-4eff-b51e-17e13bd8f808" TYPE="ext4" 
tommy2@tommy-Inspiron-531s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=b6d65084-87db-4eff-b51e-17e13bd8f808 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8ab28302-3d42-49ea-9a00-4d6101a3f1a1 none            swap    sw              0       0


```

Tommy

---

### Post by Elfy on 2013-01-15
> is it really that simple???should be :)

you can even use both if you want to, backup and edit the file 

```
sudo cp /etc/fstab /etc/fstab.bak
```

```
gksudo gedit /etc/fstab
```

Then either change 

```
UUID=8ab28302-3d42-49ea-9a00-4d6101a3f1a1 none swap sw  0       0
```

to 

```
UUID=87a4586c-7df5-4287-bf2e-af70ffafe7b7 none swap sw  0       0
```

or add the same line AFTER the existing one to use both swaps

then save the file

```
sudo swapoff -a && sudo swapon -a 
```

then ```
free -m
``` to check the swap was recognised ok, should then be there on each reboot

---

### Post by NM5TF on 2013-01-15
looks like it worked great...

thanx Elfy...:guitar:

I LOVE this Forum!!!

Tommy

---

