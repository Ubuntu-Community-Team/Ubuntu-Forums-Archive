---
title: "[SOLVED] Auto-mount problem... unrecognized mount option"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-26
Hi everyone
Just been trying to get an internal drive auto-mounted.
It's 1.5TB and formatted as ext3

I was following these instructions:
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)
But specifically post #5 further down the page

Here's what I added to my fstab file:
```
UUID=131f8acc-f4ae-4358-abf2-9f8223454607 /media/raid ext3 nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000 0 0
```

On reboot I noticed some error messages, something to do with SWAP failed, and also another thing.
So I did a dump of dmesg and here's a few lines where I think the problems are:
```
   54.116070] Adding 4915848k swap on /dev/sdb5.  Priority:-1 extents:1 across:4915848k
[   54.423789] EXT3 FS on sdb1, internal journal
[   54.969608] EXT3-fs: Unrecognized mount option "utf8" or missing value
```

So I tried removing utf8 from that fstab then I got the next error
```
EXT3-fs: Unrecognized mount option "shortname=winnt" or missing value
```

So I removed shortname=winnt from fstab and got the following error:
```
EXT3-fs: Unrecognized mount option "uid=1000" or missing value
```

Anyone know which options I need/want and what I need to change this line to?

Also, what characters are meant to be the space between the columns?
I've just done a single space, but in the above rows in my fstab they look like tab widths, but aren't tab characters? Or does it not matter?

Thanks, B

---

### Post by Eisenwinter on 2008-06-26
Hook the drive, and type sudo fdisk -l, see if it's listed there.

Report results.

---

### Post by batfastad on 2008-06-26
Yep, it's absolutely listed there

```
Disk /dev/sda: 1499.9 GB, 1499968045056 bytes
255 heads, 63 sectors/track, 182360 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaca6b75e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182360  1464806668+  83  Linux
```

And I can mount it manually without any bother:
```
sudo mount /dev/sda1 /media/raid
```
Works fine and is shared out with Samba perfectly.

Just can't get it to auto-mount:(

Thanks, B

---

### Post by batfastad on 2008-06-27
Ok I've solved it temporarily by just changing the line to:
```
UUID=131f8acc-f4ae-4358-abf2-9f8223454607 /media/raid ext3 defaults 0 0
```

Replacing all those options with 'defaults'
I hope that doesn't affect anything important, seems to be working ok though.

Thanks, B

---

