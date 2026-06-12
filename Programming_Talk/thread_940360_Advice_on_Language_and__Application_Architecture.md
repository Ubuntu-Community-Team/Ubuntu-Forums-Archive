---
title: "Advice on Language and  Application Architecture"
date: 2008-10-06
forum: Programming Talk
---

### Post by stefanadelbert on 2008-10-06
I am a C++ developer with a bit of C++ on Linux experience. I would like to write a multi-user, client/server application with the following high-level specs:

* Remote database on a Linux server
* Server-side application running on a Linux server
* Web interface (i.e. accessible from anywhere)

The application will manage stock levels and orders, manage clients and suppliers.

I'm looking for some architecture recommendations. I think the database should be MySQL, the server should be Apache2. I would like to code this up in an OO language on Linux. What language should I look at? Maybe PHP. Which IDE's are recommended? I'm looking at BlueFish. Are there any tools/API's that make interfacing with a MySQL easy (easier)?

I look forward to your suggestions.

Many thanks
Stefan

---

### Post by tinny on 2008-10-06
Do you know any OO language other than C++?

With the amazing frameworks that we have available to us nowadays architecture is becoming less and less of an issue. Usually you will just follow the frameworks way of doing things and before you know it you have been hand held to a good architecture.

In general I would go with a framework that promotes MVC, which one would depend on what OO language you might know or are prepared to learn.

My own biased suggestion would be Groovy on Grails.

---

### Post by stefanadelbert on 2008-10-06
C++ is the only OO language that I really know. I've fiddled with C# and Java a bit and then with other pseudo OO languages (VB). I don't mind learning another language at all - actually I would like to. But I would like to choose a language/environment/architecture that makes sense based on the tools we have avialable to us on Linux (Ubuntu, Gnome) at the moment and the way things are going development-wise in general.

I was talking to a mate recently who works with MVC, MySQL and PHP and is stoked with it all.

I'll do a little research into Groovy/Grails though. Thanks for the suggestion.

Stefan

---

### Post by tinny on 2008-10-06
> **stefanadelbert said:**
> C++ is the only OO language that I really know. I've fiddled with C# and Java a bit and then with other pseudo OO languages (VB). I don't mind learning another language at all - actually I would like to. But I would like to choose a language/environment/architecture that makes sense based on the tools we have avialable to us on Linux (Ubuntu, Gnome) at the moment and the way things are going development-wise in general.

I was talking to a mate recently who works with MVC, MySQL and PHP and is stoked with it all.

I'll do a little research into Groovy/Grails though. Thanks for the suggestion.

Stefan

FYI: 

Groovy is the new school language for the Java environment (the JVM). Groovy leverage's from lessons learned from Java, Ruby and Python (probably in that order).

Grails is basically a rip off of the popular Rails web framework.

---

### Post by stefanadelbert on 2008-10-07
Thanks, Tinny.

