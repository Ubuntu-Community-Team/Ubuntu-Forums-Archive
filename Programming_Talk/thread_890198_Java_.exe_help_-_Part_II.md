---
title: "Java .exe help - Part II"
date: 2008-08-14
forum: Programming Talk
---

### Post by Syndacate on 2008-08-14
Some of you might have seen and/or participated in my last thread about java executables here:
[http://ubuntuforums.org/showthread.php?t=877403](http://ubuntuforums.org/showthread.php?t=877403)

It turns out the biggest conclusion was to package everything as a .jar archive and launch it from there - or just deal the class files and have them use CLI.

NOTE:  Target is end users.

I just set up all the java equipment on a fresh Vista install.  I know everybody has been arguing that .jar files are the best method out there for targeting end users - but I do believe they're simply WRONG.

I installed a bunch of Java stuff on a new Vista install, as I previously stated, and ALL of it came in executable format.  The Java runtime environment/JVM, Netbeans, The JDK (developers tool kit) - every single program/installer that they offered came in executable format.

Furthermore, if you go into the bin folder, that you add to the path variable, both the actual java virtual machine, aka. "java" and the java compiler "javac" are BOTH executables in .exe format.

I think all of this proves that Sun intends/intended both java installs and java applications to be distributed in executable format, therefore, I figure it's the best way to release applications to end users using XP/Vista.

So I ask, how does Sun do it?  It's obvious they use installers for the runtime environments, but the installer just places all the applications for the JVM, compiler, and other components in a bin folder - so what do they do, use a C++ launcher, or what?  The programs seem to be operable in and of themselves, it's like they stuffed a bunch of java class files inside of an executable file...any idea how they set this up?

EDIT:
PS:  The reason I don't mention mac and UNIX users, is because with UNIX it's esay to distribute it with a shell script that a Linux end user would have no problem using, or even a simple CLI.  And sense macs only comprise a small portion of computer population, the majority of which don't do anything outside of their art programs, I see no immediate need to target them.

---

### Post by tinny on 2008-08-15
I thought you pretty much had a conclusion to this problem...?

Did you have a read of this thread in the end?

[http://forums.sun.com/thread.jspa?messageID=4357896](http://forums.sun.com/thread.jspa?messageID=4357896)

I thought that it would have helped you.

---

### Post by CptPicard on 2008-08-15
> **Syndacate said:**
> 
I just set up all the java equipment on a fresh Vista install.  I know everybody has been arguing that .jar files are the best method out there for targeting end users - but I do believe they're simply WRONG.

Then, get hacking on some install wizard tools that let you install .jars easily. That's the ticket.

> The Java runtime environment/JVM, Netbeans, The JDK (developers tool kit) - every single program/installer that they offered came in executable format.

Those are some sort of small .exe wrappers, not everything compiled into native in them.

> 
Furthermore, if you go into the bin folder, that you add to the path variable, both the actual java virtual machine, aka. "java" and the java compiler "javac" are BOTH executables in .exe format.

I would be *very* surprised if the JVM came in anything else except native format. Now, think of this... you want to run Java bytecode... and you would have your VM in ... Java bytecode? :confused:


> I think all of this proves that Sun intends/intended both java installs and java applications to be distributed in executable format, 

How does it prove anything? :) the executable jar is very much where they want to go, if you read their docs. Whatever is done probably in the name of ease for some given platform is not proof of long term goal.

You don't need exes... even windows has "shell scripts" that can be used to launch jars even with complex classpaths.

---

### Post by tinny on 2008-08-15
> **CptPicard said:**
> Then, get hacking on some install wizard tools that let you install .jars easily. That's the ticket.

Those are some sort of small .exe wrappers, not everything compiled into native in them.

I would be *very* surprised if the JVM came in anything else except native format. Now, think of this... you want to run Java bytecode... and you would have your VM in ... Java bytecode? :confused:

How does it prove anything? :) the executable jar is very much where they want to go, if you read their docs. Whatever is done probably in the name of ease for some given platform is not proof of long term goal.

You don't need exes... even windows has "shell scripts" that can be used to launch jars even with complex classpaths.

The technically optimal approach is the way of the jar. But if your target user is a noob or someone that simply doesn't care for things technical you need to really think about this. If an exe will work why risk distributing a jar? Your user will probably have no glue as to what a jar is (or "shell script"). Their environment will quite often not have java.exe on the path or even have a Java runtime etc... 

Often you only get one chance to hook that user.

Now that I think about this problem again I really think the OP needs to look at a "proper" Java application installer solution.

Have a look at this
[http://java-source.net/open-source/installer-generators](http://java-source.net/open-source/installer-generators)

---

### Post by CptPicard on 2008-08-15
> **tinny said:**
> 
Now that I think about this problem again I really think the OP needs to look at a "proper" Java application installer solution.


Yes, that is the logical outcome of this hopefully :)

---

### Post by Reiger on 2008-08-15
Either that or just supply the user a launcher/shortcut? *shrugs*

Remember that in order to have whatever the Java application work your user has to have the 'right' version of Java 'marked as default' *or* you have to have some way of calling it.

RE: The thing with Java apps for Windows - these so-called exes are either a symlink/shortcut to your JAR file *or* an EXE wrapper around them. Which AFAIK can be as simple as one C-statement in a main method:
```

exec("java -jar <my jar file>");

```

---

### Post by tinny on 2008-08-15
> **Reiger said:**
> Either that or just supply the user a launcher/shortcut? *shrugs*

Remember that in order to have whatever the Java application work your user has to have the 'right' version of Java 'marked as default' *or* you have to have some way of calling it.

RE: The thing with Java apps for Windows - these so-called exes are either a symlink/shortcut to your JAR file *or* an EXE wrapper around them. Which AFAIK can be as simple as one C-statement in a main method:
```

exec("java -jar <my jar file>");

```

This will work provided they have the prerequisites setup correctly. Java installed, java.exe on the path etc...

A proper java application installer will look after this prerequisite checking and even resolve the prerequisites if need be (install the JRE etc).

---

### Post by Shin_Gouki2501 on 2008-08-15
strange when i deploy my RCP Application i get an exe if i choose windows as target platfrom :P
^^

checkout the rssowl Application in my Signature for further information

---

### Post by Syndacate on 2008-08-15
> **tinny said:**
> I thought you pretty much had a conclusion to this problem...?

Did you have a read of this thread in the end?

[http://forums.sun.com/thread.jspa?messageID=4357896](http://forums.sun.com/thread.jspa?messageID=4357896)

I thought that it would have helped you.

I thought I did too, then I took another look at it and I realized I don't understand half of it.  I have no experience with C, I don't even know what a compiled C file looks like?  Does it compile to a native executable like a C++ file?

> **CptPicard]How does it prove anything? the executable jar is very much where they want to go, if you read their docs. Whatever is done probably in the name of ease for some given platform is not proof of long term goal.

You don't need exes... even windows has "shell scripts" that can be used to launch jars even with complex classpaths. [/quote]

Windows shell scripts depend on the user to have the path variable for the JVM - and most end users don't.  How does it prove it?  It'd be hypocritical for them to say the best way to release to end users is to release it in an executable jar archive - then release all their stuff in executable format - They release all their stuff in executable format.

[quote=tinny]The technically optimal approach is the way of the jar. But **if your target user is a noob or someone that simply doesn't care for things technical you need to really think about this. If an exe will work why risk distributing a jar? Your user will probably have no glue as to what a jar is (or "shell script"). Their environment will quite often not have java.exe on the path or even have a Java runtime etc...**

Often you only get one chance to hook that user.

Now that I think about this problem again I really think the OP needs to look at a "proper" Java application installer solution.

Have a look at this
[http://java-source.net/open-source/installer-generators](http://java-source.net/open-source/installer-generators)[/quote]

Pretty much exactly what I mean (bolded part).

I'm not really looking for an installer - I'm looking for the app to be portable, as in it doesn't need any other files to run, it runs in an of itself, without the need of extra libraries, like Putty or Eclipse.

I'm looking for very simple end user-ability.

As in:
Step 1.  Click download link >> "save as" >> "Desktop"
Step 2.  Double click ______.exe

I could use an installer, but I rather have it stand-alone, due to its nature.

[quote=tinny]This will work provided they have the prerequisites setup correctly. Java installed, java.exe on the path etc...

A proper java application installer will look after this prerequisite checking and even resolve the prerequisites if need be (install the JRE etc). [/quote]

Yeah - the following method relies on them having java in the path variable - and they most likely won't.

[code]exec("java -jar <my jar file>") said:**
> 

[quote=Shin_Gouki2501]strange when i deploy my RCP Application i get an exe if i choose windows as target platfrom :P
^^

checkout the rssowl Application in my Signature for further information

I'll look at it, thanks.

---

### Post by Syndacate on 2008-08-15
> **Shin_Gouki2501 said:**
> strange when i deploy my RCP Application i get an exe if i choose windows as target platfrom :P
^^

checkout the rssowl Application in my Signature for further information

I'm confused...I checked out the site in ur sig - what does RSS feeds have to do with executables?

---

### Post by tinny on 2008-08-15
> **Syndacate said:**
> I thought I did too, then I took another look at it and I realized I don't understand half of it.  I have no experience with C, I don't even know what a compiled C file looks like?  Does it compile to a native executable like a C++ file?



Windows shell scripts depend on the user to have the path variable for the JVM - and most end users don't.  How does it prove it?  It'd be hypocritical for them to say the best way to release to end users is to release it in an executable jar archive - then release all their stuff in executable format - They release all their stuff in executable format.



Pretty much exactly what I mean (bolded part).

I'm not really looking for an installer - I'm looking for the app to be portable, as in it doesn't need any other files to run, it runs in an of itself, without the need of extra libraries, like Putty or Eclipse.

I'm looking for very simple end user-ability.

As in:
Step 1.  Click download link >> "save as" >> "Desktop"
Step 2.  Double click ______.exe

I could use an installer, but I rather have it stand-alone, due to its nature.



Yeah - the following method relies on them having java in the path variable - and they most likely won't.

[code]exec("java -jar <my jar file>");



I'll look at it, thanks.

If this is everything you want then [JSmooth]("http://jsmooth.sourceforge.net/") is your answer. (As answered in your first thread)

You really should just try giving something ago. There are only really a finite number of opinions to be offered. :)

---

### Post by Shin_Gouki2501 on 2008-08-16
> **Syndacate said:**
> I'm confused...I checked out the site in ur sig - what does RSS feeds have to do with executables?

The Applciation itself is an RCP Application. Which means it contains the SAME Application code but while creating a target for platform you get an "EXECUATBLE" for your choosen platform. 

I'm not toally sure about wTF you try to achieve but its simple like the example on the RSS owl site.

(basically this has been told a lot of times but you don'T seem to listen,read or comprehend)
If you have a java Application you have basically 2 options for "executables".

1. Works on all platforms:
Assing the java jar launcher towards the jar.* file extension. so a double klick will do the "magic".

2. Platform specifc
creating platform specific "executable" which simply links to the jar file ( note you have to create diffrent targets for each platform )
Eclipse RCP Applciation help you to do that, although its trivial to do something similar  ( create shell script or exe ) on your own.


I think JSmooth is what  you are looking for, but the point is that you should understand its jsut simple linking to your java binary and how that works for windows or linux , its really not that hard.

sup

---

### Post by CptPicard on 2008-08-16
@OP, I would also like to point out that this "independent exe" method is sort of technically flawed to begin with too... I am not really sure if you want to go in that direction. It may be easy for some application distributors to create these simple .exe wrappers around their Java classes (and even their own JVM!) but they still are doing it just to take the easy way out IMO. Having your system littered with numerous .exes that you are supposed to file-manage yourself is not desireable.

This .exe hack is a particularly ugly one if you're distributing the entire JVM with it. It really is the fault of Windows. If Microsoft wanted to, everyone had a nicely configured environment ready to go. Now, as things stand, people don't, so we might just as well use installers that make sure that they do, so that the "right way" to go about it gets more prevalent.

With huge apps like Eclipse you usually do get an installer that registers the app with Windows so that it can later be properly removed. This should be the way to go IMO in the first place -- it's almost like a step in the direction of Linux package management...

---

### Post by Syndacate on 2008-08-17
> **tinny said:**
> If this is everything you want then [JSmooth]("http://jsmooth.sourceforge.net/") is your answer. (As answered in your first thread)

You really should just try giving something ago. There are only really a finite number of opinions to be offered. :)

Hrm, I didn't see that before, or I saw it and forgot to re-check it out.

That seems to be what I was after - I just dl'ed the source, I'll see how it works out.  Thanks.

[quote=Shin_Gouki2501]The Applciation itself is an RCP Application. Which means it contains the SAME Application code but while creating a target for platform you get an "EXECUATBLE" for your choosen platform.

I'm not toally sure about wTF you try to achieve but its simple like the example on the RSS owl site.

