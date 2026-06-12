---
title: "Java web framework: Struts or Spring?"
date: 2008-07-01
forum: Programming Talk
---

### Post by pmasiar on 2008-07-01
For our new project, we need to collaborate with outside, and decision was made above may payscale to use Java and Struts1.

I can wrestle with Struts1 and often win, :-) but for new project I prefer not to use technology which is becoming obsolete. I also will need to use AJAX, and brief research shows that Struts2 and Spring seems to have better support than Struts1.

One of local gurus prefers Spring, other started with Struts1 and does not plan to switch - but advises to be first here and go with Struts2.

I am also not afraid of SQL, so ORM is not a big issue. But iBatis seems more flexible than Hibernate, even if I have to write SQL - because I can, and so have more control.

What are your experiences and advice about Java frameworks, if i cannot use my favorite Python/Turbogears?

Will be Spring clear winner over Struts 1/2 in near future, or will it ramain close call? If I go with Struts1, how hard is to upgrade to 2 later? I know that Struts 1 is not very flexible,is Struts2 so much better? Better than Spring? Spring can do testing easier that Struts1, is Struts2 improved?

What about **IDE support**? Eclipse with MyEclipse saved me with Struts1, does it support Spring well? Any nice GUI way to edit horrible XML config files? Or netbeans has better support for Spring?

What are pro and cons for couple of available **templating systems** and AJAX libraries? I used JSP and JSTL, and YUI for AJAX. But if I can avoid JS and generate it with GWT, it certainly would be nice. How often GWT fails, and how hard is to fix generates JS code?

If something is enough better, any links to arguments to persuade my boss to use better alternative? I googled around but there is lots of crap about java all over the place, so I decided to ask for advice.

There are so many technologies, and it is hard to compare them without hands-on experience - but where to get time to try them all? (I do not expect answer to this one :-) )

And how comparable are **learning curves** for those technologies? Which one is steeper/has more tricks and quirks? Which is more consistent and logical? What are best tutorials/books?

**What other questions I should consider** when deciding between those technologies? What  would be better forum to ask this question (and there it is obviously as FAQ).

---

### Post by napsy on 2008-07-01
My experiences with java web development tells me that java totally sux. Too complicated, you have to edit around 10 XML files to get started and another 10 to deploy. And some configuration isn't even documented or documented very badly. And all that just to throw away a couple of 100 MB of ram to show a dynamic page.

---

