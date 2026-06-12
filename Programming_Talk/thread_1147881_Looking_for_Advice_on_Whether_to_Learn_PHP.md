---
title: "Looking for Advice on Whether to Learn PHP"
date: 2009-05-03
forum: Programming Talk
---

### Post by shatterblast on 2009-05-03
I'm a student, and I'm going to keep busy with a combination of studying books and working.  I'm strengthening my knowledge in Java already on the side while scheduled to take a C++ class next semester.  I've been programming in various languages a long time though not to the extent of some rugged professionals.  

I'm not counting punch cards of course.  I seem to meet many people who know those specifically, yet they seem unaware about compilers or interpreters since they're mostly out of practice.  Funniest story I heard was about a game of Pac-Man on an original style main frame using only punch cards.

Anyhow, PHP is for web design.  I figure I can do the whole LAMP thing easily, except I lack knowledge in SQL and the "P" part.  Those would include PHP, Python and Perl in my understanding.  I consider Python for the future, but I prefer performance over ease for the most part.  I try to avoid Perl with a passion even if it can be powerful.  So that leaves me with PHP I suppose somewhere in the middle.

I figure I can integrate Java and PHP easily enough in some form.  With Java and Python, I could possibly look at Jython in the future.  Perl is suppose to remain the fastest of the three, yet I don't have a desire at this point.

Thanks for any tips, advice and suggestions.

---

### Post by sujoy on 2009-05-03
imo you are thinking too much. want to know how PHP is? jump right in. its not like there is a limit to the maximum number of languages you are allowed to learn.

---

### Post by DGortze380 on 2009-05-03
Seriously, just play with it, drop it if you find no entertainment or use.

PHP is a nice mix of C++ and Bash in my experience. Very intuitive, very powerful.

---

### Post by Reiger on 2009-05-03
Seconded. If you are not curious you will not enjoy it; if you are curious you will gain skills with a widely used language that in my mind works really well for server side scripting.

---

### Post by irvingswiftj86 on 2009-05-03
if i were you i would defiantly learn php. it seems to have a serious chance of being the 'expected to know' language for web designers especially as sites like facebook are so heavily reliant on it.

---

### Post by CptPicard on 2009-05-03
> **shatterblast said:**
> 
Anyhow, PHP is for web design.

A lot of things are. PHP really is on the way out in the longer term IMO.

> 
  I figure I can do the whole LAMP thing easily, except I lack knowledge in SQL and the "P" part.  Those would include PHP, Python and Perl in my understanding.  I consider Python for the future, but I prefer performance over ease for the most part.

Python is a very multipurpose language, but it also happens to have nice web frameworks (Django, TurboGears) which actually give you correct architecture out of the box, quite in contrast to PHP which tends to encourage the scriptlets-in-HTML horror coding style.

It is possible that PHP is more optimized than current python-based web application solutions, but it's not as if you're writing anything performance-critical especially in the web application space any time soon. Web apps are database-bound anyway, and in them architectural cleanliness, readability of code etc beats anything else every time.


> 
I figure I can integrate Java and PHP easily enough in some form.  

Sounds pretty much impossible... I do my web apps mostly in Java, and I really can't think of a way to make the two play along well. Their approaches are too different.

> 
With Java and Python, I could possibly look at Jython in the future.

If we're still talking web apps, Groovy on Grails is probably more like it.

> 
Perl is suppose to remain the fastest of the three, yet I don't have a desire at this point.

Don't be a speed kiddie... I can understand performance considerations when writing heavy algorithms, but not when writing web applications (and when there are performance considerations, they are generally somewhat different from simple "language issues").

> 
PHP is a nice mix of C++ and Bash in my experience. Very intuitive, very powerful.

I am not sure if you're being sarcastic or not :P ... throw in the HTML and you're actually quite correct in your characterization, though.

---

### Post by DGortze380 on 2009-05-03
> **CptPicard said:**
> 
I am not sure if you're being sarcastic or not :P ... throw in the HTML and you're actually quite correct in your characterization, though.

No, not sarcastic. 
And yes, I know it's accurate, thank you.
And while HTML obviously goes hand in hand with PHP, the two are very separate, very different things.

---

### Post by shatterblast on 2009-05-04
> **CptPicard said:**
> Sounds pretty much impossible... I do my web apps mostly in Java, and I really can't think of a way to make the two play along well. Their approaches are too different.

I'll assume for the moment that a binding for PHP and Java may exist due to PHP's origin.  Java and PHP have in common that they both started in the C language.  As personal experience has proven though, it may not become easy.

