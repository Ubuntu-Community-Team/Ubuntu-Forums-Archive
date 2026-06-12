---
title: "32 bit compatibility"
date: 2015-02-06
forum: New to Ubuntu
---

### Post by jon80 on 2015-02-06
I am trying to configure a development environment that includes java and a few plugins for android programming and encountered a couple of glitches.

Would you know if there is a difference between installing ubuntu on a 32 bit or on a 64 bit processor and does it depend on the virtual host if you are using a virtualization engine (software)?

The documentation at [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) indicates that both processors are supported, however I encountered a few crashes with applications and I am wondering whether this might be a problem, since some emulators require an Intel virtualization chip (see [https://software.intel.com/en-us/android/articles/intel-hardware-accelerated-execution-manager](https://software.intel.com/en-us/android/articles/intel-hardware-accelerated-execution-manager)).

---

### Post by sandyd on 2015-02-06
> **jon80 said:**
> I am trying to configure a development environment that includes java and a few plugins for android programming and encountered a couple of glitches.

Would you know if there is a difference between installing ubuntu on a 32 bit or on a 64 bit processor and does it depend on the virtual host if you are using a virtualization engine (software)?

The documentation at [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) indicates that both processors are supported, however I encountered a few crashes with applications and I am wondering whether this might be a problem, since some emulators require an Intel virtualization chip (see [https://software.intel.com/en-us/android/articles/intel-hardware-accelerated-execution-manager](https://software.intel.com/en-us/android/articles/intel-hardware-accelerated-execution-manager)).

Which version of java are you using?

By default, Ubuntu comes with openjdk in its repositories. It is known that openjdk doesn't work well with some things.

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html) offers a nice guide on how to install the 'proper' Oracle Java 8.

---

