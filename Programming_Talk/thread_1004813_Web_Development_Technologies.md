---
title: "Web Development Technologies"
date: 2008-12-07
forum: Programming Talk
---

### Post by cufflinks on 2008-12-07
I'm currently working for a very small company (6 people in total) and am having difficulty making a decision, and hoped the wonderful community here might have a few suggestions.

This company, although very well versed in design, is unfortunately somewhat lacking in development.  My previous job had been for a software company developing banking software with strong emphasis on performance, stability and security.  We built our web-based products in C++/ISAPI (and I did some ASP.net and very little Java).

So, the previous developer at my current company had chosen to use a PHP framework called Seagull.  While Seagull eventually proves beneficial for creating websites quickly (I say eventually because the documentation is pretty much useless IMHO), there are definitely huge fallbacks in the areas of performance, security and stability (and other areas, like being able to find someone willing to work in Seagull, for instance.)

In the end, I think our choice of framework can drastically improve my work, and the ultimate quality of our product.  What I need is something that is open source, can scale nicely between a small project and a large one, is easy/nice to develop in and can serve both small websites and large ones without it being choked, and preferebly someone has developed a CMS for it (with, if possible, SEO-friendly URLs and the ability to create content based on 'content types', but perhaps not necessary.)

I've looked at the following and will list what I liked/didn't like:

CakePHP - Seems very well written and thought out... unfortunately doesn't seem to perform very well. Out of the 2 CMSs I've seen made for it, one wasn't complete, and the other seemed like overkill (although compared to Seagull, its heavenly.)

After CakePHP I kind of gave up on PHP entirely... it seems most frameworks don't offer enough functionality if they're to perform well in PHP, or offer a lot of functionality but at a pretty big cost to performance.

Next I checked out Django... from a lot of the benchmarks I've seen, this project vastly outperforms any PHP-based framework.  There do appear to be CMSs built for it that I can take advantage of as well, perhaps someone knows a particularly good one?

I toyed with the option of a compiled language such as J2EE... but for the complexity involved in getting a project running with one developer, its probably not worth it (although I do enjoy the more C-based syntax and strongly-typed nature I don't think I'd enjoy much else about it... I feel its overkill, but feel free to correct me.)

Those are the three main ones I checked out... currently I'm leaning towards Django, but am open to any and all suggestions.  Would also love to hear how others are doing things at their companies, what languages and CMSs, how you feel it performs, security whatever other thoughts you may have.

Any and all suggestions welcomed and truly appreciated!

cufflinks

---

### Post by pmasiar on 2008-12-07
Django would be a very good choice, especially compared to PHP. It gently nudges you towards clean MVC design, and Python as language is clean, easy to learn and easy to maintain. 

Yes, Python has some performance penalty over statically compiled languages like C++ or Java, but you should be more concerned about developer's productivity (which is about 5 times more using flexible dynamic languages, in my experience).

Another framework worth considering is Turbogears (which is now based on Pylons). It is more flexible than Django. Django success is due to it's approach "one size fits all", and fits about 90% of average needs in a neat way, but once you need more flexibility in templating engine or O/R mapper, Django (by early decision) does not provide you choice, but simplicity and consistency.

My advice would be to go with Django as far as you can go, and be ready to switch to TG if Dj does not fit your app.

---

### Post by mike_g on 2008-12-07
I use Joomla at work. While I havent got experience with any other CMS (apart from wordpress), I have found Joomla really impressive. It has SEO friendly URL switch in the backend. There are also loads of useful [extensions](http://extensions.joomla.org/) around for it. Generally if there something that needs doing I look for a suitable component, and if one does not exists then I come up with a solution myself. Joomla kind of loosely follows the MVC design pattern and if used correctly the framework provides good security and sanitiation. If you have a go at using it then its work checking out [JRequest](http://api.joomla.org/Joomla-Framework/Environment/JRequest.html) for dealing with request vars. Once you have the template and components you need putting up a site is a very rapid process. Like I said I cant compare it to Django, but I do know quite a lot of people that use Joomla professionally and they all like it a lot. So IMO its worth checking out.

---

### Post by cufflinks on 2008-12-07
Thanks pmasiar,

I agree my approach should be rapid development... however my concern must also be quality and reliability.  Occasionally we do get large projects... and even though the client doesn't realise it, much of the problems we're facing right now with such projects is the fact that we're using Seagull (it is MVC to some extent at least, the 'model' part leaves a lot to be desired) which unfortunately performs horribly under even the slightest amount of stress.

Obviously I've known this for quite some time, but the problem is, all of our previous projects having been written in Seagull, I'd rather have something that we can rely on for quite some time before needing to switch again.  If you suggest Turbogears, and think I might end up switching there, is there a reason I shouldn't start out there?  Also are you using a particular CMS for it that you could recommend?

---

### Post by cufflinks on 2008-12-07
Thanks for the response mike_g,

My one concern with Joomla is its performance... while I imagine its one of the better PHP projects, I can't imagine any PHP-based framework (with all the functionality I'd like to have) performing all that well (correct me if I'm wrong, I'd love to hear otherwise... would be a much easier switch).  The other definite benefit is its integrated CMS (as I recall anyhow), and definitely a rapid development environment.

