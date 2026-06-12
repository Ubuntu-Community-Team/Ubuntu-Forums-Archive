---
title: "update needs untrusted pkgs"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by donaldshelton on 2012-11-13
31 pkgs need updating  but i get this message:

checkbox checkbox-qt gir1.2-gtk-3.0 grub-common grub-pc grub-pc-bin grub2-common isc-dhcp-client isc-dhcp-common libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 qdbus seahorse

how to accept untrusted sources?

---

### Post by mardybear on 2012-11-14
Hi donaldshelton.

You could try updating your system via terminal and it might get the bugs out:

Close your update manager GUI

Open terminal (may use ctrl-alt-t combo)

Enter 'sudo apt-get update'

Enter 'sudo apt-get upgrade'

Hopefully these commands run through okay. If not, post your results especially any messages when you ran apt-get update. I sometimes get hiccups when running apt-get update myself, simply running it through again (twice succession) seems to work. Haven't missed an update yet.

mardybear

---

### Post by NikTh on 2012-11-14
Hi  , 

please close all other applications and open only a terminal (CTRL+ALT+T keys combo). Copy-paste from here bellow commands , one line at time 
```
sudo apt-key update 
sudo apt-get update ; sudo apt-get dist-upgrade
```

Give the results back here. 
**Click on "New Reply" and put the results inside [CODE] tags to be easier to read. **[See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by donaldshelton on 2012-11-14
Thanks  That did the trick!!:guitar:

---