Apart from self-startable applications like applets and JNLP Web Start items, I assume that server side information could share between the two by means of an XML file, data stream, or something similar.  If anything, both sides could probably read the same database.  As far as read and write conflicts on a single database, coordinating the two would probably become the greatest challenge in my opinion.  My approach would lean towards using one or the other.

> **CptPicard said:**
> If we're still talking web apps, Groovy on Grails is probably more like it.

I believe portions of Groovy are considerably outdated last I checked.  Java 1.6 renders part of it inconsistent since some of it might still linger in 1.4.

> **CptPicard said:**
> Don't be a speed kiddie... I can understand performance considerations when writing heavy algorithms, but not when writing web applications (and when there are performance considerations, they are generally somewhat different from simple "language issues").

I started with programming languages instead of scripting for that reason.  It's all or nothing.  :P

I'm glad to see the good comments on PHP.  I think I will prefer Python for now and refer to PHP as a secondary for web design.  Thank you.

---

### Post by myrtle1908 on 2009-05-04
> **DGortze380 said:**
> No, not sarcastic. 
And yes, I know it's accurate, thank you.
And while HTML obviously goes hand in hand with PHP, the two are very separate, very different things.

If anything, PHP has more in common with Perl than C++ and shell scripts.  After all it was created to encapsulate a bunch of Perl scripts.  Throw in CGI handling and you have PHP.

Back on topic ... PHP, like any other server-side technology is fine to learn.  Obviously it cannot hurt to know.  However If I were trying to get into web design I wouldn't bother with the server-side too much.  In fact, the choice of server-side technology for mine is not terribly important.  After all, it should really only be communicating with the database/service/whatever and spitting back something useful to the client eg. JSON/HTML/whatever.

Where the work comes IMO is in designing the client/UI.  My advice would be to learn JavaScript/DOM like the back of your hand.  Couple that with a decent toolkit eg. ExtJS/JQuery and you're away.

My $0.02

---

### Post by slavik on 2009-05-04
> **myrtle1908 said:**
> After all, it should really only be communicating with the database/service/whatever and spitting back something useful to the client eg. JSON/HTML/whatever.

really? think about that statement and if you really feel it to be true, make it again.

consider this: you need to have 90 servers serve your app, to a million and a half people in an hour. how many DB connections is that? think about it.

---

### Post by myrtle1908 on 2009-05-04
> **slavik said:**
> really? think about that statement and if you really feel it to be true, make it again.

consider this: you need to have 90 servers serve your app, to a million and a half people in an hour. how many DB connections is that? think about it.

Yes I was over-simplifying for the purposes of the discussion ... at least what I perceived it to be.  The point I was trying to make was that the server-side technology is but only a part of the web development cycle.

It seemed to me that the OP was talking about "web design" which really does not involve much server-side "glue" (despite the explicit mention of PHP).

Either way, it is hard to argue that a web-server(s) does much more than service its clients.  How it services them is another thing (which is perhaps the point you are making).

---

### Post by slavik on 2009-05-04
yes, it is my point and I understand what you are saying, but it feels as if you are disregarding server-side implementation.

design can be done in an image editing program, but architecture is in code. :)

---

### Post by myrtle1908 on 2009-05-04
> **slavik said:**
> yes, it is my point and I understand what you are saying, but it feels as if you are disregarding server-side implementation.

design can be done in an image editing program, but architecture is in code. :)

I have amended my original post to avoid further confusion.

---

### Post by slavik on 2009-05-04
> **shatterblast said:**
> Seeing as how MySQL may possibly decrease in the future because of Oracle's purchase of Sun, I would think that PHP may reduce in popularity as well.  Regardless, it's in my understanding that PHP integrates with Oracle products anyhow.

this is not making sense to me, can you restate your thought in the last sentence?

---

### Post by CptPicard on 2009-05-04
> **shatterblast said:**
> Regardless, it's in my understanding that PHP integrates with Oracle products anyhow.

Really, all web app development technologies integrate well with any half-decent databases, so although the PHP+MySQL combination is "common", they are by no means technologically "married"...


> I'll assume for the moment that a binding for PHP and Java may exist due to PHP's origin.  Java and PHP have in common that they both started in the C language.

Just because they share similar basic control constructs, doesn't really mean anything in this regard. 

> If anything, both sides could probably read the same database. 

Well, if "is able to produce HTML to client and uses same database" is your idea of integration, then ok... they may "integrate". I would expect something deeper (at least shared sessions), and that is going to be very hard.

> 
 As far as read and write conflicts on a single database, coordinating the two would probably become the greatest challenge in my opinion.

