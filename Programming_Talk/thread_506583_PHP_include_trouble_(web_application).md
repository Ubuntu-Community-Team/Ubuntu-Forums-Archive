---
title: "PHP include trouble (web application)"
date: 2007-07-21
forum: Programming Talk
---

### Post by Note360 on 2007-07-21
Sorry, i dont usually do this lol. er the permissions where al lmessed up. its fixed now, but for future reference what are the basic permissions for php files, perl scripts, html and directories (and images)

---

### Post by nitro_n2o on 2007-07-22
Let's say you have your docs in www 
then 
chmod 750 www 
for html and images
chmod 644 *.html 
for scripts 
chmod 744 *.pl

---

### Post by Note360 on 2007-07-23
> **nitro_n2o said:**
> Let's say you have your docs in www 
then 
chmod 750 www 
for html and images
chmod 644 *.html 
for scripts 
chmod 744 *.pl

Thanks man. usualyl google gives me answers but this i couldnt find.

---