### Post by xlinuks on 2008-07-01
Since Spring came after Struts it was developed with the/some Struts shortcomings in mind,
here's from Wikipedia:
> The Spring Framework features its own MVC framework, which wasn't originally planned. The Spring developers decided to write their own web framework as a reaction to what they perceived as the poor design of the popular Jakarta Struts web framework[9], as well as deficiencies in other available frameworks. In particular, they felt there was insufficient separation between the presentation and request handling layers, and between the request handling layer and the model.
[http://en.wikipedia.org/wiki/Spring_Framework](http://en.wikipedia.org/wiki/Spring_Framework)
Some say Spring is easier to use, haven't tried it since I write Java for the Desktop.

---

### Post by xlinuks on 2008-07-01
> **napsy said:**
> My experiences with java web development tells me that java totally sux. Too complicated, you have to edit around 10 XML files to get started and another 10 to deploy. And some configuration isn't even documented or documented very badly. And all that just to throw away a couple of 100 MB of ram to show a dynamic page.

I mostly agree with you, but using NetBeans (with the web plugins) - helps a lot, I tried myself, almost everything is automated.

---

### Post by CptPicard on 2008-07-01
Word of warning, I haven't done anything with Struts2 and don't even know what it's like. I did hate Struts1 :)

However, my 0,02&#8364; tells me that Spring is actually the Saviour of Java web application development for what it's worth -- and it's not just for web apps, it's essentially an integration framework that takes best components and helps you glue them together into easier to handle wholes. A good example of how it tries to present a unified model is that it tends to wrap static exceptions into RuntimeExceptions that are in its own hierarchy.

Spring is essentially a J2EE container without J2EE, and there are tradeoffs to using it of course... there's more to learn with all that IoC and such, but it also tries to give you the whole deal with relatively little integration work. Struts2 on the other hand is probably just another view technology.

There are plugins for Spring and it's my experience that even just using Netbeans' document-specification-aware XML editor works ok. I have not quite got into annotations yet.

ORM support is good, and you can even do something like use multiple database access strategies in single transaction.

If I were making your decisions for you it would be Spring all the way, but too bad I'm not :)

EDIT: Oh, and forgot to mention... of course Spring does not force you to use the included Spring MVC web-app presentation/controller layer thing. You can replace it with pretty much anything.

---

### Post by tinny on 2008-07-01
Spring is good, still JSP though. :(

AOP is quite nice to have too.

I've just finished a project with Spring MVC and I have to say it wasn't half bad.

Has the decision already been made? (Beyond using Java?)

If not have a look at Apache [Wicket]("http://wicket.apache.org/"). Good bye JSP!!!

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> Spring is good, still JSP though. :(

Actually, you can plug all sorts of view technologies to be the front end and let Spring handle the "business middle layer". Velocity templates and XML/XSLT are actually even described in the docs.

> 
If not have a look at Apache [Wicket]("http://wicket.apache.org/"). Good bye JSP!!!

Wicket is nice -- I like the component-based approach which is far more lightweight than JSF -- but I once tried to integrate it with Spring to get transaction handling and that wasn't very successful. I guess you can get Spring beans from the IoC container to be used as Wicket models, but it's hard to get the request processing weaved properly into the component handlers... there really needs to be some integration code to get Spring and Wicket to play nice together, and that's a very viable competitor to anything...

---

### Post by tinny on 2008-07-01
> **CptPicard said:**
> Actually, you can plug all sorts of view technologies to be the front end and let Spring handle the "business middle layer". Velocity templates and XML/XSLT are actually even described in the docs.



Wicket is nice -- I like the component-based approach which is far more lightweight than JSF -- but I once tried to integrate it with Spring to get transaction handling and that wasn't very successful. I guess you can get Spring beans from the IoC container to be used as Wicket models, but it's hard to get the request processing weaved properly into the component handlers... there really needs to be some integration code to get Spring and Wicket to play nice together, and that's a very viable competitor to anything...

By JSP I probably mean Just Sucks People! :) (All those Java web templating frameworks suck)

BTW, you many have just saved me a lot of time (Wicket > Spring).

Do you have any experience using Wicket with EJB3? OP, EJB3 is quite nice.

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> 
BTW, you many have just saved me a lot of time (Wicket > Spring).


You're comparing apples and oranges... Spring does different things from Wicket.

---

### Post by tinny on 2008-07-01
> **CptPicard said:**
> You're comparing apples and oranges... Spring does different things from Wicket.

(Wicket and Spring together) should have been (Wicket -> Spring) opps

What I was trying to say was that you may have just saved me a lot of time because I was thinking about using Spring with Wicket but now that ive heard that interoperability between the two is tough I will investigate further.

---

### Post by CptPicard on 2008-07-01
> **tinny said:**
> 
What I was trying to say was that you may have just saved me a lot of time because I was thinking about using Spring with Wicket but now that ive heard that interoperability between the two is tough I will investigate further.

If you find out something interesting, I would be interested in hearing.

The biggest problem is this: The request cycle is fairly page-centric. When you are doing something like long transactions which was my issue in particular -- meaning that you can use Hibernate's versioning to tell when during user wait time the transaction has failed because of concurrent update, things still remain relatively simple if your request just comes in, you process it, do whatever you need to in your transaction, prepare some sort of value hash for the view and then after view render, close (sub)transaction.

Now, transaction failures and recovery from them etc become much harder in a component-centric framework where the ongoing request cycle is being sort of abstracted away as much as possible. It's a sort of paradigm mismatch: the components are doing their best to seem "independent" of everything else in the app, but of course they are not... so you get issues.

---

### Post by tinny on 2008-07-01
> **CptPicard said:**
> If you find out something interesting, I would be interested in hearing.

The biggest problem is this: The request cycle is fairly page-centric. When you are doing something like long transactions which was my issue in particular -- meaning that you can use Hibernate's versioning to tell when during user wait time the transaction has failed because of concurrent update, things still remain relatively simple if your request just comes in, you process it, do whatever you need to in your transaction, prepare some sort of value hash for the view and then after view render, close (sub)transaction.

Now, transaction failures and recovery from them etc become much harder in a component-centric framework where the ongoing request cycle is being sort of abstracted away as much as possible. It's a sort of paradigm mismatch: the components are doing their best to seem "independent" of everything else in the app, but of course they are not... so you get issues.

Cool, thanks for that. Ill let you know if I find the silver bullet. :)

---

### Post by pmasiar on 2008-07-01
Thanks for responses. I know very well that Java sucks (as I said I did wrestled out couple pages out of Struts), and did looked in wikipedia :-) I am hoping for more experience-based comments. 

