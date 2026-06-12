---
title: "Gnome shell not displaying properly"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sir.sargento on 2011-09-09
Hello. Unity works just fine for me but when I login to gnome shell all I see is pretty much black and some gray pixelated squares where icons or buttons would be. I can click the activities button but cannot see it and it will show the programs etc.. Anybody else have this problem or know how to fix it?

Thanks.

---

### Post by MARP1961 on 2011-09-09
I was having problems with Gnome Shell not starting up so rather than try to find out why, I thought I would try a reinstall of Gnome Shell in Synaptic.

I opened Synaptic Package Manager, searched for Gnome Shell, marked it for reinstall, rebooted and everything worked.

The problems might be 'update related' with so many changes taking place on a daily basis.

---

### Post by paul_in_london on 2011-09-09
Fine here in my VM at work.

```
paul@oneiric:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.1.91+git20110908.092338a4-0ubuntu1~11.10~ricotz0
  Candidate: 3.1.91+git20110908.092338a4-0ubuntu1~11.10~ricotz0
  Version table:
 *** 3.1.91+git20110908.092338a4-0ubuntu1~11.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status
     3.1.4-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages
paul@oneiric:~$
```

I'm not using Unity - unless you count unity-greeter. :lolflag: This is G-S on top of a minimal Oneiric install.

Pretty sure this is the same version I was using last night on my 64 bit install at home. Had an issue the other day with that install where G-S was failing to load, but when I removed the gnome-shell-extensions-* packages all was ok again.

---

