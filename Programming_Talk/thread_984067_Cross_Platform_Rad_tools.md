---
title: "Cross Platform Rad tools"
date: 2008-11-16
forum: Programming Talk
---

### Post by Jonas thomas on 2008-11-16
Hi All,
I'm hoping for some advise here.
I've been working with Linux for about a year or so and really really like it.
At work, I guess I would describe myself as a self supported super user.  In other words I do a lot of programming but I'm not part of the IT staff.

I do alot of VB6 programming interacting with Oracle and Access databases.   I am addicted to Ms data environment.

I need to start programming in something other than VB6 but I want into invest in learning cross-form tools.  In other words I wish to avoid .Net if I can help it.
My personal interests have been in learning C++ but I don't think I would really consider that a weapon of choice for RAD.

I've looked at Qt, which would work for pure opensource work, but I don't want to deal with the Liscense issues at work.

Is there a crossplatform IDE that works really nice connecting up to database's through something like ODBC???
Thanks,
JT

---

### Post by Majorix on 2008-11-16
I would recommend Netbeans. Cross-platform and powerful. Eclipse is also a possibility.

---

### Post by tinny on 2008-11-16
> **Jonas thomas said:**
> Hi All,
I'm hoping for some advise here.
I've been working with Linux for about a year or so and really really like it.
At work, I guess I would describe myself as a self supported super user.  In other words I do a lot of programming but I'm not part of the IT staff.

I do alot of VB6 programming interacting with Oracle and Access databases.   I am addicted to Ms data environment.

I need to start programming in something other than VB6 but I want into invest in learning cross-form tools.  In other words I wish to avoid .Net if I can help it.
My personal interests have been in learning C++ but I don't think I would really consider that a weapon of choice for RAD.

I've looked at Qt, which would work for pure opensource work, but I don't want to deal with the Liscense issues at work.

Is there a crossplatform IDE that works really nice connecting up to database's through something like ODBC???
Thanks,
JT

What type of applications do you want to develop?

Applications for linux?
Web applications?
Cross platform desktop applications?
...?

There are lots of options out there, each with pros and cons.

---

### Post by Vadi on 2008-11-16
RealBasic, GTK+Glade, Qt+Qt Designer are the ones I can think of

---

### Post by skirkpatrick on 2008-11-16
We've been using wxWidgets with the Databaselayer add-on to work with ODBC.  You could aways use Python with wxPython for GUI.

---

### Post by Jonas thomas on 2008-11-16
> **Majorix said:**
> I would recommend Netbeans. Cross-platform and powerful. Eclipse is also a possibility.

