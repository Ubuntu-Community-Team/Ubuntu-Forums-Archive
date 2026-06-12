---
title: "distribute.sh No such file or directory found."
date: 2014-07-08
forum: New to Ubuntu
---

### Post by shane27 on 2014-07-08
Hi,

I'm trying to deploy a Python / Kivy app to an Android device using the advice here: [http://kivy.org/docs/installation/installation-linux.html](http://kivy.org/docs/installation/installation-linux.html)

I've tried both Buildozer (first) and the manual route, but I keep having the issue with '**./distribute.sh No such file or Directory**'

From what I understand, it has been superseded by other libraries. I've tried installing  [FONT=Arial]lib32z1, lib32ncurses5,  lib32bz2-1.0 but still get the same result.[/FONT]

I'm very new to Linux & Ubuntu, so please be gentle. Yes, I have searched the forums / googled, but found nothing.

I'm using Ubuntu 14.04 on a 64 bit machine.

---

### Post by Vladlenin5000 on 2014-07-08
Hi, welcome.

Are you sure you're running (trying to) from the folder where distribute.sh actually is?

---

### Post by shane27 on 2014-07-09
Thanks Vladlenin5000,

I'm not certain as I don't know (can't find) the file location in Ubuntu. When I use find, it directs me to a web search, so I suspect that it doesn't exist locally?

I miss Hitch as well.

Thanks.

---

### Post by shane27 on 2014-07-11
**SOLVED.**
I used the Linux command **find / -name "distribute.sh"** **-f** to find a copy of the file, and copied that to the target directory. Worked like a charm.

---

