---
title: "Hardy using CIFS even though SMBFS is specified"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by getut on 2008-05-01
I am having a problem with a fresh install of Hardy 32bit Desktop.

I copied in all of my scripts and none of them are working now. It appears that even though my network share scripts explicitly call out smbfs as the filesystem that cifs is being forced now.

I cannot use cifs. I have some NAS devices that cr@p themselves if I connect with cifs vs. smbfs. And cifs also takes FOREVER at shutdown if you have 10-15 locations mounted like I normally. CIFS times out on each one individually (in order) at about 20-30 seconds EACH on a shutdown.

How can I get my smbfs back in Hardy? Is this a bug that smbfs changes to cifs, or if not a bug what reasoning did they have in taking the choice away to run either cifs or smbfs?

Here is a sample... working command in Gutsy, but not working in Hardy because it is expecting cifs syntax even though smbfs is specified.

sudo mount //172.25.8.22/d$ "/media/server-1-d" -t smbfs -o username=bogususer,password=boguspassword,lfs,dmask=777,fmask=777
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.

Notice the warnings above are CIFS warnings... not SMBFS warnings and the syntax insisted on is for CIFS.

---

### Post by getut on 2008-05-04
Bump

Doesn't anyone know how to force Hardy into using the filesystem specified instead of over riding and always using CIFS?

---

### Post by getut on 2008-05-09
One week and still haven't found a fix. Found other posts talking about it, but all of them so far have given up and gone all CIFS.

I need it to do what I choose.... not override my settings ie use CIFS if I choose CIFS and SMBFS if I choose that instead of using CIFS even if I choose SMBFS.

I have NAS equipment that literally corrupts firmware if I connect to it with CIFS.

---

