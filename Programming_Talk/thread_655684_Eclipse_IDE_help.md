---
title: "Eclipse IDE help"
date: 2008-01-01
forum: Programming Talk
---

### Post by exclipse269 on 2008-01-01
I am trying to run a program I've using libraries I got from school but my eclipse keeps giving me this error 
[COLOR="Red"]Exception in thread "main" java.lang.NoClassDefFoundError: chn.util.ConsoleIO
   at Average.main([COLOR="Blue"]Average.java:7[/COLOR])[/COLOR]
I don't know what the problem since the program ran just fine in Windows and I wrote it in Ubuntu. Can someone please help with this problem.

---

### Post by nitro_n2o on 2008-01-01
When java says so it means that it can't find the .class files. 
it might be true that when u moved ur files from windows to ubuntu you forgot some class files and eclipse got confused in compiling. Or maybe you are missing the libraries in your machine. 
Other reasons to confuse eclipse might be the java version!! Make sure you are using 1.5+ java version in your machine. Finally, make sure (if you have the libraries) they are on the build path.  I didn't use eclipse for a while, but right clicking on the project folder (left hand side) well show u the place to edit the libraries u are using. 

Good luck

---

### Post by jespdj on 2008-01-02
You have to put the libraries you got from school in your classpath.

How are you running your program? From within Eclipse or from a command prompt? If it's from a command prompt, use the "-cp" or "-classpath" switch, for example:
```
java -cp schoollibrary.jar:. com.mypackage.MyProgram
```

---

### Post by exclipse269 on 2008-01-02
I have the libraries in the build path and I'm running from Eclipse. I'll check what Java version. Also another question how do you get Iced Tea to work with Eclipse like in Fedora.

---

### Post by jespdj on 2008-01-03
I've never used Iced Tea, but the normal way in Eclipse to add another JRE is to go to Window / Preferences / Java / Installed JREs, and add the JRE there.

---

### Post by TomR55 on 2008-01-03
Sounds to me that your school is using a 3rd party library that's defined a class, ConsoleIO. If my memory serves me correctly, this class was defined in one of those "packages" that educators buy to teach AP Computer Science...maybe ICT?

In any event, you need to get your hands on the JAR file, copy it onto your machine --possibly creating a directory for JAR files (I'd advise placing this in a directory outside of the workspace directory). Next, open Eclipse, navigate to the project in question. I think you need to be in Project View (or some such thing, make sure that the Projects are listed in a vertical column on the left) in order to select (by mouse clicking right) on the Project. Click on Properties ->Build Path and add an External Archive (which I think is what they call a JAR file that isn't part of the native Java distribution). Add your JAR file to your project (if you have questions, try using Eclipse Help --adding a JAR file to a Project).

Finally, navigate to the offending file(s), and import the package; it's probably something like this;

import chn.util.ConsoleIO;

I apologize for the lack of extreme detail, but you get the idea. When in doubt, check Eclipse Help files for the details. In essence, you're adding the chnutil.jar file to your Project's build path.

Good luck ..

TomR

---

