---
title: "Best Tool for Web Application Development?"
date: 2008-07-01
forum: Programming Talk
---

### Post by TorchlightJay on 2008-07-01
Hello,
   So I run into a billion and one different programming languages when it comes to web application development. I want to get more involved in Web 2.0 development but there are so many solutions. I want to master a few languages/frameworks rather than try every single one. What is the best ones out there and what makes them so great?

Some of the ones I hear of are .NET, Java, PHP, Perl, Ruby, Python, Ajax, etc. 

Any help would be great, thanks.

---

### Post by myrtle1908 on 2008-07-01
For the front-end I recommend ExtJS [http://www.extjs.com](http://www.extjs.com) ... looks fantastic, almost all of the cross-browser stuff is already worked out for you, slick and easily extendable API, great support from the community.  For the back-end I would go with J2EE on Apache Tomcat but that's just what I'm most familiar with.

It really boils down to your skill set and what you want to achieve/create.

---

### Post by tinny on 2008-07-01
> **myrtle1908 said:**
> For the front-end I recommend ExtJS [http://www.extjs.com](http://www.extjs.com) ... looks fantastic, almost all of the cross-browser stuff is already worked out for you, slick and easily extendable API, great support from the community.  For the back-end I would go with J2EE on Apache Tomcat but that's just what I'm most familiar with.

It really boils down to your skill set and what you achieve/create.

I wouldn't recommend J2EE for your classic Web 2.0 stuff (wow did I just say that).

Id go for a [LAMP]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)") stack.

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> 
Id go for a [LAMP]("http://en.wikipedia.org/wiki/LAMP_(software_bundle)") stack.

No, PHP really needs to die already. :)

Python and TurboGears is the way to go at the moment IMO. It's much more modern both in language and framework architecture terms than anything you get with PHP.

Also, PostgreSQL for database... MySQL still is a collection of ugly hacks ;)

---

### Post by tinny on 2008-07-01
> 
Also, PostgreSQL for database... MySQL still is a collection of ugly hacks 


Hacks really? Ive used it a few times and liked it from a application developer / DBA perspective. Has the code been through to many hands?

---

### Post by NathanB on 2008-07-01
> **CptPicard said:**
> No, PHP really needs to die already. :)

The way I understand it, the 'P' in LAMP can just as easily stand for Python (and maybe a few other things).

Has anyone tried hacking something cool with this?

[http://code.google.com/appengine/](http://code.google.com/appengine/)

---

### Post by LaRoza on 2008-07-01
> **CptPicard said:**
> No, PHP really needs to die already. :)
A widely used, easy to learn and very popular language. Not going to die, only evolve.

> 
Python and TurboGears is the way to go at the moment IMO. It's much more modern both in language and framework architecture terms than anything you get with PHP.

Fanboyism? :-)

Not saying that PHP is a great language, it makes it easy to do bad things and has a large global namespace, but it has its advantages.

> 
Also, PostgreSQL for database... MySQL still is a collection of ugly hacks ;)
MySQL is what this forum uses, and it seems to do OK :-)

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> Hacks really?

Yeah, it didn't even have proper ACID compliance you could trust before version 5, and I think PgSQL's MVCC and row-level locks is a far superior solution to any schemes they managed to shoehorn into MySQL.

Of course, the more abstraction you slap on top of the DB (in particular in the case of the J2EE stack) the less stays the responsibility of the DB itself, but if you think of something like Hibernate which correctly keeps concurrency control in the database, I really like the idea that ACID really is ACID as per specs ;)

Of course PgSQL has always been the leader in general standards compliance too (MySQL only recently got inner queries for example) and has a really nice query optimizer...

I never got that much into ORM, and am more of an SQL guy, so I guess my feelings may be a little bit biased in that sense, but ... PgSQL feels really robust, MySQL never did :)

---

### Post by LaRoza on 2008-07-01
> **CptPicard said:**
> 
Python and TurboGears is the way to go at the moment IMO. It's much more modern both in language and framework architecture terms than anything you get with PHP.


> **CptPicard said:**
> 
I never got that much into ORM, and am more of an SQL guy, so I guess my feelings may be a little bit biased in that sense, but ... PgSQL feels really robust, MySQL never did :)

50% assimilated into pmasiar...

---

### Post by tinny on 2008-07-01
> **LaRoza said:**
> 50% assimilated into pmasiar...

