---
title: "NetBeans, J2EE, Tomcat on Ubuntu"
date: 2005-02-08
forum: Repositories &amp; Backports
---

### Post by ubuntunewbie on 2005-02-08
Hi,

I installed Ubuntu on my workstation just yesterday. I installed J2SE from a repository (after looking at some info from ubuntuforums). I want to install netbeans and j2ee appserver along with the tomcat container on my ubuntu system. I can do that like any other installationby simply downloading from java.sun.com. But to get it through the package manager, I need a repository which contains this software. Can anybody please help me out? Can I create a local repository and then install these binaries on my system? if so, can anybody let me know how to create a local repository?

Appreciate your help !!

Regards,
A Ubuntu Newbie !

---

### Post by scoon on 2005-02-14
Hey there, 

Local Repo howto: [http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html#id2781524)

scoon

---

### Post by ubuntunewbie on 2005-02-18
Thanks !

---

### Post by ubuntunewbie on 2005-02-27
I found that you need to install libapache-mod-jk to get tomcat on your UBUNTU system. Try searching for TOMCAT in synaptec with "NAME & DESCRIPTION" in the search criteria.

---

### Post by hantsy on 2005-03-02
[QUOTE=ubuntunewbie]I found that you need to install libapache-mod-jk to get tomcat on your UBUNTU system. Try searching for TOMCAT in synaptec with "NAME & DESCRIPTION" in the search criteria.[/QUOTE]
 use libapache2_mod_jk2(apache2) or libapache_mod_jk2(apache 1.3.x)
It is more powerful and friendly ...

---

