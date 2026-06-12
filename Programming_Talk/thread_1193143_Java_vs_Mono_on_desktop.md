---
title: "Java vs Mono on desktop"
date: 2009-06-21
forum: Programming Talk
---

### Post by dixon on 2009-06-21
Hi,
I was just wondering. Why desktop apps for gnome are written in Mono and there's no default app written in Java? Why is Mono better than Java in desktop enviroment? Or is it just because Novell is pushing mono apps due to pact with MS? I was thinking about contributing to some project, but I can find only interesting mono apps. Is it worth trying MONO? Is it really so much better for the gnome desktop? Why?

---

### Post by aikiwolfie on 2009-06-21
So far as I know Mono isn't actually a programing language like Java. It's a framework of proprietary standards, APIs and libraries that can be used to help build applications. Mono is Novells' version of .NET.

Java is a programing language similar to C, Basic, Javascript, Python or Pascal.

---

### Post by ad_267 on 2009-06-21
> **aikiwolfie said:**
> So far as I know Mono isn't actually a programing language like Java. It's a framework of proprietary standards, APIs and libraries that can be used to help build applications. Mono is Novells' version of .NET.

Java is a programing language similar to C, Basic, Javascript, Python or Pascal.

Java is also a runtime environment, similar to .NET. Mono applications are usually written in C#.

From my experience, Java applications don't integrate well with the Gnome desktop. OpenOffice does ok though. I think a lot of people have C# and .NET skills from working in Windows and find it simpler to write .NET applications in Linux rather than learning another programming language. Mono applications are also much easier to integrate into a Gnome environment.

---

### Post by badactress on 2009-06-21
Although 9 times out of ten, when people say Mono, they mean C# programming for .net using mono, which together is an almost identical set-up to Java.

I think mono is racing ahead because the apps look and feel native to the Gnome desktop whereas Java apps still have little quirks that make them feel slightly alien.

For whatever reason, Mono seems to have the momentum at the moment and is becoming more popular while Java remains a web-based success that never really took off on the desktop despite being more than capable.



> **aikiwolfie said:**
> So far as I know Mono isn't actually a programing language like Java. It's a framework of proprietary standards, APIs and libraries that can be used to help build applications. Mono is Novells' version of .NET.

Java is a programing language similar to C, Basic, Javascript, Python or Pascal.

---

### Post by Habbit on 2009-06-21
Indeed: for GNOME desktop programming, the following things put C#/Mono way ahead of Java:
[LIST]
[*]GTK# bindings allow for native programming, instead of Swing with a GTK+ theme
[*]Language support for events-delegates (signals-slots) and properties
[*]The fact that a quality open source implementation was available before the Java opening (Classpath did not really excel in GUI programming)
[/LIST]

---

### Post by directhex on 2009-06-21
> **dixon said:**
> Hi,
I was just wondering. Why desktop apps for gnome are written in Mono and there's no default app written in Java? Why is Mono better than Java in desktop enviroment? Or is it just because Novell is pushing mono apps due to pact with MS? I was thinking about contributing to some project, but I can find only interesting mono apps. Is it worth trying MONO? Is it really so much better for the gnome desktop? Why?

There are two major reasons. I'm assuming here that C# as a language compared to Java as a language is  not a valid reason (although some would argue heavily in that direction).

Firstly, there's bloat. Because of the design of the core libraries, you pretty much cannot split up Java's core libraries into "useful" and "unlikely" - because there's a real spaghetti approach to interdependencies. As a result, even the simplest "hello world" desktop app requires installing the full class library, which weighs in at about a hundred meg on disk. Mono, conversely, is much more layered - and enough Mono for console "hello world" is about 7 meg. Add a couple of megs for more libraries. For comparison to the 100 meg figure for just Java (zero applications), the space taken on Jaunty for F-Spot, Tomboy, all their documentation (about 10 meg minimum), and enough Mono to run them is 54 meg. Oh, and Mono apps are MUCH less RAM-hungry than Java apps

