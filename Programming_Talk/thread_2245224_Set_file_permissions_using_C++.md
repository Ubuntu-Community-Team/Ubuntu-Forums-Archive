---
title: "Set file permissions using C++"
date: 2014-09-22
forum: Programming Talk
---

### Post by EngieOP on 2014-09-22
Using C, if I wanted to create a file with read/write permissions for the owner I would do this:

```

int fd;
fd = open("filename", O_CREAT, S_IRUSR | S_IWUSR);

```


What is the equivalent with C++? 

```

ofstream os;
os.open("filename", ?);

```

---

### Post by spjackson on 2014-09-23
Standard C++ does not provide a means of specifying file permissions, therefore any method will be implementation dependent. If you are using g++, libstdc++ on *nix, then you can use open() and construct your stream from the resultant file descriptor. See [https://gcc.gnu.org/onlinedocs/libstdc++/manual/ext_io.html](https://gcc.gnu.org/onlinedocs/libstdc++/manual/ext_io.html)

Alternatively, you can create the file with open(), close it and reopen with ofstream. Possibly [Boost filesystem]("http://www.boost.org/doc/libs/1_56_0/libs/filesystem/doc/index.htm") has something.

---

