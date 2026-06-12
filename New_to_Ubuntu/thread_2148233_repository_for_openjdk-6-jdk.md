---
title: "repository for openjdk-6-jdk"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by eslpoeor on 2013-05-24
Hi,

I'm trying to install [openjdk-6-jdk]("http://apt.ubuntu.com/p/openjdk-6-jdk") on ubuntu , but i can't find any repository with it?

can anyone help me ?

Thanks

---

### Post by Cheesemill on 2013-05-24
It's in the standard repositories for all versions of Ubuntu. What does the following command do...
```
sudo apt-get update && sudo apt-get install openjdk-6-jdk
```

---

### Post by dino99 on 2013-05-24
open a terminal (or use 'synaptic')

> sudo apt-get install openjdk-6-jdk

but 7 is usually installed now

---

### Post by eslpoeor on 2013-05-24
i have done this but it stuck on 
0% [waiting for headers]

i use 12.04 , behind proxy
and i can do without any problems [COLOR=#000000]*openjdk-7-jdk, but not the *[/COLOR][COLOR=#000000]*openjdk-6-jdk !!!!*[/COLOR]

---

