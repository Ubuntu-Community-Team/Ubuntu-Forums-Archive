---
title: "can not open anjuta second time"
date: 2011-08-26
forum: Packaging and Compiling Programs
---

### Post by krishnasagar on 2011-08-26
i Installed and oped anjuta .
when i closed it and opened again it is not opening.
I tried to open it form terminal e. but it showing and error 

"libanjuta-symbol-db-ERROR **: Opening global project under /home/sagar/.cache/anjuta"

---

### Post by krishnasagar on 2011-08-26
> **jackjwalt said:**
> Anjuta is an integrated development environment for the C, C++, Java, JavaScript, Python and Vala computer programming languages, written for the GNOME project. It comes standard on base installation DVDs of major Linux distributions such as Ubuntu, openSuse, Fedora, and Mandriva (amongst others).

yes I installed it btu i cant open int. it is showing an error.

---

### Post by Kyoushuu on 2011-09-04
Try removing the cache of Anjuta by opening a terminal by typing "rm -rf /home/sagar/.cache/anjuta" (without quotes) then enter. Maybe the symbols database is corrupted.

---

