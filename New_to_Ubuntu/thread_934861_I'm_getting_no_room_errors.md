---
title: "I'm getting no room errors"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Mazehero55 on 2008-10-01
I deleted some stuff out of tmp in a search to free up some room and now things have started happening. For instance whenever I try to download anything it says I'm out of space. 
But I checked the root and it says I have 1011mb free. And in my home I have 8.5gb free

Here's the errors: 
*One from clicking to download a picture a png*
> There is not enough room on the disk to save /tmp/mtGb3DFx.part.

Remove unnecessary files from the disk and try again, or try saving in a different location.

*it says this if I try to take a screenshot*
> Unable to save the screenshot to disk:

Fatal error in PNG image file: Write Error

anybody know whats up? I thought stuff in tmp was free to get rid of. I didn't delete everything, just some things that didn't look important.

thank you

---

### Post by kpkeerthi on 2008-10-01
What is the output of the below command?
```
df -h
```

---

### Post by Mazehero55 on 2008-10-01
thanks for a reply
here it is:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.3G  6.9G 1012M  88% /
varrun                474M  152K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   52K  474M   1% /dev
devshm                474M  188K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              65G   53G  8.0G  88% /home
overflow              1.0M 1012K   12K  99% /tmp
```

---

### Post by kpkeerthi on 2008-10-01
Is your /tmp on a separate partition? Can you post the output of the below commands?
```
mount
```
```
cat /etc/fstab
```

* Use [code] tags to post back command outputs.

---

### Post by Elfy on 2008-10-01
/ is almost full - if you haven't done so clearing your apt cache should make some room

```
sudo apt-get clean
```

---

### Post by Orange_and_Green on 2008-10-01
Hello Mazehero55

I was wondering if the directory /tmp _itself_ is still there. Because if you accidentally deleted that too (or maybe altered the permissions), I would not be surprised that you get write errors when something tries to write into it. Could you please run

```
ls -l /tmp
```

and post the results?

[EDIT] sorry, shame on me for not reading last line of the previous output
Good luck :KS

---

### Post by kpkeerthi on 2008-10-01
Gotcha you only have 1012M left in your / for /tmp to use
> /dev/sda1             8.3G  6.9G **[B]1012M **[/B] 88% /

[Clean up junks]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html") and free up some space

---

### Post by kpkeerthi on 2008-10-01
Also, if you have multiple kernels installed (as can be seen in your GRUB boot menu), keep the one that works best (usually the latest) and [uninstall]("http://ubuntuforums.org/showpost.php?p=5112848&postcount=3") the rest.

---

### Post by Mazehero55 on 2008-10-01
mount:
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)

```

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f20daedb-9ebd-4118-8369-b4c7835b6802 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=ea24c360-7b3e-4048-9f2c-6b23dc8b709a /home           ext3    defaults        0       2
# /dev/hda2
UUID=eeb35397-4008-40dd-9a89-b5cc4469d5f4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

I don't know what's taking up all the room. I don't have alot of programs installed.

---

### Post by kpkeerthi on 2008-10-01
Did you try to free up space per the instructions above?

---

### Post by Mazehero55 on 2008-10-01
yeah it looks like I have alot of Residual config files, copletely removing those won't effect anything right?

---

### Post by kpkeerthi on 2008-10-01
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
[http://ubuntuforums.org/showpost.php?p=5112848&postcount=3](http://ubuntuforums.org/showpost.php?p=5112848&postcount=3)

Just follow the steps and you should be OK. Like it was mentioned, these are junk files. Exercise extra care while removing unused kernels. Just make sure you are NOT removing the kernel you are happy with.

---

### Post by Mazehero55 on 2008-10-01
by the way I now have 1.3gb free on my / partition. and I'm still getting errors. 
I'm now also getting this error when I try to open something needing sudo

```
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.
```

[edit] I tried restarting, since I've done alot and freed up alot of space. Seems to be running pretty good now. Thanks alot everyone. I guess deleting stuff in /tmp was just a coincidence sense it started right after that. 

thank you

---

### Post by kpkeerthi on 2008-10-01
[http://ubuntuforums.org/showthread.php?t=474127](http://ubuntuforums.org/showthread.php?t=474127)

---