That sort of conflict management is what the database is supposed to be doing.

> 
I believe portions of Groovy are considerably outdated last I checked.  Java 1.6 renders part of it inconsistent since some of it might still linger in 1.4.

If there are any issues, they probably deal with generics support, but considering that GoG itself is going strong, I wouldn't worry about any of that.

> 
I started with programming languages instead of scripting for that reason.  It's all or nothing.  :P

Turing-completeness is Turing-completeness, and actually a lot of languages that some may call "scripting" languages actually are capable of expressing things in very interesting, conceptually efficient, clear ways. PHP is not one of them alas IMHO ;)

---

### Post by Kilon on 2009-05-04
> **shatterblast said:**
> 

I started with programming languages instead of scripting for that reason.  It's all or nothing.  :P

I'm glad to see the good comments on PHP.  I think I will prefer Python for now and refer to PHP as a secondary for web design.  Thank you.


The speed issue with python is a big "IT DEPENDS" , a look at some benchmarks will give a far from clear picture of how slow python is and even those benchmarks take impractical examples that do not do python justice. Underneath its skin python is C/C++ as this is where most of its libraries are based on, that is why there are function who made direct calls to C with minimum speed loss, if any. 

An example is pickle vs cpickle 

[http://209.85.129.132/search?q=cache:0q4uDdHpjX4J:www.python.org/doc/2.5/lib/module-cPickle.html+cpickle&cd=2&hl=el&ct=clnk&gl=gr&client=firefox-a](http://209.85.129.132/search?q=cache:0q4uDdHpjX4J:www.python.org/doc/2.5/lib/module-cPickle.html+cpickle&cd=2&hl=el&ct=clnk&gl=gr&client=firefox-a)

Bottom line is that python can be as fast as you want it to be and even in the rare case it cannot , it integrates C/C++ code from rather little (normal warpings) to almost automatic (boost python with py++).

I would not want force you away from PHP. I have no experience with the language and I would lie if I did not say that I would like at some point to study it. Afterall I believe that being flexible is what makes a good programmer.

---

### Post by DGortze380 on 2009-05-04
> **myrtle1908 said:**
> If anything, PHP has more in common with Perl than C++ and shell scripts.  After all it was created to encapsulate a bunch of Perl scripts.  Throw in CGI handling and you have PHP.

While you are correct about the origins of PHP. I do beg to differ. I was speaking to the syntax, structure and controls of actually using the language, not the historical connections. IMO it is very similar to writing in a combination of C++ and Bash.

End Off Topic Rant

---

### Post by Kilon on 2009-05-04
> **DGortze380 said:**
> While you are correct about the origins of PHP. I do beg to differ. I was speaking to the syntax, structure and controls of actually using the language, not the historical connections. IMO it is very similar to writing in a combination of C++ and Bash.

End Off Topic Rant

And when I first encountered C++ I thought it was nothing more than GWBASIC rip off.... I still do.... I guess perspective always plays a big role. Afterall originality is not programming languages' "forte",

---

### Post by CptPicard on 2009-05-04
... and here I am still wondering why exactly it is a good thing that something feels like a combination of C++ and bash, embedded into HTML most of the time.. :D

---

### Post by EndOn9 on 2009-05-04
> **myrtle1908 said:**
>  In fact, the choice of server-side technology for mine is not terribly important.  After all, it should really only be communicating with the database/service/whatever and spitting back something useful to the client eg. JSON/HTML/whatever.


Not necessarily, nearly all serious websites are built with a CMS these days and things can get a hell of a lot more complicated than that. Especially when you are up to your neck in E-Commerce code.

Back on topic...

I think your thinking about this far too much. If you are interested in web development then PHP is still flavour of the month so just jump and play with it for a while and see what you think. Python is a great and extremely flexible language and I would suggest trying it out. Perl is getting abit archaic but I've still yet too see a language with better integrated regular expressions (if someone else has then let me know!).

---

### Post by bigboy_pdb on 2009-05-04
Granted that you're a student, now is a good time to dabble in different languages and to figure out what you like.

With respect to front end development, there won't be too many arguments about what you'll need to know. Knowledge of HTML, CSS, and JavaScript are important. AJAX is becoming more widely used and JavaScript libraries such as JQuery can immensely simplify front end development.

With respect to back end development, there are more options and people get more defensive and emotional about their favourite languages/technologies. It would be good to use a few different languages to get an idea of what they do, but you should pick one and learn it well if you intend on working as a web developer. For popular languages, there are more help resources, but there will be more competition for employment. For less popular languages, there are fewer people to compete against, however, there are also fewer jobs to compete for. Thus, it would be best to just try a few languages and go with the language you like best because you'll want to learn more of it. If you've written bash scripts and you're familiar with progamming langauges from the C/C++ syntax family, PHP would probably be good to look into.

Also, your learning experience will probably be more enjoyable if you, first, envision a site that you want to create and, then, you attempt to create it. That way you'll encounter and fix more real world problems.

---

### Post by Reiger on 2009-05-04
> **CptPicard said:**
> ... and here I am still wondering why exactly it is a good thing that something feels like a combination of C++ and bash, embedded into HTML most of the time.. :D

I'd say it's rather different from Bash and rather closer to C/C++. That embedded in (X)HTML thing is something which you should actually try to avoid; unless you are strictly coding templates in which fields need to be filled in by the preprocessor (PHP). I think it's a bit of a "popular misconception" really: there is nothing in PHP that would require you to included HTML. PHP can be used like any scripting language: you are not restricted to HTML.

(Yes, core logic should be kept seperate from the (X)HTML for fear of melting your brains when you must maintain it afterwards.)

Incidentally with the use of header() (controlling HTTP response headers) you can achieve a lot of handy functionality easily:
[php]
<?php
header('Location: http://www.example.com'); /* let's redirect */
?>[/php]

[php]<?php header('Content-type: text/css'); /* let's dynamically generate a CSS file */ ?>[/php] 

[php]
<?
// force the client to bring up the download/save-as dialog
php header('Content-type: text/plain'); 
header('Content-disposition: attachment; filename="download.txt"');
readfile('/path/to/some/text/file.txt'); // read & write to STDOUT
?>
[/php]

EDIT: Oh and I'd be wary of using something that requires a framework to get a job done. There should be at least an intrinsic quality in the language that gets you from A to B; if you are a hammer all the world may be made of nails, but you are more sophisticated than a hammer right?

---

### Post by shatterblast on 2009-05-04
> **slavik said:**
> this is not making sense to me, can you restate your thought in the last sentence?

Whoops. I think I meant MySQL, and I automatically grouped MyPHP with it.  They are quite two different things.  I shall erase that in my first response.

---

### Post by shatterblast on 2009-05-04
> **myrtle1908 said:**
> Yes I was over-simplifying for the purposes of the discussion ... at least what I perceived it to be.  The point I was trying to make was that the server-side technology is but only a part of the web development cycle.

It seemed to me that the OP was talking about "web design" which really does not involve much server-side "glue" (despite the explicit mention of PHP).

Either way, it is hard to argue that a web-server(s) does much more than service its clients.  How it services them is another thing (which is perhaps the point you are making).

> **slavik said:**
> yes, it is my point and I understand what you are saying, but it feels as if you are disregarding server-side implementation.

design can be done in an image editing program, but architecture is in code. :)

