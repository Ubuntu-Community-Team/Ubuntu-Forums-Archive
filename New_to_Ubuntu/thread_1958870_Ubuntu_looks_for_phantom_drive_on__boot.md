---
title: "Ubuntu looks for phantom drive on  boot"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Charlie Chick on 2012-04-15
Hello everybody,

Recently, I plugged a USB drive in to format it. Having done so, I then removed it in the proper way, using 'safely remove'. Now, when I boot the computer, the boot process stops at a screen that says "40Gb drive missing. Continue to wait of press S to skip mounting, or M for manual recovery". The only way to get the computer to boot is to press S.

I re-connected the offending drive, re-formatted it and used the 'power down for safe removal' in Disk Utility, but this hasn't worked; I now get this error message on boot and it won't go away.

Please can anybody tell me how to get rid of it?

Many thanks.

---

### Post by jjpcexpert on 2012-04-18
Em. This is weird. Try posting the spew caused by ```
sudo cat /etc/fstab
``` and we'll figure it out.
It might be that it was detected on boot so is now in the FStab.

---

### Post by Charlie Chick on 2012-04-20
Thanks for your response. Here is the result of the fstab you requested: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda1 :
UUID=b4c9383f-4fb0-4ab5-b0b6-3534216b9934	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc1 :
UUID=4ABB5BE91B80369A	/media/40GB\040drive	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=34d4d216-c204-467b-ab31-2edf93a42b22	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


Would removing the line concerning the 40Gb drive get rid of the problem?

Many thanks for your help.

---

### Post by audiomick on 2012-04-20
> **Charlie Chick said:**
> 

Would removing the line concerning the 40Gb drive get rid of the problem?


Should do, I think, but I would suggest commenting it out rather than just removing it. Once you are sure that this is a good thing, you can always erase it later.

The folder /etc that fstab is in, and the file itself, belong to root. You will have to open the editor with root privileges.

```
gksudo gedit /etc/fstab
```

should do it.

First thing is to do a "save as" of the file under a different name in case things go really wrong and you want to put the original back.


Then, I would make the changes in red below
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sda1 :
UUID=b4c9383f-4fb0-4ab5-b0b6-3534216b9934 / ext4 errors=remount-ro 0 1
#Entry for /dev/sdc1 :
[COLOR="Red"]# next line commented out to fix boot problem
#[/COLOR]UUID=4ABB5BE91B80369A /media/40GB\040drive ntfs-3g defaults,nosuid,nodev,locale=en_GB.UTF-8 0 0
#Entry for /dev/sda5 :
UUID=34d4d216-c204-467b-ab31-2edf93a42b22 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0



You will notice that there is also a comment there to say what has been done.

---

### Post by Charlie Chick on 2012-04-20
Thank you Michael! That's done the trick!

---

### Post by audiomick on 2012-04-20
Great. Glad I could help. :p

Can you mark the thread as solved? The button for that is in the thread tools at the top of the thread.

---