Are we talking about ORM? I must be watching the wrong movies.

:confused:

You just melted my brain...

---

### Post by LaRoza on 2008-07-01
> **tinny said:**
> Are we talking about ORM? I must be watching the wrong movies.

:confused:

You just melted my brain...

pmasiar is a fan of Python + TurboGears and ORM.

---

### Post by maximinus_uk on 2008-07-01
Often I find the best tool for web development is a computer.




:D  thank you, I'll be here all night.....

---

### Post by pmasiar on 2008-07-01
There are 3 incompatible (by design) platforms:

- .NET (with C# and VB)
- Java
- Linux/Apache stack (LAMP, If M stands for "MySQL or Postgres", and P stands for "Perl Python PHP Ruby".

Let's just ignore .NET :-)

Java is statically typed and not flexible enough for text processing - but widely used in "enterprise" programing, million users, frameworks and other tools. But as statically types, pain and boring to develop in. And programmer will not see any substantial speed difference, because most time is wasted on web server calls, AJAX manipulation, and database calls, regardless of what language you use (out of your control). so you may as well use language which makes you more productive: dynamically typed language ("scripting" is misleading term).

PHP is natural way to get into dynamic web pages for someone with HTML background - it lets you just to add little PHP snippets, and grow from there. So it is immensely popular between beginners with little clue about programming big systems - and passionately hated by those with the clue :-) because allows to create big hairy unmaintenable mess. It's  (even if not obvious) how to do it right, and most PHP code you will see will teach you bad non-MVC approach.

To create real big maintainable web applications, you really need to bite the bullet and pull all your computing logic out of the page, separate app into layers: Model (database access), View (HTML templates to generate pages) and Controller (logic to bind M and V together, and separate them). Read up wikipedia MVC design pattern. This approach guarantees that change in one layer will not leak into another.

Perl was popular flexible language with excellent text processing when web started and widely used, but competition from PHP, Ruby and Python is taking over. And is hard to use for big programs - it was designed for simple scripts, not big systems.

Ruby with Rails was first really dynamic web framework, very radical when introduced, and got lots of popularity and hype. Since 2005, Rail's ideas were adopted by Python community.

Because Python is substantially more popular outside of web app (is often used as replacement of Perl), web app were neglected for a while (but still widely used: there were **dozens** of Python web framework, but none of them really good), but then Google (which uses Python a lot internally) hired couple leading Python developers, including author (Guido van Rossum), and make Guido to write web app for them :-) Now Python has two leading frameworks Django if you want simple functionality with lots of defaults, and Turbogears (based on Pylons) if you need lots of flexibility. Both are MVC with ORM of course, and easy to use.

If you are total beginner, start with Django. It comes with development server (simpler than Apache, and more flexible for development) and SQLite database (simpler than MySQL/Postgress), but ORM will hide this difference, you can switch later.

Python is also slightly more obvious to learn for beginner than Ruby (Ruby is too close to Perl with it's quirks).

Another option is Google App Engine (with free hosting), Python is the only choice of language they have. I wrote a thread about GAE couple months ago, dig it out for details.

So on server, Python (with Django or Turbogears) is for most people the best solution.

On client side, there are dozens of competing libraries and it's not obvious yet which one is the best.

---

### Post by LaRoza on 2008-07-01
> **pmasiar said:**
> 
PHP is natural way to get into dynamic web pages for someone with HTML background - it lets you just to add little PHP snippets, and grow from there. So it is immensely popular between beginners with little clue about programming big systems - and passionately hated by those with the clue :-) because allows to create big hairy unmaintenable mess. It's  (even if not obvious) how to do it right, and most PHP code you will see will teach you bad non-MVC approach.
I agree with all of that, except by being hated by those with a clue (unless I am clueless, then disregard this post)

I never use PHP in a messy way, and always keep everything separate. Yes, it was a deliberate design, and not something everyone will do, but it has nothing to do with the language.

However, there are times when I just want one piece of server side scripting, typically just an IP address and a simple <?php echo $_SERVER['REMOTE_ADDR'] ?> will fulfill my needs.

> 
To create real big maintainable web applications, you really need to bite the bullet and pull all your computing logic out of the page, separate app into layers: Model (database access), View (HTML templates to generate pages) and Controller (logic to bind M and V together, and separate them). Read up wikipedia MVC design pattern. This approach guarantees that change in one layer will not leak into another.

