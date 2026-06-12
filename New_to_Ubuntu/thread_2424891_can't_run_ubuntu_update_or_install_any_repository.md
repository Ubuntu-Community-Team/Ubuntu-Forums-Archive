---
title: "can't run ubuntu update or install any repository"
date: 2019-08-16
forum: New to Ubuntu
---

### Post by hmdou on 2019-08-16
hi !
I'm on ubuntu 19.04 , when I run sudo apt-get update or try to add a repository ( in my case I tried to add sudo add-apt-repository ppa:webupd8team/atom ) I get this error
[https://2.top4top.net/p_1323mqdmd1.jpg](https://2.top4top.net/p_1323mqdmd1.jpg)
please help me solve this error 
thank you

---

### Post by deadflowr on 2019-08-16
Neither ppa has an archive for 19.04.
Remove them both.
```
sudo add-apt-repository -r ppa:alexis.bienvenue/amc-stable
sudo add-apt-repository -r ppa:webupd8team/atom
sudo apt update
```

---

### Post by hmdou on 2019-08-16
I need to use these  softwares ( like amc )
so the solution is to install ubuntu 18.04 LTS ?
I'm running it on VM , so I can easily install other ubuntu compatible version.

---

### Post by deadflowr on 2019-08-16
auto-multiple-choice is in Ubuntu 19.04's own archives.
[https://packages.ubuntu.com/disco/auto-multiple-choice]("https://packages.ubuntu.com/disco/auto-multiple-choice")
So you can install like a normal package.

You can grab the deb for atom from here:
[https://atom.io/]("https://atom.io/")
Double clicking should open the software installer program to install it.
(It's also much newer than what the PPA offers.)

...Or do your thing and reinstall 18.04 and add the PPAs.
You have choices.

---

### Post by hmdou on 2019-08-17
installed 18.04
thank you very much for you help.

---

