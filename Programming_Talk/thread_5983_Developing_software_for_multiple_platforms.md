---
title: "Developing software for multiple platforms"
date: 2004-11-23
forum: Programming Talk
---

### Post by WW on 2004-11-23
I would like to hear about your  experiences developing software
for multiple platforms. Specifically, I'd like to learn more about
writing code that is easily ported between Linux, Macs (OSX) and
Windows.  I have a project started in C++ that uses the FLTK
gui library, but I am willing to rewrite using a different language
and libraries if it will make it easier to port to multiple platforms.

So far I've only dabbled in Python, but it looks like it would be a
good place to start, especially since there are a couple GUI
options: tkinter is "built in", and wxpython appears to be readily
available.

What are your experiences with developing software for multiple
platforms?  What has worked for you, and what hasn't?

---

### Post by JProgrammer on 2004-11-23
Well the easiest way to write a program for cross platform use is to use Java. The backbone of this language is the 'write once run anywhere' philosophy. It has it's ancestry in C++ so it's not that big a leap. And the [eclipse](www.eclipse.org) platform is a fantastic cross platform IDE.

---

### Post by dataw0lf on 2004-11-23
Personally, I'm not a fan of Java.  I find that it cripples far more programmers than it helps. As an alternative, there is an incredible amount of widget sets out there, wxWidgets, like you mentioned, works very well.  
dataw0lf

---

### Post by jdodson on 2004-11-23
i dont mean to start a flame war between languages.  i will be candid about my exp. with programming with certain languages.

i think c++ with FLTK?  is a fine choice for multi-os programming, if FLTK? is a cross platform library and you can compile using a cross platform compiler such as g++.  personally the only languages i use by choice are the following:

C
python
php
sql

the reason i use C is because if i need something speedy, C is a good choice.  there is hardly any reason to do assembly for speed and if you do assembly your cross platform options become somewhat limited.  plus, C is plenty fast for anything needing speed.

the reason i use python is because i can write applications quickly.  python is a great language to produce most applications, including games(with the pygame library).  if you want to build a cool GUI app, python is good for that because of the cross platform GUI toolkit options.  plus you dont have to wrap everything in a class like you do in java.  python allows you to use OOP or not use OOP if you want to.  

the reason i use php is because it is a great language to do web work in.  i use it to do dynamic web stuff all the time.  php gets some sql then displays the results, it is a great language for dynamic web apps.

the reason i use sql is because it is safer than working with flat files.  sometimes all you need is a simple file, but databases make things so much nicer.  searching, sorting, they rock the bomb.  add in the ER model and things just start getting funner:)

---

### Post by dataw0lf on 2004-11-24
> 
C
python
php
sql
 
Honestly, I couldn't have said it better myself.  C is the obvious choice in Linux (kernel structure, etc).  Python is quietly usurping Perl as the scripting language of choice on Linux (if you don't know why, try sorting through someone else's Perl code... or your own after not messing with it for months).  PHP is *the* language for web programming.  You can talk all you want about 'security' problems, but a program is only as secure as it's designer makes it.  PHP's common adherence to the C and POSIX common libraries make it a very, very attractive choice to C programmers as well.  And, SQL has just become the de facto standard nowadays. We could start a completely different flame war in a MySQL versus PostgreSQL argument ;)

dataw0lf

---