I agree with all of that, and it applies to all languages including PHP.

---

### Post by pmasiar on 2008-07-01
I agree with LaRosa 100%. Not all developers have discipline to follow the rules as borg has, so for non-borg, PHP is suboptimal choice with limited usability. :-) Or get assimilated and embrace the joys of displined PHP code :-)

---

### Post by LaRoza on 2008-07-01
> **pmasiar said:**
> I agree with LaRosa 100%. Not all developers have discipline to follow the rules as borg has, so for non-borg, PHP is suboptimal choice with limited usability. :-) Or get assimilated and embrace the joys of displined PHP code :-)

Gracias. Tengo gusto de ser conforme.

Wait! I am not castellano! 

I wouldn't want to use PHP for larger multi developer projects. That could get messy way too fast. PHP fulfills its original role for "Personal Home Pages", although it is capable of bigger things, I wouldn't want to use it for that.

(Amazing how much a difference a 'z' makes...)

---

### Post by TorchlightJay on 2008-07-01
Wow so much to eat. I am familiar with PHP and it seems to be the one everyone seems to support in one way or another. I do often hear that it isn't great for major projects.

What do you all think about Ruby On Rails. That seems to be the one that everyone is raving about these days. Is it all just hype or is there something to it?

Do we all have a bitterness toward .NET because it's Microsoft or does it truly just suck?

Sort of related, what does an SDK do?

---

### Post by LaRoza on 2008-07-01
> **TorchlightJay said:**
> 
What do you all think about Ruby On Rails. That seems to be the one that everyone is raving about these days. Is it all just hype or is there something to it?

Ruby on Rails isn't that unique anymore, see the two frameworks pmasiar mentioned for Python. (Check wikipedia for development frameworks also)

> 
Do we all have a bitterness toward .NET because it's Microsoft or does it truly just suck?
Yes it "sucks", it isn't designed to work on the most popular server used on the web.

> 
Sort of related, what does an SDK do?

It is just a Standard Development Kit. It provides the tools needed to do development.

---

### Post by tinny on 2008-07-01
> 
Do we all have a bitterness toward .NET because it's Microsoft or does it truly just suck?


Yeah the Microsoft thing.

Its fine to develop in.

> 
It is just a Standard Development Kit. It provides the tools needed to do development. 


Software Development Kit

> 
Java is statically typed and not flexible enough for text processing


Text processing, why is this so difficult in Java? (I have know idea why you think text processing is a big deal???)

---

### Post by TorchlightJay on 2008-07-01
Hmm, sounds good. So what I can gather from this forum so far, PHP is alright but it's been played out. Perl really isn't a good option. It sounds like my best bet is either Ruby On Rails or Perl with Turbogears or Django. It seems like you all have an affinity towards Python in this thread. So how do you suggest I start learning. 

Since google seems to use python and I want to do a little app development for google. Anyone know how to use the SDK for it. I downloaded it, looked at it, have no clue what to do.

---

### Post by LaRoza on 2008-07-01
> **TorchlightJay said:**
> Hmm, sounds good. So what I can gather from this forum so far, PHP is alright but it's been played out. Perl really isn't a good option. It sounds like my best bet is either Ruby On Rails or Perl with Turbogears or Django. It seems like you all have an affinity towards Python in this thread. So how do you suggest I start learning. 
Python works with Turbogears.

I suggest you check out pmasiar's wiki.

---

### Post by LaRoza on 2008-07-01
> **tinny said:**
> Yeah the Microsoft thing.

Its fine to develop in.

On Windows or Microsoft server, yeah.

> 
Text processing, why is this so difficult in Java? (I have know idea why you think text processing is a big deal???)

I find that laughable...

Text processing in Perl vs. Java? Do I even have to say why?

---

### Post by tinny on 2008-07-01
> **LaRoza said:**
> On Windows or Microsoft server, yeah.



I find that laughable...

Text processing in Perl vs. Java? Do I even have to say why?

umm, yes

Edit: Actually no please dont. I really dont want to go down this path again. :)

---

### Post by LaRoza on 2008-07-01
> **tinny said:**
> 

Edit: Actually no please dont. I really dont want to go down this path again.

And I won't take the bait again.

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> umm, yes


