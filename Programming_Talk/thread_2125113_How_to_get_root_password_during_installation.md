---
title: "How to get root password during installation"
date: 2013-03-13
forum: Programming Talk
---

### Post by galfly on 2013-03-13
Hi,

I am writing a program that requires elevated root privileges to install. How can I do it in a c++ program?
Thank you

---

### Post by lisati on 2013-03-13
Good luck on your endeavours to find a workable solution that suits your needs.

I would suggest running the installation with the appropriate permission, e.g. with the sudo command. For more information, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ofnuts on 2013-03-13
All apps requires root priviledges to install. Just package you app as .deb and .rpm and it can be installed everywhere.

---

