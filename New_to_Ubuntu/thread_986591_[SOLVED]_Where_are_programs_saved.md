---
title: "[SOLVED] Where are programs saved?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Tpolich on 2008-11-18
I have been trying to find out where are programs saved. When I install something with "apt-get install XXXX" where does it go? Thank you in advance.

---

### Post by taurus on 2008-11-18
Most of them should be in /usr/bin.

```
ls -ls /usr/bin
```

---

### Post by aeiah on 2008-11-18
it should be noted however that configuration files tend to go in your home folder, in a hidden folder (one starting with a dot). for example, mplayer's configuration files are in ~/.mplayer

its less important to know where things are in linux than in windows when we're talking about applications. if they're not in the menu you can launch them from the terminal by typing their name, or you could add them to the menu.

---

### Post by Tpolich on 2008-11-18
thank you, you gave me enough of a lead to figure the rest out. /usr/bin only has the bin file the main body of the programs was in /usr/lib

(I was adding the new 64 flash plug in for firefox that just came out)

---

### Post by GuruX on 2008-11-18
With apt-get, you download and install packages. Ubuntu will keep track of were everything is installed, so when you use apt-get remove och apt-get purge, apt-get will remove everything will be uninstalled "automatically".

---

### Post by drs305 on 2008-11-18
The 'whereis' command is also helpful in locating a package's file location(s). For example:
```

whereis gimp

*results in:*

gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/lib64/gimp 
/usr/share/gimp /usr/share/man/man1/gimp.1.gz

```

---

