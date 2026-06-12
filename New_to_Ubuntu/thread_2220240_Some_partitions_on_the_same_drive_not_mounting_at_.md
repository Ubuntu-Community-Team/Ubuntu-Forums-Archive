---
title: "Some partitions on the same drive not mounting at boot"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by oapeter on 2014-04-27
Hello everyone,

I'm having trouble with a couple partitions not mounting at boot time. I get a screen at boot that says:

```
the disk drive for /path/to/partition is not ready yet or not present. Continue to wait or press S to skip mounting or M for manual recovery
```

And this happens for two out of three partitions that are on the same drive. I can press S to skip, and the computer boots no problem. Once I'm in Ubuntu, I can click the drives in the file manager and they load without issue. 

It would be a lot nicer if they loaded at boot properly though.

Here's what my fstab file looks like. The two that won't load at boot time are Games and SteamGames. Is there something I should be doing differently in the file?

Thanks for anything!

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=c872b872-adf4-451d-9b77-6319314f35bc /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda8 during installation
UUID=df9bb489-bafd-451a-b05a-c3b30ac06fa8 /boot           ext4    defaults        0       2
# /home was on /dev/sda10 during installation
UUID=df5b5c48-e470-425a-a55d-9e1cf4348184 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=dc64b2ee-0f27-47f6-a946-dd6bd876e04a none            swap    sw              0       0

/dev/sdb1 /home/oapeter/LowStorage ntfs defaults 0 0
/dev/sdc1 /home/oapeter/Games ntfs defaults 0 0
/dev/sdc2 /home/oapeter/SteamGames ntfs defaults 0 0
/dev/sdc3 /home/oapeter/Storage ntfs defaults 0 0

```

---

### Post by oldfred on 2014-04-28
Are sdb or sdc external drives?

They have sped up boot process that external drives often have not fully spun up and are not seen during boot. If you have USB powered drives that almost always is an issue.

Some remove entries from fstab and use a script. 
Or you can run this after boot to remount
sudo mount -a

---

### Post by oapeter on 2014-04-30
Hello,

No, they aren't external drives. They are both Western Digital 3.5" drives mounted inside the case. Oddly, one of the partitions on the drive mounts, but not the other two. I have another distro installed as well, and it has no problem mounting the drives at boot, as far as I can tell. 

Thanks!

---

### Post by oldfred on 2014-04-30
I would also try using UUID, not device.
And I might run Windows chkdsk on the drives even if they seem ok.

---

### Post by oapeter on 2014-04-30
Hello again,

I modified the fstab file to use the drives UUID instead of /dev/sdc1, etc. It seems to have solved the issue so far!

The revised section now looks like this:
```

UUID=5BB502DA795E7563 /home/oapeter/LowStorage ntfs defaults 0 0
UUID=4AEE741CEE74028D /home/oapeter/Games ntfs defaults 0 0
UUID=0004076404075C52 /home/oapeter/SteamGames ntfs defaults 0 0
UUID=A4BE1F35BE1EFF8A /home/oapeter/Storage ntfs defaults 0 0

```

Thanks for the help!

---

### Post by oldfred on 2014-04-30
Glad that worked, but it was just a shot in the dark.
UUID are prefered as devices may not always be consistent.

You may want to consider some added options.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

