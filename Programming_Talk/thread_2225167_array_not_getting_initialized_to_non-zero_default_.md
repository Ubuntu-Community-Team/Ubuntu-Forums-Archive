---
title: "array not getting initialized to non-zero default value"
date: 2014-05-20
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-20
Hello,
 I used int S[10] = {1}; to initialize all the 10 elements of the array to 1, but doesn't seem to work. The log below carries all the information.

```

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat weird.c #include <stdio.h>
int S[10] = {1};
int main(void)
{
 int i = 0;
 for(i=0;i<10;i++)
  printf("S[%d] == [%d]\n",i,S[i]);

 return 0;
}

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ gcc weird.c 
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ ./a.out 
S[0] == [1]
S[1] == [0]
S[2] == [0]
S[3] == [0]
S[4] == [0]
S[5] == [0]
S[6] == [0]
S[7] == [0]
S[8] == [0]
S[9] == [0]

```

My version of gcc is as follows
```
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ gcc -vUsing built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 

```

PS : I'm going to be kicking myself if this is one of those silly questions. But I'm just so nonplussed at the moment that I'm not able to figure out what could be silly here :)

---

### Post by ofnuts on 2014-05-20
This is normal... the default initialization value is 0.

If you do:
```
int S[10] = {0};
```
You get all zeroes because the first element is initialized to the value you asked (0) and the rest to the default value (0). So when you do:
```
int S[10] = {1};
```
the first element is initialized to the value you asked (1) and the rest to the default value (0).

---

### Post by IAMTubby on 2014-05-20
> **ofnuts said:**
> This is normal... the default initialization value is 0.
Thanks ofnuts, but how then do I initialize all the integer elements to 1 ? Do I have to do the following ?

```
for(i=0;i<10;i++)a[i]=1;
```

Isn't there a way other than running it in a loop?

---

### Post by spjackson on 2014-05-20
> **IAMTubby said:**
> Isn't there a way other than running it in a loop?
```

int S[10] = {1,1,1,1,1,1,1,1,1,1};

```

---

### Post by IAMTubby on 2014-05-20
> **spjackson said:**
> ```

int S[10] = {1,1,1,1,1,1,1,1,1,1};

```
Thanks spjackson. 
But still think it would've been better had int S[10] = {1}; initialized all elements to 1. Any reason why C doesn't work so ? It's just so simple to remember that way.

---

### Post by IAMTubby on 2014-05-20
By the way, I found one more syntax which goes like,
```
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat initialize.c 
#include <stdio.h>


int main(void)
{
 int array[100] = { [0 ... 99] = -1 };


 return 0;
}

```
But, hmm :( 
 

:)

---

### Post by spjackson on 2014-05-20
> **IAMTubby said:**
> 
```

 int array[100] = { [0 ... 99] = -1 };

```

This is a GNU extension; it is not standard C. If you are not interested in porting to other standard conforming C compilers, then yes you can do that.

---

### Post by ofnuts on 2014-05-20
> **IAMTubby said:**
> 
But still think it would've been better had int S[10] = {1}; initialized all elements to 1. Any reason why C doesn't work so ? It's just so simple to remember that way.

Because the real syntax allows you to initialize the first values of the array:
```

int array[10]={1,2,3,4}
// Initializes array to {1,2,3,4,0,0,0,0,0,0}

```

Your suggestion would make "{1}" ambiguous...

---

### Post by IAMTubby on 2014-05-21
> **spjackson said:**
> This is a GNU extension; it is not standard C. If you are not interested in porting to other standard conforming C compilers, then yes you can do that.
Ok, thanks spjackson

---

### Post by IAMTubby on 2014-05-21
> **ofnuts said:**
> Because the real syntax allows you to initialize the first values of the array:
```

int array[10]={1,2,3,4}
// Initializes array to {1,2,3,4,0,0,0,0,0,0}

```

Your suggestion would make "{1}" ambiguous...
Ohhh, thanks ofnuts
That makes perfect sense and I understand why only the first element of the array gets initialized.

---