(basically this has been told a lot of times but you don'T seem to listen,read or comprehend)
If you have a java Application you have basically 2 options for "executables".

1. Works on all platforms:
Assing the java jar launcher towards the jar.* file extension. so a double klick will do the "magic".

2. Platform specifc
creating platform specific "executable" which simply links to the jar file ( note you have to create diffrent targets for each platform )
Eclipse RCP Applciation help you to do that, although its trivial to do something similar ( create shell script or exe ) on your own.


I think JSmooth is what you are looking for, but the point is that you should understand its jsut simple linking to your java binary and how that works for windows or linux , its really not that hard.

sup[/quote]

Yeah, it seems JSmooth is what I was looking for.  I'm not concerned releasing to linux because I'm confident people using linux would be able to launch via CLI - and/or have no problems executing a shell script to add it to the binary.

Nevermind though, it seems you kinda missed the point.  Or maybe you got it and are just bad at explaining it.

[quote=CptPicard]@OP, I would also like to point out that this "independent exe" method is sort of technically flawed to begin with too... I am not really sure if you want to go in that direction. It may be easy for some application distributors to create these simple .exe wrappers around their Java classes (and even their own JVM!) but they still are doing it just to take the easy way out IMO. Having your system littered with numerous .exes that you are supposed to file-manage yourself is not desireable.

This .exe hack is a particularly ugly one if you're distributing the entire JVM with it. It really is the fault of Windows. If Microsoft wanted to, everyone had a nicely configured environment ready to go. Now, as things stand, people don't, so we might just as well use installers that make sure that they do, so that the "right way" to go about it gets more prevalent.

With huge apps like Eclipse you usually do get an installer that registers the app with Windows so that it can later be properly removed. This should be the way to go IMO in the first place -- it's almost like a step in the direction of Linux package management...[/quote]

I understand what ur saying, but if it's a very small application, I see no reason to create an installer for it, it makes more sense to go with the exe wrapper.

Eclipse doesn't "install" - at least not if I remember correctly - it launches as an application, in and of itself.  It doesn't depend on library files installed by an installer and referenced to directory in "program files."

Though I do see what you mean by it being a step in the direction of package management - in a way.

You bring up a good point, with the way Microsoft developed its environment, unlike any other.

----

--

----

Thanks all, I do believe JSmooth was what I was after, I hope it works out.  For larger products, as CptPicard stated, an installer is a better method, but if it's a small program, like the one I'm currently dealing with - the compiled classes are 3.7KB (total).  It's just a small applet, it'd be a waste to make an installer for that, no?

Think of it this way:  I do realize that for a huge production, installing it with an installer is the ideal way for windows end users.  I also understand that the windows environment is unlike any other, which creates a pain in the ***.

I'm not sure how far into linux you guys are, but those of you with Windows experience, there's a small application inside "accessories" called "calculator" - If you remove "scientific mode" from the program, it looks like this:
[img]http://www.xp-tips.com/images/standard-calculator.jpg[/img]

So say that didn't exist, but you were contracted to build it.  I just looked it up on my father's comp - it's 112KB - scientific mode and all.  So say scientic mode is 75% of that you're left with a calculator that's roughly 27Kb.  So what do you do?  Do you make an installer for an application that small?  Or is it still a "hack" to wrap it in an executable.  Larger programs written in Java like Azureus make sense to have an installer, but something of this size seems redundant.

I guess what it boils down to is there's no easy way of end user launching unless you use a wrapper like JSmooth, which is considered a hack, include a JVM (which completely eliminates the point of it being platform independent), or launch from CLI.

EDIT:
Or not write it in Java, but write it in C++ or C, that will compile natively.

---

### Post by apoth on 2008-08-17
Seriously, just use a jar file. Everyone goes through this thought process initially, we all come out using jar files in the end.

Give them a JRE install option too if you want.

---

### Post by Shin_Gouki2501 on 2008-08-17
> **Syndacate said:**
> 

Eclipse doesn't "install" - at least not if I remember correctly - it launches as an application, in and of itself.  It doesn't depend on library files installed by an installer and referenced to directory in "program files."


Think of it this way:  I do realize that for a huge production, installing it with an installer is the ideal way for windows end users.  I also understand that the windows environment is unlike any other, which creates a pain in the ***.



I think that pictures it quite well, the "size" is simply irrelevant when deciding the need for an installer. An installation is to point parameters to the program so the user wont have to do it in another way.

why i gave you the link to the rss side was to see that there exist diffrent target version for each platform. And to tell you the (x) time that target managemetn is EASY with RCP while the rest surly not so. And so you have to decide how you do your platfarom managent or use the jar..


soemhow i get the feeling we scarred you to death with executables, butsoemhow it seems also you can't fully explain what you want to do and why..??

---

### Post by CptPicard on 2008-08-17
> **Syndacate said:**
> So say scientic mode is 75% of that you're left with a calculator that's roughly 27Kb.  So what do you do?  Do you make an installer for an application that small?

Tbh, I need to point out that this is something Java is not very good at to begin with. You still need to launch the entire JVM for this 27kb calculator when done in Java. It doesn't matter when you're building a monstrous application that is expected to hog the machine anyway (like Eclipse), but "small tools" in Java are just... unnatural :(

---

### Post by Syndacate on 2008-08-17
> **apoth said:**
> Seriously, just use a jar file. Everyone goes through this thought process initially, we all come out using jar files in the end.

Give them a JRE install option too if you want.

Is that something you put in the header of the JAR file?

[quote=Shin_Gouki2501]I think that pictures it quite well, the "size" is simply irrelevant when deciding the need for an installer. An installation is to point parameters to the program so the user wont have to do it in another way.[/quote]

So you'd use an installer for a 3.7Kb application?

[quote=Shin_Gouki2501]why i gave you the link to the rss side was to see that there exist diffrent target version for each platform. And to tell you the (x) time that target managemetn is EASY with RCP while the rest surly not so. And so you have to decide how you do your platfarom managent or use the jar..[/quote]

Oh, gotcha.  Yeah, I didn't understand why you sent me to that link - but now I do.  My target platform is win I guess b/c A)  That's what most pple use, B)  I can simply release a JAR to a Linux user, as they'd feel safe to use the CLI, and C)  Mac users are too small of a percentage to care about ATM.

[quote=Shin_Gouki2501]soemhow i get the feeling we scarred you to death with executables, butsoemhow it seems also you can't fully explain what you want to do and why..??[/quote]

It's nothing to do with being scarred by executables, it's simply that I know from helping people out with windows, windows end users like executables.  They like the ability to double click.

Hell, I like the ability to double click when I get a *.deb file.  Double clickary is the release to end users.

[quote=CptPicard]Tbh, I need to point out that this is something Java is not very good at to begin with. You still need to launch the entire JVM for this 27kb calculator when done in Java. It doesn't matter when you're building a monstrous application that is expected to hog the machine anyway (like Eclipse), but "small tools" in Java are just... unnatural[/quote]

So you're simply saying that Java is a bad language for small applications, and I should have instead used C++ or something?

---

### Post by CptPicard on 2008-08-17
> **Syndacate said:**
> 
So you're simply saying that Java is a bad language for small applications, and I should have instead used C++ or something?

Well, I suppose you could take it like that :D

---

### Post by tinny on 2008-08-17
> **CptPicard said:**
> Tbh, I need to point out that this is something Java is not very good at to begin with. You still need to launch the entire JVM for this 27kb calculator when done in Java. It doesn't matter when you're building a monstrous application that is expected to hog the machine anyway (like Eclipse), but "small tools" in Java are just... unnatural :(

1+

unnatural, yes.

Java seems to only be elastic in one way :(

---

### Post by CptPicard on 2008-08-17
> **tinny said:**
> 
Java seems to only be elastic in one way :(

Well, excluding embedded Java ofc... but "small desktop apps" or system utils, no. :(

---

### Post by Syndacate on 2008-08-17
> **CptPicard said:**
> Well, excluding embedded Java ofc... but "small desktop apps" or system utils, no. :([quote=CptPicard]Well, I suppose you could take it like that [/quote]

Alright.  It's too bad, Java has some pretty damn convenient methods with the javadocs, too, 'n all.

[quote=tinny]1+

unnatural, yes.

Java seems to only be elastic in one way[/quote]

Which way is that, the way that it's platform independent?

---

### Post by CptPicard on 2008-08-17
> **Syndacate said:**
> 
Which way is that, the way that it's platform independent?

It scales up very nicely, in enterprise back-end systems etc.

---

### Post by tinny on 2008-08-17
> **CptPicard said:**
> It scales up very nicely, in enterprise back-end systems etc.

:)

---

### Post by CptPicard on 2008-08-17
> **tinny said:**
> :)

What are you smiling at... it's not as if I didn't *know* or acknowledge that despite not being a fanboi ;)

(And yes, yes, EJB3 looks so much cleaner than v2...)

---

### Post by Syndacate on 2008-08-18
> **CptPicard said:**
> It scales up very nicely, in enterprise back-end systems etc.

What do you mean by scales?  I never heard the term in reference to programming nor can find any definition about it (referring to programming).

I got no clue what you two are talking about - and I don't use EJB...

[quote=Sun]Enterprise JavaBeans (EJB) technology is the server-side component architecture for Java Platform, Enterprise Edition (Java EE). EJB technology enables rapid and simplified development of distributed, transactional, secure and portable applications based on Java technology.[/quote]

Not quite sure what that means in English, but that doesn't seem to be the aim of the conversation either.

*shrugs*

So basically what it comes down to is use a more native language such as C++ or C for better development, but then u lose the HUGE library of stuff that Java has :-| - talk about a double edged sword :(.

---

### Post by CptPicard on 2008-08-18
> **Syndacate said:**
> What do you mean by scales?

Simply put, a language "scales up" well if it is relatively painless to apply it to writing "big" projects (in comparison to "average" projects. It "scales down" well if it it is also easy to write "small" projects. Java often does not scale down well, because the VM is big etc.

> 
I got no clue what you two are talking about - and I don't use EJB...

And you really don't need to know at this point, but EJB is the Java way of writing humongous enterprise applications. Think having a corporation with multiple sites globally and needing to synchronize your business processes... Java scales up well because EJB makes writing an enterprise back end "relatively easy", plus once you've got that app, you can just add nodes to your corporation's network and you get pretty painless clustering, distributed computing, etc.

---

### Post by Syndacate on 2008-08-19
> **CptPicard said:**
> Simply put, a language "scales up" well if it is relatively painless to apply it to writing "big" projects (in comparison to "average" projects. It "scales down" well if it it is also easy to write "small" projects. Java often does not scale down well, because the VM is big etc.

And you really don't need to know at this point, but EJB is the Java way of writing humongous enterprise applications. Think having a corporation with multiple sites globally and needing to synchronize your business processes... Java scales up well because EJB makes writing an enterprise back end "relatively easy", plus once you've got that app, you can just add nodes to your corporation's network and you get pretty painless clustering, distributed computing, etc.

Ah, thanks for the explanation, makes perfect sense.

So basically whether it scales up and down well is a direct effect of how high (or low) a level the programming language is (Asm vs Python) ?

So I guess this leads me to the question of:
Why does college teach Java for CS1, 2, and 3, (they switch to C++ in CS4), and most projects for later courses are supposed to be written in Java?

I mean it makes sense to start with C++ or Java from a perspective that everything is nice for new programmers, nice, easy to read, blocks of code, but if it's so shitty for small apps, wonder why they teach it..?

---

### Post by CptPicard on 2008-08-19
> **Syndacate said:**
> 
So basically whether it scales up and down well is a direct effect of how high (or low) a level the programming language is (Asm vs Python) ?

Kind of. Not a direct correlation but a good start I suppose.

> 
So I guess this leads me to the question of:
Why does college teach Java for CS1, 2, and 3, (they switch to C++ in CS4), and most projects for later courses are supposed to be written in Java?

The C++ part sounds like a diversion... it's a huge task to learn C++, I find it hard to understand what they believe will be gained by just one course...

> but if it's so shitty for small apps, wonder why they teach it..?

Well... Java IS a fair mainstream language for learners (IMO -- better alternatives would exist)... and the job market is good if you want to look at it like that.

---

### Post by nvteighen on 2008-08-19
> **Syndacate said:**
> 
So basically whether it scales up and down well is a direct effect of how high (or low) a level the programming language is (Asm vs Python) ?


BASIC is a high-level language that scales down, but not up. :)

---

### Post by Syndacate on 2008-08-19
> **CptPicard said:**
> The C++ part sounds like a diversion... it's a huge task to learn C++, I find it hard to understand what they believe will be gained by just one course...

What do you mean?  I thought they switched to C++ because of how similar it is to Java?  If you just took 3 trimesters of Java, how is learning C++ a hard task?

> **CptPicard said:**
> Well... Java IS a fair mainstream language for learners (IMO -- better alternatives would exist)... and the job market is good if you want to look at it like that.

You mean the job market for high level Java programmers?

---

### Post by tinny on 2008-08-19
> **Syndacate said:**
> What do you mean?  I thought they switched to C++ because of how similar it is to Java?  If you just took 3 trimesters of Java, how is learning C++ a hard task?


It is, memory management is one eg.

> **Syndacate said:**
> 
You mean the job market for high level Java programmers?

There are lots of jobs in Java. I think most programming Jobs in the world are Java (well in my area they are)

---

### Post by Syndacate on 2008-08-19
> **tinny said:**
> It is, memory management is one eg.

Yeah, I knew about memory management, but other than that, pointers, and a few other things, they're pretty similar...and of course the fact that Java has a huge library of built in methods that C++ doesn't seem to have :(!!

> **tinny said:**
> There are lots of jobs in Java. I think most programming Jobs in the world are Java (well in my area they are)

Oh, heh, it seems that my school's like the only one that uses Java :-\.

Out of the many mainstream programs people use every day, it seems very few are made in Java, if you look at freshmeat.net - the few that are written in Java, are also written in another language such as C as well.

Like the two main ones only written in Java are azureus and eclipse.  Guess it just seems like it's not that important for mainstream programming, or something.

---

### Post by Lster on 2008-08-19
[QUOTE=Syndacate]Oh, heh, it seems that my school's like the only one that uses Java :-\.[/QUOTE]

Nope! We "learn" Java too. ;)

---

### Post by tinny on 2008-08-19
> **Syndacate said:**
> 
Oh, heh, it seems that my school's like the only one that uses Java :-\.


Most do I think.

> **Syndacate said:**
> 
Like the two main ones only written in Java are azureus and eclipse.  Guess it just seems like it's not that important for mainstream programming, or something.

OpenOffice and Limewire as well. 

You probably use Java more than you think. Ever used applications like internet banking? These enterprise type applications are mostly written in Java (J2EE).

---

### Post by CptPicard on 2008-08-19
> **Syndacate said:**
> Yeah, I knew about memory management, but other than that, pointers, and a few other things, they're pretty similar...

The similarity is superficial... they are similar in the "big picture" -- both are "C-style" static-typed OOP languages, but when you really get down to it, C++ requires a *lot* more knowledge of all kinds of idioms and is much more complicated (I'd say convoluted...)  in the sense how much stuff you have to be aware of under the hood regardless of how superficially higher-level the language looks like.

> Oh, heh, it seems that my school's like the only one that uses Java :-\.

Well, in my school Java was the only required programming language... one semester class and then you could forget about learning languages for the rest of your degree if you were so inclined (there are classes for C and symbolic programming -- Scheme, Prolog, but still isn't a C++ class I think). Worked well for me.

> the few that are written in Java, are also written in another language such as C as well.

Do you actually have an example of this? :)

> Guess it just seems like it's not that important for mainstream programming, or something.

Here you again run up against the fact that Java is not a huge *desktop* programming language. There are loads of Java *libraries* and a lot of interesting server-side stuff is in Java.

---

### Post by Syndacate on 2008-08-19
> **tinny said:**
> Most do I think.



OpenOffice and Limewire as well. 

You probably use Java more than you think. Ever used applications like internet banking? These enterprise type applications are mostly written in Java (J2EE).

OpenOffice was written in C++, I don't know about Limewire, though.

[quote=CptPicard]The similarity is superficial... they are similar in the "big picture" -- both are "C-style" static-typed OOP languages, but when you really get down to it, C++ requires a lot more knowledge of all kinds of idioms and is much more complicated (I'd say convoluted...) in the sense how much stuff you have to be aware of under the hood regardless of how superficially higher-level the language looks like.[/quote]

This is true, Java does handle a lot of stuff for you.

[quote=CptPicard]Well, in my school Java was the only required programming language... one semester class and then you could forget about learning languages for the rest of your degree if you were so inclined (there are classes for C and symbolic programming -- Scheme, Prolog, but still isn't a C++ class I think). Worked well for me.[/quote]

Well I can stop taking CS after CS3 since I'm going for software engineering, and I do believe there's courses pertaining to other languages, it's just the main ones (CS1-3) deal with Java.  Though I plan on taking CS4.  Though most other "after courses" that don't actually teach programming, but there's still further programming projects, they are in Java :-\.  Kinda redundant, I think.

[quote=CptPicard]Do you actually have an example of this? [/quote]

There's examples all over freshmeat.net - Just to name the few that popped up first that are kinda mainstream:
-  TightVNC (Java, C++, C)
-  Berkely DB (Java, C, C++, Python, Perl, Tcl)
-  SDE for Eclipse (Java, Java J2ME, C, C++, C#)
-  Cyberduck (Java, objective C)

Those are just a few I picked up from skipping around - of course it seems that most mainstream apps don't have any Java in 'em at all.  Though I don't know most of the apps that it shows under "show all with Java" - but then again, the OSS community is huge.

[quote=CptPicard]Here you again run up against the fact that Java is not a huge desktop programming language. There are loads of Java libraries and a lot of interesting server-side stuff is in Java.[/quote]

Okay, now that you say that - I guess it's best to just give up on Java in the meantime if trying to concentrate on desktop stuff.  I was never told it wasn't a big desktop programming language.  Guess I'll stay clear of it for now until I see a place where it would come in handy  :-\.  Too bad my school concentrates on it, then.  Makes sense from their perspective of working on server-side stuff - but from my main goals of working on desktop apps it seems counter-productive.

---

### Post by CptPicard on 2008-08-19
> **Syndacate said:**
> 
Okay, now that you say that - I guess it's best to just give up on Java in the meantime if trying to concentrate on desktop stuff.

Then again, nothing stops you from being a trailblazer ;)

IMO there is nothing wrong with the platform per se, even for desktop development, but it is true that Java is more suitable for large apps where the comparative size of the VM is not huge, where the app can assume that the box is dedicated to running a couple of big apps of its kind (try creating a gazillion little Java utils running in background, you run out of resources pretty fast).

For example, I write a large number-crunching analysis toolkit that recently has grown so much that command-line interfaces are getting unwieldy. I am thinking of giving it a GUI front-end, and if I do, it's going to be one of these "get a huge box and splash the workbench to fill the entire screen and work on whatever" Eclipse-type apps. Whatever overhead the GUI + VM bring in comparison to my own algorithms is completely negligible, and I get easy cross-platformness for free, despite the desktop integration perhaps being a bit worse.

---

### Post by tinny on 2008-08-19
Have you thought about downloading [Visual Studio Express]("http://www.microsoft.com/Express/") and porting your Java application too C#? Or [SharpDevelop]("http://sharpdevelop.net/OpenSource/SD/")


> 
Okay, now that you say that - I guess it's best to just give up on Java in the meantime if trying to concentrate on desktop stuff. 

> 
Then again, nothing stops you from being a trailblazer


About 1yr ago I implemented a 20,000 lines of code desktop application in Java. And it went well. (distributed using the installer approach)

How big is your app?

---

### Post by Syndacate on 2008-08-21
> **CptPicard said:**
> Then again, nothing stops you from being a trailblazer ;)

IMO there is nothing wrong with the platform per se, even for desktop development, but it is true that Java is more suitable for large apps where the comparative size of the VM is not huge, where the app can assume that the box is dedicated to running a couple of big apps of its kind (try creating a gazillion little Java utils running in background, you run out of resources pretty fast).

Makes sense to me.  So that's why it works well for programs like Azureus and Eclipse, but not so well for smaller Desktop apps, which is kinda what I'm aiming towards.

> **CptPicard said:**
> For example, I write a large number-crunching analysis toolkit that recently has grown so much that command-line interfaces are getting unwieldy. I am thinking of giving it a GUI front-end, and if I do, it's going to be one of these "get a huge box and splash the workbench to fill the entire screen and work on whatever" Eclipse-type apps. Whatever overhead the GUI + VM bring in comparison to my own algorithms is completely negligible, and I get easy cross-platformness for free, despite the desktop integration perhaps being a bit worse.

That makes sense - mine are usually similar to number crunching apps in terms of structure, but it's not growing like yours are - seems like I'm better off sticking to C++.  But wahhhh you lose the incredibly large java library :( :(.

[quote=tinny]Have you thought about downloading Visual Studio Express and porting your Java application too C#? Or SharpDevelop[/quote]

What's the reasoning behind this?  I'm not sure what C# is better for (opposed to C, C++, and Java)

[quote=tinny]About 1yr ago I implemented a 20,000 lines of code desktop application in Java. And it went well. (distributed using the installer approach)

How big is your app?[/quote]

This is like a couple hundred...

---

### Post by tinny on 2008-08-21
> **Syndacate said:**
> 
What's the reasoning behind this?  I'm not sure what C# is better for (opposed to C, C++, and Java).

If you dont use any of the additional language features that C# provides (just use very basic OOP stuff) then IMO it would be way easier to port your application to C# than for C/C++.

By using [Visual C# Express]("http://www.microsoft.com/express/vcsharp/") you will be able to create that exe that you are after without any sort of hack. (an exe is a perfectly valid assembly for C# applications).

C# is easier than C/C++ (especially if you have some Java skills)

---

### Post by pmasiar on 2008-08-21
> **tinny said:**
> Have you thought about ... porting your Java application too C#? 

But C# is limited to Windows platform? (Yes I know about Mono but it will always be behind - by design)

If needs be, and app needs to scale to cluster, Java/Linux should be better base than C#/Windows IMHO. And Java is GPL. No forced upgrades like VB recently. It's safer without vendor lock-in.

---

### Post by jtuchscherer on 2008-08-21
> **Syndacate said:**
> 

Furthermore, if you go into the bin folder, that you add to the path variable, both the actual java virtual machine, aka. "java" and the java compiler "javac" are BOTH executables in .exe format.


Of course they are in a native format (in windows .exe). In what language do you think the JVM and the compiler are written in. Hint: It is not Java.

---

### Post by tinny on 2008-08-21
> **pmasiar said:**
> But C# is limited to Windows platform? (Yes I know about Mono but it will always be behind - by design)

If needs be, and app needs to scale to cluster, Java/Linux should be better base than C#/Windows IMHO. And Java is GPL. No forced upgrades like VB recently. It's safer without vendor lock-in.

There is quite a bit of history to this thread pmasiar. Have a read though both part 1 and 2 of "Java .exe help"

---

### Post by tinny on 2008-08-22
> **CptPicard said:**
> Well, excluding embedded Java ofc... but "small desktop apps" or system utils, no. :(

(just read this for the second time)

Embedded Java is very very cool to play with. But unfortunately for most embedded applications the micro p's required are just too expensive. :( 

I once did a prototype for a boat monitoring system using an ajile aj-100 chip. Man its a cool chip! But it was about 3 times the cost of a atmel chip that could do the same job in C (ATmega128) (with that price dif it does matter if it takes twice as long to program the embedded app). So we ended up using the ATmega128 :(

The arm7 Jazelle (JVM) chips are about x2 the price from memory.

J2ME works quite well on phones but you run into significant problems when trying to maintain a single code base for multiple models of mobile phones. (The various JVM implementations have some bad bugs)

---

### Post by SeanHodges on 2008-08-22
> **apoth said:**
> Seriously, just use a jar file. Everyone goes through this thought process initially, we all come out using jar files in the end.

Give them a JRE install option too if you want.

So true :)

---

### Post by MarkieB on 2008-08-22
no longer participating in ubuntuforums.org

---

### Post by Syndacate on 2008-08-24
> **tinny said:**
> If you dont use any of the additional language features that C# provides (just use very basic OOP stuff) then IMO it would be way easier to port your application to C# than for C/C++.

By using [Visual C# Express]("http://www.microsoft.com/express/vcsharp/") you will be able to create that exe that you are after without any sort of hack. (an exe is a perfectly valid assembly for C# applications).

C# is easier than C/C++ (especially if you have some Java skills)

Oh, I see, thank you.  This book I'm reading now on C++ is for like, uber beginners, so it's not like I'm pulling much besides basic syntaxing out of it anyways.  Guess I'll look at C# next then, if it can provide both a desktop app type platform with end userabilty..so what's the catch?

[quote=pmasiar]But C# is limited to Windows platform? (Yes I know about Mono but it will always be behind - by design)

If needs be, and app needs to scale to cluster, Java/Linux should be better base than C#/Windows IMHO. And Java is GPL. No forced upgrades like VB recently. It's safer without vendor lock-in.[/quote]

That's a good point.  I could dev in windows though.  I always keep a win install on my computers (regardless of how many distros are on there) just in case I need activeX or a game or something that other OS's simply can't do (ie. C#).

[quote=jtuchscherer]Of course they are in a native format (in windows .exe). In what language do you think the JVM and the compiler are written in. Hint: It is not Java.[/quote]

Somebody told me they were written in C++, but I was more aiming at the point where even the JRE and everything installed is all distributed like that.  Think about it.  Any file a daily windows user uses (app wise) is a .exe o.O.

[quote=tinny](just read this for the second time)

Embedded Java is very very cool to play with. But unfortunately for most embedded applications the micro p's required are just too expensive.

I once did a prototype for a boat monitoring system using an ajile aj-100 chip. Man its a cool chip! But it was about 3 times the cost of a atmel chip that could do the same job in C (ATmega12 (with that price dif it does matter if it takes twice as long to program the embedded app). So we ended up using the ATmega128

The arm7 Jazelle (JVM) chips are about x2 the price from memory.

J2ME works quite well on phones but you run into significant problems when trying to maintain a single code base for multiple models of mobile phones. (The various JVM implementations have some bad bugs) [/quote]

Wow, didn't know that.  I thought a basic JVM woulda processed basic phone apps the same.  Why are the Java chips so expensive?  Because they have to process a higher level language?  (I'm not doing embedded systems, but I'd love to if I ever got the chance).

[quote=SeanHodges]So true[/quote]

Yeayea, I think I got my answer as using JSmooth for writing Java apps like that, but more importantly I've discovered the uselessness of Java as a desktop programming language.  

I thought I needed to learn how to transfer what I've learned into programs that people can use every day.  What I didn't realize was that I had to transfer what I learned into a normal programming language, first.  It doesn't make much sense to teach Java, where everything is already done for you.  The API Java docs are ******* huge.  It's a double edged sword, if you go with java, then you have this problem, if you don't, you don't have the GIGANTIC library of stuff at ur disposal.

Though if you take into account the linux kernel being written in C, and Windows (from what i've heard been mostly C/C++), it's pretty obvious where the true powers lie.  I mean yeah, java might have great scalability, and python might be super easy to make a kick-*** script for something, but I think the structure, the basis, are made in C/C++/C#.

I'm only interested in desktop apps and embedded systems..and embedded systems is a bit advanced for my current level, so that's out, and since Java sucks so much as daily desktop apps, unless you use an installer (which only makes sense for a huge program), Java is basically out the door too.

The way I see it I gotta strengthen up my C++, and take a look at C or C#.  They seem to be the building blocks for most other stuff.

[quote=MarkieB]I won't disagree with you, I'll just say I found the results [for windows] from JET vaguely fascinating..[/quote]

<-- Lost.

---

### Post by CptPicard on 2008-08-24
Heh... I would like to point out you sound like a total language flamewar troll there down at the end of your post. (Yeah, I use the T word when I feel like a post looks like it...)

> **Syndacate said:**
> Guess I'll look at C# next then, if it can provide both a desktop app type platform with end userabilty..so what's the catch?

Uh, C# being a MSFT Windows-language. You should understand that cross-platformness is far from a trivial requirement. You either deal with it or you take a lot of complexity in the form of cross-compilation or you do as most other people do, code for either Windows or Linux.

> 
Somebody told me they were written in C++, but I was more aiming at the point where even the JRE and everything installed is all distributed like that.  Think about it.  Any file a daily windows user uses (app wise) is a .exe o.O.

The JRE possibly couldn't. Logical impossibility.

> 
Wow, didn't know that.  I thought a basic JVM woulda processed basic phone apps the same.  Why are the Java chips so expensive?  Because they have to process a higher level language?  (I'm not doing embedded systems, but I'd love to if I ever got the chance).

A "basic JVM" is too big, because of course you're not going to assume you're running on some micro-machine when you're writing a JVM for a PC a lot more resources.

Plus there are simple supply vs. demand economics in play there I suppose.

> 
I've discovered the uselessness of Java as a desktop programming language.  

Fighting words...

Java is not useless on the desktop, but there are considerations to be taken into account. As I said earlier, cross-platformness is not a trivial requirement and you can't expect to get it for free.

> What I didn't realize was that I had to transfer what I learned into a normal programming language, first.

Java is not an "abnormal" programming language...

> It doesn't make much sense to teach Java, where everything is already done for you.

Java's extensive platform is actually one of its strong points :) I LIKE having a lot of stuff being done for me.

> if you don't, you don't have the GIGANTIC library of stuff at ur disposal.

The size of the library has nothing to do with it. You only load classes for what you need and instatiate the objects you do.

> 
Though if you take into account the linux kernel being written in C, and Windows (from what i've heard been mostly C/C++), it's pretty obvious where the true powers lie.

You not being able to write a kernel in a language (well, ok, *platform* -- the language doesn't theoretically speaking stop you) that runs on a virtual machine is surprising, how? :)

This is approaching the weird argument from the low-level guys that because kernels and VMs are not written in VM-language X, the low-level language is more "powerful". It's nonsense :) (it's better for the specific case of writing a VM for another language though...)

> since Java sucks so much as daily desktop apps, unless you use an installer (which only makes sense for a huge program), Java is basically out the door too.

The need to make an installer is the reason why Java sucks so much for desktop apps? Hmm... :)

> 
The way I see it I gotta strengthen up my C++, and take a look at C or C#.  They seem to be the building blocks for most other stuff.

Well, if exes are such a requirement, I suppose it's C#. C++ it's not, and on the Linux side you want C for the kind of stuff you really need it anyway.

---

### Post by Syndacate on 2008-08-24
> **CptPicard said:**
> Heh... I would like to point out you sound like a total **language flamewar troll** there down at the end of your post. (Yeah, I use the T word when I feel like a post looks like it...)

LoL  What's that?  Somebody who tries to start **** with people arguing about which language is better?  I'm just in it for the facts, not looking for a debate or anything..


> **CptPicard said:**
> Uh, C# being a MSFT Windows-language. You should understand that cross-platformness is far from a trivial requirement. You either deal with it or you take a lot of complexity in the form of cross-compilation or you do as most other people do, code for either Windows or Linux.

Yeah, but I'm not worried about cross-platformness anymore.  If it's a Linux user, I feel comfortable giving them a shell script and/or a class file or something - but it's the windows end users I'm more concerned about...and macs are only like 10% of the population...they don't count.

> **CptPicard said:**
> The JRE possibly couldn't. Logical impossibility.

Why's that?  It couldn't be written in Java...because then you wouldn't be able to run it..?  You'll have to excuse my ignorance here, no idea why that's impossible.  From what I understand C++ is a lower level language than Java.

> **CptPicard said:**
> A "basic JVM" is too big, because of course you're not going to assume you're running on some micro-machine when you're writing a JVM for a PC a lot more resources.

Plus there are simple supply vs. demand economics in play there I suppose.

Ah, I'm sorry, I worded that badly.  I didn't mean "basic JVM" as in the JVM you'd find on any computer, I meant "basic" as in low functionality, slim, only as needed, etc.  Though yeah, I don't think there's enough demand for embedded apps, it's a kick-*** cool process, IMO, but I don't think I'd ever get the chance :(

> **CptPicard said:**
> Fighting words...

Java is not useless on the desktop, but there are considerations to be taken into account. As I said earlier, cross-platformness is not a trivial requirement and you can't expect to get it for free.

True, on the cross-platformness, but I don't mean it as "it's useless, never use it" - but IMO, for creating small apps, without installers, it is very useless.  Or maybe it's not and I got things twisted...

> **CptPicard said:**
> Java is not an "abnormal" programming language...

Well I meant a language that natively worked as a small, stand-alone application.

> **CptPicard said:**
> Java's extensive platform is actually one of its strong points :) I LIKE having a lot of stuff being done for me.

Yeah, me too, that's why I say it's a double edged sword.

> **CptPicard said:**
> The size of the library has nothing to do with it. You only load classes for what you need and instatiate the objects you do.

Yeah but the point is it does, b/c there's lots of useful classes to implement into your program already done for you, that you'd have to write-out or make-up a class wise to do that in C++ or C...what I mean by big library is the amount of classes that sun gives you - ready for use at ur disposal.

> **CptPicard said:**
> You not being able to write a kernel in a language (well, ok, *platform* -- the language doesn't theoretically speaking stop you) that runs on a virtual machine is surprising, how? :)

This is approaching the weird argument from the low-level guys that because kernels and VMs are not written in VM-language X, the low-level language is more "powerful". It's nonsense :) (it's better for the specific case of writing a VM for another language though...)

Oh, I wasn't stating that it was impossible to make it in Java - I was simply pointing out that the main kernels and the like were built using other tools.  Though your first paragraph brings up a point, about Java needing the JVM to run, making it kinda hard to run on a machine who's kernel has to run the JVM...

As far as others go - if it wasn't great, then why are all these mainstream programs, Pidgin, the linux kernel, windows core, etc. all written in C or C++?  It's because they're basic, they give full control at the cost of lots of programming.

> **CptPicard said:**
> The need to make an installer is the reason why Java sucks so much for desktop apps? Hmm... :)

Well as stated earlier, .jar files aren't trusted by the idiot end user general public, which makes releasing small applications hard.  You can make an installer for larger ones such as Azureus, but as the calculator example I used, it'd be useless to make an installer for ~25kb.

> **CptPicard said:**
> Well, if exes are such a requirement, I suppose it's C#. C++ it's not, and on the Linux side you want C for the kind of stuff you really need it anyway.

Why'd C++ get removed, and why is C bad in win?

---

### Post by drubin on 2008-08-24
> **tinny said:**
> J2ME works quite well on phones but you run into significant problems when trying to maintain a single code base for multiple models of mobile phones. (The various JVM implementations have some bad bugs)

Some of them are sooo buggy it is scary.

---

### Post by tinny on 2008-08-24
> **rubinboy said:**
> Some of them are sooo buggy it is scary.

+1 

Isn't it crazy how crap some seem to be! Also the whole application signing thing is a pain (to get access to restricted APIs E.g. JSRXXX)

---

### Post by dribeas on 2008-08-25
Quite a bunch of nonsense in the 'need to be exe to be run' part of the posts.

If java is properly installed in windows, then double-click on a .jar file should launch it (equivalent to java -jar) which is just the same you do with .exe, .msi, .cmd, .zip. Most users have default windows explorer configuration hiding extensions, so they won't even notice.

Saying that Java requiring an installer is a problem for you is the dumbest excuse I've read for a long time. How many programs written with C/C++/C# have you used that did not require installation? I don't remember any (well putty, but just because I decided to download only putty.exe and not the complete suite that comes with an installer!)

Java not being suited for desktop applications seems as an interesting point you should try to explain to Oracle, IBM, Sun, or HP as they all have desktop applications written completely in Java. Even my government does it! The software they provide to help you fill in the taxes is a java program!! And, guess what, we are happy, since they dropped .exe away three years ago I can fill in taxes both in linux and macosx (which I run more often than windows). You can download a .exe installer that just unzips some jars, or a .zip file that you manually uncompress in any other system.

Most of the issues you have brought are really non-issues.

   David

---

### Post by drubin on 2008-08-25
java > exe

---

### Post by themusicwave on 2008-08-25
I have actually gone back and read the whole of both threads.

I agree with those who tell you that any serious program will need an installer.  Simply saying that your target Linux audience will be able to figure it out with a shell script is a cop out. That shell script IS an installer.  It just doesn't have a user interface.

Also, any major program can be installed without an installer, it is just a tedious task.  At work I often write programs in C#, Java, Python and some other languages.  I always make installers for them so that my end user doesn't have headaches.  It is just good practice.  

Otherwise you have to tell them "OK copy file X to directory Y...now copy file Z to directory Y...now add this to your PATH....Edit the config file line that says X...."  That is really all an installer does.  It automates this process to make the user's life easier and prevent errors that come from a bad configuration.

You will need this whether your application is written in C, C++, Python, Java, C#, LISP, Etc... Regardless of the language, you need an installer to arrange the files properly and put the libraries where they need to go, and setup the default configuration and all of that.  This need is language agnostic.

You also need to realize you will most likely need an installer for each platform you want to support.  Each platforms(or operating system) puts things in different places, so you need an installer that puts files where they need to go.

Also, don't get sucked into thinking C# is greater than Java.  It simply isn't, it is a clone of Java.  It still works exactly the same way as Java and still requires a Virtual Machine.  In C#'s case the VM is either the .Net Framework on Windows, Mono on Linux and perhaps there is none on other platforms(have no idea about Macs and Solaris).   It's features are on par with that of Java, but it's platform support is much weaker.  

Just because C# comes out of the compiler with a .exe extension and Java comes out with a .jar doesn't mean C# runs natively.  As a matter of fact, that C# application won't run at all on some platforms.  The only reason many exes work on Ubuntu is WINE.  A jar file will run on almost any platform with very minor work.  

On Windows when you run a C# exe file, it uses Just In Time Compilation the same way a Java jar file does.  You just don't notice it because the .exe fools you into thinking it is a binary file.  I think it is possibly to make a C# binary, but I am not 100% sure.  By default it is not a binary.

C# is also never used in the embedded world.  That is primarily the domain of C.  However, the embedded space and the desktop space are two entirely different domains, I would not expect the same language to be optimal for both.

Anyways, just throwing another voice into the fray.  That was a long post...

---

### Post by nvteighen on 2008-08-25
> **dribeas said:**
> 
Even my government does it! The software they provide to help you fill in the taxes is a java program!! And, guess what, we are happy, since they dropped .exe away three years ago I can fill in taxes both in linux and macosx (which I run more often than windows).

Yup, Spanish central and autonomous governments are doing an interesting effort towards open source. Andalucia is creating its own Ubuntu-based Linux distro, GuadalinEx... ([http://www.guadalinex.org/](http://www.guadalinex.org/) In Spanish).

---

### Post by MarkieB on 2008-08-25
no longer participating in ubuntuforums.org

---

### Post by tinny on 2008-08-25
> **dribeas said:**
> Quite a bunch of nonsense in the 'need to be exe to be run' part of the posts.

If java is properly installed in windows, then double-click on a .jar file should launch it (equivalent to java -jar) which is just the same you do with .exe, .msi, .cmd, .zip. Most users have default windows explorer configuration hiding extensions, so they won't even notice.

Saying that Java requiring an installer is a problem for you is the dumbest excuse I've read for a long time. How many programs written with C/C++/C# have you used that did not require installation? I don't remember any (well putty, but just because I decided to download only putty.exe and not the complete suite that comes with an installer!)

Java not being suited for desktop applications seems as an interesting point you should try to explain to Oracle, IBM, Sun, or HP as they all have desktop applications written completely in Java. Even my government does it! The software they provide to help you fill in the taxes is a java program!! And, guess what, we are happy, since they dropped .exe away three years ago I can fill in taxes both in linux and macosx (which I run more often than windows). You can download a .exe installer that just unzips some jars, or a .zip file that you manually uncompress in any other system.

Most of the issues you have brought are really non-issues.

   David

Sorry, I completely disagree. The examples you give for successful desktop applications are for ones that are either targeted at power users or deployed within a managed IT infrastructure. A power user will always be able to get their JVM installed and setup correctly. In a managed IT infrastructure (government) the standard deployed desktop image for the organisation should have the JVM setup and really to go and if not the support desk is just a phone call away.

The OP wants to target their application at a dumb user.

If this application was distributed to my Mother as a jar she would have no glue how to install the JVM. 

Give me an example of a Java application this is distributed as a jar to beginner users and you will be showing be an application that is doomed to fail.

---

### Post by drubin on 2008-08-25
> **tinny said:**
> The OP wants to target their application at a dumb user.

If this application was distributed to my Mother as a jar she would have no glue how to install the JVM. 

Give me an example of a Java application this is distributed as a jar to beginner users and you will be showing be an application that is doomed to fail.

Never thought I would hear you say that!

---

### Post by CptPicard on 2008-08-25
> **tinny said:**
> 
Give me an example of a Java application this is distributed as a jar to beginner users and you will be showing be an application that is doomed to fail.

Well, my toolkit is distributed as a jar plus dependency jars with a text file telling how to create .bats to launch the various command line utils, how to setup CLASSPATH, PATH, JVM... ;) Support requests are answered with "rtfm".

Then again, my software has exactly one client user who is rather dependent on getting it to work so he needs to be able to afford some local desktop support instead of pestering the actual developer (me) with trivialities... ;)

---

### Post by Reiger on 2008-08-25
Granted you want an installer for serious Java apps. But as with all major apps your installer is going to 'hide' most of the thing somewhere deep inside the dark vaults of /usr/share or C:\Program Files\

Which means your average computer illiterate user won't be able to even *find* that thing back again on its own; lest you included some easy to find shortcuts/symlinks. Which is incidentally part of the installer job.

So: what's wrong with JAR files especially executable JAR files (manifest file!), especially effectively *hidden* JAR files?

It's portable too...

---

### Post by tinny on 2008-08-25
> **Reiger said:**
> Granted you want an installer for serious Java apps. But as with all major apps your installer is going to 'hide' most of the thing somewhere deep inside the dark vaults of /usr/share or C:\Program Files\

Which means your average computer illiterate user won't be able to even *find* that thing back again on its own; lest you included some easy to find shortcuts/symlinks. Which is incidentally part of the installer job.


Thats the point, they dont care. They will just happily click the shortcut that is created by the installer. DONE!

> **Reiger said:**
> 
So: what's wrong with JAR files especially executable JAR files (manifest file!), especially effectively *hidden* JAR files?

It's portable too...

Theory and practice are complete different!

So every pro jar poster here please answer me this. Say you have an application that you have developed and compiled to a jar. This application is targeted at the noob user, someone that doesn't care for the technical aspects of a computer. They have a standard install of XP with no JVM. What do you do?

(The answer is not to personally help every user with the install of the JVM)

BTW: I am pro the Java installer approach, not the jar only approach.

---

### Post by Reiger on 2008-08-25
Now let's separate two things first:
1) Installer
2) Executable.

I'm with you on the installer; but I don't see what's wrong with the well-established JAR-way of handling the executable bit.

Incidentally a proper installer will take care of the dependencies such as enabling people to install a JVM. And there are files which proclaim in big, friendly -- preferably pink -- letters: [S]"DON'T PANIC"[/S] "README". :D

EDIT: So to sum up:
1) The big Quest for the EXE is IMHO rather void; and solved easily enough with executable JAR files + symlinks/shortcuts;
2) The big issue of dependencies is something for a proper installer to take of and don't have to do anything with (1) plus won't exist by the time (1) actually becomes anything remotely of issue to the end-user.
3) There is nothing wrong with a README file. That can be used to make users aware of the need for a VM; and incidentally the users got to grab it from somewhere so there you can stick that notice too. If anything: wrap your actual JAR file inside an executable one which has only one job: to install the content. Ship that in a .zip or tarball; include README files or Instalation Instructions and/or Release notes. Do so where you publish your app too.

---

### Post by tinny on 2008-08-25
> **Reiger said:**
> Now let's separate two things first:
1) Installer
2) Executable.

I'm with you on the installer; but I don't see what's wrong with the well-established JAR-way of handling the executable bit.

Incidentally a proper installer will take care of the dependencies such as enabling people to install a JVM. And there are files which proclaim in big, friendly -- preferably pink -- letters: [S]"DON'T PANIC"[/S] "README". :D

+1 Installer :-)

Unfortunately we still have some way to go with the jar executable. :-( (Java on the desktop)

---

### Post by Syndacate on 2008-08-26
> **dribeas said:**
> Quite a bunch of nonsense in the 'need to be exe to be run' part of the posts.

If java is properly installed in windows, then double-click on a .jar file should launch it (equivalent to java -jar) which is just the same you do with .exe, .msi, .cmd, .zip. Most users have default windows explorer configuration hiding extensions, so they won't even notice.

Saying that Java requiring an installer is a problem for you is the dumbest excuse I've read for a long time. How many programs written with C/C++/C# have you used that did not require installation? I don't remember any (well putty, but just because I decided to download only putty.exe and not the complete suite that comes with an installer!)

It's not a dumb excuse if your program is 27kb...like the excuse we've been using.  Dumb is making an installer for a 27kb program.

> **dribeas said:**
> Java not being suited for desktop applications seems as an interesting point you should try to explain to Oracle, IBM, Sun, or HP as they all have desktop applications written completely in Java. Even my government does it! The software they provide to help you fill in the taxes is a java program!! And, guess what, we are happy, since they dropped .exe away three years ago I can fill in taxes both in linux and macosx (which I run more often than windows). You can download a .exe installer that just unzips some jars, or a .zip file that you manually uncompress in any other system.

Most of the issues you have brought are really non-issues.

   David

I don't wanna say you're missing the point, but **YOU'RE COMPLETELY MISSING THE POINT!! - TO NO END**  *sigh*

I'm not saying Java is bad to use on Desktops, as you seem to think I said/meant.  I mean it seems bad to produce small apps on.  I do realize what a jar file is, yes, we've discussed jar files many times.  You weren't in the first 15 pages of this post, stop tryin to jump in and insert ur $0.02 now...

Also, of course people using solaris and systems built by major manufacturers are going to have JRE's installed, that is NOT BY DAMN-SIGHT my target audience though.

> **themusicwave]I have actually gone back and read the whole of both threads.

I agree with those who tell you that any serious program will need an installer. Simply saying that your target Linux audience will be able to figure it out with a shell script is a cop out. That shell script IS an installer. It just doesn't have a user interface.[/quote]

I think you mis-understand my intentions.  I simply mean that the particular community I'm targeting is a VERY small percentage linux users (probably by far less than 1%), so I'm hoping any linux users in it will have enough "linux skill" to have no problems using CLI, as windows users tend to run 'n hide from.

[quote=themusicwave]Also, any major program can be installed without an installer, it is just a tedious task. At work I often write programs in C#, Java, Python and some other languages. I always make installers for them so that my end user doesn't have headaches. It is just good practice.

Otherwise you have to tell them "OK copy file X to directory Y...now copy file Z to directory Y...now add this to your PATH....Edit the config file line that says X...." That is really all an installer does. It automates this process to make the user's life easier and prevent errors that come from a bad configuration.[/quote]

True, but the sheer size of the program (incredibly tiny) doesn't warrant an installer, IMO.  I keep going back to the example of the basic windows calculator which I estimate without scientific mode at about 27kb.  You'd make an installer for that?

[quote=themusicwave]You will need this whether your application is written in C, C++, Python, Java, C#, LISP, Etc... Regardless of the language, you need an installer to arrange the files properly and put the libraries where they need to go, and setup the default configuration and all of that. This need is language agnostic.

You also need to realize you will most likely need an installer for each platform you want to support. Each platforms(or operating system) puts things in different places, so you need an installer that puts files where they need to go.[/quote]

Well yes and no.  With such a small app, it doesn't need any support files, so I mis-understand the need to copy the ONE file to a separate directory.  I intended this to be a stand-alone executable, executable from anywhere.

[quote=themusicwave]Also, don't get sucked into thinking C# is greater than Java. It simply isn't, it is a clone of Java. It still works exactly the same way as Java and still requires a Virtual Machine. In C#'s case the VM is either the .Net Framework on Windows, Mono on Linux and perhaps there is none on other platforms(have no idea about Macs and Solaris). It's features are on par with that of Java, but it's platform support is much weaker.[/quote]

Yeah, a friend told me it's basically a clone of Java.  I didn't know it requires a virtual Machine, but IMO, if I'm targetting Windows end users, isn't utilizing .NET frame work with C# a good idea?  (This is excluding the want for cross-platoform-usability).  I mean even in Linux or Mac I can distribute a Jar file, but if it seems impractical for windows users, who are 99.9% of the community pop I'm distributing to, it defeats the purpose - sorta.  I mean yeah a jar will work, assuming they have the JRE installed correctly, but most of these people don't know their head from their *** when it comes to anything even remotely dealing with computers.  With this rather uneducated group of people, this is a BAD assumption to make.  Regardless of how common.

[quote=themusicwave]Just because C# comes out of the compiler with a .exe extension and Java comes out with a .jar doesn't mean C# runs natively. As a matter of fact, that C# application won't run at all on some platforms. The only reason many exes work on Ubuntu is WINE. A jar file will run on almost any platform with very minor work.

On Windows when you run a C# exe file, it uses Just In Time Compilation the same way a Java jar file does. **You just don't notice it because the .exe fools you into thinking it is a binary file. I think it is possibly to make a C# binary, but I am not 100% sure. By default it is not a binary.**[/quote]

Oh, damn.  Can't say I knew that.  Though I can't care less who it fools or how it works - if it works for end users.  I don't want pple to jump through hoops for such a small app, it's stupid.  Even as much as going to download JRE becomes a hassle in some peoples' eyes.

[quote=themusicwave]C# is also never used in the embedded world. That is primarily the domain of C. However, the embedded space and the desktop space are two entirely different domains, I would not expect the same language to be optimal for both.

Anyways, just throwing another voice into the fray. That was a long post...[/quote]

That makes sense, seeing as C# is almost completely only used in Windows.  Though I wonder how its use is in Windows Mobile  said:**
> really? where?

JET makes a binary that contains [most][= the necessary portions] of the JRE in it as well, compared to the standard 'jar wrapper' style. It is, of course, for windows. The message just ahead suggested that essentially, a jar distribution is the answer in the end

Ah, I see.  It makes sense, but I'm not paying for it, lol.

> **tinny]Sorry, I completely disagree. The examples you give for successful desktop applications are for ones that are either targeted at power users or deployed within a managed IT infrastructure. A power user will always be able to get their JVM installed and setup correctly. In a managed IT infrastructure (government) the standard deployed desktop image for the organisation should have the JVM setup and really to go and if not the support desk is just a phone call away.[/quote]

I agree, it's a completely biased opinion, of course the JVM is gonna work on solaris...it's kinda redundant.

[quote=tinny]The OP wants to target their application at a dumb user.

If this application was distributed to my Mother as a jar she would have no glue how to install the JVM.[/quote]

Exactly.

[quote=tinny]Give me an example of a Java application this is distributed as a jar to beginner users and you will be showing be an application that is doomed to fail.[/quote]

That was my point - None are - all are distributed as executables.  Now I'm not sure if that's because all programs written in Java are installed or not written in Java, but I still feel it's redundant to use an installer on such a small program.

The JVM is a very double edged sword..

[quote=CptPicard]Well, **my toolkit** is distributed as a jar plus dependency jars with a text file telling how to create .bats to launch the various command line utils, how to setup CLASSPATH, PATH, JVM...  Support requests are answered with "rtfm".

Then again, my software has exactly one client user who is rather dependent on getting it to work so he needs to be able to afford some local desktop support instead of pestering the actual developer (me) with trivialities... [/quote]

Yeah, but all my point is, is how many windows end users even have the slightest clue what a toolkit is?

I think tinny said it best - *if I gave this application to my mom [s]or dad[/s] (not fair b/c he's had extensive redhat experience and been using win since DOS), would she be able to open it?*

PS:
"*RTFM*" on non-trivial **** from producers can sometimes piss me off like nothing else.  How trivial something is is relative.

[quote=Reiger]Granted you want an installer for serious Java apps. But as with all major apps your installer is going to 'hide' most of the thing somewhere deep inside the dark vaults of /usr/share or C:\Program Files\

Which means your average computer illiterate user won't be able to even find that thing back again on its own said:**
> 

Precisely.  My words exactly.  Though on the flipside, let's use a keygen for example, though I'm sure none of you are aware of that b/c nobody pirates, right?? (*actually the truth is probably closer to the fact that nobody in here uses windows so has the need to pirate, lol*) Keygens, you don't install keygens, why?  Because they're small as ****, it's completely impractical.  They're stand-alone apps.

[quote=Reiger]So: what's wrong with JAR files especially executable JAR files (manifest file!), especially effectively hidden JAR files?

It's portable too...

I suppose there wouldn't be anything wrong with it **if there was a guarantee that they had the JRE installed**.  Though there's no guarantees there.  You're typical computer illiterate ***-back end user is most likely not gonna have the JRE installed unless he "*ran into it*" somewhere and needed it, and "*went through hell*" to get it downloaded and installed.

With all my previous bitching about executables and nativeness to windows, I hadn't even thought about the JVM isn't native to windows, regardless of how cross platform it is, there's no guarantee that the JRE is even installed.  Last I checked it didn't come with any service packs or anything (or at least not with Vista, been too long since I've installed XP to remember what SP2 gave).

> **tinny]Thats the point, they dont care. They will just happily click the shortcut that is created by the installer. DONE![/quote]

Yeah, some don't even delete the shortcut for fear of deleting the entire program. O.O!!

[quote=tinny]Theory and practice are complete different!

So every pro jar poster here please answer me this. Say you have an application that you have developed and compiled to a jar. This application is targeted at the noob user, someone that doesn't care for the technical aspects of a computer. They have a standard install of XP with no JVM. What do you do?

(The answer is not to personally help every user with the install of the JVM)

BTW: I am pro the Java installer approach, not the jar only approach.[/quote]

Would you still say use a java installer for the 1 class file 27kb calculator app previously mentioned?  I see it as impractical...but I don't have a lot of experience to base that decision on.

[quote=Reiger]Now let's separate two things first:
1) Installer
2) Executable.

I'm with you on the installer said:**
> 

I guess nothing, per-se, I just feel that noob end users might get a lil skiddish "because it's not an executable" - like new-entry-linux-syndrome (NELS).  For somebody that actually knows there way around I'd say gogo jar, but most people DON'T.  You (and a few other people) brought up a good point, that extensions are hidden by default, and that they wouldn't even know.  Though this is true, it's also JRE dependent, and I didn't even consider that when I was thinking Java.  :(  That puts a kink in things even further.  JAR files seems like a **VERY PRACTICAL WAY** (yes, I'm agreeing with it) to release small applications in Java that don't have the need for an installer.  Though the question is are those JAR archives "too advanced?"  After MUCH discussion about this I'm starting to think Java isn't the best platform for producing apps for 'desktop use' (without installers) - and seasoned programmers seem to agree with me.

[quote=Reiger]Incidentally a proper installer will take care of the dependencies such as enabling people to install a JVM. And there are files which proclaim in big, friendly -- preferably pink -- letters: [S]"DON'T PANIC"[/S] "README".

EDIT: So to sum up:
1) The big Quest for the EXE is IMHO rather void; and solved easily enough with executable JAR files + symlinks/shortcuts;
2) The big issue of dependencies is something for a proper installer to take of and don't have to do anything with (1) plus won't exist by the time (1) actually becomes anything remotely of issue to the end-user.
3) There is nothing wrong with a README file. That can be used to make users aware of the need for a VM; and incidentally the users got to grab it from somewhere so there you can stick that notice too. If anything: wrap your actual JAR file inside an executable one which has only one job: to install the content. Ship that in a .zip or tarball; include README files or Instalation Instructions and/or Release notes. Do so where you publish your app too.

