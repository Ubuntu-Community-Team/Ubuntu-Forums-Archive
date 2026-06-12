---
title: "where is linux source code?"
date: 2011-07-26
forum: Programming Talk
---

### Post by chuchi on 2011-07-26
Hi friends!!! I'm sure this is a stupid question. I'm learning about sockets in Linux, and I was wondering where to find, for example, the code of the "socket" or "bind" function in the linux source code. I searched in "/usr/include/" this is the right place, isn't it? If it isn't, where is it?

Thank you very much!

---

### Post by sanderj on 2011-07-26
Start Ubuntu Software Center, in the upper right search box, type 'linux-source'. Then click to install.


Online browsing of the source: [http://lxr.linux.no/](http://lxr.linux.no/) 

And you know [http://www.kernel.org/](http://www.kernel.org/), don't you?

---

### Post by nvteighen on 2011-07-26
A GNU/Linux distro is composed of lots of different programs whose source code is independent and, in the case of Ubuntu, you can get it from APT:

```

apt-get source PACKAGE

```

Where PACKAGE is the package name in the repos. (Make sure to create a directory first and cd into it, as apt-get will download everything into your current directory).

What you're referring to is not part of the Linux kernel, but the POSIX library... well, in the case of sockets, these can also be considered as being part of the BSD API... Anyway, you won't find the implementation in the kernel source, but in the GNU C Standard Library source; be aware that that thing is huge.

To get the source:
```

apt-get source libc6

```

EDIT: FYI, /usr/include is where C and C++ headers are located. Header files don't include code, but just function definitions... (well, unless we're talking of a C++ template library; those do include implementation code). Header files are used to make the compiler aware that some function is defined, no matter whether in the compilation unit or outside... The linker will actually search for the function definition either inside your program or in the libraries you've told it to look at.

---