So what about IDE support and AJAX? Anyone has experience with DWR?

Does Java/Springs has some simple serverless database like SQLite, so I can kick the tires, like I can with Turbogears? Every time I try to do anything in Java, response is "real big enterprise will not use this toy solution, read this 1000 page API instead" and it's hard to get any progress, or even have idea if I am moving at all and in which direction.

I wonder where are all those strong Java defenders who always promote Java when I need them :-) I would expect they would jump on possibility to prove me wrong about Java, show me how easy it is if you use right tools.

---

### Post by CptPicard on 2008-07-01
> **pmasiar said:**
> 
So what about IDE support and AJAX? Anyone has experience with DWR?

[http://springide.org/project](http://springide.org/project)

No idea about AJAX :)

> 
Does Java/Springs has some simple serverless database like SQLite, so I can kick the tires, like I can with Turbogears?

Spring itself is not only db-agnostic but also database-abstraction-agnostic. You can do something like slap SQLite under Hibernate, or even use Spring's JDBC abstraction on top of the same.

---

### Post by pmasiar on 2008-07-01
> **CptPicard said:**
> Spring itself is not only db-agnostic but also database-abstraction-agnostic. You can do something like slap SQLite under Hibernate, or even use Spring's JDBC abstraction on top of the same.

I googled [http://www.google.com/search?q=hibernate+sqlite](http://www.google.com/search?q=hibernate+sqlite) and found SQLite only for NHibernate, and many other ppl asking SQLite & Hibernate in vain.

This is exactly why Java as "go it alone platform" sucks. There is excellent solution in C, but no, Java cannot link it, and all that work in C is wasted. It was too simple to use and not enterprisey enough I guess :-)

---

### Post by CptPicard on 2008-07-01
Doh, wouldn't have thought...

Oh well, you might want to look at a JDBC approach then, if ORM is not a requirement. I use it myself... Spring makes it quite nice actually, and I never liked Hibernate anyway, it isolates me too much from the database ;)

---

### Post by pmasiar on 2008-07-01
Spring with JDBC linking to SQLite - how to set it up? Can I use iBatis with SQLite - I kinda almost like iBatis.

---

### Post by CptPicard on 2008-07-01
[http://www.onjava.com/pub/a/onjava/excerpt/springadn_ch05/index.html](http://www.onjava.com/pub/a/onjava/excerpt/springadn_ch05/index.html) (and other results)

You'll need the SQLite JDBC driver anyway though regardless of which solution you choose.

[http://www.zentus.com/sqlitejdbc/](http://www.zentus.com/sqlitejdbc/)
[http://www.ch-werner.de/javasqlite/](http://www.ch-werner.de/javasqlite/)
[http://www.xerial.org/trac/Xerial/wiki/SQLiteJDBC](http://www.xerial.org/trac/Xerial/wiki/SQLiteJDBC)
[http://www.malcolmhardie.com/sqleditor/cocoa/manual/html/ch09s06.html](http://www.malcolmhardie.com/sqleditor/cocoa/manual/html/ch09s06.html)

On the other hand, I do not really see why running something like a development PgSQL db with pgAdmin is so hard.. :)

---

### Post by tinny on 2008-07-02
> **pmasiar said:**
> Thanks for responses. I know very well that Java sucks (as I said I did wrestled out couple pages out of Struts), and did looked in wikipedia :-) I am hoping for more experience-based comments. 

So what about IDE support and AJAX? Anyone has experience with DWR?

Does Java/Springs has some simple serverless database like SQLite, so I can kick the tires, like I can with Turbogears? Every time I try to do anything in Java, response is "real big enterprise will not use this toy solution, read this 1000 page API instead" and it's hard to get any progress, or even have idea if I am moving at all and in which direction.

I wonder where are all those strong Java defenders who always promote Java when I need them :-) I would expect they would jump on possibility to prove me wrong about Java, show me how easy it is if you use right tools.
(Not really keen for a fight today ;) ) If your nice pmasiar we Java guys will take you on a wonderful journey of discovery. (All while not trying to convert you)

Java web templating technologies suck.

A great lite data base is Hypersonic (and the data files can be viewed in any text editor, they are just SQL), it even has a Maven plugin. Also Jetty is a nice lite Servlet container for Dev testing (Has a Maven plugin).

I think Maven etc.. will really make your life easier, more than happy to help if your happy to listen?

Also, are you able to look at a framework like Wicket? I think this would be a more comfortable approach for you.

---

### Post by CptPicard on 2008-07-02
> **tinny said:**
> 
Java web templating technologies suck.

Not so fast... Velocity is actually very close to kid templates from TG -- pmasiar, you should perhaps look into it :)

