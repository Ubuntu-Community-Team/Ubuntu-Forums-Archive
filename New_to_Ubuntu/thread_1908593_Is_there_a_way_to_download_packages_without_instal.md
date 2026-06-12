---
title: "Is there a way to download packages without installing them?"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-01-13
If I open a terminal and type:  sudo apt-get install *package*
Is there a way to simply download the package and *not* install it?

---

### Post by MG&amp;TL on 2012-01-13
```
sudo apt-get install -d <package>
cp /var/cache/apt/archives/<package><version> /where/I/want/it/
```

Should do the trick.

There's also the ubuntu, debian, and mint package websites, and

```
apt-get source <package>
```

for tarballs which you can *debuild*.

Also bzr branch from launchpad, in some cases.

---

### Post by Basher101 on 2012-01-13
> **Learning Linux 2011 said:**
> If I open a terminal and type:  sudo apt-get install *package*
Is there a way to simply download the package and *not* install it?

1. i do not know

2. try to search on the web for *package*.deb files

3. i would also like to hear how you can > simply download the package and not install it with the terminal


regards

edit: thx MG&TL

---

### Post by Rainbow_Dash on 2012-01-13
deb packages.

You might be able to do a wget straight from Canonical's repositories as well. Not sure about that though.

---

### Post by cortman on 2012-01-13
You can generate download scripts using Synaptic and run the scripts to simply download packages.

And, like MG&TL said, you can use apt-get install with the -d flag to do it from the command line, but it won't also figure out or download dependent packages, like a Synaptic script will.

---

### Post by oldos2er on 2012-01-13
```
man apt-get
``` will show you most everything it's possible to do with apt-get.

---

