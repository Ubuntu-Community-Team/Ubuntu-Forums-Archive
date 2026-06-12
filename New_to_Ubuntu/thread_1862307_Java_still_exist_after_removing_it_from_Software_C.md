---
title: "Java still exist after removing it from Software Center in 11.10"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-10-16
Installed 11.10 from scratch.  Then I went to Software Center -> Installed -> Developer Tools and removed all Java 6 instances. 
 
I restarted ubuntu and opened a terminal and typed in
 
java
 
and it is still there.  How do I remove all existing Java installations?

---

### Post by wildmanne39 on 2011-10-16
Hi, you can use this command it should work.
```
sudo apt-get --purge remove packagename
```
Thank you

---

### Post by hoangtu69 on 2011-10-16
where do I go to find out the name of the package?  Sorry, I'm new to Linux.

---

### Post by wildmanne39 on 2011-10-16
Hi, open software center and type java and it will show the names of all the java packages.
Thank you

---

