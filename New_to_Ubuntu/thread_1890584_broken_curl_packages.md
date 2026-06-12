---
title: "broken curl packages"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by AzharCh on 2011-12-03
Hi,

I am trying to install curl on ubuntu 11.10 using
sudo apt-get install  libcurl4-gnutls-dev libcurl4-openssl-dev

and I get following error(s)....


Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcurl4-gnutls-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcurl4-gnutls-dev : Conflicts: libcurl-dev
 libcurl4-openssl-dev : Conflicts: libcurl-dev
E: Unable to correct problems, you have held broken packages.


how to get my packages repaired?????


Rgds

---

### Post by Frogs Hair on 2011-12-03
I see that curl is in the software center , is there a reason you selected that method to install it . ? Here are some commands that may help with broken packages . Pay attention to the terminal output as there may be suggestions .```
sudo apt-get autoremove
``` ```
sudo apt-get -f install 
``````
sudo dpkg --configure -a 
```

---

### Post by Fush1986 on 2011-12-03
I am having the exact same issue.

---

### Post by souviking on 2011-12-20
Sorry , but you cant ( dont need to ) install both . They are both basically the same thing with SSl support provided in libcurl4-gnutls-dev by GnuTLS and OpenSSl in libcurl4-openssl-dev .

---