1)  True, assuming the JRE is installed.
2)  What?
3)  There is something wrong with a read-me file, PEOPLE DON'T READ IT, lol.  Remember the targer, windows end users, "man foo" isn't even a remote thought to them.

[quote=tinny]+1 Installer

Unfortunately we still have some way to go with the jar executable. (Java on the desktop)[/quote]

Yeah, I hear ya, but everytime somebody mentions something pro-installer, I'ma keep mentioning that 27kb calculator application for OEM windows (since '95) which is LARGER than my program even intends to be.

Question:
What will happen if they are using a base XP SP2 (or SP3) or Vista setup and they **do not** have JRE installed, and they double click on a .jar file?

My guess is windows will go into "confusaled" mode asking "*what program do you want to use to open this file with*" and they wont' know worth of dick - and the user experience will drop through the floor pretty damn quick.  That **is** a MAJOR plus to having an installer...but the 27kb calculator app...

---

### Post by Syndacate on 2008-08-26
PS:
In case you scrolled 4 screens to see my whole post.

Sorry.

---

### Post by Reiger on 2008-08-26
Well this may be my own biased opinion of course; but if your end user is smart enough to install software that doesn't come with an installer and doens't get scared away of the thought of downloading something then manually extracting it somewhere... (You need the latter in order for the former to apply, I suppose...)