### Post by pdamoc on 2004-11-24
My advice is to let other do the toil and if you're not satisfied with their work... do your own implementation. So... program at the highest level you can: use python not C, use wxpython not wxwidgets. If you're worrying about performance think about this: bad code can be written in any language but in higher level languages is easier to fix. 
[This essay](http://www.python.org/doc/essays/list2str.html) provides for an interesting reading.

---

### Post by jdong on 2004-11-24
I'd have to say that **mono** is a serious contender for cross-platform programming.

Mono also is tons faster than Java for my apps, making it the language of my choice.

---

### Post by dataw0lf on 2004-11-24
[QUOTE=jdong]I'd have to say that mono is a serious contender for cross-platform programming.
Mono also is tons faster than Java for my apps, making it the language of my choice.[/QUOTE] 
From what I've heard, I'd have to agree.  Personally, I've never used it before (nor C#), but it's on my extensive 'TO-DO' list.   Their porting of Gtk+ to .NET bindings (read: Gtk#) has gone over quite well, apparently.  Heh, thanks for reminding me, I'm going to install it as soon as I get home. ;)
Cheers, 
dataw0lf

---

### Post by nehalem on 2004-11-24
I think the biggest appeal to mono isn't necessarily because it's the greatest language (although it by the looks a very nice language), but how much support there is.  With such a core group of gnome programmers pushing this technology you can trust that:
[list=a]
[*]The bindings and things will be up-to date and done well (they are about to release the gtk# to gtk 2.6 bindings, they are staying a little behind on purpose)
[*]The tools to develop with it are top notch.  Already MonoDevelop is about as good as it gets for linux and there is already work on a interface builder built in for it (so you don't have to use GLADE)
[*]The documentation will be good (already they have decent stuff but they won't release the next GTK# till every property is documented)
[*]You can get help from a large community.
[/list] 

With support from Novell going into this (all their client side stuff for Linux will use Mono) it just appears to be the most accessible way to develop for gnome (and later KDE since QT# widgets are in development).

It also has some interesting cross platform possibilities, although to really do this right you would want to use a seperate widget set for each OS, namely GTK#, SWF for windows, and QUARTZ# for apple (still under development).  I like when programs look native anyway.

---

### Post by jdodson on 2004-11-24
[QUOTE=jdong]I'd have to say that **mono** is a serious contender for cross-platform programming.

Mono also is tons faster than Java for my apps, making it the language of my choice.[/QUOTE]

mono looks pretty sweet.  i think i will check it out someday.

---

### Post by mt2 on 2004-11-26
QT is not a bad option and there exists a free (at least partial version) of the lastest distro for every OS you asked for.

The toolkit is actually quite a pleasure to work with. For me, it makes C++ more enjoyable!

---

### Post by elwis on 2004-11-27
I'm kind of a rookie, I've got some years of java behind me, and i have to say that java, eclipse and the SWT library is a nice option. SWT is only a wrapper of the native GUI, which makes it fast and always good looking no matter what kind of OS you're running.

I've played with mono too, and it's nice. Can be kind of troublesome to get it to work on Linux if you don't have a nice apt-get repos though, not fun to install manually package by package. ;)
The trouble with mono is, if you want to run it on Linux + windows, that Gtk# doesn't look to good on windows. by that, i mean native. And since there's no windows.forms on linux, you won't have much choice.. yet. They are rewriting the old solution with winelib as far as I know, so there will probably be a windows.Forms in the future.

The boring part about Qt is that you won't be able to write anything else then GPL software. it doesn't bother me, but if i wanted to write something at work and sell, iäll have to buy that 1500$ per-seat license. That's a reason for me to go with GTK, works everywhere in all forms :)

---

### Post by Ozitraveller on 2004-11-27
I'm already a c#, .net, vb, sql server, asp.net, ms access developer on windows,  and I've had a look mono on windows. Seems ok. I've also done C/C++, Oracle on sco unix. When I can get it to install on Ubuntu properly, I'll be very interested to give it a try.

---

### Post by randy on 2004-11-28
I'd recomend Java and the SWT Widget toolkit.  The new Java release seems to be a bit speedier and the SWT toolkit always looks like the native toolkit.  I find Java much easier to work with than C or C++ especially when it comes to cross platform applications.

---

### Post by AdrianBrown on 2004-12-08
Another vote for Java and Eclipse using the SWT widget set. SWT is much faster and more native looking than Swing or AWT. Java is natively cross platform and SWT has been ported for the platforms you're interested in.

---

### Post by jwenting on 2004-12-16
[QUOTE=AdrianBrown]Another vote for Java and Eclipse using the SWT widget set. SWT is much faster and more native looking than Swing or AWT. Java is natively cross platform and SWT has been ported for the platforms you're interested in.[/QUOTE]
 I've been working professionally with Java since 1999. With no work needed to ensure plaform independence projects have been delivered to OS/2, Linux, AIX, SCO Unix, HP Ux, Solaris, and various Windows versions.

The only other language which comes close is Python and there you have to hope that the GUI libraries are available for your hardware and OS...

---

### Post by Quest-Master on 2004-12-16
I don't like Java very much simply because it doesn't really cut development time as well as Python does.

Languages I enjoy and code in:

C/C++
Python
PHP
SQL

I'm looking into learning Pascal to use Kylix/Delphi for RAD development too.

---

### Post by jwenting on 2004-12-17
Try JSP instead of PHP, it's a lot faster...

---

### Post by warfly on 2005-05-31
Mono might be nice if it ever finishes native WinForms implementation for major platforms. However with GTK# bindings, it's just as cross-platform as other language/GTK binding combinations like C/GTK+, PyGTK or Java-Gnome.

I'd like to recommend SWT/JFace/RCP, WxWindows or QT for native looking cross platform applications. Each has its strength and weakness, so one might need to take some time trying them to be able to judge which is the best for the particular purpose.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=jwenting]Try JSP instead of PHP, it's a lot faster...[/QUOTE]Yeah,  if you have a Sun F15K backing your application server.  Otherwise, no.

Don't use Java.  Swing is slow and a PITA to program in.  SWT is faster, but even more hellish to program in.  It's simply painful.  BTW, the starlight app of SWT, eclipse, doesn't look native at all, so that's a lie.  Don't believe it.  Whoops.

[quote=elwis]The boring part about Qt is that you won't be able to write anything else then GPL software. it doesn't bother me, but if i wanted to write something at work and sell, iäll have to buy that 1500$ per-seat license.[/quote]This isn't true.  Understanding their licensing would be a good idea.  Understanding what the GPL does and doesn't allow you to do would be a better once before you spout such nonsense.

[quote=dataw0lf]PHP is *the* language for web programming. You can talk all you want about 'security' problems, but a program is only as secure as it's designer makes it.[/quote]PHP is working very hard to prove that's not true, since it's core has been riddled with fundamental security bugs a programmer could do nothing about.

That's ignoring the fact that PHP is a security nightmare from a system administration perspective if you'd like to have more than two users using it on the same box.

>  PHP's common adherence to the C and POSIX common libraries make it a very, very attractive choice to C programmers as well.It does nothing of the sort.  It emulates some portions of POSIX poorly, on Linux.  Most of the portions emulated are useless in a web contex anyway.  So I fail to see any attractiveness.

---

### Post by warfly on 2005-05-31
[QUOTE=LordHunter317]Yeah,  if you have a Sun F15K backing your application server.  Otherwise, no.[/QUOTE]
I doubt JSP or PHP has significant performance advantage over the other. I'm a professional J2EE programmer, and from my experience raw performance of scripting language is almost meaningless in most web applications. Rather it's things like productivity, tool support, code manageability, flexibility of platform, scalability that matter. For the simple rule of thumb, if you want a good productivity with relatively small application, or just prototyping choose PHP, and choose J2EE (avoid EJB if possible) for bigger projects.

[QUOTE=LordHunter317]Don't use Java.  Swing is slow and a PITA to program in.  SWT is faster, but even more hellish to program in.  It's simply painful.  BTW, the starlight app of SWT, eclipse, doesn't look native at all, so that's a lie.  Don't believe it.  Whoops.[/QUOTE]
I agree Swing is ugly on Linux, but it's resonably fast with Java 5. And it has fairly well designed API IMHO. SWT's API is confusing, but with JFace and RCP, it could be very productive if you understand the basics.

SWT uses native widgets for most part... well... what can I say if you insist those native widgets don't look native at all when used in Java? :) Of course, it's almost impossible to follow HIG, but it's not SWT's fault as any kind of cross platform GUI application has such   limitation inherently.

If you plan to evaluate certain language/library/graphic toolkit, just ignore all the FUD and try it yourself. For SWT or RCP application, just install the latest version of Eclipse (preferably 3.1M7) and create sample applications included in it so you can judge if it could meet your needs.

---

### Post by nobodysbusiness on 2005-05-31
I've been developing an app in my spare time with Python and wxPython. The wx widgets are very good, though not perfect. (I would like to see a little X button in the tab bar to easily close tabs, for example). Python is a really great language, so I would recommend trying it out if you haven't already.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=warfly]I doubt JSP or PHP has significant performance advantage over the other.[/quote]JSP has infintely more overhead than PHP.  How that transfers into pages servered/sec depends on a variety of factors, but you generally need much heftier hardware to even consider a proper JSP site.  This is why lots of sites offer PHP hosting but only a few offer JSP hosting (compartively speaking).

> And it has fairly well designed API IMHO.No, it's crap.  Swing's a bad bolt-on to AWT to provide features it should have to begin with.  Doing accessibilty work is needlessly complicated, and the full MVC paradigm is too complicated for most applications, having the controller integrated into the model or view as appropriate is superior most of the time.  That's ignoring the whole event thread problem (something .NET's S.W.F  shares, *sigh*).   Also, Java's event model sucks and isn't strong enough, something that heavily cripples Swing.
The API just reeks of *Oh crap forgot this* and someone bolting yet another excessively complicated feature.  Oh, and the fact the UI skinning is something that the application has to control is a travesty, pure and simple.

Especially when you compare it to the alternatives, Swing is terrible.  AWT isn't as bad (because it's only 1/3rd as complicated) but it lacks so many fundamental core features it might as well not exist.

---

### Post by warfly on 2005-05-31
[QUOTE=LordHunter317]JSP has infintely more overhead than PHP.  How that transfers into pages servered/sec depends on a variety of factors, but you generally need much heftier hardware to even consider a proper JSP site.  This is why lots of sites offer PHP hosting but only a few offer JSP hosting (compartively speaking).[/QUOTE]
No it's not true that JSP has more overhead than PHP. While PHP is fully interpreted at runtime in most cases, JSP is compiled to Servlet once and JIT compiles it again to native code. And as I've said above, raw performance of web scripting language is insignificant, since most overhead in web applications come from I/O or design flaw.

On the other hand, PHP is great choice for simple web sites since its productivity is awesome and there're lot of good PHP developers, but when it becomes complex lack of quality ORM framework, declarative security/transaction management, caching (local or distributed) service for domain object or dynamic content, reusable design component (like custom tags or JSF components) get in the way, so generally J2EE will be much more suitable in that case.

[QUOTE=LordHunter317]No, it's crap.  Swing's a bad bolt-on to AWT to provide features it should have to begin with.  Doing accessibilty work is needlessly complicated, and the full MVC paradigm is too complicated for most applications, having the controller integrated into the model or view as appropriate is superior most of the time.  That's ignoring the whole event thread problem (something .NET's S.W.F  shares, *sigh*).   Also, Java's event model sucks and isn't strong enough, something that heavily cripples Swing.[/QUOTE]
I agree that Swing is complex, perhaps it's overly so for many cases. However complexity doesn't mean that its design is bad. On the contrary, Swing's fault is that over-engineered design with sub-optimal implementation makes it too complex and under-performing.

But at least MVC paradigm is so popular these days and Swing also takes that simplified approach you've mentioned that it integrates controller part to view.

And also I agree that Swing sitting on top of AWT is maybe unavoidable, but nevertheless a bad design choice.

Problem of handling concurrency in GUI application is not unique in Swing.

Anyway I can't believe myself defending Swing in public BBS since I really hate it. :) But in certain cases its lightweight approach really helps and its API is elegant even if it's bit complex at times. And even if you don't like Swing/AWT there're always other choice like SWT/RCP, Java-Gnome, wx4j, and so on.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=warfly]No it's not true that JSP has more overhead than PHP.[/quote]JSP requires the full overhead of a JVM and the JSP container server.  I've yet to see a combination of those two that requires less memory than a PHP installation.   JSP requires more resource overhead than PHP.  

> And as I've said above, raw performance of web scripting language is insignificant,I wasn't really referring to overhead related to performance (apologies if I wasn't clear).  I was referring to all overhead, which includes resource utilization.  Apache + mod_jk2 + Tomcat will require more memory than Apache + PHP will.

> I agree that Swing is complex, perhaps it's overly so for many cases. However complexity doesn't mean that its design is bad.If it's complexity gets in the way of anyone using it, it sure does.

>  On the contrary, Swing's fault is that over-engineered design with sub-optimal implementation makes it too complex and under-performing.I don't see how that's not a more verbose waying of saying, "too complex."  Correcting the implementation would requiring fundamental changes to large portions of the API, or at least pulling the window dressing stunts that MS did with C#.

> and Swing also takes that simplified approach you've mentioned that it integrates controller part to view.No, it doesn't.

> But in certain cases its lightweight approachIt's not if you want to write a proper GUI.

> and its API is elegantIt is no such thing.  It's only elegant in the same way a crack addict in a thrift store prom dress can be called elegant.

---

### Post by warfly on 2005-06-01
[QUOTE=LordHunter317]JSP requires the full overhead of a JVM and the JSP container server.  I've yet to see a combination of those two that requires less memory than a PHP installation.   JSP requires more resource overhead than PHP.  

I wasn't really referring to overhead related to performance (apologies if I wasn't clear).  I was referring to all overhead, which includes resource utilization.  Apache + mod_jk2 + Tomcat will require more memory than Apache + PHP will.[/QUOTE]
You should compare Tomcat 5 vs Apache + mod_php rather than Tomcat + mod_jk2 + Apache vs Apache + mod_php. And memory usuage of JVM is not that straightfoward since it entirely depends on GC strategy. If you really want to see Tomcat 5 running with small memory footprint, try limiting maximum heap size of JVM by '-Xmx' start up parameter. Of course it's quite meaningless but you can see my point that performance of any kind of language which runs on a VM with automatic memory management cannot be measured by how much memory that VM occupies at runtime - even when it's using huge amount of memory, it could be just that it didn't see any reason to GC unused objects yet.

[QUOTE=LordHunter317]I don't see how that's not a more verbose waying of saying, "too complex."  Correcting the implementation would requiring fundamental changes to large portions of the API, or at least pulling the window dressing stunts that MS did with C#.[/QUOTE]
Because some might believe some degree of complexity can be tolerated if it gives more flexibility, cross platform ability or whatever feature that can be traded off for simplicity. My point is 'being complex' doesn't always mean that it sucks in all aspect so it needs to be fixed at all costs.

[QUOTE=LordHunter317]It is no such thing.  It's only elegant in the same way a crack addict in a thrift store prom dress can be called elegant.[/QUOTE]
Hehe, I envy your ability in literature to put it that way :) but some prefer complex but flexible design to simple hacks.

