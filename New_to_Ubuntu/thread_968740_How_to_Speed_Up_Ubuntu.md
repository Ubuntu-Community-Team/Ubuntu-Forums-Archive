---
title: "How to Speed Up Ubuntu"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-11-02
I love my linux, but it seems to be running a little slow on my computer. I don't know why. I don't have processes going other than Firefox. Not uploading songs, pictures, streaming stuff. It just seems like it could be faster...Any ideas on how I could maybe defrag it? Even though I know Linux doesn't need it.

Armaniboy:KS

---

### Post by nkri on 2008-11-02
The following method has worked for me in the past, and I've noticed the processing speed increase, but there is no guarantee that it will make a difference on your system.

Boot up a LiveCD and choose to try Ubuntu without installing.

Go into a Terminal (Applications>Accessories>Terminal) and type
```
sudo fdisk -l
```
to find which partition has Ubuntu on it.  The Ubuntu one will say "Linux" in the "System" column.  For example, this is the output of mine:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe52de52d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5708    45849478+   7  HPFS/NTFS
/dev/sda2           11481       12160     5462100   83  Linux
/dev/sda3            5709       11238    44419725   83  Linux
/dev/sda4           11239       11480     1943865    5  Extended
/dev/sda5           11239       11480     1943833+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

/dev/sda3 is my primary partition, and /dev/sda2 is my /home partition.  For this example, we would want /dev/sda3.

Now, again in the Terminal, type
```
sudo e2fsck -fD /dev/*your_partition*
```

Let it do its thing...it might take a couple of minutes since it is indexing and essentially defragging your disk.

Once it is done, restart and enjoy:)

Also, if you want it to boot faster, try [_this_]("http://ubuntuforums.org/showthread.php?t=254263") post.

Good luck!
-nkri

---

### Post by Warren Watts on 2008-11-02
I love my linux, but it seems to be running a little slow on my computer. I don't know why. I don't have processes going other than Firefox. Not uploading songs, pictures, streaming stuff. It just seems like it could be faster...Any ideas on how I could maybe defrag it? Even though I know Linux doesn't need it.


You need to provide a few more details.  

Is your computer:
Slow to Boot to the GDM Login?
Slow to open large memory hungry apps like GIMP?
Slow to open webpages when internet browsing?

How fast is the processor?  How much RAM to you have?  How big is your swap file?

---

### Post by Armaniboy on 2008-11-02
My ram is like 512mhz. I have a 60GB harddrive. My processor is a Centrino.

---

### Post by Armaniboy on 2008-11-02
Switching between screens and opening and closing programs is kind of slow.... loading tabs and switching tabs in firefox is kind of a slow thing as well.

---

### Post by OutOfReach on 2008-11-03
Maybe you should turn off compiz.
System>Preferences>Appearance, Visual Effects tab and select None.
See if that helps

---

### Post by Armaniboy on 2008-11-03
It's already off :(

---

### Post by OutOfReach on 2008-11-03
> **Armaniboy said:**
> It's already off :(

Oh. Well that might be a problem. Your memory might be insufficient to run GNOME.
You can try to install Xfce, a lighter GNOME-like desktop enviroment.
You can follow this guide: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Or if you don't want to do that, you can try using more lightweight apps: e.x. Instead of Firefox, Opera. Instead of Nautilus, Thunar. etc

---

### Post by Armaniboy on 2008-11-03
> **nkri said:**
> The following method has worked for me in the past, and I've noticed the processing speed increase, but there is no guarantee that it will make a difference on your system.

Boot up a LiveCD and choose to try Ubuntu without installing.

Go into a Terminal (Applications>Accessories>Terminal) and type
```
sudo fdisk -l
```
to find which partition has Ubuntu on it.  The Ubuntu one will say "Linux" in the "System" column.  For example, this is the output of mine:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe52de52d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5708    45849478+   7  HPFS/NTFS
/dev/sda2           11481       12160     5462100   83  Linux
/dev/sda3            5709       11238    44419725   83  Linux
/dev/sda4           11239       11480     1943865    5  Extended
/dev/sda5           11239       11480     1943833+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

/dev/sda3 is my primary partition, and /dev/sda2 is my /home partition.  For this example, we would want /dev/sda3.

Now, again in the Terminal, type
```
sudo e2fsck -fD /dev/*your_partition*
```

Let it do its thing...it might take a couple of minutes since it is indexing and essentially defragging your disk.

Once it is done, restart and enjoy:)

Also, if you want it to boot faster, try [_this_]("http://ubuntuforums.org/showthread.php?t=254263") post.

Good luck!
-nkri


I did that and I can't load Ubuntu....my comp won't start right :(

Armaniboy:KS

---

### Post by archangel74 on 2008-11-03
that's because you chose yes instead of no when it warned you.  You can check a mounted file system.  I wish I could tell you how I fixed mine.  I can't remember but I know that I had to edit some aspect of the sda that I fsck'ed.  This is how you learn.  I am a rookie to with 1 year experience.

archangel

---

### Post by Armaniboy on 2008-11-03
So no one knows how to fix this problem?

---

