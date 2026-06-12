---
title: "[SOLVED] editing is getting impossible!!"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-09
i cant seem to edit any files with out an error,nomatter what i use to edit i get this;ick@kubuntu-1:~$ su
Password:
root@kubuntu-1:/home/rick# kwrite /etcc/udev/rules.d/10-custom.rules
No protocol specified
kwrite: cannot connect to X server :0.0
root@kubuntu-1:/home/rick# kdesudo kwrite /etc/udev/rules.d/10-custom.rules
No protocol specified
kdesudo: cannot connect to X server :0.0
root@kubuntu-1:/home/rick#
is there a fix??
rick

---

### Post by cdtech on 2008-08-09
Your already root why use "kdesudo" just do "kwrite /etc/udev/rules.d/10-custom.rules"?

**P.S.**
never mind I see what your doing, kdesu

---

### Post by tinker312 on 2008-08-09
Hi Rickstr66, this previous thread may be useful for you.  [http://ubuntuforums.org/showthread.php?t=307984](http://ubuntuforums.org/showthread.php?t=307984) Happy Kbuntuing :)

---

### Post by InfinityCircuit on 2008-08-09
su will not work with X unless you let it (I think you do this with xhost +).  If you want to run root applications in X you have two safe choices:

1) kdesu

2) sudo apt-get install sux && sux.  sux is a wrapper for su that gives X privileges.

---

### Post by rixtr66 on 2008-08-09
infinitycircut;it worked like a charm,thank you!!
rick:)

---

