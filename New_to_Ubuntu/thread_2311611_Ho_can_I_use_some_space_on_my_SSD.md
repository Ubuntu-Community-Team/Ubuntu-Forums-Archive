---
title: "Ho can I use some space on my SSD"
date: 2016-01-28
forum: New to Ubuntu
---

### Post by sbtypo3 on 2016-01-28
I have been using ubuntu for about 1.5 years. I installed it on my ssd and my home folder is on my hdd.

The SSD is only using about 11GB, I have another 90 or so doing nothing and it doesn't seem like this is going to change - at least it hasn't in nearly two years.

I have steam installed and a few apps that were not installed with the software centre. These are all in my home folder on the HDD. I want these on my SSD.

How can I reduce the size of the partition by about 60gb and use the space to store my additional apps and steam games?

---

### Post by sandyd on 2016-01-28
Hi,

Have you tried creating a folder that is owned by you on the SSD, and creating symbolic links to it?

For example:

```

sudo mkdir /home-ssd
sudo chown *username:**username* /home-ssd
chmod 770 /home-ssd

```

Now, you can move things to /home-ssd and create symbolic links:
```

mv ~/*examplefolder* /home-ssd/examplefolder
ln -s /home-ssd/examplefolder /home/*username*/*examplefolder*
```

Italics are to be replaced with propper values.

/home/*username*/*examplefolder* is now on /home-ssd/examplefolder

---

### Post by oldfred on 2016-01-28
I do somewhat the same but opposite in linking.
I create a large data partition and keep /home inside / (root) and then link all the folders from my data partition back into /home. I have linked different folders from two data partitions with different formats also.

What are sizes?
df -h
sudo du -h --max-depth=1 /home/$USER | grep '[0-9]G\>'   # folders larger than 1GB

If you keep /home inside root on SSD then all the little configuration files for your user settings load faster, but data you access less often is on rotating HDD. You then also have room on SSD for another data partition with some or all of your games and/or some data.

---

### Post by Tadaen_Sylvermane on 2016-01-28
Just move the ~/.steam folder to the ssd somewhere and symlink it into ~/. Easy peasy...

Depending on how comfortable you are with it I would recommend repartitioning for sure. On my server I have a 120gb ssd and a 1tb hard drive. I have 15 gigs of the ssd assigned to / and the rest to a mountpoint called /ssd. I keep my KVM vms there. HDD is partitioned entirely as /spinner for data with a 2gb swap. Makes it easy to keep the ssd being used where it counts. Also rrun my Minecraft server from the ssd as well.

---

### Post by sbtypo3 on 2016-01-29
Thanks allf or the info.

I would prefer to have a new partition as I have had to reinstall ubuntu before and it was so much easier having my home on a different partition. If I just make a folder on /  I have to remeber to back it up before reinstalling.

Can I resize the partition and create a new one on my live system? Or do I have to use a USB bootable system and modify the drive when my live OS is "off"?

---

### Post by oldfred on 2016-01-29
You cannot work on mounted partitions.
So you need to use live installer that has gparted or download and use a gparted live version which will have a somewhat newer version of gparted.

---

### Post by leclerc65 on 2016-01-29
I divide my SSD into partitions that are around 15 G each. 
I keep old distros for several years (still have Ubuntu 12.04, Mint Maya, Rebecca).
It's annoying to find that an old document ... that refuses to be read by a new version of the program. Now I avoid using such software (Abiword for example).

---

