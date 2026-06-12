---
title: "Cisco PT installation troubles"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by MadleSs on 2013-04-10
Ok guys... When I try to run PT installation I can't get over this step - 
```
Enter location to install Cisco Packet Tracer 5.3.3 or press enter for default [/opt/pt]:
```
if I press enter this error appears: 
```
dirname: missing operand
Try `dirname --help' for more information.
install: 41: install: Bad substitution
```
Can anyone help?


EDIT: Solved... I just tried another version of PT and it's now working :)

---

### Post by jacebennest on 2013-12-05
any help for me would be great

 i have to have 6.0.1 for my school work to run, but i get the same message

---

### Post by jacebennest on 2013-12-05
anybody...? :(

---

### Post by luvarh on 2014-07-13
A mi me paso lo mismo y segun entendi fue que no le daba permisos al directorio install solo ejecutaba sh install y lo que me ayudo fue hacerlo así:
$ chmod +x install
$ ./install

---

### Post by anees2 on 2014-08-21
> **luvarh said:**
> A mi me paso lo mismo y segun entendi fue que no le daba permisos al directorio install solo ejecutaba sh install y lo que me ayudo fue hacerlo así:
$ chmod +x install
$ ./install

Thanks ..it's working.

---

### Post by MGrowl on 2015-07-07
Did you install this using the install script that came with the download on Cisco´s website? Have you tried CPT 6.2? I was just wondering if you had any idea about uninstalling Packet tracer? I´ve tried with apt-get and dpkg, but it didn´t seem to work.

---

