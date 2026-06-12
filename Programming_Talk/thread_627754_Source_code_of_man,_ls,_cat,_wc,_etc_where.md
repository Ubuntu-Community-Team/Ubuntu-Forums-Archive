---
title: "Source code of man, ls, cat, wc, etc where?"
date: 2007-11-30
forum: Programming Talk
---

### Post by TSP on 2007-11-30
H! i am learning C i it would be great if i can find the source code of all the common UNIX commands like cat, ls, pssswd, whereis, etc,etc Anyone knows where i can find this?
Thanks in advance!

---

### Post by geirha on 2007-11-30
```
$ dpkg -S `which cat`
[COLOR="Blue"]coreutils[/COLOR]: /bin/cat
$ apt-get source [COLOR="Blue"]coreutils[/COLOR]

```

---

### Post by Jessehk on 2007-11-30
A good exercise would be actually writing your own versions of cat, wc, etc. :)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-28
> **geirha said:**
> ```
$ dpkg -S `which cat`
[COLOR="Blue"]coreutils[/COLOR]: /bin/cat
$ apt-get source [COLOR="Blue"]coreutils[/COLOR]

```

Then how do i view it.
were doses this put the source code

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-28
i figured it out

---

### Post by curtlee2002 on 2009-10-25
You posted "i figured it out".  Please post what you figured out.  Answers like "i figured it out" doesn't help others when they read the thread.

"apt-get sources (package)"  downloads the source of the package to the current working directory.

You should get something like below.

```
george@georgenotebook:~/temp$ sudo apt-get source coreutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 9,729kB of source archives.
Get:1 http://mirror.anl.gov karmic/main coreutils 7.4-2ubuntu1 (dsc) [1,244B]
Get:2 http://mirror.anl.gov karmic/main coreutils 7.4-2ubuntu1 (tar) [9,709kB]
Get:3 http://mirror.anl.gov karmic/main coreutils 7.4-2ubuntu1 (diff) [19.2kB]
Fetched 9,729kB in 1s (5,825kB/s)    
gpgv: Signature made Tue 06 Oct 2009 05:24:17 AM CDT using DSA key ID 5E0577F2
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./coreutils_7.4-2ubuntu1.dsc
dpkg-source: info: extracting coreutils in coreutils-7.4
dpkg-source: info: unpacking coreutils_7.4.orig.tar.gz
dpkg-source: info: applying coreutils_7.4-2ubuntu1.diff.gz

george@georgenotebook:~/temp$ ls
coreutils-7.4                   coreutils_7.4-2ubuntu1.dsc
coreutils_7.4-2ubuntu1.diff.gz  coreutils_7.4.orig.tar.gz

```

---

### Post by cariboo on 2009-10-25
If you look at the date on the thread, you will see it is from Feb 2008. The people that participated in the thread may be long gone, or the information may be out of date. You would probably be better off creating a new thread.

This thread is closed.

---

