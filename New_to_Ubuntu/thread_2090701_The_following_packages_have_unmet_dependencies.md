---
title: "The following packages have unmet dependencies"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by erichon on 2012-12-03
Hi community,

I am new to Linux and Ubuntu  and I think I ran into a big problem: With update manager I tried to update several files, but it did not work because the perl-base file always failed to install. So I tried Synaptics, which updated all other files, but failed with the perl-base as well. Not I wanted to install software from software center, but it says you cannot install until perl-base is repaired. When I click on repair, it says it cannot repair. So what now? obviously I got stuck.

PLEASE help!!
Eric

This I get:
The following packages have unmet dependencies:

libperl5.14: Depends: perl-base (= 5.14.2-6ubuntu2.2) but 5.14.2-6ubuntu2 is installed
perl: Depends: perl-base (= 5.14.2-6ubuntu2.2) but 5.14.2-6ubuntu2 is installed
      Depends: perl-modules (>= 5.14.2-6ubuntu2.2) but 5.14.2-6ubuntu2.2 is installed
      Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is installed

---

### Post by erichon on 2012-12-03
Really nobody has an idea?

---

### Post by raja.genupula on 2012-12-03
open your terminal and type 
```
sudo apt-get install -f
```

---

