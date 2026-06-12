---
title: "How to know which software that installed by file .deb or by command line apt-get"
date: 2018-11-11
forum: New to Ubuntu
---

### Post by yeulukem on 2018-11-11
Hello EV1

Sorry for my bad english

I'm from windows and i'm newbie in linux, i want to ask a question

I have installed some software for my pc (run ubuntu) and some app, i have installed by file .deb (download from website like teamviewer, anydesk...) but some app i have to install by command line by command sudo apt-get install.....

And now i want to uninstall software, some software has uninstall but some app i don't know how to install it

Is it possible to list which software has installed by .deb and which one installed by command line and how to remove it (by command line)

Tks for help

---

### Post by Impavidus on 2018-11-11
It doesn't matter whether software was installed from a .deb file or through apt-get. Both ways the software is registered in the package management system, so in both cases you can remove it using the package manager. apt-get is one of the interfaces to the package manager, and so are dpkg, gdebi, synaptic etc.

---

### Post by ajgreeny on 2018-11-11
Generally it is only software that you have installed by completely different, ie, non dpkg means, such as from source code, that do not show in the package management system, (even they can be made to show by installing and using **checkinstall** command instead of **make install** though I suggest as a new user that you do not investigate installing that way at the moment.

You can use the command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` to see a listing of everything installed using the apt/dpkg package management system by the time/date installed.

---

### Post by yeulukem on 2018-11-12
> **Impavidus said:**
> It doesn't matter whether software was installed from a .deb file or through apt-get. Both ways the software is registered in the package management system, so in both cases you can remove it using the package manager. apt-get is one of the interfaces to the package manager, and so are dpkg, gdebi, synaptic etc.

> **ajgreeny said:**
> Generally it is only software that you have installed by completely different, ie, non dpkg means, such as from source code, that do not show in the package management system, (even they can be made to show by installing and using **checkinstall** command instead of **make install** though I suggest as a new user that you do not investigate installing that way at the moment.

You can use the command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` to see a listing of everything installed using the apt/dpkg package management system by the time/date installed.

Tks very much, work like charm :)

Love Ubuntu

---

