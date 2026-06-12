---
title: "Where to start with java web programming?"
date: 2007-11-19
forum: Programming Talk
---

### Post by Hospadar on 2007-11-19
Hi, i'm wondering if anyone here could direct me to some tutorials or a forum more focused on the topic.  I'm in college and I'm wanting to get myself into a little web programming with java for a little project I want to do.

I want to write a program with a simple server app and a client and be able to send messages between the two.  

I'm comfortable with java but the only thing I've ever done web-wise is downloading web pages to the hard drive, I don't really know where to start in terms of communicating with other apps.

Also, are there any good java-gtk tutorials about?  It's not that important to me, but it'd be nice to maintain a clean look througout my gui

Thanks in advance,
Luke

---

### Post by LaRoza on 2007-11-19
You are going to make it hard on yourself if you insist on Java. Java is good for applets in the Web sense, but for server side programming, you should use PHP, Perl, or Python.

Can Java be used with GTK? I would use Java with its native GUI toolkits, Swing is a good bet.

My wiki, and its forum may be a good place to look for Programming information. I don't have anything on Java Server Pages, but I do have links for Swing.

-EDIT I can't tell if you are coding the server and client, in which case, my comments on JSP and server side programming don't apply.

---

### Post by CptPicard on 2007-11-19
Could you elaborate a little... you're talking of "web programming" which to me means "web applications" (apps you use through the browser), but the other bits in your post suggest you're just doing regular network programming, that is, over sockets.

LaRoza is right; if you're doing web apps, stay away from Java. It's incredible how difficult web apps have been made in Javaland... I have been fooling around with them for, uh, 7 years and I still think it sucks. All the required infrastructure is just so horribly cumbersome.

Now, Enterprise Java *is* very powerful, but situations where you actually need all the Enterprise Javabeans stuff are rare. You need to be writing huge corporate information systems to actually need J2EE.

For everything else, the non-EE Java frameworks are a dime a dozen and a pain to integrate if you want to do things "right". God knows I honestly tried Spring+Hibernate+JSF/Wicket... then I gave up after months and about 3000 pages of books :)

Now I'm hacking Turbogears with Python. Looks much better and FAR less Byzantine. :)

---

### Post by pmasiar on 2007-11-19
Enterprise Java is good if you have enterprise website with 10K pages and complicated business logic. Unfortunately it does not scale down to simple website with 3 pages, like most Java.

Struts is the "standard" and I struggled with it valiantly, even wrestled couple page website out of it, but it was so much frustration ... Luckily for me, I was allowed to do further development in Python. Friends tell me Spring framework is s little simpler than Struts, if such things are possible with Java. Neither can compare with simplicity of Python with Turbogears or Django.

Java was not designed to handle text parsing and processing like websites IMHO. It is used that way - it is Turing complete, it does not mean anything.

Check Turbogears, read about how to make a wiki in 20 minutes. Even if you don't know Python, it will make sense for you. Then, try to find "hello world" app in Struts. There are many of them and all are bad...

