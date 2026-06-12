---
title: "Entering the World of Frameworks-Help with Website Development"
date: 2007-07-30
forum: Programming Talk
---

### Post by Dylnuge on 2007-07-30
Hello,

I have been working with website development for a year or so now, mainly designing my own website and also considering starting a business which designs website and software solutions for people (not exactly simple web design-more web apps then simple HTML).

I have a few people working with me who know a bit about design, but I am the sole programmer. Previously, I worked with PHP, mainly because my host only offered PHP or ASP(X), and I liked PHP better. However, I always wanted to try a framework like Ruby on Rails or Django. I am now able to get (or will soon be able to get) my own servers to host my site on. Since I can now install a framework, I am wondering what to consider.

I already know Python and a little PHP (I did not use it much). Would a Ruby or Perl based solution be worth learning the language? What are the advantages of using a Python framework over PHP? What are the advantages of Zope over Django, Django over TurboGears, vice versa, etc? I hate to directly ask the question of what is best, but I am looking for some advice.

Thanks,
Dylan

---

### Post by Note360 on 2007-07-30
Django looks good actually. Im using it abit for some basic stuff. PHP still makes more sense, but bc of Django MVC is beginning to make sense.

---

### Post by Dylnuge on 2007-07-30
Could you expand a bit? Why does PHP make more sense, and how does Django look good?

Thanks.

---

### Post by pmasiar on 2007-07-31
> **Dylnuge said:**
> I always wanted to try a framework like Ruby on Rails or Django. ...
I already know Python and a little PHP (I did not use it much). Would a Ruby or Perl based solution be worth learning the language? What are the advantages of using a Python framework over PHP? What are the advantages of Zope over Django, Django over TurboGears, vice versa, etc? 