... Then there's no harm in trusting them to either read the README or Installation Instructions or better yet: a notice above the download link. People who install software without an installer are not that hopelessly computer illiterate they can't download a JRE from SUN's. You may even provide them with a download link.

Then your JAR file works. You may even explain that indeed it's a JAR file they gonna launch to run the app and there's nothing scary about that (i.e. one is supposed to do that). :)

Actually: people who do install things usually aren't the most computer illiterate; though they do -from time to time- have surprisingly little common computer sense. ;)

---

### Post by tinny on 2008-08-26
> 
Would you still say use a java installer for the 1 class file 27kb calculator app previously mentioned? I see it as impractical...but I don't have a lot of experience to base that decision on.


I am pro installers in general for desktop Java applications. But for your small application I would not use an installer. Instead I would port the application to C# and compile it using Visual Studio Express. But thats just my opinion.

Good luck :)

---

### Post by dribeas on 2008-08-26
> **Syndacate said:**
> It's not a dumb excuse if your program is 27kb...like the excuse we've been using.  Dumb is making an installer for a 27kb program.

I'm not saying Java is bad to use on Desktops, as you seem to think I said/meant.  I mean it seems bad to produce small apps on.  I do realize what a jar file is, yes, we've discussed jar files many times.  You weren't in the first 15 pages of this post, stop tryin to jump in and insert ur $0.02 now...

Also, of course people using solaris and systems built by major manufacturers are going to have JRE's installed, that is NOT BY DAMN-SIGHT my target audience though.


First, even if I did not write, I was reading the post since the very beginning: do not assume what you don't know. For small applications a .jar file is good enough for the end user there is no difference from jar and exe files [*], you  don't need to provide an installer: it is just an excuse in your side. I think you understand that Spanish government does not have Solaris users as the intended audience for a tax program.

[*] as long as they have JRE installed, but most people already have it to run applets while browsing, as I said.

Please, re-read the post and if there is something you don't understand from it ask. *My 0.02€*

---

### Post by drubin on 2008-08-26
Most users do not even know what an exe is! They just like to double click on things.....

As long as it wont open with a archive manager. (If you have this much installed you generally know what you are doing)

---

### Post by themusicwave on 2008-08-26
@OP
I wasn't aware it was a tiny application.

Even so, there are benefits to properly installing even a small application that must be weighed.

If you user is not smart enough to install the JRE there is no way they will want to browse to the folder the application is in to run it.  An installer can make all the nice desktop shortcuts, start menu items, etc that user's expect.  Without an installer how will you provide this?

This of course is not 100% necessary and is a choice.  It merely adds a level of polish to the final product.

I also don't understand why you would willing choose to write the same program twice.  I am a big believer in writing something the right way one time.  I know the program is small so this isn't such a huge issue, but what happens when you decide to add a new feature?  You'll have to write it 2 times!  You will need to solve this issues if you ever want a manageable larger application.  Then again I tend to try to write overly elegant code, so we all have our flaws.

You should also note that the .Net Framework is not always installed with Windows and can have multiple versions.  Just yesterday one of my applications failed to deploy because my customer's IT department had uninstalled it.  I had to direct him to the Microsoft Website to download it.  There are also several versions of it, and many machines don't have the latest one.  So, how do you handle that issue?  Build against the oldest version?  Bundle it with the application?  You will have the exact same problem.

If you are truly worried about this sort of thing, then C#, Java, Python, PHP, Perl and Ruby are all out.

Your only choices are C, C++ and assembly.  Now you need to deal with any incompatibilities and cross compilation issues, the very things C# and Java were invented to prevent.

In the end you seem to have made up your mind.  

@tinny

I am developing an application for release in Java right now.  It depends not only on Java, but also on Open office and PostgreSQL.  

My current plan is either to use Netbeans to bundle the JRE with my application.  Or to build an installer that contains the JRE and performs a silent install of it using command line arguments.  This can also be done with Open Office.  I am leaning towards the second option.

Take a look at this:
[Java SE 6 Silent Install]("http://java.sun.com/javase/6/docs/technotes/guides/deployment/deployment-guide/silent.html")

I have another system in production use that relies on PostgreSQL, Python, Apache, some C# dlls, and various other files and applications.  To install it I simply wrote a small installer application to prompt the user for input.  Then using that input I pass the correct parameters to each of the component installers.  Once I verify that they have installed, I go through the config file and change anything else I need to change.

They pop the CD-ROM in the machine, the auto run pops up and they enter about 5 things and hit install.  It is very painless for them.  Behind the scenes they have little idea what is being installed, it is all documented in the manual if they really care though.

---

### Post by tinny on 2008-08-26
> **themusicwave said:**
> 

@tinny

I am developing an application for release in Java right now.  It depends not only on Java, but also on Open office and PostgreSQL.  

My current plan is either to use Netbeans to bundle the JRE with my application.  Or to build an installer that contains the JRE and performs a silent install of it using command line arguments.  This can also be done with Open Office.  I am leaning towards the second option.

Take a look at this:
[Java SE 6 Silent Install]("http://java.sun.com/javase/6/docs/technotes/guides/deployment/deployment-guide/silent.html")

I have another system in production use that relies on PostgreSQL, Python, Apache, some C# dlls, and various other files and applications.  To install it I simply wrote a small installer application to prompt the user for input.  Then using that input I pass the correct parameters to each of the component installers.  Once I verify that they have installed, I go through the config file and change anything else I need to change.

They pop the CD-ROM in the machine, the auto run pops up and they enter about 5 things and hit install.  It is very painless for them.  Behind the scenes they have little idea what is being installed, it is all documented in the manual if they really care though.

Sounds like you are doing some interesting stuff. :)

Have you looked at [advanced installer]("http://www.advancedinstaller.com/java.html")?

---

### Post by Syndacate on 2008-08-27
> **Reiger said:**
> Well this may be my own biased opinion of course; but if your end user is smart enough to install software that doesn't come with an installer and doens't get scared away of the thought of downloading something then manually extracting it somewhere... (You need the latter in order for the former to apply, I suppose...)

And if they aren't smart enough?  I know this **** seems INCREDIBLY trivial to you - but for your typical dumb-**** end user, is it so?  Not usually.

> **Reiger said:**
> ... Then there's no harm in trusting them to either read the README or Installation Instructions or better yet: a notice above the download link. People who install software without an installer are not that hopelessly computer illiterate they can't download a JRE from SUN's. You may even provide them with a download link.

There is always harm in trusting whether people will read the readme - because a lot of people never do unless sometimes, if they get stuck, AFTER they complain about it.  I realize I can simply provide a link, but people simply aren't smart about it.  They can take the approach of "*ah, ****, I gotta do this crap just to get it to run?  **** that...*"

> **Reiger said:**
> Then your JAR file works. You may even explain that indeed it's a JAR file they gonna launch to run the app and there's nothing scary about that (i.e. one is supposed to do that). :)

Actually: people who do install things usually aren't the most computer illiterate; though they do -from time to time- have surprisingly little common computer sense. ;)

All I'm saying, is since the JRE isn't defaulted in - it's one extra "hoop" the end user will see it as to jump through in order to get the program to work.  People don't like prerequisites...though of course I can always keep it in a JAR file for the mac and Linux users...OR I can distribute it as a JAR file until I port it to C# or C++.  This way I still get the cross plat-form-ability - and then a native version will come out soon enough for those that don't want to deal with downloading and installing the JRE...that might work...

> **tinny]I am pro installers in general for desktop Java applications. But for your small application I would not use an installer. Instead I would port the application to C# and compile it using Visual Studio Express. But thats just my opinion.

Good luck[/quote]

Yeah, that makes sense, I suppose.  Why C# instead of C++, though?  Easier to port than C++..or what?

[quote=dribeas]First, even if I did not write, I was reading the post since the very beginning: do not assume what you don't know. For small applications a .jar file is good enough for the end user there is no difference from jar and exe files[*], you don't need to provide an installer: it is just an excuse in your side. I think you understand that Spanish government does not have Solaris users as the intended audience for a tax program.
[*] as long as they have JRE installed, but most people already have it to run applets while browsing, as I said.

Please, re-read the post and if there is something you don't understand from it ask. My 0.02€[/quote]

Point taken.

[quote=rubinboy]**Most users do not even know what an exe is!** They just like to double click on things.....

As long as it wont open with a archive manager. (If you have this much installed you generally know what you are doing) [/quote]

LoL - I didn't think about that - but you're right, end users ARE click happy - and need to be treated as so.

Though you bring up an interesting **PROBLEM** with using the JAR format.

If they have winrar or another 3rd party archiving program installed, it will be associated with JAR's by default upon installation.  So then what - they double clicky - and it opens up a window with the class files in it - and we're back to square one...

