---
title: "cannot delete files from external hard drive"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by elliah on 2008-08-17
i cannot delete anything from my external hard drive...the delete option is greyed out...i used to be able to do so previously...what could be the problem here?

---

### Post by Yuki_Nagato on 2008-08-17
Try this:

"cd" to the directory with the file ->

```
ls -l
```

This displays more info about the files there, including the owner.

Does the file have you as the owner?  If not:

```
sudo chown XXX YYY
```

chown - Changes ownership of the file.
XXX - To this owner (your name)
YYY - The file name

---

### Post by ace007 on 2008-08-17
Is it an NTFS formatted drive?

If so, unless you mounted it with the ntfs-3g driver it will be mounted as read only.

Who owns the drive?

If it was mounted by another user, it may not be accessible to you.

There questions should only pertain to you if you've messed around in the fstab file.  If you haven't then read the above post, it'll at least tell you why you cant access it. Then you can work the problem out from there.

---

### Post by nicedude on 2008-08-17
This is just do to you not being the "owner" like the other person has stated. If you can't figure out the command line way to fix it. There is a program that can mount stuff for you and has helped me out allot, here is the command to install it.

sudo apt-get install pysdm

then this to start it

sudo pysdm

Once it is open you can select the drive and partition you want to mount ( its a simple GUI window so its easy to use ) and click mount and it should take care of this for you :-)

---

