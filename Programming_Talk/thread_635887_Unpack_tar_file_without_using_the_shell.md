---
title: "Unpack tar file without using the shell"
date: 2007-12-09
forum: Programming Talk
---

### Post by robjford on 2007-12-09
Anyone know of a library I can use with C/C++ to open a tar archive and access the files within.

I could always call system() to do the work for me, but if there's a more elegant solution, I'd like to know.

Thanks in advance.

---

### Post by geirha on 2007-12-09
There's libtar. Install the libtar-dev package and read the man pages. You'll find a list of the man-pages with ```
dpkg -L libtar-dev
```

---

### Post by zyghom on 2007-12-09
perl ?

[http://search.cpan.org/~kane/Archive-Tar-1.36/lib/Archive/Tar.pm]("http://search.cpan.org/~kane/Archive-Tar-1.36/lib/Archive/Tar.pm")

DESCRIPTION 

Archive::Tar provides an object oriented mechanism for handling tar files. It provides class methods for quick and easy files handling while also allowing for the creation of tar file objects for custom manipulation. If you have the IO::Zlib module installed, Archive::Tar will also support compressed or gzipped tar files.

---

### Post by robjford on 2007-12-09
Many thanks, libtar looks to do the job

---

