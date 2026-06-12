---
title: "Changing symlink to gcc compiler quick and easy - howto."
date: 2006-09-22
forum: Programming Talk
---

### Post by Carbonunit1 on 2006-09-22
I have a quick and easy way to change the gcc compiler symlink in graphical mode.

Call the gnome browser in root mode by typing:

 ***sudo nautilus --no-desktop***

Delete the old *'gcc'* symlink in '*/usr/bin*' (in this instance the link is associated with gcc-4.0). Right click the gcc-3.4 compiler file, then click *'make link'* in menu and name it *'gcc'*. that's it! 

now bring up a shell and type:

 ***gcc -v***

If all went right you should see the reference to the proper gcc 
compiler.

---

### Post by -Rick- on 2006-09-22
Most Makefiles support CC and CXX enviroment variabels, so putting something like

```

export CC="gcc-3.4"
export CXX="g++-3.4"

```

in your .bashrc might be easier and cleaner.

---

### Post by skymt on 2006-09-22
GCC should use the Debian alternatives system:```
sudo update-alternatives --config gcc
```

---

