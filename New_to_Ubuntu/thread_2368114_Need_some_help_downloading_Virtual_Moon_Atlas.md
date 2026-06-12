---
title: "Need some help downloading Virtual Moon Atlas"
date: 2017-08-07
forum: New to Ubuntu
---

### Post by toukiedatak on 2017-08-07
Im trying to download virtual moon atlas and followed the instructions but still get an error. After choosing in which directory it needed to download it instructed me to type:


export LD_LIBRARY_PATH=Prog/lib && Prog/bin/atlun

I get this error:
Could not load library libvma404.so Please try to reinstall the program.
I've already re-installed it multiple times but nothing works.
Someone has the same issue as me in this thread but no solution is found:
[https://ubuntuforums.org/showthread.php?t=2277679](https://ubuntuforums.org/showthread.php?t=2277679)

---

### Post by cariboo on 2017-08-07
I just downloaded if from [here]("http://www.ap-i.net/avl/en/download"), I chose the Linux version of Pro 6.0, Once I downloaded it I opened, it with Archive Manager, extracted it to my Downloads directory, then ran:

```
sudo ~/Downloads/vmapro_install.sh
```

Once it was installed, I ran:

```
/usr/local/bin/atlun
``` 

as a regular user, which result in the attached picture

BTW, I'm running Xubuntu 17.10, so if anyone should run into trouble, it should be me. :)

---

### Post by toukiedatak on 2017-08-08
It asks me in which directory I want to add it: usr or local. Which one should I pick?

---