Ah, and lastly for the MVC design of Swing... please read the following :
[http://java.sun.com/developer/onlineTraining/GUI/Swing2/shortcourse.html#JFCMVC](http://java.sun.com/developer/onlineTraining/GUI/Swing2/shortcourse.html#JFCMVC)

It clearly says how Swing combines V and C parts into one to simplify full blown MVC design.
> Swing represents components by a common variation of MVC in which **view and controller are combined into an object called a delegate**. Delegates both represent the model, as a view does, and translate user input into the model, as a controller does. Communication between view and controller is very complex. Combining the two simplifies the job of component design.

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=warfly]You should compare Tomcat 5 vs Apache + mod_php rather than Tomcat + mod_jk2 + Apache vs Apache + mod_php.[/quote]No, I really shouldn't.  Tomcat on it's own doesn't have enough featureset to be a proper webserver.  The fact that it does 90% of the work to be one and doesn't do the last 10% is irrelevant, and a real determient to it's cause (and all J2EE container servers really, blame Sun).

> Because some might believe some degree of complexity can be tolerated if it gives more flexibility, cross platform ability or whatever feature that can be traded off for simplicity. My point is 'being complex' doesn't always mean that it sucks in all aspect so it needs to be fixed at all costs.This is true, but it's not true in the specific case of Swing.  It's complexity is a problem for people using the API.