If it weren't confidential, I would show you my sports betting toolkit's part where I programmatically deal with a certain website. You know, send request, parse response. Jakarta HttpClient and java.util.regex mashed together.

It's remarkably ugly for something that some other languages are one- or two-liners.

---

### Post by myrtle1908 on 2008-07-01
There really is no "best" tool for developing web applications.

This discussion is all very emotive...personal preference etc...and frankly that's all it will ever be.

Basically, one must "play" within the boundaries that they are set and within this bound, choose the most appropriate tool for the job.

For example, in my experience in the corporate world one would have little to no chance of flogging a Ruby on Rails or a "This on That" solution.  The large client is most likely a Microsoft shop and at best may let you get away with J2EE solution.

At the end of the day it's "horses for courses" and always will be.

That said, this is an interesting discussion.

---

### Post by elithrar on 2008-07-01
> **LaRoza said:**
> 
Yes it "sucks", it isn't designed to work on the most popular server used on the web.


Apache + mod_mono do work - though when it comes down to it, it's still a reverse-engineered 'hack' of sorts.

> **TorchlightJay said:**
> Hmm, sounds good. So what I can gather from this forum so far, PHP is alright but it's been played out. Perl really isn't a good option. It sounds like my best bet is either Ruby On Rails or Perl with Turbogears or Django. It seems like you all have an affinity towards Python in this thread. So how do you suggest I start learning. 


I'd suggest starting with Django, if not just for the documentation & community alone. Definitely start with the [official documentation](http://www.djangoproject.com/documentation/) & also look at the [Django book](http://djangobook.com/). Outside of that, there's the [django-users](http://groups.google.com/group/django-users/topics) Google group & #django on irc.freenode.com.

If you're also new to Python, but *not* new to programming (or at least the basic concepts), then look at the [Python documentation](http://python.org/doc/) - the tutorials & Wiki there should go a long way in introducing you to the language. I'd also recommend picking up *Learning Python* from O'Reilly (a book), which is a solid introduction to the language as well - I found it preferable to the online docs, if only for readability.

Don't think that you're tied down to a particular language though - the good thing about Python & Django is that they share a lot of concepts with other languages (namely Ruby & Perl) and frameworks (Turbogears for Python, Pylons for Python, Ruby on Rails, etc) - time invested in one isn't wasted if you decide it's not a 'fit' for what you want to achieve.

Also: take any recommendations at face value - but I hope I've given you enough to start researching on your own. I use Python because it "fits my brain" (I say this a lot!) and Django because it's ideal for the projects I want to develop. I actually did start on Ruby (& I still adore the syntax), and still do dabble in it.

---

### Post by LaRoza on 2008-07-01
> **elithrar said:**
> Apache + mod_mono do work - though when it comes down to it, it's still a reverse-engineered 'hack' of sorts.


I know. Read what I said ;)

I said "designed".

---

### Post by pmasiar on 2008-07-01
> **tinny said:**
> umm, yes

in example, things like [string interpolation in Perl](http://www.shlomifish.org/lecture/Perl/Newbies/lecture2/interpolation.html) or at least [Python string formatting](http://docs.python.org/lib/typesseq-strings.html) - not mentioning inability in Java to simply create complicated object literal constants for mock testing.

---

### Post by sakabato on 2008-07-01
> **LaRoza said:**
> Ruby on Rails isn't that unique anymore, see the two frameworks pmasiar mentioned for Python. (Check wikipedia for development frameworks also)


Yes it "sucks", it isn't designed to work on the most popular server used on the web. 


This is simply incorrect. ASP.NET on Mono works fine with Apache via mod_mono. I also recommend it !

---

### Post by LaRoza on 2008-07-01
> **sakabato said:**
> This is simply incorrect. ASP.NET on Mono works fine with Apache via mod_mono. I also recommend it !

It is correct that .NET wasn't designed to work on anything but Windows. It is correct that there are many alternatives. 

I know you would recommend it, it is your job...

Now can you give technical reasons why people should use it over other solutions? (A person moving an existing setup to Linux, or someone already very familiar with .NET excepting.)

---

### Post by TorchlightJay on 2008-07-01
> **myrtle1908 said:**
> There really is no "best" tool for developing web applications.

This discussion is all very emotive...personal preference etc...and frankly that's all it will ever be.

Basically, one must "play" within the boundaries that they are set and within this bound, choose the most appropriate tool for the job.

For example, in my experience in the corporate world one would have little to no chance of flogging a Ruby on Rails or a "This on That" solution.  The large client is most likely a Microsoft shop and at best may let you get away with J2EE solution.

At the end of the day it's "horses for courses" and always will be.

That said, this is an interesting discussion.

Makes sense. I figured that it was all about personal preference. i thought that maybe there were some things that some languages were better at than others when it came to buiding apps for Web 2.0.

So in a realistic sense, are some of the languages like Ajax, PHP, Perl, Python, Ruby as good as say Java or .NET in terms of the development. Can you develop similar things with both programs? If so, is there a chance that large companies would want to use them? I am guessing that maybe the main reason it's not used is because of brand recognition with Microsoft.

---

### Post by CptPicard on 2008-07-01
> **TorchlightJay said:**
> Makes sense. I figured that it was all about personal preference.

While it is true that differing project requirements may cause you to look in different directions for good reason, I do have to take serious issue with the idea that it is "all about personal preference". If this were the case, there would not be generally agreed-upon best practices, such as the MVC pattern.

"Personal preference" is an argument that is sometimes used here to dilute discussions into harmlessness when other arguments fail, but certainly we can discuss about things objectively, and come to meaningful conclusions... for example, a strong preference for TurboGears-like development really does come from experience, and is worth listening to. :)

