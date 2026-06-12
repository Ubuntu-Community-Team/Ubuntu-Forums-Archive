---
title: "Making it in Open Source Software"
date: 2007-10-10
forum: Programming Talk
---

### Post by farruinn on 2007-10-10
Hi,

I'm a... fledgling computer scientist. I think I'd like to be a programmer.  Get paid for solving problems and writing code, that sort of thing.  What I'd like to know is, obviously open source software is used in a wide variety of commercial applications but how many opportunities are there to create open source software **and** money at the same time?

[THREAD=302809]This thread[/THREAD] has some interesting opinions on it, but I can't discern that many of them are held by actual professionals. Sure there are your Canonicals and Redhats of the world, and even some corporations like Apple, Sun, and IBM are supporting open source to a certain extent. Are they really committing to open source though or just paying lip service and treating it as extra-curricular?

Do you think businesses will ever evolve to the point of making the majority of their software open source? Is that even the goal of the open source movement?

---

### Post by dwhitney67 on 2007-10-10
If you are looking to make money with OSS, then the only way to do so is to make money by issuing run-time licenses for your product or provide service support (that's what Red Hat does).  The source code can be made available to all who wish to see it, but you still "own" whatever you create with your blood/sweat/tears.

If you really want to make lots of money, then OSS is probably not your best bet.  Why not just write proprietary software for a company that uses OSS as the backbone for their application.  That's what I do.

If you want to see all of the OSS I use on my project, I will cheerfully post a location where you can get it.  If you want to see the proprietary code, then you are out of luck; that I cannot share.

---

### Post by pmasiar on 2007-10-11
If you want to make a lots of money, don't waste time working for someone else: start your own startup, and get rich by IPO or buyout :-) Exhibit A: YouTube :-)

We had couple threads in last 2 months about making living using free software. But if you want just work for someone, most companies use lots of non-free software, so you cannot limit yourself.

What is your education? What are of programming you want to go into: apps? embedded? Systems? Drivers? It is hard to help you to get there if we don't have idea where you want to go... :-)

Yes, many companies (also HP, even Microsoft with IronPython recently, and hundreds of smaller players) do pay people to work on free software projects. Google is famous in that: 20% of your time can go on any project you want, including free software.

No, companies like Google or Microsoft will never make majority of code they write free - they cannot: this is capitalism, and CEO has fiduciary duty to look for interests of shareholders first, general public as distant second.

Many new companies use GPL code as a trick to get market share: ie in ERP niche, new players are companies who sell customizations to code GPL code.

---

### Post by pmasiar on 2007-10-11
> **dwhitney67 said:**
> If you are looking to make money with OSS, then the only way to do so is to make money by issuing run-time licenses for your product or provide service support 

Not true. There are many more business models:
- Good old ads. Firefox is being paid by Google for having Google as homepage.
- Customizations on top of core system: TinyERP, Sun's Office
- use FOSS as loss leader/advertisement to get contract work: TRAC, Turbogears
- government grants: Python was in part developed by that
- companies pay for sprints focusing on areas they need, like "need for speed" sprint for Python, paid by Eve Online game company
etc etc. Dual license and support services are just most widely used now.

---

### Post by SuperDuck on 2007-10-11
I found this on the Damn Small Linux home page.  It's an interesting read.  I don't know how much you'll get out of it, but it's first-hand experience from someone who's actually living what they're talking about.  

[http://damnsmalllinux.org/income-guide/](http://damnsmalllinux.org/income-guide/)

Best of luck,
Michael

---

### Post by CptPicard on 2007-10-11
> **farruinn said:**
> 
Get paid for solving problems and writing code, that sort of thing.

The first sentence contains your key operative words right there. :)

You get paid for solving people's problems, not just typing up code and selling licenses. You are going to benefit from FOSS exactly because you get all the tools in the world for free, and because your value proposition is in your problem-solving and not coding skills (which everyone has these days), you can participate in the FOSS tool/library development process without worrying too much about giving your work "away for free". The stuff gets better in general and you're the specialist who knows it inside and out, so you've got yourself covered.

Try to become a decent computer scientist so that you have the capacity to work independently on problems you're facing. Then, find some niche you can specialize into. Find your clients and take good care of their needs and they take care of yours.

Of course, if you do write something that genuinely contains some trade secrets, you don't need to give that away. But it is my impression that 95% of your code is generic. For example, one of my projects solves certain problems by using well-known algorithms, which still require some knowledge to apply... and of course, a secret set of magical numbers I'm not sharing. :p

---

### Post by RyanZec on 2007-10-11
if you want to make money programming, Open Source is not the way to go, grant you, you can make alot fo money if you create a site that does make very popular and you keep expanding on this(i mean 2 guys who started Google made over 4 Billion dollars buy sell thier shares in the company).  

I think that it depends on what you are making.  For instance i am designing a build a PHP API.  Now not only are thier already many out there already, I like project like this are very good for Open Source.  I will be releasing the API under the MIT AND GPL license.  I am also developing a Project management system(my work is based off on Sugar CRM as far as a design stand point) but this i will not be release under open source.  The reason i would release the first project is becuase it is filled with code that is designed to handle issue the other code is freely available to handle the same problems and it is designed to issue the a gerenal and not something specific.  The reason i would not release the second project is becuase is it designed to do something very specific and ther are few options available our there and some of my feature in the second don't exist as far as i know and i think i handle the other comman project management software tasks better(else why would i build it).   

That my 2 cents.

---

### Post by ssam on 2007-10-12
writing open source code will not stop a big proprietry company trying to hire you.

random example:
[http://en.wikipedia.org/wiki/Daniel_Robbins_%28Gentoo_Linux_founder%29](http://en.wikipedia.org/wiki/Daniel_Robbins_%28Gentoo_Linux_founder%29)
[http://esr.ibiblio.org/?p=208](http://esr.ibiblio.org/?p=208)

it will be much easier to show a prospective employer the programming you have done in the past if it is publicly available code.

there is also a chance that you will get hired by an open source friendly company.
[http://www.desktoplinux.com/news/NS7924011302.html](http://www.desktoplinux.com/news/NS7924011302.html)
[http://ianmurdock.com/2007/03/19/joining-sun/](http://ianmurdock.com/2007/03/19/joining-sun/)

also an interview with chris dibona from google (it was on yesterdays lwn, so if you are not a subscriber you will need to wait a week to read it)
[http://lwn.net/Articles/253173/](http://lwn.net/Articles/253173/)

---

### Post by dwhitney67 on 2007-10-12
> **SuperDuck said:**
> I found this on the Damn Small Linux home page.  It's an interesting read.  I don't know how much you'll get out of it, but it's first-hand experience from someone who's actually living what they're talking about.  

[http://damnsmalllinux.org/income-guide/](http://damnsmalllinux.org/income-guide/)

Best of luck,
Michael
DSL is not "small" enough.  Why do they include browsers and other crap.  A small Linux distro should boot to a login prompt, or better a shell prompt.

---

### Post by pmasiar on 2007-10-12
> **CptPicard said:**
> You get paid for solving people's problems, not just typing up code and selling licenses.

+1

If you are solving YOUR OWN problems using free/open source software, you are NOT going to get paid. If you are solving SOMEONE ELSE (WITH MONEY) problems, in many cases they will not care what platform do you use, just do it.

---

### Post by cwaldbieser on 2007-10-13
> **dwhitney67 said:**
> DSL is not "small" enough.  Why do they include browsers and other crap.  A small Linux distro should boot to a login prompt, or better a shell prompt.

If you really want somwthing small:
[http://www.toms.net/rb/]("http://www.toms.net/rb/")

I like DSL because I can get it to work on the old junk computers they give away at work.  I can pop a cheap wireless card and a DSL CD in on and have an Internet ready computer on every floor of my home.

---

