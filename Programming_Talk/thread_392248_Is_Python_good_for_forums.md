---
title: "Is Python good for forums?"
date: 2007-03-24
forum: Programming Talk
---

### Post by Zdravko on 2007-03-24
As I am going to build a forum in the Internet, I am concerned about the programming language, the forum system respectively. Is there a Forum in Python? Is it effective? Is it fast? Secure?
I will appreciate any suggestions or opinions.

Cheers!
Zdravko

---

### Post by Mirrorball on 2007-03-24
There is a forum for Django, a Python framework, but I can't find the site now. I don't know if it's good, but the most well known forum scripts are in PHP. I recommend vBulletin, but it costs $160. For free, I recommend punBB or Vanilla.

---

### Post by WiseElben on 2007-03-24
You probably won't find any full-featured Python based forum software because Python is quite new in the internet software world. PHPBB is an opensource and very mature PHP-based software.

I'm interested, why do you need a Python-based one? For integration with your main website?

---

### Post by Zdravko on 2007-03-24
No, I just want to be different and innovative.

---

### Post by pmasiar on 2007-03-24
> **Zdravko said:**
>  Is there a Forum in Python? Is it effective? Is it fast? Secure?

I am not aware about free forum package in Python. Django framework might be better suited for this kind of app - it was build as content management system. Ask at [http://djangoforums.org/](http://djangoforums.org/) 

I just noticed that  Mirrorball registered there - might it be our own  Mirrorball? :-)

Might be a good idea to start Python based Forums app. There are many PHP forums of different quality, so people opting for Python based forums might congregate around yours. Python and Django will lead naturally to separation of presentation and business logic (so called [Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) approach, which is cleaner and easier to update and maintain then average PHP code mixing presentation logic and code. Easier to maintain = more secure in long time.

Good luck!

---

### Post by Mirrorball on 2007-03-24
> **pmasiar said:**
> I just noticed that  Mirrorball registered there - might it be our own  Mirrorball? :-)
Our very own Mirrorball. I was trying to find the link to a Django forum app, it's called Mighty Board, I think. Instead I found that site and registered. :)

---

### Post by lnostdal on 2007-03-24
Probably one of the biggest forums of all is written in Python: [http://groups.google.com/](http://groups.google.com/) (a front-end to both "google-based" groups/forums and the standard USENET groups (huuge)).

---

### Post by pmasiar on 2007-03-26
Interesting and deep overview and comparision of leading Python web app frameworks:  Django, Pylons, TurboGears: [http://jesusphreak.infogami.com/blog/vrp1](http://jesusphreak.infogami.com/blog/vrp1)

---

