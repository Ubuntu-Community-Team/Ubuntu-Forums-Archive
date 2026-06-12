---
title: "Applicable Server-side Technology?"
date: 2011-01-05
forum: Programming Talk
---

### Post by 0000_soldier on 2011-01-05
Hello!

I have a problem: I would like to make a website for me  and friends to use, the site would allow us to manage bookings with  clients and pull up reports eg find progress on client such as weight  loss over a period of time, diet plan, setting workout programs etc,  provide notification of requested bookings and management of bookings  with clients, so basic customer relationship management for personal  trainers.

I wanted to know your suggestions on which server-side  technology to use? I was considering using java, however as I have never  attempted anything other than simple programs with java i am not to  sure where to start, for example setting login sessions, so they can  connect using a java program on the desktop as well as from the website  browser. I wanted to use java as a project to help me learn java but i  am also not sure where to begin, i looked into tomcat  etc.

any advice appreciated thanks!

---

### Post by Joe of loath on 2011-01-05
From my, albeit limited knowledge, it sounds like you'll want a MySQL backend, and a PHP web frontend as well as some kind of desktop client. It would be easiest to build a client as OS dependant, but that's probably not possible.

---

### Post by robots.jpg on 2011-01-05
Sounds like a great candidate for Django if you have some experience with Python.
   
   The benefit there is that you can keep it entirely web-based (no  clients), and the framework provides a huge number of tools for you right  out of the box, as soon as you've set up your data structure and  synchronized it with the database provider.  For example, user account management, and  administration pages for entering and editing data, that automatically  adapt to field data types and the relationships between your tables.  
   
   Of course there's a bit of a learning curve like any framework out  there.  It has its own template language that you'll have to learn if  the generic data views don't cut it for you, and remembering which files  do what and where they're stored can be a huge headache at first.  The biggest obstacle is generally figuring out how to do what you want to do.


The Django applications I've created so far are served by Apache using mod_wsgi, and MySQL providing the data.

---

### Post by PaulM1985 on 2011-01-05
Java would be good for this. Have a look at JSP (Java Server Pages).  They are like a cross between Java and HTML.  Also have a look into Java Servlets.  You would then want to start looking at JavaBeans if you where going to be storing information in a database.

Paul

---

### Post by PaulM1985 on 2011-01-05
I have been googling and found these tutorials on the java/oracle website.

[http://download.oracle.com/javaee/5/tutorial/doc/](http://download.oracle.com/javaee/5/tutorial/doc/).

It might look daunting, but I would recommend probably just scanning the Overview, it gives and example of all of the Java Enterprise Edition capabilities, but then look to focus on Enterprise JavaBeans, Java Servlets, JSP and I think the Persistence API would be relevant if you are looking to store information in a database.

So as a recap, probably look at Parts II, III and V after scanning the overview.

If you have any problems just ask.

Paul

---

### Post by juancarlospaco on 2011-01-05
[http://bbcalc.sf.net/](http://bbcalc.sf.net/)  may help you, or maybe not, check it...

---

### Post by soltanis on 2011-01-06
In general, what you have described is a web-based application. There are many relevant server-side technologies available: some have already been suggested, such as [php]("http://php.net"), python frameworks like [Django]("http://djangoproject.com"), as well as others based on [Perl]("http://perl.org") or [Ruby]("http://rubyonrails.org"). One thing that you will probably do is interface with a database, and for this the tool of choice is usually [MySQL]("http://mysql.com"), although there are some other database solutions that have recently emerged such as CouchDB (but these might be of limited use).

Given the multitude of options that you have available, you should pick those tools that you are most comfortable with and that will accomplish the job most efficiently.

---

### Post by 0000_soldier on 2011-01-06
Hey,

Thank you for insightful replies, i think Java and Oracle back-end seem to be the way to go. I downloaded plenty of ebooks and resources seem endless, this will help me a lot.

---

### Post by juancarlospaco on 2011-01-06
> **0000_soldier said:**
> 
java and oracle

**&#3237;_&#3237;**

---

### Post by r-senior on 2011-01-06
> **0000_soldier said:**
> Hey,

Thank you for insightful replies, i think Java and Oracle back-end seem to be the way to go. I downloaded plenty of ebooks and resources seem endless, this will help me a lot.
Do have a look at Spring. Looks huge, and it is, but you can use it tactically and it saves a lot of time. The JDBC templates, for example, can reduce JDBC coding (and mistakes) drastically.

Basic use of the Spring dependency injection framework and programming to interfaces can make your choice of Oracle almost arbitrary. If you decide to switch to another database later on, it becomes very simple.

My preferred way of coding Java back-ends is Spring template DAOs (with whatever database/mapping technology is required), a service/facade layer in front with Spring transaction support and JUnit tests on the service layer methods. Sounds like gobbledegook but actually quite simple in practice.

Done well, it's reusable between web apps, web services and desktop/mobile apps. A bit of organisation goes a long way.

---

### Post by 0000_soldier on 2011-01-07
> **r-senior said:**
> Do have a look at Spring. 

Done well, it's reusable between web apps, web services and desktop/mobile apps. A bit of organisation goes a long way.

Can you provide me with a link? maybey i was closed minded a bit, but can you expand a bit more? 
thank you

---

### Post by r-senior on 2011-01-07
Here's the main site: 

[http://www.springsource.com/developer/spring](http://www.springsource.com/developer/spring)

Here's the current reference documentation for Spring 3.0:

[http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/](http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/)

The dependency injection/inversion of control container is basically a configurable factory:

[http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/beans.html](http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/beans.html)

The JDBC stuff should be of interest:

[http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/jdbc.html](http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/jdbc.html)

If it doesn't make sense, or you don't see the point, let me know and I'll try and distill it into a simple example.

---

### Post by 0000_soldier on 2011-01-08
Thank you very much!

---

### Post by drdos2006 on 2011-01-08
This might be of interest to you as well.

[http://dabodev.com/](http://dabodev.com/)

regards

---

### Post by Some Penguin on 2011-01-08
Oracle is likely *very* much overkill for what you're doing, and it's expensive.  PostgreSQL would likely serve you better in terms of cost-benefit.

---

