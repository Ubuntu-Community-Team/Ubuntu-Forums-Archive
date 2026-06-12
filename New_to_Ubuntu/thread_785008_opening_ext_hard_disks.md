---
title: "opening ext hard disks"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by SKDas on 2008-05-07
hello ,
1 ubuntu hardy heron-installed with wubi in D drive.it detects the ext hard disks but wont let me open them. 
2 how to log in as root in ubuntu.
3 i have a tata indicom usb plug to surf.how to make it run.
4 how to install vlc media player . it has all the codecs.
5 how to install blender--for 3d applications
would really appreciate help-i'm stuck.
oh yes-i have ibm r51 laptop with 768 ram,1.77ghz processor,installed through wubi on windows xp

---

### Post by subzero316 on 2008-05-07
> **SKDas said:**
> hello ,
1 ubuntu hardy heron-installed with wubi in D drive.it detects the ext hard disks but wont let me open them. 
2 how to log in as root in ubuntu.
3 i have a tata indicom usb plug to surf.how to make it run.
4 how to install vlc media player . it has all the codecs.
5 how to install blender--for 3d applications
would really appreciate help-i'm stuck.
oh yes-i have ibm r51 laptop with 768 ram,1.77ghz processor,installed through wubi on windows xp

To log in as root
```
su
```

you might wanna set the password initially usind sudo passwd command

```
apt-get install vlc
apt-get install blender
```

---

### Post by subzero316 on 2008-05-07
> 1 ubuntu hardy heron-installed with wubi in D drive.it detects the ext hard disks but wont let me open them.

Try changing the permissions using command 
```
chmod
```
use prefernces accordingly

---

