---
title: "To Python People"
date: 2007-07-06
forum: Programming Talk
---

### Post by Nekiruhs on 2007-07-06
I'm making my own Python Front end for locate/slocate. I am using PyGTK. I am struggling to get the contents of a text bow coded in PyGTK to be passed to the bash command locate. I am calling the BASH Command like this os.system('locate SearchTermWouldBeHere') I just need to know how to pass data from PyGTK to bash

---

### Post by runningwithscissors on 2007-07-07
Does this not work?
```
os.system('locate ' + text_box.get_chars(0, -1))
```

---

### Post by steve.horsley on 2007-07-07
runningwithscissors is probably right. But you may well want to use popen instead of system, so you can read the output from the locate process:
pin, pout = popen4('locate ' + text_box.get_chars(0, -1))
result = pin.readlines()

---

### Post by Smygis on 2007-07-07
you can also use the commands module.

like.
```

>>> import commands
>>> result = commands.getoutput("locate %s" % ("pypanel"))
>>> result
'/usr/share/doc/pypanel\n/usr/share/doc/pypanel/changelog.Debian.gz\n/usr/share/doc/pypanel/README.gz\n/usr/share/doc/pypanel/copyright\n/usr/share/man/man1/pypanel.1.gz\n/usr/share/menu/pypanel\n/usr/share/pypanel\n/usr/share/pypanel/ppicon.png\n/usr/bin/pypanel\n/etc/pypanelrc\n/var/lib/dpkg/info/pypanel.conffiles\n/var/lib/dpkg/info/pypanel.postinst\n/var/lib/dpkg/info/pypanel.postrm\n/var/lib/dpkg/info/pypanel.md5sums\n/var/lib/dpkg/info/pypanel.list\n/var/crash/_usr_bin_pypanel.1000.crash\n/home/smygis/.pypanelrc\nhome/smygis/.pypanelrc~'
>>> print result
/usr/share/doc/pypanel
/usr/share/doc/pypanel/changelog.Debian.gz
/usr/share/doc/pypanel/README.gz
/usr/share/doc/pypanel/copyright
/usr/share/man/man1/pypanel.1.gz
/usr/share/menu/pypanel
/usr/share/pypanel
/usr/share/pypanel/ppicon.png
/usr/bin/pypanel
/etc/pypanelrc
/var/lib/dpkg/info/pypanel.conffiles
/var/lib/dpkg/info/pypanel.postinst
/var/lib/dpkg/info/pypanel.postrm
/var/lib/dpkg/info/pypanel.md5sums
/var/lib/dpkg/info/pypanel.list
/var/crash/_usr_bin_pypanel.1000.crash
/home/smygis/.pypanelrc
/home/smygis/.pypanelrc~

```

And if you want a list, simply .split("\n") it.

---

