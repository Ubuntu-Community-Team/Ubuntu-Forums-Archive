---
title: "python 2.6 help"
date: 2008-11-27
forum: Programming Talk
---

### Post by perlsyntax on 2008-11-27
How do i install python 2.6 and how do i put python 2.6 in my /usr/local?


i put python 2.6 on unbuntu 8.10

---

### Post by crazyfuturamanoob on 2008-11-27
sudo apt-get install python?

---

### Post by perlsyntax on 2008-11-27
i am install it form a tar file.

---

### Post by crazyfuturamanoob on 2008-11-27
Try putting the files into /usr/bin/Python-2.6 and running the following in terminal:
```

sudo apt-get update

sudo apt-get install build-essential

cd /usr/bin/Python-2.6

sudo ./configure

```

---

### Post by Majorix on 2008-11-27
> **perlsyntax said:**
> i am install it form a tar file.

Why exactly?

---

### Post by CptPicard on 2008-11-27
> **crazyfuturamanoob said:**
> Try putting the files into /usr/bin/Python-2.6 and running the following in terminal:


Uh, no no... would rather just unpack into one's home directory and then do 

```

./configure --prefix=/usr/local   (or /usr/local/python26)
make
sudo make install

```

But again... messing with tarball installations of Python when you don't know how to do it doesn't sound sensible :)

---

### Post by wmcbrine on 2008-11-27
> **crazyfuturamanoob said:**
> sudo apt-get install python?No... he specifically asked about Python **2.6**, which isn't in the repos yet (and presumably won't be until 9.04).

---

### Post by perlsyntax on 2008-11-30
I had no prob install it on unbuntu 8.10 and now try to install it on the laptop.

---