Secondly, there's P/Invoke. There are lots of great libraries on a GNU/Linux system, and when you design an app, you want to be able to use them, more often than not. Using a C-based library in Java is....... unpleasant. Compare [http://java.sun.com/developer/onlineTraining/Programming/JDCBook/jniexamp.html](http://java.sun.com/developer/onlineTraining/Programming/JDCBook/jniexamp.html) to the way to do it with Mono, at [http://www.mono-project.com/Interop_with_Native_Libraries#Introduction](http://www.mono-project.com/Interop_with_Native_Libraries#Introduction) (yes, those 2 lines are the whole thing, no need to build C bridges and so on as with Java). Imagine doing that 20 or more times in an app, maybe hundreds of times - which would you rather be writing?

Also, don't forget that Mono has been Free Software from day 1 (2002), whereas OpenJDK is a MUCH more recent affair, so any apps which have been in development for a long time would either have needed to be written in non-Free Java, or used a Free framework like Mono.

---

### Post by froggyswamp on 2009-06-21
> **Habbit said:**
> 
[LIST]
[*]GTK# bindings allow for native programming, instead of Swing with a GTK+ theme
[/LIST]
 You are confusing the Java look and feels with actual bindings to GTK+.

> 
Firstly, there's bloat. Because of the design of the core libraries, you pretty much cannot split up Java's core libraries into "useful" and "unlikely" - because there's a real spaghetti approach to interdependencies. As a result, even the simplest "hello world" desktop app requires installing the full class library, which weighs in at about a hundred meg on disk. Mono, conversely, is much more layered - and enough Mono for console "hello world" is about 7 meg. Add a couple of megs for more libraries. For comparison to the 100 meg figure for just Java (zero applications), the space taken on Jaunty for F-Spot, Tomboy, all their documentation (about 10 meg minimum), and enough Mono to run them is 54 meg. Oh, and Mono apps are MUCH less RAM-hungry than Java apps
Firstly this is mostly imagination and lack of knowledge about Java.

> 
"useful" and "unlikely" - because there's a real spaghetti approach to interdependencies.  As a result, even the simplest "hello world" desktop app requires installing the full class library, which weighs in at about a hundred meg on disk.
That was bafflegab, from these vague words you can believe and understand whatever you want. Whatever the author is dreaming about, you can use libraries, you can remove those that you think you won't need. If the person/company who created the GTK+ bindings to Java decided to pull all cruft into one big library it doesn't mean it's impossible to do otherwise.

Also, Mono, doesn't come with a "native" GUI so you have no choice but use bindings to other GUIs. Java, otoh, has Swing (Nimbus L&F) which features true extensibility (native to Java, no hacks) and is 100% pure vector based using no images, among other features.

Thus since Mono doesn't have a "native" GUI and Java does - the author ([directhex]("http://ubuntuforums.org/member.php?u=176650")) keeps dreaming and comparing apples to oranges.

There's also a long history of Java coming to Linux which is too long to give some clue.
Also, not all Linux distros ship Mono, and Fedora, starting with version 12 is planning to not include it into the install CD any longer.

And last but not least: as time went by Sun decided to change its wording about Java, it was a language, a framework, it was a runtime, now they call it "Java Technology", so, as time goes by, you have to be a bit of a lawyer to be sure what exactly Java stands for nowadays.

---

### Post by Habbit on 2009-06-21
> **froggyswamp said:**
> Firstly this is mostly imagination and lack of knowledge about Java.

