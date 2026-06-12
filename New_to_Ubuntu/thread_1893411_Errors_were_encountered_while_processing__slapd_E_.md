---
title: "Errors were encountered while processing:  slapd E: Sub-process /usr/bin/dpkg returne"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Qutaibah on 2011-12-10
hi I got this error after remove openssl by
sudo apt-get remove openssl

and now when I am trying to upgrade or install anything give me this error 

Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)



any help please 
note: after installing openssl again same error appear :S

---

### Post by Qutaibah on 2011-12-10
and after removing openssl 
many things removed with it as example google chrome browser 

I am using ubuntu server 11.10 64 bit

---

### Post by Qutaibah on 2011-12-10
thanks alot and sorry for wast your time for reading I solved the problem by



sudo apt-get remove --purge slapd


Then, reinstall:

apt-get install -y slapd


it works well ;):D

---

