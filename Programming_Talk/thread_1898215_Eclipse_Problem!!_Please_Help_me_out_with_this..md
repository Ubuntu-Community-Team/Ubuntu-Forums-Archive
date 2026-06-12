---
title: "Eclipse Problem!! Please Help me out with this."
date: 2011-12-20
forum: Programming Talk
---

### Post by chenr1 on 2011-12-20
Hey guys im on ubuntu 11.10 and i used minecraft coder pack 5.0 and  decompile just fine but when i try to excecute the application i made i  get this error in the eclipse console   '<terminated> Cilent[Java Application]  /usr/lib/jvm/java-6-openjdk/bin/java
Then i get "Error occurred during initialization of VM
Could not reserve enough space for object heap"

Any help is Appreciated.
-thanks Caleb

---

### Post by chenr1 on 2011-12-20
bump

---

### Post by myrtle1908 on 2011-12-20
You probably need to give the VM some more to juice play with.

Open the "Run Configuration" dialog for your project and add **-Xmx256m** (where 256m is the desired maximum heap size in megabytes) to the "VM arguments" textarea.

---