---

### Post by warfly on 2005-06-01
[QUOTE=LordHunter317]No, I really shouldn't.  Tomcat on it's own doesn't have enough featureset to be a proper webserver.  The fact that it does 90% of the work to be one and doesn't do the last 10% is irrelevant, and a real determient to it's cause (and all J2EE container servers really, blame Sun).[/QUOTE]
I'm not sure what features you're referring to which Tomcat 5 lacks to be a proper web server, but if you mean Tomcat can't handle static contents as well as Apache I'd like to point out that at least from 5.x situation has been greatly improved.

Originally this limitation has been come from the fact that unlike other Servlet containers Tomcat project didn't start as a stand alone J2EE server but as an Apache module. So most people let Apache handle static contents and redirected only JSP/Servlet requests to Tomcat.

But from 5.x onwards, performance difference is not so marked and some people even claim Tomcat 5 is faster than Apache 2 in certain situation.

Anyway I DO believe Apache 2 is still better in handling static contents since it's more feature rich and it's proven for years. However, claming Apache/PHP is better than J2EE on Tomcat 5 since Apache is better web server doesn't seem to make sense to me. There're whole lot of high performing feature rich J2EE servers other than Tomcat in market, and from performance point of view, you can do lot more aggressive optimization in J2EE generally (like domain objects caching, or page caching) and JSP/Servlet runs natively due to the JIT compiler.

