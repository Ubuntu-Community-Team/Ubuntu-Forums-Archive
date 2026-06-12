---
title: "[SOLVED] things that I don't need..."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-19
Ok... after I installed Ubuntu and allowed it to do the critical updates thing.... I installed a couple of programs...but apparently I removed 'em... I mean I used the synaptics package manager to remove the big things.... and yet I still am perplexed at how much space is taken up.... I have a 40GB HDD, and I only have 29.7 Left.... I know Ubuntu uses about 4-5GB.... so where's the rest of the 5? Any ideas on a quick way to fix things... like that.

---

### Post by avtolle on 2008-06-19
How big is your swap partition? ```
df-h
```

Also```
sudo apt-get clean
```

---

### Post by sparkyjoe34 on 2008-06-19
Either will work:
```
sudo apt-get autoclean
```
The previous removes archived packages most likely when you installed the system.
```
sudo apt-get clean
```
This one removes all archived packages whether they are old or not.

---

### Post by f37u5g0d on 2008-06-19
Applications > Accessories > Disk Usage Analyzer.  Take a minute to learn how to read it (it is rather intuitive if you give it a second.  It will tell you exactly what is on your hard-drive.  I absolutely love it.  So much more info than you're basic "23% of drive is full and accompanying pie graph."

---

### Post by 133794m3r on 2008-06-19
well I get this error when I type that cod....
```
macarthur@macarthur-laptop:~$ df-h
bash: df-h: command not found

```

---

### Post by Falcorian on 2008-06-19
You need a space, they forgot to type it.

```
df -h
```

---

### Post by 133794m3r on 2008-06-19
well I get this....
```
macarthur@macarthur-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.9G   30G  12% /
varrun                442M  124K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   44K  442M   1% /dev
devshm                442M  104K  442M   1% /dev/shm
lrm                   442M   38M  405M   9% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       36G  3.9G   30G  12% /home/macarthur/.gvfs 
```
and according the  desklet memory thingy I have 1.6GB devoted to swap... even though.... I'm only using like 41MB-64MB for it... is there anyway to change that? My laptop... has 1GB or ram... so yeah...

---

### Post by Promaster91 on 2008-06-19
This will remove any unnecessary packages.
```

sudo apt-get autoremove

```

---

### Post by 133794m3r on 2008-06-21
ok... thanks... but is there any way to decrease my swap?

---

### Post by avtolle on 2008-06-21
From a Ubuntu 8.04Live CD, after booting into the desktop, hit Alt+F2, put gksudo gparted in the box, and when the partitioner opens, select the swap partition for resizing. You will be able to shrink it that way. Alternatively, you may obtain a bootable Live CD from the Gparted website, and use it to perform this operation. As the partition needs to be unmounted, you cannot (at least I don't think you can) do this while booted into your system, as the Swap partition is mounted when the system boots from the HDD. HTH.

---

### Post by louieb on 2008-06-21
If you hibernate your computer -  swap needs to be larger that your ram. Otherwise you can cut it down to whatever you want.

---

### Post by 133794m3r on 2008-06-21
> **louieb said:**
> If you hibernate your computer -  swap needs to be larger that your ram. Otherwise you can cut it down to whatever you want.

ok but is swap like pagefile? And is there any like... uhm.. recomended amount?

---

### Post by avtolle on 2008-06-21
The recommended amount of swap space is 1.5 x your RAM. If you don't hibernate, and if you have a goodly amount of RAM installed, 1xRAM seems sufficient. By goodly amount (man, am I tired), RAM=>1 Gig, but on another box with only 512 mb, my swap is accessed rarely (it could be I don't do a lot of RAM intensive things). HTH.

---

### Post by 133794m3r on 2008-06-21
> **avtolle said:**
> The recommended amount of swap space is 1.5 x your RAM. If you don't hibernate, and if you have a goodly amount of RAM installed, 1xRAM seems sufficient. By goodly amount (man, am I tired), RAM=>1 Gig, but on another box with only 512 mb, my swap is accessed rarely (it could be I don't do a lot of RAM intensive things). HTH.

so then you're saying that i should like uhm...keep about the same? My swap is never above 45 MB... and it says that I have 1.6 GB devoted to it... I have 1GB of RAM on this machine... and I'm a gamer... and I've tabbed out and looked at it... and it was only 45MB

---

### Post by jonofan on 2008-06-21
> **f37u5g0d said:**
> Applications > Accessories > Disk Usage Analyzer.  Take a minute to learn how to read it (it is rather intuitive if you give it a second.  It will tell you exactly what is on your hard-drive.  I absolutely love it.  So much more info than you're basic "23% of drive is full and accompanying pie graph."

Wow that's a great tool, cheers!

---

