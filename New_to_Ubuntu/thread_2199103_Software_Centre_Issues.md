---
title: "Software Centre Issues"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by bernardfernando on 2014-01-12
Hi, I have not been able to update software using the software centre at all.  I tried a few avenues suggested by a few forums etc.  Still the problem remains.  I even tried to reinstall using a USB stick, but it would not work either.  Please could you help me sort this.  Many thanks.  
```

root@bernard-desktop:/var/lib/apt# cd
root@bernard-desktop:~# sudo rm -rvf /var/lib/apt/lists/*
removed directory: `/var/lib/apt/lists/partial'
root@bernard-desktop:~# sudo apt-get update
E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
root@bernard-desktop:~# ls /etc/apt
apt.conf.d     sources.list.d            trustdb.gpg   trusted.gpg.d
preferences.d  sources.list.distUpgrade  trusted.gpg
sources.list   sources.list.save         trusted.gpg~
root@bernard-desktop:~#
```

---

### Post by joachim_altmann on 2014-01-12
Hi, I found a thread that seems to cover a similar problem. Maybe [this]("http://ubuntuforums.org/showthread.php?t=1756769") helps.

---

### Post by oldos2er on 2014-01-12
Medibuntu is no more, so it needs to be removed ```
sudo rm /etc/apt/sources.list.d/medibuntu.list* && sudo apt-get update
``` Please let us know if there are any further errors.

---

