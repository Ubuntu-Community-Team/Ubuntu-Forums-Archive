---
title: "Weird occurances following upgrade"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by crashcoredump on 2008-05-10
So I made the move up to 8.0.4 LTS and so far so Good!

But there are two strange things that have occurred.

One:

My sound still works for Rythmbox but does not seem to work on some webpages and definitely is not as loud. Even at 100% is really low.

Odd eh? I am using the ALSA mixer?? I have to run it at 95% to listen to music....

Second: 
I have a one TB drive that had some issues with automount in the past but had been resolved that now it seems my system thinks is a CDrom.

Here is my fstab:

```

zao@Painhu:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf3d11c1-5818-4f7e-993f-0ce16ff3c246 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2ca58450-54a5-4356-a19c-e42a1e2192dc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
zao@Painhu:~$ 

``` 

/dev/hdb is the one TB volume. 
When I restart I need to run,

sudo mount /dev/sdb /media/Storage and then everything is fine.

Is this a labeling problem?

I would just replace the line like the drive above but I am not sure what the UUID field does.

Any help is appreciated.

---

### Post by crashcoredump on 2008-05-10
Ok so this reference fixed the volume issue.
A couple of channels in alsamixer were down real low.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

So on to the next issue.

The resolution for the sound in Firefox was to install the package libflashsupport in synaptic:)

---

