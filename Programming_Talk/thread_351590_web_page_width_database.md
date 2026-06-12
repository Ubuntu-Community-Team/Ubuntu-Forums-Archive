---
title: "web page width database"
date: 2007-02-02
forum: Programming Talk
---

### Post by sartic on 2007-02-02
Looking 4 easy sdk on linux 4 development of www pages width database support? Any hints or urls? Sorry if it offtopic.

---

### Post by pmasiar on 2007-02-02
> **sartic said:**
> Looking 4 easy sdk on linux 4 development of www pages width database support? Any hints or urls? Sorry if it offtopic.

Python: either plain CGI, or frameworks: Django or Turbogears
Ruby, with Rails

If Python/CGI looks hard, try Java/Struts for 2 weeks. Then you come back to Python and compared with java/Struts, Python/CGI will be almost trivial :-)

---

### Post by sartic on 2007-02-03
> **pmasiar said:**
> Python: either plain CGI, or frameworks: Django or Turbogears
Ruby, with Rails

If Python/CGI looks hard, try Java/Struts for 2 weeks. Then you come back to Python and compared with java/Struts, Python/CGI will be almost trivial :-)

Thx! I will investigate all your hints.

---

### Post by clouserw on 2007-02-05
[CakePHP]("http://cakephp.org/") is a decent framework for php

---

### Post by stoffe on 2007-02-05
There's a bazillion decent-to-good alternatives out there, depending on what language or other preferences you have. My vote would go to Ruby on Rails though, it's really well designed throughout which makes it very nice not only for development but for maintenance and further enhancements.

---

### Post by etank on 2007-02-05
If you do decide to try out Django I recommend looking at [http://www.djangobook.com/](http://www.djangobook.com/). It is a book that the developers of the project are writing and they are releasing it to the public a chapter or so a week.

---

### Post by gh0st on 2007-02-06
> **etank said:**
> If you do decide to try out Django I recommend looking at [http://www.djangobook.com/](http://www.djangobook.com/). It is a book that the developers of the project are writing and they are releasing it to the public a chapter or so a week.

Yeah Django is amazing, I've been a web developer for a few years now and I just started using Django. It automates a lot of the boring repetative tasks involved when developing sites. It's not all straightforward, you do need to take a bit of time to learn it.

It's really easy to start developing Django because it contains a development server that you can run a bit like Tomcat for Java if you've ever seen that. You don't need to worry about setting up Apache or anything. I started developing an app with Django yesterday on a new PC using Edgy and the setup was easy. I just got the Django package from the site, installed it and used SQLite3 to do the database which was already installed. I had a fully working site up and ready in about an hour and I can easily transfer it to a MySQL database for the production site. It was only recording simple blog stuff mostly but I would have spent ages doing it in ASP.NET which is what I used to use.

I feel like a cave man who thought fire was pretty impressive but then got given a microwave  :lolflag: 

I recommend starting with the tutorials on the Django site, the first 4 will give you the core Django skills you need. It takes a bit of getting used to but if you've done web development before you'll be throwing out sites in no time.

[http://www.djangoproject.com/](http://www.djangoproject.com/)

You can start with the installation guide and then go straight on to the tutorials, thats what I did. As you can tell, I'm pretty excited about it, I think I need to lie down.

DISCLAIMER: This is purely the opinion of the author. Other web technologies are available :) ;) 

Good Luck

---

