---
title: "db related advice"
date: 2007-09-03
forum: Programming Talk
---

### Post by neorou on 2007-09-03
Hi people...
I've been working with php now for about 4 to 5 years doing web delivered database applications. The work I've done wasn't continuous so I am not a 100% programmer. I do lots of hardware and desktop support and am trying to move away from it because it is a big source of aggravation.

Recently I picked a couple of books on python and slowly I am learning how to script in Python. Eventually I would like to create custom-tailored database management for the desktop, using sqlite and postgresql. I wanted to continue using MySQL but they closed their source, and now I am hesitant to use them because of that.

I've been a long time Mac user and just recently started developing in Linux. So far I would say I love it, as there are many choices. Therein lies the problem.

Ubuntu has been great for me as I've been able to try out new database plug-ins and libraries with little trouble. When it comes to choosing a GUI that can be ported easily to Macs and Windows I don't know which is the better platform, TKinter or WxWidgets. It seems that if I create things in Ubuntu, since it is GTK based, I should use PyGTK. But then, I would have to recreate the interfaces again in Macs using something else, or I guess I could use the GTK libraries for Windows which have become available.

Normally, I could care less about the GUIs for the other OS's and stick to developing for linux, but since it's a Windows world out there, and I work for Mac freaks, I should at least find out if I have a relatively easy way of bridging the gap.

Anyway, I'd prefer to plan this out before just picking one and discovering later that I need to use something else. I'm at a career cross-roads and I don't have lots of time to investigate and play around on my own.
Any Python developers out there with advice?

With many thanks in advance.:confused:

---

### Post by nanotube on 2007-09-03
well... it /is/ possible to do what you want. :)
one thing i'd say is to concentrate on doing your database interaction layer in a db-independent way, so that your code will be easily extended to administer any db. 

also, look around and see if there isn't some already-existing projects that do some of what you want, so that you don't have to start from scratch (unless you want to).

---

### Post by neorou on 2007-09-03
Thanks, Nanotube.

Part of the reason why I want to do this is so 'I can' build things from scratch. 

I guess that would mean having to spend the time playing with everything. Maybe I can stop sleeping or something:)

---

### Post by pmasiar on 2007-09-03
> **neorou said:**
> doing web delivered database applications. ... create custom-tailored database management for the desktop, using sqlite and postgresql. 

Great, web-based DB app in Python is something I do, let's check details:

So which one is it, desktop or web-based? For web based app, Django and TurboGears are leading frameworks. Desktop is completely different, people expect more functionality, and many ppl use wxPython. I cannot tell from personal experience, I do web apps. :-)

> I wanted to continue using MySQL but they closed their source, and now I am hesitant to use them because of that.

I think it is misunderstanding. Code is GPL, so if they will try to pull it, someone will fork. IIUC what that did is to have security fixes send to paying customers first, some misunderstood Fedora/RedHat split. And it is of course stupid, community would test them patches for free, and they soon will realize that. So I would not lose sleep about that.

> which is the better platform, TKinter or WxWidgets. 

wxWidgets are designed to look native.

---

### Post by neorou on 2007-09-04
> **pmasiar said:**
> Great, web-based DB app in Python is something I do, let's check details:

So which one is it, desktop or web-based? For web based app, Django and TurboGears are leading frameworks.

I am not familiar with either of these - I guess that's more for me to look into. I was actually referring to desktop solutions. 

> **pmasiar said:**
> 
I think it is misunderstanding. Code is GPL, so if they will try to pull it, someone will fork. IIUC what that did is to have security fixes send to paying customers first, some misunderstood Fedora/RedHat split. And it is of course stupid, community would test them patches for free, and they soon will realize that. So I would not lose sleep about that.


I hope that is the case. It's a shame to stop using it since it has been widely used since it's inception. Anyway, it doesn't hurt to start playing with the competition.:)

> **pmasiar said:**
> 
> which is the better platform, TKinter or WxWidgets. 
wxWidgets are designed to look native.

It seems more people prefer WxWidgets. That is the one that is at the top of my list. There is support for it both on Windows and Mac OS. I am not familiar to what extent though...I guess I will have to cross that bridge when I get to it.

Thanks for your advice.

---

### Post by pmasiar on 2007-09-04
> **neorou said:**
> I was actually referring to desktop solutions.

But your PHP was web-based, not desktop.
Here is the difference:
web-based: more clunky, restricted by browser quirks, less control by programmer about how application looks like, and if you want half of capabilities which desktop has, you need to dive deeply into javascript - and still user can kill your efforts by opening new window or clicking "back" when you did not expected. So why people do that? One word: ease of deployment! All deployment is on the server, nothing on client, upgrading is instant.

Desktop: flexibility and full control, but deployment is pain.

Chose your poison :-)

---

### Post by neorou on 2007-09-04
> **pmasiar said:**
> But your PHP was web-based, not desktop.
Here is the difference:
web-based: more clunky, restricted by browser quirks, less control by programmer about how application looks like, and if you want half of capabilities which desktop has, you need to dive deeply into javascript - and still user can kill your efforts by opening new window or clicking "back" when you did not expected. So why people do that? One word: ease of deployment! All deployment is on the server, nothing on client, upgrading is instant.

Desktop: flexibility and full control, but deployment is pain.

Chose your poison :-)

Yeah. You are right and I agree with you about how much better web-based solutions are in terms of deployment and ease of upgrades and overall use. 

Unfortunately, I would like to have a table full of poisons, not just one. ;)

I would like to be able to create fairly simple desktop applications. This sort of solution is necessary in some cases, where we don't always want to store all the data in the same place and also to be able to collaborate without having to share 'all' of the data on a single SQL-like server.

Being able to create desktop solutions is also another skill to add to my arsenal. To me, THAT is always a good thing.

Thanks for your opinion.

---

### Post by neorou on 2007-09-04
> **pmasiar said:**
> So which one is it, desktop or web-based? For web based app, Django and TurboGears are leading frameworks. .

By the way, this is not why I posted this question, but since you mentioned it Pmasiar, I checked out both Django and TurboGears, and so far both are very impressive, but TurboGears seem to be more attractive to me.

Cool...

---

### Post by pmasiar on 2007-09-04
> **neorou said:**
> I would like to have a table full of poisons, not just one. ;)

Good choice. Then you **always** have something tasty for your [lusers](http://en.wikipedia.org/wiki/Luser) :-)

> I would like to be able to create fairly simple desktop applications. This sort of solution is necessary... 

Absolutely, you don't have to prove it to me.

For extremely simple GUI, take look at EasyGUI. It is so simple it does not even have events. Just fancy GUI input, plain and easy :-)

---

