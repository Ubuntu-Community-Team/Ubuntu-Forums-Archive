---
title: "Difference between apt-get and aptitude"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-06-21
Hi, 
I just wanna know what excactly is the difference between apt-get and aptitude? I heard rumors, that aptitude manages dependencies better than apt-get. Is that correct? 

Thanks. Jab

---

### Post by the_doc on 2008-06-21
Any use?

[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by Jabz.biz on 2008-06-21
Thanks. :)

---

### Post by S1xp4ck on 2008-06-21
Someone more experienced can correct me if I am wrong, but how I understand it is when you use aptitude and remove a package later, the dependencies of that package will also be removed. Apt-get will only remove the package specified.

---

### Post by billgoldberg on 2008-06-21
> **S1xp4ck said:**
> Someone more experienced can correct me if I am wrong, but how I understand it is when you use aptitude and remove a package later, the dependencies of that package will also be removed. Apt-get will only remove the package specified.

"sudo apt-get autoremove package" will remove the dependencies just fine.

---

### Post by S1xp4ck on 2008-06-21
Good to know thanks =)

---

### Post by Jabz.biz on 2008-06-21
> **billgoldberg said:**
> "sudo apt-get autoremove package" will remove the dependencies just fine.

correct, but who really does that? thanks to apt-get I have some dependency left-overs :) .

---

### Post by Canis familiaris on 2008-06-21
> **Jabz.biz said:**
> correct, but who really does that? thanks to apt-get I have some dependency left-overs :) .
To save space I reckon!

---

### Post by markbuntu on 2008-06-21
I use synaptic wherever possible. It gives you the choice of removing debs or not.

---

