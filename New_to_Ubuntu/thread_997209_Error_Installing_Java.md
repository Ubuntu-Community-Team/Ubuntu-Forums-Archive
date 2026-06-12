---
title: "Error Installing Java"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by WillT87 on 2008-11-29
I was following the tutorial on how to installing the java plugin and I get this error 

ln: creating symbolic link `./libjavaplugin_oji.so': Permission denied


also on firefox pages never fully load and the address doesn't update

---

### Post by binbash on 2008-11-29
try with sudo command

---

### Post by WillT87 on 2008-11-29
I have it installed just not linked to firefox

---

### Post by WillT87 on 2008-11-29
Problem solved 

sudo ln -s /home/bill/Desktop/java/jre1.6.0_10/plugin/i386/ns7/libjavaplugin_oji.so


Sudo worked

---

### Post by ibutho on 2008-11-29
You probably need to prefix the command you ran with sudo (as mentioned above) e.g.
```
sudo ln -s /path/to/libjavaplugin_oji.so /usr/lib/firefox/plugins/.
```
An alternative would be to enable the universe and multiverse repositories and then install the sun-java6-plugin package.

Edit: I must have been typing this post when you posted the solution that worked for you.

---