---

### Post by myrtle1908 on 2008-07-01
> **TorchlightJay said:**
> Makes sense. I figured that it was all about personal preference. i thought that maybe there were some things that some languages were better at than others when it came to buiding apps for Web 2.0.

So in a realistic sense, are some of the languages like Ajax, PHP, Perl, Python, Ruby as good as say Java or .NET in terms of the development. Can you develop similar things with both programs? If so, is there a chance that large companies would want to use them? I am guessing that maybe the main reason it's not used is because of brand recognition with Microsoft.

Not so much because of "brand recognition" rather they usually have invested heavily in Microsoft technologies and switching becomes difficult and very expensive...eg. new support people, licensing etc.

Also, AJAX is not a language rather it is a technique or a methodology...*With Ajax, web applications can retrieve data from the server asynchronously in the background without interfering with the display and behavior of the existing page [ref. wikipedia [http://en.wikipedia.org/wiki/AJAX]](http://en.wikipedia.org/wiki/AJAX])*

Finally, yes you can achieve the same results with all the different languages/technologies around today.  After all Web 2.0 just describes a richer, more interactive web interface.

---

### Post by pmasiar on 2008-07-02
> **TorchlightJay said:**
> are some of the languages like Ajax, PHP, Perl, Python, Ruby as good as say Java or .NET in terms of the development. Can you develop similar things with both programs? If so, is there a chance that large companies would want to use them? 

There is **big difference** between dynamically typed languages (Perl, Python, Ruby, PHP) and statically typed (C#, Java), and it was discussed many times, even this week, in multiple threads. 

And frankly if you don't feel the difference (or limit it to the "speed"), it will be hard to persuade you. And was discussed to death.

Hint: developing in dynamically typed languages is much faster (more productive). Languages differ, Python and Ruby are winners for big system (for other design decisions).

Smart companies use flexible languages, big companies do not risk and use Java or C#, but not because they are the best: because they are safe bets and nobody gets fired for using "standard", however bad it is. Read "Beating the averages": [www.paulgraham.com/avg.html](www.paulgraham.com/avg.html)

---

### Post by tinny on 2008-07-02
> Not so much because of "brand recognition" rather they usually have invested heavily in Microsoft technologies and switching becomes difficult and very expensive...eg. new support people, licensing etc.

Bang on!

In larger reputable organisations most of the time the decision is already made before a technical person gets involved.

[http://ubuntuforums.org/showthread.php?t=846478]("http://ubuntuforums.org/showthread.php?t=846478") ;)

> There is **big difference** between dynamically typed languages (Perl, Python, Ruby, PHP) and statically typed (C#, Java), and it was discussed many times, even this week, in multiple threads.

A CIO (the decision maker) will never listen to that argument, never.

---

### Post by sakabato on 2008-07-02
> **LaRoza said:**
> It is correct that .NET wasn't designed to work on anything but Windows. It is correct that there are many alternatives. 

I know you would recommend it, it is your job...

Now can you give technical reasons why people should use it over other solutions? (A person moving an existing setup to Linux, or someone already very familiar with .NET excepting.)

Sure, but this would be an asp.net versus others comparison. I am stressing, asp.net support of mono is pretty much complete. The only missing parts are web parts and listview(which exists in svn head)

If you want a technical comparison , I've blogged about it:

[URL="http://reverseblade.blogspot.com/2008/06/web-development-aspnet-webforms-versus.html"]
ASP.NET versus Others[/URL]

[Rails versus Others]("http://reverseblade.blogspot.com/2008/06/web-development-ruby-on-rails-versus.html"), read on!

---

### Post by pmasiar on 2008-07-02
> **tinny said:**
> In larger reputable organisations most of the time the decision is already made before a technical person gets involved.

Exactly. Decision is made based on PHB chitchat and buzzwords overheard at conferences.

> A CIO (the decision maker) will never listen to that argument, never.

Argument for CIO might be increased productivity with dynamic languages. 

But even that often does not work: PHB is afraid to employ coding guru, even if more productive using "niche" language: he is afraid that guru will leave and nobody else will be able to maintain the code. CIO is more interested in having replaceable cogs in machinery than talented programmers. That's why Google is so good: they are not afraid of talent, and pay them to work (famous 20%) on what talented people consider right, not PHB.

---

### Post by TorchlightJay on 2008-07-02
I see, all a lot to swallow. Google implements a lot of python, do you think that can help python grow in the larger organizations. 

I want to learn programming for Web 2.0 and actually make it usable. I want something that works well and can be used for a variety of development.

I know that WordPress, Joomla!, Drupal, phpBB, and what not are all made with PHP so I want to be able to integrate with these other tools (no point in reinventing the wheel). I want a tool that can build some powerful apps though.

---

### Post by tinny on 2008-07-02
> Exactly. Decision is made based on PHB chitchat and buzzwords overheard at conferences.

No. For reasons that are  far above our heads. So why even bother speculating.

> But even that often does not work: PHB is afraid to employ coding guru, even if more productive using "niche" language: he is afraid that guru will leave and nobody else will be able to maintain the code. CIO is more interested in having replaceable cogs in machinery than talented programmers. That's why Google is so good: they are not afraid of talent, and pay them to work (famous 20%) on what talented people consider right, not PHB.

COME ON, lets not go down this path again.

A java programmer can be a guru.
A python programmer can be a guru.
A java programmer can be a cog.
A python programmer can be a cog.

Your smart / talented, im smart / talented... whatever, at best all we can do is generalise and speculate.

---

### Post by LaRoza on 2008-07-02
> **tinny said:**
> Your smart / talented, im smart / talented... whatever, at best all we can do is generalise and speculate.

Actually, I think pmasiar has more authority in this discussion, being someone with a lot of experience and actually using Java and Python.

---

### Post by CptPicard on 2008-07-02
> **tinny said:**
> 
A java programmer can be a guru.

It's somewhat hard to be a guru in Java or in any other similar language though because the language doesn't give you much leeway in actually doing interesting things. :) Of course you can be a guru in the sense of knowing reams of API by heart, but I'm not awfully impressed by that...

Of course my own preferences are about being a guru in a mostly language-independent sense, but still...

---

### Post by tinny on 2008-07-02
> 
Of course my own preferences are about being a guru in a mostly language-independent sense, but still...


Yeah, knowing the software domain.

> **LaRoza said:**
> Actually, I think pmasiar has more authority in this discussion, being someone with a lot of experience and actually using Java and Python.

What do you know about my experience in Software Development??? I could be James Gosling for all you know.

Only 1 year of programming and you already feel wise enough to consistently slap people with far more experience than you. You are doing a very good job of alienating people from the forum you are charged with looking after.

This sucks :(

User CP > List Subscriptions > Delete "Best Tool for Web Application Development?"

---

### Post by pmasiar on 2008-07-02
> **LaRoza said:**
> Actually, I think pmasiar has more authority in this discussion, being someone with a lot of experience and actually using Java and Python.

I don't think of myself as a guru - I can pretend in this forum, but most I know is what **I** picked in posts from real named experts (who do not waste time here on this forum).

And I am definitely not a Java guru - I am quite a beginner, asking for help (see my other thread), also from people like tinny (and I am glad he is helping - please don't scare him away), so...

I see tinny's point. But in enterprise world, people use language thay are told to use, so people who ue Python in enterprise are curious or having influence on smarter CIO than average.

I don't think Python programmer can be a cog, because big projects where any warm body can fill the job opening does not use Python - they use Java, sadly :-)

---

### Post by LaRoza on 2008-07-03
> **pmasiar said:**
> 
And I am definitely not a Java guru - I am quite a beginner, asking for help (see my other thread), also from people like tinny (and I am glad he is helping - please don't scare him away), so...


@tinny I didn't mean to offend you, but to tell you since I know pmasiar's experiences, his advice means more to me. (except I still don't know what to think about you saying Java is as good as Perl for text processing...)

I plan on being a perpetual beginner; I like to learn.

---

### Post by TorchlightJay on 2008-07-03
I think this is all interesting but i really didn't want my question to result in a miniature flame war. I am sure everyone hear is skilled and has their own opinion.Maybe some of you can make your preferred programming language purr like no other. 

I guess i oughta learn myself some python and maybe php for good measure.


what is an API?

---

### Post by LaRoza on 2008-07-03
> **TorchlightJay said:**
> I think this is all interesting but i really didn't want my question to result in a miniature flame war. I am sure everyone hear is skilled and has their own opinion.Maybe some of you can make your preferred programming language purr like no other. 

On the internet, there is no way to tell. You have self important script kiddies giving "advice" based on the one thing they do know, and you have programmers with years of experience and higher degrees and everyone in between. (Not saying anyone on this thread is a script kiddie)

> 
what is an API?
[http://en.wikipedia.org/wiki/API](http://en.wikipedia.org/wiki/API)

---

### Post by GulamGaus on 2008-10-11
The best web development tool would be 

[LIST]
[*]Ubuntu for your OS
[*]Django Web Framework for your Web site development. This includes Python as the base language. Assumes operational knowlegdge of Python. As rightly said Python is here to stay. J2EE must die..
[*]Postgresql for your database
[/LIST]

J2EE, MySQL all sucks even to that matter, your javascript. Mochikit would be a better player than Javascript. I prefer Django as the MVC stack is loosly decoupled unlike Tourbogears where all the layer is tightly coupled with one another. If I dont want to use another Template such as Cheetah..I cannot do that in Turbogears but yes Django you are free to use whatever best suits you..:=)

---

### Post by pmasiar on 2008-10-11
> **GulamGaus said:**
> Mochikit would be a better player than Javascript. I prefer Django as the MVC stack is loosly decoupled unlike Tourbogears where all the layer is tightly coupled with one another. If I dont want to use another Template such as Cheetah..I cannot do that in Turbogears but yes Django you are free to use whatever best suits you..:=)

Just clearing some mis-advice:

Django is excellent for beginner, as it has policy "one size fits all", it is best for 90% of that you need, and smoothly integrated, but once you feel the seams at the limits, is better to swith to Turbogears (or all the way to Pylons), which allows you way more freedom (for the price of losing the tight integration). Flexibility is always for a price.

TG supports about a dozen templating engines,  JS libraries, and widgets to create your own "smart form items". It is TG what is layered and decoupled, not Django (so Django is easier to start with as is, and TG gives you more flexibility if you need it).

Mochikit is decent Javascript library, there are many, like jQuery, dojo, scriptaculous.

---

### Post by GulamGaus on 2008-10-13
> **pmasiar said:**
> Just clearing some mis-advice:

Django is excellent for beginner, as it has policy "one size fits all", it is best for 90% of that you need, and smoothly integrated, but once you feel the seams at the limits, is better to swith to Turbogears (or all the way to Pylons), which allows you way more freedom (for the price of losing the tight integration). Flexibility is always for a price.

TG supports about a dozen templating engines,  JS libraries, and widgets to create your own "smart form items". It is TG what is layered and decoupled, not Django (so Django is easier to start with as is, and TG gives you more flexibility if you need it).

Mochikit is decent Javascript library, there are many, like jQuery, dojo, scriptaculous.



Thanks! for the information. I would also appreciate if you could kindly tell me what exactly it would be to "feel the seams" in terms of development & usability. I'd just started a project using Django. I dont want to be in trouble in between or after reaching the core. However would you know any pointers for technical/community help on using Django?

---

