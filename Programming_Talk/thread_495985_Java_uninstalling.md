---
title: "Java uninstalling"
date: 2007-07-08
forum: Programming Talk
---

### Post by aliov_85 on 2007-07-08
Hello every body.

Can any body tell me please how can I uninstall my jdk (for reinstalling) ?

---

### Post by jespdj on 2007-07-08
Did you install it via the normal Ubuntu package management system (Synaptic or Adept)? Then you just uninstall it via Synaptic or Adept.

---

### Post by Ramses de Norre on 2007-07-08
And otherwise you just delete the folder into which you installed it.

---

### Post by aliov_85 on 2007-07-09
Hi,
First thanks 4 replies;

Second: I installed through this:  
> 
sudo apt-get install sun-java5-jdk,

---

### Post by jespdj on 2007-07-09
The you uninstall it like this:
```
sudo apt-get remove sun-java5-jdk
```

You should familiarize yourself with tools like apt-get. Try typing in 'man apt-get' to see what options there are.

---