Oh, is it? Let us check a "barebones" Java installation, for example OpenJDK. What would we pull if we do "apt-get install openjdk-6-jre"?:
[LIST]
[*]openjdk-6-jre: ~0.9 MB
[*]openjdk-6-jre-headless: 74.2 MB
[*]openjdk-6-jre-lib: 8.9 MB
[/LIST]For a total of about 84 MB (and I'm only listing the "important" packages). If we use Sun's java instead, numbers are even worse:
[LIST]
[*]sun-java6-jre: 14.6 MB
[*]sun-java6-bin: 80.4 MB
[/LIST]For a total of about 95 MB. Let's now check Mono, which has a more-finely-packaged class library. First, a "headless", console-only install, that is: "apt-get install mono-runtime":[LIST]
[*]mono-runtime: pulls mono-2.0-runtime and mono-2.0-gac
[*]mono-2.0-runtime: pulls mono-jit and libmono-corlib-2.0-cil
[*]mono-jit: 2.5 MB
[*]libmono-corlib-2.0-cil: 2.7 MB
[*]mono-gac: pulls libmono-security-2.0.cil and libmono-system-2.0-cil
[*]libmono-security-2.0-cil: 0.4 MB
[*]libmono-system-2.0-cil: 4.3 MB
[/LIST]Which rounds up to a nice 10 MB. Now tell me, where's the imagination in those figures?

---

### Post by froggyswamp on 2009-06-21
Read again
> 
Also, Mono, doesn't come with a "native" GUI so you have no choice but use bindings to other GUIs. Java, otoh, has Swing (Nimbus L&F) which features true extensibility (native to Java, no hacks) and is 100% pure vector based using no images, among other features.

Thus since Mono doesn't have a "native" GUI and Java does - the author ([directhex]("http://ubuntuforums.org/member.php?u=176650")) keeps dreaming and comparing apples to oranges.

not to mention other packages.

Pay attention to what I mean by apples and oranges, you don't seem to get it.

---

### Post by Habbit on 2009-06-21
Perhaps if you would explain yourself we would get what you mean. However, in your current messages I find only ranting and no arguments at all. The only point you made is, lo and behold, that Swing is native to Java and Mono has no comparable framework, instead having to use either System.Windows.Forms or Gtk# (among many others). But what about the Java penalty (aka 100-MB-to-run-Hello-World)?

---

### Post by froggyswamp on 2009-06-21
Facts are being discarded or qualified as one fits. I'd like to explain further but it would take too long. But a few examples:
- how many computers that come with C#/Mono preinstalled come with "cli" only installed? They come with bindings to GUI libraries preinstalled, right?
- how much space does the windows C#/Net (they come always together on a user's desktop) occupy?
Compare that with Java. And there you'll say, "wait a bit, C# != Mono != Net", which is what I mean. To prove something people arrange facts the way it fits them best, that's the M$ tactics, an example of this tactics: how they put up the new "get the facts" IE8 propaganda - they claim that CSS2.1 is the standard and then they claim that IE8 is more compliant and if you put facts this way, then yes, IE8 is the most compliant browser in the world.
So if you define that you need "cli" and no GUI/other libraries to do typical development for the pc desktop - good for you - if you like your facts this way. I can easily take your role and prove 10 times that Mono is (much) better than Java, but how much does this have to do with real world pc desktop apps is another issue, nonetheless I got room enough to argue that Mono is better and when you're sick proving my "facts" wrong I'll say "I told you Mono is (much) better and you don't reply cause you admit it!".

---

### Post by Habbit on 2009-06-21
Erm... seriously your writing is a bit convoluted, but still, I dare you to check the size of a "full" Mono installation comprising the following: my 10MB "cli" install, System.Data, System.Web, Gtk#, System.Windows.Forms and any dependencies that might be pulled in by that (i18n, Cairo, SharpZipLib, etc.), then compare it against the 100 MB for the JRE.

---

### Post by froggyswamp on 2009-06-21
I'm really getting tired, I'm using Sun's JDK7 (which is not yet out, it's JRE6+java.nio2 and a few other things) it's JRE has 83.4 MB (not exactly 100mb), it offers me a huge range of important libs - hence I don't normally need to think about external bindings.
It's important for me to know that all those packages are installed when I design my app, I won't have to tell the client "ok, you have Java installed, but please also check that the net libraries and java.nio is installed". I could pull a lot of reasons why I want Java to be a stack, exactly the way it is now.
Which packages have been selected to be part of standard JRE is another issue.

