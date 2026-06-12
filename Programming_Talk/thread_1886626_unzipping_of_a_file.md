---
title: "unzipping of a file"
date: 2011-11-25
forum: Programming Talk
---

### Post by shamjs on 2011-11-25
Hi All,

1 > im using unzipping option in my project 
but the code is supporting in windows but not in linux ,
you can download unzip.h and unzip.cpp from 
[http://www.gzip.org/zlib/](http://www.gzip.org/zlib/)

plz suggest me what modifications i have to do .................

2 > And i need to know whats the meaning of #ifdef ZIP_STD
 since this condition is not getting trued in my linux g++ compiler.....

waiting for your reply................

---

### Post by An Sanct on 2011-11-25
Please check out [this page]("http://www.wischik.com/lu/programmer/zip_utils.html")

> One final option: if you compile with "**ZIP_STD**" defined for the preprocessor, then zip and unzip will compile using solely stdlib -- with no windows dependencies. They can compile under linux with g++. Note that some of the prototypes in zip.h and unzip.h will change accordingly: filetimes will be time_t structures rather than FILETIME, and various functions will use FILE* rather than HANDLE, and it doesn't support unicode or memory-mapping. The example program "std" does this.

---

