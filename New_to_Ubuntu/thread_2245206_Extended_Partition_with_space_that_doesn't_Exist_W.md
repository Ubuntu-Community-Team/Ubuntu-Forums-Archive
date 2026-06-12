---
title: "Extended Partition with space that doesn't Exist? What the what?"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by kira-yamato-2008 on 2014-09-21
Alright I have my suspicions; however, how did this happen?

The basics are that I have a 250 GB HDD, all of it is accounted for between my Primary partition(Lubuntu 14.04, 147GB), a secondary OS partition (currently Ubuntu 14,04, 100GB), and a 3GB swap partition. 

Now after installing VMWare Player I have an anomalous 103 GB Extended partition with space that shouldn't exist... I only noticed this last night so my question: Did VMWare Player do this, or did something else?

---

### Post by Bill Tetzeli on 2014-09-21
An extended partition, if I'm not mistaken, is simply a container for two or more partitions - in this case the Ubuntu 14.04 (100 GB) and swap (3 GB) partitions, which explains the 103 GB extended partition.  It's not new - it's been there all along.  You can confirm this by installing GParted, if you haven't already, via

sudo apt-get install gparted

in the command line.  Then when you run GParted it'll show your internal drive on startup by default.  You should see listed your primary drive (Lubuntu) and an extended drive, under which in a tree-like structure you'll see the 100 GB Ubuntu 14.04 and 3 GB swap partitions. It should be something like this:

Partition                    File System                    Mount Point                    Size
/dev/sda1                  ext4                                /                                      147.00 GiB
/dev/sda2                  extended                                                               103.00 GiB
    /dev/sda5              ext4                                /                                      100.00 GiB
    /dev/sda6              linux-swap                                                                 3.00 GiB

As I said, the extended partition isn't new.  It simply contains both the Ubuntu 14.04 and swap partition.

---

### Post by kira-yamato-2008 on 2014-09-21
Ah thank you for clearing that up, I was very confused... I hadn't seen it before, even after installing Ubuntu along side Lubuntu...

---

