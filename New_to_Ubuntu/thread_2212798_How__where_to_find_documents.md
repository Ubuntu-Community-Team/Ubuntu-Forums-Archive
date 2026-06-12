---
title: "How / where to find documents"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by Nosphky on 2014-03-23
New to Ubuntu 13.10 64bit.  I installed KeePass2 using the Software centre.  On the KeePass2 page, there was a list of optional add-ons from which I selected 'Password Manager - Documentation (keepass2-doc)'.  The size of the download increased appropriately so I supposed that the option was included.

After successful installation and import of existing database, KeePass2 worked fine but I can't find the optional documentation.

I tried using the 'search your computer' facility in the icon tray on left side of screen (top icon) and also tried laboriously going through the file structure looking at anything with keepass in the name but did not find the 'keepass2-doc'.

Can someone please advise me of the simplest way to search for a file and the likely places that documentation would be stored in the ubuntu file structure during installation ?  Thanks.

---

### Post by Dave_L on 2014-03-23
For an installed package, you can view the list of installed files with the command:
```
dpkg --listfiles PACKAGE-NAME
```

The --listfiles option can be abbreviated as -L.

Synaptic also shows this information.  I don't remember if the Software Center does this.

---

### Post by steeldriver on 2014-03-23
... it's usually somewhere like /usr/share/doc/<progname> i.e. in this case /usr/share/doc/keepass2

---

### Post by Dave_L on 2014-03-23
I forgot about packages.ubuntu.org.  It shows the files from that package:
[http://packages.ubuntu.com/saucy/all/keepass2-doc/filelist](http://packages.ubuntu.com/saucy/all/keepass2-doc/filelist)
So they are, as steeldriver said, in /usr/share/doc/keepass2

---

### Post by Nosphky on 2014-03-23
Thanks Dave and Steeldriver.  I couldn't find keepass2-doc using the means you suggested so I concluded it had not been installed as the option - probably something wrong in the way I did it first time ?  

 However, all's well - I reselected and installed the option again just now and have now found the keepass2-doc in /usr/share/doc/keepass2-doc

I also found /usr/share/doc/keepass2  and at first glance, the contents of keepass2 and keepass2-doc seem to be the same.   I live and learn.  Thanks again for your help.

---

