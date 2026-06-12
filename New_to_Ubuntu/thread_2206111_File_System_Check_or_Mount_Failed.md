---
title: "File System Check or Mount Failed"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by geomcd1949 on 2014-02-17
"Fix it til it breaks." -What a great motto!

AsRock z87 extreme4 motherboard, Intel i-4770 cpu, vertex 240 gb ssd, 2 other 1TB HDDs. (Computer is put together from parts from other, properly working, computers).

I fiddled with the utility called Disks, but can't recall exactly what I did.

On startup (Ubuntu 13.10) I get a screen that says - The disk drive for /mnt/def4b53-f27d-4b3d-8eb7-dbbe9d0c5fe7 is not ready yet or not present. Continue to wait, or press S to skip mounting or M for manual recovery.

Pressing M, I get : file system check or mount failed. A maintenance shell will now be started. Control -D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored. Then: root@george-desktop:~#

Since I don't know what to do here, I hit Control -D. Then it says mountall start/starting, then nothing happens.

So, restarting the process, I get to where it says to Press S to skip mounting, and I press S. Ubuntu starts.

Everything works, except Localhost. (LAMP server installed, and worked properly before I screwed up the computer this time.)

However, when I click Files, I don't see a category for File System, which I used to see.

Under Devices, there are listed 1 TB Hard drive, 1.0 TB Volume, and Computer. Clicking on any of these gives access to the folders within. (The OS is on the SSD, which I guess is what's labeled Computer).

As ever, advice is greatly appreciated.

~George

---

### Post by deadflowr on 2014-02-17
Do you have any idea what you did in Disks?

Perhaps posting the output for
```
sudo blkid
```
and
```
cat /etc/fstab
```
will help us.
we'll see if their is a mismatch between the UUIDs of the disk and those listed within the fstab file.

Use code tags (# symbol in the reply to thread, not in quick reply)

---

### Post by geomcd1949 on 2014-02-17
Thanks! Sorry, I simply can't recall what I did in Disks. All I remeber i that I DIDN'T Format anything.

```
george@george-desktop:~$ sudo blkid
[sudo] password for george: 
/dev/sda1: UUID="52ba7213-6bc6-4397-877b-3fbb97e21bc5" TYPE="ext4" 
/dev/sda5: UUID="f86e2c88-773b-4130-8768-f19bdd08fb1a" TYPE="swap" 
/dev/sdb: LABEL="1 TB Hard Drive" UUID="b2f4f031-0fba-445a-b65d-09e6a54abe87" TYPE="ext4" 
/dev/sdc: UUID="1b0c85e4-0b24-4da2-9983-5d2a0322b95c" TYPE="ext4" 

```

```
george@george-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=52ba7213-6bc6-4397-877b-3fbb97e21bc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f86e2c88-773b-4130-8768-f19bdd08fb1a none            swap    sw              0       0
/dev/disk/by-uuid/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 /mnt/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```

---

### Post by deadflowr on 2014-02-17
Did you add this
```
dev/disk/by-uuid/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 /mnt/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```


Off the bat I can see that there is no matching UUID from blkid.
However, I don't understand the x-gvfs-show option.
Is this a network shared drive?
Or something?

Edit: Decided to look around about this and found this from the mint forum
[http://forums.linuxmint.com/viewtopic.php?f=50&t=129169](http://forums.linuxmint.com/viewtopic.php?f=50&t=129169)

---

### Post by geomcd1949 on 2014-02-17
Not sure what you mean by "Did you add this" followed by code.

It is probable that at least one of the HDDs has an Ubuntu OS installed on it. Should I disconnect the HDDs, or take them out, or something else?

---

### Post by deadflowr on 2014-02-17
> **geomcd1949 said:**
> Not sure what you mean by "Did you add this" followed by code.

It is probable that at least one of the HDDs has an Ubuntu OS installed on it. Should I disconnect the HDDs, or take them out, or something else?

The bottom line of fstab.
Seems like something a user would have added manually. Maybe not, though.

Don't see how disconnecting a hard drive is going to change anything.
A simpler solution would be to add a comment(#) to the line in fstab.
```
gksu gedit /etc/fstab
```
change
```
dev/disk/by-uuid/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 /mnt/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
to
```
#dev/disk/by-uuid/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 /mnt/def4fb53-f27d-4b3d-8eb7-dbb9ed0c5fe7 auto nosuid,nodev,nofail,x-gvfs-show 0 0
``` 

This will at least stop it from saying the disk isn't ready, or whatever it says.
No point in trying to mount something that doesn't exist.

---

### Post by geomcd1949 on 2014-02-17
Great, thanks! On startup, it goes right to Ubuntu 13.10, without any error messages.

Everything now works but Localhost. I have the folder /var/www, and all the folders within it. But can't open the .php files in a web browser.

When I click the "Files" icon on the Launcher, I don't get a listing for File System, which I always got before. Its folders and files all seem to be in the listing for "Computer," which is listed in Files under the Devices category.

Really appreciate the instructions for getting rid of the initial error messages.

~George

---

### Post by deadflowr on 2014-02-17
I don't know what is what about the messed up localhost, so...

Nautilus changed the naming scheme from File System to Computer at some point.

If something jogs in you memory about what you might have done in Disks, please post it.
It could help set straight whatever happened.

---

### Post by geomcd1949 on 2014-02-17
Deadflowr

Thanks very much!

~George

---

