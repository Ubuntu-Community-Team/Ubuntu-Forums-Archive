---
title: "Backup Script"
date: 2008-03-20
forum: Programming Talk
---

### Post by Ultra Magnus on 2008-03-20
Hi I've been trying to write a simple backup script. I want to be able to automatically backup whenever my external hard drive is plugged in, but I don't know where to start, is there a way to execute something when a drive with a certain label is plugged in ?

Thanks
Jim

---

### Post by Fbot1 on 2008-03-20
> **Ultra Magnus said:**
> is there a way to execute something when a drive with a certain label is plugged in ?


A label?

---

### Post by ruy_lopez on 2008-03-20
> **Fbot1 said:**
> A label?

I think he means a volume label.

---

### Post by Fbot1 on 2008-03-20
> **ruy_lopez said:**
> I think he means a volume label.

Oh, lol.

---

### Post by Ultra Magnus on 2008-03-25
Hi, I know you can label a drive and mount a drive by its label, as in

```

mount LABEL=drivelabel /your/directory

```

But I was wondering whether its possible to write a script that mounts the drive automatically when the drive is plugged in and executes something like rsync to backup your stuff, so something like:

-plug in drive
-drive label is detected and mounted
-rsync backs up files

Is it even a good idea to have something running the whole time in order to poll for this or is there a good way to have something that is already running trigger the script to run?

Thanks,

Jim

---

### Post by mssever on 2008-03-26
Look into udev. I believe that you can hook into udev and specify a script to run based on a number of parameters. It just might have what you need.

---

### Post by kpkeerthi on 2008-03-26
> **Ultra Magnus said:**
> Hi I've been trying to write a simple backup script. I want to be able to automatically backup whenever my external hard drive is plugged in, but I don't know where to start, is there a way to execute something when a drive with a certain label is plugged in ?

Thanks
Jim

[http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

---

### Post by wrightee on 2008-03-26
```

#! /usr/bin/env python
import os
m="WD"
stat=os.system("mount | grep "+m)
if stat==0:
	os.system("rsync -avh --exclude=vmware /home/wrightee /media/WD*/bak --delete")
else:
	print "Drive not ready"

```

I do it like that, external drives are called WD (I use a couple), rsync handles everything I need.  Not perfect, was my first ever python script, but works!

---

### Post by Ultra Magnus on 2008-03-26
Awesome, the udev thing was exactly what I was looking for.

Thanks allot

---

