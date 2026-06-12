---
title: "Django or CherryPy?"
date: 2008-07-08
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-07-08
Hi,

I'm new to python and trying to implement a client based application in python. I need a web based and stand alone applications as clients that can communicate with the server. I'm going to use python for developing the entire project. I'm going to use wxPython library for the stand alone application.

I'm wondering which of Django or cherryPy frameworks are more suitable for me. I'm looking for an easy to learn framework and I want two clients share most of their code other than the user interface one. I know that Django is an MVC based framework but I'm not sure if it is easy to use wxPython in it. 

I will really appreciate if you share your thoughts about it with me,

---

### Post by babacan on 2008-07-08
let the Django versus TurboGears war begin!

---

### Post by loell on 2008-07-08
cherrypy is an "http framework" while django is mostly identified as  "web framework" , so how can you compare apples to oranges?

and no even turbogears is base on pylons.


or maybe you're just looking for **python's Twisted framework**

---

### Post by pmasiar on 2008-07-08
1: aiming for both web-based and desktop client/server app, you double amount of work you have to do. Choose one: web based is likely better choice, if you can deal with non-desktop behavior of application in browser. With some AJAX, web app will be more desktop-like.

2: OP, you are comparing apples to oranges, as loell said. Why: CherryPy is web server, while Django supports web application front-to-end: it provides object-relational mapper, template, session management, automagically generates DB schema and all CRUD screens, and more.

3: Django vs Turbogears war is not going to erupt, because OP (as a beginner) is obvious prime candidate for Django. Turbogears will be there when OP outgrows limits of Django :-)

4: OP: if you are experienced programmer just beginning with Python, then Turbogears might be better choice, because it gives you more control over your app. Ask experts on TG mailing list about dual mode with web and desktop integration.

---

### Post by mohtasham1983 on 2008-07-09
> **pmasiar said:**
> 1: aiming for both web-based and desktop client/server app, you double amount of work you have to do. Choose one: web based is likely better choice, if you can deal with non-desktop behavior of application in browser. With some AJAX, web app will be more desktop-like.


Basically, I need a VoIP stand alone application. I don't think that I can create use AJAX for that. Even if I do it using AJAX, server load will be heavy.

---

### Post by pmasiar on 2008-07-09
VOIP? Then you don't need web based app in traditional sense (browser fetching HTMP pages from a server). You need desktop client talking to server over IP, but that would not be web server (not serving pages). You don't need neither Django nor CherryPy, IMHO.

It's not my area but I know there are plenty of frameworks (like twisted) and probably whole FOSS stack: client + server.

---

### Post by mohtasham1983 on 2008-07-09
As I said earlier, my client server based application has to have a stand alone and a web based application. VoIP is not the only type of service it's going to provide. Actually, VoIP is the only service that the web based client is not capable of doing. 

I am planning to use twisted for the VoIP part. However, I wanted to share some code with the web based application. Things like log in system, displaying friends, etc.

---

### Post by ramayer on 2009-10-06
Both! :P

You can run Django on to of CherryPy.

---

### Post by Can+~ on 2009-10-06
> **ramayer said:**
> Both! :P

You can run Django on to of CherryPy.

And I thought that Eternal September ended.

Oh well..

---

