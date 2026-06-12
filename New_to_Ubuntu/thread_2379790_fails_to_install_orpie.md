---
title: "fails to install orpie"
date: 2017-12-09
forum: New to Ubuntu
---

### Post by sprinterdriver on 2017-12-09
Hi.

I want to install orpie (RPN calculator for Terminal). However, when I try to install - this happens:
```
sprinterdriver@Aspire-5737Z:~$ sudo apt-get install orpie
[sudo] password for sprinterdriver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package orpie

```

Man page for orpie
[http://manpages.ubuntu.com/manpages/xenial/man1/orpie.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/orpie.1.html)

---

### Post by again? on 2017-12-09
If you're using the artful repositories, there doesn't appear to be a build.
[https://packages.ubuntu.com/search?keywords=orpie&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=orpie&searchon=names&suite=all&section=all)

**[COLOR="#FF0000"]Edit[/COLOR]**: I can install the bionic deb.
Requires 2 dependencies on my Ubuntu 17.10 install.

Choose mirror and dowload bionic deb...
[https://packages.ubuntu.com/bionic/amd64/orpie/download](https://packages.ubuntu.com/bionic/amd64/orpie/download)

Open terminal and cd to directory containing orpie deb...
```
cd ~/Downloads
```
Install deb (dpkg does not install dependencies so may show errors)
```
sudo dpkg -i orpie_1.5.2-2_amd64.deb
```
Fix dependencies...
```
sudo apt install -f
```

---

### Post by sprinterdriver on 2017-12-09
Thank you very much.

After downloading the deb file, it also works to right click on it (in Caja) and choose *Open With GDebi Package Installer*.

---

