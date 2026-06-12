---
title: "E: Unable to locate package nepenthes"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by hshehari on 2013-06-14
Hi,,

** I try to install Nepenthes package**
```
sudo apt-get install nepenthes
```

** but this message appears:**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nepenthes
```


[B]I'm using Ubuntu 13.04 x86
and this is official site of Nepenthes:[/B]
[http://nepenthes.carnivore.it/download](http://nepenthes.carnivore.it/download)

** Any help?**

---

### Post by coffeecat on 2013-06-14
The nepenthes package hasn't been in the Ubuntu repositories since Ubuntu 10.04, which is now end-of-life. It's not in the 13.04 repository which is why you get the Unable to locate package nepenthes error. From reading your link it could very well be that nepenthes is abandonware. The page you linked hasn't been updated for well over 4 years, and the source package for download is dated 2008.

---

### Post by newb85 on 2013-06-14
A newer version was released for Precise.  The source package can be found at launchpad.

[https://launchpad.net/ubuntu/precise/+package/nepenthes](https://launchpad.net/ubuntu/precise/+package/nepenthes)

---

### Post by hshehari on 2013-06-16
> **coffeecat said:**
> The nepenthes package hasn't been in the Ubuntu repositories since Ubuntu 10.04, which is now end-of-life. It's not in the 13.04 repository which is why you get the Unable to locate package nepenthes error. From reading your link it could very well be that nepenthes is abandonware. The page you linked hasn't been updated for well over 4 years, and the source package for download is dated 2008.

> **newb85 said:**
> A newer version was released for Precise.  The source package can be found at launchpad.

[https://launchpad.net/ubuntu/precise/+package/nepenthes](https://launchpad.net/ubuntu/precise/+package/nepenthes)


Thank you all,
I found that Nepenthes is outdated and I have to use Dionaea instead
[http://nepenthes.carnivore.it/](http://nepenthes.carnivore.it/)

---