However, if it can't perform well enough for larger sites, that means we'd probably have to have two solutions, a 'smaller site' solution and a larger site solution, most likely written in another language... and I imagine would be an absolute headache to maintain these different codebases.

---

### Post by Reiger on 2008-12-07
It may be just me, of course, but if 'performance' is what you want you should not even be in webprogramming. If you've got a crappy internet connection, the Internet Delay is going to dwarf all performance issues on your program's side, but I digress.

Now to be of slightly more help: I think if you want *real* performance you'd have to end up writing things out yourself. And please note that language isn't quite the issue: how many perfectly nice PHP or Python scripts beat the gazillions of sluggish ASP.NET or JSP corporate crap that feels like you're wading through a couple buckets of lime? Of course it is undoubtedly an unfair comparison; but you should note that my earlier remark about the Internet Delay rings true -- it takes the performance hit from miliseconds to seconds or even minutes.

---

### Post by cufflinks on 2008-12-07
You're right in a sense, but performance issues in web are actually a lot more apparent than in desktop applications (IMHO).  For instance, a badly written desktop application will only affect the one user, if the user notices it at all.

For web-based apps, a badly performing web app will affect everyone accessing your site... while the connection may be sufficient to handle all of your users, the bottleneck could very well turn out to be badly written code (as I've unfortunately experienced first hand with some of the projects my company has been involved in.)

You're also right in that if I want really good performance, there's no reason I can't get it with PHP or pretty much any server-side technology out there... (provided I use a very minimalist framework, or none at all), but then the development time increases significantly... and I don't see why I can't find a 'middle way', where performance is quite good, but I also get good basic functionality and a rapid development environment.  The problem I've been encountering is a very wide range of clients, with very different goals... from very small projects to relatively large ones, and the problems associated with using a framework that doesn't perform very well at all.

---

### Post by pmasiar on 2008-12-07
> **cufflinks said:**
> however my concern must also be quality and reliability. 

how so, if you use PHP? PHP is **notorious** for messy apps.

> Occasionally we do get large projects... 

If YouTube can run on Python, any of your app should be able to run with Python too ;-)

>  Also are you using a particular CMS for it that you could recommend?

I don't do CMS, but trivial google search suggests [http://django-cms.org/](http://django-cms.org/) "free, BSD-licensed content management system for Django."

BSD, so you can make own private changes without sharing them back. Life cannot get any easier than that!

---

### Post by nsche on 2008-12-07
I would suggest you look at Ruby on Rails.  With a small programming team it will give you a good chance of really getting a usable system.  There are implementation approaches that handle thousands of connections using a cluster if needed.

YMMV

---

### Post by slavik on 2008-12-08
> **pmasiar said:**
> ...
If YouTube can run on Python, any of your app should be able to run with Python too ;-)
...


take the above idea and do the following:
s/Youtube/Wikipedia/g
s/Python/PHP/g

If Wikipedia can run on PHP, any of your app should be able to run with PHP too ;-)

NOTE: Mediawiki (the wiki engine powering Wikipedia and other Wikimedia wiki sites is written in PHP). Wikimedia has a total of 11 projects using mediawiki as the engine.

PS: I am not a PHP proponent.

---

### Post by cufflinks on 2008-12-08
@pmaiser

> how so, if you use PHP? PHP is **notorious** for messy apps.

I wouldn't entirely agree that that's PHP's fault... also using PHP (and Seagull) wasn't a decision I made, nor one I think will work for our needs... hence the thread.

> If YouTube can run on Python, any of your app should be able to run with Python too