While I believe it is possible to build a high performance enterprise web sites in PHP in some cases, I also believe (and actually have done many times) building a small and efficient web applications in J2EE is also possible. What matters is design and development skill not raw performance of containers.

Anyway, to get back to the topic (er... what was the topic of this thread? :)), I think Java is perfectly viable approach (esp. with SWT/RCP and stuffs) in building crossplatform applications, so I hope others will evaluate this option too when they plan to build such applications.

As a last note, I'm not defending Java on some kind of religious ground but I've done many crossplatform client or server applications with it and most of them are developed on Linux. So I'm more than happy to see other's criticism, opinions, personal experience on this subject.

All the best.

---

### Post by LordHunter317 on 2005-06-01
[QUOTE=warfly]I'm not sure what features you're referring to which Tomcat 5 lacks to be a proper web server, but if you mean Tomcat can't handle static contents as well as Apache I'd like to point out that at least from 5.x situation has been greatly improved.[/quote]Yes, but not fully rectified.  As such, it's not a fair comparsion unless I retain my existing web server featureset.

My understanding is it's lacking in some other areas related to proper virtual hosting too, plus it doesn't allow for other sorts of dynamic content easily.

> But from 5.x onwards, performance difference is not so marked and some people even claim Tomcat 5 is faster than Apache 2 in certain situation.I wouldn't be terribly suprised about that as prefork is slower in Apache 2 than Apache 1.3.  Apache 2 is only faster if you're serving pure static content via the worker MPM.

> However, claming Apache/PHP is better than J2EE on Tomcat 5 since Apache is better web server doesn't seem to make sense to me.I didn't claim that.  What I claimed was there's less resource overhead with Apache/PHP and that I'll *generally* need less of a server to run a site written in PHP then I will for a site written in JSP.  Something that the industry will support me on.  
Is it possibly to write a JSP site that uses less resources than the PHP one?  Possibly, with a lot of work?  Is that going to be the case for the vast majority of sites?  No, I don't believe so.  Java isn't designed that way.  Nor is J2EE.  Nor would a site taking proper leverage of the features it provides.  None of this is  an issue if you have the hardware to throw at it (which usually isn't a problem).  Hardware's cheap, after all.

> Anyway, to get back to the topic (er... what was the topic of this thread? :)), I think Java is perfectly viable approach (esp. with SWT/RCP and stuffs) in building crossplatform applications, so I hope others will evaluate this option too when they plan to build such applications.Given that C# and .NET are here, I hope no one writes new GUI applications in Java.  Why suffer through that hell?  S.W.F has plently of flaws, I'll admit, as do some other portions of .NET, but they're better than any Java GUI API.

My personal preference is C++ and Qt, but that means you have to pay to do a Windows port.  Something I'm fine with but others are not.

---

### Post by warfly on 2005-06-01
[QUOTE=LordHunter317]Yes, but not fully rectified.  As such, it's not a fair comparsion unless I retain my existing web server featureset.

My understanding is it's lacking in some other areas related to proper virtual hosting too, plus it doesn't allow for other sorts of dynamic content easily.[/QUOTE]
Ok, I agree with that :) If you need to run various web scripting language together, or do a public virtual hosting service Apache is still the best option out there.

