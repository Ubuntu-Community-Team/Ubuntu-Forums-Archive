---
title: "apt-get error"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by shashank.ks on 2008-06-24
I get the following error message while installing or removing packages. 


var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:2635: parser error : Opening and ending tag mismatch: toc line 2312 and sect 
</toc></doc></sect> 
                   ^ 
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:3231: parser error : Opening and ending tag mismatch: doc line 2312 and sect 
</toc></doc></sect> 



the full errors are attached with the thread. Because of these i am not able to install the netbeans which i need very badly.


Please help :cry:

---

### Post by Nikitas350 on 2008-06-24
Try run this command sudo scrollkeeper-rebuilddb

---

### Post by phidia on 2008-06-24
This is sort of a basic question but have you issued: > sudo apt-get update? If not try that and then try the install again.

---

### Post by shashank.ks on 2008-06-24
philida:      I had done that already. But the problem is when install any package using the apt-get i get this error message.


nikitas350: I issued the command u suggested. But it is taking long time. I will know more at the end of execution.

---

### Post by phidia on 2008-06-24
[This]("http://www.linux.com/articles/48910") is a good article on what to do when apt fails. I hope that helps.

---