What IDE would you recommend for Groovy? I believe that there is a Groovy plugin for Eclipse (I've used Eclipse on Windows before for C++). Also just read up a bit on IDEA. Seems that IDEA is favoured.

Stefan

---

### Post by tinny on 2008-10-07
> **stefanadelbert said:**
> Thanks, Tinny.

What IDE would you recommend for Groovy? I believe that there is a Groovy plugin for Eclipse (I've used Eclipse on Windows before for C++). Also just read up a bit on IDEA. Seems that IDEA is favoured.

Stefan

Im using the Eclipse plugin and its ok. I think the NetBeans support will be awesome! But its currently in beta (NetBeans 6.5), im waiting for the full release.

Ive tried this beta and its really good.

---

### Post by stefanadelbert on 2008-10-07
Anyone coding in C# on Linux? Is there a LINQ port available for Linux? Is it actually feasible to look at C# on Linux? I could do with the exposure to C# - plenty of C# jobs out there!

I reckon that the transition to C# from C++ would be an easyish one, but if there are better tools out there than Mono...

---

### Post by tinny on 2008-10-07
You may have to explain a little more about what it is you are wanting to achieve at the end of this exercise.

Do you want to learn something to use for a Job? (Java + Struts or Spring, C# .Net)

Do you want to create a Web 2.0 type application? (Rails, Grails, TurboGears, Django)

Do you want to do some full on enterprisey system? (EJB, Spring)

Do you want to be a linux hacker? (Python, C/C++)

The suggested answers to your questions will vary depending on your goal.

E.g. The best tool for the Job will not be the best to for getting a job. Strange but true. I write enterprise systems (bank / insurance) and the tools I use are rubbish! If I could use Groovy + Grails for work it would be a dream.

---

### Post by l3dx on 2008-10-07
> **stefanadelbert said:**
> Anyone coding in C# on Linux? Is there a LINQ port available for Linux? Is it actually feasible to look at C# on Linux? I could do with the exposure to C# - plenty of C# jobs out there!

I reckon that the transition to C# from C++ would be an easyish one, but if there are better tools out there than Mono...

Mono 2.0 just have just been released(huge "face lift":) ). I haven't tried it, but the front pages says that LINQ now is supported!

Mono is definitively the best .NET implementation for Linux as I know of...

---

### Post by pmasiar on 2008-10-07
If you try to do web-based app in anything but Python or Ruby, you are wasting your time. Python+Turbogears or Django will save you 95% efforts.

---

### Post by tinny on 2008-10-07
> **pmasiar said:**
> If you try to do web-based app in anything but Python or Ruby, you are wasting your time. Python+Turbogears or Django will save you 95% efforts.

Really? Is Groovy and Grails not even worth a look?

EDIT: It is by the way! Groovy borrows a lot from both Ruby and Python. Grails is Rails++.

Ive had a play with Django and yep its fantastic! Grails is fantastic too. For the time being I am using Grails because it allows me to transfer a lot of my Java experience.

---

### Post by CptPicard on 2008-10-07
I hate to say this regarding TG, but I still like the robust feel of enterpriseyness I get from Java-based web development, and Grails looks like a huge step in the right direction to make the unnecessary complex crap go away. In TG I still get this feeling of "scripting on top of Apache"... it seems like even request parameter and session handling is rather low-level still compared to how Java app servers do it.

Grails really seems like [best of both worlds]("http://en.wikipedia.org/wiki/The_Best_of_Both_Worlds_(TNG_episode)")... at least I am not yet [advocating using mostly Mono]("http://www.youtube.com/watch?v=Ub_DPM_YYkQ")...

(Interestingly, Best of Both Worlds pt 1 was the first ever ST episode I ever saw...)

---

### Post by tinny on 2008-10-07
Yes, "best of both worlds". Or I think its more accurate to say that you can choose which world to be in as you go.

E.g 

Groovy allows you to seamlessly traverse between the dynamic and statically typed worlds. Java code is valid Groovy code and Groovy can interoperate with standard Java classes (Java classes can also call groovy code). But you can write perfectly valid applications without ever having to write a line of Java code if you like.

Grails has enterprisey infrastructure under the hood. Grails is built on Spring and Hibernate. The really nice thing is that you dont have to worry about either of these two technologies unless you want too. Grails provides a sort of ORM facade over the top of Hibernate called GORM (No prise for guessing that acronym). GORM is nice and simple :-)

As for the spring part... 

The simplification hear is auto wiring and convention over configuration approaches.

[http://grails.org/Spring+Integration](http://grails.org/Spring+Integration)

So if you want dependency injection use the above, if you dont want it then dont use it. (Controllers are automatically “wired up” by following a convention over configuration approach)

Summary: The few concepts (there are more) I detailed above are very powerful and give you that enterprisey infrastructure if you want it. But the really powerful thing is that if you dont understand what im talking about above you dont need to worry about it as the framework will hold your hand.

---

### Post by themusicwave on 2008-10-07
> **tinny said:**
> Ive had a play with Django and yep its fantastic! Grails is fantastic too. For the time being I am using Grails because it allows me to transfer a lot of my Java experience.

I just checked out the grails site and it is interesting.  I know both Python and Java, but I have more experience in Java.  However that is all in Java SE, strange, but true...

I've been looking at lots of web frameworks for a big idea I have(shhh it's a secret).  I am still leaning toward Django, but I will also consider grails.  I have been watching Groovy for quite awhile now.  Only played with it a bit.

I'll probably still go with a more established Python framework like Django, but it is cool to see what is out there for Groovy as well.

---

### Post by tinny on 2008-10-07
> **themusicwave said:**
> I just checked out the grails site and it is interesting.  I know both Python and Java, but I have more experience in Java.  However that is all in Java SE, strange, but true...

I've been looking at lots of web frameworks for a big idea I have(shhh it's a secret).  I am still leaning toward Django, but I will also consider grails.  I have been watching Groovy for quite awhile now.  Only played with it a bit.

