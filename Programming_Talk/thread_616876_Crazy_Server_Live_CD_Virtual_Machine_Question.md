---
title: "Crazy Server Live CD Virtual Machine Question"
date: 2007-11-18
forum: Programming Talk
---

### Post by SuperMike on 2007-11-18
I have a crazy question because I don't know how to put it to words exactly.

You see, I've written an Apache/PHP/PostgreSQL web app, but now want to use a unique way of distributing it. The technique must be:

* The user boots into something and does not run commands, or runs very few commands.

* Even newbies to Linux can boot it.

* It needs to be a popular platform that most of the developers will use.

* It needs to not harm their hard drive that much -- just create some directories or files in an existing partition. (The hard drive will have to be an EXT3 system with available disk space.)

* On a reboot, it needs to remember the admin's settings.

I've thought about using a Live Server CD, or using a Virtual Machine in this new JeOS platform. 

**Which of those two would you recommend?** I'm nervous about using JeOS because I don't want to require that the user know how to install a VM -- I need something that does it for them.

[B]Has anyone started a project very similar to this that I could download and insert my web app into?
[/B]

---

### Post by LaRoza on 2007-11-18
[http://lamppix.tinowagner.com/](http://lamppix.tinowagner.com/)

If that is not exactly what you want, you can use: XAMPP Portable for running your server on any Windows PC with a flash drive. [http://portableapps.com/apps/development/xampp](http://portableapps.com/apps/development/xampp)

The link in my sig will give you a live cd list (among other things) which can peruse.

-EDIT XAMPP would have been perfect, but uses MySQL.

---

