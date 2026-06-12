---
title: "Python vs. Java, which is better at dealing with XML database?"
date: 2011-07-12
forum: Programming Talk
---

### Post by zhaotianwu on 2011-07-12
Hi, I'm building a multi-purpose XML database and wondering which language I should use as back-end programming language, Java or Python. My first thought was Python as it is easier and more friendly. However, as I do more research it seems to me that Java seems to be better at dealing with XML. There are many tools dealing with XML are based on Java. Is that true? Seniors please give me some thoughts, thanks.

---

### Post by ricegf on 2011-07-12
> **zhaotianwu said:**
> Hi, I'm building a multi-purpose XML database and wondering which language I should use as back-end programming language, Java or Python.

XML is a fairly mature and widespread technology, so most languages have excellent support for both DOM and SAX processing approaches including Java and Python.

I would personally choose based on two factors.

First is the class of system you plan to build. If you're building an enterprise-class corporate data processing system, I'd lean toward Java, as the infrastructure for the high end has generally better commercial support. If you're building a workgroup-class or personal system, I'd lean toward Python due to it's cleaner and less verbose syntax. If you're building a third-party hosted system for the open Internet, then I'd lean toward whichever technology your preferred hosting company supports best.

Second is resources. If your team (or you if this is currently a one-person project) is more familiar with one language or the other, that will be the lower risk approach. But if you want to learn the less familiar language to round out your resume, here's a great opportunity if you can presently afford the learning curve.

You also have a third option, of course - Jython, an implementation of Python that runs on (and gives easy access to the class libraries for) the Java Virtual Machine. Perhaps that would give you the best of both worlds; we've used it quite successfully as well in a mixed Python / Java environment.

If you go with Python, I would also recommend that you avoid the temptation to treat it as a scripting language for quick and dirty implementation. Instead, design and implement your classes well, just as you would with a OO-only language like Java, and you'll be more likely to end up with a stable and maintainable system in the end.

Have fun!

---

### Post by zhaotianwu on 2011-07-13
> **ricegf said:**
> XML is a fairly mature and widespread technology, so most languages have excellent support for both DOM and SAX processing approaches including Java and Python.

I would personally choose based on two factors.

First is the class of system you plan to build. If you're building an enterprise-class corporate data processing system, I'd lean toward Java, as the infrastructure for the high end has generally better commercial support. If you're building a workgroup-class or personal system, I'd lean toward Python due to it's cleaner and less verbose syntax. If you're building a third-party hosted system for the open Internet, then I'd lean toward whichever technology your preferred hosting company supports best.

Second is resources. If your team (or you if this is currently a one-person project) is more familiar with one language or the other, that will be the lower risk approach. But if you want to learn the less familiar language to round out your resume, here's a great opportunity if you can presently afford the learning curve.

You also have a third option, of course - Jython, an implementation of Python that runs on (and gives easy access to the class libraries for) the Java Virtual Machine. Perhaps that would give you the best of both worlds; we've used it quite successfully as well in a mixed Python / Java environment.

If you go with Python, I would also recommend that you avoid the temptation to treat it as a scripting language for quick and dirty implementation. Instead, design and implement your classes well, just as you would with a OO-only language like Java, and you'll be more likely to end up with a stable and maintainable system in the end.

Have fun!