I eventually intend to use XML as a basis for a database on a personal project.  The various forms of SQL seem commercially popular though I should stick with what I know first.

I also desire to extend slightly into the TCP/IP side of things via Java JNLP Web Start to server communication, but I consider that goal somewhat distant.  I figured Java could handle that load.

---

### Post by CptPicard on 2009-05-04
> **Reiger said:**
> I think it's a bit of a "popular misconception" really: there is nothing in PHP that would require you to included HTML. PHP can be used like any scripting language: you are not restricted to HTML.

I know, in theory, but there seems to be "something" about PHP that creates awful-looking solutions to problems... I do realize that it is probably the weakness of the programmer, but I wonder why there are so many weak programmers doing PHP.. ;)

> 
EDIT: Oh and I'd be wary of using something that requires a framework to get a job done. There should be at least an intrinsic quality in the language that gets you from A to B; if you are a hammer all the world may be made of nails, but you are more sophisticated than a hammer right?

This is an interesting proposition... I was over the winter involved in a [dotcom project]("http://lambdagrok.wikidot.com/how-not-to-do-a-dotcom") where the lead developer insisted on PHP and doing everything himself because he was "sophisticated" and did not want to make use of any frameworks. Eventually he even refused to actually let me see his side of the code as I was asking too many tough questions :D

Web apps are very much a known quantity -- they have been architectured to death, and there is certainly convergence these days -- so I have no issues using a general-purpose programming language without "intrinsic" qualities that make it suitable for web apps plus a framework that separates model, (simple template) views and controller code, which in turn is hopefully pretty much pure logic code. Well, ok, C may not be a suitable general-purpose language for web apps (why does PHP bother to make the value/reference semantics distinction?), but you catch my drift...

