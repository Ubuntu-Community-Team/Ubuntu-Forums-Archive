---
title: "Can't print with Lexmark S405 Lubuntu 12.10 cups-insecure filter - what gives?"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by sgarre13 on 2013-01-27
So, everything in Lubuntu is working fine on my Emachines em350 Netbook, but I thought I'd try printing which is a doddle to setup on Windows XP and that's where it went wrong.

I've downloaded the deb packages from the Lexmark website - they were for Ubuntu 12.04, but it's the closest to what I've got - so should work. Packages installed fine, no worries. Now when I try to print something as a test I get a cups-insecure filter error warning.

Lots of posts but for a noob, no clear set of commands available or process to sort this out. And as a comment - why should I have to sort this out, since nothing hints at this problem during setup, I should be printing reams of stuff by now, but there's this stupid security restriction imposed in some program called CUPS which appears abitrary and artificial. In other words it's a problem which didn't need to exist and helps no one.

Please educate me and also convince me that this is better than the windows route!

---

### Post by sgarre13 on 2013-01-27
well finally I sorted it:-

I just change the permission on the file :
cd /usr/local/lexmark/v3/bin/
sudo chmod 755 printfilter

from [http://ubuntuforums.org/showthread.php?t=2082570](http://ubuntuforums.org/showthread.php?t=2082570)

Thanks.

but my comment still stands and I might expand on it and ask why a noob has to do this?

---

### Post by lavinog on 2013-02-09
It looks like the permissions were set to 775 which means that the group has edit access to the file.  This is usually a security issue because members of the group have the ability to edit a system file instead of just being able to execute it.
However, it looks like the group was set to root, so it prob was not a big deal...but since there was no real reason for the group to have write access, the system likely just being cautious and blocked it.
```

drwxr-xr-x 3 root bin    4096 Feb  8 21:30 ./
drwxr-xr-x 8 root bin    4096 Feb  8 21:30 ../
-rwxr-xr-x 1 root bin  755469 Aug 16 00:35 lxhcp*
-rwxrwxr-x 1 root bin  110411 Aug 16 00:35 lxusb*
-rwxrwxr-x 1 root root 146921 Aug 16 00:35 printfilter*
drwxr-xr-x 2 root bin    4096 Feb  8 21:30 .scripts/

```

Edit:  I would suggest chmodding lxusb to 755 also.

FYI: Many websites get hacked because of a single file being set to 777 or 775

---

### Post by zafo on 2013-10-21
I upgraded from 13.04 to 13.10 and encountered this problem. I tried several other suggestions to change various permissions, but this is the one that did it. My Lexmark S815 is working again!  Thanks.

---