[quote=themusicwave]@OP
I wasn't aware it was a tiny application.

Even so, there are benefits to properly installing even a small application that must be weighed.

If you user is not smart enough to install the JRE there is no way they will want to browse to the folder the application is in to run it. An installer can make all the nice desktop shortcuts, start menu items, etc that user's expect. Without an installer how will you provide this?[/quote]

This is true, but I wasn't aiming for shortcuts 'n the like - I was aiming for "wherever you put it - it will run" - like any other app of its size...Actually, I'm aiming for just the contrary - I DON'T want this to be a big thing, with shortcuts and startmenu entries 'n all - I want this to be very small and portable - like a keygenerator.  When was the last keygen u used that needed an install??

[quote=themusicwave]This of course is not 100% necessary and is a choice. It merely adds a level of polish to the final product.[/quote]

True, but I'm not looking for a level of polish - **I'd abolish the GUI altogether and keep it CLI with letter entry if I could find a way to keep the damn terminal/command prompt open...**  I don't think all u expert programmers realize what a low-level program this is.  It doesn't even calculate anything!  It's simply a few loops and a ****-ton of if/then/else statements!

[quote=themusicwave]I also don't understand why you would willing choose to write the same program twice. I am a big believer in writing something the right way one time. I know the program is small so this isn't such a huge issue, but what happens when you decide to add a new feature? You'll have to write it 2 times! You will need to solve this issues if you ever want a manageable larger application. Then again I tend to try to write overly elegant code, so we all have our flaws.[/quote]

I do see your point.  My willingness does come from the fact that in C++ it would be x = 2 + 2 said:**
> You should also note that the .Net Framework is not always installed with Windows and can have **multiple versions**. Just yesterday one of my applications failed to deploy because my customer's IT department had uninstalled it. I had to direct him to the Microsoft Website to download it. There are also several versions of it, and many machines don't have the latest one. So, how do you handle that issue? Build against the oldest version? Bundle it with the application? You will have the exact same problem.

Yeah, I've run into the multiple versions of .Net pwning each other issue a few times myself when I was not smart and used windows on a daily basis.  I do see what you're saying, and that **WOULD** be something to look out for - **IF** my program wasn't the end all most basic hello-world-type program ever constructed.  The structures/methods 'n such that I'm using are so old they're a hop-skip-and a jump from assembly.  Seriously, NOTHING is above die-hard basic stuff.  I haven't even ran into any language specific data structures yet - nor intend to, just prim types and **** that is shared in every language (such as loops and conditionals) - that's how damn basic this program is - I really think you guys are simply overestimating what my program is.  _All it is is a huge party of loops and conditionals_ - I could write the thing in C if I wanted to and it'd probably take just as long to write it _and I don't even know C_.

I mean that dude mentioned his Spanish Gov't.  ---  This program is NOWHERE NEAR that caliber - it's seriously in the neighborhood of *a semester of GENERAL programming class without any assignments (just listening)*.  I swear, if I could find a way to manipulate the CLI to stay open this thing wouldn't even come near a GUI.  Think of it as creating a calculator in basic CLI enter X value and enter Y value; (print x + y) - it's simply more basic than that because it doesn't even use any logic operators.

Lemme illustrate it a different way:
I could probably make a big chart in a notepad file that would serve the purpose of this program...but that's just stupid.  And yes, if I do use C# I would have to simply depend on the .NET framework being intact - though the version wouldn't matter worth of dick, unless if statements & loops are something new to C#...which I don't think they are...

[quote=themusicwave]If you are truly worried about this sort of thing, then C#, Java, Python, PHP, Perl and Ruby are all out.

Your only choices are C, C++ and assembly. Now you need to deal with any incompatibilities and cross compilation issues, the very things C# and Java were invented to prevent.

In the end you seem to have made up your mind.[/quote]

I have, I guess, I'm just not happy with it.  I'd use the JAR file in a heartbeat (even with my JRE doubts) if it wasn't for the fact that I can easily see me getting blamed for complications due to aftermarket archiving programs suchs as winace and winrar defaulting themselves to the JAR file extension.  Let's not forget, Windows doesn't use MIME types (and if it does it sure as **** seems like it doesn't).  Tons of people have aftermarket archiving programs such as winrar - this makes this a VERY BIG PROBLEM.

How the heck do you tell an end user to locate the JVM when you hit "open with?" -- "*Yeah, don't worry, it's in the java binary folder, it's called 'java'*"

I have no problem using C++, that was my original intention, as that compiles natively.  I dual boot all my systems with a win distro on each, so I can compile the source separately on my mac, Vista, XP, and *nix - so I doubt I'd run into many cross compilation issues since even in *nix most use the same basic compiler.  Assembly takes too ******* long and nowhere near relates to end user-ability - and C is still on the table as well.

[quote=themusicwave]@tinny

I am developing an application for release in Java right now. It depends not only on Java, but also on Open office and PostgreSQL.

My current plan is either to use Netbeans to bundle the JRE with my application. Or to build an installer that contains the JRE and performs a silent install of it using command line arguments. This can also be done with Open Office. I am leaning towards the second option.

Take a look at this:
Java SE 6 Silent Install

I have another system in production use that relies on PostgreSQL, Python, Apache, some C# dlls, and various other files and applications.To install it I simply wrote a small installer application to prompt the user for input. Then using that input I pass the correct parameters to each of the component installers. Once I verify that they have installed, I go through the config file and change anything else I need to change.

They pop the CD-ROM in the machine, the auto run pops up and they enter about 5 things and hit install. It is very painless for them. Behind the scenes they have little idea what is being installed, it is all documented in the manual if they really care though.[/quote]

It sounds great - but based on your description I see words like **GARGANTUAN**, **PROFESSIONAL** and **COMPLEX** float across my mind ;).  If I was doing that (which I wouldn't be, because that's way over my head), I would be using an installer too, and damn straight it'd be bundled with every environment it needs under the sun - but that's not.

Think of the 27kb calculator.

Think of a keygen.

Think linux - think small.  Think about the 5Mb Distro witch Apache that guy made using LFS.
[http://www.linuxfromscratch.org/pipermail/lfs-support/2001-October/000202.html](http://www.linuxfromscratch.org/pipermail/lfs-support/2001-October/000202.html)

;).

Maybe now u see what I mean - this program is so ridiculously simple, I think everybody's overshooting it.  And I do have worries about releasing it in a JAR and peoples' archiving programs associating it as just an archive, along with the obvious JRE deal.

Though as I said, C and C++ are still very-much-so on the table...

---

### Post by Reiger on 2008-08-27
Well yes but my point is that people who actively go out there online to seek themselves an app to do what they want... These aren't the most computer illiterate users. Of course if you'd ship your app on CD's/DVD's then you can't assume that anymore -- but hey: you'd be including an installer for those anyway; so that's not the case. ;)

Point 2 is that people who go out there online to seek themselves an app to do whatever they want; can repeat that feat to download SUN's JRE -- better yet: these people are likely to have installed Java before; if only for the web applets.

Again that's my idea; not neccesarily rock solid fact.

---

### Post by themusicwave on 2008-08-27
@OP

I better understand your goals now.  You simply want a standalone file with no absolutely dependencies that runs native on most any system. No polish no nothing, just the application.

I would say to achieve this you will need to write it in C or C++ or perhaps D(no experience with it).  There is simply no other way around it.  With a very basic application like this, you shouldn't run into many cross platform issues.

You can't use C# for the same reason you cannot use Java.  The user may not have the .Net Framework(or Mono) and it would be similar to downloading the JRE.  Also, the framework doesn't even exist for some platforms as far as I know.

Similar concerns come with Python, Ruby, PHP, LISP, Perl and just about every interpreted or hybrid language(JIT Compilation).

I think in this case you need to just write a C or C++ program that uses nothing platform specific(ex no Windows.h) and compile it for different platforms.  

The only reason I bring up so many things in my other posts, is that as you begin to write more complex programs you will run into some cross platform issues.  One of the beauties of Java and Python and other languages like them is that they remove almost all of these issues.

I would never recommend writing the same program in multiple languages for multiple platforms.  You need to do it once the right way and be done with it.  Especially if you want to do weekly updates.

You still have the added annoyance of having to compile the app multiple times each time you build it.  But you don't have dependency worries.

Much of programming and engineering in general is about trade offs.  You trade one thing for another.  In this case you give up some ease of cross platform support and gain no dependencies.  As you program and engineer and build things you will run into these sorts of things.  You need to weigh the choices and pick the trade off you think is best.

---

### Post by tinny on 2008-08-27
> **themusicwave said:**
> 
You can't use C# for the same reason you cannot use Java.  The user may not have the .Net Framework(or Mono) and it would be similar to downloading the JRE.  


For the last 5 years I haven't seen a Windows XP install that doesn't at least have .Net 1.1. Many of Microsoft's core products require .Net. (.Net 1.1 easily provides the functionality to deliver the basic application that the OP is after)

Migrating from Java to C# will be ALOT easier than migrating to C/C++.

> **themusicwave said:**
> 
Also, the framework doesn't even exist for some platforms as far as I know.


Details please? And if so, so what? Remember Linux is only 2% of the desktop market, BSD even less. (Remember the OP is interested in Windows)

---

### Post by themusicwave on 2008-08-27
> **tinny said:**
> For the last 5 years I haven't seen a Windows XP install that doesn't at least have .Net 1.1. Many of Microsoft's core products require .Net. (.Net 1.1 easily provides the functionality to deliver the basic application that the OP is after)


Details please? And if so, so what? Remember Linux is only 2% of the desktop market, BSD even less. (Remember the OP is interested in Windows)

I agree windows has the lion's share.  But what about Macs?  They are gaining ground and are probably at 8-10% and rising fast.  SO even if Linux only has 2% you add that to Macs and you have 10-12%.  

That may be acceptable sometimes, but considering this is a Linux forum I figured he would want native Linux support.

I agree that MOST Windows machines have .Net, but that doesn't mean they absolutely will.  There is a very slim chance they won't.  There is an absolute chance a Mac or Linux machine won't.

Basically, by using C# you are ensuring that 10-12% of people can't run your app natively.

I guess if you only want a Windows program then C# is fine.  I had seen mentions of Linux support in the thread.  If this isn't the case and you never ever want to support anything other than Windows, then use C#.

---

### Post by Syndacate on 2008-08-29
> **Reiger said:**
> Well yes but my point is that people who actively go out there online to seek themselves an app to do what they want... These aren't the most computer illiterate users. Of course if you'd ship your app on CD's/DVD's then you can't assume that anymore -- but hey: you'd be including an installer for those anyway; so that's not the case. ;)

The program is for a forum community.  They'd know what it is, what it does, and what to expect before even downloading it.  They wouldn't be actively searching for it - it'd be in a sticky.

> **Reiger said:**
> Point 2 is that people who go out there online to seek themselves an app to do whatever they want; can repeat that feat to download SUN's JRE -- better yet: these people are likely to have installed Java before; if only for the web applets.

Again that's my idea; not neccesarily rock solid fact.

Good point, but if you read above about my target audience - you'll see it's quite different than that.  Though you're right, somebody seeking a certain program would most likely have the competence to realize that he/she needs JRE at some point or rather (some error msg, readme, or forum "help" post is bound to tell him).

[quote=themusicwave]@OP

I better understand your goals now. You simply want a standalone file with no absolutely dependencies that runs native on most any system. No polish no nothing, just the application.[/quote]

Exactly!

[quote=themusicwave]I would say to achieve this you will need to write it in C or C++ or perhaps D(no experience with it). There is simply no other way around it. With a very basic application like this, you shouldn't run into many cross platform issues.[/quote]

Yeah, I realize there shouldn't be any issues with cross platform stuff.  I don't know anything about D either, I think it's safe to say that's off the table.  I think my target at the moment is C - though I was wondering, and I'm sure this can't simply be answered in one simple post, but what's the major changes (besides a lot of library method add-ons) that C++ has that C doesn't?  I'm feeling C - it's the lightest of the languages, from what I can tell, and is pretty open in terms of platform.  Don't know anything about it though, but with a program this simple I'm going to assume that syntax isn't anything that can't be learned in a few minutes of reading.

[quote=themusicwave]You can't use C# for the same reason you cannot use Java. The user may not have the .Net Framework(or Mono) and it would be similar to downloading the JRE. Also, the framework doesn't even exist for some platforms as far as I know.[/quote]

True, but the chances of them having .NET Frame work is A LOT higher than them having JRE.  Even though a lot of computers have JRE, .NET Framework updates are an automatic update from Microsoft.  Unless somebody messed with it by removing versions in the add/remove programs interface, it should work out of the box on any up-to-date windows system.  Which begs the question of:  Would it be better to do it in C# or C?...or is C++ still involved?

[quote=themusicwave]Similar concerns come with Python, Ruby, PHP, LISP, Perl and just about every interpreted or hybrid language(JIT Compilation).[/quote]

Well I don't know anything about Ruby or LISP, but Perl IIRC is mostly used in database interface, and so if PHP is often used with MySQL DB's.  Though those are both serverside, I'm not sure how that has anything to do with what they have locally, though. ? I thought about making it as a web app, like .js or PHP (and yes, I realize JS would still require the JRE, but it'd take care of running the program) - but the problem is simply I want it to be able to be ran locally - without internet access.

PS:  What's a hybrid language?

[quote=themusicwave]I think in this case you need to just write a C or C++ program that uses nothing platform specific(ex no Windows.h) and compile it for different platforms.[/quote]

Yeah, that's what I was thinking.  I'm just trying to determine which, now.

[quote=themusicwave]The only reason I bring up so many things in my other posts, is that as you begin to write more complex programs you will run into some cross platform issues. One of the beauties of Java and Python and other languages like them is that they remove almost all of these issues.[/quote]

While you're right, Java is also very heavy.  I'm not sure how C# is though due to the integration (or lack there of?) of the .NET frame work - but the JVM can lag down some machines without fail.  That's simply something a language like C or C++ doesn't do.

Though there shouldn't be any problems with cross platform (as long as it was compiled ON that platform) for C or C++ either, should there?

Also, what does Python use?  I thought it ran out of regular libraries like C++.  It runs off a VM? - or what makes it not have cross platform problems.

The thing is, with an app this small and the major audience being windows users (probably like 95%, then like 4.9% mac users, then like .1% linux users), cross platform usability isn't exactly something I'm concerned about, though I do need to learn about it so I won't have this problem in the future with more advanced programs.

[quote=themusicwave]I would never recommend writing the same program in multiple languages for multiple platforms. You need to do it once the right way and be done with it. Especially if you want to do weekly updates.

You still have the added annoyance of having to compile the app multiple times each time you build it. But you don't have dependency worries.[/quote]

Yeah, it doesn't seem like a smart move at all - even I see that..

[quote=themusicwave]Much of programming and engineering in general is about trade offs. You trade one thing for another. In this case you give up some ease of cross platform support and gain no dependencies. As you program and engineer and build things you will run into these sorts of things. You need to weigh the choices and pick the trade off you think is best.[/quote]

Yeah, I can see now, more clearly, that most of it is trade-offs.  It seems the language most suited for this task is either C or C++ - or C#, I suppose - I know nothing when comparing the three.

[quote=tinny]For the last 5 years I haven't seen a Windows XP install that doesn't at least have .Net 1.1. Many of Microsoft's core products require .Net. (.Net 1.1 easily provides the functionality to deliver the basic application that the OP is after)

Migrating from Java to C# will be ALOT easier than migrating to C/C++.[/quote]

Yes, and Yes.  Yes from what I've seen, the .NET framework is usually all there and all intact on like 95% of daily used XP systems, IMO.  A guy once told me he could probably write all the differences between Java and C# on a 4x6 notecard, though I don't know how accurate that is.  Obviously it'd be easier to change to C#, but I'm wondering if that's the wisest move?  I don't know anything when comparing C#, C++, and C together.  I mean what do they have to offer?  C++ would have more library support I suppose than C...and C# would run natively because of .NET...but then again C++ and C would run natively just because they do that...so I don't know...

[quote=tinny]Details please? And if so, so what? Remember Linux is only 2% of the desktop market, BSD even less. (Remember the OP is interested in Windows) [/quote]

Yeah, but even so - I mean what's so bad about writing this in C or C++ and then being able to easily compile it on a linux or mac system?  Is C# really that much better that it'd be wiser to use that if the main target is windows?

[quote=themusicwave]I agree windows has the lion's share. But what about Macs? They are gaining ground and are probably at 8-10% and rising fast. SO even if Linux only has 2% you add that to Macs and you have 10-12%.[/quote]

Yeah, that's why I was wondering why C# over C++ or C (something that could also work on a mac).

[quote=themusicwave]That may be acceptable sometimes, but considering this is a Linux forum I figured he would want native Linux support.[/quote]

I see it as stupid to "*not use linux*" - the reason for this is because if you get a good, solid, distro (such as ubuntu), with good, solid, repos (such as ubuntu) - you pretty much have everything you need to do daily tasks.  And this isn't just with Ubuntu, Fedora and SuSE are also great for people that don't wanna deal with backend stuff.

I mean if you think about what the average computer user does:
- View pictures
- Listen to music
- Watch porn
- Watch movies
- Surf the web
- Check their e-mail
- make MS stuff (word, excel, ppt, etc.)

