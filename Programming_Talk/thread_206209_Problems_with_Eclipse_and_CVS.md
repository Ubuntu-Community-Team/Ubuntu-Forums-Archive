---
title: "Problems with Eclipse and CVS"
date: 2006-06-29
forum: Programming Talk
---

### Post by tincup on 2006-06-29
Hi. I don't know if this is on-topic in here:


I'm trying to checkout CVS projects in Eclipse from an external server (with SSH access). Both ext and extssh methods do not work:

ext actually works but I have to enter the password again and again (around 10 times to checkout a project)

extssh does not work at all, i don't even get an error message.


Any ideas?

Regards,
 Tin

---

### Post by grimesp on 2006-08-29
I am having the same problem. Does anybody have a solution?

---

### Post by Blacktalon on 2006-08-29
Could you be little bit more specifice with the situation, are you trying to access Eclipse through ssh?  If this is the case I have had a similar problem until I realized something, that I couldn't view or do anything with it from another mechine cause it was working properly but it was being pulled up to the mechine that I was sshing to.  The only suggestion I can think of is since you obivously know where to ssh to, try ftping the program to your local mechine then (assuming you have eclipse on your local mechine) open it up there and view CVS from your local mechine.  This the best suggestion I can give you guys, I hope it helps.


~BT

---

### Post by curtisf14 on 2006-09-08
I believe I have found a solution (I had this same problem, and it was getting really annoying).  Take a look at [this post]("http://www.eclipseplugincentral.com/PNphpBB2-viewtopic-t-939.html"); you can see how to fix the problem.

Basically it has to do with where /etc/alternatives/java points to, and what is in the /etc/eclipse/java_home file.  Make sure /etc/alternatives/java points to the "java" program from Sun, not the GNU version, and make the corresponding change in /etc/eclipse/java_home.  Hope this helps!

---

