---
title: "project development in a group"
date: 2008-08-03
forum: Programming Talk
---

### Post by dexter.deepak on 2008-08-03
this question is very much related to how open-source development works.

for the first time i am involved in a group project, involving 4 members.
this is basically a web-based project (using JSP).
all the members are residing in different hostels but are under the same local-network of our college.

so, i am looking for a better way of communicate with each other and integrate our project in an efficient manner.

i have heard things like "CVS" and "BAZAAR", and i feel like these stuff are going to help me here, but since i have never used them (nor anyone in my surroundings), i wonder if its my piece of cake.

any other solution is also appreciated.

---

### Post by bobbocanfly on 2008-08-03
The best way to communicate in a smaller group I find is via IRC. Get a channel on freenode (if its opensource) and you can just ping your other devs when you need them.
[URL="http://en.wikipedia.org/wiki/Version_control"]
Version Control[/URL] (CVS/BZR) lets you keep track of changes made to your source tree and is almost essential if you are working in a group. I'd recommend bzr for this as it is easy to pick up once you get started and getting help is very easy on freenode.

---

### Post by dexter.deepak on 2008-08-03
we want to avoid interacting over the internet, as we face frequent internet failures....we just want to stick to the local network.
wont bzr serve the purpose ?

irc is a communication tool over the internet, is there some similar tool for people to contact on a local network ?

---

### Post by pmasiar on 2008-08-03
Do you plan to have central code repository? Subversion is more modern than CVS, but ask if IT or CompSci don't provide some (any) repository, and use that. If not, consider Google Code or Sourceforge.

Because you are close, consider weekly meetings, face-to-face is hard to replace by technology. Getting email list should be easy (either university IT, or Google Groups). Running local IRC server is little harder.

---

### Post by tinny on 2008-08-03
> **pmasiar said:**
> Do you plan to have central code repository? Subversion is more modern than CVS, but ask if IT or CompSci don't provide some (any) repository, and use that. If not, consider Google Code or Sourceforge.

Because you are close, consider weekly meetings, face-to-face is hard to replace by technology. Getting email list should be easy (either university IT, or Google Groups). Running local IRC server is little harder.
If your project is open source then go with a solution like source forge or google code. Otherwise Id advice that you set up a virtual development server (a VMWare server image running [subversion]("https://help.ubuntu.com/8.04/serverguide/C/subversion.html")).

(I have a VMWare image you can have that has Ubuntu server, Subverion, MySQL and Open ssh all setup if you want it? Just PM me)

Also as pmasiar has suggested, do face-to-face meetings! There is nothing like face-to-face human communication, something that is unfortunately avoided by a lot of software developers.

---

### Post by xelapond on 2008-08-03
Why does it have to be a central server?  Wouldn't a distributed model work better?  In their setup, it does not sound as if a server is viable, so with something like git they could work on their own branch, then merge when something works.  I know their are LAN chat programs, I can't name any off the top of my head though.  You could always use netcat:)

---

### Post by tinny on 2008-08-03
> **xelapond said:**
> Why does it have to be a central server?  Wouldn't a distributed model work better?  In their setup, it does not sound as if a server is viable, so with something like git they could work on their own branch, then merge when something works.  I know their are LAN chat programs, I can't name any off the top of my head though.  You could always use netcat:)

Yeah that is a good idea. A distributed model could work well for them.

---

### Post by hariprs on 2008-08-03
You can also try this Virtual office.
[http://officezilla.com/](http://officezilla.com/)

---

### Post by tinny on 2008-08-04
> **hariprs said:**
> You can also try this Virtual office.
[http://officezilla.com/](http://officezilla.com/)

[Google Apps]("http://www.google.com/a/help/intl/en/users/user_features.html") works well for this type of document based collaboration.

---

### Post by dexter.deepak on 2008-08-04
thanks a lot for all your replies...but still i feel all the solutions need an active internet connection, and thats what i avoid..i am looking for a lan based solution.
in that case, subversion seems to be a better option for me.

...and i dont understand what is a central / distributed code repo, as i told i am just learning to get onto these things:)

additionally, i forgot to mention, 2 of my team members are windows-user. though i can prompt them to linux, yet it would be better if they could work through windows.

---

### Post by tinny on 2008-08-04
> **dexter.deepak said:**
> 
...and i dont understand what is a central / distributed code repo, as i told i am just learning to get onto these things:)


**Centralized version control (E.g. Subversion):**

A classic client / server model.

**Distributed version control (E.g. Git):**

A peer to peer approach. Much like how peer to peer file sharing applications are structured. No server infrastructure is required.

In terms of what is best to learn, Id go with Subversion if I was you. In the open source world distributed version control is becoming more popular, however in the proprietary software world (where you will most likely be looking for a job in one day) centralized version control dominates.

---

### Post by hariprs on 2008-08-04
There are lots of free groupware solutions for Linux that can run in LAN, the phpgroupware is a free groupware solution similar to officezilla that i mentioned in my previous reply. Visit [www.phpgroupware.org](www.phpgroupware.org) and download the software.

---

