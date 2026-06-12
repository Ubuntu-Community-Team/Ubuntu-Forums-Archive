---
title: "compilation problem"
date: 2007-06-06
forum: Programming Talk
---

### Post by sulekha on 2007-06-06
Hi all,

        I am not even able to compile a simple program such as this:

  #include<stdio.h>
  int main(void)
 {   printf("Hello world");   return(0); }

 i compiled as follows gcc -o check check.c

 but the o/p is as follows

check.c:2:19: error: stdio.h: No such file or directory
check.c: In function ‘main’:
check.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

then i removed the line   #include<stdio.h>
and  compiled again as gcc -o check check.c to get the following result

check.c: In function ‘main’:
check.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Can anybody suggest a way to fix this problem??

 i tried the following command gcc -v and is giving the o/p as (I am using dapper 6.06.1)

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

---

### Post by WW on 2007-06-06
Install the package **build-essential**:
```

$ sudo apt-get install build-essential

```
and try again.

Installing just gcc doesn't install all the libraries and header files.

---

### Post by sulekha on 2007-06-06
I have done what you  said, now there is no compilation problem.Thanks for the help.
  BTW  where can i find information as on how to install rhide IDE for gcc .

---

