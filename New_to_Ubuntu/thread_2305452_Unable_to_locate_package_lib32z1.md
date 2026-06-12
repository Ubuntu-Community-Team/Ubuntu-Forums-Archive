---
title: "Unable to locate package lib32z1"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by csar7 on 2015-12-06
Enviroment: Ubuntu  15.10 32bit
First of all I would like to thank your help. I have to execute: cap_gen_auto   to generate a .upg file. I've been told to use zlib libraries by installing:sudo apt-get install lib32z1 but I always get the followong:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lib32z1
Could anyone help me?
Thanks a lot. Regards.

---

### Post by matt_symes on 2015-12-06
Hi

Firstly, welcome to the forums :)

> **csar7 said:**
> Enviroment: Ubuntu  15.10 32bit

Any reason you are using 32 bit ? Hardware limitations ?

> First of all I would like to thank your help. I have to execute: cap_gen_auto   to generate a .upg file. I've been told to use zlib libraries by installing:sudo apt-get install lib32z1 but I always get the followong:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lib32z1
Could anyone help me?
Thanks a lot. Regards.

I can only find the package lib32z1 for 64 bit from the repositories.

[http://packages.ubuntu.com/wily/lib32z1](http://packages.ubuntu.com/wily/lib32z1)

I'm not sure it's available for 32 bit.

Can you upgrade to 64 bit ? You could also build the library yourself.

Kind regards

---

### Post by csar7 on 2015-12-06
I will try it with 64bit and post the results. Thanks a lot, kind regards.

---

### Post by csar7 on 2015-12-12
):PIt finally worked with Ubuntu 64bit. Thanks a lot.  SOLVED

---

### Post by oldos2er on 2015-12-12
Please mark the thread 'Solved' under the Thread Tools menu at the top of the page. Thanks!

---

