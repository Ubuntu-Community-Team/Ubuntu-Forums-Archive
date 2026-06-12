---
title: "[SOLVED] cant update ultimate gamers edition"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by m3t3ors on 2008-05-15
ive just got mand installed the ultimate gamers edition but it wont let me update.
i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
any help guys im also wanting to install the nvidia driver after i update

---

### Post by forestpixie on 2008-05-15
run the command it's asking for

sudo dpkg --configure -a

---

### Post by m3t3ors on 2008-05-15
> **forestpixie said:**
> run the command it's asking for

sudo dpkg --configure -a

just ran the command and it tells me i need to be the superuser
it never asked me for a superuser password during install

when i type in the password i use during installing software it says password incorrect

---

### Post by forestpixie on 2008-05-15
You ran it as I posted? or without sudo

superuser is root, you can use sudo (SuperUser DO)

It should be same password as you use to login, you won't get an echo in terminal - it will be invisible, but it is there

---

### Post by m3t3ors on 2008-05-16
problem solved thanx forestpixie

---

