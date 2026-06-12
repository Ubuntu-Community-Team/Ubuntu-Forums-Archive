---
title: "lxml for python 2.7 on ubuntu 10.10"
date: 2011-02-22
forum: Programming Talk
---

### Post by ghee22 on 2011-02-22
cross-posted on [StackOverflow.com]("http://stackoverflow.com/questions/5082422/lxml-for-python-2-7-on-ubuntu-10-10")

On Ubuntu 10.10, I am unable to install lxml to python 2.7. Here are the steps I take.

```
sudo su -
apt-get install python2.7
apt-get install python-lxml
```
Note when running the install for python-lxml package, the following appeared:

```
INFO: using unknown version '/usr/bin/python2.7' (debian_defaults not up-to-date?)"
```
Importing the module in python2.6 (the version that comes standard with Ubuntu) works. However, importing the module under python2.7 does not.

---

