---
title: "http:Allow acces to password protected folder."
date: 2008-05-13
forum: New to Ubuntu
---

### Post by saj0577 on 2008-05-13
Hey,

Im creating a website that stores photos for me, the thing is i don't want anyone to be able to see these photos, is it possible to do it so if your not logged in you cant see the photos but if you log into the website through a php script then you can view the images. If so how would this be  achieved.


Saj

---

### Post by Inxsible on 2008-05-13
> **saj0577 said:**
> Hey,

Im creating a website that stores photos for me, the thing is i don't want anyone to be able to see these photos, is it possible to do it so if your not logged in you cant see the photos but if you log into the website through a php script then you can view the images. If so how would this be  achieved.


SajThis looks more like an homework assignment than an Ubuntu support question. :D

---

### Post by saj0577 on 2008-05-13
A homework asignment?

Psychology
Sociology
Philosophy
R.S
Critical Thinking

I think not mate. ;) More like a home project of a website i want to host my familys pictures on,(different part of family, my family, my sisters family,etc..)

Saj

---

### Post by Inxsible on 2008-05-13
Well there are lots of ways you can do this and it depends on the language you use to code. For eg. HTTP gives HTTP Basic Authentication, Form Based Authentication. You can use any to meet your objective. You can have the photos as private resources all under one folder and make that entire folder private meaning, a login is required to access anything under that folder.

You can also define your own login mechanism and even give different levels of authorization to every user.

---

### Post by saj0577 on 2008-05-13
Well. There are gonig to be different Users, and i only want them to be able to access certain folders,there own, i want it so once the person is logged in with a php/mysql log in system. That it then authenticates them to view the images(content) in the folder.

So like when you access a cpanel and the window pops up is there anyway to automatically enter and submit that data, otherwise my users will be logging in once to have abilities to add photos and again to view them.


Saj

---

### Post by Inxsible on 2008-05-13
> **saj0577 said:**
> Well. There are gonig to be different Users, and i only want them to be able to access certain folders,there own, i want it so once the person is logged in with a php/mysql log in system. That it then authenticates them to view the images(content) in the folder.

So like when you access a cpanel and the window pops up is there anyway to automatically enter and submit that data, otherwise my users will be logging in once to have abilities to add photos and again to view them.


SajYou would have to save the state once they log in so that they can add and then view the photos. Check out HTTP Basic Auth. Its pretty straightforward given that the passwords are also passed in plain text. If you are willing, you should go for form based, since it will re-direct you to a login page if you try to access any secured material on your website.

---

### Post by saj0577 on 2008-05-13
Okay then.

Is it possible to store images in a mysql table?

Saj

---

### Post by Inxsible on 2008-05-13
> **saj0577 said:**
> Okay then.

Is it possible to store images in a mysql table?

SajWhy would you wanna do that?

---

### Post by saj0577 on 2008-05-13
Just a method of storing them.

Why not do it?

Saj

---

### Post by Inxsible on 2008-05-13
> **saj0577 said:**
> Just a method of storing them.

Why not do it?

SajBecause it is much easier to just store them on the server instead of putting them into a database table. Also easier accessing them since you do not have to open a database connection everytime you want to see a photo file.


By the way, it is possible to store images ...but you would have to store them as BLOBS or CLOBS i think and then reconstruct the image everytime someone asks for it.

---