[QUOTE=LordHunter317]Is it possibly to write a JSP site that uses less resources than the PHP one? Possibly, with a lot of work?  Is that going to be the case for the vast majority of sites? No, I don't believe so.  Java isn't designed that way.  Nor is J2EE.  Nor would a site taking proper leverage of the features it provides.  None of this is  an issue if you have the hardware to throw at it (which usually isn't a problem).  Hardware's cheap, after all.[/QUOTE]
It's real simple matter of putting something like '-Xmx32m' in the command line argument. But there's no point in limiting maximum amount of memory VM can use to lot less than what is physically available. Yes, JVM is designed to handle memory management automatically, so generally it's not a big deal if Tomcat occupies huge amount of memory - they'll be GCed when needed anyway.

J2EE is not overly complex in my opinion, just some parts of it (like EJB) are so. And while EJB was designed to handle really complex problems which might be the case in about 1% of total web application requirements. When it became available for the first time, Developers who seeks some new technology with which to fill their resumee all rushed to it and applied it everywhere and it failed miserably in most cases. Fortunately J2EE developers became lot smarter so they use lightweight containers and ORM solutions like Spring/Hibernate and so on.

[QUOTE=LordHunter317]Given that C# and .NET are here, I hope no one writes new GUI applications in Java.  Why suffer through that hell?  S.W.F has plently of flaws, I'll admit, as do some other portions of .NET, but they're better than any Java GUI API.[/QUOTE]
I personally hate every .NET things especially when they're used in open source projects - just a thought of writing a GNOME application in WinXP with VS.NET and launch it with .exe executable in gnome-terminal make me cringe  ;-) )

Anyway it's all matter of personal preference so I won't push my choice to others. However I hope you to provide more solid reason why SWF is so much better than any kind of Java GUI toolkits. It's not very productive to say 'I hate this language but I won't tell you why. But I really hate it so I don't even like anyone to use it' without very good reason.

On the otherhand my personal experience with Eclipse RCP is really positive. And I think it's one of the best option to build cross platform GUI application right now since :

(1) It takes native approach just like wxWindows but much more stable IMO. Lightweight toolkits can't really integrate well with desktop environemnt - see the file dialog implementation in Win32 version of GTK+ or Swing's.

(2) Comparatively easy to learn API. It also has full MVC support via JFace. Common components like wizards, preference pages are all built-in.

(3) With RCP, you can get lot of the core features of Eclipse like dockable view management, cross platform help system, editor support for free.

(4) Tool support - Developing RCP application with PDE in Eclipse is real productive. With 3.1M7 you can even package your RCP application for multiple platforms.

(5) Momentum - Currently lot of people are actively participating in developing RCP and SWT so chances are that it will become more mature and feature rich very soon.

(6) 3rd party libraries - With Java, you can get whole lot of quality 3rd party libraries (most notably Jakarta Commons) for many tasks.

---

### Post by LordHunter317 on 2005-06-01
> **warfly]It's real simple matter of putting something like '-Xmx32m' in the command line argument.[/quote]Will tomcat actually run with 32MB of heap or is it going to throw java.lang.OutOfMemoryError the first time I load anything in it?

> J2EE is not overly complex in my opinion, just some parts of it (like EJB) are so.For the simple task of shoving data from a database to a webpage, it is.  

>  And while EJB was designed to handle really complex problems which might be the case in about 1% of total web application requirements.EJBs aren't really truly meant for web applications.

> Fortunately J2EE developers became lot smarter so they use lightweight containers and ORM solutions like Spring/Hibernate and so on.Neither of which are part of the standard J2EE APIs.  

If I take away things like Spring and Hibernate, your job becomes a lot tougher.  To be perfectly fair, sane output without a 3rd party templating system is tough in PHP too.  


[quote]I personally hate every .NET things especially when they're used in open source projects - just a thought of writing a GNOME application in WinXP with VS.NET and launch it with .exe executable in gnome-terminal make me cringe   said:**
> I manage to write C# code without Windows XP just fine.

[quote]However I hope you to provide more solid reason why SWF is so much better than any kind of Java GUI toolkits.The eventing system isn't retarded.  I could go on, but I'd just as soon as drop this.  I think I've made my reasons for disliking Swing perfectly clear.  I could point out some others if you really want to know them.

---

### Post by warfly on 2005-06-01
[QUOTE=LordHunter317]Will tomcat actually run with 32MB of heap or is it going to throw java.lang.OutOfMemoryError the first time I load anything in it?[/QUOTE]Of course if it ever requires more than the specified maximum heap size it will throw OutOfMemoryError, but you don't ever need that much memory to run a simple homepage.

