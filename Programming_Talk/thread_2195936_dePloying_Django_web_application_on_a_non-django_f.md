---
title: "dePloying Django web application on a non-django friendly linux host."
date: 2013-12-27
forum: Programming Talk
---

### Post by mosalem on 2013-12-27
I need to deploy a web application based on Django framework on a non-django-friendly shared host.
By the word Non-Django-Friendly, I mean as follows:
[LIST]
[*]no SSH access
[*]no django Installed in the Python path
[*]no mod_wsgi for the apache web server
[*]just mod_python and mod_proxy for the Apache webserver
[/LIST]
What I have achieved till now is as follows:
[LIST]
[*]develop the web application on another dev platform so I don't need an ssh for django commands offered by manage.py for the project maintainance.
[*]adding django libraries within the web application path itself, so the application** works** and can access the framework needed libraries.
[/LIST]
What I **need to** achieve is : 
[LIST]
[*]adding mod_Python handler support to my web application in addition of the needed config for my .htaccess.
[*]:D Or any kind of hack with mod_proxy and .htaccess to pass the requests to my django wsgi :popcorn:.
[/LIST]
What I do **Not** need is :
[LIST]
[*]Any kind of alternative suggestions.
[/LIST]

I really appreciate your honored opinions.

---