Thank you for the suggestions.  
I need to digest this a little bit. 
[http://en.wikipedia.org/wiki/NetBeans]("http://en.wikipedia.org/wiki/NetBeans")

[http://wiki.netbeans.org/]("http://wiki.netbeans.org/")
[URL="http://en.wikipedia.org/wiki/Eclipse_(software)"]
http://en.wikipedia.org/wiki/Eclipse_(software)[/URL]

---

### Post by tinny on 2008-11-16
> **Jonas thomas said:**
> Thank you for the suggestions.  
I need to digest this a little bit. 
[http://en.wikipedia.org/wiki/NetBeans]("http://en.wikipedia.org/wiki/NetBeans")

[http://wiki.netbeans.org/]("http://wiki.netbeans.org/")
[URL="http://en.wikipedia.org/wiki/Eclipse_(software)"]
http://en.wikipedia.org/wiki/Eclipse_(software)[/URL]

Eclipse and Netbeans can be used for all types of development: C/C++, Python, Groovy, J2SE, J2EE, PHP, C# etc...

By choosing either of these IDE's (thats all they are IDE's / Editors) you wont get any closer to choosing an effective tool set thats best for your problem. (E.g. Which runtime? Python, JVM, Mono etc...)

We really need to know what type of development you are trying to do. Or at least what you are trying to archive. Otherwise you will be left with a sub par answer...

---

### Post by Jonas thomas on 2008-11-16
> **tinny said:**
> What type of applications do you want to develop?

Applications for linux?
Web applications?
Cross platform desktop applications?
...?

There are lots of options out there, each with pros and cons.

Well, I think my main focus at this moment is that I want to develop cross platform desktop applications.  As I said, I do quite a bit of application programming at work, industrial engineering sort of stuff and use Linux practically exclusively at home.  I'm quite willing to learn the basics of a new language on my home(own) time, but I need to be stay productive at work(not a lot of time for a learning curve).  Typically, the kind of stuff that I at work is use vb6 data environment using sql to data-mine production data into my control of choice, the hierarchical flexgrid.  I very much love the compare statement, which is an incredible tool to be able to problematically sort lists in ways which would be difficult (if not impossible) to accomplish within standard SQL calls.

Anyway, as I said, VB6 is becoming a bit of a dinosaur, but I to start thinking about starting moving to something else. It's just that I have a limited amount of time to invest and I want to maximize my return on my personal investment in being able to apply this to a Linux as well as Ms environment.

---

### Post by tinny on 2008-11-16
> **Jonas thomas said:**
> Well, I think my main focus at this moment is that I want to develop cross platform desktop applications.  As I said, I do quite a bit of application programming at work, industrial engineering sort of stuff and use Linux practically exclusively at home.  I'm quite willing to learn the basics of a new language on my home(own) time, but I need to be stay productive at work(not a lot of time for a learning curve).  Typically, the kind of stuff that I at work is use vb6 data environment using sql to data-mine production data into my control of choice, the hierarchical flexgrid.  I very much love the compare statement, which is an incredible tool to be able to problematically sort lists in ways which would be difficult (if not impossible) to accomplish within standard SQL calls.

Anyway, as I said, VB6 is becoming a bit of a dinosaur, but I to start thinking about starting moving to something else. It's just that I have a limited amount of time to invest and I want to maximize my return on my personal investment in being able to apply this to a Linux as well as Ms environment.

Oh industrial automation... (I used to work in this area...)

So you would probably be interested in extracting data from SCADA systems and perhaps interfacing with Modbus and OPC?

Based on that I would be looking at either Java or .Net (.Net also has a linux implementation called Mono).

Are you interested in just extracting process monitoring type information? Or do you want to perform control type operations?

---

### Post by Jonas thomas on 2008-11-16
> **Vadi said:**
> RealBasic, GTK+Glade, Qt+Qt Designer are the ones I can think of

I'm not familiar with RealBasic, I need to research this a littlebit.
[http://en.wikipedia.org/wiki/REALbasic]("http://en.wikipedia.org/wiki/REALbasic")
I guess that its not open source... There home page got me sort of irritated since, I had to start jumping through a bunch of pages searching for there cost structure...

I'm just starting to play with GTK+Glade, and gtkmm at home.  
Would I be better of starting out with Wxwidgets?

I also, playaround a little bit with the Qtdemo.  That impressed me.  There licensing is a little hinky and expensive if you don't want to publish your code.  So I think they're out..

---

### Post by Jonas thomas on 2008-11-16
> **tinny said:**
> Oh industrial automation... (I used to work in this area...)

So you would probably be interested in extracting data from SCADA systems and perhaps interfacing with Modbus and OPC?

Based on that I would be looking at either Java or .Net (.Net also has a linux implementation called Mono).

Are you interested in just extracting process monitoring type information? Or do you want to perform control type operations?

No not at the moment, I'm not really doing industrial automations stuff.. Never say never though.   I  do a lot of interphasing between a ERP database, DMS's and the like..

---

### Post by tinny on 2008-11-16
> **Jonas thomas said:**
> No not at the moment, I'm not really doing industrial automations stuff.. Never say never though.   I  do a lot of interphasing between a ERP database, DMS's and the like..

Ok, so really you want a technology stack with good DB functionality and data processing capabilities. 

If I where you id look into Java or .Net (Mono) as they will give you the best chance of actually learning something that can be used in the "real world" (They may not be the best tools but they are considered industry standards).

If you want something that is a little more fun and more Linux centric (but still platform independent) why not have a crack at Python.

---

### Post by Jonas thomas on 2008-11-16
> **skirkpatrick said:**
> We've been using wxWidgets with the Databaselayer add-on to work with ODBC.  You could aways use Python with wxPython for GUI.

This looks interesting..
[http://wxcode.sourceforge.net/components/databaselayer/]("http://wxcode.sourceforge.net/components/databaselayer/")

Preliminary looksee says it similar to [JDBC]("http://en.wikipedia.org/wiki/Java_Database_Connectivity")
Unfortunately I'm not familiar with that..

From what I've been reading about wxWidgets it seems like it's definitely worth me spending some time playing with it to see if it's worth pursuing futher.   I was doing some searches on the wxWidget Databaselayer and the search results seem a little bit sparse which is somewhat worrisome. (Perhaps, I wasn't using the correct search terms..)

---

### Post by Jonas thomas on 2008-11-16
> **tinny said:**
> Ok, so really you want a technology stack with good DB functionality and data processing capabilities. 

If I where you id look into Java or .Net (Mono) as they will give you the best chance of actually learning something that can be used in the "real world" (They may not be the best tools but they are considered industry standards).

If you want something that is a little more fun and more Linux centric (but still platform independent) why not have a crack at Python.

Actually, the Java thing, sort of makes sense to me.   I've spent a huge amount of fun time, learning C++ and feel that I've barely scratched the surface.  I get the impression you need to spend a couple of years working with C++ to get proficient at it.  Having said that, I'm under the impression that if you understand what's going on with C++, then Java is no big deal.. Would you agree??

The Python thing is interesting to me also..  But... only so many hours in the day.... I'm under the impression that this is language that's no about to go away either..

---

### Post by Vadi on 2008-11-16
One reason I dislike wxWidgets for is that they claim great cross-platformity, but in reality, they manage to fit in poorly with all 3 platforms (linux, windows, mac). Same for Java.

GTK and Qt look OK on all platforms, with GTK being completely open-source and LGPL - so you can use it in your commercial applications just fine too. I like that freedom. Qt, free for open-source stuff, but then you have to jump through licensing hoops if you want to get anywhere.

I found their GUI designer to be quite lacking when compared to Glade. You cannot do certain things in the designer that you can do via code, forcing you to hardcode certain parts.

---

### Post by Jonas thomas on 2008-11-16
> **Vadi said:**
> One reason I dislike wxWidgets for is that they claim great cross-platformity, but in reality, they manage to fit in poorly with all 3 platforms (linux, windows, mac). Same for Java.

GTK and Qt look OK on all platforms, with GTK being completely open-source and LGPL - so you can use it in your commercial applications just fine too. I like that freedom. Qt, free for open-source stuff, but then you have to jump through licensing hoops if you want to get anywhere.

I found their GUI designer to be quite lacking when compared to Glade. You cannot do certain things in the designer that you can do via code, forcing you to hardcode certain parts.

Hmm... That's interesting.. I was going through the gtkmm tutorial on my "fun" projects and it was sort of disheartening with the amount of coding required just to create a simple widget...(far from RAD) Some of the preliminary research on wxWidgets had me tempted to bypass Glade and try that instead..  Perhaps.... I should work through the Glade tutorial for my fun stuff at home and see where that leads me.....  I'm not sure how much I can leverage that with my work needs though...

---

### Post by Vadi on 2008-11-16
Yeah, use Glade for all your UI creation. Coding only for handling the callbacks and functions.

---

### Post by skirkpatrick on 2008-11-17
> **Jonas thomas said:**
> This looks interesting..
[http://wxcode.sourceforge.net/components/databaselayer/]("http://wxcode.sourceforge.net/components/databaselayer/")

Preliminary looksee says it similar to [JDBC]("http://en.wikipedia.org/wiki/Java_Database_Connectivity")
Unfortunately I'm not familiar with that..

From what I've been reading about wxWidgets it seems like it's definitely worth me spending some time playing with it to see if it's worth pursuing futher.   I was doing some searches on the wxWidget Databaselayer and the search results seem a little bit sparse which is somewhat worrisome. (Perhaps, I wasn't using the correct search terms..)

Actually, I've found wxWidgets to blend very well with their target OS's.  Windows apps look like Windows apps, Linux apps look like Linux, etc.  The biggest reason we went with wxWidgets instead of Qt is because of the licensing.

As far as ODBC goes, wxWidgets is phasing out wxDB inside of wxWidgets due to lack of maintenance.  Databaselayer was pretty easy to build and use in our system.  You can find it along with some other add-ons at [http://wxcode.sourceforge.net/]("http://wxcode.sourceforge.net/") or specifically at [http://wxcode.sourceforge.net/components/databaselayer/]("http://wxcode.sourceforge.net/components/databaselayer/").

---

### Post by Jonas thomas on 2008-11-17
> **skirkpatrick said:**
> Actually, I've found wxWidgets to blend very well with their target OS's.  Windows apps look like Windows apps, Linux apps look like Linux, etc.  The biggest reason we went with wxWidgets instead of Qt is because of the licensing.

As far as ODBC goes, wxWidgets is phasing out wxDB inside of wxWidgets due to lack of maintenance.  Databaselayer was pretty easy to build and use in our system.  You can find it along with some other add-ons at [http://wxcode.sourceforge.net/]("http://wxcode.sourceforge.net/") or specifically at [http://wxcode.sourceforge.net/components/databaselayer/]("http://wxcode.sourceforge.net/components/databaselayer/").
Just out of curiosity, where did you see that wxDB is being phased out?? Is there something else planned to replace it?

---

### Post by tinny on 2008-11-17
> **Jonas thomas said:**
> Actually, the Java thing, sort of makes sense to me.   I've spent a huge amount of fun time, learning C++ and feel that I've barely scratched the surface.  I get the impression you need to spend a couple of years working with C++ to get proficient at it.  Having said that, I'm under the impression that if you understand what's going on with C++, then Java is no big deal.. Would you agree??

The Python thing is interesting to me also..  But... only so many hours in the day.... I'm under the impression that this is language that's no about to go away either..

Yeah, Java is easier than C/C++

Java is just a little stale thats all. Recently ive been playing with Dynamic languages on the JVM, [Groovy]("http://en.wikipedia.org/wiki/Groovy") and [Jython]("http://en.wikipedia.org/wiki/Jython") are a lot of fun.

Having said all this I think you should look into Python personally. If you are going to be doing this learning in your free time you want it to be fun. Python is not a language going nowhere, it is used heavily by the smart people at Google. Also you obviously have an interest in Linux (as you are posting here), Python is very popular in the Linux world.

---

### Post by Kilon on 2008-11-17
> **Jonas thomas said:**
> Actually, the Java thing, sort of makes sense to me.   I've spent a huge amount of fun time, learning C++ and feel that I've barely scratched the surface.  I get the impression you need to spend a couple of years working with C++ to get proficient at it.  Having said that, I'm under the impression that if you understand what's going on with C++, then Java is no big deal.. Would you agree??

The Python thing is interesting to me also..  But... only so many hours in the day.... I'm under the impression that this is language that's no about to go away either..

Actually I think that all languages are no big deal when you take them step by step and leaving out all the things that they do not really interest you or will be any help to you in the foreseeable future. 

Also I think that some languages that are named "easy" can be proven quite difficult under some circumstances (see Python or VB or whatever). "Easy" can be  a very relative and tricky term. In the end what counts is to Enjoy yourself and have fun. Afterall programming is a lot more than learning a computer language as chess is a lot more than simply learning the rules. And that is what makes programming and chess so fun.

---

### Post by Jonas thomas on 2008-11-17
> **tinny said:**
> Yeah, Java is easier than C/C++

Java is just a little stale thats all. Recently ive been playing with Dynamic languages on the JVM, [Groovy]("http://en.wikipedia.org/wiki/Groovy") and [Jython]("http://en.wikipedia.org/wiki/Jython") are a lot of fun.

Having said all this I think you should look into Python personally. If you are going to be doing this learning in your free time you want it to be fun. Python is not a language going nowhere, it is used heavily by the smart people at Google. Also you obviously have an interest in Linux (as you are posting here), Python is very popular in the Linux world.

I've played a little bit with Python, I did some quick checks and found some non-free ODBC drivers for ACCESS and Oracle in the Windows world..
In the open source world if one was to say Widgets are to Glade as SQL is to ????.  What would ???? be?

---

### Post by tinny on 2008-11-17
> **Jonas thomas said:**
> I've played a little bit with Python, I did some quick checks and found some non-free ODBC drivers for ACCESS and Oracle in the Windows world..
In the open source world if one was to say Widgets are to Glade as SQL is to ????.  What would ???? be?

Ummm... (im reaching here)

This is what I would say.

.... as SQL is to MySQL Workbench. (Among other things MySQL workbench is used to design database schemas, it can generate SQL create scripts)

Hope this helps!?!?

---

### Post by Jonas thomas on 2008-11-18
I'm thinking that I'm probably going to need to take some test drives using Netbeans and Python.. and see how I like them... My suspicion is that netbeans will be more useful to me at work, but Python will probably me more fun for me at home.  
I downloaded NetBeans from synaptic to give it a try on my Linux box.
The first issue I'm having is:
```
Warning - could not install module JPDA Debugger API
    JPDA Debugger API - This module requires JDKHOME/lib/tools.jar to be accessible.
This file was not found. Usually this means you are trying to run the IDE with the JRE instead of the full JDK.
If so, please use the --jdkhome command line option to specify a JDK installation.
```
I found a link that I think solves the problem..
[http://ubuntuforums.org/showthread.php?p=5224928]("http://ubuntuforums.org/showthread.php?p=5224928")
Don't have the chance to check this out, since my little one would like some attention :)
(not a big deal, but shouldn't synaptic pick that up as a missing dependancy?

---

### Post by Vadi on 2008-11-18
it should, please report a bug

---

### Post by slavik on 2008-11-18
look at ArgoUML ;)

---

### Post by Jonas thomas on 2008-11-19
> **slavik said:**
> look at ArgoUML ;)

That looks very interesting: [http://en.wikipedia.org/wiki/ArgoUML]("http://en.wikipedia.org/wiki/ArgoUML")

I'm running out of time here before I need to leave for work....
From the wiki link this application seems to be a code generator from a UML.

Some support for SQl?? Hmm...

I think I found a link to a user manual ArgoUML:[http://www.scribd.com/doc/2677506/ArgoUML-manual0-25-4]("http://www.scribd.com/doc/2677506/ArgoUML-manual0-25-4")

---

### Post by Jonas thomas on 2008-11-19
> **Vadi said:**
> it should, please report a bug

Hmm.. I'm not real familiar with the guts of synaptic, but I don't think this an issue with synaptic, but some one who created the the synaptic package didn't cross and t or dot an i...
I need to see if there is some contact info somewhere...

---

### Post by Vadi on 2008-11-19
yes, click on help->report a problem in synaptic

---

### Post by tinny on 2008-11-19
> **slavik said:**
> look at ArgoUML ;)

Does AgoUML support full round tip engineering for any languages? (Java?) E.g. Generate classes from UML modify the class source then synchronise with the UML diagram.

---

### Post by Jonas thomas on 2008-11-19
> **Vadi said:**
> yes, click on help->report a problem in synaptic

That was easy :)

---

### Post by Vadi on 2008-11-19
that's what ubuntu's all about ;)

---

### Post by skirkpatrick on 2008-11-19
> **Jonas thomas said:**
> Just out of curiosity, where did you see that wxDB is being phased out?? Is there something else planned to replace it?

No, there is no plan to replace wxDB.  It is still in the 2.8.x series but will not be in 2.9.x or the new 3.x.

From what I can gather when I started digging into some problems I had with wxDB, it was originally added to wxWidgets after it was implemented and maintained by a company who was using it.  The problem is that there hasn't been a maintainer for several years.

As to why it isn't being replaced, wxWidgets decided to move some of the features out to separate maintained libraries instead of being part of the core.  The Databaselayer addon is up to date and actively maintained.

---

### Post by Jonas thomas on 2008-11-20
> **skirkpatrick said:**
> No, there is no plan to replace wxDB.  It is still in the 2.8.x series but will not be in 2.9.x or the new 3.x.

From what I can gather when I started digging into some problems I had with wxDB, it was originally added to wxWidgets after it was implemented and maintained by a company who was using it.  The problem is that there hasn't been a maintainer for several years.

As to why it isn't being replaced, wxWidgets decided to move some of the features out to separate maintained libraries instead of being part of the core.  The Databaselayer addon is up to date and actively maintained.

I'm a little bit confused here(and should probably research this before blurting something stupid) Do you have any tutorial links on the Databaselayer addon that you could recommend?

Decisions, decisions and lack of time... I think I'm going to spend some time over the holidays playing with Netbeans, as well as wxWidgets probably with Python..  There was a post suggesting I check out Argouml. By chance have you used that application? Any opinions?

---

### Post by wayne.philip on 2008-11-20
I have taken a number of students through this.  Best advice agreed by my post grad students is to load LAMP (Linux Apache MySQL PHP) onto you box (WAMP) for Windows, Use eclipse with PHP as an editor, set up permanent links to php.net and MySql websites and then download an OO (Object Oriented) project into the dev environment like PHPMyEdit or Mantis reverse engineer your way through the code whlst actually building some stuff for yourself. 

Using proper PHP /MySQL projects such as these as a basis ensures that some of the bad habits prevalent i the PHP environment are avoided.

Wayne

---

### Post by skirkpatrick on 2008-11-20
> **Jonas thomas said:**
> I'm a little bit confused here(and should probably research this before blurting something stupid) Do you have any tutorial links on the Databaselayer addon that you could recommend?

Decisions, decisions and lack of time... I think I'm going to spend some time over the holidays playing with Netbeans, as well as wxWidgets probably with Python..  There was a post suggesting I check out Argouml. By chance have you used that application? Any opinions?

I've done some small Python programs that do DB access and use wxWidgets for a GUI.  The only reason they are small is because it is Python :).  wxPython only implements the GUI portions of wxWidgets, everything else (like DB access) is standard Python.  I used pyodbc for my DB access.

Here is the link to Databaselayer's online documentation [http://wxcode.sourceforge.net/docs/databaselayer/]("http://wxcode.sourceforge.net/docs/databaselayer/") which has some sample code.

---

### Post by slavik on 2008-11-20
> **tinny said:**
> Does AgoUML support full round tip engineering for any languages? (Java?) E.g. Generate classes from UML modify the class source then synchronise with the UML diagram.
no idea, I have never used it extensively ...

---

### Post by Jonas thomas on 2008-11-20
> **skirkpatrick said:**
> I've done some small Python programs that do DB access and use wxWidgets for a GUI.  The only reason they are small is because it is Python :).  wxPython only implements the GUI portions of wxWidgets, everything else (like DB access) is standard Python.  I used pyodbc for my DB access.

Here is the link to Databaselayer's online documentation [http://wxcode.sourceforge.net/docs/databaselayer/]("http://wxcode.sourceforge.net/docs/databaselayer/") which has some sample code.

Thanks for the link... I was hoping for little less formal howto, but what the heck, I'll give it a go.

I was looking at some links for pyodbc.  This is looking very interesting to me.  This is sort of a delicate question..
The company I work for has a very conservative[read MSFT] approach to things.  If I pitch the idea of using non-Msft open source cross platform product to the It staff to link into their ERP Oracle based database, I'm going to get an earful...  
I just realized I just said something ironic.  Oracle isn't Msft. But that's besides the point.

Any life advise here/ case studies to site to insure them bad things won't happen?
Regards,

{EDIT} I was looking for answers to my questions.
[http://ubuntuforums.org/showthread.php?t=134680]("http://ubuntuforums.org/showthread.php?t=134680")

---

### Post by Jonas thomas on 2008-11-23
> **skirkpatrick said:**
> Actually, I've found wxWidgets to blend very well with their target OS's.  Windows apps look like Windows apps, Linux apps look like Linux, etc.  The biggest reason we went with wxWidgets instead of Qt is because of the licensing.

As far as ODBC goes, wxWidgets is phasing out wxDB inside of wxWidgets due to lack of maintenance.  Databaselayer was pretty easy to build and use in our system.  You can find it along with some other add-ons at [http://wxcode.sourceforge.net/]("http://wxcode.sourceforge.net/") or specifically at [http://wxcode.sourceforge.net/components/databaselayer/]("http://wxcode.sourceforge.net/components/databaselayer/").

Ok... So I downloaded wxwidgets and downloaded wxFormBuilder as well.
I've been working my way through a tutorial:[http://wiki.wxformbuilder.org/Tutorials/UsingWxFormBuilder]("http://wiki.wxformbuilder.org/Tutorials/UsingWxFormBuilder")
All I have to say is that for a pretty hardcore VB6 programmer, this is feeling very comfortable so far.   Now, I'm at a fork in the rode at step 10 of the tutorial:
> # Now it is time to integrate the generated code with your IDE (Visual C++, Dev-C++, Code::Blocks...). You will have to add the generated files (tutorial_gui.h/cpp) to the project. 
 
So... I'm looking for opinions for optimization here...  
Parameters:
[LIST]
[*]Most of the learning will be in Linux
[*]Long term doing will be in XP.
[*]Personal interests is to pursue C++ at this point (although at some point, when I know what I'm doing, python or Java may be pursued to be more Rad'ish
[*]Need to work in a Mshft environment want to avoid being locked into it. (As a VB6 user who feels abandoned, fool me once, shame on me.... fool me
[/LIST]....)
I need to research Dev-C++ Code:Blocks, etc.. further..
If I choose to run a C++ in XP would I regret using GNU compiler?  I haven't dug into this too far yet, but doesn't MS offer a free compiler?
As far a time and aggravation, would this be the better path??
Also, I read somewhere that there is compatibility issues using pre-compiled libraries with different compilers.

What is the C++ path of least resistance/min hassle on the MS side to optimize cross platform.

WxWidgets=>Wxformbuilder=>(IDE???)=>(compiler?? (Linux(gnu), XP(??))

[Edit]
I just looked at this really interesting wiki page:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")

[Edit]
Just found a interesting link as to how to get Code:;Blocks running in Ubuntu
[URL="http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu"]http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu
[/URL]


It seems like Code:Blocks is the logical choice for my needs...
I guess that leaves the compiler question for XP...

---

### Post by skirkpatrick on 2008-11-23
We have used both GCC (via MinGW) and MS's compiler (yes there is a free version) to build wxWidgets apps.  If you use the GCC compiler, it will make it easier when you want to build the app on Linux.  However, it appears that the MS compiler generates slightly faster and smaller code.

As far as pre-compiled libraries, C libraries are a non-issue.  However, C++ libraries almost never work with a different compiler.  So, if you use MS compiler compatible libraries, you have pretty much locked yourself out of making that program easily transferable to another OS.

We have guys using Code::Blocks while I have been using DialogBlocks (paid for) and Eclipse.  To be honest, I only used DialogBlocks for my first wxWidgets app as all the other apps I've created use an embedded webserver for the GUI.

---

### Post by Jonas thomas on 2008-11-24
> **skirkpatrick said:**
> We have used both GCC (via MinGW) and MS's compiler (yes there is a free version) to build wxWidgets apps.  If you use the GCC compiler, it will make it easier when you want to build the app on Linux.  However, it appears that the MS compiler generates slightly faster and smaller code.

As far as pre-compiled libraries, C libraries are a non-issue.  However, C++ libraries almost never work with a different compiler.  So, if you use MS compiler compatible libraries, you have pretty much locked yourself out of making that program easily transferable to another OS.

We have guys using Code::Blocks while I have been using DialogBlocks (paid for) and Eclipse.  To be honest, I only used DialogBlocks for my first wxWidgets app as all the other apps I've created use an embedded webserver for the GUI.

I need to play with Code::Blocks wxWidgets for a couple of weeks at home, before I try to talking the IT department into installing it on my work machine.  Since my work apps are used exclusively for work on MS machines, I don't think it'll be a big deal if I use the MS compiler.  Actually probably less of an issue...
My primary machine at home is partitioned, with Linux on one side and XP on the other.   It's going to be an interesting exercise see the look and feel as well as performance between the 2 os's...

Btw.. Thank you for sharing your incites, it's been very helpful.

---

### Post by a_flj_ on 2010-11-28
> **skirkpatrick said:**
> 
We have guys using Code::Blocks while I have been using DialogBlocks (paid for) and Eclipse.  To be honest, I only used DialogBlocks for my first wxWidgets app as all the other apps I've created use an embedded webserver for the GUI.
Although your message is old, could you please expand a little on the optic "embedded webserver for the GUI"? I'm just researching what I need for a similar solution (just started a few hours ago and hit this post of yours).

For now, I came up with HSQLDB embedded plus some Java code around it, using the web server of HSSQLDB, but I couldn't find a way of calling the database server over HTTP via JS - I was thinking of using [qooxdoo]("http://qooxdoo.org") for the UI. So I'm a bit stuck.

---

### Post by Elfy on 2010-11-28
Closing 2 year old thread.

@ a_flj_  - start a new thread if you need help

---

