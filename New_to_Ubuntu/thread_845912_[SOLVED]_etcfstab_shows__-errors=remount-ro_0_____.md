---
title: "[SOLVED] /etc/fstab shows  -errors=remount-ro 0       1"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-07-01
Hi all, I am going through the page listed below, trying to learn how to use the shell, and have come upon this error. 
when I go to the /etc directory and run "less /etc/fstab" I get this output.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1d675fe8-f84f-4383-9d74-8794cdfe6f56 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=88457893-f070-4384-b6e1-b09fa6ec54ab /home           ext2    relatime        0       2
# /dev/sda6
UUID=0f789bee-bcdb-4fcd-8a61-ba6624f660f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~

```

This is the page I am using.
[http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by Elfy on 2008-07-01
My fstab shows the same line for my / drive

Do you have a problem with it ?

---

### Post by iaculallad on 2008-07-01
Actually, its not an error. The errors=remount-ro option will mount the filesystem in read-only mode if in case problems occur during the mount process which prevents data loss.

Filesystem's way of "Self-Preservation".

---

### Post by bab1 on 2008-07-01
:D It's not an error.  it tells the os to mount the root partition read only IF there are errors.

---

### Post by Dutch70 on 2008-07-01
Ok, great, guess that's a good thing then...lol

and no,forestpixie, no problems. just wondering if there were some that I wasn't aware of yet.

Thanks everyone!:D

---

### Post by tipiglen on 2008-07-03
> **iaculallad said:**
> Actually, its not an error. The errors=remount-ro option will mount the filesystem in read-only mode if in case problems occur during the mount process which prevents data loss.

Filesystem's way of "Self-Preservation".

Any idea how to get it to stop?  How to find out why mine remounts as read-only every time I boot?

I added a new user and if I log in as that then everything is OK.  Where might I look in my home directory for the error?

I'm getting very impatient with this.

One re-install did seem to sort it, but somewhere I found a way to screw it up again...

In hope
ed

---

### Post by Dutch70 on 2008-07-03
hi ed, you probobly wont get nay answers on this thread as it has been marked solved, by me...I just happened across this now.

start a thread from the top left corner of the absolute beginners page, and they will help you, if they can.:)

Dutch

---

### Post by EdSantilli on 2011-01-19
Hi Ed,
I have the same error. Please let me know what you come up with if you fix this!
-Ed

---

### Post by EdSantilli on 2011-01-19
Hi Ed,
I have the same problem...the \ partition mounts as read only at every boot. Please let me know what you come up with if you fix this!
-Ed

---

### Post by yetiman64 on 2011-01-19
> **EdSantilli said:**
> Hi Ed,
I have the same problem...the \ partition mounts as read only at every boot. Please let me know what you come up with if you fix this!
-Ed

Try in a terminal,
```
sudo touch /forcefsck
```, 
then reboot the machine.  Edit: your password won't show on input, but if entered correctly should work OK.

The code will force a filesystem check of all your partitions on the next boot - including root. This hopefully will repair whatever the problem is that is causing the read only mounting of root for you. Note the checks can take some time to complete, be patient with them.

---

