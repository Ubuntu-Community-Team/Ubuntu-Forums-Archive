---
title: "a beginer in linux has problem with Anjuta"
date: 2006-02-08
forum: Programming Talk
---

### Post by sirmoreno on 2006-02-08
i got a msg that i need "glib" and i can't find it
i tryed looking up "libglib" but can't find that too
and i don't realy know what to do with the folders i copyed from the ftp
some help pls

---

### Post by Adrian on 2006-02-08
Try installing the **build-essential** package from Synaptic.

---

### Post by sirmoreno on 2006-02-08
how?

---

### Post by nixclusive on 2006-02-08
try
```
sudo apt-get install build-essential
```

in the terminal window. (Right Click on the desktop and click open terminal.)

---

### Post by sirmoreno on 2006-02-08
I already install sudo apt-get install build-essential
but the anjuta tells me to install new packages:
glib,automake,autoconf,libtool and i have no idea how.

---

### Post by nixclusive on 2006-02-08
simple:
```

sudo apt-get install glib automake autoconf libtool
```

The beauty of apt-get is that it automatically satisfies dependencies. :D

---

### Post by jan on 2006-03-24
Watch out to install also the -dev packages for the libraries - like libglib2.0-dev, libglib1.2-dev etc. I had Anjuta telling about missing glib but it is actually one of these -dev i think. Now my anjuta seems to work fine. Simply use Synaptic to install the packages, its located in System > Administration > Synaptic Package Manager :D.

---

