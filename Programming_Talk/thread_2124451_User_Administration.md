---
title: "User Administration"
date: 2013-03-11
forum: Programming Talk
---

### Post by vlyalcin on 2013-03-11
I want to share with you the User Management that I wrote in Python with help PyQt interface library.

You can reach the source codes from [https://github.com/vlyalcin/User-Administration](https://github.com/vlyalcin/User-Administration)

User Administration is for manage the users in the Ubuntu systems. Program mainly add new users, edit or delete existing users. Also you can choose user 
picture from computer or using computer camera.

Used os, sys, shutil, datetime, Image, cv, python-passlib, PyQt4 libraries for various purposes.

With the installation of program with help "python setup.py install" command, program gets your /etc/passwd, /etc/shadow, /etc/group files backup to "/usr/share/user-administration/.backup" path.
If any problem occur, you can fix the problem with move back your backup files to related paths.

Program works only in Ubuntu successfully, because of the user picture situation.

**Screen Shoots**

[IMG]http://3.bp.blogspot.com/-aY1DEsamD5k/UTuNuP-CHBI/AAAAAAAAAGU/POAtClJ9Ars/s1600/add-user.jpg[/IMG]

[IMG]http://2.bp.blogspot.com/-asEiXgtKvfs/UTuNvcEwYjI/AAAAAAAAAGc/iwYUmcj4Szc/s1600/main-window.jpg[/IMG]

[IMG]http://2.bp.blogspot.com/-pz57ue3koQc/UTuNwZ-1hAI/AAAAAAAAAGk/6Gmwt4bmvR8/s1600/new-user-on-cat-windows.jpg[/IMG]

---

