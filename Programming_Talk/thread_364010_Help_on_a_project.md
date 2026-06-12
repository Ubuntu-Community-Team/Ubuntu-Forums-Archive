---
title: "Help on a project"
date: 2007-02-17
forum: Programming Talk
---

### Post by orlox on 2007-02-17
Rigt now, I'm developing a telescope control system ([http://sourceforge.net/projects/tcsd/](http://sourceforge.net/projects/tcsd/)), and I'm looking for recomendations for a part of the application.

The program consists on a java program that runs as a daemon and communicates with the telescope on the server. There is a web GUI to access and control the daemon, that works using ajax.
The javaScript on the gui accesses php scripts that are located on the server. These php scripts connect to the daemon app through sockets. Then, the php script echoes the data received, so the javascript reads it...

I was wondering if there is a smarter way to do this...I believe java web services could be a choice, but can't figure how can the web services  access the data in the daemon application.

Any suggestions??

---

### Post by LordHunter317 on 2007-02-17
Either by running as part of the daemon application, by converting the daemon application to EJB session beans, or by the same manner as PHP does already.

As far as smarter, just make sure you do as much processing server-side as you can.  The less work you have to do in Javascript, generally the better off you are.

---

### Post by orlox on 2007-02-17
hadn't heard before of EJB session beams...guess I'll check on that. Thanx!

---

### Post by LordHunter317 on 2007-02-17
I was being a little tounge-in-cheek saying that.  For a developed solution, moving to EJBs isn't likely to save you anything.

---

