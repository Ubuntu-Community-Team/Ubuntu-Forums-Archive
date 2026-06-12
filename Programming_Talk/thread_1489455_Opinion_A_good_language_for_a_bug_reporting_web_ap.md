---
title: "Opinion: A good language for a bug reporting web app?"
date: 2010-05-21
forum: Programming Talk
---

### Post by PrototypeAlex on 2010-05-21
Hello all, 

At the moment I am doing an assignment on project management at Massey university all the way down in New Zealand. We have to estimate the effort required to develop bugzilla using Function Point analysis. I have already done the work, but the final part (its just for fun) is to pick a programming language that you would develop it in. 

I was just wondering if anyone had opinions on the languages out there that are suited to this. I was thinking Ruby on Rails, it looks very fast with it frameworks, but i have no experience so I'm just going by what I've read about it on the net. 

Any opinions out there would be greatly appreciated.

---

### Post by new_tolinux on 2010-05-21
Wouldn't any web application require something like PHP, at least for the server side that is.

For the client I have no idea.

---

### Post by r-senior on 2010-05-21
So it's basically a web application with a database backend? The main choices that would spring to mind would be:

[PHP](http://en.wikipedia.org/wiki/Php) & MySQL - along with Apache, the AMP in [LAMP](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

[Ruby on Rails](http://en.wikipedia.org/wiki/Ruby_on_Rails) - again, probably integrated with Apache and MySQL. Look into Ruby Gems and package management.

[Groovy/Grails](http://en.wikipedia.org/wiki/Grails_%28framework%29) - rapid development but still access to the range of APIs in Java, e.g. [Hibernate](http://en.wikipedia.org/wiki/Hibernate_%28Java%29) for database persistence. Pick any database really.

[Java EE](http://java.sun.com/javaee/) - many permutations possible but the major paths would be [JSF](http://java.sun.com/javaee/javaserverfaces/) and [EJB](http://java.sun.com/products/ejb/) or [Spring](http://www.springsource.org/about) and Hibernate. Need application server to run - e.g. Tomcat for Spring/Hibernate, but EJB applications need full-blown application servers like Glassfish and WebSphere. EJB is really moving into the global enterprise application scale of things, i.e. sledgehammer to crack nut.

Or there's the "other side" of course ... [.NET](http://www.microsoft.com/net/) ;)

EDIT: @new_tolinux - the point (and indeed, value) of a web application is that you don't need client software. The browser becomes the client software standardised through HTTP/HTML/XML/JavaScript support so there's nothing to write or install for the client side.

---

### Post by Mordred on 2010-05-21
You could also do it in python using django.

---

### Post by new_tolinux on 2010-05-21
> **r-senior said:**
> EDIT: @new_tolinux - the point (and indeed, value) of a web application is that you don't need client software. The browser becomes the client software standardised through HTTP/HTML/XML/JavaScript support so there's nothing to write or install for the client side.

Ok, I was thinking about the bug-report system in *buntu, which has a client-side outside the browser (collecting system-info etc.).

---

### Post by slavik on 2010-05-21
> **new_tolinux said:**
> Ok, I was thinking about the bug-report system in *buntu, which has a client-side outside the browser (collecting system-info etc.).
still, the answer is anything. your app can do a post with XML to some webservice written in anything.

as for tomcat, it's not a j2ee server, it's a container. jboss and weblogic are other j2ee servers.

---

### Post by soltanis on 2010-05-21
Just about any language (no actually, any language) with suitable I/O routines and DB bindings could do this. What I'd personally suggest is Python with web.py though.

---

### Post by weezerBo on 2010-05-21
> **Mordred said:**
> You could also do it in python using django.
WIN. A friend asked me to take on a project for his startup, and at the time my knowledge of python was limited and my knowledge of django was next to non-existent, and I had 0 experience in web development. But I was able to complete it within a month. It works perfectly.

Having SQL abstracted away is probably the biggest win of all.

---

### Post by PrototypeAlex on 2010-05-21
> **r-senior said:**
> 

Or there's the "other side" of course ... [.NET](http://www.microsoft.com/net/) ;)


The sad thing about that is first and second year at Massey University has been taken over by .net (I think they must be funding us), So most of the students will probably pick C# or C++. :(

---

### Post by PrototypeAlex on 2010-05-21
> **soltanis said:**
> Just about any language (no actually, any language) with suitable I/O routines and DB bindings could do this. What I'd personally suggest is Python with web.py though.

Hmmm, well I guess my next question then is how do you make the choice of programming languages when creating a game plan for project?

Is it just down to personal experience and knowledge?

---

### Post by new_tolinux on 2010-05-21
> **PrototypeAlex said:**
> Hmmm, well I guess my next question then is how do you make the choice of programming languages when creating a game plan for project?

Is it just down to personal experience and knowledge?
Afaik: yes
I would write something in PHP with a MySQL backend because that's about the only "modern" thing I know.

Long time ago I did a lot of programming in various DOS languages, but beside my knowledge about database structures and some basic "start1-start2-finish2-finish1" rules of programming that's not of any use to me anymore. It's more of a problem because sometimes I know how to do it in those languages, but can't find a simple way to it in PHP. Most times that's also my lack of knowledge, because it happens very regular that I find a simple way to do it in PHP afterwards. Didn't follow any course about it, didn't have any proper education on it, only use the PHP-manual from PHP.net in CHM-format to find my way (beside Google ofcourse ;))

I'm thinking about starting another language beside PHP, but since I can do almost everything I need/want with PHP, it seems of no use. Beside that, I really don't know which one to pick. So I'll probably stick with PHP for the near future.

---

### Post by harx1337 on 2013-03-28
> **new_tolinux said:**
> Wouldn't any web application require something like PHP, at least for the server side that is.

For the client I have no idea.

This. You'll have little complex logic here so why go with anything more complex?

---

### Post by mharv on 2013-03-30
C or Assembly. Your application doesn't require garbage collection or a full suite of run-time diagnostics so these people recommending Python and PHP are not recommending the correct tool for the job.

For the client your only choice is JavaScript.

---

### Post by r-senior on 2013-03-30
I am intrigued by the suggestion of using assembler to write a web application. Could you expand on your reasoning?

Would you plug assembler modules into a web server like Apache? Or would you write everything, right down to sockets?

---

### Post by mharv on 2013-03-30
Sockets are already written by the kernel developers and the C libraries already provide useful interfaces so I would not rewrite anything.I would use existing libraries as much as possible ([http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/) and [http://dev.mysql.com/doc/refman/5.0/en/c-api.html](http://dev.mysql.com/doc/refman/5.0/en/c-api.html)) the logic could be written in assembler though OR C since needing to port to another architecture is very unlikely and definitely will never be necessary (or even beneficial).

---

### Post by r-senior on 2013-03-30
Would you be able to use the libcurl and mysql APIs from assembler?

Are you saying that Python and PHP are only appropriate choices if there is an immediate need to create a cross-platform web application?

---

### Post by mharv on 2013-03-30
Yes you can link to any C library from assembler and the other way around (Both are also accessible from any other high level language implementation but NOT the other way around). I'm saying Python and PHP are only appropriate choices if there is an immediate need to create a cross-platform web application AND you don't know C or assembly yet.

C is shorthand for assembly (and there are some other differences) but it is not shorthand enough to outweigh familiarity, so I would personally consider them interchangeable because of their ability to link together and would use whichever one was freshest in my mind at the time.

---

### Post by ofnuts on 2013-03-31
> **mharv said:**
> Yes you can link to any C library from assembler and the other way around (Both are also accessible from any other high level language implementation but NOT the other way around). I'm saying Python and PHP are only appropriate choices if there is an immediate need to create a cross-platform web application AND you don't know C or assembly yet.

C is shorthand for assembly (and there are some other differences) but it is not shorthand enough to outweigh familiarity, so I would personally consider them interchangeable because of their ability to link together and would use whichever one was freshest in my mind at the time.

Python and PHP are appropriate choices when you look at developer's productivity. The Python programmer will be having a beer to celebrate a succesul delivery when you will still be struggling with memory allocation problems in that C routine that receives uploaded files.

---

### Post by mharv on 2013-04-01
"struggling with memory allocation problems". I guess I'm just smarter than you.

---

### Post by lisati on 2013-04-01
From the forum rules:

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

This is a three-year-old thread that has somehow come back to life.......

---