> **shatterblast said:**
> I eventually intend to use XML as a basis for a database on a personal project.

I am not sure why you would do that; it sounds like a pretty cumbersome proposition, in particular updating such files.

>   The various forms of SQL seem commercially popular though I should stick with what I know first.

Not only "commercially" popular... relational data storage is the backbone of IT, you need to understand it, period. And SQL is a standardized language; it's used by a lot of (most) relational database engine implementations.

> 
I also desire to extend slightly into the TCP/IP side of things via Java JNLP Web Start to server communication, but I consider that goal somewhat distant.  I figured Java could handle that load.

TCP/IP works on a much lower level. From our abstraction level here, it is nearly transparent.

---

### Post by shatterblast on 2009-05-04
> **bigboy_pdb said:**
> Granted that you're a student, now is a good time to dabble in different languages and to figure out what you like.

Please don't take this as me bragging or coming across as rude, but I have 20 years of exposure to 10 or more different languages.  I'm trying to avoid flavors of the moment.  "Ye olde" Basic still makes me shudder, and learning Pascal still hasn't benefited me much.  JavaScript use to make Windows 98 itself crash.  (Whee!)  I wish I learned C when I had the opportunity.  But no, everyone wanted C++.  "We'll never hire you if you learn C," I heard a couple of times.  Glory to goodness, things are much different in the land of Linux.

> **bigboy_pdb said:**
> With respect to front end development, there won't be too many arguments about what you'll need to know. Knowledge of HTML, CSS, and JavaScript are important. AJAX is becoming more widely used and JavaScript libraries such as JQuery can immensely simplify front end development.

I'm thinking of delving further into XHTML.  CSS intrigues me, but I haven't allocated time for it.  AJAX I'm not familiar with yet.

> **bigboy_pdb said:**
> With respect to back end development, there are more options and people get more defensive and emotional about their favourite languages/technologies. It would be good to use a few different languages to get an idea of what they do, but you should pick one and learn it well if you intend on working as a web developer. For popular languages, there are more help resources, but there will be more competition for employment. For less popular languages, there are fewer people to compete against, however, there are also fewer jobs to compete for. Thus, it would be best to just try a few languages and go with the language you like best because you'll want to learn more of it. If you've written bash scripts and you're familiar with progamming langauges from the C/C++ syntax family, PHP would probably be good to look into.

Good advice I think.  I have learned that when an individual knows something about a "scarce" language that I usually have a shadow of their knowledge.  I am like a rookie compared to a veteran in that respect.  I seem to keep picking up engineering-related work even if I prefer the science portion so I'm usually impressed when I meet someone in the field.  :lolflag:

> **bigboy_pdb said:**
> Also, your learning experience will probably be more enjoyable if you, first, envision a site that you want to create and, then, you attempt to create it. That way you'll encounter and fix more real world problems.

I work on simulations as personal projects.

> **CptPicard said:**
> I am not sure why you would do that; it sounds like a pretty cumbersome proposition, in particular updating such files.

I'm wanting something high level and low level depending on the complexity of a project I work on.  I'm thinking I may try to integrate XHTML with Python for web page layouts while later relying on Java for server-side implementation stuff.  XML has the ability for streamlining if the requirements are simple.  While it has the ability to operate more efficiently over the fastest version of SQL, SQL over all should be easier.  SQLite comes to mind.  And yes, XML can supposedly become very cumbersome to handle should its complexity reach a deep extent I think.  XML has a problem with either the existence or lack of proper templates, or something of that nature.

> **CptPicard said:**
> TCP/IP works on a much lower level. From our abstraction level here, it is nearly transparent.

I am considering that as a topic for a different day.  I may be wrong, but integrating XML with a TCP/IP data stream is suppose to be fairly comfortable and easy.  I think I read it could even be done through PHP to a Java client side application.  I tested one application that pulled it off.

---

### Post by Reiger on 2009-05-04
> **CptPicard said:**
> I know, in theory, but there seems to be "something" about PHP that creates awful-looking solutions to problems... I do realize that it is probably the weakness of the programmer, but I wonder why there are so many weak programmers doing PHP.. ;)



I think it's the same as with Java or JavaScript: it's a typical "first language" so to speak. Using a new language to tackle a new class of problems tend to result in less than optimal solutions; or even "conceputally OK" solutions. When you get well versed with the problem matter at hand and get to see a bit more of a language you will develop a set of "survival thechniques" and looking back you can't possibly fathom how clumsy your earlier attempts were.

> 

