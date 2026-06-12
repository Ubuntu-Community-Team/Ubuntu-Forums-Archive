---
title: "Whats a failing Hard Drive copy command?"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-17
Hi,

I've got a failing hard drive (not root,home or swap)

Its sdd1

Whats the procedure to copy all files across to new drive?

Any Terminal command?

Or just copy and paste from Nautulis?

many many thanks..

---

### Post by westie457 on 2012-01-17
Hi

There are several ways this can be achieved.

One way is with the use of the dd command in the terminal - man dd for more information.

Another way is to copy and paste partitions using Gparted.

Both of these only work using a Live Desktop. The advantage is the new hard drive can be used immediately after the old one has been disconnected. Grub should not throw any errors about a missing drive.


Hope this helps

---

### Post by Mark Phelps on 2012-01-17
If you use Clonezilla, you can simply "clone" the contents of the old drive to a new drive.

---

### Post by Double.J on 2012-01-17
^^^ +1, Both very good suggestions. While you're downloading them, and burning, I'd recommend copying the most important data off while you have access, a drive can go completely at any time, leaving you unable to access - if you are able to copy, I'd grab the unreplaceables now :)

Once a hard drive displays symptoms, in a desktop at least, it can be quite a while 'til they go - instant fails are more common in laptops where they get dropped.

Best of luck!

---

### Post by hopelessone on 2012-01-30
```
blade@oneiric:~$ ddrescue -r3 /dev/sdd1 /dev/sde1 logfile
ddrescue: Output file exists and is not a regular file.
ddrescue: Use `--force' if you really want to overwrite it, but be
ddrescue: aware that all existing data in output file will be lost.
Try `ddrescue --help' for more information.

```

Is that right? 

bad hdd is sdd1
good formatted hdd is sde1

but is says Output file exists and is not a regular file.

What do i do?

---

### Post by hopelessone on 2012-01-30
```
ddrescue -f -n /dev/sdd1 /dev/sde1 logfile
     

```

I'll do this first..

---

### Post by WasMeHere on 2012-01-30
> **hopelessone said:**
> ```
blade@oneiric:~$ ddrescue -r3 /dev/sdd1 /dev/sde1 logfile
ddrescue: Output file exists and is not a regular file.
ddrescue: Use `--force' if you really want to overwrite it, but be
ddrescue: aware that all existing data in output file will be lost.
Try `ddrescue --help' for more information.

```

Is that right? 

bad hdd is sdd1
good formatted hdd is sde1

but is says Output file exists and is not a regular file.

What do i do?
You are using ddrescue, which is a good idea. What you intend to do is the second line of ***Example 2*** in the excellent manual page ```
info ddrescue
```
```
Example 2: Rescue an ext2 partition in /dev/hda2 to /dev/hdb2
Note: you need to create the hdb2 partition with fdisk first. hdb2
should be of appropiate type and size.

     ddrescue -n /dev/hda2 /dev/hdb2 logfile
     ddrescue -d -r3 /dev/hda2 /dev/hdb2 logfile
     e2fsck -v -f /dev/hdb2
     mount -t ext2 -o ro /dev/hdb2 /mnt
     read files from /mnt

```
I suggest that you modify it and start with the first line with the -n option. And then you run the line with the -d and -r3 options ...

---

### Post by hopelessone on 2012-01-30
Now does this copy the files over even if there is errors?

so to make it clearer movie.avi will copy across with gaps in it?

Also hard drives are mounted...start again?

---

### Post by halitech on 2012-01-30
> **westie457 said:**
> Hi

There are several ways this can be achieved.

One way is with the use of the dd command in the terminal - man dd for more information.

Another way is to copy and paste partitions using Gparted.

Both of these only work using a Live Desktop. The advantage is the new hard drive can be used immediately after the old one has been disconnected. Grub should not throw any errors about a missing drive.


Hope this helps

GRUB might not but what about fstab if its set up to use UUID instead of /dev/sd* ?  Does cloning copy the UUID as well?

---

### Post by WasMeHere on 2012-01-31
> **hopelessone said:**
> Now does this copy the files over even if there is errors?

so to make it clearer movie.avi will copy across with gaps in it?

Also hard drives are mounted...start again?

Yes, ddrescue copies what can be copied, and leaves 'gaps' where there are bad sectors on the source. If everything is readable on the source, the target will be a perfect clone, including the UUID and the boot sector.

And you should do the cloning with the drives ***unmounted*** to avoid other processes writing (and destroying) during the cloning process.

---

### Post by hr0201 on 2012-02-27
hopelessness, did: 
ddrescue -f -n /dev/sdd1 /dev/sde1 logfile
work, or did you still get the Output flie exists error?
 
I ran into the same problem before when source and target partitions weren't the same filesystem. But I *think* that it also occurs if the logfile is on a read only partition. If you're not sure, just try creating a file (or directory); if you get a read only error, try plugging in a USB flash drive and writing the logfile there (of course ensuring it's mounted read/write). Because of the ambiguity of the error message, I was also concerned with the logfile being destroyed, so just in case, after each pass I make a copy of the logfile (e.g. wd_1tb_sdd1_logfile_1, wd_1tb_sdd1_logfile_2, etc.).

---

