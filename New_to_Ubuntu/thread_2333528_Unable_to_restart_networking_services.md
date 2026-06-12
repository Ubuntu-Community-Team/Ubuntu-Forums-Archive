---
title: "Unable to restart networking services"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by pradeep8985 on 2016-08-10
Hi

I am new to Ubuntu and I am currently using Ubuntu 14.04.3 LTS. I am unable to restart networking services using 
"service networking restart" . The reason why I am particular about this command is I have configured bonding in the server and I cannot simply use of "ifdown & ifup" commands. Can anyone help.

PS: Let me know if I am not clear, I will try to explain better

---

### Post by entropy1 on 2016-08-10
Try
```
sudo service network-manager restart
```

---

