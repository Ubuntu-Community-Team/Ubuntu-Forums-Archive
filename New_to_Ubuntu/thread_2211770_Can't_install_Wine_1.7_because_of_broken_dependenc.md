---
title: "Can't install Wine 1.7 because of broken dependencies"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by patagriff253 on 2014-03-17
When trying to install Wine 1.7 from the terminal, I receive this message:

The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-amd64 (= 1:1.7.14-0ubuntu1~saucy1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


How do I find out what these held broken packages are and repair them?

I am using Ubuntu 13.10.

---

### Post by deadflowr on 2014-03-17
```
sudo apt-get -f install
```
should tell you what broken packages you have, as well as try to fix them.
You might try
```
sudo apt-get update
```
and then
 ```
sudo apt-get upgrade
```
first, to make sure all packages installed are up to date.

---

