---
title: "question about build essential package"
date: 2008-03-01
forum: Programming Talk
---

### Post by thungmail on 2008-03-01
hi
I am new to Ubuntu and I have some questions about compile C
I went to System > Administration > Synaptic Package Manager,click search "gcc" and I instaledl gcc compiler from the list. Then i tried to compile C codes again. It showed the message
hello.c: In function ‘main’:
hello.c:3: warning: implicit declaration of function ‘printf’
hello.c:3: warning: incompatible implicit declaration of built-in function ‘printf’
After that, I installed gcc again by using "sudo apt-get install build-essential".
I tried again but it did not work either until i install "build essential" package.
As i know gcc compiler is in build essential. However, I do have gcc compiler in my computer already. I dont get it. Can some one help me out.
Thanks

---

### Post by LaRoza on 2008-03-01
Install build-essential to compile C and C++ programs. There is more to it than gcc.

---

### Post by thungmail on 2008-03-01
Thanks! it is clearer now for me.
After install build essential package. Where is directory for it
Tuan

---

### Post by LaRoza on 2008-03-01
> **thungmail said:**
> Thanks! it is clearer now for me.
After install build essential package. Where is directory for it
Tuan

build-essential is a meta package, it is many packages under one name.

GCC is in /usr/bin/gcc, but the headers and other packages are elsewhere.

---

