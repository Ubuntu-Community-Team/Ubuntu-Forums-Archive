---
title: "Java Executable Help"
date: 2008-08-01
forum: Programming Talk
---

### Post by Syndacate on 2008-08-01
I'm going to be making a small program, either in Java or C++, mostly targeted at Windows computers, though I want a version for Linux, also.

My question is simple, how do you avoid terminal for end users?

If I make a GUI (which I plan to), and compile it in windows, it'll compile to an executable, which they can just click on.  Though you can't double click a class file, so what do I do there?

I mean Azureus & Eclipse were written in Java so I'm obviously missing something, but how do I create a launcher, even if I have to create the launcher in a different language to launch the program, is there any way to do that instead of calling the JVM from terminal/command prompt.

Goals for the trivial, idiotic program:
- Application, not installer with other files
- Multi platform (I'm most interested in Windows, since that's what the majority of pple use, but I want it to work on Linux, also)

So anybody know how I can do that?  Like stuff 2 or 3 class files inside an executable?  Or am I SOL?

Which leads me to a slight digression.  If I decide temporarily, in the beta version (yeah, I'm calling it the beta version, what of it? ;) ), if I decide to have it open in terminal, is there anyway to KEEP TERMINAL OPEN?  If you've ever tried opening a program that runs in terminal or the command prompt it'll open then close - I need it to stay open and the like.  Any way to do that, either with C++ or Java?

---

### Post by tinny on 2008-08-01
> **Syndacate said:**
> I'm going to be making a small program, either in Java or C++, mostly targeted at Windows computers, though I want a version for Linux, also.

My question is simple, how do you avoid terminal for end users?

If I make a GUI (which I plan to), and compile it in windows, it'll compile to an executable, which they can just click on.  Though you can't double click a class file, so what do I do there?

I mean Azureus & Eclipse were written in Java so I'm obviously missing something, but how do I create a launcher, even if I have to create the launcher in a different language to launch the program, is there any way to do that instead of calling the JVM from terminal/command prompt.

Goals for the trivial, idiotic program:
- Application, not installer with other files
- Multi platform (I'm most interested in Windows, since that's what the majority of pple use, but I want it to work on Linux, also)

So anybody know how I can do that?  Like stuff 2 or 3 class files inside an executable?  Or am I SOL?


So you just want to turn your Java application into an exe, right? Your not interested in a Java Application installer like [WebStart]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp") or [Advanced Installer]("http://www.advancedinstaller.com/java.html")?

Have a look at [JSmooth]("http://jsmooth.sourceforge.net/"). JSmooth is used to create a native windows executable wrapper around your Java application.

> 
Which leads me to a slight digression.  If I decide temporarily, in the beta version (yeah, I'm calling it the beta version, what of it? ;) ), if I decide to have it open in terminal, is there anyway to KEEP TERMINAL OPEN?  If you've ever tried opening a program that runs in terminal or the command prompt it'll open then close - I need it to stay open and the like.  Any way to do that, either with C++ or Java?

Just launch the Java application from the common line.

```

java -jar yourapplication.jar

```

---

### Post by Syndacate on 2008-08-02
> **tinny said:**
> So you just want to turn your Java application into an exe, right? Your not interested in a Java Application installer like [WebStart]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp") or [Advanced Installer]("http://www.advancedinstaller.com/java.html")?

Have a look at [JSmooth]("http://jsmooth.sourceforge.net/"). JSmooth is used to create a native windows executable wrapper around your Java application.



Just launch the Java application from the common line.

```

java -jar yourapplication.jar

```

I'll look at JSmooth, yeah, I knwo I can launch it from the command line, but I'm trying to tailor it for end users - they're not going to want to go into the command prompt.

---

### Post by CptPicard on 2008-08-02
Frankly, I am very, very "stylistically opposed" to this idea that applications have to be .exes that can be just clicked on. It's a particularly awful thing to do for languages like Java and Python where you end up with massive exes with duplication of runtime environment code between all different applications...

Just create an installer. It will take care of end user not being forced to muck around in classpaths etc, is nicely clickable, and as a bonus, Does Things Right...

---

### Post by PaulM1985 on 2008-08-02
Hi

Your could create the jar file.  This would make the file executable (run on a double click) but it would not have the .exe extension.

I think if the users have Java installed on the computer, then this should run ok and there would be no need for end users to use the command prompt/terminal.

It depends if you just want a program that runs after being clicked on, or a program with a .exe file extension.

Hope this helps

Paul

---

### Post by drubin on 2008-08-02
WHY WHY WHY WHY WHY ?? 

Please ask your self you would like to take a platform independent language and remove one of the main reasons for using it?

Just package it as a Jar file (basically a zip file with a manifest listing details.. like main class) on most operating systems (windows,linux) they can very very easily be configured to allow them to be opened(executed) with java on "double click".

I know that if you install the JRE(at least suns version) on windows it automatically associates .jar files to do this. :).

For most linux user they will be able to get around this.. either by configuring it to do this, or by typing the command to run the jar.

I really hope you do not choose to go the exe route with Java.

---

### Post by tinny on 2008-08-02
Yeah, not good to wrap the whole application in an exe but you could do something like what Eclipse has done on windows. Eclipse has a small exe, a sort of "boot loader" for the application. I think this exe just runs the main Eclipse jar.

---

### Post by drubin on 2008-08-02
> **tinny said:**
> Yeah, not good to wrap the whole application in an exe but you could do something like what Eclipse has done on windows. Eclipse has a small exe, a sort "boot loader" for the application. I think this exe just runs the main Eclipse jar.

Ye true then for their different OS's they just have different boot loaders.

---

### Post by tinny on 2008-08-02
> **rubinboy said:**
> Ye true then for their different OS's they just have different boot loaders.

I think it is important to have something that at least looks native to the end user (the dumb user). My mother once thought a Jar file was possibility a virus. :(

---

### Post by drubin on 2008-08-02
> **tinny said:**
> I think it is important to have something that at least looks native to the end user (the dumb user). My mother once thought a Jar file was possibility a virus. :(

Funny how a "zip" file is more of a virus then a binary unreadable file!!

---

### Post by tinny on 2008-08-02
> **rubinboy said:**
> Funny how a "zip" file is more of a virus then a binary unreadable file!!

Yep, haha

I have her on Ubuntu now, so she can click all the exe's she wants!

---

### Post by Syndacate on 2008-08-03
> **CptPicard said:**
> Frankly, I am very, very "stylistically opposed" to this idea that applications have to be .exes that can be just clicked on. It's a particularly awful thing to do for languages like Java and Python where you end up with massive exes with duplication of runtime environment code between all different applications...

Just create an installer. It will take care of end user not being forced to muck around in classpaths etc, is nicely clickable, and as a bonus, Does Things Right...

I don't want to make it an installer because it's not a big thing, it's a very small program designed to be "dropped" into a folder, and then ran from there (any folder, it's an organizer of sorts).  Maybe I should switch to C++ while I'm still in the early stages?

[quote=PaulM1985]Hi

Your could create the jar file. This would make the file executable (run on a double click) but it would not have the .exe extension.

I think if the users have Java installed on the computer, then this should run ok and there would be no need for end users to use the command prompt/terminal.

It depends if you just want a program that runs after being clicked on, or a program with a .exe file extension.

Hope this helps

Paul[/quote]

Oh, that would be great.  Yeah, I don't give a **** if it's a .exe file or not, I just want people to be able to double click it to run it.  Just designing for the end user.

I guess after I complete it I'll test it on my XP part, see what's up.  Same with Vista.  I'll look into that.

[quote=rubinboy]WHY WHY WHY WHY WHY ??

Please ask your self you would like to take a platform independent language and remove one of the main reasons for using it?

Just package it as a Jar file (basically a zip file with a manifest listing details.. like main class) on most operating systems (windows,linux) they can very very easily be configured to allow them to be opened(executed) with java on "double click".

I know that if you install the JRE(at least suns version) on windows it automatically associates .jar files to do this. .

For most linux user they will be able to get around this.. either by configuring it to do this, or by typing the command to run the jar.

I really hope you do not choose to go the exe route with Java.[/quote]

Aight bro, chill the hell out =).  When I said ".exe file" - I meant double click on it and it opens, as an executable, not necessarily a ".exe" file per-se.

I haven't heard of .jar files outside of what we get our files delivered to us in for labs (archives) - I didn't know they could be configured to execute.  If that works, and windows automatically associates them with the JVM, and runs them off a double click, that's a fine route too.  I don't care what the extension is, just end user-ability.

[quote=tinny]Yeah, not good to wrap the whole application in an exe but you could do something like what Eclipse has done on windows. Eclipse has a small exe, a sort of "boot loader" for the application. I think this exe just runs the main Eclipse jar.[/quote]

Ah, I see, yeah, now that I found out that .jar's are also executable (I thought they were just an archiving format developed by sun) I'll look into that.

[quote=rubinboy]Ye true then for their different OS's they just have different boot loaders.[/quote]

Makes sense.  More languages should be like Java with the JVM, or at least an option for it.  Though it does take its toll in terms of speed.

[quote=tinny]I think it is important to have something that at least looks native to the end user (the dumb user). My mother once thought a Jar file was possibility a virus.[/quote]

Yeah, that's why my first lean was towards executables, everybody knows what they are.  Everybody knows that you double click them.  It's very common knowledge.  With .jar it isn't so much, I just used them for storage, never to execute - so I'm sure a lot of end users don't know either.

[quote=rubinboy]Funny how a "zip" file is more of a virus then a binary unreadable file!![/quote]

Yeah, but everybody knows what zip is...at least a lot of people do...okay a the majority don't, but at least they know they have to double click on them.  Step 1 for any computer I suppose.

[quote=tinny]Yep, haha

I have her on Ubuntu now, so she can click all the exe's she wants![/quote]

Yeah, I'm going to try to get my dad to get on Ubuntu or Fedora Core.  I've been around with linux distros, everything from BSD (not quite linux), to linux from scratch, to Gentoo, to Arch linux, to redhat, and back to Ubuntu again.  I like Ubuntu because it comes standard with everything you need for a daily driven operating system.  That's why I want to get more people turned onto it - if you need to game or use a windows specific program - that's where dual booting or if you have the power, VM's comes in EXTREME handy.

---

### Post by LaRoza on 2008-08-03
> **rubinboy said:**
> Funny how a "zip" file is more of a virus then a binary unreadable file!!

I believe a ".jar" is a ".zip".

---

### Post by jtuchscherer on 2008-08-03
All the Java programs I use come with a *.bat and a *.sh file. Windows user doubleclick on the bat file and unix user on the .sh file. 
In those start script files you basically have your command line call. The end user will not see it. It is perfectly hidden. Prerequisit for this method is that the environment is setup in a way that you can call java form the command line without providing the full path (because you - the software creator - don#t know where the end user did install java). you just assume it is installed and in the path). If that is a problem you can bundle you java program with a jre. The user then downloads your java program and the jre. For the sh script then you know where the jre is installed (in the program's directory).

I hope that helps.

---

### Post by Syndacate on 2008-08-03
> **jtuchscherer said:**
> All the Java programs I use come with a *.bat and a *.sh file. Windows user doubleclick on the bat file and unix user on the .sh file. 
In those start script files you basically have your command line call. The end user will not see it. It is perfectly hidden. Prerequisit for this method is that the environment is setup in a way that you can call java form the command line without providing the full path (because you - the software creator - don#t know where the end user did install java). you just assume it is installed and in the path). If that is a problem you can bundle you java program with a jre. The user then downloads your java program and the jre. For the sh script then you know where the jre is installed (in the program's directory).

I hope that helps.

Yeah, that would work, but it adds an extra step.

What do you mean bundle it with a JRE?  You mean you can include certain parts of the java library in the .jar so it's not dependent?

---

### Post by runningwithscissors on 2008-08-03
You can create a click-to-execute jar file, with the following steps:

Compile your Java classes:
```
$ javac *.java
```

Create a manifest file called MANIFEST.MF with the following contents:
```
Main-Class: <class with the main function>
Class-Path: <the classpath for your programme><carriage-return>
```
Make sure that you add a carriage return ("enter" after the last line) at the end. An example of a proper manifest file would be:
```
Main-Class: Class1
Class-Path: .

```

Run:
```
$ jar cmf MANIFEST.MF <the executable file name you want>.jar Class1.class Class2.class etc etc
```

That should produce a file (with the .jar extension) that can be executed via a click.

Also, be careful about the encoding of the manifest file. Last time I tried this, the jar programme had trouble parsing the manifest if it's not saved with the proper encoding or the proper line-break characters. Took some trial and error for that to play nice.


You can either follow these steps or use an IDE like Eclipse to create it for you. I've never created an executable jar in eclipse so I don't know how that works.

Also see this if you don't mind poring over incredibly boring documentation:
[http://java.sun.com/docs/books/tutorial/deployment/jar/index.html](http://java.sun.com/docs/books/tutorial/deployment/jar/index.html)

---

### Post by drubin on 2008-08-03
> **LaRoza said:**
> I believe a ".jar" is a ".zip".

That it is, just with the added manifest and change of extension. (for association)

---

### Post by dexter.deepak on 2008-08-03
> **CptPicard said:**
> 
Just create an installer. It will take care of end user not being forced to muck around in classpaths etc, is nicely clickable, and as a bonus, Does Things Right...

how to do that ?

---

### Post by drubin on 2008-08-03
[izpack]("http://izpack.org")

Although that requires the JRE already installed on the users system

---

### Post by jtuchscherer on 2008-08-03
> **Syndacate said:**
> 

What do you mean bundle it with a JRE?  You mean you can include certain parts of the java library in the .jar so it's not dependent?

You would release a zip file. This zip file basically contains two files and a folder. The two files are your jar file and the .sh script calling starting your program. In the folder you would deliver the jre. This is a lot of download overhead for the end user, but he can start the program without any problems.
The Database Frontend tool I am using is doing it like this (Aqua Datastudio) and my favorite IDE (InteliJ) is doing it, too. The approach with the .sh and the .bat is used by all java application servers I have seen so far (Tomcat, Glassfish, JBoss).

---

### Post by Syndacate on 2008-08-04
> **runningwithscissors said:**
> You can create a click-to-execute jar file, with the following steps:

Compile your Java classes:
```
$ javac *.java
```

Create a manifest file called MANIFEST.MF with the following contents:
```
Main-Class: <class with the main function>
Class-Path: <the classpath for your programme><carriage-return>
```
Make sure that you add a carriage return ("enter" after the last line) at the end. An example of a proper manifest file would be:
```
Main-Class: Class1
Class-Path: .

```

Run:
```
$ jar cmf MANIFEST.MF <the executable file name you want>.jar Class1.class Class2.class etc etc
```

That should produce a file (with the .jar extension) that can be executed via a click.

Also, be careful about the encoding of the manifest file. Last time I tried this, the jar programme had trouble parsing the manifest if it's not saved with the proper encoding or the proper line-break characters. Took some trial and error for that to play nice.


You can either follow these steps or use an IDE like Eclipse to create it for you. I've never created an executable jar in eclipse so I don't know how that works.

Also see this if you don't mind poring over incredibly boring documentation:
[http://java.sun.com/docs/books/tutorial/deployment/jar/index.html](http://java.sun.com/docs/books/tutorial/deployment/jar/index.html)

Alright, thank you.

[quote=jtuchscherer]You would release a zip file. This zip file basically contains two files and a folder. The two files are your jar file and the .sh script calling starting your program. In the folder you would deliver the jre. This is a lot of download overhead for the end user, but he can start the program without any problems.
The Database Frontend tool I am using is doing it like this (Aqua Datastudio) and my favorite IDE (InteliJ) is doing it, too. The approach with the .sh and the .bat is used by all java application servers I have seen so far (Tomcat, Glassfish, JBoss).[/quote]

Ah, I see.

I'll look more into that approach then.

Thank you.

---

### Post by Reiger on 2008-08-04
I would simply make an executable jar file. Using the Eclipse IDE it's really very straightforward:

[list="1"]
[*]Right click your project
[*]From the context menu that pops up: select the item that reads "Export"
[*]From the wizard that pops up: select "Java" and then "JAR file"
[*]From the wizard that pops up: select the resources your JAR file requires (you can include source code, classes, and other files), and specify the "export desintation" (where to save the archive)
[*]When that's done; click: next
[*]On the bottom of the wizard you'll see a field which points to the "main" class, initially empty: specify your main class here (you can click "browse" to navigate to the "main" class in your package)
[*]Generate the JAR file
[/list]

Now you will have a JAR file which invokes the "public static void main (String [] args)" of your "main" class, thereby launching your app. Easy, huh?

---

### Post by Syndacate on 2008-08-04
> **Reiger said:**
> I would simply make an executable jar file. Using the Eclipse IDE it's really very straightforward:

[list="1"]
[*]Right click your project
[*]From the context menu that pops up: select the item that reads "Export"
[*]From the wizard that pops up: select "Java" and then "JAR file"
[*]From the wizard that pops up: select the resources your JAR file requires (you can include source code, classes, and other files), and specify the "export desintation" (where to save the archive)
[*]When that's done; click: next
[*]On the bottom of the wizard you'll see a field which points to the "main" class, initially empty: specify your main class here (you can click "browse" to navigate to the "main" class in your package)
[*]Generate the JAR file
[/list]

Now you will have a JAR file which invokes the "public static void main (String [] args)" of your "main" class, thereby launching your app. Easy, huh?

Thank you.  I'll have to move it to my mac to package it b/c this computer's too slow and eclipse lags, lol.

---

### Post by drubin on 2008-08-05
> **Syndacate said:**
> Thank you.  I'll have to move it to my mac to package it b/c this computer's too slow and eclipse lags, lol.

If your PC can't handle eclispe try the CLI way of doing it

---

### Post by issih on 2008-08-05
Its worth noting that on ubuntu (and therefore I presume most lini distributions) jar files need to be changed to be executable (exactly like anything else), after that they run when clicked on. Interestingly they appear to have slightly odd behaviour in terms of the folder they are running in. I discovered that a jar file run from the desktop runs in the context of the home folder. That is to say that config files are read from and written to the home folder, rather than the desktop folder.

Makes a certain amount of sense, so I suspect it might actually be a deliberate feature, but it provides a point of confusion as running it from the command line doesn't function like that.

Other than that, I agree with everyone else, executable jar files are the way to go.

---

### Post by Reiger on 2008-08-05
I think the odd behaviour is more of a built-in OS thing rather than Java playing up, because AFAIK that doesn't happen anywhere else. And considering the Desktop is somewhat of a special folder; for each user there being a Desktop - even though it's not hidden: I suspect it's 'partially' reserved by your OS/Desktop-Environment?

---

### Post by Syndacate on 2008-08-06
> **rubinboy said:**
> If your PC can't handle eclispe try the CLI way of doing it

It usually can, I don't know what the big problem's been lately *shrugs*.

It lags, but it works, I can do necessary stuff, it's just not ideal at the moment.

[quote=issih]Its worth noting that on ubuntu (and therefore I presume most lini distributions) jar files need to be changed to be executable (exactly like anything else), after that they run when clicked on. Interestingly they appear to have slightly odd behaviour in terms of the folder they are running in. I discovered that a jar file run from the desktop runs in the context of the home folder. That is to say that config files are read from and written to the home folder, rather than the desktop folder.

Makes a certain amount of sense, so I suspect it might actually be a deliberate feature, but it provides a point of confusion as running it from the command line doesn't function like that.

Other than that, I agree with everyone else, executable jar files are the way to go.[/quote]

Right, but on linux I can make a .sh script to run it.  You could do something comparable with .bat files in Windows, but pple won't trust .bat files...at least not the really dumb end users :-\.

[quote=Reiger]I think the odd behaviour is more of a built-in OS thing rather than Java playing up, because AFAIK that doesn't happen anywhere else. And considering the Desktop is somewhat of a special folder; for each user there being a Desktop - even though it's not hidden: I suspect it's 'partially' reserved by your OS/Desktop-Environment?[/quote]

You lost me somewhere around the Desktop folder.

---

### Post by Syndacate on 2008-08-09
----------------------------------------------

Just for a change in topic here.

I installed Vista onto a computer today.  

I installed tons of stuff from sun's site for Java production including Eclipse IDE, JDK, and a few other goodies.

**ALL** of them come as .exe executables.

So obviously pple are wrong when they're saying "*release them in jar files*" or something similar.  .exe files are obviously the way to release to end users, if even a company that made Java does it that way, I'm going tot ake that as the norm.  People don't trust .jar files, they trust .exe's.

So does Sun use a wrapper?  Or a launcher written in C++, or what?

---

### Post by tinny on 2008-08-09
> **Syndacate said:**
> ----------------------------------------------

Just for a change in topic here.

I installed Vista onto a computer today.  

I installed tons of stuff from sun's site for Java production including Eclipse IDE, JDK, and a few other goodies.

**ALL** of them come as .exe executables.

So obviously pple are wrong when they're saying "*release them in jar files*" or something similar.  .exe files are obviously the way to release to end users, if even a company that made Java does it that way, I'm going tot ake that as the norm.  People don't trust .jar files, they trust .exe's.

So does Sun use a wrapper?  Or a launcher written in C++, or what?

This is what I was saying earlier.

> 
I think it is important to have something that at least looks native to the end user


> 
Yeah, not good to wrap the whole application in an exe but you could do something like what Eclipse has done on windows. Eclipse has a small exe, a sort of "boot loader" for the application. I think this exe just runs the main Eclipse jar.


Although the "JAR" way of doing it is the pure Java way to do it, it is not practical. The problem is you are making the assumption that your user knows what to do with the jar file (lots of people wont know that it can be executed) and that the user has their Java environment setup correctly (path to "java").

A "SH" file will be fine on linux where your user is usually a power user and knows what a script is.

I dont think a "BAT" file is a good choice. On windows your user is quite likely to be a bit dumb and will not know what a bat file is. Everyone that uses Windows should know what a exe file is....

So having said all that, yes you should write some sort of C/C++ application launcher.

You should find this thread useful.
[http://forums.sun.com/thread.jspa?messageID=4357896](http://forums.sun.com/thread.jspa?messageID=4357896)

---

### Post by Syndacate on 2008-08-09
> **tinny said:**
> This is what I was saying earlier.

Although the "JAR" way of doing it is the pure Java way to do it, it is not practical. The problem is you are making the assumption that your user knows what to do with the jar file (lots of people wont know that it can be executed) and that the user has their Java environment setup correctly (path to "java").

Yeah, I read your post earlier.  Exactly my point, I'm not expecting people to add the path variable for the java executable and execute it through CLI - most users don't even know what the command prompt is.  It's stupid to aim there.  As far as JAR files go, I do realize that they're native, but like both you and I said, they're not *normal* to most people.  Not only that, but suppose for some reason it's not defaulted to open like that - only thing ur left with is a confusing file type and a confused end user that doesn't know how to open it.  Also, if the person has WinRAR installed, there's a STRONG possibility that WinRAR took the default program for opening JAR files, as it's part of the default settings.  Therefore the JAR would NOT be executed by default.

> **tinny said:**
> A "SH" file will be fine on linux where your user is usually a power user and knows what a script is.

I'm not worried about linux users at all - I'll release it to them as a simple class file - if somebody's using linux, it's safe to assume they know basic commands of the command line, even so, as you said, an .sh script is fine for launching in linux, most linux users have used 'em.  No idea what to do for mac though.

> **tinny said:**
> I dont think a "BAT" file is a good choice. On windows your user is quite likely to be a bit dumb and will not know what a bat file is. Everyone that uses Windows should know what a exe file is....  

Yeah, I don't think it's a good choice either, that's why my original (and now current) aim is a .exe executable.

> **tinny said:**
> So having said all that, yes you should write some sort of C/C++ application launcher.

You should find this thread useful.
[http://forums.sun.com/thread.jspa?messageID=4357896](http://forums.sun.com/thread.jspa?messageID=4357896)

Alright, thank you.  I'll have a looksee there when I get some free time.

---

