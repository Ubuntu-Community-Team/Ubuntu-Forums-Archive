---
title: "Can't compile xrdp - missing libvnc"
date: 2007-05-03
forum: Programming Talk
---

### Post by FizzBuntu on 2007-05-03
Hello
I don't know if I'm in the good forum...
I'm trying to compile xrdp and it says that it can't find the libvnc.so file.
I'v tried and search for it and only found that it was supposed to be a part of VNC, but I didn't get the chance to actually find the file...

Any clue ?

---

### Post by hod139 on 2007-05-03
you probably need to install the libvncserver-dev package.

---

### Post by WW on 2007-05-04
I don't know if this is what you need, but the package  **vnc4server** (in universe) provides usr/lib/xorg/modules/extensions/libvnc.so

---

### Post by FizzBuntu on 2007-05-04
ok, found it in vnc4server (still can't compile 'cause it's missing other libs...)

thx

---

