---
title: "Owner"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by phantalon on 2008-05-04
I've just formatted a new drive and Ubuntu tells me that I'm not the owner...how do i take ownership of this drive?

---

### Post by kirios on 2008-05-04
Is it an external drive? Type **mount** in a terminal (Applications > Accessories > Terminal) _with the drive connected_ and post the output here.

---

### Post by tamoneya on 2008-05-04
use the chown command (change owner) after you have mounted the files.  It will look something like this```
sudo chown -R username /directory/of/drive
``` -R makes it recursive and will make you the owner of all sub directories as well.

---

### Post by msrinath80 on 2008-05-04
If you have just formatted a new drive, the correct *nix way to use it is to first create a directory (as root) on the media after mounting it. Then you should chown and chgrp that directory to your username/group (usually the same as the username). Now, you unmount and unplug the drive and then replug it in. This time you will be able to see the directory you created and will have full read/write access to it.

---

### Post by phantalon on 2008-05-04
Not sure how to create a directory, it's an internal drive and it shows up as /dev/sda1...

---

### Post by tamoneya on 2008-05-04
the first thing you need to do is mount.  Execute the following command:```
sudo mkdir /otherdrive
sudo mount /dev/sda1 /otherdrive
cd /otherdrive
ls
```
That should list the files in the root of your other partition.

---

### Post by subzero316 on 2008-05-04
> **phantalon said:**
> Not sure how to create a directory, it's an internal drive and it shows up as /dev/sda1...


Use
```

sudo mkdir <directory name>
```

:KS

---

### Post by phantalon on 2008-05-04
phantalon@phantalon-desktop:~$ sudo mkdir /otherdrive
mkdir: cannot create directory `/otherdrive': File exists
phantalon@phantalon-desktop:~$ sudo mount /dev/sda1 /otherdrive
mount: /dev/sda1 already mounted or /otherdrive busy
mount: according to mtab, /dev/sda1 is already mounted on /otherdrive
phantalon@phantalon-desktop:~$ cd /otherdrive
phantalon@phantalon-desktop:/otherdrive$ ls




ok now what...drive doesn't show up in 'places' now

---

### Post by subzero316 on 2008-05-04
Theres a [COLOR="Red"].gtk-bookmarks[/COLOR] file in your home directory ...

append the location you want in it

---

### Post by phantalon on 2008-05-04
Well I can write to the drive now but it wont show permissions...

---

### Post by subzero316 on 2008-05-05
TRY,

```
ls -l
```

it`ll list with permissions

---

### Post by phantalon on 2008-05-05
Thank you all for your help how do i mark this solved?

---

### Post by subzero316 on 2008-05-05
See if it is in the thread tools on top..

for the Thank you you could click the medal on the right end corner of d reply of the user

---

