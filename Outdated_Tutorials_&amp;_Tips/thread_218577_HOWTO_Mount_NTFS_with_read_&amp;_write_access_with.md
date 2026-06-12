---
title: "HOWTO: Mount NTFS with read &amp; write access with (ntfs-3g-beta) Latest Driver!"
date: 2006-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by asplode on 2006-07-18
Some opening thoughts:
[SIZE="4"]This is still experimental, as it is still in BETA.  That being said, it has been tested a great deal with no failure on a good number of systems, and is more solid than the older libfuse2 and ntfsutils methods.  Please note that I recommend defragging all NTFS drives from Windows before attempting this.[/SIZE]

**Getting The Goods**
First things first, you need the source code.
For FUSE (a prerequisite)
[SIZE="3"][Download FUSE-2.5.3 from sourceforge.net]("http://prdownloads.sourceforge.net/fuse/fuse-2.5.3.tar.gz?download")[/SIZE]
```
tar -xvf fuse-2.5.3.tar.gz
cd fuse-2.5.3.tar.gz
sudo apt-get install build-essential
sudo apt-get build-dep fuse
./configure
make
sudo make install
```
For NTFS-3G
[SIZE="3"][Download the package from linux-rulez.org]("http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz")[/SIZE]
```
tar -xvf ntfs-3g-20070714-BETA.tgz
cd ntfs-3g-20070714-BETA
./configure
make
sudo make install
```

Now all the software necessary is installed, all there is left to do is make it work with your system...

Time to edit that fstab.
```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

Now look for any lines that mount NTFS drives, and adapt them to look like this:
```
/dev/hda1 /mnt/windows ntfs-3g silent,umask=0 0 0
```
You can add your own locale code or various options or permissions as you see fit.  Do this to each NTFS partition you have.  Save your fstab file and continue.

According to [an earlier HOWTO made by LKRaider]("http://www.ubuntuforums.org/showthread.php?t=142481") there is a bug in Dapper [(#29865)]("https://launchpad.net/distros/ubuntu/+source/linux-ntfs/+bug/29865") having something to do with fuse and NTFS.  I can't really see what this command would hurt, so I'm going to throw it in here, but I am not sure if it is still necessary or not. 
```
sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse
```

Now to see if it works.
```
sudo modprobe fuse && sudo umount -a && sudo mount -a
```
Now see if you have write permissions.  If all goes well, you should.  If indeed you do, its now time to make the fuse modules load at boot, so you can set it up and forget about it (at least until this driver comes out of beta...:))
```
echo fuse | sudo tee -a /etc/modules
```

And thats it.

If I messed up somewhere, go easy and help me fix it. :D 

Long live ubuntu!

---

### Post by Noahod on 2006-07-19
Works for me (I can read + write) but whenever I try to copy or move anything I get the error "mv: setting permissions for `FILE': Operation not permitted". I had a similar problem with ntfs-fuse. 

Currently my fstab reads:
/dev/sda5       /media/music  ntfs-3g    silent,gid=1001,umask=0007    0    0

---

### Post by asplode on 2006-07-22
I wrote this tutorial before I saw that one had already been made, and then I couldn't find it, but I just relocated my thread...

The (ostensibly) more popular how-to [is located here.]("http://ubuntuforums.org/showthread.php?t=217009")

---