> Also, are you able to look at a framework like Wicket? I think this would be a more comfortable approach for you.

If the business-layer requirements do not need Spring underneath, Wicket may be interesting, otherwise, it's actually quite different from TurboGears which is fairly page-oriented... (from what I've been able to tell with my limited experience with it)

---

### Post by Quikee on 2008-07-02
> **pmasiar said:**
> Does Java/Springs has some simple serverless database like SQLite, so I can kick the tires, like I can with Turbogears?

Yes... [HSQLDB]("http://hsqldb.org/"). It is a in-memory / file-based DB.

---

### Post by CptPicard on 2008-07-02
By the way, regarding IDEs, Netbeans 6.1 seems to have Spring MVC support built in... haven't tested yet but it seemed to flash by as a plugin in the installer. Netbeans > Eclipse in web app development anyways, so that's great.

This alone is a reason to use Spring over Struts... you're going to be struggling enough with getting plugins to work for Struts, and Netbeans' integration is generally excellent.

And hey, it's got Hibernate support too, downloadable from the plugins dialog!! w00t.

---

### Post by pmasiar on 2008-07-02
> **tinny said:**
> I think Maven etc.. will really make your life easier, more than happy to help if your happy to listen?

Also, are you able to look at a framework like Wicket? 

I am very happy to listen to any advice which will make my Java hacking easier and more productive. Thanks for suggestions. Java universe is so vast that finding the good stuff by myself is pure luck. I need tools which handhold and nudge me to use best practices without reading mountains of docs. I do not freedom to shoot myself to my own foot: I want someone smart doing correct decisions for me. Because i have no strong preferences, less freedom (toward correct solution) is better for me.

I am afraid that I need to go with mainstream framework like Struts or possibly Spring, no niche framework like Wicket will do. Tools are different, I may use what I want, but with core technology I have less options. 

I heard good words about Velocity templating before, I'll take another look.

---

### Post by Quikee on 2008-07-02
> **pmasiar said:**
> I am very happy to listen to any advice which will make my Java hacking easier and more productive. Thanks for suggestions. Java universe is so vast that finding the good stuff by myself is pure luck. I need tools which handhold and nudge me to use best practices without reading mountains of docs. I do not freedom to shoot myself to my own foot: I want someone smart doing correct decisions for me. Because i have no strong preferences, less freedom (toward correct solution) is better for me.

Well its not any different than for other platforms. If I were to choose a web framework in Python I would not know which to choose - I heard of turbo gears and pylons but I know there are others available. Either I would need someone else to choose or research and evaluate myself. 

I generally found it is very helpful to subscribe to a Java news site like [JavaLobby]("http://java.dzone.com/") and check it regular just to be up to date with the alternatives you have.

I would think about the following tools/frameworks to use in Java for a new project:

[LIST]
[*]Spring (with all its frameworks like Spring Webflow, MVC, Batch, Security,...)

[*]Eclipse for IDE (just because I don't have any experience with NetBeans - maybe NetBeans is a even better choice)

[*]openArchitectureWare for modelling (if you choose tu addopt use MDA (model driven approach) of development)

[*]Maven2 for build management (Its principle is "convention over configuration" which means that if you stick with its convention it will almost work out-of-the-box. Also it can download dependencies from online repositories - similar as a Linux package manager - just define the dependency and let him do the magic)

[*]m2eclipse (just a plugin to bind maven2 with eclipse)

[*]JUnit4 for testing framework

[*]JMock for construction of mock objects for test

[*]AspectJ (if Spring AOP is not enough)

[*]Groovy as a alternative language (to use it where it is appropriate) and check out Grails (Groovy on rails) )

[*]Hibernate for persistence or EclipseLink (as it might get a advantage in future as it has been chosen to be the reference implementation for JPA 2.0)

[*]Tomcat as web container

[*]maybe something else that I don't remember currently...
[/LIST]

---

