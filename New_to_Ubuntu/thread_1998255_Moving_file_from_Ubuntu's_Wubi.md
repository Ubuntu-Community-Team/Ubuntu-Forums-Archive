---
title: "Moving file from Ubuntu's Wubi"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-06
Currently I installed **Ubuntu via Wubi** ... but now it's in ERROR. So I unable to log-in.
So, I wish to move all file, which stored within Ubuntu and **resize the Vista NTFS Partition to 70GB** and build **a brand new ext4 partition 30Gb** and installed Ubuntu.
Since Windows unable to read Ubuntu's folder, I wish for using LiveCD to moved all files.
But I don't know where can I find them.
Please help me ....

---

### Post by bcbc on 2012-06-06
This tool can read the root.disk from windows: [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

From a live cd you need to identify the partition the root.disk is on and mount it. e.g. if it's on /dev/sda1 then:
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt

```
Then you can copy data from /mnt to /media/win (back to your windows partition).

From your other thread, you may need to fsck the root.disk to fix it. Doing hard shutdowns can damage both the ntfs file system as well as the internal ext4 file system on the root.disk. It's not necessary to do hard shutdowns on linux you can use Alt+SysRq R-E-I-S-U-B instead.

To fsck the root.disk, you need to identify the partition it's on (and don't do this if you've already mounted it):
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk 

```

you can supply -fyv to fsck to force the check even if it appears clean, make it give verbose output, and fix automatically. See 'man fsck' for more info.


If you're unable to identify the location of the root.disk (the partition), you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and publish the results or look yourself.

---

### Post by czgirb on 2012-06-07
> **bcbc said:**
> 
This tool can read the root.disk from windows: [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

Thank you. I will give it a try.
But would you mind to tell me in which folder **Ubuntu's Default folder** is?
Cos I unable to see it, even I use **LiveCD**.
Please guide me ....

> **bcbc said:**
> 
Then you can copy data from /mnt to /media/win (back to your windows partition).

How to copy the data? Would you mind to guide me?

> **bcbc said:**
> 
... It's not necessary to do hard shutdowns on linux you can use Alt+SysRq R-E-I-S-U-B instead.

Alt+SysRq ... OK. But what is R-E-I-S-U-B ???

> **bcbc said:**
> 
... If you're unable to identify the location of the root.disk ...

I know where it was placed.
C => ubuntu => disk ... root.disk ... 15,097,856KB

---

### Post by bcbc on 2012-06-07
See here: [REISUB - safe reboot ]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot")

If you use the ext2read tool you just download it, run it, and open up the C:\ubuntu\disks\root.disk
It will give you an explorer like view of the root.disk and you can copy files off it.

If you mount it from a live CD you need to know what partition C: represents. As I said earlier, if you cannot figure this out then run the bootinfoscript and post the RESULTS.txt and I'll tell you which one it is.

---

### Post by czgirb on 2012-06-07
> **bcbc said:**
> 
See here: [REISUB - safe reboot ]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot")

Thank you ... it increased my experienced

> **bcbc said:**
> 
... ext2read ...

Try it ... and the file was moved.
Thank you ... Thank you very much

> **bcbc said:**
> See here: [REISUB - safe reboot ]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot")
... If you mount it from a live CD you need to know what partition C:  represents. As I said earlier, if you cannot figure this out then run  the bootinfoscript and post the RESULTS.txt and I'll tell you which one  it is.


Yesterday, I used LiveCd, pointed to **root.disk** to access the file. But no matter how much click I made ... it won't show-up as what I see as ext2read did.
Thank you.

---

### Post by bcbc on 2012-06-07
In order to view the contents of root.disk you need to [loop mount]("http://en.wikipedia.org/wiki/Loop_device") it.

So, viewing it and clicking on it won't do the trick. You need to identify the full path to the file and mount it. If you've just clicked on the partition in Nautilus then it defaults to mount as /media/<label> (if the partition has a label) or /media/UUID (if there is no label).
Then you can drop to a terminal Ctrl+Alt+T and mount it and then it's available under the /mnt mountpoint:
```
sudo mount -o loop /media/OS/ubuntu/disks/root.disk /mnt
nautilus /mnt
```

If your partition has no label you need to specify the full UUID (probably easiest to copy and paste (Ctrl+Shift+C/V for terminal usage). Or make use of the [TAB] key for autocompletion:
e.g. assuming your UUID is 2345-asdr3-aded3-ada2
```
sudo mount -o loop /media/234[TAB] /mnt
```

If you wanted to fsck it you should do this prior to mounting in which case you'd need the same path to the root.disk:
```
sudo fsck /media/OS/ubuntu/disks/root.disk
```

---