I like the Python suggestion, and will definitely be looking more into Django... everything I read spoke highly of it, and recommendations from here also seem to suggest its a good way to go.  I believe much of google is also running python (or so I've read somewhere), but of course that's not Django, that would most likely be a very minimalist framework (if anything) handling only what each page would require for processing I would imagine.

That being said, we obviously don't have the same requirements as they, and definitely look forward to starting with Django.

Also, thanks for the link, I like the BSD license... nice to have Django itself in that license as well.

@slavik
> If Wikipedia can run on PHP, any of your app should be able to run with PHP too

I believe Facebook is also primarily a PHP app, there are many examples of succesfully running huge websites for probably every scripting/programming technology in existence... but same as how Google and Youtube would use Python, Facebook and Wikepedia most likely use very, very minimalist frameworks (if any for most of their processing, or spend huge amounts of money on hardware.)  My main concern was finding an open source framework (in any language really) that can scale fairly well to moderately larger projects... large is a bad word here, especially when I'm seeing responses mentioning Wikipedia and Youtube... we haven't built anything quite to that size (if we had, the websites would've certainly been built without the use of a heavy framework.)

@nsche

> I would suggest you look at Ruby on Rails. With a small programming team it will give you a good chance of really getting a usable system. There are implementation approaches that handle thousands of connections using a cluster if needed.
Good for a small team, you say?  Scales well you say?  Many thanks for the suggestion will definitely give that a whirl as well.  Definitely helps to hear recommendations instead of looking at benchmark graphs and huge table charts of comparisons, especially when someone knows "it's good for small teams" (which many such charts seem to leave out!)

---

### Post by pp. on 2008-12-08
> **pmasiar said:**
> PHP is **notorious** for messy apps.

A person competent in programming will do a reasonable job using PHP. An incompetent one will fail to do so in any language or even in pseudocode.

---

### Post by tinny on 2008-12-08
> **cufflinks said:**
> 
I toyed with the option of a compiled language such as J2EE... but for the complexity involved in getting a project running with one developer, its probably not worth it (although I do enjoy the more C-based syntax and strongly-typed nature I don't think I'd enjoy much else about it... I feel its overkill, but feel free to correct me.)


J2EE is completely over kill for a small company.

If you are looking for a more Java technology centric option have a look at Groovy + Grails.

Groovy is a dynamic programming language specifically designed for the Java platform.

[http://groovy.codehaus.org/](http://groovy.codehaus.org/)

Grails is basically a Rails rip off. Grails is the web framework to use with Groovy.

[http://grails.org/](http://grails.org/)

I have a lot of Java platform knowledge stored in my memory banks, so for me a trim Java platform web framework makes sense.

However if you have no previous platform knowledge you want to take advantage of then spend a week kicking them all around (time well invested). 

Id play with, Django, Groovy, Turbogears and Rails if I was you. Id stay away from PHP. Regardless of which one you choose its going to be a huge improvement over C/C++ for web development :shock:

---

### Post by tinny on 2008-12-08
> **pp. said:**
> a person competent in programming will do a reasonable job using php. An incompetent one will fail to do so in any language or even in pseudocode.

+1

---

### Post by cufflinks on 2008-12-08
Thanks Tinny (much respect to the bender avatar!!)

Yeah, C++/ISAPI was in my last company. I actually really really enjoyed it to be honest, for some reason I liked the complexity. I built our own very simplistic templating engine for it as well... pretty sweet... our client-side code also had to support IE4, which, call me crazy, but I enjoyed that too :P

Wow, Groovy... one I haven't heard of before.  Love the Java connection, definitely will check it out!

---

### Post by tinny on 2008-12-08
> **cufflinks said:**
> Thanks Tinny (much respect to the bender avatar!!)


:guitar:

> **cufflinks said:**
> 
Yeah, C++/ISAPI was in my last company. I actually really really enjoyed it to be honest, for some reason I liked the complexity. I built our own very simplistic templating engine for it as well... pretty sweet... our client-side code also had to support IE4, which, call me crazy, but I enjoyed that too :P


:shock::shock::shock:

You are crazy!!! :-)

Im trying to get the technical complexity out of my Job. I personally find it hard enough to deliver what my customers want. The process involved in solving a problem is the challenge that I am most interested in nowadays. Human communication etc. I personally find that using simple tools somewhat frees up the limited capacity I have in my mind to actually get the job done, then I can go home and watch Futurama. :-)

But I guess I do try and do some complicated stuff in my free time when coding at home.

> **cufflinks said:**
> 
Wow, Groovy... one I haven't heard of before.  Love the Java connection, definitely will check it out!

Yeah Groovy is pretty cool, although it is still very new.

---

### Post by cufflinks on 2008-12-08
I totally understand what you're saying as well... if my old company built websites it would've been crazy, it was a banking system they created, and the web module was one aspect of it.  The web module also had a port in Java, and a reporting module in .NET and supported SQL Server, DB2 and Oracle :)

If it was a process we had for creating client websites, I would've definitely gone crazy!

---

### Post by inazir on 2012-01-18
Glad to hear the views, my vote is for PHP as the best development tool in the world.

---

### Post by gesti on 2012-01-18
for me web development = PHP :) gave Django a try once but couldn't feel any performance difference compared to Yii framework, like Reiger mentioned it the network connection has a very important part in performance.
For example there is a big difference between Apache and lighttpd server regarding response speed, lighttpd is a lot quicker with response and the whole site will be snappier. But like always something for something, apache well documented and configuration can be adjusted by the web-developer with a .htaccess; lighttpd is badly documented and can be only configured by the server administrator.
I use Yii and it's really good for moderate and large projects. Completely follows the MVC concept, got great extensions and with good cache rules IMHO it can compete with django regarding speed.

---

### Post by howefield on 2012-01-18
Thread closed, let it sleep.

---

