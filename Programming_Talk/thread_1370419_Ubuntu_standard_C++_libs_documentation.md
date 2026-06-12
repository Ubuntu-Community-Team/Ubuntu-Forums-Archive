---
title: "Ubuntu standard C++ libs documentation?"
date: 2010-01-02
forum: Programming Talk
---

### Post by kahumba on 2010-01-02
Hi,
I know how to install the C++ Gtk+ docs (libgtkmm-2.4-doc) and browse them at
/usr/share/doc/libgtkmm-2.4-doc/reference/html/classes.html

is there such a package for Ubuntu for the **standard C++ classes (libs)** like <iostream> etc?

---

### Post by dwhitney67 on 2010-01-02
Here:  [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

### Post by kahumba on 2010-01-02
I know but my internet connection is so shaky that I really need an offline version of the docs, preferably a good one, I thought it's possible just like with the gtkmm package mentioned above.

---

### Post by dwhitney67 on 2010-01-02
I do not know of any; you could always download this tutorial in its PDF format.

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by kahumba on 2010-01-02
Thanks, I guess I'll use that one.
I found libstdc++6-4.4-doc which can be browsed at
/usr/share/doc/gcc-4.4-base/libstdc++/html/index.html
but it seems to "raw" for me.

---

### Post by Sockerdrickan on 2010-01-02
> **kahumba said:**
> I know but my internet connection is so shaky that I really need an offline version of the docs, preferably a good one, I thought it's possible just like with the gtkmm package mentioned above.
[http://www.cppreference.com/wiki/](http://www.cppreference.com/wiki/)

&&

[http://www.cppreference.com/cppreference-files.tar.gz](http://www.cppreference.com/cppreference-files.tar.gz)

you are welcome

---

### Post by alexkaz on 2010-01-02
I am having similiar problems trying to run gcc and g++ on  a recent install of gcc 4.2.2.
When running the good 'ol hello.c, many errors are returned. 
gcc : hello: no such file or directy
hello.c:1:22: error isotream.h: No such file or directory
hello.c: in function 'main':
hello.c:4 error: 'cout'undeclared (first use in this function)
hello.c:4:error: (Each undeclared identifirer is reported only once
hello.c:4:error: for each function it appears in.)

in what directory file should the c and cpp library headers be located?

Thanks

---

### Post by not_a_phd on 2010-01-02
Alex,

If you have installed the g++ package, you should have no issues with locating header files. I would offer the following for your hello-world woes:

1. You need to include the <iostream> library. Not the <isostream> library to do stuff with cout and the like.

2. You should probably name the file hello.cpp or hello.cxx to let gcc know that it is a C++ file, not a standard c file.

3. You should probably compile with g++ instead of gcc.

Regards.

---

### Post by alexkaz on 2010-01-03
Thanks for your follow up. 
1. the isostream was a typo when composing the forum question. it is entered as iostream in the hello.cpp file. 
2. Yes, it was named as hello.c for gcc run and hello.cpp for g++ run
3. it is accurate to assume all c files must compile with gcc and all cpp must compile with g++. Will g++ recognize  filename.c code?

---

### Post by alexkaz on 2010-01-03
no. 3: should be IS it ???

---

### Post by KIAaze on 2010-01-03
> **alexkaz said:**
> 
3. is it accurate to assume all c files must compile with gcc and all cpp must compile with g++. Will g++ recognize  filename.c code?

So, we meet again... 8)

Yes, g++ should recognize filename.c code.
Actually, the contents of the files is more important than the filename (but it is a good habit to use the .c extension for C code and .cpp for C++ code).
gcc can only compile C code (ex: printf), while g++ can compile C and C++ (ex: cout).

P.S.: You can use the "edit" button in the bottom-right of your post to correct typos. ;)

---

