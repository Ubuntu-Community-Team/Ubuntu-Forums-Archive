---
title: "&quot;disc-cover&quot;   Device initialization failed"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by trebor7_1 on 2008-11-04
Hi All,

Just reloaded "disc-cover" programe that I've used before on Ubuntu 7.x

I've recently upgraded to 8.10 and now get the following error message at start up :-

Error: Device initialization failed.

Solution: Make sure "/dev/cdrom0" points to a valid Cdrom device.

Well I'v tried changing some setting in the disc-cover script, "my ($config_device) = "/dev/cdrom0"; but always get the same error.

The dvd /cd drive works fine and is in  fstab as :-

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

any suggestions please

---

