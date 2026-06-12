---
title: "questions about im applications.."
date: 2008-08-26
forum: Programming Talk
---

### Post by hockey97 on 2008-08-26
HI I am currently finishing up my website and would like to prepare for the next project.

I am going to try and make my own IM application. I want to know if I can have my application to connect to AIM and yahoo msn users so people on my im software can talk directly to others with other im software. 

If I can do so would you think it would be illegal to do so?? I am guessing I would need permissions from each IM software developer that I want to allow my users to connect.

I plan to make this IM a friendly IM software that can be installed on linux type OS'S and also windows and macs.

I also would like to know what is the best programming lango to use for such a project??

I was thinking python,  I code mostly in c and c++  but I did learn basics of pyhton I just and not that experienced with it yet.

I have heard python is more friendly meaning it can be used to create applications that can run on linux distr, and windows, and macs  OS'S

just would like any advice opinion, or any website that could help me understand more about IM applications and what I need to do to make a application that can be used with linux type and windows,macs type OS'S.

Thanks for your time.

---

### Post by CptPicard on 2008-08-26
Well, it should be easy to grab the source of either Kopete or Pidgin and get hacking. You can lift protocol implementations straight from there.

---

### Post by jinksys on 2008-08-26
> **hockey97 said:**
> HI I am currently finishing up my website and would like to prepare for the next project.

I am going to try and make my own IM application. I want to know if I can have my application to connect to AIM and yahoo msn users so people on my im software can talk directly to others with other im software. 

If I can do so would you think it would be illegal to do so?? I am guessing I would need permissions from each IM software developer that I want to allow my users to connect.

I plan to make this IM a friendly IM software that can be installed on linux type OS'S and also windows and macs.

I also would like to know what is the best programming lango to use for such a project??

I was thinking python,  I code mostly in c and c++  but I did learn basics of pyhton I just and not that experienced with it yet.

I have heard python is more friendly meaning it can be used to create applications that can run on linux distr, and windows, and macs  OS'S

just would like any advice opinion, or any website that could help me understand more about IM applications and what I need to do to make a application that can be used with linux type and windows,macs type OS'S.

Thanks for your time.

Ouch. My Brain.

Why would you think it to be illegal?  Gaim, trillian, kopete, et al have been doing it for years.

---

### Post by pmasiar on 2008-08-26
> **jinksys said:**
> Ouch. My Brain.

Ouch. My brain. :-)

Why you cannot as common courtesy to delete irrelevant quoted parts, so I can see to what part of the quoted post you answer?

---

### Post by themusicwave on 2008-08-26
I know with AIM you can use the OSCAR protocol.  It's actually a semi open protocol.  I am sure other clients have similar protocols available.

[OSCAR Protocol(Wikipedia)]("http://en.wikipedia.org/wiki/OSCAR_protocol")

Additionally, if you really want a challenge you can always try creating your own protocol.  I did it once in high school several years back.  We made our own very simple instant messenger it allowed you to chat with others on your buddy list by ip address.  You could send text messages and we eventually mad it so you could give yourself an alias instead of an IP.

It was a great way to get around the school firewalls and chat from computer lab to computer lab.  When my programming teacher caught us he told us good job and stop it.

---

### Post by Nemooo on 2008-08-26
Pidgin has a library called libpurple, which can be used for other IM applications. It's written in C, so you should be able to understand and/or edit it. Probably worth a look:

[http://developer.pidgin.im/wiki/WhatIsLibpurple](http://developer.pidgin.im/wiki/WhatIsLibpurple)

---

### Post by Nemooo on 2008-08-26
EDIT: Double post.

How do I delete my own posts?

---

### Post by jimi_hendrix on 2008-08-26
> **hockey97 said:**
> I also would like to know what is the best programming lango to use for such a project??

I was thinking python,  I code mostly in c and c++  but I did learn basics of pyhton I just and not that experienced with it yet.


just throwing this out there...ive heard msn messenger was coded in C# (logically...it is microsoft)

and i think (i havnt done it much) it is relatively easy to interface with the internet in C#

downside is im not sure how compatible it is and i doubt you would find source for it

---

### Post by Rome.konig on 2008-08-26
i like pidgin, works great for me. plus with hardy, it comes installed!

---