It's also important to notice that you're stressing out the size (although the libs must only once be installed, not for every app). We're talking about the desktop, needless to talk about nowadays standards. If I'd like to push my Java app to the mobile - there's another mobile Java, problem solved. Your worrying about the size of the JRE in 2009 is only valid for selected issues, the overwhelming majority doesn't care, for one look how windows jumped from XP with about 2GB install size to like 16GB in Vista and windows 7. Almost nobody says it's a rampant difference. Mono's big brother - C#+Net occupy more than Sun's JRE does or at least as much.
But you don't like that, you're dragging the discussion to the point that you need the "cli" for desktop development. Oh wait, now you added a few more libraries to the "must have" list for desktop development.
So the desktop is not a place to measure space at such low level, but if you insist, I'd ask you to gather all libraries for Mono that implement all JRE's functionality and then tell me the difference.

---

### Post by Habbit on 2009-06-21
Well, I'm stressing out the size because other poster mentioned it and you told him bluntly that he was an ignorant. I was just rebuking your argument. I could also stress how nicer it is to program in C# compared to Java, with properties, events and generics instead of puny emulations of them nailed in later... The native interface is also orders of magnitude simpler (P/Invoke against JNI), etc. The only language feauture in which I think Java is superior is the new first-class enums, but then C# has true value types that can emulate them at a very low programming cost.

WRT your argument about the ease of having the whole stack installed at once, I've had my own clashes with this. You implicitly acknowledge that even though a stack is initially preferable, the question of what makes it into "the" stack is delicate.

---

### Post by directhex on 2009-06-21
> **froggyswamp said:**
> Facts are being discarded or qualified as one fits. I'd like to explain further but it would take too long. But a few examples:
- how many computers that come with C#/Mono preinstalled come with "cli" only installed? They come with bindings to GUI libraries preinstalled, right?
- how much space does the windows C#/Net (they come always together on a user's desktop) occupy?
Compare that with Java. And there you'll say, "wait a bit, C# != Mono != Net", which is what I mean. To prove something people arrange facts the way it fits them best, that's the M$ tactics, an example of this tactics: how they put up the new "get the facts" IE8 propaganda - they claim that CSS2.1 is the standard and then they claim that IE8 is more compliant and if you put facts this way, then yes, IE8 is the most compliant browser in the world.
So if you define that you need "cli" and no GUI/other libraries to do typical development for the pc desktop - good for you - if you like your facts this way. I can easily take your role and prove 10 times that Mono is (much) better than Java, but how much does this have to do with real world pc desktop apps is another issue, nonetheless I got room enough to argue that Mono is better and when you're sick proving my "facts" wrong I'll say "I told you Mono is (much) better and you don't reply cause you admit it!".

What does any of the above have to do with the original poster's question, of "Why desktop apps for gnome are written in Mono and there's no default app written in Java?"

If anything, it confirms it.

---

### Post by fevans on 2009-06-21
> **ad_267 said:**
> From my experience, Java applications don't integrate well with the Gnome desktop. OpenOffice does ok though.

Its amazing how often people say this. But OpenOffice is NOT written in java. Its C++. Even more amazing, every time I've heard someone attribute OpenOffice to java, it is in defense of java on the desktop, which makes the foible all the more tragic.

But so what if java isn't the 1st choice for desktop development. Its still a valid solution for misc server-side applications.

The same basic common-sense guidelines apply to mono. It happens to be very good at desktop apps, but that doesn't mean its a silver bullet for everything. For example, if I'm doing heavy image-processing then... well, duh, how about C++ or even C.

For me the magic polyglot stack is: mono/swig/ikvm. This lets me implement the code in whatever language is appropriate, but hook them together in a single stack.

---