I'll probably still go with a more established Python framework like Django, but it is cool to see what is out there for Groovy as well.

Both Grails and Django are at version ~1.0.x stages...

But Django has Googles support (Default in google app engine).

---

### Post by CptPicard on 2008-10-07
> **themusicwave said:**
> 
I'll probably still go with a more established Python framework like Django,

The underlying Java stuff is EXTREMELY established mind you :)

---

### Post by stefanadelbert on 2008-10-07
Thank you all for your input on what I reckon is a very interesting (if somewhat subjective) topic.

To answer the questions that Tinny posed earlier (quoted below), I'm hoping to put together a system that I can use for a home business startup (equipment hire) and also learn something useful along the way (for future job prospects should the business go South).

It would be useful to learn C# as there are plenty of job prospects out there (regrettably confined to MS development it seems).

I reckon it would make sense to go Web 2.0, but the application requirements are VERY straight forward so it might not be necessary.

Enterprisey would make sense, as the system would initially have two users but should be able to cope with more (from different, remote locations) and would have the classic data contention issues of any similar system.

Of course I want to be a Linux Hacker! Who doesn't?!? Seriously, I've got some C++ experience which I would like to leverage off if I can, but I'm not married to C++. In fact, I would like a change, which is one of my big reasons behind this post.

I've written distributed systems in C++ on Linux for banks and the tools we used were shockingly crap. If we'd had powerful tools at our disposal, we would have been capable of way bigger and better things (and the bank may not have gone plop, hint hint).

I'm going to setup Groovy/Grails and run through a few tutorials and see what I think. I'm sure I'm going to be swung by the development tools rather than the language in the end.

Further recommendations welcome, chaps!

Stefan

> **tinny said:**
> You may have to explain a little more about what it is you are wanting to achieve at the end of this exercise.