Most of that **** is handled in gnome:
- pictures = eye of gnome (and associate gwenview for .gif's)
- music (HUGE variety of things including the widely used amarok, totem, and rhythmbox)
- porn (kaffeine has a great tracking system & load time so it's great for this)
- movies (VLC)
- surf the web (FF)
- E-mail (evolution or thunderbird)
- Open Office?

That's what a BASIC computer user does - and all of that stuff is easily done on a linux system, but you don't get BSOD's and the like.  Also, anything extra is just a repo away, you don't have to pay for any of it, and best of all - it's 100% stable.

These are my views on why I use linux, why I've tried 20 bazillion flavors of it.  I do try to force it down people's throats as a concept, to see the reasoning behind it - that what they do is not THAT dependent on windows, but whether people want to use it or not is their own call.  The majority of people don't.  That's why viruses for linux and macs are at huge low - if you exclude the major security holes in windows, people who design viruses target the 90%, no use targeting the other 10 - so if I'm designing software, why not think the same way?

In any event, my useless reasoning behind why people who don't use their computers for specified tasks requiring windows (such as some 3D modeling like solidworks or Pro Engineer) should use linux for their daily **** asside..

I would make it in C or C++ so it always runs natively.  That's why I'm wondering what the advantages of writing it in C# are to C or C++ (then there's the obvious combat of C or C++).

[quote=themusicwave]I agree that MOST Windows machines have .Net, but that doesn't mean they absolutely will. There is a very slim chance they won't. There is an absolute chance a Mac or Linux machine won't.[/quote]

Yeah, but there's no absolutes in life except death and taxes.  Targeting windows users' .NET is a good deal, don't see what hypes it up from a lower level like C or C++ though.  Though it's still hitting up the big 88-90% of daily users.

[quote=themusicwave]Basically, by using C# you are ensuring that 10-12% of people can't run your app natively.[/quote]

Exactly, which begs the question of what makes C# so "attractive?"

[quote=themusicwave]I guess if you only want a Windows program then C# is fine. I had seen mentions of Linux support in the thread. If this isn't the case and you never ever want to support anything other than Windows, then use C#.[/quote]

Yeah, that's a bit extreme, but my main target is windows users.  Though I'm still trying to figure out what throws C# so high up the list above C++ and C for windows users, lol.  I still can't figure that out.  If anything I'd expect it to be worse because it uses .NET framework (sorta like a VM) instead of running natively from something built into the kernel (like C or C++ would).

---

### Post by SeanHodges on 2008-08-31
> True, but the chances of them having .NET Frame work is A LOT higher than them having JRE. Even though a lot of computers have JRE, .NET Framework updates are an automatic update from Microsoft.

I didn't receive my .NET Framework automatic update from Microsoft. Is it in Universe or Multiverse?

---

### Post by drubin on 2008-08-31
> True, but the chances of them having .NET Frame work is A LOT higher than them having JRE. Even though a lot of computers have JRE, .NET Framework updates are an automatic update from Microsoft.

When you isntall the JRE it automatically keeps you uptodate. 

> **SeanHodges said:**
> I didn't receive my .NET Framework automatic update from Microsoft. Is it in Universe or Multiverse?

lol, I think it is part of the black hole. package.

---

### Post by CptPicard on 2008-08-31
> **Syndacate said:**
> The program is for a forum community.  They'd know what it is, what it does, and what to expect before even downloading it.  They wouldn't be actively searching for it - it'd be in a sticky.


[Java Web Start]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp")...

---

### Post by drubin on 2008-08-31
> **SeanHodges said:**
> I didn't receive my .NET Framework automatic update from Microsoft. Is it in Universe or Multiverse?

> **CptPicard said:**
> [Java Web Start]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp")...

Great solution +1

---

### Post by Syndacate on 2008-09-01
> **CptPicard said:**
> [Java Web Start]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp")...

As far as I can tell, that requires the web - I was lookin for this to be a program that ran locally, or else yeah, I would have written it in JS or something of the sort.

---

### Post by CptPicard on 2008-09-01
Hmm... AFAIK it's just a deployment tool that pulls the needed JRE automagically. Do you need to go to the web page every time you want to run the app?

---

### Post by tinny on 2008-09-01
> **CptPicard said:**
> Hmm... AFAIK it's just a deployment tool that pulls the needed JRE automagically. Do you need to go to the web page every time you want to run the app?

Java web start requires that you ALREADY have a JRE installed before clicking the *.jnlp file (web start file). After clicking if you have the incorrect JRE version it will try and update it for you (I think).

So we still have the same problem of requiring the JRE to be installed correctly before we do anything.

---

### Post by CptPicard on 2008-09-01
Oh... :(

---

### Post by SeanHodges on 2008-09-02
This thread does not make any sense...

If you have found a use-case where a particular language does not fit, so you use a different language. This concept really is one of the simple parts of programming!

"A simple calculator that has no dependencies, it must be a single file that can be distributed and run on multiple architectures and platforms without needing to be deployed or any other user interaction beyond double-clicking the binary."

This particular program clearly has some requirements that Java is not meeting. Java requires that the JRE is installed on the machine, and methods of doing that require a form of deployment. So USE ANOTHER LANGUAGE! Jesus, programming languages are tools, no language meets all use cases. You should be defining the goal, then picking the language, not the other way around.

Personally, I think a trade-off would be needed for the above use case, as platforms differ so much that some kind of deployment is always required for write-once-run-anywhere solutions. 

A simple C program could be compiled for all the common architectures, and a few smarts in the hosting website/CD could make sure the correct binary is offered to the user when downloaded. This is only one option though, and assumes that the priority is for the program to be small and simple.

---

### Post by CptPicard on 2008-09-02
> **SeanHodges said:**
> 
Personally, I think a trade-off would be needed for the above use case, as platforms differ so much that some kind of deployment is always required for write-once-run-anywhere solutions. 


As I said earlier in the thread, IMO these requirements are so strict in every direction that I don't think the problem really is solvable. In particular the expectation that cross-platformness comes "for free" is unreasonable and the whole thing seems biased to prove that and if Java is unable to provide it 100% trivially, it therefore is useless as a language... :)

---

### Post by themusicwave on 2008-09-02
> **Syndacate said:**
> 
PS:  What's a hybrid language?


Hybrid is a term that basically means a language that combines both interpreted and compiled aspects.  For example in Java, Java code is compiled into Java Byte Code, which is an intermediate language.  At run time this Java Byte Code is translated on the fly or Just In Time into machine code by the virtual machine.  C# works exactly the same way.


> **Syndacate said:**
> 
While you're right, Java is also very heavy.  I'm not sure how C# is though due to the integration (or lack there of?) of the .NET frame work - but the JVM can lag down some machines without fail.  That's simply something a language like C or C++ doesn't do.

C# is nearly identical to Java in every way. I don't have exact figures, but it is probably just as "heavy" as Java.  It just doesn't seem that way because everything is already integrated into Windows.  Behind the scenes it works just like Java. 

> **Syndacate said:**
> 
Also, what does Python use?  I thought it ran out of regular libraries like C++.  It runs off a VM? - or what makes it not have cross platform problems.


Python is also a hybrid language as far as I know.  It can be compiled to a byte code, .pyc files and then those files get interpreted at run time by the python interpreter.  I believe Python is must slower than Java and C#, but development is much simpler.  Python is installed on most Linux systems bye default and comes with OS X.

> **Syndacate said:**
> 
The thing is, with an app this small and the major audience being windows users (probably like 95%, then like 4.9% mac users, then like .1% linux users), cross platform usability isn't exactly something I'm concerned about, though I do need to learn about it so I won't have this problem in the future with more advanced programs.


With C#, you are most likely cutting out 5% of your target audience.  You have to decide if that is acceptable to you.  I don' think C# works at all on Macs.

> **Syndacate said:**
> 
Yeah, that's why I was wondering why C# over C++ or C (something that could also work on a mac).

I don't know of anythign to run C# on a Mac.

> **Syndacate said:**
> 
Exactly, which begs the question of what makes C# so "attractive?"

C# has a lot of nice features like being object oriented, garbage collection, easy integration into Windows and many others. C++ has object orientation, but no garbage collection.  People mainly use C# because it is easy to write Windows applications using it.  These are cross platform in the M$ definition of "Runs on any version of Windows".

> **Syndacate said:**
> 
Yeah, that's a bit extreme, but my main target is windows users.  Though I'm still trying to figure out what throws C# so high up the list above C++ and C for windows users, lol.  I still can't figure that out.  If anything I'd expect it to be worse because it uses .NET framework (sorta like a VM) instead of running natively from something built into the kernel (like C or C++ would).

You can only target Windows with C# as far as I know.

I think the above posts really sum it all up.  Either you need to quit being so picky or give somewhere.  

You can't have everything free and easy.  Things that make life easy for users make it hard for developers.

Some work will be required somewhere to get the same app to run on Windows, OS X and Linux.  Either you do that work cross compiling or possibly writing different versions of your application, or you make the user do it an install Python or the JRE or whatever.

---

### Post by DavidBell on 2008-09-03
@OP, Sorry haven't read all the thread it's a bit long, so maybe someone has suggested this, but if it's just a simple calculator why don't you do it in javascript embedded on a web page on the local hard disk. Advantages ...

   * There's hardly a computer on the planet that won't run it,
   * should be relatively easy to convert your working java code,
   * meets 'all in one file' spec
   * meets 'just double-click the file' spec (or it can go in favourites)
   * meets 'no install' spec

On windows you can rename it ???.hta and it will open as a simple application without all the browser stuff. Don't know if there is an equivalent in Linux. In Linux there is also Gtkdialog but that's more a bash thing I think.

DB

---

### Post by Reiger on 2008-09-03
For a simple pocket-style calculator one could, of course, use a functional language. Let the compiler worry about cross-platform inconsistencies. ;)

And for this job the performance of Java will be nearly indentical to that of C# or indeed C anyways, as the real load is Event handling & Expression parsing; next in line would be the the output to the screen (including sane error messages) and some basic storage memory functionality.

Indeed, the only performance benefit you may notice with one language over another could very well be that of development time...

---

### Post by SeanHodges on 2008-09-03
> **Reiger said:**
> For a simple pocket-style calculator one could, of course, use a functional language. Let the compiler worry about cross-platform inconsistencies. ;)

And for this job the performance of Java will be nearly indentical to that of C# or indeed C anyways, as the real load is Event handling & Expression parsing; next in line would be the the output to the screen (including sane error messages) and some basic storage memory functionality.

Indeed, the only performance benefit you may notice with one language over another could very well be that of development time...

I think you're missing the point here. The given problem is not performance between languages, its to do with deployment and distribution.

What the OP wants is the cross-platform equivalent of a small .exe file that can be distributed all on its own. No dependencies, no interpretor, no VM... essentially no deployment tasks necessary for the user at all.

Think back to the days of VB6... when all you needed was the runtime DLL's that already came with Windows, and people shipped the .exe without any instructions saying "First ensure you have Python/JRE5/.NET1.1 installed". Imagine that, and then throw in the complexities of cross-platform compatibility.

My post above still stands, a simple program can be written in anything, but if you can't live with dependencies/deployment then pick a language that doesn't require them.


Edit: I like David's idea: [http://ubuntuforums.org/showpost.php?p=5717760&postcount=90](http://ubuntuforums.org/showpost.php?p=5717760&postcount=90), simple but effective.

---

### Post by Reiger on 2008-09-03
First paragraph. ;)

---

### Post by SeanHodges on 2008-09-03
> **Reiger said:**
> First paragraph. ;)

Which first paragraph? YOUR first paragraph?! The one that suggested using a functional programming language?

Name ONE functional programming language that doesn't require a runtime or interpretor to be installed, for all platforms.

The ones I know of:

Erlang - requires an Erlang interpretor. Not included in Windows, OSX, and most distro's out of the box.

Scheme - requires a Scheme interpretor. Same deal as Erlang, though I imagine a few distro's come with Guile...

XSLT - Well this is the closest we have. Running an XSLT on the provided Web browser (IE, Safari, Firefox...) However, writing even a simple program in XSLT would be a nightmare. There are definitely better options.

---

### Post by Reiger on 2008-09-03
Haskell. ;)

It can be interpreted; but it can also be compiled to an executable. ;)

---

### Post by CptPicard on 2008-09-03
I really don't understand what kind of benefit Haskell would bring to this problem even considering it's a "pocket calculator"... yeah, Haskell's syntax may resemble math but that's it. It's just a modelling decision. I don't even understand why Haskell would model this so particularly well -- just because it "calculates"? :)

Standard C compiles to little standalone executables just as well, and if we really keep it as simple as you're suggesting, there is no difference. The problems come with GUI toolkits etc, and are just going to be worse in Haskell.

---

### Post by Syndacate on 2008-09-03
> **CptPicard said:**
> Hmm... AFAIK it's just a deployment tool that pulls the needed JRE automagically. Do you need to go to the web page every time you want to run the app?

No, not at all, I wanted it to be 100% local.  As in if the internet was out, you can still utilize the program 100%.

> **tinny]Java web start requires that you ALREADY have a JRE installed before clicking the *.jnlp file (web start file). After clicking if you have the incorrect JRE version it will try and update it for you (I think).

So we still have the same problem of requiring the JRE to be installed correctly before we do anything.[/quote]

Well that would work rather well if it asked them and "helped them" DL/Install the JRE upon clicking on it.  Though I want the program to be for offline use as well...actually I don't want it to have any web "pieces" at all - stand-alone as in no internet, no extra backup-files.

(Keep thinking of a keygen)

[quote=SeanHodges]This thread does not make any sense...

If you have found a use-case where a particular language does not fit, so you use a different language. This concept really is one of the simple parts of programming!

"A simple calculator that has no dependencies, it must be a single file that can be distributed and run on multiple architectures and platforms without needing to be deployed or any other user interaction beyond double-clicking the binary."

This particular program clearly has some requirements that Java is not meeting. Java requires that the JRE is installed on the machine, and methods of doing that require a form of deployment. So USE ANOTHER LANGUAGE! Jesus, programming languages are tools, no language meets all use cases. You should be defining the goal, then picking the language, not the other way around.[/quote]

Yes, thankyou, I realized that upteen pages ago.  If you read my later posts you'll see I pretty much gave up on Java for this app, and pretty much turned to C, C#, or C++ (still trying to find help on the differences).

[quote=SeanHodges]Personally, I think a trade-off would be needed for the above use case, as platforms differ so much that some kind of deployment is always required for write-once-run-anywhere solutions.

A simple C program could be compiled for all the common architectures, and a few smarts in the hosting website/CD could make sure the correct binary is offered to the user when downloaded. This is only one option though, and assumes that the priority is for the program to be small and simple.[/quote]

That's what I was aiming for after I figured out the *truth* behind Java's agenda.  Though if I only wanted to go for Windows I'd probably go for C#...but what would be better for windows with C#, that C and C++ wouldn't have?  Or why would C be better than C++ if I decided to stay away from C# so I can compile it on different platforms?

[quote=CptPicard]As I said earlier in the thread, IMO these requirements are so strict in every direction that I don't think the problem really is solvable. In particular the expectation that cross-platformness comes "for free" is unreasonable and the whole thing seems biased to prove that and if Java is unable to provide it 100% trivially, it therefore is useless as a language...[/quote]

Please, allow me to re-iterate what I need from this program, because I have a feeling this has been dragged out so long, people are forgetting the aim, or rather, what the "requirements" are.
1)  I need it to work offline, so this excludes Java applets and JS
2)  I'd like it to run natively, so they don't have to use additional framework that they might not have such as the JRE - but if it "helps" them install it (like Java webstart), that's fine too, but that conflicts with #1 (web based).  I mean C, C#, C++ will all run (obviously exception for C#) without extra crap, so what's wrong with them?
3)  I'd LIKE it to be platform independent, but if I can only make it for windows due to my requirements being too strict, so be it.
4)  I'd like it to be end-user friendly (double click & run).

I really don't think that's a whole lot of requirements here...the way I see it, C, C++, and if I really didn't care about #3, C#, could all fit the requirements just fine...I CAN simply compile all three on their respective platforms, and they should run fine..I mean it certainly DOES seem like we've came to the conclusion that Java can't run the way I want it to, therefore isn't a good language for this - it seems Java simply blows for desktop applications without installers.

Keep in mind I'm more than willing to keep the program (if dependent on other files) in **A FOLDER**, BUT, That has to be independent of the OS.  IE. Not stored in Program Files or some other library directory of the sort on Linux.  Sort of like how Eclipse runs - no installer - pretty much just runs out of wherever you unzip the folder from.

The JAR **COULD** work fine, if I didn't KNOW from first hand experience that WinRAR and WinACE will have no problem re-associating a JAR with themselves.  I'm assuming there's no easy way to slide up in there and re-associate a JAR extension to the JRE?  Though it seems Java is pretty much outta this battle...unless somebody could make a claim as to why it's worth it?  

I initially started this thread simply trying to figure out how - but after realizing more what Java is aimed out, I really don't "require" it to be Java anymore, I'm more looking for the language best suited for the job, which seems to be one of the C's.

[quote=themusicwave]Hybrid is a term that basically means a language that combines both interpreted and compiled aspects. For example in Java, Java code is compiled into Java Byte Code, which is an intermediate language. At run time this Java Byte Code is translated on the fly or Just In Time into machine code by the virtual machine. C# works exactly the same way.[/quote]

Gotcha.  Is Hybrid code necessarily a bad thing?  I mean you'd think it'd take longer since it seems to have "2 steps" - but is it good?  bad?  (Oppose to regular languages that just compile to machine code like C).

[quote=themusicwave]C# is nearly identical to Java in every way. I don't have exact figures, but it is probably just as "heavy" as Java. It just doesn't seem that way because everything is already integrated into Windows. Behind the scenes it works just like Java.[/quote]

Yeah.  I have a friend in one of my classes that co-op'ed for MicroSoft over the summer - she said all they wrote in was C#.  So even MS interprets the .NET framework as being native, and if the computer is automatically updated correctly, and you don't have idiots trying to remove certain parts of the frame work thinking it's "unneeded" - it usually runs fine.  Though yeah, I've heard multiple times C# is almost exactly like Java.

[quote=themusicwave]Python is also a hybrid language as far as I know. It can be compiled to a byte code, .pyc files and then those files get interpreted at run time by the python interpreter. I believe Python is must slower than Java and C#, but development is much simpler. Python is installed on most Linux systems bye default and comes with OS X.[/quote]

Yeah, Python seems to be the ultimate in ***-kickery in terms of production, though I do believe it's over-kill by A LOT for this proeject.  I don't need that high level of a language.  Also, how does Python run in Win?  I'm assuming it needs a 3rd party interpreter?

[quote=themusicwave]With C#, you are most likely cutting out 5% of your target audience. You have to decide if that is acceptable to you. I don' think C# works at all on Macs.[/quote]

From what I've read, C# doesn't work at all on Macs, and has run incredibly shitty on Linux.  From what I understand, if I decide to go with C#, I'll be cutting out 10-12% of total population.  That was fine until yesterday...when I found a few people using Hardy, that I didn't know existed.  I mean it is an acceptable loss to an extent - greater good of the many over greater good of the individual - but I need to ask:  What makes C# better than C, or C++, what makes it worth the 10-12% hit in usability?  Simply the fact that it's nearly identical to Java and runs natively on Windows?

[quote=themusicwave]I don't know of anythign to run C# on a Mac.[/quote]

That particular parenthesis set was referring to C, not C#.  "*Something that could also run on a mac*" was referring to C or C++.

[quote=themusicwave]C# has a lot of nice features like being object oriented, garbage collection, easy integration into Windows and many others. C++ has object orientation, but no garbage collection. People mainly use C# because it is easy to write Windows applications using it. These are cross platform in the M$ definition of "Runs on any version of Windows".[/quote]

Gotcha, so it's great because it has so many nice features (sorta like Java), but runs natively on up-to-date windows machines.

[quote=themusicwave]You can only target Windows with C# as far as I know.

I think the above posts really sum it all up. **Either you need to quit being so picky or give somewhere**.

You can't have everything free and easy. Things that make life easy for users make it hard for developers.[/quote]

Refer to my "revised" list - I might have missed something, but that's the general gist of it.  That's too much to ask for?  Why isn't C or C++ capable of doing this?

[quote=themusicwave]Some work will be required somewhere to get the same app to run on Windows, OS X and Linux. Either you do that work cross compiling or possibly writing different versions of your application, or you make the user do it an install Python or the JRE or whatever.[/quote]

Right, I got that part - but if I choose C++ or C, what's the problem?

[quote=DavidBell]@OP, Sorry haven't read all the thread it's a bit long, so maybe someone has suggested this, but if it's just a simple calculator why don't you do it in javascript embedded on a web page on the local hard disk. Advantages ...[/quote]

I thought of this, but I also know that there's a nice chunk of pple running slow connections, including dial-up.  I rather run a local app, it's very small, hard disk space is barely a concern.

[quote=DavidBell]
* There's hardly a computer on the planet that won't run it,
* should be relatively easy to convert your working java code,
* meets 'all in one file' spec
* meets 'just double-click the file' spec (or it can go in favourites)
* meets 'no install' spec

On windows you can rename it ???.hta and it will open as a simple application without all the browser stuff. Don't know if there is an equivalent in Linux. In Linux there is also Gtkdialog but that's more a bash thing I think.

DB[/quote]

That would be good - I don't know anything about JS, but scripting languages are usually used off line, plus it would still need to be opened with the browser in order to utilize the browser's JS plugin to run...which true, can be made to run off-line, theoretically (never seen it done), but there's gotta be a reason a lot of other people don't do it.

[quote=**REVISED LIST**]
* should be relatively easy to convert your working java code, >>> At this stage, converting already written code is absolutely no problem.
* meets 'all in one file' spec >>> That spec is changed to "all in one file" -- OR -- all in one folder (see Eclipse) - not looking for something that needs additional libraries installed, but multiple files in the downloaded folder is OK, like Eclipse.  I do prefer stand-alone (as in they can actually dl an executable), but if that's what it takes, so be it.  I just want to stay away from installers for something this small.
* meets 'just double-click the file' spec (or it can go in favourites) >>> This is still a spec - end users get confused if u have to do anything other than double click a file.
* meets 'no install' spec >>> Yeah, but even Java can do that (see Eclipse)
[/quote]