Thank you ricegf for your very generous and informative tip!
My project so far is still a one-person project and still a bit messy. :) So I guess Python will be the choice. I wasn't sure earlier because software like eXist that provides XML query seems to be based on only Java. Actually if I really want to think outside of the box and my database is small I don't even need a query language, I can write my own search codes, can I? Is that feasible?
Another question for you, since part of this program will be run on a smart phone system, probably Android or Windows Mobile, it needs to constantly sync with the desktop counterpart. Does Jython support seamlessly portability as well as native Java Virtual Machine does? I mean, if portability is an issue, should I choose native Java exclusively?
Many thanks!
[COLOR=#000000]
[/COLOR]

---

### Post by ricegf on 2011-07-14
> **zhaotianwu said:**
> Actually if I really want to think outside of the box and my database is small I don't even need a query language, I can write my own search codes, can I? Is that feasible?

Certainly. On a modest machine, you could simply load the database file directly into RAM (e.g., DOM, or perhaps Python's Pickle) and work with it as is. 

> 
Another question for you, since part of this program will be run on a smart phone system, probably Android or Windows Mobile, it needs to constantly sync with the desktop counterpart. Does Jython support seamlessly portability as well as native Java Virtual Machine does? I mean, if portability is an issue, should I choose native Java exclusively?


Well, your desire for a native smartphone app is likely to drive you to a specific technology - for Android or RIM, you're probably best off to program in Java (different class libraries for each, unfortunately), for iPhone think Objective C, for Symbian and MeeGo think C++ or Python with Qt4 (also used for Unity 2D, I believe), and for Windows Phone 7 think C# and .NET.

But most of the above are also supporting Internet standard clients - Javascript and HTML 5, which is also the target language for HP's webOS and the upcoming Windows 8 for Tablets, or so I hear, and (more importantly ;-) ) for Unity. That may be a more portable approach for a client than Java or Python, though HTML 5 isn't yet a standard and so portability is still a bit of a work in progress, and it's arguably more difficult to implement a complex client in web technologies than native toolkits.

You have quite a few choices. It's a blessing - and a curse. :-D

---

### Post by PaulM1985 on 2011-07-14
As ricegf said, you should really be looking at what languages your target platform supports before looking at which of Python and Java is best at dealing with XML.

Paul

---

### Post by zhaotianwu on 2011-07-15
> **ricegf said:**
> Certainly. On a modest machine, you could simply load the database file directly into RAM (e.g., DOM, or perhaps Python's Pickle) and work with it as is. 



Well, your desire for a native smartphone app is likely to drive you to a specific technology - for Android or RIM, you're probably best off to program in Java (different class libraries for each, unfortunately), for iPhone think Objective C, for Symbian and MeeGo think C++ or Python with Qt4 (also used for Unity 2D, I believe), and for Windows Phone 7 think C# and .NET.

But most of the above are also supporting Internet standard clients - Javascript and HTML 5, which is also the target language for HP's webOS and the upcoming Windows 8 for Tablets, or so I hear, and (more importantly ;-) ) for Unity. That may be a more portable approach for a client than Java or Python, though HTML 5 isn't yet a standard and so portability is still a bit of a work in progress, and it's arguably more difficult to implement a complex client in web technologies than native toolkits.

You have quite a few choices. It's a blessing - and a curse. :-D

If I'm reading this right, in the long run taking into consideration HTML5, Javascript seems to be the finalist winner? Did I get this right? Can I just write a single piece of jython code and run both on desktop and smartphone JVM (smartphone is using Android)? 

By the way, you mentioned that if using Python it is recommended not treating it as a scripting language but try to design the classes from scratch, which is paying in the long run in terms of stability and maintainability. I find this philosophy quite insightful and deep. Would you please elaborate on this a little bit, preferably give me an example? As a beginner I think it is very tempting to try to &quot;glue&quot; everything out there, rather than design everything from scratch.:P

---

### Post by PaulM1985 on 2011-07-15
If you are using Android I would say you would probably be better to use Java.

Try to read about object-oriented design, you should see that your questions on scalability and maintainability become answered:
[http://codebetter.com/raymondlewallen/2005/02/08/advantages-of-an-object-oriented-approach-for-new-programmers/](http://codebetter.com/raymondlewallen/2005/02/08/advantages-of-an-object-oriented-approach-for-new-programmers/)
[http://staffweb.londonmet.ac.uk/~chalkp/proj/ootutor/](http://staffweb.londonmet.ac.uk/~chalkp/proj/ootutor/)
[http://en.wikipedia.org/wiki/Object-oriented_design](http://en.wikipedia.org/wiki/Object-oriented_design)

Paul

---

### Post by ricegf on 2011-07-15
> **zhaotianwu said:**
> ... part of this program will be run on a smart phone system, probably Android or Windows Mobile...


> **zhaotianwu said:**
> ...smartphone is using Android...
 

*Sigh*  The FIRST step in any software project is to understand your requirements. (Not to feel bad - the first mistake most beginners make is NOT understanding their requirements! ;-) ) 

You started with two smartphone platforms, Android which is most commonly programmed in Java, and Windows Mobile, which is most commonly programmed in C++ (though I also considered that you might really mean Windows Phone, a newer and totally incompatible environment most commonly programmed in C#). You also mention the desktop a little later, which could be Windows (C#), Mac (Objective C), or Linux (C for Gnome or C++ for KDE). 

The common denominator, so that your client has a fair shot at running on all six from a single code base, would be JavaScript and HTML5, so that was my recommendation.

If you're interested in an Android-**only** client, then as I said above, Java is the native language and the most direct route to an Android smartphone client. 

> 
Can I just write a single piece of jython code and run both on desktop and smartphone JVM (smartphone is using Android)?


Not as easily as that. The next realization is that, for modern programming, the language is *almost* as important as the class library. 

The class library provides you with the methods you'll need to create application windows, buttons, lists and other GUI elements, and the mechanisms your users will need to interact with them. It also provides your network access and XML tools.

Java has a standard class library used on the desktop. Android provides its own unique class library, which is distinct from the desktop Java class library. So while both are programmed in the Java *language*, the libraries differ quite a bit. 

A clever programmer could maintain a single code base in Java that covers both platforms, but I'm less clever and would keep them distinct (if I chose Java).

Jython can indeed run on Android if you know how to get it there (google is your friend), but it's not a good choice if you plan to share your code. And Android is open source and can be run in a virtual machine on a desktop, so you could use a native Android app there, but that's not trivial either.

JavaScript, however, provides its own class library which is fairly common across all popular smartphones and desktops. In fact, Microsoft has announced that Windows 8 will focus on using Javascript and HTML5 in place of .NET. If you want to minimize the amount of code you write to cover *multiple* client platforms, your best bet (and likely the wave of the future given Microsoft's endorsement) is to learn JavaScript and the associated technologies.

So, bottom line given more than one client platform (Android and desktop, right?), I'll end up still recommending Python on the server and JavaScript on the client. The languages are fairly easy to learn and quite portable, and I think you'll get something up and running faster this way.

A fair alternative is to do a native Android client in Java, a separate desktop client in Java (different class library, remember?), and the server in Java - three code bases instead of two, but a single language.

Your choice.

> 
if using Python it is recommended not treating it as a scripting language but try to design the classes from scratch, which is paying in the long run in terms of stability and maintainability... Would you please elaborate on this a little bit...


Script code tends to get unwieldy after a few hundred lines, even well-structured into functions. The problem is that you have to pass functions your data structures, and the data structures tend to evolve as your program matures. The effects of data structure changes are thus scattered around your code base, making it hard to keep everything coherent and introducing obscure bugs.

In OO, the data structures are objects that come with associated methods. You can change the data structures, and all of the methods that care are *right there next to them*. Other parts of your program access the data structures through those methods, so as long as the method signature doesn't change, the other parts of the program aren't affected. And if the method signature does change, the compiler will almost always catch that for you. (Compilers will miss changes in *protocol*, e.g., "call the Init method before the Display method", but we still don't have the RPM (Read Programmer's Mind) instruction. Yet. ;-) )

If you're new to Python and decide to go that route, read the OO sections of [http://diveintopython.org](http://diveintopython.org).  Great resource.

Aren't you glad you asked?  :-D 

Have fun!

---

### Post by ricegf on 2011-07-15
Y'know, on re-reading your original posts, I think your architecture is actually client-only - you're just downloading an XML file from your desktop to smartphone via (say) a file manager so you can view the data on the go.  Right?

In that case, if you're only using Android for the smartphone, I'd be tempted to go all-Java. You'll have to write a different GUI on the desktop in the long term, but in the near term you can probably get Android running in a virtual machine on your desktop (mine's running on Ubuntu 10.10) and so get a functional system up and running rather quickly with a single program.

Quick gratification sounds like the ticket here, and Java will get you there fastest in this case (assuming I'm finally understanding).  Sorry for the diversion - but hope it was helpful in the broader sense. And you can see why building enterprise-class systems is so hard - it's not the coding, it's *figuring out what we need *that causes all the detours!  :-D

---

### Post by zhaotianwu on 2011-07-16
Hi ricegf.
After a thorough reading of your rich advice, I'm now convinced that [SIZE=2]**Javascript and HTML5**[/SIZE] is my choice. And you have really read my mind  that I'm really tempted to establish something up and running soon.:oops:

> **ricegf said:**
> 
You started with two smartphone platforms, Android which is most commonly programmed in Java, and Windows Mobile, which is most commonly programmed in C++ (though I also considered that you might really mean Windows Phone, a newer and totally incompatible environment most commonly programmed in C#). You also mention the desktop a little later, which could be Windows (C#), Mac (Objective C), or Linux (C for Gnome or C++ for KDE). 


Actually here is my platforms profile. My desktop is dual-boot between Windows XP and Unbuntu 10.10. As for the smartphone, my phone is quite old and is running on Windows Mobile 6.1, my girl friend's phone is Android, but she knows nothing about programming, not even a beginner:p:p. My next phone is very likely an Android.

> **ricegf said:**
> 
The common denominator, so that your client has a fair shot at running on all six from a single code base, would be JavaScript and HTML5, so that was my recommendation.
......
JavaScript, however, provides its own class library which is fairly  common across all popular smartphones and desktops. In fact, Microsoft  has announced that Windows 8 will focus on using Javascript and HTML5 in  place of .NET. If you want to minimize the amount of code you write to  cover *multiple* client platforms, your best bet (and likely the  wave of the future given Microsoft's endorsement) is to learn JavaScript  and the associated technologies.

I've never done any programming before and this is my first one-person project. So my goal is just a program that can run, no matter how bad the performance is.


> **ricegf said:**
> 
So, bottom line given more than one client platform (Android and desktop, right?), I'll end up still recommending Python on the server and JavaScript on the client. 

Why do I still need Python on the server? Couldn't I just use Javascript both on my desktop and on my smartphone? Does Python provide any benefit that Javascript doesn't?

> **ricegf said:**
> 
Jython can indeed run on Android if you know how to get it there (google  is your friend), but it's not a good choice if you plan to share your  code.

I don't quite understand this:confused:. Why is Jython bad for sharing code? Isn't it also an open source implementation of Python? Would you please explain a bit little more? Thanks.

> **ricegf said:**
> 
Script code tends to get unwieldy after a few hundred lines, even well-structured into functions. The problem is that you have to pass functions your data structures, and the data structures tend to evolve as your program matures. The effects of data structure changes are thus scattered around your code base, making it hard to keep everything coherent and introducing obscure bugs.

So I guess this drawback is not limited only to Python. Maybe Javascipt also need to resist the temptation to &quot;glue&quot; existing codes excessively. Actually I've seen someone describe Javascript as &quot;superglue&quot;, does it mean Javascript relies even more heavily on scripting?



Sorry for being so long, especially on a weekend:P. Thank you!

---

### Post by zhaotianwu on 2011-07-16
> **ricegf said:**
> Y'know, on re-reading your original posts, I think your architecture is actually client-only - you're just downloading an XML file from your desktop to smartphone via (say) a file manager so you can view the data on the go.  Right?


Exactly! The program on my smartphone will be just a "viewer". And it won't communicate with desktop end through the Internet. It will synchronize with the desktop part either through Microsoft Activesyc or I will sync them manually.

---

### Post by ricegf on 2011-07-16
> Do you think this is feasible or just a crazy idea?

Sounds like a great idea to me!

> Why do I still need Python on the server? Couldn't I just use Javascript both on my desktop and on my smartphone? Does Python provide any benefit that Javascript doesn't?


Javascript isn't used much for programming servers on the open Internet, so Python or Java might be a better choice if you wanted to do that - the latter two have excellent frameworks (class libraries) that do much of the heavy lifting for you, and you'll find more forums and people who will give tons of advice (*self-conscious pause*).

But I now think that you're only doing desktop and smartphone versions of your application, and Javascript should be just fine for those platforms. And using Firefox to render your UI should work well and result in a highly portable app, too.

NOTE FOR LATER: Once your code is doing useful things, and if you're willing to share it with others, consider learning to use a site such as bazaar or github. This is called "configuration management", keeping track of your earlier versions with very little effort while also allowing other programmers to see and suggest changes ("patches") to your program. It's central to becoming a successful programmer, once you've got your first program up and running.  But code first.  ;-)

> 
I don't quite understand this:confused:. Why is Jython bad for sharing code? Isn't it also an open source implementation of Python? Would you please explain a bit little more? Thanks.


That was badly worded on my part. What I meant is that, if you wrote a Jython program to share with other Android users, and if they would need to separately install Jython on their phones to run it, that would be far less convenient that writing a Java or Javascript app that would install seamlessly with no additional effort. 

Disclaimer: I'm not personally familiar with Android package management, so I'm not *sure* that you couldn't just declare a dependency to Jython and all would be well, as you could in (for example) Ubuntu. The google results implied getting Jython onto Android required some manual effort, and that would discourage users from trying your program.  But if it's just for you and a friend or two, it's not a big deal.

Darned near every computing device has Javascript, though, so you're set.

> I've seen someone describe Javascript as "superglue", does it mean Javascript relies even more heavily on scripting?

Javascript is even more focused on scripting than Python, but it's a full object-oriented language and probably among the 10 most popular (with Java, C/C++/C#/Objective C, Python, and a couple of others - google "TIOBE Programming Community Index" for one such measure if you're interested). I'd encourage you to design your Javascript according to good object-oriented principles, and your app should work well.

---

### Post by zhaotianwu on 2011-07-17
> **ricegf said:**
> Sounds like a great idea to me!



Hi ricegf, Thank you very much for your encouragement!

1. Mozilla Firefox is written in C/C++, JavaScript, CSS, XUL, XBL. If I really want to play with Mozilla Firefox (may even modify it) for my project quick and dirty but still don't have a lot of time to learn everything, can I get away with just learning Javascript and XML? Or at least I should try to learn CSS as well? I appreciate your advice.

2. Any comment on some dialect of Javascript, e.g. coffeescript?

Thank you!;)

---

### Post by myrtle1908 on 2011-07-17
> **zhaotianwu said:**
> 2. I want my program (a CRM & decision support system) capable of replacing much of Microsoft Office Suite features, like calendar, schedule planner, journal, email storage, etc, based on a business logic database. Can Javascript's class libraries allow me to program all these features? Since it will involve a lot of "drill down" features, 


JavaScript (the language) does not provide any UI widgets/libraries.  Widgets are created by interfacing with the browser Document Object Model (DOM).  For example, to create a non-standard button you may draw a box (DIV tag), colour/style it with CSS and make it clickable  via a DOM Event/Handler.  Unless you wish to get your hands dirty creating these from scratch, there are many toolkits which will do this for you ie. widgets and layout management and all things UI.  For example, take a look at Sencha/ExtJS ... [http://www.sencha.com/](http://www.sencha.com/).

> **zhaotianwu said:**
> is Javascript good at dealing with Vector Graphics?

Look at Scalable Vector Graphics (SVG) which most modern browsers implement.  Note: for IE it's v9+.  Older IEs do VML.  Again, there are toolkits which do the heavy lifting for you ... like this JavaScript one ... [http://raphaeljs.com/](http://raphaeljs.com/).

---

### Post by zhaotianwu on 2011-07-18
> **myrtle1908 said:**
> JavaScript (the language) does not provide any UI widgets/libraries.  Widgets are created by interfacing with the browser Document Object Model (DOM).  For example, to create a non-standard button you may draw a box (DIV tag), colour/style it with CSS and make it clickable  via a DOM Event/Handler.  Unless you wish to get your hands dirty creating these from scratch, there are many toolkits which will do this for you ie. widgets and layout management and all things UI.  For example, take a look at Sencha/ExtJS ... [http://www.sencha.com/](http://www.sencha.com/).



Look at Scalable Vector Graphics (SVG) which most modern browsers implement.  Note: for IE it's v9+.  Older IEs do VML.  Again, there are toolkits which do the heavy lifting for you ... like this JavaScript one ... [http://raphaeljs.com/](http://raphaeljs.com/).

Thank you myrtle1908, this is very helpful.
Dear ricegf, what is your opinion towards my 1 and 3 question, I'm very much looking forward to that!:P

---

