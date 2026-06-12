---
title: "how to assign swap"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by murderd2death on 2011-09-14
ive been tryng to assign a swap partition for ubuntu. i have made the partition with a ive puppy linux cd. i cannot find any instructions that will explain to me how to assign that partition as my swap from ubuntu. i am sure this has been explained but any time i do a search on this site i get several irrelevant topics because swap is a very hot keyword for linux. please help.

regards.

---

### Post by haqking on 2011-09-14
> **murderd2death said:**
> ive been tryng to assign a swap partition for ubuntu. i have made the partition with a ive puppy linux cd. i cannot find any instructions that will explain to me how to assign that partition as my swap from ubuntu. i am sure this has been explained but any time i do a search on this site i get several irrelevant topics because swap is a very hot keyword for linux. please help.

regards.

create the partition and choose swap as the filesystem.  it should automatically mount is as /swap.

however it depends on your system and memory as to whether you need it.

You may want to look at a swapfile instead [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by iceguy on 2011-09-14
There are a few steps that you need to follow.
1. select the drive to partition it: sudo fdisk /dev/ydx where "y" could be an "h" for IDE hdd or "s" for sata/scsi/sas drives
check the menu that the fdisk gives you, **make sure to backup you data before doing any changes**, and make a simple patition and change the partition ID to number 82
2. command to chose the specific part as as swap fs: sudo mkswap /dev/sda1
3. command to activate it: sudo swapon /dev/sda1
4.command to verify if you have a swap part is: swapon -s
That's it.

---

### Post by Lisiano on 2011-09-14
... or use GParted ("sudo apt-get install gparted" or use synaptic/Ubuntu software center to install it) and format the partition intended as swap. It should get mounted on every boot this way too.

---

### Post by murderd2death on 2011-09-14
> **haqking said:**
> create the partition and choose swap as the filesystem.  it should automatically mount is as /swap.

however it depends on your system and memory as to whether you need it.

You may want to look at a swapfile instead [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
  i accidentally formatted it as ext 4 instead of linux swap. solved it. thank you :)

---

### Post by Elfy on 2011-09-14
add it to fstab, get it's UUID

```
sudo blkid |grep swap
```


make note of the UUID

```
gksudo gedit /etc/fstab
```

something like

```
UUID=*longnumberfromblkid*  none  swap  sw  0     0
```

save and close gedit, you can 

```
sudo swapon -a
```if necessary


[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

---

### Post by haqking on 2011-09-14
> **murderd2death said:**
> i accidentally formatted it as ext 4 instead of linux swap. solved it. thank you :)

no problems you are very welcome,

Peace

---

### Post by papu40000 on 2012-07-15
> **Elfy said:**
> add it to fstab, get it's UUID

```
sudo blkid |grep swap
```


make note of the UUID

```
gksudo gedit /etc/fstab
```

something like

```
UUID=*longnumberfromblkid*  none  swap  sw  0     0
```

save and close gedit, you can 

```
sudo swapon -a
```if necessary


[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

Really thanks for this tips !!

---

