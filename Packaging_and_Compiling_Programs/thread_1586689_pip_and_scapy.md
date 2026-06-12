---
title: "pip and scapy"
date: 2010-10-02
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-10-02
How do i download scapy from a urc with python.I been try to find way i can install scapy from a url with pip.:confused:

---

### Post by pythonsyntax on 2010-10-02
anyone?

---

### Post by SevenMachines on 2010-10-03
i'm not sure i totally follow the question so apologies if this isnt what you meant..

scapy is available from the repositories, use that unless you have a special reason for the very latest version
$ sudo apt-get install python-scapy

or, download it and run ./setup.py install in the source directory
[http://www.secdev.org/projects/scapy/](http://www.secdev.org/projects/scapy/)

---

### Post by SevenMachines on 2010-10-03
I'm guessing you meant something more like 
$ pip install Scapy

Unfortunately the current location pip looks for scapy in is down, i know nothing about pip/python so i'm not sure how that could be fixed. i'm guessing the pip index would need to be fixed/updated unless its a temporary outage
[http://pypi.python.org/pypi?%3Aaction=search&term=scapy&submit=search](http://pypi.python.org/pypi?%3Aaction=search&term=scapy&submit=search)

```
/usr/bin/pip run on Sun Oct  3 15:15:38 2010
Downloading/unpacking Scapy
  Getting page http://pypi.python.org/simple/Scapy
  URLs to search for versions for Scapy:
  * http://pypi.python.org/simple/Scapy/
  Getting page http://www.cartel-securite.fr/pbiondi/scapy.html
  Could not fetch URL http://www.cartel-securite.fr/pbiondi/scapy.html (from http://pypi.python.org/simple/Scapy/): HTTP Error 404: Not Found

```

---

### Post by pythonsyntax on 2010-10-23
then how?

---

### Post by pythonsyntax on 2010-10-25
i know i got it installed with the url but can't rem how.

---

### Post by SevenMachines on 2010-10-25
Hi, what i meant i the url at that site is broken, and that seems to be what pip uses ( i'm ignorant of pip though ), so the url at that site would need to be fixed or maybe pip takes a url manually if you can find one. python-scapy is obviously still available in the repositories but how to get pip working is more to do with a working url i think

[EDIT] I'm guessing the last time you tries it the url was still valid

---

### Post by pythonsyntax on 2010-10-25
i did try from scapy web site but can't rem how i did it.

---

### Post by SevenMachines on 2010-10-25
You might want to look at 
[http://www.dirk-loss.de/scapy-doc/installation.html](http://www.dirk-loss.de/scapy-doc/installation.html)

The url,
> $ wget [http://hg.secdev.org/scapy/raw-file/v1.2.0.2/scapy.py](http://hg.secdev.org/scapy/raw-file/v1.2.0.2/scapy.py)
$ sudo python scapy.pycertainly works but i'd use the package myself so you'll need to judge if installing manually from a url is needed for what you want to do or not

---

### Post by SevenMachines on 2010-10-25
Just to note, the whole cartel-securite website used by pip is gone, 
[http://www.cartel-securite.fr](http://www.cartel-securite.fr)

---

### Post by pythonsyntax on 2010-10-25
this pip install [http://www.secdev.org/projects/scapylatest.tar.gz](http://www.secdev.org/projects/scapylatest.tar.gz) that what i mean

---

### Post by SevenMachines on 2010-10-25
bug reference from scapy home
[http://trac.secdev.org/scapy/ticket/369](http://trac.secdev.org/scapy/ticket/369)

---

### Post by SevenMachines on 2010-10-25
Thats not a pip install, If you want to install scapy you can install

* from the ubuntu repositories (recommended!)
$ sudo apt-get install python-scapy

* Use pip, the link to scapy is broken so this does not work (X!)
$ pip install Scapy

* Manually build and install scapy from its website
$ wget [https://www.secdev.org/projects/scapy/files/scapy-latest.tar.gz](https://www.secdev.org/projects/scapy/files/scapy-latest.tar.gz) --no-check-certificate
$ tar -zvxf scapy-latest.tar.gz 
$ cd scapy-2.1.0/
$ sudo python setup.py install

---

### Post by pythonsyntax on 2010-10-25
what this mean


root@myworld:~# scapy
WARNING: No route found for IPv6 destination :: (no default route?)
INFO: Can't import python Crypto lib. Won't be able to decrypt WEP.
INFO: Can't import python Crypto lib. Disabled certificate manipulation tools


where do i get the IPV6 tool?

---

### Post by SevenMachines on 2010-10-25
I notice the official documentation for scapy shows the ipv6 error too as part of a starting run so it may be worth looking at that, i'm guessing not a big problem though.
The other is probably missing pythonn crypto support
$ sudo apt-get install python-crypto

---

### Post by pythonsyntax on 2010-10-25
what that eror mean.i don't have to worry about wep i don't use that on my desktop

---

### Post by pythonsyntax on 2010-10-26
anyone??

---

### Post by SevenMachines on 2010-10-26
Remember, its a just a warning not an error :) I'm guessing you dont have a default ipv6 route setup, neither do I, and i dont really want one! I'd ignore it but if you want to, you may want to look to the support forums, I think theres quite a few threads on setup ipv6. You can check if you have a ipv6 route with something like (if i remember rightly!)
$ ip -6 route show

---

