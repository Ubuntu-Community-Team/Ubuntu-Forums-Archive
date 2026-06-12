---
title: "Problem with the initramfs generation"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by krede21 on 2008-09-25
Got the dkpg-error.

Typed 
```
dpkg --configure -a
```

In this is what i got:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
mv: cannot stat `/boot/initrd.img-2.6.24-19-generic.new': No such file or directory
dpkg: underproces post-installation script returnerede afslutningsstatus 1
root@John:/home/christian#


underproces post-installation script returnerede afslutningsstatus 1

means something like:

"subprocess post-installation script returned finishing-status 1".

What's my problem? 
And most important, how do I solve it?

---

### Post by Spaceman Spiff on 2008-09-25
I'm kind of new but at first glance I would say you're missing a header file?  Look up how to get that file "initrd.img-2.6.24-19-generic.new."  Do a locate on it in terminal, maybe you need to mv it to the /boot directory before you run that command?

---

### Post by krede21 on 2008-09-26
I wasn't able to find anything about "initrd.img-2.6.24-19-generic.new" - so i'm really stuck here - any help guys?

---

### Post by krede21 on 2008-09-26
Anyone?

---

### Post by krede21 on 2008-09-27
Bump

---

### Post by drs305 on 2008-09-27
krede21,

Did you run the command in the first post as root?
```
sudo dpkg --configure -a
```

If that doesn't fix things, if you run the following do you see "/boot/initrd.img-2.6.24-19-generic.new"
```

ls /boot/initrd.img-2.6.24-19-generic*

```

---