Do you want to learn something to use for a Job? (Java + Struts or Spring, C# .Net)

Do you want to create a Web 2.0 type application? (Rails, Grails, TurboGears, Django)

Do you want to do some full on enterprisey system? (EJB, Spring)

Do you want to be a linux hacker? (Python, C/C++)

The suggested answers to your questions will vary depending on your goal.

E.g. The best tool for the Job will not be the best to for getting a job. Strange but true. I write enterprise systems (bank / insurance) and the tools I use are rubbish! If I could use Groovy + Grails for work it would be a dream.

---

### Post by tinny on 2008-10-07
> **stefanadelbert said:**
> 
Enterprisey would make sense, as the system would initially have two users but should be able to cope with more (from different, remote locations) and would have the classic data contention issues of any similar system.


Trust me, Enterprisey doesn't make sense for your application.  Enterprisey implementations are only really necessary when you are concerned with a wider distributed type problem domain. 

E.g. 

If your are selling car insurance online you will need to talk to a vehicle insurability service, post code service, centralised customer details repository, premium rating service, policy creation service and a payment gateway.  Enterprisey architecture becomes fesiable when you are dealing with having to wire up all of these types of distributed services.  

YouTube has more users than you are ever likely to have right? They are not Enterprisey.

The BEST thing you could do is keep it simple!

---

### Post by stefanadelbert on 2008-10-07
I've just had a look at a screencast on Scaffolding on the Grails site and I am literally blown away by how powerful Grails appears to be. I can't wait to get it all installed at home and start fiddling.

I'm a big believer in keeping it simple, but also in doing it properly. I believe that these are not necessarily two mutually exclusive objectives and it's a compromise that I'm seeking here, I suppose.

Tinny, could you please recommend some good Groovy/Grails resources? I'm the kind to learn from tutorials and "doing" rather then reading up, so some solid examples and tutorials would be a massive help for me.

---

### Post by stefanadelbert on 2008-10-07
To respond to my own request, here are some (potentially) useful links re. Groovy/Grails for those embarking on a similar mission to mine:

[http://grails.org/Home]("http://grails.org/Home")
[http://www.anyware.co.uk/2005/grailsrocks/]("http://www.anyware.co.uk/2005/grailsrocks/")
[http://www.indicthreads.com/news/541/groovy_grails_tutorial.html]("http://www.indicthreads.com/news/541/groovy_grails_tutorial.html")
[http://www.ibm.com/developerworks/java/library/j-grails01158/]("http://www.ibm.com/developerworks/java/library/j-grails01158/")
[http://apachecon.com/2006/Asia/wp-content/presentations/GroovyGrailsTutorial.pdf]("http://apachecon.com/2006/Asia/wp-content/presentations/GroovyGrailsTutorial.pdf")

I'll try and stick anything useful info I find in this thread. Anyone else out there gone down a similar route recently? Anyone got any good Groovy/Grails resources to share or advice to proffer?

Stefan

---

### Post by tinny on 2008-10-07
> **stefanadelbert said:**
> I've just had a look at a screencast on Scaffolding on the Grails site and I am literally blown away by how powerful Grails appears to be. I can't wait to get it all installed at home and start fiddling.

I'm a big believer in keeping it simple, but also in doing it properly. I believe that these are not necessarily two mutually exclusive objectives and it's a compromise that I'm seeking here, I suppose.

Tinny, could you please recommend some good Groovy/Grails resources? I'm the kind to learn from tutorials and "doing" rather then reading up, so some solid examples and tutorials would be a massive help for me.

Hmmm, Grails is a little lite on the tutorial resources right now.

I personally like books. I have just worked through this book.

[http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451](http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451)

If you have a programming back ground then I believe this book is for you.

Obviously there's the Grails site, but its no where near as structured as the book ive just worked through.

[http://grails.org/Tutorials](http://grails.org/Tutorials)

---

### Post by tinny on 2008-10-07
Here is a free book

[http://www.infoq.com/minibooks/grails](http://www.infoq.com/minibooks/grails)

---

### Post by CptPicard on 2008-10-07
> **tinny said:**
> 
I personally like books. I have just worked through this book.

[http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451](http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451)

+1

Nice, that book just pushed my current Amazon shopping cart over the limit to actually making an order... :)

---

### Post by slavik on 2008-10-07
if you want to write something along the lines of a stock trading client/server thing using simple http, you have already failed. the reason is because your server will have to push data to the clients (it would probably be best by keeping the connection open).

if you do anything 'web based' (meaning there is a web server and web browser involved) then expect to look into something like comet. ([http://en.wikipedia.org/wiki/Comet_(programming](http://en.wikipedia.org/wiki/Comet_(programming)))

what you use server side (Perl, Python, Ruby) will pretty much talk to the C++ server code.

in my opinion however, the path of least resistance would probably be to learn to use a GUI framework (gtk/qt/tk/wx ... whatever has what you want for this project) and then to write a server component that listens for connections and a client components (the GUI).

Although maybe an Ajax page that opens an http request and data is pushed through that could be easier.

Either way, the code should not be very complicated.

---

### Post by stefanadelbert on 2008-10-07
My aim is to use OO code to represent the entities in the application (stock item, customer, supplier, booking, etc.). I would like to persist instances of the entities in a database. I would like to be able to interact (create, edit, delete, etc.) with the instances via a web browser from anywhere (implying a server supplying web services).

I would defintely like to avoid rich client (e.g. GTK or some winforms equivalent).

Because I have no experience with archtectures of this type, I'm looking for some solid advice on which architectures would make sense, which components to use, which tools are available; given that I would like to do all the work on Linux and have everything running on Linux.

It seems to me that Groovy/GRail is very nicely suited to these requirements. Thank you for your suggestions though. I'll take a look into Comet.

Stef

---

### Post by pmasiar on 2008-10-07
> **tinny said:**
> Groovy allows you to seamlessly traverse between the dynamic and statically typed worlds. Java code is valid Groovy code and Groovy can interoperate with standard Java classes (Java classes can also call groovy code). But you can write perfectly valid applications without ever having to write a line of Java code if you like.

Grails has enterprisey infrastructure under the hood. Grails is built on Spring and Hibernate. The really nice thing is that you dont have to worry about either of these two technologies unless you want too. Grails provides a sort of ORM facade over the top of Hibernate called GORM (No prise for guessing that acronym). GORM is nice and simple :-)

Interesting. Thanks for bringing it up.

Rails was such a brilliant idea: "convention instaed of configuration". Use introspection of dynamic languages to make code look simpler.

Now everyone is doing it, but Rails was first, and powered the Ruby revolution.

I'll try to sell Groovy instead of Java to my boss... :-/

---

### Post by tinny on 2008-10-07
> **slavik said:**
> 

in my opinion however, the path of least resistance would probably be to learn to use a GUI framework (gtk/qt/tk/wx ... whatever has what you want for this project) and then to write a server component that listens for connections and a client components (the GUI).


By taking this approach you are just pushing the complication on to the customer. (they have to install an application to buy something from you...)

Sure life is easier for the coder when using a thick client... But thats not good business.


> **pmasiar said:**
> Interesting. Thanks for bringing it up.

Rails was such a brilliant idea: "convention instaed of configuration". Use introspection of dynamic languages to make code look simpler.

Now everyone is doing it, but Rails was first, and powered the Ruby revolution.

I'll try to sell Groovy instead of Java to my boss... :-/

The sell...

"Hey boss man / woman, there's this JSR 241 we need to look into.” 
“We need to use Enterprise 2.0”
“We need to use enterprise Java scripting”

---

### Post by slavik on 2008-10-08
> **tinny said:**
> By taking this approach you are just pushing the complication on to the customer. (they have to install an application to buy something from you...)

Sure life is easier for the coder when using a thick client... But thats not good business.


That is a good point ... but then again, it depends on what you are selling ... A well known company whose founder is the mayor of NYC has a service that they sell for thousands per month, and in order to access the service, you have to install their client program, not only that, but you actually have to call them to activate it ... I guess it all depends on what you are selling and to whom. :)

---

### Post by stefanadelbert on 2008-10-09
I installed Groovy and Grails on Ubuntu 8.04 following (excellent) instructions here: [http://beans.seartipy.com/category/grails/]("http://beans.seartipy.com/category/grails/").

I then followed the classic "Hello World" example spelled out here: [http://beans.seartipy.com/2008/06/15/creating-hello-world-web-application-using-the-grails-framework/]("http://beans.seartipy.com/2008/06/15/creating-hello-world-web-application-using-the-grails-framework/").

It all worked out nicely and the process was painless. I'm impressed so far and looking forward to getting stuck in a little deeper.

---

### Post by stefanadelbert on 2008-10-10
Update

I've started working through the excellent minibook here: [http://www.infoq.com/minibooks/grails]("http://www.infoq.com/minibooks/grails").

I am COMPLETELY blown away by Groovy and Grails. Groovy seems properly OO, but in a way that makes sense to the coder straight away. Grails does a massive amount of work for you and I had an application up and running in no time at all. I had a bit of trouble connecting to a local MySQL database, but that's because the tutorial was based on an earlier version of Grails (see my post "Problem with Grails connecting to local MySQL database").

Anyone had experience with adding a Groovy/Grails project to source control? Which files in the project directory actually need to go into source control?

---

### Post by tinny on 2008-10-11
> **stefanadelbert said:**
> Update

I've started working through the excellent minibook here: [http://www.infoq.com/minibooks/grails]("http://www.infoq.com/minibooks/grails").

I am COMPLETELY blown away by Groovy and Grails. Groovy seems properly OO, but in a way that makes sense to the coder straight away. Grails does a massive amount of work for you and I had an application up and running in no time at all. I had a bit of trouble connecting to a local MySQL database, but that's because the tutorial was based on an earlier version of Grails (see my post "Problem with Grails connecting to local MySQL database").

Anyone had experience with adding a Groovy/Grails project to source control? Which files in the project directory actually need to go into source control?

Good to hear you are enjoying it.

I use the Eclipse plugin to do my Groovy + Grails development. Eclipse has subversion intergeneration via the subclipse plugin.

[http://subclipse.tigris.org/](http://subclipse.tigris.org/)

---

### Post by stefanadelbert on 2008-10-13
I spent a few hours fiddling with various aspects of the Groovy/Grails project and it all makes good sense and works really well. It helps to have a good tutorial though!

I installed Eclipse and the Eclipse plugin. I struggled to get it working initially, but that's because Eclipse wasn't picking up the GRAILS_HOME env variable, even though I am exporting it in ~/.profile. I thought ~/.profile is sourced at login and available to an apps running the Gnome session. Just ended up manually sourcing ~/.profile in a terminal and starting eclipse from the same terminal.

I downloaded IDEA, but didn't get around to installing it. Looking forward to seeing it in action. Didn't realise that it wasn't free! Pity about that.

Anyway, thanks for the advice. I've enjoyed what I've seen so far and it's definitely the right choice for what I'm trying to achieve.

Stef

---

### Post by tinny on 2008-10-13
> **stefanadelbert said:**
> I spent a few hours fiddling with various aspects of the Groovy/Grails project and it all makes good sense and works really well. It helps to have a good tutorial though!

I installed Eclipse and the Eclipse plugin. I struggled to get it working initially, but that's because Eclipse wasn't picking up the GRAILS_HOME env variable, even though I am exporting it in ~/.profile. I thought ~/.profile is sourced at login and available to an apps running the Gnome session. Just ended up manually sourcing ~/.profile in a terminal and starting eclipse from the same terminal.

I downloaded IDEA, but didn't get around to installing it. Looking forward to seeing it in action. Didn't realise that it wasn't free! Pity about that.

Anyway, thanks for the advice. I've enjoyed what I've seen so far and it's definitely the right choice for what I'm trying to achieve.

Stef

Have you had a look at NetBeans 6.5? Its in beta right now but it seems all good. It has Groovy + Grails support. I havent tried writing a Grails app with it but the Groovy support is very good.

[http://www.netbeans.org/community/releases/65/](http://www.netbeans.org/community/releases/65/)
[http://download.netbeans.org/netbeans/6.5/beta/](http://download.netbeans.org/netbeans/6.5/beta/)

---

### Post by mssever on 2008-10-13
> **stefanadelbert said:**
> I thought ~/.profile is sourced at login
That's only true for console-based logins (~/.bashrc is sourced by all interactive shells (maybe non-interactive ones, too? I don't remembeR). I think there's some X dotfile where you can set the environment for X sessions. I don't remember what that is. I personally put that kind of stuff in /etc/profile, which DOES apply to all logins, including Gnome. Of course, anything in /etc/profile applies to all users, but that's OK for my needs. YMMV.

---

### Post by stefanadelbert on 2008-11-25
Just thought I'd put something in here by way of an (outdated) update.

I took a look at IDEA and wasn't all that impressed really. Installation seemed a little tricky (it was going to take me more than 15mins to get right, yes I'm a lazy ****). I've worked with Eclipse before and would probably invest the time in getting that environment working rather, especially since it's free.

But I lost a lot of momentum on the Groovy + Grails side of things, mainly due to lack of documentation and resources for Groovy. I was very keen to start writing my own Groovy classes, but couldn't find a language reference anywhere and had no idea how to implement even simple inheritance, etc. I hope I'm missing something and someone can point me to what I'm looking for.

The platform has plenty of promise, but falls short at the moment IMHO. Anyone got any comments or anything to add to that? I am more than happy to be proven wrong here!

---

### Post by tinny on 2008-11-26
> **stefanadelbert said:**
> 
I took a look at IDEA and wasn't all that impressed really. Installation seemed a little tricky (it was going to take me more than 15mins to get right, yes I'm a lazy ****). I've worked with Eclipse before and would probably invest the time in getting that environment working rather, especially since it's free.


So what IDE are you using now? Eclipse? I really like the Netbeans 6.5 Groovy + Grails support.

> **stefanadelbert said:**
> 
But I lost a lot of momentum on the Groovy + Grails side of things, mainly due to lack of documentation and resources for Groovy. I was very keen to start writing my own Groovy classes, but couldn't find a language reference anywhere and had no idea how to implement even simple inheritance, etc. I hope I'm missing something and someone can point me to what I'm looking for.


Yeah, the Groovy on-line documentation is very poor and the Grails documentation is not that much better. As I mentioned in an earlier post I prefer books and can recommend the following...

Groovy:
[http://www.amazon.com/Groovy-Action-Dierk-Koenig/dp/1932394842/ref=pd_sim_b_2](http://www.amazon.com/Groovy-Action-Dierk-Koenig/dp/1932394842/ref=pd_sim_b_2)

Grails:
[http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1227677411&sr=8-2](http://www.amazon.com/Beginning-Groovy-Grails-Novice-Professional/dp/1430210451/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1227677411&sr=8-2)

[http://www.amazon.com/Definitive-Guide-Grails-Second/dp/1590599950/ref=pd_sim_b_3](http://www.amazon.com/Definitive-Guide-Grails-Second/dp/1590599950/ref=pd_sim_b_3)

If in doubt you should just code your groovy classes as you would code your Java classes (80% of Java code is valid groovy code). This is what I do when im "stuck", then after awhile I find my code starts to naturally become more Groovy like (does that make sense???). I guess this is just part of learning something new.

> **stefanadelbert said:**
> 
The platform has plenty of promise, but falls short at the moment IMHO. Anyone got any comments or anything to add to that? I am more than happy to be proven wrong here!

Id be happy to try and help if you could give specific examples.

---

### Post by stefanadelbert on 2008-11-26
Thanks for the reply Tinny. I'm sure you're the only one still following this thread, although I was amazed to see that it got over 600 reads.

I have to admit that I'm a little loathe to go out and buy books when really the documentation *should* be on the web somewhere. But I was so impressed with the framework while working through the racetrack tutorial that I really might consider investing in a good book. I'm not currently doing any web development, so there is no burning need for a solution for the time being.

Unfortunately I'm not a java programmer so my knowledge of the java language is about as developed as my knowledge of Groovy. Java is well documented though, I suppose, so maybe the idea is to find out how to do it in java and code Groovy that way and work from there.

I'm not currently using an IDE on linux as I'm not developing on/for linux ATM (work has me confined to VB6 on MS! Yuk!). I've had a look at a few (Anjuta, MonoDevelop, KDevelop, Eclipse) and prefer Eclipse and reckon I would stick with it.

For the moment, it would be a good starting point to be able to put together a class hierarchy that implements some public and private inhertiance (multiple inheritance supported?) and some of the other basic OO concepts (method overriding, abstract base class, interfaces) and then which containers are available (STL equivalents).

Many thanks in advance.
Stef

---

### Post by pmasiar on 2008-11-26
> **stefanadelbert said:**
> I'm a little loathe to go out and buy books when really the documentation *should* be on the web somewhere.

There is no law of physics to guarantee that. ;-)

Some languages (promoted by companies) do have that kind of support, a few are really popular and have the community, but to get there, someone has to set aside time from making money and write the docs - and it is fair to expect to be rewarded for that. I am always amazed how much excellent docs are there for Python for free, with no big company to pay the bills.

Presence of free docs is not given - it is sign of big and mature user community. Lack of it is sign that the language is not there yet.

---

### Post by tinny on 2008-11-26
> **pmasiar said:**
> 
Presence of free docs is not given - it is sign of big and mature user community. Lack of it is sign that the language is not there yet.

Yep, there is a lot of truth to what you are saying. Personally I really do feel that Groovy is going to fill a big gap in the Java market, but yes it is not a mature language yet.

I do get the feeling that there has been a lot of investment into this technology and that right now perhaps some of that investment is being recouped through selling learning material. I personally dont have a problem with this as I feel it is a worth while technology and that the people involved deserve to make some money from it.

People could always try the Groovy forum [http://www.groovy-forum.org/](http://www.groovy-forum.org/) (but it too is very lite on material)

---

### Post by tinny on 2008-11-26
> **stefanadelbert said:**
> I spent a few hours fiddling with various aspects of the Groovy/Grails project and it all makes good sense and works really well. It helps to have a good tutorial though!

I installed Eclipse and the Eclipse plugin. I struggled to get it working initially, but that's because Eclipse wasn't picking up the GRAILS_HOME env variable, even though I am exporting it in ~/.profile. I thought ~/.profile is sourced at login and available to an apps running the Gnome session. Just ended up manually sourcing ~/.profile in a terminal and starting eclipse from the same terminal.

I downloaded IDEA, but didn't get around to installing it. Looking forward to seeing it in action. Didn't realise that it wasn't free! Pity about that.

Anyway, thanks for the advice. I've enjoyed what I've seen so far and it's definitely the right choice for what I'm trying to achieve.

Stef

Did you follow the Grails Eclipse IDE setup instructions? (E.g. Setting up eclipse environment variables)

Also, you should be using the Eclipse Groovy plug-in [http://groovy.codehaus.org/Eclipse+Plugin](http://groovy.codehaus.org/Eclipse+Plugin)

---

### Post by stefanadelbert on 2008-12-04
Right! I've actually got a project on the go now, rather than just some luke-warm interest in the technology in general. There is a website that needs redesigning from the top down (or bottom up). There is a requirement for CMS, newsletter generation, a few input forms, etc.

I've decided on the LAMP stack and am busy looking at CMS's at the moment. Silverstripe shows promise in theory, although I'm having a little trouble configuring Apache2 ATM (but may have a solution thanks to the Silverstripe forums).

Seems that Silverstripe has a PHP code generation and database abstraction layer framework and many themes that can be downloaded and used for free. There also seem to be many modules available for download that will make newsletter generation amongst other things relatively easy to do.

I think I'll be going this route for the time-being. Got to start somewhere.

Anyone used Silverstripe before? Anyone got any other (LAMP stack compatible) CMS recommendations?

Rock
Stef

---