This is an interesting proposition... I was over the winter involved in a [dotcom project]("http://lambdagrok.wikidot.com/how-not-to-do-a-dotcom") where the lead developer insisted on PHP and doing everything himself because he was "sophisticated" and did not want to make use of any frameworks. Eventually he even refused to actually let me see his side of the code as I was asking too many tough questions :D

Web apps are very much a known quantity -- they have been architectured to death, and there is certainly convergence these days -- so I have no issues using a general-purpose programming language without "intrinsic" qualities that make it suitable for web apps plus a framework that separates model, (simple template) views and controller code, which in turn is hopefully pretty much pure logic code. Well, ok, C may not be a suitable general-purpose language for web apps (why does PHP bother to make the value/reference semantics distinction?), but you catch my drift...



Yes you are right in so far that when you develop "real" web apps you will want to use a framework. A bit like: the people who wrote frameworks are 99% of the time better than you at this kind of thing anyway (they wrote those frames to solve a whole lot of intrinsic architectural problems with a fell swoop), and for that 1% there is always the possibility to write your own customization layer on top of it.

*But* that is when your developing *real* stuff. Not when you are toying with a language to learn both that language and how you solve problems with it. At least I feel that if you develop the basic skill set to write apps with a given language from the ground up you will better appreciate what a framework does, and also better understand how it does things (which should reduce the 1% to 0.01%). EDIT: Which is to say that if you have the choice between X and Y and you are interested in solving problems of a given type, then it may be prudent to first learn X if X is inherently better at these problems than Y -- for instance because it was designed to _solve_ this kind of problem. Nothing wrong with learning to solve the same problems in Y, though.

It is a bit like: if you have seen how memory management works at the processor level you will be able to appreciate the memory management in the kernel a bit better, going up to realising why it is a bad thing to hardcode pointer-sizes in C/C++, going up to realising that C/C++ may not be such a great language to develop you app in if you do not need raw memory/device access... moving ultimately towards a much higher level of abstraction from the problem which is rather more productive. But if you never see something (if only just see the examples in a textbook) of the lower level management required to make your Python VM or JVM or Mono run like it does, it is more difficult to understand why they behave the way they do.

Or compare it to using Mathematica: if you never develop the basic skill set required to solve even for simple recursive equations, then how are you going to understand why Mathematica coughs up a given answer and not another one?

> I am not sure why you would do that; it sounds like a pretty cumbersome proposition, in particular updating such files.

I have done a similar thing for somehting which is slightly closer to a "real data base problem even". If you do not have dedicated data base servers to play with; have a problem which inherently involves recursivity then XML tied to XSLT/XPath can be a very flexible proposition: you can hide a lot of the more raw XML stuff in XSLT by supplying appropiate templates to make it more accessible from your given language.

---

### Post by CptPicard on 2009-05-04
Regarding the whole framework issue -- yes, a framework should not "dictate" too much, and the underlying stuff ought to be accessible for those cases when you need it. Then again, I am not 100% sure that doing crappy by-hand designs at first is particularly helpful even as a learning experience.. :)


> **Reiger said:**
> I have done a similar thing for somehting which is slightly closer to a "real data base problem even". If you do not have dedicated data base servers to play with; have a problem which inherently involves recursivity then XML tied to XSLT/XPath can be a very flexible proposition

Hmm, sounds like a rather specific need. May work fine for what you did, but I am not sure one would go down that sort of route in the general case as first solution. And of course that still is rather read-only, lacks referential integrity and all that...

---

### Post by stevescripts on 2009-05-04
> **CptPicard said:**
> I know, in theory, but there seems to be "something" about PHP that creates awful-looking solutions to problems... I do realize that it is probably the weakness of the programmer, but I wonder why there are so many weak programmers doing PHP.. ;)
...


Perhaps it is the ***boatload*** of bad/poorly crafted PHP code readily available for them to snag off the net, and include in their work?

---

### Post by Can+~ on 2009-05-04
Funny that the OP first wanted speed but still limited to the access speed of a hard disk for requesting data from a Database (and later, from XML?). Even if your table (or xml text file) is totally allocated in memory, web applications are not speed critical, think that an operation on a processor take less than a nanosecond, but you'll be bound to an internet connection, hard disk reads, pretty much the reason why no one sets up a server on assembly.

You're clearly leaping to early into a lot of things, go tackle one after another, there's considerable amount of time to learn each one, trying them all at once will lead you only to disappointment.

---

### Post by shatterblast on 2009-05-04
> **Can+~ said:**
> Funny that the OP first wanted speed but still limited to the access speed of a hard disk for requesting data from a Database (and later, from XML?). Even if your table (or xml text file) is totally allocated in memory, web applications are not speed critical, think that an operation on a processor take less than a nanosecond, but you'll be bound to an internet connection, hard disk reads, pretty much the reason why no one sets up a server on assembly.

