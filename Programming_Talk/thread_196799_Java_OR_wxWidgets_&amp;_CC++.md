---
title: "Java OR wxWidgets &amp; C/C++?"
date: 2006-06-14
forum: Programming Talk
---

### Post by nythrix on 2006-06-14
Hi everyone!
Please easy on me, I'm quite new to linux and totally new to this forum. I've tried Mandriva and even managed to install Gentoo but i run back to windows after a week of using. So far Ubuntu looks like a deeper and true-er relationship. Especially when it comes to my xpfriends. Their drooling over this Xgl-compiz driven gnome calls for some secret camshots :cool:. Besides, I feel quite safe (can't work as regular user on XP, some apps I need don't work), stability is good (my win run very stable so no big change then), language support is wonderful, don't hear my hdd's furious grabbing anymore (that's a mystery to me), (un)installing is like grand-grandpa-proof, and did i mention the eyecandy?
Ok, some things are not that good (no driver for my printer, a couple of games and apps really missing) but that's not fault of the developers or the community. All in all a huge thank to ALL of you. You're doing a fantastic job.

Speaking of community, I have this half finished school project (cards game) I'd like to make available. It's written in C++ and uses MFC (yes, i know) and I'd like to have a fully portable version of it. Should i rewrite it to Java? Or is it better to hang  it on something cross-platformic like wxWidgets?
The java way has the advantage of being nicely portable but then I have to rewrite it all (~50kB).
The other way round may not be full of typing but I have 00 (double zero) experience with this kind of development. Plus I can't find a nice IDE for C/C++. I was used to Visual Studio which is MS's best piece of soft IMO.
Suggestions?

Watch your step when parsing, I have no native english support :D

---

### Post by nythrix on 2006-06-14
Heck! I totally forgot about C# and .NET! They crossed my way two or three times and would be a bit easier than Java. How's .NET support going on on linux? Is it usable?
Thanx again.

---

### Post by snoop on 2006-06-14
I personally would write it in wxWidgets. Are you using directX, opengl, sdl or something else?

I would personally stay away from .net because mono is still incomplete, though useable as shown by beagle, diva, etc..C# is a pleasure to use, I have to admit. Edit: Apparently, mono is not too bad. See this post: [http://www.ubuntuforums.org/showthread.php?t=193457](http://www.ubuntuforums.org/showthread.php?t=193457)

Since it is a card game and speed is not important, and if you want to rewrite all of it, I would suggest python and pygame. Really simple to write and development goes fast. 

Oh, and I would avoid java.

Edit: a good c/c++ ide would be anjuta. [http://www.anjuta.org/](http://www.anjuta.org/) Its in the repositories.

---

### Post by vinodis on 2006-06-14
IMHO:
Write it in Java with the Free NetBeans IDE using its free GUI editor just like your Visual Studio.
Its the fastest and most cross-platform and efficient approach.

---

### Post by bieber on 2006-06-15
C# using .GNU isn't too terribly bad, but Microsoft holds some key patents on C#, and could bring it all down.

With Java, ignoring the fact that it's a crappy language and you'd have to rewrite everything, you'd have to either use a proprietary platform (Sun Java) or a platform that's not well supported everywhere and not as complete as Sun's Java (GNU Java).

So I say go with C++, but probably not wxWidgets.  GTK+ is a good way to go (what I'm learning atm), you'll just need to grab the gtkmm library to use it with C++.  It has ports for pretty much every operating system in common use, so you're good for portability.  Here's the tutorial I'm using:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)

As for an IDE, drop that Visual Studio crap.  Learn to use GNU Emacs.  It'll take a little while, but it's a decision you'll never regret.  *The* ultimate text editor.

---

### Post by vinodis on 2006-06-15
IMHO:
@bieber : get your facts r8 on java. java is about reusability and the library support is awesome. the netbeans ide is great and defnitely java is not crappy as you suggested nor do you have to rewrite anything.

---

### Post by nythrix on 2006-06-15
Here's more details about the system specific code.
- game uses GDI+ right now (no directx, opengl or sdl). it was my choice because it's easy.
- the user interface is pretty simple. just a window and a menu bar.
- i do my drawing offscreen and then throw it all onscreen (kind of doublebuffering) to avoid flicker.
So all I need is rendering to an offscreen bitmap, a timer and a small menu. Which is easier to use regarding these points? GTK+ or wxWidgets?

2 bieber:
What do you mean with chossing between Sun Java or GNU Java? How come they don't work the same way?? How many javas are out there? I'm a bit confused now.

---

### Post by Kimm on 2006-06-15
> 
What do you mean with chossing between Sun Java or GNU Java?


I dont get that statement eighter.
Java is Java, but it so happens that GNU Java is still not complete, so some applications may have trubble running on GNU Java.

Still, the language is still the same and a Java program compiled using Suns compiler will run on GNU Java (if it doesnt use unsupported functions), and the other way around.

GNU Java can run almost anything at the moment.
Azureus runs on both GNU Java and Sun Java!

---

### Post by kunnk on 2006-06-15
In my opinion Java has one really serious advantage when compared to other options in Linux. Java has absolutely best development tools. We have many IDE-s, profilers, testing tools, statical code analysers, GUI builders, libraries for everything, continuous integration tools, application severs, frameworks, you name it! And basically in every tool category you have choice between several free and commercial implementations. This makes Java most productive development platform in Linux, no doubt.

I quite recently read from de Icaza blog that they have now graphical C# debugger and it "almost works". It was pretty funny to read and compare it against Java tools.

---

### Post by snoop on 2006-06-15
[QUOTE=nythrix]Here's more details about the system specific code.
- game uses GDI+ right now (no directx, opengl or sdl). it was my choice because it's easy.
- the user interface is pretty simple. just a window and a menu bar.
- i do my drawing offscreen and then throw it all onscreen (kind of doublebuffering) to avoid flicker.
So all I need is rendering to an offscreen bitmap, a timer and a small menu. Which is easier to use regarding these points? GTK+ or wxWidgets?

2 bieber:
What do you mean with chossing between Sun Java or GNU Java? How come they don't work the same way?? How many javas are out there? I'm a bit confused now.[/QUOTE]

I have never used GDI+, but I dont understand about the offscreen bitmap part. In sdl, there are surfaces, which can be drawn on and then shown. This is in sdl itself and not in the windowing toolkit. So it wouldnt matter if you were using gtk+ or wxwidgets. 

The only thing I have against java is the amount of memory it takes up (ie: azereus).

---

### Post by bieber on 2006-06-15
I was under the impression the two Javas had substantial compatibility issues.  NIce to know they play nice together.

Anywho, if you already have a lot of code written in C++, I'd say going and rewriting it all in Java seems like a pretty silly idea, if you already have a substantial amount done.

---

### Post by KLineD on 2006-06-15
I say go with Java, as kunnk says, it has some of the best open source IDE's out there (Netbeans, Eclipse anyone?) and other development tools. There are plenty of libraries to make your development easier and Sun's implementation is very good at cross plataform compatibility. Because of the licence change, now you can install Sun Java with apt-get so it's very easy to do in Ubuntu.

Also, for all the folks that say Java apps look ugly, [take a look]("http://jroller.com/page/gfx?entry=extreme_gui_makeover_2006_screenshots") at what this guy can do with Java. It's really amazing and of course Romain is an expert in Swing and Java but with a little effort in aesthetics, you could make a really great looking, multiplataform Game with some of the best development tools out there.

---

### Post by bieber on 2006-06-15
While we're at it, does anyone know if Sun is truly making Java free software, or is the extent of "Open Sourcing" Java going to be making it easier to include with GNU/Linux distros?

---

### Post by QMario on 2006-06-15
I don't know about you guys, but after going to that URL, I believe that extreme applications are the way to go. :p

---

### Post by KLineD on 2006-06-15
[QUOTE=bieber]While we're at it, does anyone know if Sun is truly making Java free software, or is the extent of "Open Sourcing" Java going to be making it easier to include with GNU/Linux distros?[/QUOTE]
Schwartz, the new Sun CEO [said that]("http://www.vnunet.com/vnunet/news/2156205/sun-promises-open-source-java") "It's not a question of whether we'll open source Java, the question is how." So it's supposed to go open source at some time. They are just concerned about forking and the Java name, with consumers and developers being confused about products with Java in its name but based in some forked Java project, for example.

[QUOTE=QMario]I don't know about you guys, but after going to that URL, I believe that extreme applications are the way to go.[/QUOTE]
They do look gorgeous... check out [Aerith in that same page]("http://jroller.com/page/gfx?entry=aerith_a_very_cool_swing") for some of the stuff presented in this years JavaOne conference.

---

### Post by nythrix on 2006-06-15
Java it is then. I know I have a bit of rewriting work ahead but there's two facts that counter it.
- I need the devtools helping me not fighting me. Emacs/Vim/gEdit/ may be pretty good text editors (didn't really test anjuta) but using a text editor for developing sounds horrible to me. I used windows' notepad to develop a small chess thing in prolog and it was a kick in the teeth. I've grown alergic to this kind of developing since then.
- I won't be counting the new-delete pairs anymore :D

Thanks to everyone for their tips.

---

### Post by bieber on 2006-06-15
Emacs is far more than a text editor, though.  If it could run on its own, it could easily be classified as an OS.  Supports any editing feature you can want, and you can also build, run, and debug applications from within it, along with countless other things (browsing the web, checking your email, chatting, keeping a diary, you name it, Emacs does it.)

---

### Post by ltmon on 2006-06-15
You'll probably hate Vim or Emacs as well, but but once I got used to Vim I couldn't turn back... It is incredibly productive, and IDE's just get in the way for me these days.

Mind you, it did take me about 2 years of diligent hacking to get used to Vim, so it may not be worth the effort ;)

For a Java IDE your best choices are IntelliJ (I think there's a freeish version), NetBeans or Eclipse.  These are all pretty good in their own way, but different strokes for different folks.

L.

---

### Post by grexk on 2006-06-16
Python :)
Python has bindings in different languages(.net,java,tcl,wxpython,*)

---

### Post by KLineD on 2006-06-16
I hear nothing but good comments about python and I've been trying to get a hang of it, unfortunately I've failed everytime.

---

### Post by xeero on 2006-06-16
[QUOTE=nythrix]Java it is then. I know I have a bit of rewriting work ahead but there's two facts that counter it.
- I need the devtools helping me not fighting me. Emacs/Vim/gEdit/ may be pretty good text editors (didn't really test anjuta) but using a text editor for developing sounds horrible to me. I used windows' notepad to develop a small chess thing in prolog and it was a kick in the teeth. I've grown alergic to this kind of developing since then.
- I won't be counting the new-delete pairs anymore :D

Thanks to everyone for their tips.[/QUOTE]

Since you've decided on Java, I have some recommendations for you:

IDE: Either Eclipse or Netbeans.  Eclipse has tremendous support (and plugins) and is used widely in industry.  You can also configure it to use any external editor (e.g., vim, emacs, etc).  Netbeans looks good too, and has a gui editor called Matisse that is as good as using Visual Studio.  Eclipse also has a gui editor, but it requires additional libraries to use.  

TEST: Use JUnit to do your unit testing.  JUnit easily integrates with the IDEs.  

If you have the time to learn and do extra good stuff...

GUI: Check out JGoodies ([http://www.jgoodies.com/](http://www.jgoodies.com/)) for a clean, consistent gui on different platforms.  Just use JGoodies classes in building your guis.  

BUILD: Use Ant or Maven for managing your builds.  I know both can integrate with Eclipse (probably for Netbeans too, but not sure).  Ant may actually integrate more seamlessly in Eclipse, but Maven can be easier to use than Ant.  Maven can also be used within the Eclipse IDE.

---

### Post by KLineD on 2006-06-16
In my experience, Eclipse Visual Editor can be a bit difficult and cumbersome to use. Netbeans GUI builder (Matisse) it's a total joy, very similar to what Visual Studio 2005 has to offer.

You can use both IDEs at the same time, both are powerful enough so they'll reload files modified outside the IDE automagically.

---

### Post by nythrix on 2006-06-17
2 xeero & KLineD: Thanks for those tips. I've already used Eclipse before (winxp) and I must say it's a nice IDE. So I'm off with it already. But I could give a try to Netbeans too. Btw: is it in the repositories? Search for "netbeans" gives no hits.
I found out the rewriting isn't that horrible. In fact, I can copy paste big chunks of code without having to alter a char. I'd be done by now wasn't it for those school exams getting on my way.

---

### Post by LordHunter317 on 2006-06-17
> **bieber]C# using .GNU isn't too terribly bad, but Microsoft holds some key patents on C#, and could bring it all down.[/quote]No, they don't hold any patents on C# or .NET, yet.  They're pending, all early in the process.  None of the ones I've seen them apply for are actually legally valid, either.

> With Java, ignoring the fact that it's a crappy language and you'd have to rewrite everything,You don't have to rewrite everything said:**
>  you'd have to either use a proprietary platform (Sun Java) or a platform that's not well supported everywhere and not as complete as Sun's Java (GNU Java).No, you have to use SUN Java.  GNU's stuff is a total non-starter.

> As for an IDE, drop that Visual Studio crap.Why?  You're far more productive in it for many things then you will be in Emacs.

> Emacs is far more than a text editor, though. If it could run on its own, it could easily be classified as an OS.No, it could not.

[quote=vinodis]get your facts r8 on java. java is about reusability [/quote]First off, please speak proper english.  Second off, it's appalling you'd correct someone and then make a huge factual error.  Java isn't about reusability.

[quote=Kimm]GNU Java can run almost anything at the moment.[/quote]No, it can't run crap.  Almost everything major that runs on it has bugs that only appear when running with classpath and/or compliled with gcj.  It's a total non-starter.

[quote=Kunnk]Java has absolutely best development tools.[/quote]No, it does not.  Many of the tools are of terrible quality or poor design, or both.  Having lots of tools doesn't mean you have good tools.  Quantity and qualitity are not related.

> I quite recently read from de Icaza blog that they have now graphical C# debugger and it "almost works".Visual Studio has a rather awesome one, pay no attention to mono.

[quote=xeero]
BUILD: Use Ant or Maven for managing your builds. I know both can integrate with Eclipse (probably for Netbeans too, but not sure). Ant may actually integrate more seamlessly in Eclipse, but Maven can be easier to use than Ant. Maven can also be used within the Eclipse IDE.[/quote]Do not use Maven unless you're a masochist.  Seriously, that's totally crap software.

---

### Post by KLineD on 2006-06-17
[QUOTE=nythrix]2 xeero & KLineD: Thanks for those tips. I've already used Eclipse before (winxp) and I must say it's a nice IDE. So I'm off with it already. But I could give a try to Netbeans too. Btw: is it in the repositories? Search for "netbeans" gives no hits.
I found out the rewriting isn't that horrible. In fact, I can copy paste big chunks of code without having to alter a char. I'd be done by now wasn't it for those school exams getting on my way.[/QUOTE]

Netbeans is not in the repositories, but you can download it from [www.netbeans.org](www.netbeans.org), be sure to download the .bin with no JDK bundled. To install it, first chmod 755 netbeans.bin (or whatever the name of the download is, to make it executable) and then just execute it. Of course, be sure to have installed sun-jdk from the repos. Netbeans installation is graphical, I always install it to /opt/netbeans but that's a matter of how do you want your files organized. The install even puts a menu entry under "Programming".

---

### Post by bieber on 2006-06-17
[QUOTE=LordHunter317]
You don't have to rewrite everything;
[/QUOTE]

So kindly tell me how one switches a project from C++ to Java without rewriting the code that was written in C++...

---

### Post by kunnk on 2006-06-17
> 
No, it does not.  Many of the tools are of terrible quality or poor design, or both.  Having lots of tools doesn't mean you have good tools.  Quantity and qualitity are not related.


What i have to say, yes it does? Quality and design are usually also better than alternatives offer.

> 
Visual Studio has a rather awesome one, pay no attention to mono.


We are using linux, its ubuntuforums you know. Dont you know that Visual Studio does not run in linux? For me, this is the reason why i dont pay attention to C# and .Net. I just want to develop in linux not in windows.

---

### Post by christhemonkey on 2006-06-17
I would reccomend Code:Blocks as an IDE.

Back in the day when i was learning C, was the best thing for me.
Allthough it is still in fairly intense development!


Although my learning C phase lasted about 4 days before i gave up and just went back to my nonprogramming life! :D
Just started python and its great though :)

---

### Post by LordHunter317 on 2006-06-17
[QUOTE=bieber]So kindly tell me how one switches a project from C++ to Java without rewriting the code that was written in C++...[/QUOTE]You could use JNI, for starters.

But that's irrelevant, because how is that question relevant here in the least?  It's not.  He would have to rewrite large portions of it lto port it to Linux: MFC doesn't run on Linux at all and unless you wrote the application to be portable to another graphics toolset in the first place you're going to be rewriting most, if not all, of the application.  And if he had written it to be portable he wouldn't be asking the question here.

[quote=kunnk]What i have to say, yes it does?[/quote]No, you don't have to say anything.  But it's hard to believe from the way your post was written that you weren't trying to associate better with 'we have lots of tools to do the same thing'.  You even called that a good thing.

> Quality and design are usually also better than alternatives offer.Not especially.  IDEA is nice, but Eclipse is absolute trash and Netbeans has only become acceptable recently.

> We are using linux, its ubuntuforums you know.And?  This particular forum is OS-agnostic; more importantly, you can develop (and many do) Linux-targeted .NET applications on Windows.

More importantly, not giving fair mention to the best-of-breed .NET tools (even if they don't run on Linux) is disingenious.  Also, especially given the best-of-breed Java tools all cost money.

---

### Post by nythrix on 2006-06-17
2 LordHunter317:
What's JNI?
And what do you think I should do? Since you wrote java = crap, I suppose you know of some good C/C++ tools (at least half as good as Visual Studio)? I'm completely migrating to Linux so anything that doesn't run in it is pretty useless. As I wrote before, I can learn and use any language without probems as long as I don't have to fight it's devtools. I like Visual Studio and I was looking for something similar.  It's tightly integrated debugger rocks so I don't know what to do with just a plain text editor. Suuure, I can write some lines but once I get the mysterious "What the hell?" error I'm done...

I've laid a nice big line between MFC and the game logic. It wasn't a priority of the project but I had this feeling. Just 3 or 4 methods make up the interface so it's not a problem to cut the rope. Besides it's just a window and a small menu so no big GUI deal anyway.

Java runtime is also more common than wxWidgets, or GTK runtime. I guess windows users wouldn't mind installing it either. After all, we have our cellphones full of Java games so "we've heard of it".

---

### Post by LordHunter317 on 2006-06-17
[QUOTE=nythrix]2 LordHunter317:
What's JNI?[/quote]JNI is the Java Native Interface, which allows Java code to call "native" (C or C++) code.  If you see a method defined with the attribute 'native' in a .java file, it's a stub for a JNI method.

> And what do you think I should do? Since you wrote java = crap,No, that's not what I said.  I said it was "poor", with justification.  Specific features the language should have are missing and design decisions have been repeatedly made that simply have no valid justification (like the continued crippiling of generics).  

That doesn't mean you shouldn't select the language.  I can leverage the same cricticisms about C and C#, and have here before.  But my main reason for that statement was despite the fact that many aspects of Java are poor, I doubted that bieber could explain why.

Java has it uses, and when you have to use it, it's acceptable.

>  What I said was suggesting that tools  I suppose you know of some good C/C++ tools (at least half as good as Visual Studio)?They don't exist.  Anjuta is ok, Kdevelop is sorta-ok.  None of my C/C++ projects in Linux have been large enough scale to warrant a full IDE, so I've rarely used one.  

> 
I've laid a nice big line between MFC and the game logic. It wasn't a priority of the project but I had this feeling. Just 3 or 4 methods make up the interface so it's not a problem to cut the rope. Besides it's just a window and a small menu so no big GUI deal anyway.That doesn't mean your code rewrite won't be substantial.  Substantial is a relative term, after all.

> Java runtime is also more common than wxWidgets, or GTK runtime.My experience is all 3 are equally uncommon.  You'll be bundling and installing whatever you depend on, on Windows.  On Linux, dependencies are dependencies.

---

### Post by nythrix on 2006-06-17
[QUOTE=LordHunter317]JNI is the Java Native Interface, which allows Java code to call "native" (C or C++) code.  If you see a method defined with the attribute 'native' in a .java file, it's a stub for a JNI method.[/QUOTE]
I might use this feature. Does this mean I can write a "wrapper" for the game logic?

[QUOTE=LordHunter317]No, that's not what I said.  I said it was "poor", with justification.  Specific features the language should have are missing and design decisions have been repeatedly made that simply have no valid justification (like the continued crippiling of generics). [/QUOTE]
Right, you didn't said so. I just got that general feeling from your post. I've recently started with Java (as you might have figured out by now) so don't know much about it yet. Generics sound like C++ templates to me.

---

### Post by LordHunter317 on 2006-06-17
[QUOTE=nythrix]I might use this feature. Does this mean I can write a "wrapper" for the game logic?[/quote]You could, but I wouldn't unless it was very complicated and would be difficult to port to Java (by it's nature I guess it's probably neither)  There's a fair chance the time you'll gotten JNI working, you could have just ported the code.


>  Generics sound like C++ templates to me.They are, but are less featureful.  They're essentially compiler-made casts.  There's several articles on the Internet that can explain how they're broken (google on erasure).

---

### Post by mlind on 2006-06-18
[QUOTE=LordHunter317]Also, especially given the best-of-breed Java tools all cost money.[/QUOTE]

nope, infact they're all free software. Eclipse, Apache & Jakarta stuff, tons of other goodies.
Good profilers still cost money though.

I suggest you start with Java. GUI stuff is easy. Swing and SWT are rather easy to learn,
and both encourage separating model from the view which is good practice to begin with.

---

### Post by kunnk on 2006-06-18
> 
No, you don't have to say anything.  But it's hard to believe from the way your post was written that you weren't trying to associate better with 'we have lots of tools to do the same thing'.  You even called that a good thing.


Yes, choice is good thing. For example, if one project is inactive or goes to wrong direction then we can replace it with another project. Even better is if there are several *good* tools to do the same thing, competition is good.

> 
Not especially.  IDEA is nice, but Eclipse is absolute trash and Netbeans has only become acceptable recently.


Calling Eclipse "abolute trash" is really silly thing to do. You obviously just dont know what you are talking.

> 
And?  This particular forum is OS-agnostic; more importantly, you can develop (and many do) Linux-targeted .NET applications on Windows.


First, i just dont want to develop in Windows, i "pay no attention" to this opportunity. Second, .NET applications developed in Windows might not work in Linux anyway, mono is just incomplete in some areas. And finally, this forum is not OS agnostic, this is ubuntu forum and ubuntu is linux not windows.

---

### Post by LordHunter317 on 2006-06-18
> **mlind]nope, infact they're all free software.[/quote]No, they're not.

>  Eclipse,Inferior to IDEA, which isn't free.  Eclipse is absolute crap: it's buggy, they regress core bugs every feature release, they cannot make a stable plugin API for the life of them, the UI is inconsistent beyond belief, the UI wastes space beyond belief, it leaks memory like a sieve, it's CVS code is fundamentally designed wrong and broken at several levels, etc.  I could go on all day.

> Apache & Jakarta stuff,Almost universally crap.  Gerimino is a joke.  Tomcat is an abortion compared to every other Servlet container out there, both free and commerical.  Most of Jakarta is terrible, virtually all of the commons stuff is bad or is good surrounded with enough bad to make it not worthwhile.  And like all Apache projects, the developers know when it's crap, yet steadfastely refuse to actually fix it in a timely or sane fashion.  Still waiting on the Apache HTTP server config to get fixed...

Good stuff from the Apache group?  Well we have hrm, ant.  Ant is pretty nice.  But being better than make isn't hard, mind you.  And ant still has plenty of braindamage said:**
> Yes, choice is good thing.No, it might be a good thing.  Choice isn't universally a good thing and for many things, it's a bad thing.  For example, there are tons of J2EE containers.  But in practice, choice among them is only relevant to a few of them: Sun's, BEA's, Oracle's and IBM's.  Anything else is a joke.  You might be able to sneak away with say, Jetty, if you only need Servlet containment and nothing else, for example.  But by and large, serious development will only be deployed on one of those four (really only three). 

[edit]Forgot Oracle because I'm dumb in the mornings.

Same goes for Web frameworks.  Having lots of choices here is bad because most of them are universally terrible.  There's only a few sane choices, so the presence of lots of choice has made making the right decision harder. 

> For example, if one project is inactive or goes to wrong direction then we can replace it with another project.This is a non-sequitur; the presence of existing choice doesn't let you do this.  This doesn't make sense.

>  Even better is if there are several *good* tools to do the same thing, competition is good.But there rarely is.  And more importantly, the good things almost universally cost cash.

> Calling Eclipse "abolute trash" is really silly thing to do. You obviously just dont know what you are talkingYes, I do.  I've developed and done configuration managment on several Java projects weighing it at between 6 and 7-figure codebases where the developers are using Eclipse.  I could write a white paper on the design flaws in it's CVS codebase alone.  They regress every release without fail.  Their plugin architecture is utter crap, yet it's their single biggest selling point.  The ANT Builder is still broken.  The new web development extensions are utter and complete trash: designed  wrong, implemented wrong, and just plain useless.  Their visual design tools are incredibly inferior to everyone else's, they were too busy sacrificing to the god of enterprise development (UML baby!)  to realize they were making bad tools.  Let's not talk about the debugger, which usually pulls down Eclipse switching perspectives before your code breakpoints.  Or the lack of any sane management tools for J2EE containers except in commercial plugins.

No, I do know what I'm talking about.  I know what I'm talking about probably more intimately than most because I'm the guy who has to make this shit work for all the coders.  So I'm the one who has to solve the problems or say, "It can't be done."  I have plenty of experience at working around eclipse braindamage, of which there is a nearly infinite quantity of.  Don't tell me I don't know what I'm talking about.

>  Second, .NET applications developed in Windows might not work in Linux anyway, mono is just incomplete in some areas.And?  Non-sequitur, this isn't relevant.  One developing an application in Windows that would target linux would presumably know what the limitations of Mono are.  If they're not, they're incompetent and probably not really worth worrying about.

>  And finally, this forum is not OS agnostic, this is ubuntu forum and ubuntu is linux not windows.No, you're wrong. Please read the forum description, which I've provided here for you:> 
This forum is for all programming questions.
**The questions do not have to be directly related to Ubuntu** and any language is allowed. (emphasis mine).  Windows questions are perfectly legal here.

---

### Post by xeero on 2006-06-18
>  Java runtime is also more common than wxWidgets, or GTK runtime. 

> My experience is all 3 are equally uncommon.  You'll be bundling and installing whatever you depend on, on Windows.  On Linux, dependencies are dependencies.

I have a couple questions: 
Do the C++ GUI libraries have something like Java's DefaultMutableTreeNode JTree nodes with support for drag and drop?  I want to start an app with a tree interface supporting drag and drop and I know that Java has this.  I think Visual Studio supports this too with MFC.  How about wxWidgets and GTK?  

Also, what about C++ support for internationlization?  Available for Visual Studio, wxWidgets and GTK?  

I'm also concerned about finding support for wxWidgets and GTK.. any experience with getting help on specific tasks with these libraries?

---

### Post by xeero on 2006-06-18
i thought you're supposed to be able to delete posts...

---

### Post by LordHunter317 on 2006-06-18
[QUOTE=xeero]I have a couple questions: 
Do the C++ GUI libraries have something like Java's DefaultMutableTreeNode JTree nodes with support for drag and drop?[/quote]GTK+ does and I'm pretty certain Qt does.  I'm not sure if wxWindows does, but I'm sure it has to in some capacity.

I also know System.Windows.Forms does in .NET.

> Also, what about C++ support for internationlization?  Available for Visual Studio, wxWidgets and GTK?Internationalization support is provided by the C++ Standard and is reasonably conformant on Windows and Linux.  There's a few issues though:[list][*]No facility is provided for message localization, so you'll have to use GNU gettext or similar for localized messages.  There's a mesage class provided by the standard, but it's woefully inadequately defined, at present.  I believe the next round of standardization will address this.[*]You cannot pass wchar_t to iostream classes, meaning filenames with special characters may have to be handled in an OS-specfic manner.[*]i18n in C++ is relatively complicated to grasp, you'll need to do some reading.  It's a part of the STL not commonly taught.[/list]

> I'm also concerned about finding support for wxWidgets and GTK.. any experience with getting help on specific tasks with these libraries?
Tons of places to ask, they're both very common.

---

### Post by mlind on 2006-06-18
[QUOTE=LordHunter317]....[/QUOTE]

lol man, you obviously don't even know what you're talking about. It seems that you
just like to troll without any good points or proper knowledge.

---

### Post by LordHunter317 on 2006-06-18
[QUOTE=mlind]lol man, you obviously don't even know what you're talking about. It seems that you
just like to troll without any good points or proper knowledge.[/QUOTE]Oh really? Then perhaps you can justify these decisions made by the Eclipse project:[list][*]Lack of support for SSL in the CVS plugin when it was initially coded.[*]No mechanism was provided within the exported plugin classes to be able to add new connection methods for CVS.  This means that support for things like the extra methods supported by CVSNT on Windows cannot be supported by Eclipse[*]Lack of support for CVSNT in the first place; it's a popular CVS alternative even on UNIX and has several features worth supporting.[*]The fact the CVS plugin keeps extra state that's unnecessary (CVS can tell you what it wants to know) and the forces you to recheck out the project if it gets corrupted (because it'll no longer correctly synch the repository)[*]No support for local .project files: either I don't check it in and have to copy it in manually, or I check in one copy and everyone's stuck with it.  This is a royal PITA when making/testing changes to project structure or build.[/list]That's just a few items. I know what I'm talking about.  You've on the other hand, failed to list **even one** good thing about Eclipse, whereas I can enumerate hosts of both bad and good things.

---

### Post by mlind on 2006-06-18
> **LordHunter317]Oh really? Then perhaps you can justify these decisions made by the Eclipse project:[list][*]Lack of support for SSL in the CVS plugin when it was initially coded.[*]No mechanism was provided within the exported plugin classes to be able to add new connection methods for CVS.  This means that support for things like the extra methods supported by CVSNT on Windows cannot be supported by Eclipse[*]Lack of support for CVSNT in the first place said:**
> The fact the CVS plugin keeps extra state that's unnecessary (CVS can tell you what it wants to know) and the forces you to recheck out the project if it gets corrupted (because it'll no longer correctly synch the repository)[*]No support for local .project files: either I don't check it in and have to copy it in manually, or I check in one copy and everyone's stuck with it.  This is a royal PITA when making/testing changes to project structure or build.[/list]That's just a few items. I know what I'm talking about.  You've on the other hand, failed to list **even one** good thing about Eclipse, whereas I can enumerate hosts of both bad and good things.


Personally I think Eclipse IDE is one of the best things opensource community,
(well IBM, but license is open) has ever produced. I've used it on production use
almost 2 years now. I was using JBuilder and IntelliJ IDEA before that, and briefly
tried NetBeans too.

Features you seem to miss are most related to CVS which I haven't used in 4
years. SVN capabilities offered by Subclipse plugin on the other had are very mature
and stable. SSL support is there too.

If I'd need to compare Eclipse for other similar IDEs, I'd say it has superior
usability, offers great editors with all sort from basic interface extracting to
complex refactoring processes. Plugin framework is best I've seen too.

local .project files are there, and strogly supported. Just put .project file on
version control and you retain all settings on CVS/SVN checkout.

I don't think you've had enough experience with eclipse, but I suggest to try it out
more. For beginners it can be very confusing with all features offered, but you
don't really need to customize anything to get you project up and running.
GUI could be more intuitive, but once you get used to shortcut keys, you can't
switch to other IDE's any more.

There are just pointers, but there's so many good features that improve
productivity that you don't see until you don't have 'em. Good debugging
mode being one of them.

Trust me, I developed 3 years using just JBuilder, year with IDEA and now staying
with Eclipse permanently. So *I know* what I'm talking about.

Your comments about Apache stuff were just funny.

---

### Post by LordHunter317 on 2006-06-18
[QUOTE=mlind]Features you seem to miss are most related to CVS which I haven't used in 4
years.[/quote]No, I can cover lots more.  The UI is a textbook example in how to not design things.  It's impossible to specify where the tabs are actually located, for example.  The tab bar below the editor windows should go at the bottom, instead of the top, or be configurable.  It's not.  Oops.

The whole perspectives idea is nifty, but tends to cause Eclipse to ballon resources in a bad way (frequently hitting heap or stack limits causing its death).  A way to always force the previous perspective closed would be nice.   A way to place the perspective bar in any arbitrary location would be nice too.

Dialogs are inconsistent.  The 'Create Project' from  CVS dialog  simply opens the same dialog again after doing the checkout, whoops.  That's a major UI problem there in and of itself.

The web tools are useless.  They require you to use xdoclet, but make external ant calls (including a process spawn) to process xdoclet.  This is completely and totally unnecessary.  Far more difficult to forgive is the fact that this will be trigged if you save the document whenever you have autobuild turned on.  So you can either give up compile-as-you-go or watch your system crawl as Eclipse spawns external stuff everytime you hit Ctrl-S.

Unforgivable is the fact there's no way to control the paths where the tools expect stuff.  That's just appalling.  Also, there's no way to control any of the J2EE servers sanely: you *must* deploy, there's no way to get it to just spit out a WAR for you.  You can't stop/start them sanely either.

This forces you to use a commerical J2EE plugin for J2EE development.  Good Job Eclipse team.

> If I'd need to compare Eclipse for other similar IDEs, I'd say it has superior
usabilityHow so? I'd love to see an IDE-by-IDE comparions from you.  Eclipse is textbook bad.  To be fair, JBuilder is pretty absymal too, but in different ways.

>  Plugin framework is best I've seen too.No, it's not.  It doesn't have a stable API (they change it every release, including minor releases).  They change what is and isn't exported all the time.  More importantly, they can't decide the best way to do things.  

They're committing by-the-book mistakes on plugin API/ABI.  You must be stable: once something is put out, you don't take it away.  But they do that all the time, usually because they export things they didn't really mean to in the first place.

Also, the plugin API is unnecessarily complicated: I shouldn't have to declare extensions and such that have to be coded in a specific manner anyway.  But redundant declarations is the hallmark of a lot of Java stuff (e.g., web.xml, Struts, Spring).

> local .project files are there, and strogly supported. Just put .project file on
version control and you retain all settings on CVS/SVN checkout.No, you completely misunderstood what I said.  I want the ability to projve .project per-user.  If I put .project in CVS, I lose that ability.  If I don't put it in CVS, then everyone has to copy .project in manually to create the eclipse project (i.e., you loose eclipse checkout support).

It needs to support per-user .project files.  It does not.  Visual Studio 2K5 supports this.

> I don't think you've had enough experience with eclipse, but I suggest to try it out
more.I'm the one enumerating issues here.  All you've you said, is it rocks.  You can't say why it rocks, or what it specifically does to rock, just that it does.

> Trust me, I developed 3 years using just JBuilder, year with IDEA and now staying
with Eclipse permanently. So *I know* what I'm talking about.So?  ***You've failed to EXPLICTLY state what's bad about htem or what's good about eclipse.***  I OTOH, have managed to list multiple objections I've had when I said I have a problem with something.  So no, I don't believe you know what you're talking about until you actually can list things you like or dislike and why it should be done that way.  I've managed to do so, you have not.  So kindly put up or retract.

> Your comments about Apache stuff were just funny.See [http://www.jroller.com/page/fate/20060420](http://www.jroller.com/page/fate/20060420) for why Tomcat is an abortion of a Servlet container.  At this point, you're making it really apparent you don't know what you're talking about.  Searching his blog archives will show you some of hte major mistakes Germino has made, as well as the commons-logging group, to name a few other Apache foundation mistakes.  In the latter case, the commons-logging developers admitted what they had created was crap.  

I'll say that again, for the benefit of everyone: ***The developers themselves admitted to writing bad code.***

---

### Post by mlind on 2006-06-18
[QUOTE=LordHunter317]No, I can cover lots more.  The UI is a textbook example in how to not design things.  It's impossible to specify where the tabs are actually located, for example.  The tab bar below the editor windows should go at the bottom, instead of the top, or be configurable.  It's not.  Oops.
[/QUOTE]

I think it's a matter of personal taste. You should be able to customize pretty
much the view you want. I know v3.2 is expanding this feature even more.

[QUOTE=LordHunter317]
The whole perspectives idea is nifty, but tends to cause Eclipse to ballon resources in a bad way (frequently hitting heap or stack limits causing its death).  A way to always force the previous perspective closed would be nice.   A way to place the perspective bar in any arbitrary location would be nice too.
[/QUOTE]

You basically have run eclipse with larger heap, default is something like 32MB.
With 128, you will perfom quite nicely and with 512 there's no problems opening
several editors while debugging your j2ee app.

You seen to be bothered about Eclipse's UI, which is actually very customizable,
new 3.2 version offers even more features for this.

[QUOTE=LordHunter317]
The web tools are useless.  They require you to use xdoclet, but make external ant calls (including a process spawn) to process xdoclet.  This is completely and totally unnecessary.  Far more difficult to forgive is the fact that this will be trigged if you save the document whenever you have autobuild turned on.  So you can either give up compile-as-you-go or watch your system crawl as Eclipse spawns external stuff everytime you hit Ctrl-S.
[/QUOTE]

WTP ? I don't see any xdoclet dependency here.. Eclipse actually has very smart
incremental compiler which was one of the main benefits I forgot to mention.

[QUOTE=LordHunter317]
Unforgivable is the fact there's no way to control the paths where the tools expect stuff.  That's just appalling.  Also, there's no way to control any of the J2EE servers sanely: you *must* deploy, there's no way to get it to just spit out a WAR for you.  You can't stop/start them sanely either.
[/QUOTE]

Huh ? Are you talking about WTP platform or what? There's plugins for Tomcat
and jetty which allow you to run webapps without deploying, and .war .ear
exporting is available after you install WTP. Or just Sysdeo plugin for Tomcat.

[QUOTE=LordHunter317]
This forces you to use a commerical J2EE plugin for J2EE development.  Good Job Eclipse team.
[/QUOTE]

WTP is free.

[QUOTE=LordHunter317]
How so? I'd love to see an IDE-by-IDE comparions from you.  Eclipse is textbook bad.  To be fair, JBuilder is pretty absymal too, but in different ways.
[/QUOTE]

There's already plenty good reviews written, just google a bit.

[QUOTE=LordHunter317]
No, it's not.  It doesn't have a stable API (they change it every release, including minor releases).  They change what is and isn't exported all the time.  More importantly, they can't decide the best way to do things.  
They're committing by-the-book mistakes on plugin API/ABI.  You must be stable: once something is put out, you don't take it away.  But they do that all the time, usually because they export things they didn't really mean to in the first place.
[/QUOTE]

Actually it's not true. IBM has quite good quality assurance. API's ofcourse change
between major releases, but are frozen on minors. Execptions occurs of course
like in any other delopment cycle too.

[QUOTE=LordHunter317]
No, you completely misunderstood what I said.  I want the ability to projve .project per-user.  If I put .project in CVS, I lose that ability.  If I don't put it in CVS, then everyone has to copy .project in manually to create the eclipse project (i.e., you loose eclipse checkout support).

It needs to support per-user .project files.  It does not.  Visual Studio 2K5 supports this.
[/QUOTE]

.project file usually stores information about project settings and dependencies right? not about how your workspace is setup. You usually want your team
members to have same project template. Good practice is to implement project dependant .jars and resources as another module, and place it under version control. Next time someone does a checkout, project dependant resources are automatically updated and classpaths set correctly.

If you don't place it on CVS then you don't. Checkout will always produce new
.project file. It just stores your project preferences. Just don't put it on version control if want others to have personal .project templates, or after checking it out
delete it.


[QUOTE=LordHunter317]
I'm the one enumerating issues here.  All you've you said, is it rocks.  You can't say why it rocks, or what it specifically does to rock, just that it does.

So?  ***You've failed to EXPLICTLY state what's bad about htem or what's good about eclipse.***  I OTOH, have managed to list multiple objections I've had when I said I have a problem with something.  So no, I don't believe you know what you're talking about until you actually can list things you like or dislike and why it should be done that way.  I've managed to do so, you have not.  So kindly put up or retract.
[/QUOTE]

lol, funny stuff :mrgreen: 
Resourcewise, it makes my workday almost 40% more productive than using any
another editor. I already listed important features why I feel confortable using
Eclipse. Most of the features are related to code generation, navigation, tools,
plugins and views that I've failed to find on other IDE's. Is there any area that
would intrest you particulary ?
 

[QUOTE=LordHunter317]
See [http://www.jroller.com/page/fate/20060420](http://www.jroller.com/page/fate/20060420) for why Tomcat is an abortion of a Servlet container.  At this point, you're making it really apparent you don't know what you're talking about.  Searching his blog archives will show you some of hte major mistakes Germino has made, as well as the commons-logging group, to name a few other Apache foundation mistakes.  In the latter case, the commons-logging developers admitted what they had created was crap.  
[/QUOTE]

:-D If you don't feel comfortable with Tomcat, don't use it. I don't. I prefer Jetty.
or JBossed container. Apache is umberella foundation for different projects, so
I bet there's low quality stuff too. My experiences have been pretty much very positive.
I've used many Apache components on production use at commercial products.

---

### Post by LordHunter317 on 2006-06-18
> **mlind]I think it's a matter of personal taste. You should be able to customize pretty much the view you want.[/quote]But you cannot.  More importantly, given that you cannot, they've made the wrong UI decisions.  I won't argue that full customization would be nice, but in the absence thereof, the Eclipse team has consistently made bad choices.

> You basically have run eclipse with larger heap, default is something like 32MB.No, it's 64 MiB, but it doesn't really matter.

> With 128, you will perfom quite nicely and with 512 there's no problems opening several editors while debugging your j2ee app.But I shouldn't have to set that to begin with: eclipse invokes java.exe for me.  Meaning they should set a sane value.  The fact they're still stupid enough to use the less than appropriate Sun defaults just screams both incompetence and stupidity on their part.  This would be different if eclipse were just a JAR and I invoked java directly.  But it's not, so they should have some value much closer to sanity.  And they do not.  GG guys.

> You seen to be bothered about Eclipse's UI, which is actually very customizable, new 3.2 version offers even more features for this.This is a non-sequitur.  Are you going to show how to resolve my issues?  Or is this your answer, 'Wait to the next version?'  That's not a good answer, especially seeing as some of these problems are fundamental and customization isn't a solution to them (like most of the rampant dialog misdesign and misuse).

> WTP ? I don't see any xdoclet dependency here..Yes, it does have it, if you want it to generate web.xml and the like for you.  The problem isn't that it requires it said:**
> Huh ? Are you talking about WTP platform or what? There's plugins for Tomcat and jetty which allow you to run webapps without deploying, and .war .ear exporting is available after you install WTP.They apparently added right after the beta I was using.  I'll retract that.

> There's already plenty good reviews written, just google a bit.And?  Many of them are wrong or don't go into sufficent technical detail.  This isn't a valid appeal to authortity.  I know what the reviews say, I don't care about them.  I want to know what ***you personally*** think.

> Actually it's not true. IBM has quite good quality assurance. API's ofcourse change between major releases, but are frozen on minors.So why the major changes to what is exported between 3.0 and 3.1?  I know this happened because it broke a plugin I had to add SSL to CVS.  They removed all the hooks.  Why do I have to get new versions of eclipse plugins with almost every .x release?  

> Execptions occurs of course like in any other delopment cycle too.Yet groups like virtually any OS development group manage to not have this problem.

> .project file usually stores information about project settings and dependencies right?It stores other details about project configuration too.  More importantly, if I want to disable building a portion of a tree or tweak builds or such, Eclipse makes this harder than necssary.  On major projects, being able to do this flexiably on a per-developer basis is necessary.   Eclipse makes this difficult (poor ANT integration doesn't help either, which would solve the problem). 

> If you don't place it on CVS then you don't. Checkout will always produce new .project file. It just stores your project preferences. Just don't put it on version control if want others to have personal .project templates, or after checking it out delete it.See, but I need both.  I need to be able to have global build settings for the project, and I need the ability to customize.  Again, other IDEs give me this ability and Eclipse is lacking.

> I already listed important features why I feel confortable using
Eclipse.No, you have not.  You've said it is more usable, which could mean anything.  You've said you like the plugin-architecture but have yet to directly answer my criticisms of it, implying you don't understand how it actually works.  

You've said you liked the refactoring stuff but failed to say how it's superior to say, Visual studios or IntelliJ.  To be fair, most of the refactoring stuff is nice, when it works.  Some of the code generation stuff is good, but the way you customize it is unwiledly (but better than visual studios) but less accessible.  More importantly, code generation should always be mapped to a shortcut so I don't have it happen automatically, but can still generate what I want.  Eclipse doesn't support this for things like comments, which is fustrating.

> :-D If you don't feel comfortable with Tomcat, don't use it. I don't. I prefer Jetty. or JBossed container.That's ironic.  JBoss's servlet container is Tomcat.  This statement is IMHO, a serious blow to your credibility.

>  Apache is umberella foundation for different projects, so
I bet there's low quality stuff too.The major stuff is all universally low quality, save for Ant.

> I've used many Apache components on production use at commercial products.So have I, but that doesn't mean they're not crap.  After all, people deployed entire enterprise infrastructures on NT4 despite all its problems.

---

### Post by mlind on 2006-06-18
> **LordHunter317]
But I shouldn't have to set that to begin with: eclipse invokes java.exe for me.  Meaning they should set a sane value.  The fact they're still stupid enough to use the less than appropriate Sun defaults just screams both incompetence and stupidity on their part.  This would be different if eclipse were just a JAR and I invoked java directly.  But it's not, so they should have some value much closer to sanity.  And they do not.  GG guys.
[/QUOTE]

for _most_ usecases default value is sufficient. You probably know that launching
eclipse using -vmargs you can define heap size. Or just mofidy eclipse.ini.

[QUOTE=LordHunter317]
This is a non-sequitur.  Are you going to show how to resolve my issues?  Or is this your answer, 'Wait to the next version?'  That's not a good answer, especially seeing as some of these problems are fundamental and customization isn't a solution to them (like most of the rampant dialog misdesign and misuse).
[/QUOTE]

I'm not sure about versions prior 3.2, but you can define tab positions for editors,
and views with this version. Would you like to have screenshot about this?
For custom L&F see [http://wiki.eclipse.org/index.php/RCP_Custom_Look_and_Feel](http://wiki.eclipse.org/index.php/RCP_Custom_Look_and_Feel)

[QUOTE=LordHunter317]
Yes, it does have it, if you want it to generate web.xml and the like for you.  The problem isn't that it requires it said:**
> 

I never created one using a wizard so I don't know. I believe xdoclet support is
embedded on platform, so dependency is transparent. I'm actually fan
of xdoclet myself and I use it extensively.

[QUOTE=LordHunter317]
It stores other details about project configuration too.  More importantly, if I want to disable building a portion of a tree or tweak builds or such, Eclipse makes this harder than necssary.  On major projects, being able to do this flexiably on a per-developer basis is necessary.   Eclipse makes this difficult (poor ANT integration doesn't help either, which would solve the problem). 


I agree with ant support, but I write my ant scripts using external editor anyway.
I don't understand your problems with building, I always separate my project
as different modules (as projects in eclipse) so I don't have any problems
with building larger trees. I usually use eclipse only for developing where building
is an external ant/maven process.

[QUOTE=LordHunter317]
No, you have not.  You've said it is more usable, which could mean anything.  You've said you like the plugin-architecture but have yet to directly answer my criticisms of it, implying you don't understand how it actually works.  
[/QUOTE]

Presenting feature rich application is very hard GUI-wise. For beginners it may
be hard to adopt such GUI that current Eclipse offers, but I've grown into it.
I just hate to see you bash it when you don't seem to have too much knowledge
or experinece about using it.

I usually make plugin packs out of necessary plugins and apply them as
extensions depending on the project type/workspace. I find it very nice feature.
Marjor revision changes always break API compatibility, but I've had no problems
maintaining API compatibility of my own plugins.

[QUOTE=LordHunter317]
More importantly, code generation should always be mapped to a shortcut so I don't have it happen automatically, but can still generate what I want.  Eclipse doesn't support this for things like comments, which is fustrating.
[/QUOTE]

Huh ? Alt+Shift+S submenu provides you a small view about code generation
templates. And stuff like writing *main*, then Ctrl+Space will provide you
stub of main method. There are like tons of similar features, just check them out
on manual.

[QUOTE=LordHunter317]
That's ironic.  JBoss's servlet container is Tomcat.  This statement is IMHO, a serious blow to your credibility.[/QUOTE]

I find your statement somewhat offending. Tomcat is default for newer JBoss
versions, but Jetty was used before. Mortbay offers Jetty integration, so I guess
you should check your facts straight.

---

### Post by nythrix on 2006-06-18
And then, a short post happened ;) 
I don't think you're goinna solve anything guys. Let everyone use what he thinks is good and we're all happy...
Netbeans looks good. Doesn't work with Xgl though (blank window). Had to switch back to normal Xorg. Where can I report bugs?

---

### Post by mlind on 2006-06-18
[QUOTE=nythrix]And then, a short post happened ;) 
I don't think you're goinna solve anything guys. Let everyone use what he thinks is good and we're all happy...
Netbeans looks good. Doesn't work with Xgl though (blank window). Had to switch back to normal Xorg. Where can I report bugs?[/QUOTE]

I'm sorry for posting offtopic stuff in your thread. I just felt some remarks were not valid.

---

### Post by KLineD on 2006-06-18
[QUOTE=nythrix]And then, a short post happened ;) 
I don't think you're goinna solve anything guys. Let everyone use what he thinks is good and we're all happy...
Netbeans looks good. Doesn't work with Xgl though (blank window). Had to switch back to normal Xorg. Where can I report bugs?[/QUOTE]

This happened to someone else here in the forums, do a search for it. However I don't think you should be running Xgl and coding at the same time, as you know, Xgl is unstable and in the event of a Xgl server crash, you might loose all your unsaved work.

It's just a word of caution.

---

### Post by nythrix on 2006-06-18
[QUOTE=KLineD]This happened to someone else here in the forums, do a search for it. However I don't think you should be running Xgl and coding at the same time, as you know, Xgl is unstable and in the event of a Xgl server crash, you might loose all your unsaved work.

It's just a word of caution.[/QUOTE]

Yes, I know. It's just that Xgl feels so natural I simply forgot about it. Now I'm back to normal.
I'm used to VERY frequent Ctrl+S. Never lost more than a couple of lines :wink:. Programming in Windows does teach you something...

---

### Post by nythrix on 2006-06-18
[QUOTE=mlind]I'm sorry for posting offtopic stuff in your thread. I just felt some remarks were not valid.[/QUOTE]

I don't mind reading. Sounds like a superfast Eclipse learning course to me and you never know when it might be handy.
I'm also testing Netbeans. At the end I will go with the one that suits me and this project.

---

### Post by LordHunter317 on 2006-06-18
[QUOTE=mlind]for _most_ usecases default value is sufficient.[/quote]Not for Eclipse in virtually any use case.

>  You probably know that launching eclipse using -vmargs you can define heap size. Or just mofidy eclipse.ini.***What part of, "I shouldn't have to," is difficult to understand?***
I could understand if it didn't work for some cases or for non-realistic pathological ones, like multi-million line code bases or something similar.  But the defaults don't work for the majority of Eclipse use cases, including every environment I've ever used Eclipse in.  The J2EE container guys seem to manage to do this, so it's inexcusable that Eclipse does not.  There's no valid justification.

> I'm not sure about versions prior 3.2,AFAIK, there's no way to move the tab bars, even in an end-user unfriendly manner, short of writing a UI plugin (which isn't a reasonable solution).  If there is, I could never find a way.  I still can't find a way playing with 3.1 RTM right now.  They're still always on top, even in situations where they shouldn't be so.  Tabs in the left and right sidebars minimize incorrectly:they should have the tabnames turn vertical and slide to the edge, like Visual Studio does it, the bar shouldn't just become the minimize/maximize buttons.  What they do now is useless.  The fact that you have those buttons is a sin too, because they don't work like they do on a real window exactly.  They do different things, so the icon should be different.  This is GUI 101. That's besides the fact that it makes no sense to maximize a tab in a sidebar anyway.  Also, tabs that change their look based on whether they have focus or not is criminal.  The shape changing is just appallingly stupid.

> I never created one using a wizard so I don't know.But I did and I do know what it does.  It spawns an external process running ant to do the work, which is unquestionably the wrong way to go about it.   There's no sane reason to do that beyond the developer in question was too lazy to hook into xdoclet correctly.

> I don't understand your problems with building,I'm a CM guy, building is my life for a lot of projects.  I'm the guy fixing existing project's broken build systems and providing segmentation, QA control in the build process, etc.  Having fine-grained control over my builds is important, and Eclipse goes out of it's way to make that actively difficult.  Mainly, because I want to provide it's development tools to my developers (e.g., the incremental compiler and such) but those tools are inadequate for actual real builds.  Integrating the two is an unnecessary hassle: the former forces the latter to take a certain format and design.  Certain paths have to be fixed, for example, and I have to build certain files in certain places, or Eclipse eats its own lunch.  This makes my life fustrating, to say the least.

> I always separate my project as different modules (as projects in eclipse) so I don't have any problems with building larger trees.That's wonderful, but not always an option I have to take.  More importantly, I shouldn't have to do that to get around build problems due to my IDE's limitations.

> I just hate to see you bash it when you don't seem to have too much knowledge or experinece about using it.So show me where my statements are invalid.  Besides one point (where I was using a beta and admitted they added the feature afterwards) you've failed to do so.  

> Marjor revision changes always break API compatibility, but I've had no problems maintaining API compatibility of my own plugins.Many others seem to have this problem though.

> And stuff like writing *main*, then Ctrl+Space will provide you
stub of main method.I was talking about Javadoc comment templates, which there are no way to control: you either disable the templates (or make them empty), or you always get them when you type /**.  To be fair, VS doesn't provide a way either AFAICT, now that I've used it today.

But I want it to be like other stubs.  Have the ability to hit Ctrl+Space and get the javadoc template as a valid insert where it is valid or be able to hit Ctrl+Space after typing /** and insert it.  I should have the option of not having them generated all the time, and I don't.  That's a glaring UI inconsistency.  But like I said, everyone is guilty of this.

> I find your statement somewhat offending. Tomcat is default for newer JBoss versions, but Jetty was used before.And?  Tomcat is the default container now.  Who cares what it used previously, unless you're going to seriously suggest I use a JBoss version that old (which would bring us back to where we were).

> Mortbay offers Jetty integration, so I guess you should check your facts straight.And?  You didn't suggest that, did you?  You didn't say, JBoss with Jetty replacing tomcat, or a version of JBoss including Jetty instead of Tomcat.  So what did you want me to think?

---

### Post by mlind on 2006-06-18
[QUOTE=LordHunter317]
***What part of, "I shouldn't have to," is difficult to understand?***
[/QUOTE]

The whole idea. Because you really don't need to.

[QUOTE=LordHunter317]
AFAIK, there's no way to move the tab bars, even in an end-user unfriendly manner
[/QUOTE]

Eclipse v3.2
Window -> Preferences -> Appereance -> Override presentation settings
Editor Tab positions -> Bottom
View Tab positions -> Bottom

That wasn't so hard, was it?

[QUOTE=LordHunter317]
But I did and I do know what it does.  It spawns an external process running ant to do the work, which is unquestionably the wrong way to go about it.   There's no sane reason to do that beyond the developer in question was too lazy to hook into xdoclet correctly.
[/QUOTE]

Care to explain why ?
You know that "XDoclet can only be used as part of the build process utilizing ant" ?


[QUOTE=LordHunter317]
I'm a CM guy, building is my life for a lot of projects.  I'm the guy fixing existing project's broken build systems and providing segmentation, QA control in the build process, etc.  Having fine-grained control over my builds is important, and Eclipse goes out of it's way to make that actively difficult.  Mainly, because I want to provide it's development tools to my developers (e.g., the incremental compiler and such) but those tools are inadequate for actual real builds.  Integrating the two is an unnecessary hassle: the former forces the latter to take a certain format and design.  Certain paths have to be fixed, for example, and I have to build certain files in certain places, or Eclipse eats its own lunch.  This makes my life fustrating, to say the least.
[/QUOTE]

Eclipse is not a project management/building tool like ant or maven. Why the heck
would anyone use to manage project builds?


[QUOTE=LordHunter317]
I was talking about Javadoc comment templates, which there are no way to control: you either disable the templates (or make them empty), or you always get them when you type /**.  To be fair, VS doesn't provide a way either AFAICT, now that I've used it today.
[/QUOTE]

Were you or you just made an excuse? But no worries, you can control templates
too just go to Window > Preferences > Java > Code Style > Code Templates.
I think you can't find a missing feature there either.


[QUOTE=LordHunter317]
But I want it to be like other stubs.  Have the ability to hit Ctrl+Space and get the javadoc template as a valid insert where it is valid or be able to hit Ctrl+Space after typing /** and insert it.  I should have the option of not having them generated all the time, and I don't.  That's a glaring UI inconsistency.  But like I said, everyone is guilty of this.
[/QUOTE]

If you then decide to have issues with code templates too, see
Window > Preferences > Java > Editor > Templates. You can even switch them
off! Funny thing about this that you can make code styles a project specific too,
not just global.

[QUOTE=LordHunter317]
And?  Tomcat is the default container now.  Who cares what it used previously, unless you're going to seriously suggest I use a JBoss version that old (which would bring us back to where we were).
[/QUOTE]

You keep amusing me :mrgreen:
I actually never said anything about what servlet container might JBoss use,
I said I don't use Tomcat. I use JBoss as microkernel and embed Jetty on their
container.



 I find you somewhat challenged to find any true meaning about my replies. But that's okay. :D

---

### Post by LordHunter317 on 2006-06-18
[QUOTE=mlind]The whole idea. Because you really don't need to.[/quote]You just said I did previously.  You've agreed that in many situations, Eclipse needs more RAM and that raising the Java heap solves OOM problems with it.  So this statement is contradictory.

> That wasn't so hard, was it?Eclipse ***3.2***  Which isn't final yet, is it?  No.  It's good to know they're fixing this, like I've said several times already.

> You know that "XDoclet can only be used as part of the build process utilizing ant" ?Nope, that's not true.  There's no reason why you can't hook into the Xdoclet the same way ant does, especially given that Eclipse already is hooked into ant at several points.

> Eclipse is not a project management/building tool like ant or maven. Why the heck would anyone use to manage project builds?Because developers have to build software to use it.  That means Eclipse needs to integrate with the build tools people use.  And it does a really shitty job of it.   It expects you to use it's own integrated tools (which have value anyway, especially for developers). 

The point is: I should be able to write ant scripts that Eclipse can run to do full builds and incidental work (resource generation, deployment, etc.)  and still make use of the Eclipse features like the incremental compiler and the like.  But I currently cannot do that.  I can barely use ant from Eclipse at all.

> Were you or you just made an excuse?Yes, I was.  I specfically said comments originally could not be shortcutted.  You have no control when the stubs are generated: it's all or nothing.

> But no worries, you can control templates too just go to Window > Preferences > Java > Code Style > Code Templates. I think you can't find a missing feature there either.***Again, that's not what I'm talking about.***  I can either type /** and get my javadoc template or not.  I can't trivally sometimes get the template and sometimes not, like I can for other generated stubs.  It's not possible, Eclipse does not support it.

> I actually never said anything about what servlet container might JBoss use,***Right, but your response was to a comment about not using Tomcat.***  This is a deflection.

> I said I don't use Tomcat. I use JBoss as microkernel and embed Jetty on their container.No your response was: if you don't want to use Tomcat, use Jetty or JBoss instead.  The latter is a non-sequitur, because it is Tomcat unless you actively change it.  Which you didn't say to do, now did you.

> I find you somewhat challenged to find any true meaning about my replies. But that's okay. :DThat's because, and no offense, your English has been terrible and you refuse to explain yourself at all unless you're challenged repeatedly.

---

