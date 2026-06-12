---
title: "installing mercurial"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by sabretruth on 2012-02-07
Hello, I just installed Ubuntu 11.10 on my PC in order to run scientific linux-only applications.
The first one I am trying uses a a bash script to install from online, which stops when it fails to find hg and tells me to install mercurial. I tried doing so with the command line:

sudo apt-get install mercurial

and then entering my password. Doing so, I get back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mercurial

What am I missing here?

---

### Post by wojox on 2012-02-07
```
sudo apt-get update; sudo apt-get install mercurial
```

---

