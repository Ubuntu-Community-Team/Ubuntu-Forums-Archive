---
title: "import pcapy"
date: 2018-02-13
forum: Programming Talk
---

### Post by iayosr on 2018-02-13
Hello,

I have problem with **pcapy **library.

I am using python 3.6.2. When I import pcapy, I have this error:

**import pcapy**
[B]ModuleNotFoundError: No module named 'pcapy'

[/B]I installed: python-pcapy. I downloaded pcapy and installed. However, this error always exists.

Thanks!

---

### Post by norobro on 2018-02-14
Apparently python3 requires a later version than is in the repo.

Two ways to install pcapy that worked on my machine: 

   1. Run "pip3 install pcapy"
   2. Download the source from here: [https://github.com/CoreSecurity/pcapy](https://github.com/CoreSecurity/pcapy)  and run "sudo python3 setup.py install"

You need to have libpcap-dev installed.

---

### Post by iayosr on 2018-02-14
Hi,

Thanks for the answer. Unfortunately, I still have the same problem.

---