You're clearly leaping to early into a lot of things, go tackle one after another, there's considerable amount of time to learn each one, trying them all at once will lead you only to disappointment.

I prefer to look at it as setting goals.  The phrase "divide and conquer" might seem appropriate here.  Some languages serve better at certain goals than others.  I have no desire to point out any language as bad, but I prefer to maximize my learning to reduce the effort necessary to create software.  I also like things incredibly complex so that I can simplify and optimize.  It helps me to know why.

Hard drive speeds are a non-issue for me.  I find Python appealing because it happens to exist as general-purpose anyway.  My original intent for that language was to allow modules as plug-ins in for a personal Java project.  How ever, I delayed that since I'm researching an OpenGL GUI at the moment.

PHP seemed interesting because of its popularity.  I only leaned towards Python because I can separate my need for efficiency from utility.  Also, Python integrates with a couple of other software packages that I happen to like.  I may have to study on the differences between Python and PHP for now.

Thank you all for the input.  This provides me more information to consider.  :-\"

---

### Post by Can+~ on 2009-05-04
> **shatterblast said:**
> I prefer to look at it as setting goals.  The phrase "**divide and conquer**" might seem appropriate here.  Some languages serve better at certain goals than others.  I have no desire to point out any language as bad, but I prefer to maximize my learning to reduce the effort necessary to create software.  I also like things incredibly complex so that I can simplify and optimize.  It helps me to know why.

Hard drive speeds are a non-issue for me.  I find Python appealing because it happens to exist as general-purpose anyway.  My original intent for that language was to **allow modules as plug-ins in for a personal Java project.**  How ever, I delayed that since I'm researching an** OpenGL GUI** at the moment.

**PHP seemed interesting** because of its popularity.  I only leaned towards Python because I can separate my need for efficiency with utility.  Also, Python integrates with a couple of other software packages that I happen to like.

You delayed a Java plugin project for a OpenGL GUI and now you're pursuing PHP or Python for a web app that changed from the original Database to a XML file.

Divide and conquer indeed. But you're diving, what? the whole programming universe?

> I have no desire to point out any language as bad, but I prefer to maximize my learning to reduce the effort necessary to create software.

That's great, specially if you want to learn a bit of everything, but do it right.

Sorry to be so sarcastic, but I was exactly like you, pursuing everything, ending up with nothing; until I set up a goal and didn't gave it up until accomplished.

> PHP seemed interesting because of its popularity.

I would be on windows programming in C++ and posting with Internet Explorer if it were by popularity.

---

### Post by CptPicard on 2009-05-04
> **shatterblast said:**
> I prefer to look at it as setting goals.  The phrase "divide and conquer" might seem appropriate here.  Some languages serve better at certain goals than others.  I have no desire to point out any language as bad, but I prefer to maximize my learning to reduce the effort necessary to create software.  I also like things incredibly complex so that I can simplify and optimize.

Well, perhaps you "divide and conquer" by making your learning process as contrived as possible, but it seems to me that you're mostly just speculating all over the place with rather vague grasp of what you're dealing with. Going from here it's pretty hard to see you meaningfully "simplifying and optimizing". It may be more appropriate to take some logical, proven approach to whatever you're doing and just asking more specific questions when you run into problems.

> 
Hard drive speeds are a non-issue for me.

Why not? Web apps are I/O bound. Hard drive speeds are definitely not a non-issue.

> My original intent for that language was to allow modules as plug-ins in for a personal Java project.

... by using Jython I guess?

> I only leaned towards Python because I can separate my need for efficiency with utility.

What exactly is this need of yours for efficiency? A matter of principle? If you're running some heavy algorithms in your web app, you may want to write a C extension for Python... but you don't need that unless you need that...

---

### Post by Reiger on 2009-05-04
> **CptPicard said:**
> What exactly is this need of yours for efficiency? A matter of principle? If you're running some heavy algorithms in your web app, you may want to write a C extension for Python... but you don't need that unless you need that...

Or cache results if applicable. This is usually a conceptually straightforward and easy way to gain a lot of performance at little cost; especially for otherwise static content which is required to be regenerated at specific intervals. (Think: updating a site with contents of external RSS feeds.)

---

### Post by CptPicard on 2009-05-04
> **Reiger said:**
> Or cache results if applicable.

Yes, naturally. The "need for speed" here is vague enough that the *specifics* of web app optimization are not really relevant yet.. :)

