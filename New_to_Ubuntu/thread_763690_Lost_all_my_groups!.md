---
title: "Lost all my groups!"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by wooly on 2008-04-23
A little knowledge is a dangerous thing.

I created a new group 'common" and wanted to add myself to it.
```
usermod -G common john
```
I didn't use the -a option, so I lost all my groups.

I would appreciate if some forum users would type: 
```
groups
```
in a shell and tell me what the output is.
I Know that the setup may be different on different computers, but at least it's a start. 

Thanks in advance.

---

### Post by sdowney717 on 2008-04-23
scott@scott-desktop:~$ groups
scott adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin sambashare vboxusers
scott@scott-desktop:~$

---

### Post by jken146 on 2008-04-23
The most important one you'll need is admin.  Then there's likely audio, cdrom, floppy, plugdev, scanner, video, scanner and maybe some others.  The Users and Groups app in GNOME has a list of useful ones.

---

### Post by wooly on 2008-04-23
> scott@scott-desktop:~$ groups
scott adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin sambashare vboxusers

> The most important one you'll need is admin. Then there's likely audio, cdrom, floppy, plugdev, scanner, video, scanner and maybe some others. The Users and Groups app in GNOME has a list of useful ones.

Thank you both. I will check /etc/group and see which of those are listed.

---

