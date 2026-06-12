---
title: "ubuntu10.10 install gcc/g++ 4.1.2"
date: 2010-10-12
forum: Programming Talk
---

### Post by melon1234 on 2010-10-12
[Solved] Simply download gcc sourcecode and make/install to a individual directory.


I'm running ubuntu10.10 x86 version. It has gcc/g++4.4. But my team use gcc/g++4.1.2 for development. How can I install them?

I tried 
    apt-get install gcc-4.1
It's ok. However there is *no* 
    apt-get install g++-4.1
Where can I get the package? Do I need to add some new update sources? How about headers and *.a libs?

Thank you in advance.

--
ShenLei

---

### Post by herrlorenzen on 2010-10-13
Hi.

where did you get the source from and how did you install it?

I tried downloading g++4.1 from the gcc.gnu page, but i have no idea how to install it.

---

### Post by melon1234 on 2010-10-13
you can follow the GNU gcc installation guide:
[http://gcc.gnu.org/install/](http://gcc.gnu.org/install/)

Simply 
/objdir/configure --xxxxx
make
make install

create some soft-links for your compiler in /usr/bin.

--
ShenLei

---

### Post by Queue29 on 2010-10-13
> **melon1234 said:**
> 
Simply 
/objdir/configure --xxxxx


Yea, figuring out how to correctly set those configure options isn't "Simply".

---

### Post by melon1234 on 2010-10-15
> **Queue29 said:**
> Yea, figuring out how to correctly set those configure options isn't "Simply".

Indeed. FYI, my setting is:
configure --prefix=/xxx/gcc-4.1.2 --disable-multilib --with-local-prefix=/xxx/gcc-4.1.2 --enable-shared --enable-threads=posix --disable-checking --enable--long-long --with-system-zlib --enable-languages=c,c++

--
ShenLei

---

### Post by skywalk423 on 2010-10-18
I'm in the same boat as the OP. I have a large build that requires g++ 4.1 and not super comfortable building and installing it manually. Is there not a more "Ubuntu-y" way to do this? Maybe a software source I can add in SPM?

---

