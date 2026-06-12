---
title: "can't install software from software center"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by Nabeel Abbas on 2014-01-17
Guys i was previously using a 12.10 on a latitude E6400 machine, I just sold it and brought a E4310 machine. Now i have installed the 64-bit 13.10 on it and from the start i can't install snypatic or gdebi on it.

when i run <*sudo apt-get install gdebi*> i get 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gdebi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gdebi' has no installation candidate


```

also when i open the software center and search the gdebi package it says that "**available from "universe"** **source** " but when i press the button "**use this source**" it just qury it and then nothing happens?????

This is also hapenning when i try to install chrome, Except it gives error about unsatisfied dependencies??? what should I do???

---

### Post by mörgæs on 2014-01-18
Please post the results from 
```
sudo apt-get update
```

---

### Post by kostkon on 2014-01-18
Also post the output of
```
apt-cache policy gdebi
```
and
```
apt-cache policy synaptic
```

---

### Post by Nabeel Abbas on 2014-01-18
Nevermind the universe and multiverse sources weren't selected. It seems there is a bug that these don't get enabled if you select them from the software centre. I had to enable them manually by ```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe restricted multiverse"
```

---

### Post by mörgæs on 2014-01-18
Good, please mark the thread 'solved'.

---

