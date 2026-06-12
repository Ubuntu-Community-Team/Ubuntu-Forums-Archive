---
title: "adding cmd to sudoers"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by tubos2 on 2014-08-01
Purpose: Allow john to perform hdparm without entering password
john is already part of sudo group.

I searched the net for adding a cmd to my sudoers 
file and came up with this:

```

[SIZE=3]$ sudo visudo
#(add line below and save)
john    ALL = (root) NOPASSWD: /sbin/hdparm[/SIZE]

```

but it doesnt seems to work , can someone help?



Ubuntu 14.04.1 LTS

---

### Post by sisco311 on 2014-08-01
It should work. But, sudo reads the sudoers file from the top to bottom. The last line will overwrite any previous conflict with the config settings. So try to put it on the bottom of the file.

---

### Post by tubos2 on 2014-08-01
Moving it to the bottom of the file fixed it , thank you

---

### Post by sisco311 on 2014-08-01
You are welcome.

---

