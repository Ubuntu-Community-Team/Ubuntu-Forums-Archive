---
title: "Python web development, a few questions"
date: 2011-08-03
forum: Programming Talk
---

### Post by mendhak on 2011-08-03
Hi, I've just started learning Python and am interested in web development with it.  So, a few questions

1)  Websites in Python - is it common?  

2)  What IDEs would you use for this?

After a lot of reading, it appears that everyone would rather have me use FastCGI instead of mod_python.  However, documentation and examples are sparse!  [This]("http://www.electricmonk.nl/docs/apache_fastcgi_python/apache_fastcgi_python.html") was the only guide I had to get it up and running.    


3) So is Python with FastCGI common or mod_python?  I'm forcing myself to go FastCGI because I plan to host on hostgator.com and they don't do mod_python.  They do FastCGI and Apache2.  Please tell me if I should pick a better option in terms of hosting or something other than Apache2.

4)  Hypothetically speaking - if I were to use lighttpd+fastcgi and write a python script, would it work if I deployed to an Apache2+fastcgi environment?  

5) I noticed that in 'regular' mod_python, errors show up on the web page itself, very useful.  But in fastcgi, I just get an 'internal server error' and I have to go into the apache error logs to see what the error was.  Is there an easier way to debug Python with fastcgi?  I'd rather not do this via the commandline because I want to 'see' the rendered output.  

6)  It might just be me... but I've got a Python script which I originally wrote for mod_python.  I then 'converted' it to use FastCGI.  But I've noticed that the script is slower in FastCGI than it was in mod_python.  Just me, right?


Thanks... any answers to any questions are appreciated.  :D

---

### Post by LemursDontExist on 2011-08-03
> **mendhak said:**
> Hi, I've just started learning Python and am interested in web development with it.  So, a few questions

1)  Websites in Python - is it common?  

2)  What IDEs would you use for this?

After a lot of reading, it appears that everyone would rather have me use FastCGI instead of mod_python.  However, documentation and examples are sparse!  [This]("http://www.electricmonk.nl/docs/apache_fastcgi_python/apache_fastcgi_python.html") was the only guide I had to get it up and running.    


3) So is Python with FastCGI common or mod_python?  I'm forcing myself to go FastCGI because I plan to host on hostgator.com and they don't do mod_python.  They do FastCGI and Apache2.  Please tell me if I should pick a better option in terms of hosting or something other than Apache2.

4)  Hypothetically speaking - if I were to use lighttpd+fastcgi and write a python script, would it work if I deployed to an Apache2+fastcgi environment?  

5) I noticed that in 'regular' mod_python, errors show up on the web page itself, very useful.  But in fastcgi, I just get an 'internal server error' and I have to go into the apache error logs to see what the error was.  Is there an easier way to debug Python with fastcgi?  I'd rather not do this via the commandline because I want to 'see' the rendered output.  

6)  It might just be me... but I've got a Python script which I originally wrote for mod_python.  I then 'converted' it to use FastCGI.  But I've noticed that the script is slower in FastCGI than it was in mod_python.  Just me, right?


Thanks... any answers to any questions are appreciated.  :D

I would strongly encourage you to use mod_wsgi instead of either mod_python or FastCGI.  It's fast and very easy to use (it took me about 30 minutes to set up and integrate with a web app that was running under mod-python before).  

As for writing web apps in python - writing the app in pure python is a lot of work, and not very convenient, but [Django]("https://www.djangoproject.com/") is amazing.  Many major websites are written in Django, it is scalable, easy to write in, and has modules to do anything you can think of.  It's a pure python module - you can import the parts you need and run the code directly in the interpreter.  Errors appear on the website directly (as long as a debug flag is sent, otherwise you get email updates).

If you want an example of what you can do easily in Django let me plug [the site I wrote using Django]("http://bitcoinharbor.com/") =).

Here's [a good starting point]("https://docs.djangoproject.com/en/dev/howto/deployment/modwsgi/") for Django+mod_wsgi development

---

### Post by juancarlospaco on 2011-08-03
1) Yes
2) [http://ninja-ide.org/](http://ninja-ide.org/)
3) I dunno, i dont need Apache
4) I dunno, i dont need Apache or lighttpd
5) I dunno, i dont need Apache
6) I dunno, i dont need Apache

I use this [http://bottlepy.org/](http://bottlepy.org/) like this [http://www.youtube.com/watch?v=vfzz36Hbetg](http://www.youtube.com/watch?v=vfzz36Hbetg)

---

### Post by mendhak on 2011-08-04
Thanks for your advice, everyone.  I had a look at Django and it seems to be popular and has good documentation.  I also see that it has its own web server, which lets me write the app first and worry about the deployment configuration later.  Thanks again!

---

### Post by MicahCarrick on 2011-09-10
1) Yep. I've been a PHP developer for 10+ years and have been moving more and more towards Django over the last few. I'm not alone in this.

2) Everybody has a different favorite. Personally, I love Gedit (the GNOME text editor). I wrote a plugin specifically for working with Django. You can see a quick screencast video here: [_Django Project Plugin for Gedit 3_](http://www.micahcarrick.com/django-project-gedit-plugin.html) Pair that with any other plugins you like for development, such as  [_gedit-source-code-browser_](https://github.com/Quixotix/gedit-source-code-browser) and the [_gmate project_]("https://github.com/gmate/gmate")

3) I actually left hostgator (well, I still use them for PHP projects) for this reason. I went with Slicehost so I can really fine-tune my Django sites. I use Nginx as a proxy to Apache with mod_wsgi as recommended by Django devs. There are plenty of arctiles on how to set that all up.

4, 5, and 6) No clue.

---

### Post by Pynalysis on 2011-10-08
> **mendhak said:**
> Hi, I've just started learning Python and am interested in web development with it.  So, a few questions

1)  Websites in Python - is it common?  

2)  What IDEs would you use for this?

After a lot of reading, it appears that everyone would rather have me use FastCGI instead of mod_python.  However, documentation and examples are sparse!  [This]("http://www.electricmonk.nl/docs/apache_fastcgi_python/apache_fastcgi_python.html") was the only guide I had to get it up and running.    


3) So is Python with FastCGI common or mod_python?  I'm forcing myself to go FastCGI because I plan to host on hostgator.com and they don't do mod_python.  They do FastCGI and Apache2.  Please tell me if I should pick a better option in terms of hosting or something other than Apache2.

4)  Hypothetically speaking - if I were to use lighttpd+fastcgi and write a python script, would it work if I deployed to an Apache2+fastcgi environment?  

5) I noticed that in 'regular' mod_python, errors show up on the web page itself, very useful.  But in fastcgi, I just get an 'internal server error' and I have to go into the apache error logs to see what the error was.  Is there an easier way to debug Python with fastcgi?  I'd rather not do this via the commandline because I want to 'see' the rendered output.  

6)  It might just be me... but I've got a Python script which I originally wrote for mod_python.  I then 'converted' it to use FastCGI.  But I've noticed that the script is slower in FastCGI than it was in mod_python.  Just me, right?


Thanks... any answers to any questions are appreciated.  :D

Additional answer:

2)  What IDEs would you use for this?
Eclispe with PyDev plugin for rapid development with Python/Django,

---

