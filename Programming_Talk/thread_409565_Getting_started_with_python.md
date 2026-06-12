---
title: "Getting started with python"
date: 2007-04-14
forum: Programming Talk
---

### Post by hellothere55 on 2007-04-14
Hello, after reading some of the book Programming Python it seems that python is something I would like to delve deeper into.  The only thing is, I have no idea what I should try and write.  So I was hoping that someone here could help point me to a group/program that would be a good starting place for a person with limited python knowledge, but that is willing to learn whatever is necessary.  I'm hoping that with a goal I can start to learn python instead of just playing around with it.  Thanks.

---

### Post by pmasiar on 2007-04-14
[http://learnPython.pbwiki.com/](http://learnPython.pbwiki.com/) - online books about Python syntax, data structures, tasks to solve. Good luck!

---

### Post by rmemm on 2007-04-14
I don't think I have an answer for your exact question.

You might want to check out comp.lang.python Usenet new group.  You can access that via a news reader (like Pan or the news featcher of Mozilla Thunderbird)  or you can use Google "Groups" which is essentially a web based usenet gateway.  I mention this because this is the official python internet forum and is very popular.

Other thing I would say -- welcome -- python is wonderful -- I use it at work all the time.

Rob

---

### Post by sas on 2007-04-14
> **hellothere55 said:**
> Hello, after reading some of the book Programming Python it seems that python is something I would like to delve deeper into.  The only thing is, I have no idea what I should try and write.  So I was hoping that someone here could help point me to a group/program that would be a good starting place for a person with limited python knowledge, but that is willing to learn whatever is necessary.  I'm hoping that with a goal I can start to learn python instead of just playing around with it.  Thanks.

Usually in open source it works by you choosing what you want to work on. It's probably best to start small - maybe you can write a python program to automate a task that you have to do, maybe you could write a plug-in for something like deskbar-applet or gedit, maybe you can fix a bug in an application that you suffer from.

You could always search for "gnomelove" bugs on bugzilla.gnome.org and look for applications implemented in python.

It takes a sort of mental shift to get from "I know python syntax", to actually going and writing something. It took me a while (not that I've done much)

---

### Post by hellothere55 on 2007-04-14
Thanks for the heads up to the news group, I had forgotten about that.  And thanks for the welcome.  After listening to the FLOSS Weekly podcast on python I decided to start looking into it and I'm very glad I have so far, much easier than php.

---

### Post by rmemm on 2007-04-14
If your into web stuff -- the python way is zope and plone.  I also think twisted is in python (??).  I use plone which is a zope based cms for some things at work.  There's certainly a lot of work to do on plone plugins if there's something that interests you.

I do agree with the other comments though -- maybe start on something small that interests you -- and there's always working on testing and bug fixes.

Rob

---

### Post by hellothere55 on 2007-04-14
I'd write something, it's just that I don't know what I want to write or accomplish.  Which was why I put this question seeing if anyone knows of a project that would be good for a beginner to join, even if it was only for reading the source code at the start to see how things work and start to understand python better.

---

### Post by rmemm on 2007-04-14
What comes to mind for projects -- OpenOffice.org has a python interface and some people working on this and one can write plugins in python for OO I think.  The Gnome idea was a good one.  Plone which I mentioned -- there are many many python related thing.  You could search freshmeat.net for python code and check out those projects.  I think you can search freshmeat by language.  The FSF and savannah.gnu.org have task lists which request help from people -- some of these are in python usually.  Probably sourceforge.net has the same thing.  There is a team at enthought.com that's working on a windows distribution and the support and develop scientific tools for windows and linux in python.  You could use synaptic to see what packages depend on python and which packages that are python libraries and start from there -- for every ubuntu package you can download the source -- to see the python code.

Any way -- just some ideas.

Other thing I would decide -- what general type of project.  Python has very wide application range -- by that I mean:  (a) applications, (b) scripting (os and applicaiton scripts and plugins), (c) web.  These are quite distinct things.  

Sorry, no specific recommendations.

Rob

---

### Post by hellothere55 on 2007-04-14
Its no big deal about the specific recommendations, you pointed me to places that will give specific projects.  But I put this on the comp.lang.python forum as well and it seems like this has some kind of interest as someone else commented that they would like to know as well.  But I think I'm going to have to start scouring freshmeat and sourceforge.  

And isn't it if the package is python, the source code is already viewable since you don't compile?

Thanks for the links.

---

### Post by pmasiar on 2007-04-14
I almost forgot: [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) is place to start and have fun. Series of puzzles, solved by Python, with forums and hnts for every level.

---

### Post by rmemm on 2007-04-14
Regarding python not compiled -- yes that's true generally -- I wasn't thinking.  

There are python to exe builders for windows which do a kind of distribution packaging which would make viewing code annoying without the source.  And I'm not certain it has to be distributed as source in general -- but for open source stuff on Linux it probably is almost always that way.

Rob

---

### Post by pmasiar on 2007-04-14
> **rmemm said:**
> If your into web stuff -- the python way is zope and plone.

I do not want to go into [web framework comparision](http://www.djangoproject.com/weblog/2006/dec/06/comparisons/) but zope as THE web python way? Django was pronounced, TurboGears is next competitor, Pylon is close third, about dozen of also-runs, all before zope. Zope is way more complex. And simplest way to try web apps is not even Django and certainly not zope: plain old CGI with simple server is best to get your feet wet, see [http://LearnPython.pbwiki.com/WebApplication](http://LearnPython.pbwiki.com/WebApplication)

> I use plone which is a zope based cms for some things at work.  There's certainly a lot of work to do on plone plugins if there's something that interests you.

Do you just use zope - or do you really write plugins? Because if you really do, I would be awed. I heard that couple of projects started with just part of zope (because authors claimed zope is too complex to hack).

---

### Post by rmemm on 2007-04-14
Sorry, have not heard of the others -- though happy to -- do you have any personal recommendation?

Regarding plone/zope--as a rough metric of popularity I often use freshmeat popularity:

Plone=6.96
Zope=5.65
Django=not in database
TurboGears=0.26
Pylon=0.09

My point -- at least by these numbers plone and zope are way ahead.  Do you have other information?  

Rob

---

### Post by pmasiar on 2007-04-14
> **rmemm said:**
> Regarding plone/zope--as a rough metric of popularity I often use freshmeat popularity:

No idea how the "popularity" is measured - any links? Or at least URL where you got the results?

You can dig many comparisons with Google, random sample: [Django](http://www.pythonthreads.com/articles/interviews/django-shines-when-it-comes-to-developing-content-oriented-web-sites.html) - [Guido pronounced Django](http://www.oreillynet.com/onlamp/blog/2006/08/guido_blesses_django_django_an.html).

Seems that TurboGears lost because [Guido dislike XML](http://www.artima.com/weblogs/viewpost.jsp?thread=146647). I hate overuse of XML as bad as next guy, but I learned that using XML in kid's templates is *really, really cool* and I really like it - because if is perfect XML, you can view your page design as kid template without any data! And template language is Python - how cool is that.

---

### Post by rmemm on 2007-04-14
[www.freshmeat.net](www.freshmeat.net) - I love this site.

I would be the first to say that popularity is very rough and I don't know how they calculate it.  It also probably tends to overweight older items that were popular in the past -- because new cool software takes time to build massive popularity. 

Zope and Plone were pretty popular at one time and probably still are quite popular -- but I do think they've lost momentum -- especially with the zope2->zope3 transition etc.

Linux for example was unknown at one time.

Anyway -- I'll have to take a look at your recommendations.  I'm always interested in new python things.

Rob

---

### Post by pmasiar on 2007-04-15
well, url to freshemeat homepage is obvious - google knows that much. URL to the "popularity" numbers you mentioned? I tried but did not get any meaningfull results from freshmeat search facility.

Looks like turbogears added some plugins to freshmeat, Django, as more self-contained, did not bother...

---

### Post by cisforcojo on 2007-04-15
I second the pythonchallenge recommendation. I am doing it now and am hooked. (Using it to start learning Python and it's a GREAT tool. I didn't even know how to write a for loop in python when I started and now I'm doing jpeg manipulation) faaaaaaaaaaaaaaaaaaantastic!

---

### Post by manjunath on 2008-10-01
Use full link for you..

[http://www.python.org/dev/process/](http://www.python.org/dev/process/)

--Manju

---

