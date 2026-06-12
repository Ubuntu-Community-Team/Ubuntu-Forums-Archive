---
title: "Updating to Ubuntu 12.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by chase321 on 2012-05-04
Hello, i am trying to upgrade to ubuntu 12.04 from 11.10. in the update manager, i can see the button to upgrade to 12.04 LTS, but when i click upgrade it starts to download the upgrade tools and a bout halfway through the download the update manager closes... any idea what i should do?

---

### Post by Bölvaður on 2012-05-04
Open the terminal (ctrl+alt+C) and write
```
gksu update-manager
```
Write in your password and try again, there might be interesting things popping up in the terminal just before it closes. What that is, is what we would want to see.

---

### Post by chase321 on 2012-05-04
I did the command you said and got this:


chase@Chase-Linux:~$ gksu update-manager

(gksu:10967): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:10967): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:10967): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:10967): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by jonedney on 2012-05-04
Hello Chase!

Try installing this, then try to upgrade and see if you get anywhere:

```
sudo apt-get install gtk2-engines-pixbuf
```

Thanks!
Jon

---

### Post by chase321 on 2012-05-05
Thanks it worked!! :)

---

