---
title: "[SOLVED] Having trouble with Mount syntax."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by philinux on 2008-06-29
sudo mount  -t vboxsf vboxshare /home/philinux/Desktop/SharedFiles

The above command works fine but I end up with the folder SharedFiles with root only access.

I tried adding -o user to the command but it fails.

---

### Post by Rocket2DMn on 2008-06-29
Have you tried using umask, like umask=000 ?

---

### Post by philinux on 2008-06-29
No I haven't.

[http://www.acm.uiuc.edu/workshops/cool_unix/umask.html](http://www.acm.uiuc.edu/workshops/cool_unix/umask.html)

I thought -o user would make the directory accessible from any user.

I need to get the mount syntax correct

---

### Post by Rocket2DMn on 2008-06-29
I haven't used the vbox mounting stuff, but the syntax is
```
sudo mount <filesystem> <mount point> -t <fsytype> -o <options,with,commas,no,spaces>
```
So something like
```
sudo mount vboxshare /home/philinux/Desktop/SharedFiles -t vboxsf -o uid=1000,umask=000
```
The placement of the command line options (with a dash) doesn't actually matter.  You can fiddle around with different options.  That will set permissions 777 (because umask is 000) and should be owned by the user with uid 1000, aka the original username on the system.

---

### Post by philinux on 2008-06-29
sudo mount vboxshare /home/philinux/Desktop/SharedFiles -t vboxsf -o uid=1000

That did the trick umask came up as unknown option.

I assume uid=1000 is my normal user then.

---

### Post by Rocket2DMn on 2008-06-29
Maybe umask isn't available for that FS (?).  Yes, you should have uid 1000 unless you are running a system with multiple users.

---