### Post by pmasiar on 2008-07-02
I am open to try Spring with Maven myself at home, to persuade boss, and in ubuntu instead of my work PC with Windows. What installs and runs smoother on ubuntu: Eclipse or Netbeans? Tomcat is OK. Is Maven any different on Windows and Linux? Is there some ubuntu-compatible repository for relevant parts (Spring, Maven, netbeans etc) so I can use Synaptic? 

Any other plugins suggestions for Eclipse and/or Netbeans?

I hate fighting with installers.

Thanks for suggestions, I'll look at them. I'll love "conventions instead of configurations" - I prefer to choose carefully and then follow conventions, not fight with them. But my alternative language will by Jython and not Groovy :-)

There is even Spring for Python :-)

---

### Post by CptPicard on 2008-07-02
> **pmasiar said:**
> What installs and runs smoother on ubuntu: Eclipse or Netbeans? Tomcat is OK.

Netbeans FTW for web apps all the way. It seems to always work out of the box while Eclipse never does even after lots of configuration. The Spring and Hibernate integration looks very, very good, while analogous Eclipse plugins still probably throw mystical NullPointerExceptions at your face.

> Is Maven any different on Windows and Linux? Is there some ubuntu-compatible repository for relevant parts (Spring, Maven, netbeans etc) so I can use Synaptic? 

Just keep your own personal "java-lib" under "home"... you need to construe that once, and then you have everything you need. Maven is another of those "tools that help you manage Java" that actually just needs another tool for you to actually use *that* tool.

---

### Post by Quikee on 2008-07-02
> **pmasiar said:**
> I am open to try Spring with Maven myself at home, to persuade boss, and in ubuntu instead of my work PC with Windows. What installs and runs smoother on ubuntu: Eclipse or Netbeans? Tomcat is OK. Is Maven any different on Windows and Linux? Is there some ubuntu-compatible repository for relevant parts (Spring, Maven, netbeans etc) so I can use Synaptic? 

Any other plugins suggestions for Eclipse and/or Netbeans?

I hate fighting with installers.

I have not done yet a lot of exploration regardin Java and IDEs under Ubuntu because at work we also use Windows XP. The only thing I tried at home is Eclipse with Groovy, Jython, Scala and Ruby integration. 

The good thing about Eclipse (on Linux and Windows) is that it doesn't need any installation - just extract and it runs (if it finds the JDK on the usual place). This is very nice for doing start-up IDE environments - eclipse packaged with all needed plugins and tools to start developing as quickly as possible. If anything goes wrong just delete the environment and unpack the "clean" one - if you need to test some other plugin but don't want to ruin the current environment just unpack in a different directory and try it out. This can be very convenient for a "team" environment. Because of this feature of Eclipse some distributions have emerged with the purpose to provide some Eclipse + plugins for a specific purpose (for Web development, Mobile development,...) - [EasyEclipse]("http://www.easyeclipse.org/site/distributions/index.html"). I think that NetBeans can't do this and needs a "proper" installation, but I might be wrong.

As far as Maven goes it looks like it is made for a unix environment so I guess should work great with Ubuntu - but I haven't tried it out yet. If you will use Maven in a team environment you should also have a look at [Continuum]("http://continuum.apache.org/") - this is a tool for continuous integration. 

To try out other frameworks like Spring it is better to check out Maven and [m2eclipse]("http://m2eclipse.codehaus.org/") plugin first (I think the plugin is all you need because it has maven embedded), because it will automatically download from the web ([http://repo1.maven.org/maven2/](http://repo1.maven.org/maven2/) being the main repository, but other also exist) all dependencies (including "nested" dependencies), you define, to your local "repository" and will make them available to your project. 

I wouldn't use ubuntu-compatible repositories for this.

---

### Post by Quikee on 2008-07-02
> **CptPicard said:**
> Maven is another of those "tools that help you manage Java" that actually just needs another tool for you to actually use *that* tool.

Don't agree at all. Maven is like Ant or Autotools but even more powerful. With continuum it can automatically (scheduled) run tests, build documentation / site / javadoc, assemble (project with all dependencies into a jar), build translations, manage dependencies, ... You can also write your own plugins if needed. Something like this is a blessing for a team environment.

---

### Post by tinny on 2008-07-02
> **pmasiar said:**
> I am open to try Spring with Maven myself at home, to persuade boss, and in ubuntu instead of my work PC with Windows. What installs and runs smoother on ubuntu: Eclipse or Netbeans? Tomcat is OK. Is Maven any different on Windows and Linux? Is there some ubuntu-compatible repository for relevant parts (Spring, Maven, netbeans etc) so I can use Synaptic? 

Any other plugins suggestions for Eclipse and/or Netbeans?

I hate fighting with installers.

Thanks for suggestions, I'll look at them. I'll love "conventions instead of configurations" - I prefer to choose carefully and then follow conventions, not fight with them. But my alternative language will by Jython and not Groovy :-)

There is even Spring for Python :-)

