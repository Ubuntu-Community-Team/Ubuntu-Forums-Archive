---
title: "The Rise of C#?"
date: 2009-03-13
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-03-13
i keep hearing it all over the forums...why is C# better than java? C# is a great language....etc

i myself am a fan of it

do you think its time we look at it as something more than a MS language?

---

### Post by ajackson on 2009-03-13
It is a language with it's roots in Microsoft, their answer to Java but the also took the, surprising, route of getting an independent standard created for it. So while it's roots are Microsoft, it can also be a viable cross platform language thanks to the Mono implementation.

Anything that helps Windows developers develop for non-Windows systems should, IMHO, be seen as a positive thing to promote applications becoming more available to people who choose not to use Windows.

The battle between C# and Java should prove interesting though I see it becoming another "holy" war (like vi/emacs, etc)

---

### Post by scottuss on 2009-03-13
I find both to be generally terrible. Fair enough C# has it's uses, especially now it's tied in with Gnome in the sense of Tomboy, Banshee and loads of other great Gnome apps. But the Microsoft origins just make me feel a little dubious.

Java is terrible. It's slow, buggy and just looks and feels clunky and old fashioned.

I've had to use a lot of Java (and J2ME) for university stuff and I have to say as soon as I can stop using it the better. I don't usually have it installed on my main machine because I think it's a waste of resources.

The idea behind it was awesome, but I would rather use something like Python for cross platform programming. It's faster, cleaner and feels much nicer. That's just my experience anyway. And Java IDE's (Netbeans and Eclipse) are bloated.

</rant>

---

### Post by Can+~ on 2009-03-13
I dislike both.

For the simple reason that I waste minutes looking for the exact component I need, although you'll have to transverse a f-load of classes, packages and namespaces before getting there.

---

### Post by Simian Man on 2009-03-13
> **scottuss said:**
> 
The idea behind it was awesome, but I would rather use something like Python for cross platform programming. It's faster, cleaner and feels much nicer.


I like Python too, but it is *not* faster than Java or C#.  Java actually has generally good performance.  The main reason for its stigma as being slow (1) historical as the first implementations used bytecode interpretation, and (2) the fact that it uses non-native widgets.  Feeling slow for desktop apps is a lot worse than actually being slow.

I think C# is much better than Java, but I hate the fact that you can't avoid OOP.  Ocaml is my language of choice by the way.

---

### Post by directhex on 2009-03-13
> **scottuss said:**
> The idea behind it was awesome, but I would rather use something like Python for cross platform programming. It's faster, cleaner and feels much nicer.

Python is up to hundreds of times slower than Mono

---

### Post by mcla0203 on 2009-03-13
C# and visual studio hate my MacBook.  Boo.

---

### Post by directhex on 2009-03-13
> **mcla0203 said:**
> C# and visual studio hate my MacBook.  Boo.

[img]http://monodevelop.com/files/thumb/c/c9/800px-MacMonoDevelop.png[/img]

---

### Post by mcla0203 on 2009-03-13
I may have to look into that.  Maybe I'll change my mind...

---

### Post by scottuss on 2009-03-13
> **directhex said:**
> Python is up to hundreds of times slower than Mono

I agree. Mono IS faster than Python. However I think I failed to explain myself correctly. As pointed out in a previous post, I did actually mean desktop application performance, not code execution.

Python is interpreted and thus is obviously going to be slower. However if I create two nearly identical applications, one written in Java with a Swing interface and a Python one with a PyGTK interface, the Swing one will be more "laggy".

Don't get me wrong, I do like Mono for the most part. I was a bit harsh about it before. But my dislike for Java still stands. It's too bloated in so many ways!

---

### Post by Vadi on 2009-03-13
Hm... Vala?

---

### Post by Shin_Gouki2501 on 2009-03-13
> **scottuss said:**
> I find both to be generally terrible. ...

Java is terrible. It's slow, buggy and just looks and feels clunky and old fashioned.


</rant>

J2ME is not J2SE.

As i have been programming with java the last 2 years i can say:
its NOT buggy. Its NOT slow and it doesn't feel clunky OR old fashinoed(what ever that means in the context). If you don't like Swing maybe try SWT?

