---
title: "Eclipse - Java compiling on different platforms"
date: 2009-01-23
forum: Programming Talk
---

### Post by MaindotC on 2009-01-23
Can I write and compile a project in Eclipse on a Ubuntu machine and then provide my project folder to my professor that he can compile the code on his Windows version of Eclipse and view the expected output?

Today is my first day of class in Java programming ([http://cit.morrisville.edu/courses/cita350%5Ccita350.html](http://cit.morrisville.edu/courses/cita350%5Ccita350.html))  and our professor requires that we use Eclipse.  The school issues us laptops with an XP or Vista image on a T60 or T61 (see my sig) and we are free to download and install Windows binaries of Eclipse from shared folders set up for our classes that are only accessible on campus or via VPN.  In fact, he wants us to install an earlier version of Eclipse because it supports certain plugins (this is listed on the syllabus but I can't seem to access it on his site).  I told him that I use Ubuntu and I could just use the Eclipse installation because Java is cross-platform right?

He said that wasn't really the case and you can't always take a Java program and compile and run it on different machines - in fact one student is using Vista 64-bit and he tried sending the professor a simple "Hello World" project folder but when the professor tried to compile and run it on his 32-bit machine it didn't work.

So does what I'm asking make sense and if so, can you move project folders from a Ubuntu machine to a Windows machine and have them work the same way?

---

### Post by Kilon on 2009-01-23
> **strAlan said:**
> Can I write and compile a project in 


Nothing in this world is absolute. Even "nothing" ;)

Java programs are made on the idea of cross platform. There are libraries however using functions specific to the platform. For example Apple has included several MACOS specific libraries. 

But in JAVA world these libraries are generally avoided. Java is very strict on this issue. a JAVA programm HAS to be able to run on all major platforms with NO change to the code. 

So generally yes in at least 90% of cases your code will run unchanged in all major platforms .  Do not worry about it. 

I work with JAVA in WinXP, UBUTNU and MACOSX 10.4 , I had no issues . I NEVER HAD TO CHANGE MY CODE to make it work in any of these platforms. Not only that but also looks and behaves as it was made for the specific platform. In that respect I love Java.

---

### Post by jespdj on 2009-01-23
> **strAlan said:**
> He said that wasn't really the case and you can't always take a Java program and compile and run it on different machines - in fact one student is using Vista 64-bit and he tried sending the professor a simple "Hello World" project folder but when the professor tried to compile and run it on his 32-bit machine it didn't work.
That sounds like nonsense. I wonder what strange stuff there was in that "Hello World" program.

With Java, you don't even have to recompile your code. Your compiled *.class file can be run on any operating system that has the same version of Java (or newer).

Maybe the professor had an older version of Java, and that "Hello World" program was compiled with a newer version - that might make it not work.

---

### Post by shadylookin on 2009-01-23
> **strAlan said:**
> Can I write and compile a project in Eclipse on a Ubuntu machine and then provide my project folder to my professor that he can compile the code on his Windows version of Eclipse and view the expected output?

Today is my first day of class in Java programming ([http://cit.morrisville.edu/courses/cita350%5Ccita350.html](http://cit.morrisville.edu/courses/cita350%5Ccita350.html))  and our professor requires that we use Eclipse.  The school issues us laptops with an XP or Vista image on a T60 or T61 (see my sig) and we are free to download and install Windows binaries of Eclipse from shared folders set up for our classes that are only accessible on campus or via VPN.  In fact, he wants us to install an earlier version of Eclipse because it supports certain plugins (this is listed on the syllabus but I can't seem to access it on his site).  I told him that I use Ubuntu and I could just use the Eclipse installation because Java is cross-platform right?

He said that wasn't really the case and you can't always take a Java program and compile and run it on different machines - in fact one student is using Vista 64-bit and he tried sending the professor a simple "Hello World" project folder but when the professor tried to compile and run it on his 32-bit machine it didn't work.

So does what I'm asking make sense and if so, can you move project folders from a Ubuntu machine to a Windows machine and have them work the same way?

well either your prof screwed up or his student did because java is cross platform if you're using the same jre version. The only time a java program wouldn't be cross platform compatible is if you use native libraries. 

I'm pretty sure that if you export as a java project it will work on eclipse regardless of the platform. My guess is that the student used a different version of eclipse than your professor and that's what caused the issue.

---

### Post by Kilon on 2009-01-23
> **shadylookin said:**
> well either your prof screwed up or his student did because java is cross platform if you're using the same jre version. The only time a java program wouldn't be cross platform compatible is if you use native libraries. 

I'm pretty sure that if you export as a java project it will work on eclipse regardless of the platform. My guess is that the student used a different version of eclipse than your professor and that's what caused the issue.

What I do is to take the source code and import to another project in the different platform and VIOLA!!!! it just works!

---

### Post by MaindotC on 2009-01-23
Thank you all for replying and let me clarify something.  I'm going to use Visual Studio as an example because I've done little with Eclipse and I took a VB class using Visual Studio.  When we created a project, it was stored in a specific folder and I'm assuming that folder contained everything that the VB project needed to run.  It's unfair of me to say that I would just send the source code.  I'm not sure what all those other files in a VB project are, but it's not just a text file that my instructor copied into his Visual Studio and compiled.  So now, with Eclipse, I'm assuming that a "project" will be started the same way and in order to submit the assignment to my professor I have to send him the entire project folder.

Having said that - does it change your opinion on if it SHOULD run on his Vista machine?  Kilon - I agree with you that there are always conditions and hopefull we won't run into those.  I think the professor said something about some plugins that we're going to use.  I attached a copy of the syllabus if that would make this any more understandable.

In any event I'm going to run a VM of Windoze and install the eclipse.exe on it and move the project from my host Ubuntu machine to the VM via a shared folder and see if there are any problems.  I just wanted to know what your thoughts were and hopefully it will work.

---

### Post by MaindotC on 2009-01-23
> **shadylookin said:**
> My guess is that the student used a different version of eclipse than your professor and that's what caused the issue.

He does require us to use a specific version - version 3.2.2 - and I just checked the one I have installed from the Hardy repos and it's 3.2.2.  Hopefully I'll be fine - right now I'm scrambling to study for a different class's test :D

---

### Post by Kilon on 2009-01-23
> **strAlan said:**
> He does require us to use a specific version - version 3.2.2 - and I just checked the one I have installed from the Hardy repos and it's 3.2.2.  Hopefully I'll be fine - right now I'm scrambling to study for a different class's test :D

Do not mix VB with JAVA those two beast are diffirent. VB requires its IDE in order to work properly . JAVA is totally independent and solely self reliant. Need no IDE , no other libraries , no other tools. It works as it is. Eclipse is irrelevant. Eclipse is just a tool to help you write java code faster. Eclipse version is alos irrelevant you can import any java source code.

---

### Post by MaindotC on 2009-01-23
I'm not "mixing" VB with Java - I'm just using that as an EXAMPLE and saying it's the same concept of sending my professor the folder that contains the folder!  I just want to know if I send a project folder created with Eclipse 3.2.2 on a Ubuntu machine to a Vista machine running Eclipse 3.2.2 will the professor be able to open, view, compile, and run my project on the Vista machine?

The reason I ask is that he clearly stated that he doesn't want me to send him something that he can't view and/or compile because it will result in a grade of 0.  You know what I'm just going to write up a quick program and send him the folder and see what happens.

---

### Post by Kilon on 2009-01-23
> **strAlan said:**
> I'm not "mixing" VB with Java - I'm just using that as an EXAMPLE and saying it's the same concept of sending my professor the folder that contains the folder!  I just want to know if I send a project folder created with Eclipse 3.2.2 on a Ubuntu machine to a Vista machine running Eclipse 3.2.2 will the professor be able to open, view, compile, and run my project on the Vista machine?

The reason I ask is that he clearly stated that he doesn't want me to send him something that he can't view and/or compile because it will result in a grade of 0.  You know what I'm just going to write up a quick program and send him the folder and see what happens.


Actually you do. And no it is not the same concept. 

Let me make it even more clear. 

**Your teacher does not need any Eclipse file to run your/compile/ evaluate your JAVA source code. Your JAVA source is completely autonomous. **

All you need to sent are the files with *.java extension. 

The only things that the Eclipse files will offer him is the proof that you know how to use the Eclipse to build/create/debug a Java project that is all. While a VB project will require ALL the files even the ones that the IDE creates.  I have experience these issues when I was working with Delphi which is very similar to how VB works.

Please do not be offended by my post , I offer only a kind advice  that is all. Internet can get me easily misunderstood sometimes.

---

### Post by MaindotC on 2009-01-23
> **Kilon said:**
> Actually you do. And no it is not the same concept. 

Let me make it even more clear. 

**Your teacher does not need any Eclipse file to run your/compile/ evaluate your JAVA source code. Your JAVA source is completely autonomous. **

All you need to sent are the files with *.java extension. 

The only things that the Eclipse files will offer him is the proof that you know how to use the Eclipse to build/create/debug a Java project that is all. While a VB project will require ALL the files even the ones that the IDE creates.  I have experience these issues when I was working with Delphi which is very similar to how VB works.

Please do not be offended by my post , I offer only a kind advice  that is all. Internet can get me easily misunderstood sometimes.

You have to understand with whom I'm dealing with.  He DOES need the folder because that's simply how it will make it easiest for him to grade.  I KNOW and HE KNOWS that all you need is the source but do you think he's going to copy the files into his own version of Eclipse and run them?  I even told him about how you can just use javacc from the command line - in both Linux distros and Windows - and he won't even listen to that.  The "concept" that I meant is copying the project folders - the idea of sending an entire folder - not mixing code.  To further supplement this I'm going to send you a PM.

---

### Post by Kilon on 2009-01-23
> **strAlan said:**
> You have to understand with whom I'm dealing with.  He DOES need the folder because that's simply how it will make it easiest for him to grade.  I KNOW and HE KNOWS that all you need is the source but do you think he's going to copy the files into his own version of Eclipse and run them?  I even told him about how you can just use javacc from the command line - in both Linux distros and Windows - and he won't even listen to that.  The "concept" that I meant is copying the project folders - the idea of sending an entire folder - not mixing code.  To further supplement this I'm going to send you a PM.

I have read your pm.

OMG and I thought I knew some bad teachers. Actually he does not have to copy anything the whole process is two click only. 1) Open a new Java project 2) execute the import command and import the java file.That is it. This only 5 seconds deal. 

Now it seems that you have no choice but to take the manual route. Will it work ? Have no idea. What I can tell you though is that Eclipse saves all relevant files to one folder. It puts it in what it calls a workspace folder . You will find the workspace folder this way. Make sure you have opened your project and selected your source file. Go File->Properties. In resources see "Path:" "Type:" and "Location:". 

Then just copy the project folder and you should be fine unless Eclipse save files essential to the project in other folders that I am not aware of. 

Then just email the folder to your idiot ....er.... I mean teacher. End of the story probably not the end to your pain. Good luck tolerating the guy.

---

### Post by MaindotC on 2009-01-23
I'll try it out in the VM.  Building an XP VM right now :D

---

### Post by MaindotC on 2009-02-04
I turned in my first assignment and although it wasn't finished, my professor was able to view the contents of the project folder and my code on his Vista machine so I'm guessing we're good there.

Today I ran into a bit of a problem.  We're beginning to learn how to connect to databases.  I'm familiar with connecting to a MySQL db but he wants us to use MS Database & Access.  He showed us how to create a database in our /workspace folder with the mdb and accdb drivers.  I can create a database using Open Office in that folder (/workspace/TrucksAndCargo/Database) so I dunno what I'm going to do about the MS Database & Access stuff.  I'll keep you posted but thought it would be interesting to share with you.

---

