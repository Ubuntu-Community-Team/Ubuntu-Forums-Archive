---
title: "How do I add a message/comments script for my website?"
date: 2008-07-26
forum: Programming Talk
---

### Post by randell6564 on 2008-07-26
Hey folks.

I want to write my own script that will allow visitors to my website to leave comments. I want to insert the script directly into my page. (so that a 'Leave comment' box appears on my page)

What I do not want is to use a premade script. I am looking for a step-by-step tutorial that will guide me in creating, and inserting my own.

Can you help?  Thanks!

---

### Post by -grubby on 2008-07-26
You'll defintely want to use MySQL for that. PHP is a typical web language, but by no means do you have to use it. It depends on what your host supports. You can start [Learning about PHP and Mysql](http://www.w3schools.com/php/php_intro.asp)(Mysql is a bit later in the tutorial)

---

### Post by pmasiar on 2008-07-28
There are many different ways to do it (most of them without PHP and MySQL :-) ) but you need to learn more about programming. I suggest Python as simple universal language, or PHP if you plan to limit yourself to web apps only, and don't mind messy code :-)  There are many open-source apps you can install and learn from, so it is hard (or time consuming) to give good answer without knowing your preferences and skills.

---

### Post by Kadrus on 2008-07-28
You can make it with almost any language you want,using CGI,or an exisiting web development library or framework for this language that you are using,as said above you need to learn more about programming.Python or Perl would be a good choice,but if you want to go with PHP,no one is stopping you.

---

### Post by drubin on 2008-07-28
> Python or Perl would be a good choice,but if you want to go with PHP,no one is stopping you. 

You make it sound as if php is a last resort.... I would recommend it has the web development lang of choice.

---

### Post by randell6564 on 2008-07-31
Thanks for all your replies!

---

### Post by LaRoza on 2008-07-31
> **randell6564 said:**
> 
I want to write my own script that will allow visitors to my website to leave comments. I want to insert the script directly into my page. (so that a 'Leave comment' box appears on my page)

What I do not want is to use a premade script. I am looking for a step-by-step tutorial that will guide me in creating, and inserting my own.


It is rather easy. I made one for my site at one point without using any database engine.

Basically, you need some sort of style for it (basically, a <div class="comment">) and a way to add them. My script used a text box, and authentication box (users IP address, which was echoed next to it) and it could be disable with a password.

The comments were just plain text appended to a file which was included into the page.

---