Here is netbeans runing on mac:
[http://blogs.sun.com/stan/resource/laf/nbdev.png](http://blogs.sun.com/stan/resource/laf/nbdev.png)

It looks nice imo. Other programms in java (as in C#) show that it _ALWAYS_ depends on the implementation if your Application is "sluggish" or not.

See another good example here:
[http://www.pushing-pixels.org/?p=1122](http://www.pushing-pixels.org/?p=1122)

I would say( i have used .NET for my diploa) that C# and Java. Are almost on the same level. They both have generics. while C# has lambda etc.
Java has some less Language features but the JVM is just growing. And the diversity of this will bring some nice progress towards the jvm.

see here:
[http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48](http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48)

and i just thought this thread did mentioned all that stufff..
[http://ubuntuforums.org/showthread.php?t=1084770&page=8](http://ubuntuforums.org/showthread.php?t=1084770&page=8)

regards
Shin Gouki

---

### Post by directhex on 2009-03-13
> **Vadi said:**
> Hm... Vala?

Vala's still very young, but it could show promise as a halfway house between C# and C.

The following Jaunty apps use Vala:
avant-window-navigator
awn-extras-applets
ejecter
gnome-format
gtask

Monodevelop offers a Vala IDE.

---

### Post by Shin_Gouki2501 on 2009-03-13
> **Simian Man said:**
> I like Python too, but it is *not* faster than Java or C#.  Java actually has generally good performance.  The main reason for its stigma as being slow (1) historical as the first implementations used bytecode interpretation, and (2) the fact that it uses non-native widgets.  Feeling slow for desktop apps is a lot worse than actually being slow.

I think C# is much better than Java, but I hate the fact that you can't avoid OOP.  Ocaml is my language of choice by the way.

If you like OCaml , you should try F# or even Scala.

---

### Post by Vadi on 2009-03-13
I have yet to see a Java that looks OK on Linux. Their GTK+ emulation is quite poor, and the Morthif style is plain ugly.

Only good visual implementation I've seen is the GNU Java, but that is still buggy.

It looks great on Windows though...

---

### Post by Simian Man on 2009-03-13
> **scottuss said:**
> Python is interpreted and thus is obviously going to be slower. However if I create two nearly identical applications, one written in Java with a Swing interface and a Python one with a PyGTK interface, the Swing one will be more "laggy".


As I said earlier that has nothing to do with the language implementation and everything to do with the "feel" of the widget library.  Swing feels slow even though it isn't.  It's all about perception.  Luckily C# didn't make that mistake because the GTK# bindings are great!

[QUOTE=Shin_Gouki2501]
If you like OCaml , you should try F# or even Scala. [/QUOTE]
I have heard of F# and, while it sounds good, it hasn't been standardized by anyone yet, so I haven't really got into it.  Scala I haven't heard of, I will look into it thanks :).

---

### Post by scottuss on 2009-03-13
> **Simian Man said:**
> As I said earlier that has nothing to do with the language implementation and everything to do with the "feel" of the widget library.  Swing feels slow even though it isn't.  It's all about perception.  Luckily C# didn't make that mistake because the GTK# bindings are great!


I have heard of F# and, while it sounds good, it hasn't been standardized by anyone yet, so I haven't really got into it.  Scala I haven't heard of, I will look into it thanks :).

Actually it does have something to do with the language implementation. Compiled VS Interpreted will always bring up discussion about speed! And as I said (and you agree) Swing "feels" (read: is not actually slow) whereas pyGTK "feels" fast. I do understand what you're getting at, and I agree.

---

### Post by Reiger on 2009-03-13
Well the reason that Java looks ugly on Linux is that the underlying _native_ stack *is* ugly. [However if you have the CPU cycles to spare...]("https://substance.dev.java.net/see.html")

---

### Post by jimi_hendrix on 2009-03-13
> **Simian Man said:**
> I have heard of F# and, while it sounds good, it hasn't been standardized by anyone yet, so I haven't really got into it.  Scala I haven't heard of, I will look into it thanks :).

actually F# pretty much is ocaml on the .Net framework

even MS admits it

however there is the preprocessor command #light which changes the syntax away from ocaml a little...but it is still very similar

#light is commonly used

---

### Post by Simian Man on 2009-03-13
> **scottuss said:**
> Actually it does have something to do with the language implementation. Compiled VS Interpreted will always bring up discussion about speed! And as I said (and you agree) Swing "feels" (read: is not actually slow) whereas pyGTK "feels" fast. I do understand what you're getting at, and I agree.

My point was you shouldn't judge Java (or C# by extension) based on the crappy Swing library.  We both agree that Swing makes for slow-feeling, ugly desktop applications.  There are better alternatives like SWT which somebody mentioned.

Python is great, but its performance is not even close to JIT languages like Java or C# and saying that it is faster based on Swing's suckage is silly.

---

### Post by bobmatino17 on 2009-03-13
C++ better than both.

---

### Post by Vadi on 2009-03-13
> **Reiger said:**
> Well the reason that Java looks ugly on Linux is that the underlying _native_ stack *is* ugly. [However if you have the CPU cycles to spare...]("https://substance.dev.java.net/see.html")

I don't care what the stack is, but I do care that java apps are looking quite horrible with my nice theme. 

Also your link only shows some pre-made skins for the thing, nothing about uhh actually using what the user has already chosen. And the demo fails to run after downloading.

At least GTK# does this with zero tinkering ;)

---

### Post by slavik on 2009-03-13
Java - WebLogic, WebSphere, JBoss, Tomcat
C# - ???

---

### Post by arrancaru on 2009-03-13
C# is newer so in theory it should be better than Java. Besides, C# is getting better because IronPython team ideas.

---

### Post by directhex on 2009-03-13
> **bobmatino17 said:**
> C++ better than both.

Faster? Probably. Ease & speed of development? No chance

---

### Post by jimi_hendrix on 2009-03-13
> **bobmatino17 said:**
> C++ better than both.

if you, like me, enjoy challenges

---

### Post by Sinkingships7 on 2009-03-13
> **directhex said:**
> faster? Probably. Ease & speed of development? No chance

+1

---

### Post by Reiger on 2009-03-13
> **Vadi said:**
> I don't care what the stack is, but I do care that java apps are looking quite horrible with my nice theme. 

Also your link only shows some pre-made skins for the thing, nothing about uhh actually using what the user has already chosen. And the demo fails to run after downloading.

At least GTK# does this with zero tinkering ;)

No, I don't think you understood what I meant. Substance is a LAF library. Call it a theme for Java if you will. GTK is a widget toolkit, substance happens to add a couple of widgets to the default Swing library but at the core it is something entirely different from GTK: it isn't about widgets, it is a highly dynamic theme 'engine'. What you see there is actually 99% Swing with the prettify-me-layer of Substance.

In actual fact that is little different from how the IMO not-so-pretty GTK library gets turned into a quite-slick-looking piece of kit on your Ubuntu machine: the Ubuntu developers wrote their own theme for it. (Read: wrote their own substance for it.) Of course there will be more to that than I know or write, but to me it seems to boil down to the fact that Swing may look ugly on Ubuntu is that you don't have a proper theme installed to go with it. (By comparison Swing doesn't look as bad on a Windows box which has a rather more blue-ish appearance to begin with.)

In other words: substance (and those skins are just part of the default package) is a library (in JAR format). You add the library to your classpath, and use a couple of calls to the underlying JVM to tell it to use Substance. The result is what you see in the screenshots.

---

### Post by shadylookin on 2009-03-13
what's even written in c# other than tomboy posted notes?

There's nothing wrong with the syntax that I'm aware of. I just don't really want to learn a language whose future rests in Microsoft's hands if I can somehow manage to get out of it.

---

### Post by Sockerdrickan on 2009-03-13
> **shadylookin said:**
> what's even written in c# other than tomboy posted notes?

There's nothing wrong with the syntax that i'm aware of. I just don't really want to learn a language whose future rests in microsoft's hands if i can somehow manage to get out of it.
+1

---

### Post by Shin_Gouki2501 on 2009-03-13
> **arrancaru said:**
> C# is newer so in theory it should be better than Java. Besides, C# is getting better because IronPython team ideas.

So is Java and the jvm. Clojure, Scala , JRuby,Jython and Groovy proove that.

---

### Post by Vadi on 2009-03-13
Reiger: problem is, that this java substance doesn't seem to have integration with my gtk+ substance. I, as a user, want Java apps to look the same as my other ones - because I've spent time setting up a nice gtk+ enviroment.

---

### Post by Shin_Gouki2501 on 2009-03-13
> **Vadi said:**
> Reiger: problem is, that this java substance doesn't seem to have integration with my gtk+ substance. I, as a user, want Java apps to look the same as my other ones - because I've spent time setting up a nice gtk+ enviroment.

[http://www.ensode.net/java_swing_mustang_screenshots_gtk.html](http://www.ensode.net/java_swing_mustang_screenshots_gtk.html)

like that not pleasing?

---

### Post by Vadi on 2009-03-13
[No it's not]("http://www.ubuntu-pics.de/bild/11005/screenshot_100_539__4T129s.png"), sorry :)

I might be on the extreme of making my desktop seem pleasing to me - but still, there are way more gtk+ skins than the special java ones. Making java use the gtk+ skins perfectly is a much better solution, for me personally.

---

### Post by directhex on 2009-03-13
> **shadylookin said:**
> what's even written in c# other than tomboy posted notes?

 banshee 

 beagle 

 blam

 bless 

 cowbell 

 dfo 

 drapes 

 f-spot 

 gbrainy 

 gfax 

 giver 

 gnome-do 

 gnome-rdp 

 gnome-subtitles 

 graphmonkey 

 gshare 

 gtwitter 

 hipo 

 last-exit 

 lat 

 monodevelop 

 muine 

 podsleuth 

 smuxi 

 sysinfo 

 tangerine 

 tasque 

 youtranslate

---

### Post by HotCupOfJava on 2009-03-13
Well its obvious when someone doesn't like Java....its just like anything else: once they've made up their mind no amount of arguing is going to change it.

I rather like Java myself....

---

### Post by doas777 on 2009-03-13
personally I love C#.

one thing i have to give MS, I have never had trouble with client runtimes in .net, whereas I have never found a tester that will run my java apps with the correct minimal version of the JRE. "No, you can't run it with 1.2_14! thats from like '98! What part of 1.5 or higher is so hard to understand?!"

I've also found that porting legacy .net apps up to the newest version is usually a bit more straight forward than converting java 1.4_2 to 1.5 or whatever.

---

### Post by wmcbrine on 2009-03-14
> **Shin_Gouki2501 said:**
> [http://www.ensode.net/java_swing_mustang_screenshots_gtk.html](http://www.ensode.net/java_swing_mustang_screenshots_gtk.html)

like that not pleasing?In those screenshots, it appears that Java's still doing its own, ugly, "hey look at me I'm a Java program" fonts. So, not there yet, in terms of looking native.

---

### Post by Shin_Gouki2501 on 2009-03-14
> **wmcbrine said:**
> In those screenshots, it appears that Java's still doing its own, ugly, "hey look at me I'm a Java program" fonts. So, not there yet, in terms of looking native.

Well the font issue is IMO related to that native underlying stack ( as state here before). I use a mac quite happy and so there is:
[http://blogtrader.net/dcaoyuan/entry/better_look_feel_of_netbeans](http://blogtrader.net/dcaoyuan/entry/better_look_feel_of_netbeans)
A nice option to enable very nice font rendering for Swing Apps on mac.If OSX can do it why wouldn't Linux gfx stack able to do it?

I'm not 100% sure but also i think effords on JDK7 : [http://openjdk.java.net/projects/caciocavallo/](http://openjdk.java.net/projects/caciocavallo/)

Could improve the situation.


I think once Java 7 will be there, it *could* enrich the Linux desktop clearly.

---

### Post by directhex on 2009-03-14
> **Shin_Gouki2501 said:**
> I think once Java 7 will be there, it *could* enrich the Linux desktop clearly.

It could. Nicking sufficient ideas from .NET (such as being able to split the class library so you can run "hello world" with less than a 100 meg footprint) will help to renew interest in Java as a platform for Linux desktop app development - though after 14 years of failing miserably to attract support for that task, it's got its work cut out

---

### Post by myrtle1908 on 2009-03-15
Like Java, C# is just another language (and a poor one at that IMO).  What is important in this discussion is the framework and supporting technologies upon which these languages run.

Please, somebody, show me a half decent application server for the bloated .NET environment.  You cannot.  

Java/JEE has one great advantage over .NET ... that of being the closest thing to multi-platform that you will find.  It is also far more scalable than its poor MS cousin. 

The single advantage that I have found with .NET solutions is that the cost of development is much lower when compared to Java solutions.  It is much easier to find a good .NET developer than a competent JEE developer ... this is my experience.

.NET really is only good for *lite* internal (read intranet) *no-think* apps where you can get the average 16 year old to knock something up and it will work.  It is excellent for prototyping applications.  This is good.  Deployment is a pain however.

There is so much underlying rubbish with the .NET framework that it will never win my vote for mission critical heavy-load applications.

---

