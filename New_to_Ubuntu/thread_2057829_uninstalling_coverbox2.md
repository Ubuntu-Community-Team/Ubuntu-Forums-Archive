---
title: "uninstalling coverbox2"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-09-14
okay i am at a loss. link to program at bottom of post. i installed okay. however i cant remove it keeps autostarting. it is not listed in the startup programs. i have deleted the files including the config. but the config file still loads. cant find the program using the spm . running ubuntu 12.04. any ideas 


[http://www.omgubuntu.co.uk/2012/08/coverbox-puts-music-artwork-controls-on-the-ubuntu-desktop?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+(OMG!+Ubuntu](http://www.omgubuntu.co.uk/2012/08/coverbox-puts-music-artwork-controls-on-the-ubuntu-desktop?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+(OMG!+Ubuntu)!)

---

### Post by cyb3r_sn4k3 on 2012-09-14
I've never used coverbox2 but if your lucky. From your source directory you might be able to run.
```

make uninstall 

```

Also, check hidden folders in your home directory.

---

### Post by rburkartjo on 2012-09-14
cyb tks but i solved it this way. searched and found that there was a coverbox link in etc/xdg/autostart and it was also placed in usr/bin and usr/share. just opened all as root and deleted.did the trick. the weird thing is that if i logged into xubuntu the program would  behave go figure.

---

### Post by jerrrys on 2012-09-14
Maybe search coverbox in Nautilus and see what you missed.

---

### Post by rburkartjo on 2012-09-14
yup did that jer. should of thought of it

---

