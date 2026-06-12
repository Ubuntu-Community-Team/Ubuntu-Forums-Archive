---
title: "Tip for installing Tile support on Tcl/Tk 8.4"
date: 2007-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Icarosaurus on 2007-04-30
I needed Tile support on Tcl/Tk 8.4 for using better skins on amsn with the Chameleon plugin.
Well, I just downloaded it the 0.7.8 version from:
[http://sourceforge.net/project/showfiles.php?group_id=11464]("http://sourceforge.net/project/showfiles.php?group_id=11464")
extracted it and opened a terminal in the extracted directory for compiling it:
```

$ ./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4
$ make
$ sudo make install

```
I found the tip in the wiki:
[http://wiki.tcl.tk/11075]("http://wiki.tcl.tk/11075")
It should work starting from Ubuntu 5.10 to 7.04 ...
See you!

---

### Post by GatorV on 2007-11-01
Thanks for your tip, also if you are compiling remember to install the -dev packages from synaptic for Tk8.4 and TCL8.4, before running ./configure.

---

