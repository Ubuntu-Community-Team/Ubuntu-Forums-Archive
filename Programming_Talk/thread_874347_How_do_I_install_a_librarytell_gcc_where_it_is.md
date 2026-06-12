---
title: "How do I install a library/tell gcc where it is?"
date: 2008-07-29
forum: Programming Talk
---

### Post by Yes on 2008-07-29
I downloaded a library I need for a program I'm working on, but I'm not sure how I make gcc know where it is.  I know you add '-l[libname]' to the arguments, but if it's not "installed", what do I do?  Do I need to install it?  If I do, would that be distro specific, because I'm not using Ubuntu.

Thanks!

---

### Post by LaRoza on 2008-07-29
> **Yes said:**
> I downloaded a library I need for a program I'm working on, but I'm not sure how I make gcc know where it is.  I know you add '-l[libname]' to the arguments, but if it's not "installed", what do I do?  Do I need to install it?  If I do, would that be distro specific, because I'm not using Ubuntu.

Thanks!

First tell what library it is (and in what state. A tarball? An RPM? etc) and what distro you are using.

---

### Post by Yes on 2008-07-29
It's libmpdclient, I've got the tarball, and I'm using Arch.

---

### Post by dwhitney67 on 2008-07-29
```
$ gcc MyProg.c -L<pathToLibrary> -l<libname> -o MyExec
```
The <pathToLibrary> is the full path where the library file exists.  If the file is in /usr/lib or /lib, then you do not have to specify the -L option.  The last sentence is not meant to imply that you should place your library file in those restricted areas, but merely to enlighten you to where gcc normally looks to find system libraries.

The <libname> is the short-hand version of the library name.  So if you want to link in libsomething.so, then you would specify "-lsomething".  Note that the leading "lib" and the trailing ".so" (or ".a") are not required.

---

### Post by Yes on 2008-07-30
I don't have anything called ".so" or ".a", just libmpdclient.c and libmpdclient.h.  Is that a problem?  I tried putting them in the same directory as the source file and running ' gcc client.c -L./ -llibmpdclient -o client', but I got the error '/usr/bin/ld: cannot find -llibmpdclient'.

---

### Post by LaRoza on 2008-07-30
> **Yes said:**
> I don't have anything called ".so" or ".a", just libmpdclient.c and libmpdclient.h.  Is that a problem?  I tried putting them in the same directory as the source file and running ' gcc client.c -L./ -llibmpdclient -o client', but I got the error '/usr/bin/ld: cannot find -llibmpdclient'.

In that case, you can either create a library, or just compile it yourself.

Say your program is in a file called "Main.c":

```

gcc Main.c libmpdclient.c -o <program-name>

```

Include the header in Main.c.

---

### Post by nvteighen on 2008-07-30
If interested on how to build libraries (static or shared), look here: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

### Post by Yes on 2008-07-30
Great, thanks.

---

