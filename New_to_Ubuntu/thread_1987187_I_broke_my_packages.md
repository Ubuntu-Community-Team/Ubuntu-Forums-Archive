---
title: "I broke my packages"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by bug67 on 2012-05-26
I was trying to upgrade GIMP to version 2.8 following the instructions here:

[http://www.tuxgarage.com/2012/05/install-gimp-2-8-in-precise-and-oneiric.html](http://www.tuxgarage.com/2012/05/install-gimp-2-8-in-precise-and-oneiric.html)

It didn't appear to work because when I launched GIMP, it was still version 2.6.

I then followed the instructions from the above web site to purge the PPA
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:otto-kesselgulasch/gimp
```
Now, things are really messed up.  I am receiving the following and can't seem to fix it.
> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list'

Help please.

---

### Post by raja.genupula on 2012-05-26
give us output of 

```
cat /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
```

---

### Post by bug67 on 2012-05-26
> **raja.genupula said:**
> give us output of 

```
cat /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
```

The output of which is:

```
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
ain
```

---

### Post by raja.genupula on 2012-05-26
yeah we have the mistake at bold  text . 

```
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
**ain**
```. so now do as 

```
sudo gedit /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
``` and remove the text of bold and save it & close . now do 

```
sudo apt-get update
``` again

---

### Post by bug67 on 2012-05-26
I fixed it.

Went to the folder: 

*/etc/apt/sources.list.d*

Opened as root and deleted the offending repository files from there.  All is well.  :)

Looks like I might've gotten a little wonky on my copy/paste.

---

