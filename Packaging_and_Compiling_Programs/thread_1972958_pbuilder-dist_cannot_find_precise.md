---
title: "pbuilder-dist cannot find precise"
date: 2012-05-04
forum: Packaging and Compiling Programs
---

### Post by csoler on 2012-05-04
Hi,

I usually make use of pbuilder-dist to build source debian packages on natty for other distributions. However, the command fails for precise pangolin:

> pbuilder-dist precise create
Warning: Unknown distribution "precise". Do you want to continue [y/N]? 

...apparently pbuilder-dist does not know precise yet. This is weird. Should I enable it somewhere?

Subsidiary question: where is the list of supported distribution names? I could not find it. 

Config: ubuntu natty-amd64.

Thanks for any help!
Cyril

---

### Post by csoler on 2012-05-07
up?

---

### Post by Despot on 2012-07-03
I encountered the same issue recently. Adding "precise" to the UBUNTU_SUITES variable in ~/.pbuilderrc solved the problem for me.

---