[QUOTE=LordHunter317]For the simple task of shoving data from a database to a webpage, it is.[/QUOTE]I'm not sure why do you think JDBC API is so much complex. For simlpe web page directly accesses database, JSP isn't much different than PHP. Hell, you can even use somthing like [this](http://jakarta.apache.org/taglibs/doc/dbtags-doc/dbtags-1.0/index.html#overview.tags.resultset) if you really want to shove persistence logic into scripting page.

IMO, whole point of J2EE is flexibility and freedom of choice between quality 3rd party libraries built around it. You can either choose simple JDBC call, DBTags, DBUtil, Spring JDBC, SQLMap, OJB, Hibernate, various JDO implementations, or even dreaded EJB CMP for the persistence layer. AFAIK no other web platform provides such wide variety of choice in every aspect of the application as J2EE does now.

[QUOTE=LordHunter317]Neither of which are part of the standard J2EE APIs.[/QUOTE]That doesn't matter to me as long as I can just as easily use 3rd party libs. So, what standard ORM framework or reusable GUI component API (like custom tag or JSF) does PHP provides as standard API? Does it even has other basic features like filter API or declarative security management? I'm not bashing PHP, but clearly J2EE is better choice for some situations.

[QUOTE=LordHunter317]I manage to write C# code without Windows XP just fine.[/QUOTE]Currently, your best bet in writing crossplatform applications in Mono/C# is GTK#. 

And for obvious reason, it has all the problem lightweight approach has on platforms where GTK+ is not default GUI toolkit. Just look at how file dialog is handled in Windows version of GTK+ or Mac version. Many end users don't even know 'My Document' folder is actually resides in 'C:\Documents and Settings\blah blah'.

GUI toolkits with native approach like SWT or WxWindows provides much better native fidelity.

[QUOTE=LordHunter317]I think I've made my reasons for disliking Swing perfectly clear.  I could point out some others if you really want to know them.[/QUOTE]Yes, I remember you've said Swing is too complex and event system is bad and I agree at least with the former one. However how come these couple of criticisms on Swing can justify you to say '.NET is better than **any kind of Java GUI**' so you don't even want others to try Java at all? SWT/RCP/JFace, Wx4J, Java-Gnome are all really bad just because Swing has some flaws? Sorry, but I don't seem to follow your reasoning here.

---

### Post by LordHunter317 on 2005-06-01
> **warfly]Of course if it ever requires more than the specified maximum heap size it will throw OutOfMemoryError, but you don't ever need that much memory to run a simple homepage.[/quote]But if I want to do anything interesting  How far will 32MiB of heap really take me?  This isn't worth discussing much further.  It's accepted fact Java's design is going to require more system resources than PHP.  End of story.  How much of a big deal that is or isn't is situationally dependent.

> I'm not sure why do you think JDBC API is so much complex.I never did say that or imply that.  I don't think it's complex, though I do think it's somewhat tedious.

It's the shoving data out that J2EE makes tedious.

>  Hell, you can even use somthing like [this](http://jakarta.apache.org/taglibs/doc/dbtags-doc/dbtags-1.0/index.html#overview.tags.resultset) if you really want to shove persistence logic into scripting page.If I was going to do that, I'd just pay for ColdFusion MX, I think.

> IMO, whole point of J2EE is flexibility and freedom of choice between quality 3rd party libraries built around it.Not really.  Considering third party libraries makes any comparsion difficult unless you fix what libraries you're talking about.

Even then, it's not really fair argument anyway, as I can do that just as easily with PHP as I can with J2EE.  J2EE doesn't have any revolutionary features that make using 3rd-party frameworks any eaiser.  

As such, what's interesting is what's provided by the J2EE standard and the PHP releases.  Everything else is tagential. 

And if you're talking about doing JSPs using just what's provided by the J2EE specification, it's a fairly painful experience indeed.  Which is why nobody does it.

>  AFAIK no other web platform provides such wide variety of choice in every aspect of the application as J2EE does now.If we're considering 3rd-party libraries, I bet I can find a comparable mess of PHP code out there as well.  In fact, I wouldn't build a large-scale site in PHP (if I were going to do such a task) without it.  Just like I probably wouldn't do much JSP work without Spring.

> That doesn't matter to me as long as I can just as easily use 3rd party libs. So, what standard ORM framework or reusable GUI component API (like custom tag or JSF) does PHP provides as standard API? It doesn't, but what J2EE provides is crap.  That's why everyone uses some 3rd-party system.  In some aspects, I think "If you can't do it right, don't do it at all" is really appropriate here, and something the Java developers should have heeded.

> I'm not bashing PHP, but clearly J2EE is better choice for some situations.Yes, if your needs are complicated, J2EE can be worthwhile.  If your needs are simple and all you have is J2EE, it doesn't really look that much better than PHP.  Really.  

And I don't think I've said anything different, and I don't think you've really said anything different, but you seem hellbent on continual preaching to the choir.   said:**
> GUI toolkits with native approach like SWT or WxWindows provides much better native fidelity.True, but at the end of the day, users will generally deal and it's not worth the programmer fustrations to jump through unecessary hoops for native L&F toolkits if there's a clearly superior lightweight solution.

> However how come these couple of criticisms on Swing can justify you to say '.NET is better than **any kind of Java GUI**' so you don't even want others to try Java at all?Because several of Swing's fundamental flaws (like the eventing) are fundamental of Java itself, hence all GUI toolkits suffer from it?  

Seeing as GUIs deal largely with events, I want an event model that doesn't suck.  Which means no Java.

---

### Post by warfly on 2005-06-02
> **LordHunter317]Yes, if your needs are complicated, J2EE can be worthwhile.  If your needs are simple and all you have is J2EE, it doesn't really look that much better than PHP.  Really.