[quote=Reiger]For a simple pocket-style calculator one could, of course, use a functional language. Let the compiler worry about cross-platform inconsistencies.

And for this job the performance of Java will be nearly indentical to that of C# or indeed C anyways, as the real load is Event handling & Expression parsing said:**
> 

Dev time isn't a concern.  At all.  This is due to the simplicity of this program.  Yes, anything written in C or C++ I can compile on win, mac, and linux, so that's not a big deal.  I really don't care what language it is, as long as it can do the job, getting as close to spec as possible.

[quote=SeanHodges]I think you're missing the point here. The given problem is not performance between languages, its to do with deployment and distribution.

What the OP wants is the [s]cross-platform[/s] equivalent of a small .exe file that can be distributed all on its own. No dependencies, no interpretor, no VM... essentially no deployment tasks necessary for the user at all.

No, if I have to take the ability to have it cross-platform away for the good of the most users, I will do that.  I don't care if it's "no dependencies" - I just don't like relying that end users have the JRE installed, because that's an assumption.

> **SeanHodges]Think back to the days of VB6... when all you needed was the runtime DLL's that already came with Windows, and people shipped the .exe without any instructions saying "First ensure you have Python/JRE5/.NET1.1 installed". Imagine that, and then throw in the complexities of cross-platform compatibility.[/quote]

Yeah.  Is there any way I can write a script in say...C++ to check - I mean I don't think it would be that hard - to see if the JRE is installed - then pop up a msg linking them and instructions to installing the JRE.

I mean that would be fine as well, something along the lines of:
*Run this program first, to make sure you have the proper dependencies*.

Though you still encounter the slight problem of, IF they have the JRE installed, but install WinRAR or WinACE (or any other of the god knows how many archiving programs are out there) afterwards, it'll take JAR's as archives and re-associate them.

I mean I don't have to worry about the association issue with Macs or Linux like I do with Windows, but is there any script I can write that can re-associate it with the JRE?

[quote=SeanHodges]My post above still stands, a simple program can be written in anything, but if you can't live with dependencies/deployment then pick a language that doesn't require them.[/quote]

Right, which begs the question of:  What's wrong with C++ or C?

[quote=SeanHodges]Edit: I like David's idea: [http://ubuntuforums.org/showpost.php...0&postcount=90](http://ubuntuforums.org/showpost.php...0&postcount=90), simple but effective.[/quote]

I like the idea too, but there's gotta be some major downfalls to it - if there wasn't, a lot more people would use it.  I've never even heard of that method before.  I suppose that's not saying much, but it still seems a bit outlandish, no?

[quote=Reiger]First paragraph.  said:**
> 

You're going to **NEED** to be more specific as to "which" first paragraph you're speaking of =).

[quote=SeanHodges]Name ONE functional programming language that doesn't require a runtime or interpretor to be installed, for all platforms.

What about C and C++?  I mean obviously there's tradeoffs everywhere.  I rather deal with .NET though, then the JRE, but if I can find an easy way to deal with the JRE (Which I haven't been able to) then I wouldn't care if I had to use that either.  Every "spec" I made has the ability to stretch - a lot - as long as it doesn't infringe upon the end user.

> **Reiger]
The ones I know of:

Erlang - requires an Erlang interpretor. Not included in Windows, OSX, and most distro's out of the box.

Scheme - requires a Scheme interpretor. Same deal as Erlang, though I imagine a few distro's come with Guile...

XSLT - Well this is the closest we have. Running an XSLT on the provided Web browser (IE, Safari, Firefox...) However, writing even a simple program in XSLT would be a nightmare. There are definitely better options.[/quote]

Yeah, I see what you're saying, but my specs are more of what I'm trying to achieve, not what **needs to be in stone, unconditionally**.

[quote=Reiger]Haskell.  said:**
> 

Never even heard of it.  I assume it's not mainstream by a long shot...

[quote=CptPicard]**Standard C compiles to little standalone executables just as well, and if we really keep it as simple as you're suggesting, there is no difference.** The problems come with GUI toolkits etc, and are just going to be worse in Haskell.

That's what I'm saying.  Why can't I keep this in C or C++?

---

### Post by CptPicard on 2008-09-03
> **Syndacate said:**
> 
That's what I'm saying.  Why can't I keep this in C or C++?

If you're willing to maintain multiple builds and do cross-compilation, yes, why not. But this cross-platformness doesn't come for cheap, as mentioned.

I guess the GUI toolkit would be wxWidgets, then...

---

### Post by themusicwave on 2008-09-03
@Op
I don't believe "Java simply blows for desktop applications without installers", you are just putting many restrictions on it.  As such, it doesn't meet your strict set of requirements.

However, you keep saying that with C# you are willing to make your program unrunnable for 10-12% of people.  To me that really blows.  Think about it this way, what blows more, having to download a run time environment one time or not ever being able to run a  program?  I'll take option one any day.

At this point I really think only C or C++ meet your requirements.

As the good captain said, cross compilation is not without headaches and is not free.  That is why languages like Java were created, because we programmers were sick of having to handle all the cross platform stuff.  Most of the time there is a reason things are created, usually to solve a problem.

If you applications has a GUI you need a cross platform one.  This of course may incur additional dependencies....

---

### Post by Reiger on 2008-09-03
@CptPickard: the advantage would be that even though you'd have to compile the code on multiple architectures; you still get the benefit of being able to write cross-platform *code*. Haskell on a Mac isn't any different from Haskell on a Linux or Windows box, at least as far as the *code* goes. (Which I think is going to take most of your development time anyways, seeing the app is gonna be small and use relatively few functions.)

As for a GUI; unless the OP is going to do everything from scratch this will either with C(++), Haskell or indeed most other languages I know of, incur a dependency penalty. Funny thing is that with Java it doesn't. ;)

---

### Post by DavidBell on 2008-09-03
> **Syndacate said:**
> 
That would be good - I don't know anything about JS, but scripting languages are usually used off line, plus it would still need to be opened with the browser ...


Javascript runs fine offline, only difference users will see is that it loads faster, and it will be 99.9% crossplatform out of the box. All you do is make the html page with the controls (eg edit boxes, buttons) in a <FORM> tag, and at the top of the page there is a <SCRIPT> tag where the code goes. That is it's just one file. You save that on your hard disk and it's ready to go. As mentioned in windows at least if you save it as .HTA it will open as a standalone application without the browser.

One limitation with javascript is that by default it wont let you open files on the disk if you need them, this is for security reasons.

> **Syndacate said:**
> 
That's what I'm saying.  Why can't I keep this in C or C++?

Well that's what I would do (C++ with wxWidgets, though not sure how well wx works on OSX though), but I got the feeling from the start of this thread that the reason you wanted java->exe because you weren't yet up to speed with C++. Also forgive if it's someone else but I seem to recall seeing you ask some pretty basic C++ questions here ... and I'm thinking the world may not be ready for you deploying apps that segfault and so forth.

BTW if you do use wx, you will have to static link or it will require you to do an install program for the libs.

Anyway, whatever way you choose to go I think it's time you made a decision and started coding, you could have got half a dozen claculators working in the time this thread has been running.

HTH DB

---

### Post by SeanHodges on 2008-09-04
> Java .exe help - Part II
(Topic title)

> It turns out the biggest conclusion was to package everything as a .jar archive and launch it from there - or just deal the class files and have them use CLI.

NOTE: Target is end users.

I just set up all the java equipment on a fresh Vista install. I know everybody has been arguing that .jar files are the best method out there for targeting end users - but I do believe they're simply WRONG.

> So I ask, how does Sun do it? It's obvious they use installers for the runtime environments, but the installer just places all the applications for the JVM, compiler, and other components in a bin folder - so what do they do, use a C++ launcher, or what? The programs seem to be operable in and of themselves, it's like they stuffed a bunch of java class files inside of an executable file...any idea how they set this up?

> As far as I can tell, that requires the web - I was lookin for this to be a program that ran locally, or else yeah, I would have written it in JS or something of the sort.
(Referring to Java Web Start suggestion)

> No, if I have to take the ability to have it cross-platform away for the good of the most users, I will do that. I don't care if it's "no dependencies" - I just don't like relying that end users have the JRE installed, because that's an assumption.

> Right, which begs the question of: What's wrong with C++ or C?

> I like the idea too, but there's gotta be some major downfalls to it - if there wasn't, a lot more people would use it. I've never even heard of that method before. I suppose that's not saying much, but it still seems a bit outlandish, no?
(Referring to the Javascript solution)

> What about C and C++? I mean obviously there's tradeoffs everywhere. I rather deal with .NET though, then the JRE, but if I can find an easy way to deal with the JRE (Which I haven't been able to) then I wouldn't care if I had to use that either. Every "spec" I made has the ability to stretch - a lot - as long as it doesn't infringe upon the end user.

> Yeah, I see what you're saying, but my specs are more of what I'm trying to achieve, not what needs to be in stone, unconditionally.

> Never even heard of it. I assume it's not mainstream by a long shot...
(Referring to Haskell suggestion)


It seems to me that your question is a moving target. You start by asking about the packaging and deployment in Java, then move on to providing a use case that (I suspect deliberately) doesn't fit Java, and then you start asking about the differences between C, C++ and C# - adjusting your previous use-case to shunt out any other suggestions.

I personally don't think you are actually looking for an answer, you seem to be guiding the thread into a passive-aggressive argument about how C and C++ is better than all other languages (see above quotes).

If I'm wrong, and you are genuinely looking for an answer, then I apologise, but suggest then that there are in fact 3 different threads going on here:

"How does Java packaging and deployment work, and how does this affect it's usage?" 
(this question may be defunct now, but the subject title will continue to draw people in to answer your original question.) 

"Which language would be best for creating a small client-side program that can be run in Windows (and possibly other platforms, but this is not an objective)? The program cannot require any dependencies that are not already included on the system, and an installer is not acceptable. It should be written in a mainstream language (e.g. not Haskell)"

"What benefits and disadvantages are there for using .NET over C or C++?"


> That's what I'm saying. Why can't I keep this in C or C++?

PLEASE PLEASE **PLEASE** write your specific program in C or C++! Between the two, you will have to decide whether your program will benefit from OOP.

---

### Post by nvteighen on 2008-09-04
> **SeanHodges said:**
> 
PLEASE PLEASE **PLEASE** write your specific program in C or C++! Between the two, you will have to decide whether your program will benefit from OOP.

Not agree: you can write OOP in C :)

But anyway, yes, this thread is somewhat annoying...

---

### Post by Syndacate on 2008-09-05
**Accidental post.

---

### Post by Syndacate on 2008-09-05
> **CptPicard said:**
> If you're willing to maintain multiple builds and do cross-compilation, yes, why not. But this cross-platformness doesn't come for cheap, as mentioned.

I guess the GUI toolkit would be wxWidgets, then...

I don't get it - what's so hard about cross compilation?

I FTP the source to one of my many other computers - and compile it..what am I missing?

PS @ Everybody who suggested JAR archives - I tried one on an OEM solaris system, and out of the box double clicking on it does absolutely nothing.  You still need to tell it to run the jar command.  If Solaris doesn't do it out of the box, there's no reason to think regular Linux distros will - and I already know that windows doesn't.

[quote=themusicwave]@Op
I don't believe "Java simply blows for desktop applications without installers", you are just putting many restrictions on it. As such, it doesn't meet your strict set of requirements.[/quote]

If my restrictions are way too strict, then it fails.  It's as simple as that.  When a real company produces software their restriction regiments are 10x as strict because they KNOW end users can't be having problems with it or they get persuaded away from using it..

[quote=themusicwave]However, you keep saying that with C# you are willing to make your program unrunnable for 10-12% of people. To me that really blows. Think about it this way, what blows more, having to download a run time environment one time or not ever being able to run a program? I'll take option one any day.[/quote]

You think it blows because you're one of those 10-12%.  With C# it really comes down to sacrificing 10-12% of the people for the greater good of the vast majority.  It's sort of like how Communist China works, and it's frowned upon by Americans.

[quote=themusicwave]At this point I really think only C or C++ meet your requirements.

As the good captain said, cross compilation is not without headaches and is not free. That is why languages like Java were created, because we programmers were sick of having to handle all the cross platform stuff. Most of the time there is a reason things are created, usually to solve a problem.

If you applications has a GUI you need a cross platform one. This of course may incur additional dependencies.... [/quote]

I'm trying to understand what's so hard about compiling C or C++ on other machines?  I think I'm def. missing something here.  I thought it was just a matter of moving the source code over there and compiling it there...and yeah, I think C or C++ meet my requirements, but I'm not really ready to exclude Java just yet...but the JAR is definitely out - as that simply doesn't work - even on sun's machines out of the box it doesn't work, and most pple with have JRE, but they'll also have WinRAR or WinACE making it fail.  I simply can't see a JAR release as a good one to all end users.  Though I'm not really sure I wanna out Java yet - there doesn't seem to be any other methods other than making a web applet, but that requires an online dependency :crook:.

I'm still combing over the idea of using JSmooth to make a C++ wrapper.  That idea doesn't seem bad, either.

As far as GUI's go - I'm trying to stay away from them, but I think I'll have to submit to them in the end, as there's no way to keep a terminal open from what I can tell O.o.

[quote=DavidBell]Javascript runs fine offline, only difference users will see is that it loads faster, and it will be 99.9% crossplatform out of the box. All you do is make the html page with the controls (eg edit boxes, buttons) in a <FORM> tag, and at the top of the page there is a <SCRIPT> tag where the code goes. That is it's just one file. You save that on your hard disk and it's ready to go. As mentioned in windows at least if you save it as .HTA it will open as a standalone application without the browser.[/quote]

I'll have to look more into that - but there has to be some reason why it's not more widely used offline if it's just "so great."

[quote=DavidBell]One limitation with javascript is that by default it wont let you open files on the disk if you need them, this is for security reasons.[/quote]

Ah, bummer.  This program won't require that, but that is a set-back in totality, yes.

[quote=DavidBell]Well that's what I would do (C++ with wxWidgets, though not sure how well wx works on OSX though), but I got the feeling from the start of this thread that the reason you wanted java->exe because you weren't yet up to speed with C++. Also forgive if it's someone else but I seem to recall seeing you ask some pretty basic C++ questions here ... and I'm thinking the world may not be ready for you deploying apps that segfault and so forth.[/quote]

Yes, it was me who asked some simple C++ questions here - I am NOT up to speed with C++, if you read the past thread, you'd see the reason why I wanted to do it so badly in Java is because it's the only language I'm proficient (or semi-proficient, anyway) in.  I can do basic C++, other than that, minus the lack of data-structures, it seems pretty much like Java in terms of syntaxing.  For a program this complex (or not complex) I don't fore-see me not being as proficient with C++ as I am with Java being a problem.  How nice of you to assume that just because I'm not an expert C++ programmer that I can't handle memory management.  While it is one of the more complex things to learn after transferring from Java to C++, for a program this simple, I doubt it will be a major problem.  Not to mention I'm rooming with a guy who's very good at C++, so he can look at my code if I run into mistakes.  I'm sure I can produce it without memory faults, just fine.

[quote=DavidBell]BTW if you do use wx, you will have to static link or it will require you to do an install program for the libs.[/quote]

I don't plan on using wx.

[quote=DavidBell]Anyway, whatever way you choose to go I think it's time you made a decision and started coding, you could have got half a dozen claculators working in the time this thread has been running.

HTH DB[/quote]

Right, yeah, coding without an aim - smart.

[quote=SeanHodges]It seems to me that your question is a moving target. You start by asking about the packaging and deployment in Java, then move on to providing a use case that (I suspect deliberately) doesn't fit Java, and then you start asking about the differences between C, C++ and C# - adjusting your previous use-case to shunt out any other suggestions.[/quote]

It's not really a moving target at all - but I see how you came to that conclusion.  I didn't realize Java's limitations as far as releasing to end users on a Desktop level goes.  After people started suggesting other languages, I started wondering about them, instead of Java.  The ones that you mentioned I "shunted" - we're all web based (with the exception of offline Javascript (what???)) - that was a rather initial condition.

[quote=SeanHodges]I personally don't think you are actually looking for an answer, you seem to be guiding the thread into a passive-aggressive argument about how C and C++ is better than all other languages (see above quotes).[/quote]

I'm not "guiding" the thread anywhere - I simply don't know.  I can give a **** less if C/C++ are better than other languages - I'm simply looking for pros and cons in terms of my target release group.

[quote=SeanHodges]If I'm wrong, and you are genuinely looking for an answer, then I apologise, but suggest then that there are in fact 3 different threads going on here:[/quote]

You are wrong, and apology accepted.

[quote=SeanHodges]"How does Java packaging and deployment work, and how does this affect it's usage?"
(this question may be defunct now, but the subject title will continue to draw people in to answer your original question.)[/quote]

Yes, this was my original question, the reason I say this was because Java is the language we learn here - it's the language I'm most proficient at, I want/wanted to release it to end users.

[quote=SeanHodges]"Which language would be best for creating a small client-side program that can be run in Windows (and possibly other platforms, but this is not an objective)? The program cannot require any dependencies that are not already included on the system, and an installer is not acceptable. It should be written in a mainstream language (e.g. not Haskell)"[/quote]

This arose from the realization as cpt and a few others said about Java simply not being a great language for Desktop apps targeted at end users without an installer - my point is simply at the simplicity of my program, an installer is pointless.

[quote=SeanHodges]"What benefits and disadvantages are there for using .NET over C or C++?"[/quote]

At the mention of maybe using C# (seeing as it is apparently very similar to Java) I started wondering about it - and what so special about it.

If you believe I'm trying to dictate the direction of the thread, you're simply nowhere near accurate.

Let me show you what I initially invisioned.

The program is small, very small, I estimated 30Kb, TOPS.

At this level, I invisioned the following:
User goes to site, clicks link of:
-  blahblahblah.com/prog.exe
-  *it downloads*
-  *User double clicks program after download*
-  Said program works.

That was my initial intention, that's why I compared it to the calculator program that comes standard since win 95.  I don't see how that seems like too regimented of requirements - lots of small apps are released that way, at least in my exp with windows.  ie.  atomicclocksync, pretty much all keygens, Cd-Key grabbers, etc.

It's as simple as that.  I didn't realize that trying to make Java do this would turn into a royal pig-****.  Then people started mentioning other languages (none were originally mentioned by me), and I started becoming interested in those as an alternative to what Java doesn't seem to be able to do well.

So I think you guys missed the point, which is why it seems it's a "moving target."

---

### Post by themusicwave on 2008-09-05
> **Syndacate said:**
> I don't get it - what's so hard about cross compilation?

I FTP the source to one of my many other computers - and compile it..what am I missing?


There are a few difficulties off the top of my head with cross compilation.

1) You have to have all the platforms to compile on.  That means you at least need 3 different operating systems.

2) You have to deal with little issues like Linux and OS X using / where windows user \.

3) Some Libraries are not on your platform by default, you may need to include them as external dependencies.

For something very simple, it is trivial to handle all this, however once you start including a GUI and third party libraries and other things you end up needing different builds for each system.  You also end up needing to include all those dependencies.

You don't want to include the JRE dependency, but is ok it to include a GUI dependency?  How will you make sure the user has it?  You don't want to use an installer, so that is out.

> **Syndacate said:**
> 
PS @ Everybody who suggested JAR archives - I tried one on an OEM solaris system, and out of the box double clicking on it does absolutely nothing.  You still need to tell it to run the jar command.  If Solaris doesn't do it out of the box, there's no reason to think regular Linux distros will - and I already know that windows doesn't.
:crook:.


