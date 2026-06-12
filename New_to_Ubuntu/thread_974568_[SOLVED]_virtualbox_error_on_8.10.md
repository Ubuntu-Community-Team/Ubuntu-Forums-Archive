---
title: "[SOLVED] virtualbox error on 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by akkad on 2008-11-07
i've just installed 8.10, am trying to install virtualbox 2.0.2 where am facing this error :

[COLOR="Red"]"dependency is not satisfiable: libqtcore4"[/COLOR]

any idea ??

---

### Post by shifty_powers on 2008-11-07
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

get the deb file. it's better than the ose version anyways...

---

### Post by akkad on 2008-11-07
> **shifty_powers said:**
> [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

get the deb file. it's better than the ose version anyways...

in fact it is the same one i have downloaded, am not using the ose one.

---

### Post by akkad on 2008-11-07
> **akkad said:**
> in fact it is the same one i have downloaded, am not using the ose one.

any one can help??

---

### Post by akkad on 2008-11-07
solved, it was about perform ubuntu update before installing vbox, thnx anyway.

---

### Post by stinger30au on 2008-11-07
correct me if im wrong, but the 8.10 version of virtual box has more features then the 8.04 version from the repos

---

### Post by jamesallen on 2011-05-04
apt-get install libcurl3 libgl1-mesa-glx libqt4-network libqt4-opengl libqtcore4 libqtgui4
 
Above will fix that error message
also learn to use dpkg and apt-get
This version worked under

virtualbox-4.0_4.0.6-71344~Debian~lenny_amd64.deb

Linux debian 2.6.26-2-amd64 | Working 


[www.faqs.org](www.faqs.org)
and
[http://adeb.posterous.com/oh-debian-how-i-dislike-you](http://adeb.posterous.com/oh-debian-how-i-dislike-you)
and
[www.debian-administration.org](www.debian-administration.org)
Searching those will give you more knowledge

---

