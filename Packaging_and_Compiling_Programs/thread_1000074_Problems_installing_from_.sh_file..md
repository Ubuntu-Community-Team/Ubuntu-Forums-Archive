---
title: "Problems installing from .sh file."
date: 2008-12-02
forum: Packaging and Compiling Programs
---

### Post by Tamalin on 2008-12-02
I am trying to install CDEverywhere from the .sh script they give me, but every time I try, I get the following error message:

Preparing to install...
/tmp/install.dir.7666/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I tried running
sudo apt-get install libstdc++-dev
but I was told it was a virtual package...  So I ran
sudo apt-get install libstdc++6-4.1-dev,
but when I ran the installer script from CDEverywhere again.  I recieved the same error...

Can anyone help me?  Thanks!

---

### Post by Meow27 on 2008-12-03
you actually have to find that particular package (you need the same thing for epsxe )

ill try too look for it as well (i need to keep i copy of it @_@)

edit- you might need to use alien to convert it into a deb file... just a heads up

---

### Post by Meow27 on 2008-12-14
i cant find it... sry

---

