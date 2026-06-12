---
title: "Fix for email password expose for Pidgin"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by npnutn7 on 2008-09-18
I read this post in another site [LINK]("http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html") to hide your stored passwords in pidgin. 

I don`t if this one works or not , but i am asking who tried it before. is it good enough? and how to check that the passwords are not visible again.

---

### Post by npnutn7 on 2008-09-18
anyone?

---

### Post by nowshining on 2008-09-18
hmmm u gotta patch pidgin first ie: compile a copy of pidgin urself..are u up for it??

---

### Post by npnutn7 on 2008-09-18
thanks for ur reply.why would i compile pidgin first! it`s already there
..

---

### Post by vikram on 2008-09-18
> **npnutn7 said:**
> I read this post in another site [LINK]("http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html") to hide your stored passwords in pidgin. 

I don`t if this one works or not , but i am asking who tried it before. is it good enough? and how to check that the passwords are not visible again.

I can't help you with Pidgin since I dont use it.  However Kopete has similar functionality with webcam support. Like all other KDE apps stores its passwords in Kwalletamanger which uses encryption.

Hope this helps.

---

### Post by nowshining on 2008-09-18
to patch it :) and it won't work on the latest versions, again it's a patch, u need the source file - untar it, installed needed devs, ./configure, make and sudo make install or to build a simple deb package install checkinstall and follow the directions..

---

### Post by npnutn7 on 2008-09-18
I have gnome, but i don`t know if the encryption and keyrings works as the same as kwallet.

meanwhile i will try to patch souce code

---