Programmers add structure and design pattern to create better, higher quality solutions. Like realizing that GOTO makes for unmanageable programs. After structured and OOP paradigms, developers working on GUI established [ulr=http://en.wikipedia.org/wiki/Model-view-controller]Model-View-Controller[/url] design pattern. You really, really want to do GUI that way, trust me :-)

All popular frameworks you mentioned are MVC: RoR, TG and Django and about the same. PHP creates messy pages without MVC structure (although I am told it is possible to do MVC in PHP - only it is harder, and most people don't). Zope was good solution 5 years ago, but now it is overcomplicated - good for huge sites where you can develop your own custom structure.

Now, there are 4 mainstream so called "scripting" languages for quick app development. Perl was first, but stagnated 5 years ago - and is not readable, is rather quirky. PHP has that MVC problem. Ruby and RoR was first "rapid web app framework" which started the revolution. It gave big popularity boost to Ruby, Python 3 years ago had about 2 dozens web app frameworks with different levels of popularity (joke was that Python has more frameworks than reserved keywords), but none was dominant. Now Python catched up on Ruby, and arguably TG out-RoR Rails.

So basically you need to select between languages first. I prefer Python over Ruby, because IMHO Python has cleaner, more readable syntax, and bigger popularity == more libraries. If you choose Ruby, RoR is your framework. Python has now 2 leading frameworks: TurboGears and Django. They have different approach: Django was started sooner, and decided to develop all modules in-house and integrate then really well, so they work good together. 

Django was designed for newspaper-publishing kind of websites, where expert can create first version in hours (so redactors can start publishing articles) - and it will scale, it is not PHP.

TG was created as a front-to-back integration of best available modules for every task, so they integrate outside modules (and write glue code to let then work together). 

Django is best option, is you prefer what it does for you: it's goal is not flexibility in changing parts, it is a monolitic app. TG is little more work, but you have more freedom, bacause TG is more modular

Many more details from far better experts than me:

[http://www.google.com/search?q=django+turbogears+comparison](http://www.google.com/search?q=django+turbogears+comparison)

---

### Post by Dylnuge on 2007-07-31
Thanks.

I am going to download Django, TurboGears, and Pylons, and try all of them on the same task and see which I enjoy most. Google returned many conflicting results on which is best, so I will see for myself.

-Dylan

---

### Post by pmasiar on 2007-07-31
Pylons is different - it's goal is not front-to-end integration like Django or TurboGears.

---

### Post by Modred on 2007-07-31
> **pmasiar said:**
> So basically you need to select between languages first. I prefer Python over Ruby, because IMHO Python has cleaner, more readable syntax, and bigger popularity == more libraries. **If you choose Ruby, RoR is your framework.**

There's also [Nitro](http://www.nitroproject.org/).  It's not nearly as widespread as Rails, but probably the most notable site using it I know of is ruby-doc.org.  I can't speak to any advantages over Rails, as I haven't tried it out.

After hearing your comparison between Django and TG, I may give TG a try.  At least I can be reasonably certain that "integration" in a Python framework doesn't mean the same as it did with Catalyst, which was "fight with CPAN for hours and still not have a working install".

---

### Post by pmasiar on 2007-07-31
> **Modred said:**
> There's also [Nitro](http://www.nitroproject.org/).  It's not nearly as widespread as Rails, 

I always heard there is also "the other" Ruby framework but never knew the name. Now I know. :-)

People (pythonistas) did noticed that on software conferences, Python is often mentioned without web (as most of it's usage is outside of web apps. Guido famously said "he does not do web and does not care about the web apps" at Pycon 2005 - months before being hired by Google, and [his first task at Google](http://www.artima.com/weblogs/viewpost.jsp?thread=146149) was - you guessed it - web app :-) 

RoR was "the" rapid web framework back then in 2004, but since 2005, Python was gaining lost ground quickly.

> After hearing your comparison between Django and TG, I may give TG a try. 

Please do. I found that it's idea of integrating best-of-breed modules for every part, and creating front-to-back integration, is very .... unix-like. They created APIs so ie new templating systems can be used (hot-swap replace), new ORMs, etc. And module developers like it too, because it gives in exposure.

I am only beginning with TG (and should be doing it instead of answering post in forums :-) but I like the feel of it. And [widgets](http://docs.turbogears.org/1.0/Widgets) looks like very clever and simple way to create [reusable custom "tags"](http://turbogears.org/cogbin/) for shared functionality. 

And people do share: look at this amazing [http://www.tinyerp.org/](http://www.tinyerp.org/) - open-source [ERP](http://en.wikipedia.org/wiki/Enterprise_resource_planning) with many modules, including shopping and inventory control. You can do a lot with dynamic language and introspection :-)

> At least I can be reasonably certain that "integration" in a Python framework doesn't mean the same as it did with Catalyst, which was "fight with CPAN for hours and still not have a working install".[/QUOTE]

Not so :-) With setuptools, cheeseshop and egg format, installing became really easy - script downloads eggs and unpacks them. It was about the time :-) From start of install, you should build your own TG-based wiki within an hour using [this 20 minute wiki tutorial](http://docs.turbogears.org/1.0/Wiki20/Page1)

---

### Post by Dylnuge on 2007-07-31
I am considering TurboGears and Django for sure. I may also give Zope/Plone a try, especially after seeing this video: [http://oodt.jpl.nasa.gov/better-web-app.mov](http://oodt.jpl.nasa.gov/better-web-app.mov) (not sure how old it is). Since I am a programmer at heart, I really don't mind writing code, but 58 minutes for TG vs an average of about 10 for the others seems like a major turn off (admissably, not anywhere near the 255 for J2EE, but I was never considering J2EE for web development anyway). Clearly, there has yet to be a solution that combines the pros of all-making me assume that trying a simple project and seeing which one fits for me may work best. Some things I love/hate as of this moment:

**Django:**
Takes a lot of configuration, but I like the auto-security. I don't love the need to map the URLs, but at least it is much eaiser to make a URL look like an actual file, instead of post?$=yes&text+then%20it.

**Turbogears:**
Takes a while, but the interactivity seems different. Like being able to swap modules, also don't like it, since it means the framework was not originally designed to work together.

**Zope/Plone**
Like and dislike the preconfigured interface-seems more like a modifiable web app then an actual framework.

-Dylan

---

### Post by pmasiar on 2007-07-31
> **Dylnuge said:**
> 
**Turbogears:**
Like being able to swap modules, also don't like it, since it means the framework was not originally designed to work together.


Not so. Modules were selected to work together, glue code (TurboGears) written to do that, and communities around each module strive to make TG happy because TG is often their easiest and best way to reach users.

---

