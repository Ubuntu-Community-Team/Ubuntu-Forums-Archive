---
title: "web site"
date: 2009-04-14
forum: Programming Talk
---

### Post by lridings on 2009-04-14
I have a very broad question and I dont expect anyone to answer it all but I have an idea and I need to learn some things. I want to know what the basic components of a social networking website are. I dont need any code but I want to plan this idea out before I jump into anything. thanks for your help.

---

### Post by Jesdisciple on 2009-04-14
Having worked a good bit with both client- and server-side web development, I can tell you that the main thing is to have lots and lots of databases - for users, images, groups, applications, songs, messages, and anything else you need to keep track of.  Once you have those structured, you obviously need pages to allow the user to operate on them, and the pages need to be pretty (CSS and JavaScript).  Beyond that, it depends on exactly what the users should be able to do.

---

### Post by soltanis on 2009-04-14
A storage scheme for information, and lots of it; even moderate sized social-networking sites would produce huge amounts of information that you need to be able to handle. You must be able to store data reliably, retrieve it efficiently, and be able to modify it easily.

Then you need a scheme for serving web content (i.e., what kind of server-side technologies are you going to use?) through HTTP requests in a consistent manner.

Tying the storage into the web-content serving is pretty much the hard part. A lot of people use technologies like MySQL to quickly store, retrieve, and modify content. Depending on how many requests you have to serve, you may need to modularize your architecture and implement load-balancing.

---

### Post by pmasiar on 2009-04-14
You can see the code how exactly it is done - check Django components, they include wiki, forum, email registration, and more. All in documented Python

---

### Post by matmatmat on 2009-04-15
If you want a book on MySQL & PHP (skills that you would need) try [this]("http://www.amazon.co.uk/PHP-MySQL-Web-Development-3rd/dp/0672326728/ref=sr_1_7?ie=UTF8&s=books&qid=1239788461&sr=8-7") book

---

### Post by s.fox on 2009-04-15
Hi,

For ideas you could just try and copy existing social networking sites such as Facebook and MySpace.  Once you have that set up you could try and introduce features that would be unique to your site.

-Ash R

---

