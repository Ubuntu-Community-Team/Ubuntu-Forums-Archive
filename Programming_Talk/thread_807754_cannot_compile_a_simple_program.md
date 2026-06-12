---
title: "cannot compile a simple program"
date: 2008-05-26
forum: Programming Talk
---

### Post by namtien on 2008-05-26
Hi all,
i am new in ubuntu and i cannot compile the simple program below:
 
//Using libtiff
#include <stdio.h> 
#include <tiffio.h> 
int main (int argc, char** argv) 
{
  TIFF* tiff; 
  tiff = TIFFOpen (argv[1], "r"); 
  TIFFClose (tiff); 
  return 0; 
} 

the error say that it doen't understand TIFF. 
I ran command 'locate libtiff*' then it return libtiff.so.4
but when i ran command 'locate tiffio.h' it returns nothing

Would anyone help me?

thanks

---

### Post by gborzi on 2008-05-26
Perhaps you need to install the libtiff4-dev package, i.e. *sudo apt-get install libtiff4-dev*. To compile and link use > cc -o ex ex.c -ltiff

---

### Post by namtien on 2008-05-26
thanks a lot gborzi!!! it works fine now :-)

---

### Post by bleriot13 on 2009-07-16
Well, it doesn't work for me.

I already have libtiff4-dev installed, so I get no COMPILER errors, but, on the contrary, the loader refuses to find libtiff.

Here's the output I get from gcc:

> 
gcc: -ltiff: No existe el fichero o directorio
which, translated to english, means "File or directory not found".

I have libtiff.a and libtiff.so.4 in /usr/lib. The include (header) files are also in place (otherwise, the code wouldn't compile).

Any idea about what can be wrong?

Thanks.

P.S.: I forgot to mention that I'm using Ubuntu 9.04.

---