---

### Post by DocForbin on 2009-05-04
The main reason php is so popular is just that it is ubiqutous among cheap web hosting providers. Tons of websites use php for basic stuff like a mail form because that's what was available to use on the  $20/month they signed up for years ago.

Someone early on said php usage is on the decline. I'm curious if this is actually true.

PHP.net stats are old, but shows a sharp decline in 05-06, then a steady rise from 06-07.

[IMG]http://img219.imageshack.us/img219/9097/phpstats200707.png[/IMG]

From [TIOBE]("http://www.tiobe.com/index.php/paperinfo/tpci/PHP.html") 

[IMG]http://img219.imageshack.us/img219/8135/historyphp.png[/IMG]

That site puts PHP as the 4th most used language currently, with 9.921%, under Java(19.537%), C (16.128%), and C++ (11.068%). Really only Java competes with PHP on the web server today (I mean strictly in terms of usage, of course).

With the java app engine support now, Google seems to have solved for java what I would guess is one of the main reasons cheap hosts offer php: easy sandboxing (let losts of people run lots of different, self-contained, sandboxed php scripts on one server).

---

### Post by slavik on 2009-05-04
so, to conclude this thread, learning PHP is not a bad thing ... is there anything else left to discuss here?

---

### Post by Dr.Vista on 2009-05-04
You should, it allows you to create very dynamic content where a user can interact with a page and save information to it. Its pretty easy to learn as well.

---

### Post by DocForbin on 2009-05-04
> **slavik said:**
> so, to conclude this thread, learning PHP is not a bad thing ... is there anything else left to discuss here?

translation: Slavik is bored with this thread

---

### Post by shatterblast on 2009-05-05
> **CptPicard said:**
> What exactly is this need of yours for efficiency? A matter of principle? If you're running some heavy algorithms in your web app, you may want to write a C extension for Python... but you don't need that unless you need that...

Just to entertain Mister Picard, I usually find it entertaining when I can take a computer system worth a fifth of the amount of some other system and make it perform equally.  That is one of the beauties of Linux, though I can do the same thing with Microsoft products and hardware choices.

A personal computer worth $1,500?  I can go pick pieces worth $400, include a flat-screen monitor in that total, and get roughly comparative performance.  Sometimes, a system will exceed in one area yet fall behind in another.  (Shopping for deals on my preferred hardware can take 2 months.)  Most of my computer career has involved tweaks, changes, and so on for recycling both hardware and software as silly as that might sound.  The last computer company I worked for found an old copy of Windows 3.11 still in their storage bins.  :confused:

Anyhow, I just wanted to learn something else so I can throw stuff together for friends, the church, and so on.  My desire for speed and such is really like a personal hobby.  I could compare it someone who likes to ride his or her motorcycle though I don't personally own one yet.  I only tweak a system when I can call it "mine" for some amount of time.  I won't do that for co-workers or company servers usually, but I will when a customer requests a special load of some sort.  It's sort of like a signature on a piece of art to me.

---

### Post by slavik on 2009-05-05
the thing to lookout for is what is called "premature optimisation" and making sure you are solving the correct problem. with that said, I am of the opinion that having efficiency in the back of your head is also a good idea.

---

### Post by shatterblast on 2009-05-06
I am guilty of that.

---

### Post by salvachn on 2009-05-06
I suggest  you jump right in if you want to develop code by hand, else try PHPRunner if you wanna use a database. SQL is pretty easy.

---

### Post by Mickeysofine1972 on 2009-05-06
Having worked with PHP since I got into linux around 3 - 4 years ago I've had a consistently more successful employment history in that I have tripled my wages in that time and been involved in loads of projects and gained loads of experience.

Next month I'm going to work for another company using Python, which for me is "th future". 

But I honestly believe that there are two good decisions I made when this all started.

1) I switched to linux
2) I learned a programming language that for the foreseeable future, will provide me with a guaranteed income.

PHP is really just a great decision on the part of the developer and the client. Its cost effective, you can get it anywhere on the net and you can develop all the latest technologies with it.

That means when a client asks for the latest buzz word to be a feature of his site you can pretty much say yes to the request and that means you will win more clients becuase of easy of service aquisition and cost.

Like I said, I'm moving job at the end of this month but I will still be using PHP as my web development language becuase when I google for web hosting I just dont see anyone offering me a serious setup with any other language support at the same costs.

I get PHP5 and Mysql for about £2.90 a month for my hosting. I dont imaging I could get a equal service on a windows based setup.

well that all I have to offer, hope that gives you and insight.

Mike

---

