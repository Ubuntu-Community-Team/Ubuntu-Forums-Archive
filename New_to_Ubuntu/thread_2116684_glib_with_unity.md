---
title: "glib with unity"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by asnain on 2013-02-16
hi,
i accidently installed glib on my 64 bit ubuntu 12.04 and now the system won't start it only shows me a the initial splash  screen
any idea what to do?????

---

### Post by Frogs Hair on 2013-02-16
Hello and Welcome

You may be able to remove the package from the TTY console but you need have the _complete package name_ . 

When the splash screen appears press Ctrl + Alt + F1 .

If you are successful the black screen will read Ubuntu TTY

Where it says Login enter user name in lower case and then enter password below. 

Remove the Package (lower case) 
```
sudo apt-get remove insert package name here
```

After the package is removed 
```
sudo reboot
```

---

### Post by schragge on 2013-02-16
> **asnain said:**
> I accidently installed glibDo you mean [libglib2.0-0](http://packages.ubuntu.com/quantal/libglib2.0-0)?

---

### Post by asnain on 2013-02-17
i tried 
```
sudo apt-get remove 
```
but it didn't work
i had tried to install the package from its source and went too deep

the source was glib-2.34.3.tar.xz

---

### Post by schragge on 2013-02-17
I guess you've installed it with *make install*, right? Then try
```

sudo make uninstall-local

```

---

### Post by Frogs Hair on 2013-02-17
I don't know if the command below will work as written the exact package name is required. 

```
sudo apt-get remove glib-2.34.3
```

---

### Post by schragge on 2013-02-17
No, it won't work because the library has been built and installed from source, and thus, is unknown to APT. Besides, there's no such package *glib-2.34.3* in Ubuntu repositories. Moreover, the suggested name violates package naming policy on Debian-based systems.

---

### Post by asnain on 2013-02-18
already tried that....won't work either
also searched the internet for help...nothing helped
i think i will just reinstall my ubuntu

---

