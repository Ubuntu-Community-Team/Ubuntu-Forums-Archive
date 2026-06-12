---
title: "Need a bit of partitioning advice"
date: 2017-11-20
forum: New to Ubuntu
---

### Post by mivo on 2017-11-20
It's been a while since I used Linux on a production machine, but since the latest Windows 10 "feature update" pushed me over the edge (keeps failing, while completely clogging up my connection) I'm looking to put 17.10 on my desktop. I'm unsure about how to best partition the machine (500 GB SSD, 3 TB HDD). My first thought was to put root (/) on the SSD drive and use the HDD for /data/. On the other hand, with future upgrades in mind, it may be favorable to split the SSD into / and /home. Assuming that Steam installs games into the home directory, what would be a safe size for / without the home directory? I'm unfamiliar with current binary sizes. Which approach would be preferable?

A bit related: How smooth are upgrades to new six-month releases? Back when I was more familiar with Ubuntu, the best advice was usually to just format and install the new release from scratch. But that was years ago. :)

---

### Post by Dennis N on 2017-11-20
I install the OS on the SSD, and have a separate data partition on an HDD. I don't use a separate home partition. I allow 25-30 gB for the OS, which does not include the data partition. I have several OS installed in a multiboot setup. All of them are set to mount and share the data partition. My system is UEFI, which I prefer over bios. 

As to upgrades, I used to do a new install for a new OS version, but recently upgraded Xubuntu 17.04 to 17.10 on two computers without any problem, so I would probably do it again.

I don't use Steam, so can't comment on that.

---

### Post by oldfred on 2017-11-20
I still prefer new install. But I have multiple 25GB partitions I use for / (root) on both SSD & HDD and keep old LTS and then newer LTS as main working install and test/try each 6 month release to review or test changes.

Upgrades usually fail as users have added proprietary drivers or ppa. They need to be removed before the upgrade and then reinstalled. If ppa is not available in newer version upgrade fails as ppa cannot then be read.

I prefer having / for main working install(s) on SSD, and then I have a large data partition on HDD. I link all my data back into / so system looks like all data is in usually locations.

Do not know how large games may be. I just did a new install to a 64GB flash drive sdc, and sda is my 16.04 with lots of updates, but regular housecleaning. But no games.

```
 fred@Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        30G [COLOR=#ff0000]  11G[/COLOR]   18G  38% /
/dev/sda1        50G   54M   50G   1% /boot/efi
/dev/sdb6       202G   53G  139G  28% /mnt/data
/dev/sdc3        36G   27G  7.6G  79% /media/fred/data64
/dev/sdc2        21G  [COLOR=#ff0000]4.9G[/COLOR]   15G  26% /media/fred/xenial64 


```

---

### Post by Dennis N on 2017-11-20
On the upgrades without doing a new install, I found it a relief not to have to spend an hour or so per computer setting up the OS to be like the old one I was replacing. So that is a big advantage I see for that. And since all my data was safe on my data partition, even if the upgrade should fail there is no loss to me. Total upgrade time: 30 - 40 minutes.

---

