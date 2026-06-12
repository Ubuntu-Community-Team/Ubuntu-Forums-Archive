---
title: "java version help"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by goof on 2013-07-04
hi i havee jaava 7 installed and java 6 and all icetea packages from software ceter i have netbeans from there site not software center but when i java -version it tells me im using 1.5.0 how do i fix this problem?thanks

---

### Post by claracc on 2013-07-05
To choose what java you want to use, you run the following command: 
```
sudo update-alternatives --config java
```

You will be presented with a series of choices, then you select the number you want to use.

Good reference about java in ubuntu: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by goof on 2013-07-06
thanks that done it but i had to uninsall java completely and then install from scratch and get netbeans from there site respositories version to outdated

---

