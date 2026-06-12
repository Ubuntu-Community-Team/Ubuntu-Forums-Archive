---
title: "installing the man page"
date: 2005-11-30
forum: Packaging and Compiling Programs
---

### Post by jobherzt on 2005-11-30
hello, 
sorry my question is really a newbie's question, but I'm making my first source package, and the original upstream don't wrote a man page. so I did it, but I don't know where i must specify how to install it. an other problem is, that I saw that manapages are gziped. so, myquestions are :

- where do I configure the installation of the manapages ( makefile ? rules ? .. )
- does I gzip it myself ( ie add a gzip command in the makefile ? ), or is it automatically done during the install ?

thanks !!

---

### Post by manavendra on 2010-05-08
```
sudo apt-get install manpages manpages-dev freebsd-manpages funny-manpages gmt-manpages man2html manpages-posix manpages-posix-dev asr-manpages
```

---

### Post by rosenkavalier on 2011-08-09
I don't know what's the exact way, IIRC it involves copying the man files into /usr/share/man directory. for Archlinux, the compression is done automatically by the package-creator, so it seems that the compression is done by distro's package management system.

> **manavendra said:**
> ```
sudo apt-get install manpages manpages-dev freebsd-manpages funny-manpages gmt-manpages man2html manpages-posix manpages-posix-dev asr-manpages
```

I know we don't like 'newbie excuse' in a question, but please refrain from such attitude when replying to a post. your reply doesn't even help here.

---

### Post by Bachstelze on 2011-08-09
If you are building a DEbian package, you can use debhelper to install the man page

```
man dh_installman
```

---