### Post by froggyswamp on 2009-06-22
> **Habbit said:**
> Well, I'm stressing out the size because other poster mentioned it and you told him bluntly that he was an ignorant.
Exactly, because he arranged his own stack of priorities and "facts" and from there draws his fantasies about small sized C# apps.
But I put it this way and it's also right: my "hello world" GUI Java app takes only about 1KB. Don't believe me? Check the attached file.
Given this now you wanna say that you actually mean only the JRE size, not the size of a Java app any more. To which I reply that on windows XP the size of the .NET stack is almost twice bigger: 195MB vs Java's JRE of 97MB - and nobody's complaining about the .NET's size, right?
But I see you already don't like the idea of the small sized mono stack and taking the course "screw the size", Mono is just better. With such tactics of course you'll prove some day that you're right. But let me put it this way: you're happy with your "cli" library for desktop development? Good for you, those who are in their mind know they need much more bindings and libraries to develop typical desktop apps, and GUI alone isn't enough either, which is why the windows .NET stack is even bigger.

```

Why desktop apps for gnome are written in Mono and there's no default app written in Java?

```
It's something (that among other things) you have to watch in the news, because how Microsoft strikes deals and how Novell became "the Mono company" to develop (through Miguel) and push Mono software into Linux  and how M$ bribes key people is not something I'm allowed to discuss in (this) forum, because of that your "truth" is on your side this time and I'm not gonna argue about companies policies and not comment on why Red Hat is trying to get rid of Mono starting with Fedora 12.

---

### Post by Habbit on 2009-06-22
> **froggyswamp said:**
> (rants about the size of .NET instead of Mono and the misguided actions of the Red Hat developers)
Ok, have your cake and eat it, I don't want to hijack this thread any longer. Java is soooo way better than Mono and that's why it enjoys wide use in the desktop.

PS: what's most ironic is that I'm writing a Swing app - adsvote @ sourceforge

---

### Post by froggyswamp on 2009-06-22
I was just "implying" that both are about the same in terms of "price/quality" and because both are sophisticated technologies there's more than enough ground for anyone to misrepresent the facts in his interests.
Also, it's rather the developers who prefer Java/Mono over C/C++, the users - not so much. The devs want to be able to develop the apps fast and easily, the users want their apps to start up fast, eat least memory and be very responsive. So as a user I don't want any of them.

---

### Post by aikiwolfie on 2009-06-22
> **ad_267 said:**
> Java is also a runtime environment, similar to .NET. Mono applications are usually written in C#.Java isn't just a Run time environment. There's a whole language that goes with it. As you say, Mono applications are written in C#. Java applications are written in Java.

Java applications are compiled to byte code much similar to Python. This allows the Java application to run on any platform with the corresponding Java runtime installation. Just like Python.

Applications written in C#, Mono, .Net or otherwise will normally only run on the OS platform they were compiled for.

---

### Post by Habbit on 2009-06-22
> **aikiwolfie said:**
> Applications written in C#, Mono, .Net or otherwise will normally only run on the OS platform they were compiled for.
Wrong. C# is compiled to another byte-code form just like Java. If a theoretically "universal" application compiled for a virtual machine like the Java JVM or the .NET CLR fails to run in different platforms it's usually because the fault of lazy *** developers: for example hardcoding '\' as a path separator in .NET applications instead of using the plaform-provided System.IO.Path.DirectorySeparator will make your application fail on non-Windows platforms. This can happen both with Java and .NET. Also, using native code (JNI in Java, P/Invoke in the CLR) will usually tie your application to the platform the native libraries you are using were compiled for, though Mono has tricks to be able to use cross-platform native libraries with reasonable portability.

---

### Post by aanderse on 2009-06-22
> **dixon said:**
> Hi,
I was thinking about contributing to some project, but I can find only interesting mono apps.

Maybe you should take a look at Vala as well. Vala has no runtime or additional libraries (over the existing c libraries). All vala code is compiled down to raw c code and the language was designed to leverage c.

