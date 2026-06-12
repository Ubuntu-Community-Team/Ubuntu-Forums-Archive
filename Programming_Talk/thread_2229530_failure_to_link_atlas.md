---
title: "failure to link atlas"
date: 2014-06-13
forum: Programming Talk
---

### Post by vimsical on 2014-06-13
I have these packages install:
```
$ apt-policy libatlas-{base-,}dev
libatlas-base-dev:
  Installed: 3.8.4-3build1
  Candidate: 3.8.4-3build1
  Version table:
 *** 3.8.4-3build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status
libatlas-dev:
  Installed: 3.8.4-3build1
  Candidate: 3.8.4-3build1
  Version table:
 *** 3.8.4-3build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
        100 /var/lib/dpkg/status

```

and I am trying to compile this test program:
```
#include <atlas/clapack.h>


int main() {
        int n = 2, m=3;
        double a_v[] = {1, 4, 2, 3};
        double b_v[] = {1, 2, 3, 4, 5, 6};
        int status = clapack_dposv(CblasRowMajor, CblasUpper, n, m, a_v, n, b_v, n);
}

```

But I got a linker error:
```
gcc proto/atlas_test.c -o atlas_test -L/usr/lib/atlas-base/ -latlas -lcblas
/tmp/ccoG7mea.o: In function `main':
atlas_test.c:(.text+0xd3): undefined reference to `clapack_dposv'
collect2: ld returned 1 exit status

```

I tried to use nm to see where the symbol clapack_dposv in various library files in /usr/lib/atlas-base/, but they all seem to have no exported symbol. Any help and suggestion are appreciated.

---

### Post by steeldriver on 2014-06-13
I admit to finding the whole atlas/blas/lapack thing confusing - however I *think* it's correct to say that atlas just provides alternative versions of the regular blas and lapack libraries i.e.

```

$ update-alternatives --get-selections | grep 'blas\|lapack'
libblas.so                     auto     /usr/lib/atlas-base/atlas/libblas.so
libblas.so.3                   auto     /usr/lib/atlas-base/atlas/libblas.so.3
liblapack.so                   auto     /usr/lib/atlas-base/atlas/liblapack.so
liblapack.so.3                 auto     /usr/lib/atlas-base/atlas/liblapack.so.3

```

In other words, all that should be necessary is to verify that your update-alternatives are set correctly - if not, you can use

```

sudo update-alternatives --config libblas.so

sudo update-alternatives --config liblapack.so

```

and then
```

gcc -o atlas_test atlas_test.c -lblas -llapack

```

---

### Post by vimsical on 2014-06-16
Thanks you!

---

