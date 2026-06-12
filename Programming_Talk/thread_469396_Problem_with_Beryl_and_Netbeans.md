---
title: "Problem with Beryl and Netbeans"
date: 2007-06-09
forum: Programming Talk
---

### Post by malfist on 2007-06-09
If I launch netbeans with beryl running I only get a blank splash screen and can't do anything with it. Even worse, when I go back to GNOME (restart X and turn off Beryl) netbeans tells me it can't find some things like the Java Debug thingy and will only let be create new projects with an exsisting ant script.

Do I need to reinstall Java SDK? How would I fix the Beryl problem?

On a side note, once Beryl is running, checkgmail doesn't respond to my clicks anymore :(

---

### Post by samjh on 2007-06-10
Beryl/Compiz is not compatible with Swing (Java's standard GUI library).

As for your other problem with Netbeans, it's been commonly reported but I haven't experienced it personally.  Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=448764](http://ubuntuforums.org/showthread.php?t=448764)

---

### Post by malfist on 2007-06-10
I fixed it, I went to the module manager and selected the options that had been turned off for some reason on installation. Although Beryl/Compiz not compatable with Swing is a bummer. What about the checkgmail thing?

---

### Post by Freaky#Funga on 2007-11-26
> **malfist said:**
> I fixed it, I went to the module manager and selected the options that had been turned off for some reason on installation. Although Beryl/Compiz not compatable with Swing is a bummer. What about the checkgmail thing?

Could You please tell me exactly how You've fixed this (which modules etc.)?
Thanks

---

### Post by malfist on 2007-11-27
Egads, it's been forever since I did that. That link should help you, there's two ways to do it and the second worked for me.

Is it not fixed for compiz-fusion, I think it is.

---

### Post by malfist on 2007-11-27
The missing options was due to automatix not installing all the defual moduals, they are included with netbeans so use it's linux installer (don't use automatix unless nessecary). The blank stuff was due to beryl not working with flash, there are fixes and patches floating around, just google for beryl and swing.

---

### Post by mssever on 2007-11-27
To fix the swing/beryl incompatibility, put the following in /etc/profile, log out, then back in.
```
export AWT_TOOLKIT=MToolkit
```

---

### Post by Freaky#Funga on 2007-11-28
> **mssever said:**
> To fix the swing/beryl incompatibility, put the following in /etc/profile, log out, then back in.
```
export AWT_TOOLKIT=MToolkit
```

Thanks a lot, this absolutely solved my problem. :KS

---

