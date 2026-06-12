---
title: "What packages do I need to compile ?"
date: 2009-03-03
forum: Packaging and Compiling Programs
---

### Post by tebbens on 2009-03-03
What packages do I need to compile programs ?

I know I need build-essential, which I installed.

There are a number of automake versions available.
Which automake do I install ?

Do I also install autoconf ?

Thanks!

---

### Post by InfinityCircuit on 2009-03-03
Depends on what you are compiling.

I would get:

```
aptitude install build-essential devscripts automake autoconf m4 autotools-dev subversion cvs git-core bzr bzrtools mercurial darcs xorg-dev
```

---

### Post by tebbens on 2009-03-03
> **InfinityCircuit said:**
> Depends on what you are compiling.

I would get:

```
aptitude install build-essential devscripts automake autoconf m4 autotools-dev subversion cvs git-core bzr bzrtools mercurial darcs xorg-dev
```

Thanks for the info !

I always use Synaptic Package Manager so I can view descriptions..etc.
Synaptic show many versions of automake, which would I pick ?

I've never really used aptitude or apt-get, I'll have to lookup what the
differences are.

---

### Post by nzadLithium on 2009-03-03
Just run that command tebbens gave you from the terminal, it will install all the latest versions in repos of those packages. If your really wanting to install them via synaptic just get the latest versions (unless you know you need a specific older version for some reason?) :p

---

### Post by InfinityCircuit on 2009-03-04
```
eee:/home/dmr# aptitude search --disable-columns -F '%p %V' ~n^automake
automake 1:1.10.1-3
automake1.10 <none>
automake1.4 1:1.4-p6-13
automake1.4-doc <none>
automake1.7 1.7.9-9
automake1.9 1.9.6+nogfdl-3
automake1.9-doc 1.9.6-1
automaken <none>

```

Just install "automake" it is the newest version (automake 1.10).

---

### Post by tebbens on 2009-03-04
> **InfinityCircuit said:**
> Depends on what you are compiling.

I would get:

```
aptitude install build-essential devscripts automake autoconf m4 autotools-dev subversion cvs git-core bzr bzrtools mercurial darcs xorg-dev
```


Found everything in Synaptic, thanks !

---

