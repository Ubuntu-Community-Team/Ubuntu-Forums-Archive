---
title: "want to access data files saved on fedora from ubuntu"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Nixie99 on 2013-04-11
Hi,

I have two HDDs both are 250GB, the first is Ubuntu 12.04 (LTS)(sda), work great.
The second drive is a old dual boot winxp and fedora core12 ( I think)(sdb), I can connect to this HDD alone and boot up in winxp with no error but failed
to boot on fedora, errors about 'too many bad sectors'. I need to retreive data out from this fedora.

With the two HDDs connected and boot to ubuntu, the second disk is mount automatically and I can see directory but can not access any content, icon of my user name has a lock key icon on it.

Can someone help me accessing this directory. I try chmod command but did not work.

thanks for your time.
Nixie

---

### Post by Bashing-om on 2013-04-11
Nixie99; Hi ! Welcome to the forum .

I am a kinda get my hands dirty guy and look at things from the command line.
How about this approach: Booting up ubuntu:
```
sudo fdisk -l ##to identify the partitions
```
Then mount the fedora partition (whatever from "fdisk" output:
```
sudo mkdir /mnt/fedora
sudo mount /dev/sdb3 /mnt/fedora ##sdb3 is but an example "fdisk"rules
ls -la /mnt/fedora
sudo ls -la /mnt/fedora

```
Then maybe change the ownership of selective directories if needed !
```
sudo chown <username>:<username> /mnt/fedora/<some_directory>
```
Copy the files you need - or those you can - and when done:
REMEMBER to (un-)mount that partition, failure to do so will result in file corruption at some level !!!
```
sudo umount /mnt/fedora
```[INDENT=2]
advise on how this goes
       regards

[/INDENT]

---

### Post by black veils on 2013-04-12
or ```
gksudo nautilus
```to open the file manager with root privileges, which should allow you to access the fedora files.

---

### Post by fantab on 2013-04-12
You have to mount the concerned Fedora partition first. Then open it with 'nautilus'... no need to gksudo it, unless you are accessing files in the filesystem, that have root permissions. On default installs this will work, However if you have changed permissions then probably 'gksudo' should help.

---

### Post by oldfred on 2013-04-12
Fedora's default install is usually in LVM, so you may first need the lvm2 driver in Ubuntu. Then it should work.

sudo apt-get install lvm2

---

### Post by Bashing-om on 2013-04-12
@ oldfred --- Thanks for that ---It had slipped my mind that Fedora builds on LVM.
[INDENT=2]
3 heads are better than 1, even if one is a goat head

[/INDENT]

---

### Post by black veils on 2013-04-12
> **oldfred said:**
> Fedora's default install is usually in LVM, so you may first need the lvm2 driver in Ubuntu. Then it should work.

sudo apt-get install lvm2


using thi method [http://ubuntuforums.org/showthread.php?t=2121985&p=12540548&viewfull=1#post12540548](http://ubuntuforums.org/showthread.php?t=2121985&p=12540548&viewfull=1#post12540548)

---

### Post by napapon on 2013-04-12
Somehow  Ubuntu mounted all my disks corretly on booted but the partitions are kind of messy. I putup with it and now copied all my files needed.

SOLVED.

thanks for all your help.

---

### Post by napapon on 2013-04-12
Sorry for the two login names for this post, I fogot that I have tihs name registered already.

will use this name from now on.

---

