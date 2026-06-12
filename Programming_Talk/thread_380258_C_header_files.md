---
title: "C header files"
date: 2007-03-09
forum: Programming Talk
---

### Post by webdreamer on 2007-03-09
Ok, the deal is I've installed Ubuntu last week and I should be using the gcc compiler to compile the code written in VIM, but I found out I hadn't installed any header files, including stdio.h, and so it didn't work... The problem is I've installed Ubuntu in an old laptop of mine and I can't connect it to the Internet - ok, I could do it, but it would be so slow I rather not do it. So I want to know how I can get header files to be recognized by the gcc compiler in my old laptop. I really need to do this as soon as possible.

Thanks in advance.

---

### Post by invalid on 2007-03-09
Well the proper way to go about it would be installing build-essentials, which includes among other things, the header files. If you don't want to go the internet route, I would suggest grabbing a .deb of libc6-dev which includes the necessary header files. Put this on a flash dive and transfer it over.

---

### Post by Wybiral on 2007-03-09
So they aren't in your "/usr/include" folder?

But gcc and g++ are installed and you have the actual libraries (the binary files)?

---

### Post by lnostdal on 2007-03-09
lib6-dev would probably do the trick .. to confirm you can take a look at the dependencies of build-essential:

```

aptitude show build-essential
...
Depends: libc6-dev | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)

```

..that's what build-essential downloads and install for basic c-stuff to work .. 

i'd also download manpages-dev and glibc-doc so you can use `man' to look up documentation for stuff ..

---

### Post by hod139 on 2007-03-09
The package build-essential (and its dependencies) are available on the CD.  You can either add the cd as a source in your sources.list, or I believe if you put the cd into the computer a GUI pops up asking if you want to install something.

---

