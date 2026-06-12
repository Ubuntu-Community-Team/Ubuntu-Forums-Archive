---
title: "using ldconfig to include link lib .so"
date: 2011-09-14
forum: Packaging and Compiling Programs
---

### Post by fausten on 2011-09-14
I added /usr/local/libpqxx/lib into /etc/ld.so.conf and executed ldconfig. 

When I linked my program using option of -lpqxx, I still cannot find libpqxx.so. I had to specify -L/usr/local/libpqxx/lib to link the so.

I am using ubuntu server 11.04 now. Is the ldconfig only used for runtime dynamic loading ?

Anyone can help ?

Thanks a lot,

fausten

---

### Post by fausten on 2011-09-15
> **fausten said:**
> I added /usr/local/libpqxx/lib into /etc/ld.so.conf and executed ldconfig. 

When I linked my program using option of -lpqxx, I still cannot find libpqxx.so. I had to specify -L/usr/local/libpqxx/lib to link the so.

I am using ubuntu server 11.04 now. Is the ldconfig only used for runtime dynamic loading ?

Anyone can help ?

Thanks a lot,

fausten

It is a bug of 11.04. After upgrading to 11.10, ldconfig works.

great!

---