Check out the list of "Applications developed in Vala" ([http://live.gnome.org/Vala]("http://live.gnome.org/Vala#head-a2a9eb379001c7c92a6fcf5b84b0f08f8b71f997")) and you might find a project you're interested in.

---

### Post by directhex on 2009-06-22
> **aikiwolfie said:**
> Applications written in C#, Mono, .Net or otherwise will normally only run on the OS platform they were compiled for.

Broadly speaking, that's the real-world result, even though the theory suggests otherwise. Once an app starts to P/Invoke things, or use system-specific libraries like GNOME#, it starts to require actual work to port. Not to say that it's impossible, though - install Smuxi on your Ubuntu desktop, copy-paste to a Vista desktop, and run it unaltered.

---

### Post by aikiwolfie on 2009-06-22
So what you're saying is it doesn't matter what we use. In the real world we're skrewed either way? So it's all stupid then? Awesome! It's all settled. Now lets all go back to fighting with PulsAudio to see if we can get it working the same way twiced in as many days.

---

### Post by howlingmadhowie on 2009-06-22
> **Habbit said:**
> Wrong. C# is compiled to another byte-code form just like Java. If a theoretically "universal" application compiled for a virtual machine like the Java JVM or the .NET CLR fails to run in different platforms it's usually because the fault of lazy *** developers: for example hardcoding '\' as a path separator in .NET applications instead of using the plaform-provided System.IO.Path.DirectorySeparator will make your application fail on non-Windows platforms. This can happen both with Java and .NET. Also, using native code (JNI in Java, P/Invoke in the CLR) will usually tie your application to the platform the native libraries you are using were compiled for, though Mono has tricks to be able to use cross-platform native libraries with reasonable portability.

no, that won't cause a fail on the jvm. the jvm will automatically catch a bad path separator.

the jvm is actually a really nice virtual machine and has excellent multi-tasking capabilities. it's big problem in my eyes is probably the java language, but who programs in java nowadays when there are groovy, jython and the like?

---

### Post by howlingmadhowie on 2009-06-22
> **Habbit said:**
> Wrong. C# is compiled to another byte-code form just like Java. If a theoretically "universal" application compiled for a virtual machine like the Java JVM or the .NET CLR fails to run in different platforms it's usually because the fault of lazy *** developers: for example hardcoding '\' as a path separator in .NET applications instead of using the plaform-provided System.IO.Path.DirectorySeparator will make your application fail on non-Windows platforms. This can happen both with Java and .NET. Also, using native code (JNI in Java, P/Invoke in the CLR) will usually tie your application to the platform the native libraries you are using were compiled for, though Mono has tricks to be able to use cross-platform native libraries with reasonable portability.

another thing occurs to me. the jvm has it's own graphical capabilities, which greatly reduces the need for external system specific library bindings. what happens in C#? can i write a GUI application and compile it and have it run on every computer with a .NET or Mono runtime? if so, which graphic elements do i use?

---

### Post by directhex on 2009-06-22
> **howlingmadhowie said:**
> another thing occurs to me. the jvm has it's own graphical capabilities, which greatly reduces the need for external system specific library bindings. what happens in C#? can i write a GUI application and compile it and have it run on every computer with a .NET or Mono runtime? if so, which graphic elements do i use?

The ECMA335 spec does not include a GUI - just the System.Console namespace.

System.Windows.Forms is the "standard" way to draw a GUI with Microsoft.NET 1.1+. There's a compatible assembly in Mono. WPF is the "new" way to do it, with Microsoft.NET 3.5+, and there's no equivalent with Mono.

GTK# is the preferred method for Mono apps, and GTK# works on Windows too (as long as you install the GTK#-for-ms.net libs).

---

### Post by Habbit on 2009-06-22
> **howlingmadhowie said:**
> no, that won't cause a fail on the jvm. the jvm will automatically catch a bad path separator.
The JVM will most certainly not do that, but maybe the class libraries will do it, I haven't checked. Have you? It would be nice in most contexts, but I can't find any info on that in the Java docs: it seems to do things similar to .NET, with a java.io.File.separator and java.io.File.pathSeparator instead of System.IO.Path.DirectorySeparatorChar and System.IO.Path.PathSeparator. Providing "magic" behaviour without specifying it in the docs might (or might not) cause a lot of headscratching for developers later on.

> **howlingmadhowie said:**
> another thing occurs to me. the jvm has it's own graphical capabilities, which greatly reduces the need for external system specific library bindings. what happens in C#? can i write a GUI application and compile it and have it run on every computer with a .NET or Mono runtime? if so, which graphic elements do i use?
I'm not sure if this is what you mean: .NET has System.Drawing. In the Windows .NET Framework this basically implemented with GDI+, but Mono replicates it with open source code. By the way, "the jvm" does not have "graphical capabilities" on its own, it most likely uses JNI to call into its own C libraries for speed, just like Mono does with libgdiplus. Unlike the limited support Java provides, direct rendering is not directly supported in Mono, but I think SDL and OpenGL, both of which have C# bindings, are widespread enough as to not have to worry that someone will not have them.

---

### Post by Reiger on 2009-06-22
> **Habbit said:**
> The JVM will most certainly not do that, but maybe the class libraries will do it, I haven't checked. Have you? It would be nice in most contexts, but I can't find any info on that in the Java docs: it seems to do things similar to .NET, with a java.io.File.separator and java.io.File.pathSeparator instead of System.IO.Path.DirectorySeparatorChar and System.IO.Path.PathSeparator. Providing "magic" behaviour without specifying it in the docs might (or might not) cause a lot of headscratching for developers later on.

The JVM *may* do that in the special case of the forward slash. That is to say using C:/test.txt will usually work on a Windows machine. I guess this is because the underlying stack must be able to operate on both file names and file URLs, the latter always use the forward slash (by convention).

---

### Post by howlingmadhowie on 2009-06-22
> **Habbit said:**
> The JVM will most certainly not do that, but maybe the class libraries will do it, I haven't checked. Have you? It would be nice in most contexts, but I can't find any info on that in the Java docs: it seems to do things similar to .NET, with a java.io.File.separator and java.io.File.pathSeparator instead of System.IO.Path.DirectorySeparatorChar and System.IO.Path.PathSeparator. Providing "magic" behaviour without specifying it in the docs might (or might not) cause a lot of headscratching for developers later on.

can't be bothered to check it now (busy at work), but i can remember seeing a hard-coded '\path\to\file' working fine on a jvm running on a unix machine.

> 
I'm not sure if this is what you mean: .NET has System.Drawing. In the Windows .NET Framework this basically implemented with GDI+, but Mono replicates it with open source code. By the way, "the jvm" does not have "graphical capabilities" on its own, it most likely uses JNI to call into its own C libraries for speed, just like Mono does with libgdiplus. Unlike the limited support Java provides, direct rendering is not directly supported in Mono, but I think SDL and OpenGL, both of which have C# bindings, are widespread enough as to not have to worry that someone will not have them.

there are a couple of 3D libraries for the jvm as well. i must admit i have no idea how javax.swing.JFrame (for example) actually works or how it does what it does. the important thing to note is, whatever it needs to do what it does comes with the jre package. you would seem to be saying that this in not the case with Mono.

---

### Post by Habbit on 2009-06-22
> **howlingmadhowie said:**
> there are a couple of 3D libraries for the jvm as well. i must admit i have no idea how javax.swing.JFrame (for example) actually works or how it does what it does. the important thing to note is, whatever it needs to do what it does comes with the jre package. you would seem to be saying that this in not the case with Mono.
Oh, I'm sorry, it seems I misunderstood you. When you said "graphics libraries" I thought you were talking about some graphic-intensive processing or headless image generation. If you are talking about a GUI akin to the Java AWT/Swing that is "native" to the .NET Framework, then it's System.Windows.Forms you're after. However, I recognize the inherent superiority of Swing in this aspect, with its fine layout control, theming et cetera. If only it were written in C# (with properties, events and the like)... Linux Mono developers usually use Gtk# instead because it blends better with GNOME and, while it doesn't come with the framework itself, it's not hard to bundle.

---

### Post by aikiwolfie on 2009-06-23
Java sounds like a far simpler, less time consuming solution to me.

---

### Post by blackxored on 2009-06-23
First, let put things in their place. .Net is a hijack of java, doesn't let anybody full you. 
Java is wider, simpler, and most community-aware than .NET. 
IMHO the main reason of not supplying a default JRE installation is size. Fedora, for example, includes it by default I think, although then it misses OpenOffice.org. 
.NET doesn't have the GUI facilities java has and people are complaining about. With java, you could do almost anything without resorting to a lot of external libraries, what makes me to the next point, java libraries are huge a lot in the internet, free. I won't start a religious war in here, but I have to say that Mono has been recently blamed on ubuntu-dev mailing lists, so there's no clear answer about it. Also check that Mono is not related to Microsoft direcly; and openjdk has a lot of relationships with upstream java. Check sun page.

---

### Post by SKLP on 2009-06-25
> **froggyswamp said:**
> Given this now you wanna say that you actually mean only the JRE size, not the size of a Java app any more. To which I reply that on windows XP the size of the .NET stack is almost twice bigger: 195MB vs Java's JRE of 97MB - and nobody's complaining about the .NET's size, right?The size of .NET is irrelevant for the topic of this thread. The only point would be if someone built a gnome application using mono and then decided they wanted to release a windows version. But it is pretty much a non-issue as it  (.net) is a core framework in Windows and it is not something which the windows user in question would have to install for this particular port. The only thing they would need, besides the app is the GTK# for windows installer which is pretty tiny.

---

### Post by Vadi on 2009-06-25
Vala.

:)

---

### Post by Can+~ on 2009-06-25
> **Habbit said:**
> for example hardcoding '\' as a path separator in .NET applications instead of using the plaform-provided **System.IO.Path.DirectorySeparator** will make yo...

Jesus christ, and I though typing os.sep was excessive.

(this thread has been hijacked beyond recognition)

---

### Post by SKLP on 2009-06-26
> **Can+~ said:**
> Jesus christ, and I though typing os.sep was excessive.

(this thread has been hijacked beyond recognition)
A shorter way would be to first import the namespace ("using System.IO;"), then do something like this:
```
Path.Combine(a, b);
```
instead of a+"/"+b or a+@"\"+b

---

### Post by dixon on 2009-06-27
Thank you for your answers :) 
Regarding the point you guys mentioned about the size of the jre. I don't think it's issue for end users, but it's issue for distributions - they want to fit all needed applications on one installation CD. 
You also mentioned the GTK# bindings as advantage of mono. I developed several swing applications and you're right they look bit alien on linux, but they're cross platform. Currently I'm looking into swt and gnome-java. 
I'm deciding between swt, gnome-java vs mono stuff. I'm java hobbist, but was deciding mono because of his current popularity on linux desktop, but nobody stated any real advantage of mono. 
I'm just java hobbist I do ABAP development for living so I think I won't make any mistake trying to develop some java apps for gnome in my spare time. I wish I could have more spare time :(

---

### Post by dixon on 2009-06-28
Ok, I must admit I forget about one thing - memory management. How does memory management work in mono? Do you have to "guess" the heap size as in Java or is the memory footprint  stretching and shrinking with application needs just like in C/C++ apps?

---

### Post by directhex on 2009-06-28
> **dixon said:**
> Ok, I must admit I forget about one thing - memory management. How does memory management work in mono? Do you have to "guess" the heap size as in Java or is the memory footprint  stretching and shrinking with application needs just like in C/C++ apps?

The latter. There's never a need for -Xmx1024M

---

