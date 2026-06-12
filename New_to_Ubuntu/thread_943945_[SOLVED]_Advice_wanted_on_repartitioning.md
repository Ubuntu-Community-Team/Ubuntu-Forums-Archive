---
title: "[SOLVED] Advice wanted on repartitioning"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Brian Vaughan on 2008-10-10
When I initially installed Ubuntu 8.04.1, I created two partitions for it, a 2GB swap partition, and 112GB ext3 partition, with / mounted. I've read that the recommended setup for a desktop system is a swap partition, a partition of 3-15GB with / mounted, and the rest with /usr/home mounted. Can I use Gparted to change to that setup? If so, how? Or, should I just leave well enough alone?

I have a LiveCD version of Gparted, which I used to initially reduce the size of my Windows XP partition to half the drive, but then used the Ubuntu installation, manual partitioning, to finish the setup. So far, everything is working well, but I thought it might be a good idea to sort this out before I start copying my music collection from my Windows folders.

---

### Post by shifty_powers on 2008-10-10
firts of all it is not /usr/home just /home.

tbh, it's not a biggie. it has some advantages having a separate /home partition. if you ever need to reinstall, you can just leave it unofrmatted and keep your data and settings.

tbh, just leave it as is for now...

---

### Post by brujoand on 2008-10-10
Afaik there is no major reason for doing the swap, /, /home partition scheme you are mentioning unless you are using different filsystems, other than making reinstalls a walk in the park, since you dont have to back up your /home. 
For instance I use that scheme with swap(swap), /(reiserFS) /home(ext3). I do this because reiser is fast when dealing with small files, and ext3 is better on large files like movies etc..  But there isn't to much to gain here..

---

### Post by shifty_powers on 2008-10-10
> **GrimmVarg said:**
> Afaik there is no major reason for doing the swap, /, /home partition scheme you are mentioning unless you are using different filsystems, other than making reinstalls a walk in the park, since you dont have to back up your /home. 
For instance I use that scheme with swap(swap), /(reiserFS) /home(ext3). I do this because reiser is fast when dealing with small files, and ext3 is better on large files like movies etc..  But there isn't to much to gain here..

i in fact use it, and find it very useful seomtimes. if something goes wrong and i muck up the kernel for some reason, i can reinstall, leave / and /home untouched, and just install /boot.

but it is far from a necessity...

---

### Post by Brian Vaughan on 2008-10-10
Making reinstallation "a walk in the park" seems like a good idea to me. Is there a significant downside to repartitioning? And how would I do it?

---

### Post by jemate18 on 2008-10-10
> **Brian Vaughan said:**
> When I initially installed Ubuntu 8.04.1, I created two partitions for it, a 2GB swap partition, and 112GB ext3 partition, with / mounted. I've read that the recommended setup for a desktop system is a swap partition, a partition of 3-15GB with / mounted, and the rest with /usr/home mounted. Can I use Gparted to change to that setup? If so, how? Or, should I just leave well enough alone?

I have a LiveCD version of Gparted, which I used to initially reduce the size of my Windows XP partition to half the drive, but then used the Ubuntu installation, manual partitioning, to finish the setup. So far, everything is working well, but I thought it might be a good idea to sort this out before I start copying my music collection from my Windows folders.

Here is a sample setup I have... this might be of little help do...
HD Size 80GB
RAM: 1GB

device----------------mountedon-----------------------size
/dev/hda1-------------/boot---------------------------100MB
/dev/hda2-------------swap(this is not mounted)-------2GB
/dev/hda5-------------/-------------------------------10GB
/dev/hda6-------------/opt-----------------------------3GB
/dev/hda7-------------/usr/local-----------------------5GB
/dev/hda8-------------/home----------------------------the remaining size

---

### Post by bodhi.zazen on 2008-10-10
You resize your partitions from a live CD with gparted. You can use the Ubuntu Desktop CD.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

To move home :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

And just to add to the mix, i do not think you need a separate /home partition, but I suggest a separate data partition.

You can call it what you want and mount it in /media

Lets say /media/data

You then make links

ln -s /media/data/music ~/music
ln -s /media/pictures ~/pictures

and on ...

The issue I have with a separtate /home is each distro uses it's own config or . files in /home and they *may* conflict (especially between say Fedora and Ubuntu).

If you share a /home be sure to give each distro a unique user name, but this is more chaotic , IMO, then a data partition.

---

### Post by Brian Vaughan on 2008-10-10
I think I'll go with the separate home partition, as I don't intend to install other distributions, and would prefer to stick to a conventional setup, but it was worth considering. And thanks for the links.

---