[http://www.allapplabs.com/struts/struts_example.htm](http://www.allapplabs.com/struts/struts_example.htm)
[http://javaboutique.internet.com/tutorials/Struts/](http://javaboutique.internet.com/tutorials/Struts/)
[http://www.informit.com/articles/article.aspx?p=31197&rl=1](http://www.informit.com/articles/article.aspx?p=31197&rl=1)
[http://benmira.free.fr/en/j2ee/struts1.htm](http://benmira.free.fr/en/j2ee/struts1.htm)
[http://www.laliluna.de/first-steps-using-struts-tutorial.html](http://www.laliluna.de/first-steps-using-struts-tutorial.html)
[http://www.ociweb.com/jnb/jnbMar2003.html](http://www.ociweb.com/jnb/jnbMar2003.html)
[http://www.tek271.com/articles/struts/strutsHowTo-0-12.html](http://www.tek271.com/articles/struts/strutsHowTo-0-12.html) and many more...

Despite trying hard, i was not able to figure it without MyEclipse (paid non-free) plugin, which wizardry hides all complexities and makes me trained monkey - but at least it works afterwards :-/
[http://www.informit.com/guides/content.aspx?g=java&seqNum=291&rl=1](http://www.informit.com/guides/content.aspx?g=java&seqNum=291&rl=1)
[http://www.informit.com/guides/content.aspx?g=java&seqNum=281&rl=1](http://www.informit.com/guides/content.aspx?g=java&seqNum=281&rl=1)

---

### Post by CptPicard on 2007-11-19
To be honest, Struts hasn't been the standard for ages, it's a bad example. 

Spring on the other hand is much more than Struts and it makes stuff a bit better, but not much, and it adds its own complexity as you'll be designing your app around the IOC container. It's essentially a way to do "Enterprise Javabeans without Enterprise Javabeans". It also means more XML, but it does make the business logic layer better decoupled and in particular gives you non-J2EE transactions which you can integrate to your database layer.

The tough bits always seems to be in the integration... in a modern Java web app you want Spring for the business logic layer and kind of general glue framework, some view technology to present your results  -- integrating this can be tough especially if you take one of the new fancy componentized frameworks that will fight Spring over control of your app all the way -- and something for your database layer; Hibernate as the ORM is all the rage, and adds even more XML and an 800 page tome you just need to learn and understand *well* so that you don't inadvertently mess up your database access especially in cases such as long transactions...

There are just so many different frameworks that it is really difficult to stay current on all of the interesting ones, let alone understand them deeply enough so that you are actually able to make them play nicely together in the same application. "How do I do something simple using X and Y together" is a really typical question asked when it comes to Java web app development.

The whole deployment architecture is a bit weird too. Java likes to think of web apps as nice little packages that are just dropped into the server and there they run. Well, it's a nice idea, but in practice you certainly want to edit your running web application's static pages by hand quite often. Deploying an exploded, editable web app on Tomcat behind Apache can be an interesting exercise.

---

### Post by Hospadar on 2007-11-19
Thanks for all the response!

To clarify, yes I am looking to do a regular application that starts and runs independantly of a web browser, and just communicates to a specified machine via an IP and a port, which is why I thought I might go with java, as I already know it and with c++ I can only imagine would be much more difficult.

I suppose I could be even more specific as to what I'm writing.  It's going to be a platform for rolling dice for roleplaying games as played over the internet (through something else like a chat, or videoconference).  The app I'm writing just needs to send simple requests to the server (roll some dice) and the server then sends out the results to all registered users.  A little nerdy yes, but we're going to have some friends abroad soon and I thought it might be a good primer to internet programming and get me deeper into GUI stuff.

Thanks again for all the help.

---

### Post by scotlynhatt on 2007-11-21
I would say that you have the background to work in Java but since you posted in the Ubuntu forums I'll assume you are on that OS. You could very easily install the libraries and compiler for C++ and be off creating some apps in a language you are familiar with. If you are just creating a "web service" as you say and do not require GUI elements, then C++ should do just fine. Hell, you could drop down to ANSI-C just as easy.

    From the simple Java perspective, the available APIs for network interaction are quite robust and you could easily find some examples on opening a socket and responding to requests. From this angle you could build a simple stand-alone Java app run from the command line. This requires that you set up some scripting to handle startup and shutdown automatically. Otherwise you'll have to run it from the terminal and that may not always be desirable.

    From the Java "Web Service" side I think a simple servlet application would be a good fit for what you describe. This, unfortunately requires set up of an application server like Tomcat(J2SE) or JBoss(J2EE) which it didn't sound like you had experience with. The big advantage here is you could have services and add GUI elements later if you so desire. This also puts in you in a good position to move into the Struts MVC paradigm mentioned by other posters. 
    This of course would be the long way to the end you are looking for but your experience would not go to waste as working with Java and web services is a fairly marketable skill. I also think your object oriented experience would help you grasp all of this since it is very organized in contrast to the web scripting approaches, php, perl, et al. 

  There is no easy answer here really. If you want to get into Java you need to start with the usual Hello World and work from there.

Have fun.:)

---

### Post by mesocal on 2007-12-01
there seems to be a lot of anti java here.  i think jsf/jsp are difficult to learn and are very time consuming especially if you do them by hand. if you have a fair knowledge of java, then checkout apche's new project Wicket.  its a light weight framework that eliminates all markup text.  ive been playing with it for a little while, and im really pleased with it. theres a lot of built ajax classes and dojo as well.  well, thats just my two cents.

---

### Post by tenmillionmilesaway on 2007-12-02
Network communication in Java is quite simple, but a direct connection between sockets means that you have to figure out you're own protocol, which for anything other than a trivial app can get quite complicated.  As an alternative to this you could look at XMLRPC and/or Web Services (calling methods remotely via XML) which, when set up, should be simpler.

Another alternative would be to use groovy (a scripting type language that runs on the JVM and is byte-code compatible with java).  These two pages should show you how easy it is to to do XMLRPC with groovy: [http://groovy.codehaus.org/XMLRPC](http://groovy.codehaus.org/XMLRPC) and [http://groovy.codehaus.org/GroovyWS](http://groovy.codehaus.org/GroovyWS)

As for actual web apps (ie web pages) being difficult in Java, we us wicket at work and its really quite simple, the problem with Java is that there are too many choices and the most popular aren't always the best.

---

