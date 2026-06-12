---
title: "Newest Muine"
date: 2005-02-03
forum: Repositories &amp; Backports
---

### Post by stwog on 2005-02-03
I tried out Muine music player quite a while ago and I really enjoyed it. I stopped using it though do to some stuff it was missing and development wasn't moving very quickly. These days that seems to be changing and development has picked up again. I tried to build the newest version on my box, but its too difficult to get my Ubuntu box setup for development work with mono and it always fails. The version in  the repositories is quite old now and I would really like to try the new one. Could someone build the newest version for me and provide a package? Thanks to anyone that can.

Simon

---

### Post by ow50 on 2005-02-03
I just installed the new 0.8.1 version so while at it a made a deb package with checkinstall. Get it [here](http://koti.mbnet.fi/ots/ubuntu/).

I don't know if it works for you, this is the first time for me building a deb package.

---

### Post by stwog on 2005-02-04
I tried the package, thanks, but it didn't seem to work for me. I think it might be a mono problem. This is the error I get:


** (/usr/lib/muine/muine.exe:15802): WARNING **: Could not find assembly gtk-sharp, references from /usr/lib/muine/muine.exe (assemblyref_index=1)


It might be a build problem though as I know I have GTK# installed. I'll play around with it. Thanks.

Simon

---

### Post by ow50 on 2005-02-04
The un-apt-gettable stuff i had to install to get muine to compile was gtk-sharp and dbus-sharp. I'm not sure whether these are needed for running or just for compiling.

Gtk-sharp I installed from source. It was the latest version, unstable 1.9.1 from [the sourceforge project download page](http://sourceforge.net/project/showfiles.php?group_id=40240).

Dbus-sharp i could't get to compile so I installed it by aliening an fc3 rpm package. I installed version 0.22-13 found from [rpm.pbone](http://rpm.pbone.net/).

---

### Post by kmf on 2005-02-07
What about ...... [http://muine.gooeylinux.org/muine-0.8.2.tar.gz](http://muine.gooeylinux.org/muine-0.8.2.tar.gz) ?

Karl ;)

---

### Post by ow50 on 2005-02-07
[QUOTE=kmf]What about ...... [http://muine.gooeylinux.org/muine-0.8.2.tar.gz](http://muine.gooeylinux.org/muine-0.8.2.tar.gz) ?

Karl ;)[/QUOTE]
Does this mean the package I made works?
Either way I uploaded a package for 0.8.2.
[[link]](http://koti.mbnet.fi/ots/ubuntu/)

---

### Post by el toro on 2005-02-07
I just installed 0.8.2 from source...took a few minutes to get all the packages (gtk-sharp,etc.), but I'd been waiting for a .deb for so long I just couldn't take it anymore.  :D

---

