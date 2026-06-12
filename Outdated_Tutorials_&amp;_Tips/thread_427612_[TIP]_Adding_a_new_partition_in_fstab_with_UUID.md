---
title: "[TIP] Adding a new partition in fstab with UUID"
date: 2007-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Ateo on 2007-04-29
I search the Ubuntu forums first for any Ubuntu questions. So, I believe this TIP should be here.

If you want to add a new partition in /etc/fstab under file system you no longer have /dev/xxx but an UUID (Unique unit ID). To find out the UUID of your partition just use the following command:
```
$ sudo vol_id -u device
```

[url=http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html]
Thanks to this Source[/url]

---

### Post by HumbleGod on 2007-05-14
Thanks, this was just what I needed!

---

### Post by gnulab on 2009-05-22
> **Ateo said:**
> I search the Ubuntu forums first for any Ubuntu questions. So, I believe this TIP should be here.

If you want to add a new partition in /etc/fstab under file system you no longer have /dev/xxx but an UUID (Unique unit ID). To find out the UUID of your partition just use the following command:
```
$ sudo vol_id -u device
```[URL="http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html"]
Thanks to this Source[/URL]

I wouldn't replace /dev/xxx with a UUID, since it screws things up.

Take a look at this post.
[http://ubuntuforums.org/showthread.php?p=7326352](http://ubuntuforums.org/showthread.php?p=7326352)

---

### Post by jward3010 on 2009-07-07
My UUID is shockingly short compared to the others in fstab: 847CFB207CFB0BA4 - do I have to do anything with this to make it look standard?
UPDATE!: Don't worry, this strange number still works, even though its way different from the others in "fstab". For those wondering here's a copy of my fstab, the reason I'm posting mine is because I wanted to see an fstab example myself to see what it all looked like after placing a UUID in:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation
UUID=23fcd069-72ab-4f36-823e-2c74374efd4b /               ext4    relatime,errors=remount-ro 0       1

# swap was on /dev/sda2 during installation
UUID=ecffc2c3-e7be-4145-b6f1-28c3a725acfc none            swap    sw              0       0

# DVD drive
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# NTFS partition
UUID=847CFB207CFB0BA4	/media/JOHN-DATA	ntfs-3g		user,fmask=0111,dmask=0000   0   0
```

Finally, want to see if it works without a restart, type:

Step 1.```
sudo umount /dev/sdXX
```
This will unmount the drive you want to now mount using UUID.

Step 2.```
sudo mount -a
```
This will mount everything thats found in fstab, thats not mounted, including your drive that now has a UUID as its identifier instead of /dev/sdXX. If the drive mounts then WELL DONE!

---

