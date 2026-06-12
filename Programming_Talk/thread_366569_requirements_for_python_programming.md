---
title: "requirements for python programming"
date: 2007-02-21
forum: Programming Talk
---

### Post by Isoss on 2007-02-21
Hello programming community

I am a php programmer, and I am learning python. I love it so far and want to start real implementation of the language in web programming and as a desktop application programming.

What I need to know is the following. I'll appreciate any help:

1. What is required for python web programming? what are the main applications that I should install to get it working with apache and mysql? how can I configure apache to read both php and python files (esp. index) wherever they are located on the server?

2. For desktop application programming, what are the requirements? what about database? is mysql a good choice? what other choices for database other than mysql I may use for such a programming? .. 

I searched a lot online but never found what I wanted, so I thought maybe some of the developers here can give more accurate answers!

Thanks in advance.

Isos

---

### Post by Mirrorball on 2007-02-21
I'm going to give a not very detailed answer to your first question. You will need one of these Apache modules: mod_python or cgi or fastcgi. If you just want to be able to drop Python scripts in any web directory, install and configure fastcgi. To use MySQL within Python scripts, install python-mysqldb. I also recommend [Django]("http://www.djangoproject.com/"), a framework for web development.

---

### Post by Isoss on 2007-02-21
> **Mirrorball said:**
> I'm going to give a not very detailed answer to your first question. You will need one of these Apache modules: mod_python or cgi or fastcgi. If you just want to be able to drop Python scripts in any web directory, install and configure fastcgi. To use MySQL within Python scripts, install python-mysqldb. I also recommend [Django]("http://www.djangoproject.com/"), a framework for web development.

Thanks! I will download all that, but still waiting for more answers, especially concerning my second question! 

thanks again.

---

### Post by pmasiar on 2007-02-21
> **Isoss said:**
> 1. What is required for python web programming? what are the main applications that I should install to get it working with apache and mysql? how can I configure apache to read both php and python files (esp. index) wherever they are located on the server?

Remember that "bateries are included": Standard default Python installation has everything you need to start web programming: cgi.py module is good enough. I created simple intro to web programming in Python [http://learnpydia.pbwiki.com/WebApplication](http://learnpydia.pbwiki.com/WebApplication)

You can place your cgi python programs in any Apache cgi-enabled directory, and execute them.

> 2. For desktop application programming, what are the requirements? what about database? is mysql a good choice? what other choices for database other than mysql I may use for such a programming? .. 

bateries are included again... :-) sqlite is library for SQL-based access to files. You don't need the multi-user server of MySQL utill you need it - and when you do, you can reuse most SQL queries you created.

If you insist on MySQL, your friend Google suggests MySQLdb as top hit when searching "python mysql" and I can only agree. :-)

Popular cross-platform library is wxPython, but it is not "settled" enough to be included as standard.

Good luck!

---

### Post by Isoss on 2007-02-21
Thanks to you guys! I'll read everything I can find on the hints you gave me and hopefully I'll start serious python programming soon.

Thanks again. .. This is still open for more suggestions and helpful ideas.

---

### Post by Isoss on 2007-02-21
Oh, by the way, is python web templating also "bateries are included?"

---

### Post by pmasiar on 2007-02-21
> **Isoss said:**
> Oh, by the way, is python web templating also "bateries are included?"

htmltmpl was included in my Ubuntu distro but IIUC is not part of standard distro - you have plain string interpolation instead.

For real production web apps you should look into Django or Turbogears instead.

---

### Post by stani on 2007-03-06
In case you are looking for a good editor, try SPE which has an interpreter built in:
[http://pythonide.stani.be](http://pythonide.stani.be)

There will be a new release soon which is very focused on running smooth on Ubuntu. You can also try out the old release:

sudo apt-get install spe

Stani

---

