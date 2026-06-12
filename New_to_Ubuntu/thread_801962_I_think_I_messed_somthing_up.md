---
title: "I think I messed somthing up"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by twisted_hick on 2008-05-21
Hi all I have had troubles with my dads computer and I used a DSl live cd version 3.4 I think(ubuntu wouldn't load) and I kept getting a hard disk error. So I dmesg | grep hd and get the out put then I get this idea to do it on my machine loaded with hardy. Now I got nothing from the output and like a dummy I did a sudo dmesg |grep hd and still got nothing. I went on to do something else like download a torrent and I noticed something strange like azureus wasn't even a option when choosing a torrent client. So I use locate in terminal and it shows up so I try to find it using the option to pick the client to open the torrent file with and I can't locate it even though terminal locate told me where it is. I check and my file system is showing all crazy numbers when I click on properties. I reinstall azureus and it has all my torrents and everything seems fine (except main file system size reporting) so I am at a loss as to what happened and how to fix it. any ideas ? thanks in advance for your time and suggestion

---

### Post by Xiong Chiamiov on 2008-05-21
What exactly do you mean by "my file system is showing all crazy numbers"?  I don't believe that dmesg should be able to do anything to your system from a brief look at the man page.

---

### Post by twisted_hick on 2008-05-21
my hard drive is a 100 GB and its showing it as 197.1 GB

---

### Post by jimv on 2008-05-21
What OS is installed on your dad's machine?

---

### Post by twisted_hick on 2008-05-21
my dad's was a windows xp box now its a dsl live cd for the moment I'm on a hardy box

---

### Post by jimv on 2008-05-21
What was the problem that was happening in XP?

---

### Post by twisted_hick on 2008-05-21
it was booting to the safe mode select screen. I used a gparted live cd to see If i could repartition it and had a string of errors that are related to the boot sector and now its totally unable to read the hard drive. I will have new hard drive to install in a day or two so that machine will be taken care of. I'm concerned with my machines loss of azureus and the main hard drive showing up at double the size of what it is with the reading of the right amount of free space. any ideas?

---

### Post by jimv on 2008-05-21
I think it could just be a case of the dying hard drive.

---

### Post by unutbu on 2008-05-21
Please post

```
sudo fdisk -l
```

What program is showing the 100GB drive as being 197GB? GParted? 

Sometimes the filesystem can think it has a different size than the partition that it is on. Sometimes it can take up less space, but I've never heard of it taking up more space. Anyway, if that is the problem, the following command is safe, and may (or may not) fix your problem:

```
resize2fs /dev/sdax
```

change the x in sdax to an appropriate value. This works for ext2/ext3 filesystems only.

Explanation from the man page for resize2fs:
> The  size  of  the filesystem  may never be larger than the size of the partition.  If size parame&#8208;
       ter is not specified, it will default to the size of the partition.

---

### Post by twisted_hick on 2008-05-21
heres the out put of the fdisk -l
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006363c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11973    96173091   83  Linux
/dev/sda2           11974       12161     1510110    5  Extended
/dev/sda5           11974       12161     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033072
 nautilus is the one showing the wrong size for the main hard drive  thanks for all your help

---

### Post by unutbu on 2008-05-21
Okay, let's try to see if the problem is isolated to Nautilus, or if it is system-wide.

Please post the output to

```
df -h
```

---

### Post by twisted_hick on 2008-05-22
darrell@darrell-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              91G  6.2G   81G   8% /
varrun               1014M  220K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   56K 1014M   1% /dev
devshm               1014M   60K 1014M   1% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       91G  6.2G   81G   8% /home/darrell/.gvfs
/dev/sdb1             230G  200G   19G  92% /media/data

---

### Post by unutbu on 2008-05-22
Well, the good news is the problem does not show up under GParted, fdisk or df. So your filesystem is not messed up. The problem seems to be isolated to Nautilus alone.

The bad news is I know next to nothing about Nautilus.
Here are some naive suggestions, but think carefully before following them since, as I said, I know next to nothing:

As long as you don't have any special scripts or settings, I think it is safe to delete your nautilus  configuration directory. Nautilus should create a new one after you delete this one:

```

Log out, so you get back to the gdm login screen.
CTRL-ALT-F2  (to take you to a text console)
Log in.
cd
tar cf .nautilus.tar .nautilus/
rm -rf .nautilus
exit
CTRL-ALT-F7

```

The reason for doing this from a virtual terminal is that you don't want Nautilus running while you modify it.

The tar command saves a copy of your entire .nautilus directory and saves it as a file called .nautilus.tar. 

If you ever want your original .nautilus directory back, all you need to do is

```
cd
rm -rf .nautilus
tar xf .nautilus.tar
```

The `rm -rf` command will delete the .nautilus directory. Then open a Nautilus window and see if the problem persists.

If the problem persists, I would then try reinstalling nautilus:
```

apt-get install nautilus --reinstall
```

Hope this helps.

---

### Post by twisted_hick on 2008-05-22
thank you for all your help its been great having your knowledge to help me out. I'll try the nautilus thing tonight after I get some back ups done and the lawn taken care of then I'll post what happens. thank you again

---

### Post by twisted_hick on 2008-05-22
unutbu again many thanks for all your help I tried what you suggested and it didn't work. The nautilus directory deletion and the reinstall of nautilus didn't change a thing. I'll keep my eye out for some one else that reports this problem. I'm hoping my hard disk isn't on its way out although it is about 6 years old with heavy heavy use.

---

