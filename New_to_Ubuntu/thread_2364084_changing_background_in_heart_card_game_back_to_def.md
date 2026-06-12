---
title: "changing background in heart card game back to default setting"
date: 2017-06-18
forum: New to Ubuntu
---

### Post by newblank25 on 2017-06-18
I changed the background in hearts. i don't like what i did so how can I change it back. i only see back ground image as dondorf.svg and also card style as dondorf.svg but not default settings. I tried uninstalling & then insatlling it but I don't get default setting.

---

### Post by #&amp;thj^% on 2017-06-18
Do you have "gnome-cards-data" installed?
Or just show the return of this from the terminal:
```
apt-cache policy gnome-cards-data
```

---

### Post by newblank25 on 2017-06-18
gnome-cards-data:
  Installed: 1:3.18.2-1ubuntu1
  Candidate: 1:3.18.2-1ubuntu1
  Version table:
 *** 1:3.18.2-1ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
        100 /var/lib/dpkg/status
This is what was shown. so how does this allow me to change the layout? thx for help.

---

### Post by howefield on 2017-06-19
The default image can be found in /usr/share/pixmaps/gnome-hearts

So, Preferences > Style > Choose a background image > navigate to the above folder.

---

### Post by newblank25 on 2017-06-19
thx it worked

---

### Post by howefield on 2017-06-20
> **newblank25 said:**
> thx it worked

You're welcome, feel free to mark the thread as solved.

---

