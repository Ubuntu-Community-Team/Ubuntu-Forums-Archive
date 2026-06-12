---
title: "unallocated HDD"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by tommytiptree on 2012-10-18
Hi, I have installed ubuntu 12.04 on a pc formally running XP. The PC has two disk drives. The first was for the operating system and the second with two partitions for my music and photos. Ubuntu does not recognise the second hard disk and Gparted shows it as unallocated. The partitions do not show up. How do allocate and mount the partitions on my second disk. I need to be extremely careful as the disk contains all my family photos going back many years.

---

### Post by Grenage on 2012-10-18
That doesn't sound particularly promising; the partitions should show up if they are NTFS/FAT (which Windows XP can see).  Was the archive drive connected when you installed Ubuntu?  Are you positive that you did not accidentally delete the partition table?

---

### Post by jerrrys on 2012-10-18
Does it show up in Nautilus?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+mount+hdd&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+mount+hdd&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by tommytiptree on 2012-10-18
Bad news, it looks as if when installing something has gone wrong. My second disk had 2 partitions of equal size for my photos and music, I now still have 2 partitions but one is sized at 2 Gb and the other at 198 Gb. I have a bad feeling that all my data has been lost.

---

### Post by Grenage on 2012-10-18
> **tommytiptree said:**
> Bad news, it looks as if when installing something has gone wrong. My second disk had 2 partitions of equal size for my photos and music, I now still have 2 partitions but one is sized at 2 Gb and the other at 198 Gb. I have a bad feeling that all my data has been lost.

Oh dear, but panic not too heavily just yet; unless a load of data has been written to the new partitions, it should still be recoverable.

photorec (part of the destdisk suite) is a good reclamation tool.  You can install it using:

```
sudo apt-get install testdisk
```

While there are plenty of guides around, the crux is this:

Open a terminal and browse to the directory you want your recovered data to go (**not the source drive**), then run photorec referencing the source drive:

```
photorec */dev/sdb*
```

Where */dev/sdb* is the archive drive.

There are Windows alternatives, such as 'Get data back for NTFS' - those are also excellent.  Do _not_ put any data on the archive/source drive.

---

### Post by Mark Phelps on 2012-10-19
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

