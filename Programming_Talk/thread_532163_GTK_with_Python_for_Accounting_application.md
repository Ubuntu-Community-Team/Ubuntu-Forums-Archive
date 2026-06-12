---
title: "GTK with Python for Accounting application"
date: 2007-08-22
forum: Programming Talk
---

### Post by CostaRica on 2007-08-22
Has anyone done an accounting (invoice, bank accounts,etc) application with GTK+ with python?

I need to develop it because is has special requirements for an Optometrist (clinical history, etc) that can't be handled with a one-size-fits-all tinyERP application.  It needs to be connected to a MySQL database server in Linux over the web with four stores synchronizing data to this  server.

---

### Post by CostaRica on 2007-08-22
pmasier gave me the idea of TurboGears, but imo it is not aimed at the application I need to develop.  Am I wrong?

---

### Post by pmasiar on 2007-08-22
another idea I just found today: [http://www.satchmoproject.com/](http://www.satchmoproject.com/) open source online store based on Django. All is web technology, no GTK

---

### Post by scooper on 2007-08-22
Agree with the previous 2 posts that suggest making it a web app using something like Django or TurboGears.  Those tool kits help you with both the user interface and with data access, plus you only have to install to the server, not to each user's workstation.  Yes, you a few more UI options with non-web widgets, but there's not much you can't do anymore with web technology.

---

### Post by pmasiar on 2007-08-23
Well it is not obvious for me me web app is right way to go - OP must decide that.

Questions to consider:
- what kind of functionality user will expect? Web based apps are still less flexible than real desktop app.
- what is my infrastructure? Will it hold web-based app? 
- what are skills on my team, timeline, and budget? 
- do i want to learn web app technology: web server, AJAX, web app frameworks? Does it have market in your country within (pick your number) years?

It is quite possible, that good old fashioned wxPython is better GUI for you, even if Turbogears is better for me. YMMV, look before you leap.

**Edit**
I just found [this discussion](http://groups.google.com/group/comp.lang.python/msg/5452f49c591668cf) on python.org mailing list - interesting coincidence!

[whole thread](http://groups.google.com/group/comp.lang.python/browse_thread/thread/1f823a9c8a41c8bb) is interesting reading: quite strong arguments **against** web-base apps, and for new, modern Tkinter modules. Well, i guess not all people do web apps for living like i do! :-)

---

