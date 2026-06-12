---
title: "git-gui crashes on commit"
date: 2015-08-03
forum: Programming Talk
---

### Post by marchello_lippi2 on 2015-08-03
Hi all, 

Hope this is correct thread. 

Git-gui crashes when trying to commit. 
git-gui version 0.18.0.14.g1b2c7
git version 1.9.1 
Tcl/Tk version 8.6.1

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

I use Lubuntu. 

This program works fine for me under windows. 

BTW, the situation didn't change during many weeks. I thought this is error in package and it should be fixed soon. 
This is one of few situations when I should switch to windows, I'd like to avoid this. What to do?

---

### Post by spjackson on 2015-08-05
I have the same environment, with the exception that it's Xubuntu instead of Lubuntu, and git gui doesn't crash on commit for me. Does it do this for just one project or for all projects? If I were in your shoes, I would definitely not switch to Windows. I would either stick with git gui and do commits from the command line, or try another gui [https://git-scm.com/downloads/guis](https://git-scm.com/downloads/guis) . To be honest, most of my git activity is from the command line anyway.

---

### Post by marchello_lippi2 on 2015-08-05
spjackson

>>> Does it do this for just one project or for all projects?

git-gui crashes when I try to commit any of my projects. 

>>> try another gui [https://git-scm.com/downloads/guis](https://git-scm.com/downloads/guis) 

Maybe you or someone else can please suggest another gui that has logic and interface similiar to git-gui ? I will try it by myself too of course.

---

### Post by spjackson on 2015-08-05
My git usage is mainly from the command line. I have heard that gitg is good but I don't have experience of using it in anger.

---

### Post by marchello_lippi2 on 2015-08-07
spjackson

gitg looks good, I mean design. 
I'm waiting when something will be needed to commit. Don't have test git environment, can't try at production without reason.

---

