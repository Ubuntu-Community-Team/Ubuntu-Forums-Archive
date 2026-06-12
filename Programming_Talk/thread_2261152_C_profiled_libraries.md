---
title: "C profiled libraries"
date: 2015-01-16
forum: Programming Talk
---

### Post by typedeph on 2015-01-16
Hello Ubuntu Community, I'm currently in the process of learning some C tools -- specificially gprof. I would like to profile some C functions against another function. Under the gprof documentation here: [https://sourceware.org/binutils/docs-2.24/gprof/Compiling.html#Compiling](https://sourceware.org/binutils/docs-2.24/gprof/Compiling.html#Compiling), they state:
> "In addition, you would probably want to specify the profiling C library, libc_p.a, by writing `-lc_p' instead of the usual `-lc'. This is not absolutely necessary, but doing this gives you number-of-calls information for standard library functions such as read and open."
Unfortunately when I look under /usr/lib/x86_64-linux-gnu I only see libc.a and libc.so but no libc_p of any kind. How can I obtain the C profiled library? is there a repo with up to date compiled binaries for this?

---

### Post by ofnuts on 2015-01-16
Install package libc6-prof?

---

### Post by typedeph on 2015-01-16
Thank you, I think that did it. If you don't mind, could you tell me how you found the package? I thought perhaps I didn't do the minimal homework of having apt search | grep profil* but it doesn't come up with the package this way, so I'm really curious to know how you came about finding it.

---

### Post by ofnuts on 2015-01-17
Googled for it ("Linux C profiling libraries", from my Browser history).

---

### Post by schragge on 2015-01-17
I usually use [apt-file]("http://manpages.ubuntu.com/manpages/trusty/en/man1/apt-file.1.html") to find out what uninstalled package contains the file I'm interested in. In this case the command would be
```
apt-file find /libc_p.a
```

---

