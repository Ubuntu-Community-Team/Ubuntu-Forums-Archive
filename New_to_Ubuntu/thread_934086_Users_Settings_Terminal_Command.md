---
title: "Users Settings Terminal Command"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by kineem on 2008-09-30
Hello. I use ubuntu server edition. When I try to  unlock **users settings** panel It warns me like [B]Could not authenticate 
An unexpected error has occurred[/B].  Probably it wants me to open the users settings panel as root on terminal But I dont know how to start users settings on terminal. Could you help please?

Thanks in advance.

---

### Post by Joeb454 on 2008-09-30
Does the user account have privileges to use sudo normally?

You could always try running ```
gksudo users-admin
``` from a terminal and seeing if that works

---

### Post by kineem on 2008-09-30
> **Joeb454 said:**
> Does the user account have privileges to use sudo normally?

You could always try running ```
gksudo users-admin
``` from a terminal and seeing if that works

I am root but I cant unlock users settings from gui. Your code also didnt help. Here is the terminal output:


[PHP]
** (users-admin:7651): CRITICAL **: Unable to lookup session information for process '7651'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
[/PHP]

---