I have WinRar on this Windows XP machine I am on now.  My Jar files still point to Java.  However, if that is your biggest concern it is quite trivial to write a C wrapper to call the command : java <YOURAPP>.jar.  But we have already gone there so lets not rehash that again.

> **Syndacate said:**
> 
If my restrictions are way too strict, then it fails.  It's as simple as that.  When a real company produces software their restriction regiments are 10x as strict because they KNOW end users can't be having problems with it or they get persuaded away from using it..
:crook:.

I work for a real company.  Everyday I write software for my company to sell to other people.  I use C#, Java, VBScript, C and Python in varying degrees.  I am writing software in Java to distribute and I wouldn't even think of doing it without an installer.  Even my C# programs that I write for work need installer, they need dozens of .dll files to be in the right place as well as images and config files and all sorts of things.  Any non trivial program needs and installer.  You aren't writing anything near a commercial grade application so it may not apply in your case.

> **Syndacate said:**
> 
You think it blows because you're one of those 10-12%.  With C# it really comes down to sacrificing 10-12% of the people for the greater good of the vast majority.  It's sort of like how Communist China works, and it's frowned upon by Americans.
:crook:.


I do think it blows for that reason.  So do the rest of the 10-12%.  Why be exclusive when you can be inclusive?  That's what I don't understand.  But that's your decision.  The point I was making is that even if Java requires 100% of people to jump through a hoop, that is better than having 12% not be able to run it at all.  That's my opinion, but it's your project so you decide what matters.

Eventually you have to realize that sometimes software has dependencies.  As a programmer you need to make sure they are there.  Now it is possible a simple command line only C or C++ program has no dependencies.  If that is the case cross compiling it should be pretty easy.

You have to realize that many of us here are used to working on large projects.  We can't help, but try to do everything in a way that works best in general.  Someday you are going to write a program that is more complex.  You will have to deal with these issues.  In most cases it is easier for you then if you deal with them now.

At this point I think you need to just get coding.  You have made up your mind already, some of us disagree, but it is your program.  You have to make a choice.  If you spend the next month arguing that won't get you very far, there comes a point where you pick what you think is best and do it.  I think you are there now.

If you think C or C++ is best then do it.  If you want to say "Windows Only" then go C#.  You know the trade offs involved, you need to decide what matters for this project and make the call.

---

### Post by mssever on 2008-09-05
> **Syndacate said:**
> 1)  I need it to work offline, so this excludes Java applets and JS
That doesn't exclude Javascript. I once wrote a [Javascript time calculator]("http://www.scottseverance.us/html/time_calculator.htm"). After a number of people e-mailed me wanting to be able to use it offline, I created a download edition. The only differences are:

[LIST=1]
[*]I bundled up everything into a single file.
[*]I serve it with a mime type that causes the browser to open a download window rather than rendering the page. Then, when people double click it they get an offline time calculator with no external dependencies.
[/LIST]

---

### Post by Reiger on 2008-09-05
Heck, you could just wrap it in a .zip and include all the files you want...

---

### Post by Tomosaur on 2008-09-05
Double clicking .Jar files works just fine for me. If you have an archive manager getting in the way, all you do is just change the assosciation (Right click > Properties > Opens with). Most users likely to even know what a .Jar file is supposed to do should be able to handle something as simple as that anyway, and there's nothing stopping you just giving them instructions.

---

### Post by DavidBell on 2008-09-06
(Pretty sure this is my last post in this thread, dont really see what can be added but ...)

> **Syndacate said:**
> there has to be some reason why it's (javascript) not more widely used offline if it's just "so great."

I never said it was so great, just it seemed to fit your original spec. It has limitations like any other language, most are for security reasons so you can open web pages like this one without worrying if they will brick your computer. But as mserver showed it can be used for simple calculator style apps, and it's very capable, if you google terms like 'javascript calculator tutorial' my guess is you will find hundreds of similar examples.

> **Syndacate said:**
> How nice of you to assume that just because I'm not an expert C++ programmer that I can't handle memory management.

Recognising, dealing with, and best *avoiding* memory issues is simply part of learning C/C++ languages. If your attitude is that you will magically rise above it then you are off to a bad start. 

It's not rocket science but you have to do it or when you release your app and it messes up for the third time, doesn't matter how minor the fault, your users will simply stop using your program. Forever. 

> **Syndacate said:**
> Right, yeah, coding without an aim - smart.

You have an aim - that is your yet to be written application. You have been given half a dozen suggestions for tools that would do the job and more than enough information to decide which is best for you. 

You need to stop obsessing over which is the *"best"* tool, it wont make any difference as far as your users are concerned.

HTH DB

---

### Post by Syndacate on 2008-09-07
> **themusicwave said:**
> There are a few difficulties off the top of my head with cross compilation.

1) You have to have all the platforms to compile on.  That means you at least need 3 different operating systems.

I have multiple instances of all 3.

> **themusicwave said:**
> 2) You have to deal with little issues like Linux and OS X using / where windows user \.

Ah, didn't even think about stuff like that...though where would that come in in the actual code?  It's not searching through any directories.

> **themusicwave said:**
> 3) Some Libraries are not on your platform by default, you may need to include them as external dependencies.

With a program this simple...what wouldn't be included?

> **themusicwave said:**
> For something very simple, it is trivial to handle all this, however once you start including a GUI and third party libraries and other things you end up needing different builds for each system.  You also end up needing to include all those dependencies.

Ah, I see what you're saying.  That makes sense, yeah.  Too many trade off's :'(.  Java seems to be the way to go to market to all, but it seems like such a pain to bring to the end user without an installer.

> **themusicwave said:**
> You don't want to include the JRE dependency, but is ok it to include a GUI dependency?  How will you make sure the user has it?  You don't want to use an installer, so that is out.

Right, you have a point.  I didn't think about that.  Though that's sorta why I'm trying to stay away from GUI's, they add extra crap..I mean very few programs (mozilla, azureus, pidgin..) are marketed for all platforms, I realize now why this is.  So I suppose the question simply is:  Why should mine be any different?

> **themusicwave said:**
> I have WinRar on this Windows XP machine I am on now.  My Jar files still point to Java.  However, if that is your biggest concern it is quite trivial to write a C wrapper to call the command : java <YOURAPP>.jar.  But we have already gone there so lets not rehash that again.

Yeah, ur right, I checked this last night, actually, you have to click "associate with all" - if you use the default, it doesn't associate with .jar's.  Though I like ur idea though - just use a wrapper in C or C++ (JSmooth comes to mind) to execute the .jar - that pretty much solves everything...so would that be the ultimate way to go, or is that bad for some reason?

> **themusicwave said:**
> I work for a real company.  Everyday I write software for my company to sell to other people.  I use C#, Java, VBScript, C and Python in varying degrees.  I am writing software in Java to distribute and I wouldn't even think of doing it without an installer.  Even my C# programs that I write for work need installer, they need dozens of .dll files to be in the right place as well as images and config files and all sorts of things.  Any non trivial program needs and installer.  You aren't writing anything near a commercial grade application so it may not apply in your case.

Yeah, that's all I'm saying, ur talking about huge companies, tons of dependencies, lots of .dll files, etc. etc. - I'm talkin about < 500 lines of code with no libraries except the util (for scanner).

> **themusicwave said:**
> I do think it blows for that reason.  So do the rest of the 10-12%.  Why be exclusive when you can be inclusive?  That's what I don't understand.  But that's your decision.  The point I was making is that even if Java requires 100% of people to jump through a hoop, that is better than having 12% not be able to run it at all.  That's my opinion, but it's your project so you decide what matters.

I see what ur saying, and that's what the creator has to weigh, I suppose, the simple inquiry of:
"Is making 100% of the people jump through hoops worth making it distributable to 100% of the population."

Sometimes I think yes, other times I think no...

> **themusicwave said:**
> Eventually you have to realize that sometimes software has dependencies.  As a programmer you need to make sure they are there.  Now it is possible a simple command line only C or C++ program has no dependencies.  If that is the case cross compiling it should be pretty easy.

What about programs like pidgin?  That's written in C IIRC and I looked at the code, it doesn't look simplistic, IMO, but it's basically tri-platform - not sure why it won't work on macs, but what would you consider that?

> **themusicwave said:**
> You have to realize that many of us here are used to working on large projects.  We can't help, but try to do everything in a way that works best in general.  Someday you are going to write a program that is more complex.  You will have to deal with these issues.  In most cases it is easier for you then if you deal with them now.

I do see what you're saying.

> **themusicwave said:**
> At this point I think you need to just get coding.  You have made up your mind already, some of us disagree, but it is your program.  You have to make a choice.  If you spend the next month arguing that won't get you very far, there comes a point where you pick what you think is best and do it.  I think you are there now.

Yeah, I'm not sure that I am there, though, because I don't know enough about the languages to completely make my decision, but that method of using a C or C++ wrapper to launch a jar file sounds really intriguing..

> **themusicwave said:**
> If you think C or C++ is best then do it.  If you want to say "Windows Only" then go C#.  You know the trade offs involved, you need to decide what matters for this project and make the call.

Yeah, I get what you mean, the only trade-off I don't get is why use C# over C++ or C.  Though I suppose that's a discussion for another day.  I think it's just a competition of Java vs the C's - though I see where the downs and ups are of each, I think.

[quote=mssever]That doesn't exclude Javascript. I once wrote a Javascript time calculator. After a number of people e-mailed me wanting to be able to use it offline, I created a download edition. The only differences are:

   1. I bundled up everything into a single file.
   2. I serve it with a mime type that causes the browser to open a download window rather than rendering the page. Then, when people double click it they get an offline time calculator with no external dependencies.[/quote]

That doesn't seem like a bad way, I suppose.  You don't see it used a lot, though.  I don't ever recall seeing it being used.  Any specific reason for that?

[quote=Reiger]Heck, you could just wrap it in a .zip and include all the files you want...[/quote]

Yeah, but then there's the end user launch issue..

[quote=Tomosaur]Double clicking .Jar files works just fine for me. If you have an archive manager getting in the way, all you do is just change the assosciation (Right click > Properties > Opens with). Most users likely to even know what a .Jar file is supposed to do should be able to handle something as simple as that anyway, and there's nothing stopping you just giving them instructions.[/quote]

How do you even select the JRE to "open with?"  You mean just run with java.exe?  It'd be nice if there was a script that could be ran to re-associate it without the end user having to do anything except run it.

[quote=DavidBell]I never said it was so great, just it seemed to fit your original spec. It has limitations like any other language, most are for security reasons so you can open web pages like this one without worrying if they will brick your computer. But as mserver showed it can be used for simple calculator style apps, and it's very capable, if you google terms like 'javascript calculator tutorial' my guess is you will find hundreds of similar examples.[/quote]

Alright, maybe I'll look into it, then.

[quote=DavidBell]Recognising, dealing with, and best avoiding memory issues is simply part of learning C/C++ languages. If your attitude is that you will magically rise above it then you are off to a bad start.[/quote]

It's not that I'd "magically rise above it" - more simply so that the response was to the intention that I simply "*wouldn't be able to do it.*"

[quote=DavidBell]It's not rocket science but you have to do it or when you release your app and it messes up for the third time, doesn't matter how minor the fault, your users will simply stop using your program. Forever.[/quote]

Possibly.  But if that was the case the majority of computer users wouldn't be using windows.  Same goes for pretty much any Mozilla app.

[quote=DavidBell]You have an aim - that is your yet to be written application. You have been given half a dozen suggestions for tools that would do the job and more than enough information to decide which is best for you.

You need to stop obsessing over which is the "best" tool, it wont make any difference as far as your users are concerned.

HTH DB[/quote]

Well I think it would make the difference - they're the ones using it, they're the ones that would have to deal with any additional things they go around to utilize the program.  I'd think it'd matter to them the most.

EDIT:
But yeah, I'm pretty sure I got the info I needed as per doing this.

I'm really digging the .jar file with a C or C++ executable wrapper idea - are there any major downfalls (aside from needing the JRE..which I guess isn't that big of a deal) I should know about, if using this method?

---

### Post by mssever on 2008-09-07
> **Syndacate said:**
> That doesn't seem like a bad way, I suppose.  You don't see it used a lot, though.  I don't ever recall seeing it being used.  Any specific reason for that?I can tell you why I did it that way. I'm not very experienced with GUI programming, and I couldn't get wxPython to give me the GUI features I wanted. But I already had a working Javascript version.

Really, I think you're over-complicating this. Why your extreme insistence on not having an installer? PuTTY is the only installer-free program I know of (but even it has an installer for convenience). Everything else has an installer. And if nearly *everybody* does something some way, then that's what all users expect--so it's not necessarily hard. (It's a lot simpler than jumping through hoops to solve a non-existent problem.) Furthermore, there are very many companies whose ability to stay in business depends on their customers' ability to install their software. Don't you suppose that they've worked out a reasonable way to accomplish that?

Based on the above, the statement that all installers are too difficult cannot possibly be true.

Something else to consider: When I first came across PuTTY, it took me a while to figure out how to install it. I looked and looked for an installer, but didn't find one (there was no installer available at the time). I didn't realize that I was supposed to just double click putty.exe. So providing an installer-less program is more likely to cause confusion than providing an installer.

---

### Post by Tomosaur on 2008-09-08
Right click the .jar file > Properties:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84564&stc=1&d=1220880353[/IMG]

Click 'Open With' tab:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84565&stc=1&d=1220880353[/IMG]

Select whichever runtime. Anybody who knows what a .jar file is supposed to do should know how to do this, and if not - just give them a readme.txt file explaining it. It should be the same process on Windows and, I assume, Mac too (although don't quote me on that, I haven't used a Mac in a looooong time).

It's really not very complicated.

Besides, if the worst comes to the worst, just include a batch script or a bash script which will launch the jar file manually.

---

### Post by themusicwave on 2008-09-08
Syndacate,

I know a lot of my last post doesn't apply directly to your program.  You were asking general questions about cross compiling so I gave general answers.

My idea of wrapping the command to run Java in an executable does work.  Then you have your actually exe as well.

However, you would still need to have the JRE on their computer for it to work.  

One thing to do is make the launcher exe check if Java isn't there.  To do this use:

```

java - version

```

On this Windows XP machine I get:

```

C:\Documents and Settings\UserName\Desktop>java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

So  you could just parse what the command returns to see if they have a JRE.  If they don't print a message saying to go and download it, providing the link.

Accompany all that with a readme or manual and you should be fine.

---

### Post by Syndacate on 2008-09-14
> **mssever said:**
> I can tell you why I did it that way. I'm not very experienced with GUI programming, and I couldn't get wxPython to give me the GUI features I wanted. But I already had a working Javascript version.

Really, I think you're over-complicating this. Why your extreme insistence on not having an installer? PuTTY is the only installer-free program I know of (but even it has an installer for convenience). Everything else has an installer. And if nearly *everybody* does something some way, then that's what all users expect--so it's not necessarily hard. (It's a lot simpler than jumping through hoops to solve a non-existent problem.) Furthermore, there are very many companies whose ability to stay in business depends on their customers' ability to install their software. Don't you suppose that they've worked out a reasonable way to accomplish that?

Lots of small programs don't have installers.  Eclipse and WinSCP are 2 more programs that I use on almost a daily basis that don't have installers.

> **mssever said:**
> Based on the above, the statement that all installers are too difficult cannot possibly be true.

It's not that installers are too difficult, it's just that it's too much of a pain in the *** for a 27KB file - people want to run a 27KB file, not install it.

> **mssever said:**
> Something else to consider: When I first came across PuTTY, it took me a while to figure out how to install it. I looked and looked for an installer, but didn't find one (there was no installer available at the time). I didn't realize that I was supposed to just double click putty.exe. So providing an installer-less program is more likely to cause confusion than providing an installer.

No offense man, but I think by **far** you're the minority in that.  If I only provide one file for download (like I plan to), a typical end user will just double click it.  They will **not** be confused and start asking where the installer is.

[quote=Tomosaur]Right click the .jar file > Properties:

Click 'Open With' tab:

Select whichever runtime. **Anybody who knows what a .jar file is supposed to do should know how to do this**, and if not - just give them a readme.txt file explaining it. It should be the same process on Windows and, I assume, Mac too (although don't quote me on that, I haven't used a Mac in a looooong time).

It's really not very complicated.

Besides, if the worst comes to the worst, just include a batch script or a bash script which will launch the jar file manually.[/quote]

Yes, but two questions, 1)  Does it show up the same on windows? - Can you select it in the open with dialog?

2)  Note the bolded text..

Have you actually been reading all this?  None of the people that are getting this are going to have the slightest clue what a .jar file is.

I still think wrapping the .jar in a C or C++ executable to launch it seems like the best idea standing...

[quote=themusicwave]Syndacate,

I know a lot of my last post doesn't apply directly to your program. You were asking general questions about cross compiling so I gave general answers.

My idea of wrapping the command to run Java in an executable does work. Then you have your actually exe as well.

However, you would still need to have the JRE on their computer for it to work.

One thing to do is make the launcher exe check if Java isn't there. To do this use:

```
java - version
```

On this Windows XP machine I get:

```
C:\Documents and Settings\UserName\Desktop>java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
```

So you could just parse what the command returns to see if they have a JRE. If they don't print a message saying to go and download it, providing the link.

Accompany all that with a readme or manual and you should be fine.[/quote]

That's an awesome idea.

Thank you.

That one idea pretty much covered all my goals.

A)  The program is stand-alone, no installer to install extra files needed, no web needed - it will run no matter where they run it from.
B)  The program is in a native executable format, so they can simply double click it - without reassociating anything.
C)  The launcher can run a JAR file as if it was a CLI, so you don't have to worry about extra archivers like winrar or winace trying to open it
D)  That check is awesome - good call - It can just check that and toss an exception with an error msg if it doesn't have the proper JRE installed.

And yup, any other questions can be answered using a read-me.

Thank you.  That's pretty much exactly what I was looking for - and runs exactly how I want it to run.  At first I was sketchy about them installing the JRE or whatever, but then I realized if I'm writing it in Java, trying to get around that is simply an unrealistic goal.

:thumbup: - Thank you everybody for your assistance in getting to the bottom of these goals.  Personally I don't think my goal was too hard, others disagree, either way the answer was provided after 2 topics and 20 something pages..

Thanks.

---

### Post by Reiger on 2008-09-14
As for Windows; by default the .JAR extension is associated with the (most up to date) JRE of SUN installed on the machine; but even in case that is manually overriden somewhere (pretty advanced user already, there...) it can still be opened from within the context menu ("Open With") entry. (And Windows does it's best to hide extensions from the user.)

So that's cleared up, I suppose.

Have fun with your C wrapper! :)

---

### Post by SeanHodges on 2008-09-14
> **Syndacate said:**
> Lots of small programs don't have installers.  Eclipse and WinSCP are 2 more programs that I use on almost a daily basis that don't have installers.

Interesting that you mention Eclipse here, which is itself a Java program. If you edit the following file:

```
vi /usr/bin/eclipse
```

You'll find that the Eclipse "binary" is little more than a BASH wrapper that launches the program jar under a pre-configured environment.

This will also be the case for Windows, Mac, etc. Although they will be distributed with their own native wrappers.

Using wrappers in this way will avoid you needing an installer. It does however mean that the resulting distribution is not a single binary, but is instead the platform-independent jar *and* a native wrapper script, often bundled into a zip file for convenience.

---

### Post by Tomosaur on 2008-09-15
> **Syndacate said:**
> 
Yes, but two questions, 1)  Does it show up the same on windows? - Can you select it in the open with dialog?


Unless the user has done something in the past, it should work just fine without having to even associate it with the JRE.

> 
2)  Note the bolded text..

Have you actually been reading all this?  None of the people that are getting this are going to have the slightest clue what a .jar file is.


I've read bits. The point was this should just work, unless that user has done something to change the association of jar files.

---