And I don't think I've said anything different, and I don't think you've really said anything different, but you seem hellbent on continual preaching to the choir.   said:**
> Ok, fair enough I will drop the whole J2EE arguments here since it's irrelevant to to topic. But before accusing me of my 'preaching to the choir', please consider what you've said about JSP/J2EE above :

> Yeah, if you have a Sun F15K backing your application server. Otherwise, no.
[QUOTE]JSP has infintely more overhead than PHP.
> Tomcat on it's own doesn't have enough featureset to be a proper webserver.
At least I think those kind of remarks are ungrounded FUD, so I simply asked you for the reason because my personal experience as a professional J2EE developer seems to be much different than yours.

Anyway let's just drop this J2EE vs PHP stuffs for now, since it seems both of us are running risk of hijacking this thread to another subject.

[QUOTE=LordHunter317]Because several of Swing's fundamental flaws (like the eventing) are fundamental of Java itself, hence all GUI toolkits suffer from it?  

Seeing as GUIs deal largely with events, I want an event model that doesn't suck.  Which means no Java.[/QUOTE]
Could you please be more specific about those 'fundamental' flaws? I'm aware that you've mentioned about thread synchronization issue but I don't think other toolkits are immune to it.

---

### Post by LordHunter317 on 2005-06-02
[QUOTE=warfly]At least I think those kind of remarks are ungrounded FUD,[/quote]They're not, since I justified them, althought they were intentionally ridden with hyperbole.  

> Could you please be more specific about those 'fundamental' flaws?Oh sure.  Because Java doesn't have anonymous methods, only anonymous classes, an object listening must inherit some declared interface (e.g., ActionListener).  This sounds fine, until you realize that most interfaces in Java look like this:```
public interface MyStupidEventListener {
    public void myStupidEventOccurred(MyStupidEvent e);
}
```and are just one method.  The reason we have to have so many different interfaces is because the method signature is different in what event they take.
  
C# uses delgates to solve this same problem and avoids all the extra tedious work and namespace polution.  It gives me the advantages that I don't have to inherit from anything, I can put my method wherever I want, and I can call my method however I want. 

With Java, I can only really put Listeners with a single method wherever I want.  Consider the case of WindowListener.  It has something like 4-5 methods in it.  But generally, a class inheriting from WindowListener is only interested responding to events fired to one or two of those methods.  Meaning that if you inherit from WindowListener, you have to provide stubs for all these other methods.  Sun however, saw this problem and provided a solution: WindowAdapter.  It's a class that inherits from WindowListener and provides stub methods implementations that do nothing.  So now, I can inherit WindowListener and only provide a implementation for whatever method I'm interested in.

Except that exposes another problem.  WindowListener is an interface.  WindowAdapter is a class.  Any class can freely inherit from WindowListener, since it's an interface.  Only classes not inheriting from a parent class can extend WindowAdapter.  So now, the limitations of Java's MI model have come to bite us.
Sun's solution of course, is to use anonymous classes.  Which works in a lot of situations.  But they're somewhat ugly to type and mean you have to deal with the restrictions imposed on them.  Sometimes, those restrictions get in your way.  

C# doesn't have these problems.  The event model is just cleaner, since it's modeled on methods, not whole classes.  

Also, adding a listener to an event isn't standardized in any way in Java.  By convention, a method named like: "addActionListener()" is used to add an object to the list of those to recieve an event.  But it's just a convention, and nothing forces me to do that.  In C#, this is standardized.

---

### Post by warfly on 2005-06-02
Ok, it seems finally I can understand what you're talking about 'fundamental flaws' of Java. I tend to agree that event handling in Java is quite verbose, but at least I don't think it is so fundamental a flaw as to forbid others from using it at all. Anyway I respect your opinion on that matter and I don't have any intention to persuade you to use it.

It's not just event handling that is verbose in Java language in general. But it's simply a design choice and I prefer to have clearer design even if it's rather verbose or complex to compact but obscure one since you can always let tools to do the tedious part and concetrate yourself on design instead. With Eclipse, you can add an event handler via annonymous class in less than 3 seconds. 

Finally, event handling via 'addXXXListener' is not enforced but at least is well documented in JavaBeans spec. just like getter/setter method convention. It'd be better if it could be enforced by language, but no big deal if it's not.

Anyway it's not very productive to refute or justify personal preferences, so I'd like to leave it to others to decide if it meets their needs or not in cross platform development and abstrain myself from refuting such claims from now on.

---

