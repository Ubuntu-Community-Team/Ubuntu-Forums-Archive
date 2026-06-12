---
title: "Kernel &amp; C Library"
date: 2010-03-23
forum: Programming Talk
---

### Post by riph72 on 2010-03-23
Hello all,

1) Does the choice of C library (i.e. glibc or uclibc) affect the kernel (and it's configuration) at compile-time?  Or can a given compiled kernel be used with either library?

2) How can I tell which C library a given Linux system (I won't necessarily be using an off-the-shelf distribution) is using?

If it's not obvious, my interest is directed towards "embedded" Linux...

Cheers,
Richard.

---

### Post by soltanis on 2010-03-23
I don't think the actual kernel parts of the kernel use the C standard library at all, since it's supposed to be a portable library for interacting with the operating system. So basically it shouldn't matter; there are plenty of Linux systems that use stripped down libc's and run fine.

---

### Post by Compyx on 2010-03-23
The linux kernel does use the system C library, although historically the Linux kernel used it's own version of the C library since GNU's libc missed some functionality. For embedded systems, some projects use other C libraries such as uClibc and dietlibc.

I suspect you could look at /lib/libc.so.* to dermine which C library is used:
```

compyx@aspire7730g:~$ ls -l /lib/libc.so.*
lrwxrwxrwx 1 root root 14 2010-03-23 14:02 /lib/libc.so.6 -> libc-2.11.1.so

```

On systems using uClibc there would be a symlink to uClibc-x.x.x.so or something similar.

---

### Post by MadCow108 on 2010-03-23
you can actually "execute" the library to get version information:
> >/lib/libc.so.somenumber
GNU C Library (EGLIBC) stable release version 2.10.1, by Roland McGrath et al.
...


---

### Post by Compyx on 2010-03-23
> **MadCow108 said:**
> you can actually "execute" the library to get version information:

Nice one! Learned something new today :)

---

### Post by riph72 on 2010-03-24
> **MadCow108 said:**
> you can actually "execute" the library to get version information:
That should be very useful, thanks!

---

### Post by riph72 on 2010-03-24
> **Compyx said:**
> The linux kernel does use the system C library, although historically the Linux kernel used it's own version of the C library since GNU's libc missed some functionality. For embedded systems, some projects use other C libraries such as uClibc and dietlibc.

I suspect you could look at /lib/libc.so.* to dermine which C library is used:
```

compyx@aspire7730g:~$ ls -l /lib/libc.so.*
lrwxrwxrwx 1 root root 14 2010-03-23 14:02 /lib/libc.so.6 -> libc-2.11.1.so

```On systems using uClibc there would be a symlink to uClibc-x.x.x.so or something similar.
Ok, that's great too, thanks.  I now know how to identify the C library in use.

So would switching from e.g. libc <-> uClibc be just a matter of changing the files in /lib, or does the kernel need to be modified/recompiled in some way?

---

### Post by grayrainbow on 2010-03-24
A short kernel overview [http://www.ibm.com/developerworks/linux/library/l-linux-kernel/]("http://www.ibm.com/developerworks/linux/library/l-linux-kernel/")

If some lib does not work properly, you better change the lib, not the kernel. Some libs(as libc) has a lot of wrappers around system calls, so if you change what kernel export, your costume kernel could brake libc, in which case you should change the lib, and so on, and so on.

Edit: Software stack is supposed to be PnP stile, let say similar to Ubuntu, Kubutu differences, and in THEORY just changing one lib shouldn't be problem.

---

### Post by Compyx on 2010-03-24
I wouldn't recommend changing C library implementations. If you were to replace Glibc with uClibc you'd have to recompile all packages that rely on the C library, which basically means just about all packages on the system.

I also wouldn't be surprised if a lot of GNU software (Gtk+/Gnome) relies on Glibc-specific features.

Personally I think that once you've done a 'make install' of a different C library on a GNU libc-based system, the system will crash and most likely won't even boot properly afterwards.


Building a system from scratch using a non-GNU libc would be a different matter altogether, perhaps Linux From Scratch can be built using such a library. I know Gentoo-embedded uses uClibc, perhaps you could take a look at that.

---

### Post by jpkotta on 2010-03-25
> **Compyx said:**
> I wouldn't recommend changing C library implementations. If you were to replace Glibc with uClibc you'd have to recompile all packages that rely on the C library, which basically means just about all packages on the system.

I also wouldn't be surprised if a lot of GNU software (Gtk+/Gnome) relies on Glibc-specific features.

Personally I think that once you've done a 'make install' of a different C library on a GNU libc-based system, the system will crash and most likely won't even boot properly afterwards.


Building a system from scratch using a non-GNU libc would be a different matter altogether, perhaps Linux From Scratch can be built using such a library. I know Gentoo-embedded uses uClibc, perhaps you could take a look at that.

It's a bad idea to replace your C library, but you can install another one along side.  For example, if you run a 64-bit system, you can install a 32-bit toolchain with the packages ia32-libs-dev and gcc-multilib.

```

$ gcc -o hello hello.c && ldd hello && ./hello
	linux-vdso.so.1 =>  (0x00007fff78343000)
	libc.so.6 => /lib/libc.so.6 (0x00007ffa80e5a000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ffa811cc000)
hello, world!
$ gcc -m32 -o hello.32 hello.c && ldd ./hello.32 && ./hello.32
	linux-gate.so.1 =>  (0xf7fa8000)
	libc.so.6 => /lib32/libc.so.6 (0xf7e22000)
	/lib/ld-linux.so.2 (0xf7fa9000)
hello, world!

```

---