Eclipse starts up quicker, both operate at about the same pace.

Netbeans has MUCH better support for Maven!

I guess you will be choosing Netbeans? Not sure about Netbeans from the repositories (I just downloaded it from netbeans.org, it was easy to install)

Once you have netbeans installed, setup the Maven plug-in. [http://mevenide.codehaus.org/m2-site/mevenide2-netbeans/installation.html]("http://mevenide.codehaus.org/m2-site/mevenide2-netbeans/installation.html") 

Dont worry about downloading anything else (Spring, Struts, Tomcat etc etc), Maven will do all this for you :).

Next you will need to setup an Archetype for your application.

Struts / Spring MVC, whatever. I suggest you try both (not at the same time :)). 

Once you have Netbeans setup with Maven, File > New Project > Maven > Maven Project > Archetypes from remote Maven Repositories

You will then be given lots of project setup options (Lots of Archetypes)

One of the great things about Maven is it will just setup your whole environment (all while not tieing you to the IDE), Dependencies, Dev run environment, XML config (you'll like that).

Try the above as a starting point and let us know how it goes.

If you have problems with these instructions PM me and I can maybe send you a pom.xml file. (The pom.xml file is central to a Maven project)

Also for what its worth, I personally I have a preference for using Spring MVC instead of Struts.

---

### Post by tinny on 2008-07-02
> 
To try out other frameworks like Spring it is better to check out Maven and m2eclipse plugin first (I think the plugin is all you need because it has maven embedded), because it will automatically download from the web ([http://repo1.maven.org/maven2/](http://repo1.maven.org/maven2/) being the main repository, but other also exist) all dependencies (including "nested" dependencies), you define, to your local "repository" and will make them available to your project.


Dont use the m2eclipse plugin, its really bad.

> 
Just keep your own personal "java-lib" under "home"... you need to construe that once, and then you have everything you need. Maven is another of those "tools that help you manage Java" that actually just needs another tool for you to actually use that tool.


Not so. I exclusivity use Maven from the command line. Its just easier to start using it from the IDE. Seriously, once you know how to use Maven it is a joy to work with.

As for continuous integration, only really useful when it is supported by an XP methodology (Test driven development etc...). OP I think you have more than enough to get up to speed on without further complicating things.

BTW: this looks perfect for your needs. [http://struts.apache.org/2.1.2/docs/struts-maven-archetypes.html]("http://struts.apache.org/2.1.2/docs/struts-maven-archetypes.html")

---

### Post by CptPicard on 2008-07-03
This is very nice too, playing with it atm:

[http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html](http://www.netbeans.org/kb/61/web/quickstart-webapps-spring.html)

---

### Post by Quikee on 2008-07-05
> **tinny said:**
> Dont use the m2eclipse plugin, its really bad.

Have you any experience with [Q4E]("http://code.google.com/p/q4e/") ?


> **tinny said:**
> As for continuous integration, only really useful when it is supported by an XP methodology (Test driven development etc...). OP I think you have more than enough to get up to speed on without further complicating things.

Well.. in the exact moment you have automated test any work in a team environment - continuous integration is a very nice thing to have and you don't have to follow any XP methodologies for other things at all. 

Also I think that any "serious" project nowadays should have automated test unless you are really masochistic and want to make life deliberately harder. 

Talking about test - I forgot to mention [selenium]("http://selenium.openqa.org/") for web page testing.

---

### Post by pmasiar on 2008-07-05
I know about continuous testing, TDD etc - but in a team where one of my colleague never heard of MVC, TDD is not gonna be easy... :-(

---

### Post by tinny on 2008-07-05
I am a big fanboy of continuous integration! :guitar:
Maybe we can chat about it here?
[http://ubuntuforums.org/showthread.php?t=850754]("http://ubuntuforums.org/showthread.php?t=850754")

I just think we are starting to fork off the topic now. 

> Java web framework: Struts or Spring?

---

### Post by StutteringJohnSmith on 2011-02-07
starting to program on ubuntu! can someone help me setup java, springs and struts

---

### Post by Some Penguin on 2011-02-07
Please don't arbitrarily re-open multi-year-old threads.

---

