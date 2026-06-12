---
title: "Ant build: javac slower on two cores than on one core?"
date: 2008-03-03
forum: Programming Talk
---

### Post by mike65134 on 2008-03-03
Hi,

I am building my java project with ant. When ant invokes the javac compiler the compilation lasts longer on two cores than on one core (maxcpus=1 at the grub prompt).

This is strange:
I thought javac is not threaded? But top shows a java process with up to 200%  cpu usage on my dual core machine.

I tried to limit it with  cpulimit -e java  -l 100, but the cpu usage still rises above 100%.

Does anybody know how I could get the faster compile times that I get with only one core activated - but without deactivating the second core?
Thanks!

---

### Post by HuBaghdadi on 2008-03-03
Are you using GNU Java compiler or Sun JDK's compiler?
GNU Java compiler is know for being slow.

---

### Post by mike65134 on 2008-03-03
Thanks! But I am using the original JDK from java.sun.com 
(32-bit linux Binary installer):

java version "1.6.0_04"
Java(TM) SE Runtime Environment (build 1.6.0_04-b12)
Java HotSpot(TM) Server VM (build 10.0-b19, mixed mode)

I am not complaining about the absolut speed, but about the compile time being significantly longer on a dual core machine than on the same machine with only one core activated.

---

### Post by mike65134 on 2008-03-08
In case anybody finds this thread with a search engine:
I went with the question to the apache ant mailing list:
[http://marc.info/?l=ant-user&m=120489376615576&w=2]("http://marc.info/?l=ant-user&m=120489376615576&w=2")
Maybe it can be resolved there, as there are more ant experts.

---

