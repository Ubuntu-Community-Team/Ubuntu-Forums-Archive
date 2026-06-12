---
title: "which file used on bootup?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-19
When the OS boots, does anyone know which file is used to tell the system where to find the users /home directory?

---

### Post by EXCiD3 on 2008-05-19
<whoops>

---

### Post by sdennie on 2008-05-19
The information should be stored in /etc/passwd.

---

### Post by Tatty on 2008-05-19
I dont know, but if you are trying to change where the home folder for a user is located you can do it in System->Administration->Users and Groups.

Hope that helps :)

---

### Post by tropdoug on 2008-05-19
what I am trying to do, is find out what file actually points the boot sequence to /home/kim. I made a mess of moving my home dir to a separate partition, and the recovery process I followed hasn't worked completely. What happens now is that on boot the system tells me that the /home/kim directory appears not to exist, which is weird cos it does, so obviously a file is pointing to the wrong place still. I thought it would be fstab but that seems okay, any suggestions?

---

### Post by dwhitney67 on 2008-05-19
Make sure that your new partition name is explicitly specified in the /etc/fstab file to be mounted at /home.

My /etc/fstab looks something like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2a721a42-9f7d-4da0-925d-0ba69f09254e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=a6d931b7-a99a-4852-a50e-7d94dbc2689f /boot           ext3    defaults        0       2
# /dev/sda3
UUID=f2906003-a142-45c8-a19e-8a42e9894b8a /home           ext3    defaults        0       2
# /dev/sda4
UUID=f90d4cfc-6645-4ec3-a5e0-147acc258ffd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Note the statement after the comment "# /dev/sda3".  That's the line you need to correct.

P.S.  Personally I wish Ubuntu would get rid of the UUID stuff.  It's so confusing.  It would be better to see something like:
```
...
/dev/sda3     /home     ext3   defaults 0     2
...
```

---

### Post by tropdoug on 2008-05-19
Thanks for the help Dwhitney67 seems I am not the only one to have this same issue, lol, I found another thread on the same thing, also no fix yet. Sooo, cos I cannot wait around too much I decided to do a resintall, which is ok, cos I am getting really good at finding the right packages now. 

Anyway I appreciate the help, and even though I messed up, I still reckon Ubuntu Rock's and so does this forum! (have you noticed when people messup, they always look for someone else outside to blame? roll on 2012!)

---

