---
title: "getting an (Errcode: 13) message when trying to write to a text file with mysql"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by badperson on 2008-04-24
Hi,

I have a working query, but when I add the command to write to a text file, it gives me the (Errcode: 13) message, which has to do with permissions. 

I'm trying to write to my Documents folder, but have tried a few others as well. 

Anyone know how to set the permissions so mysql can write to the HD?
thanks, 
bp

---

### Post by Monicker on 2008-04-24
> **badperson said:**
> Hi,

I have a working query, but when I add the command to write to a text file, it gives me the (Errcode: 13) message, which has to do with permissions. 

I'm trying to write to my Documents folder, but have tried a few others as well. 

Anyone know how to set the permissions so mysql can write to the HD?
thanks, 
bp

As the root mysql user do the following from the mysql cli or gui:

grant file on *.* to username


File is a global option, so use it carefully, because there are security implications.

---

