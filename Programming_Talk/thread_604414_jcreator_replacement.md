---
title: "jcreator replacement"
date: 2007-11-06
forum: Programming Talk
---

### Post by yakovyarmo on 2007-11-06
i am looking for JCreator replacement.
i looked at jeditor and it looks good but i can i compile through it?
do you recommend on any good plugins?
and how i can install them?

---

### Post by Zugzwang on 2007-11-06
> **yakovyarmo said:**
> 
i looked at jeditor and it looks good but i can i compile through it?
do you recommend on any good plugins?
and how i can install them?

According to the web-page, you have the possibility to compile using JEditor directly. However, it doesn't state anything about plug-ins, maybe there is no support for it?

By the way, why not trying to use one of the "major" IDEs instead like Eclipse or Netbeans? If your computer is fast enough, they are quite useful.

---

### Post by yakovyarmo on 2007-11-06
my problem is pretty simple.
i am working with *.java file that i am getting from the university.
i want to compile and run just the *.java file and i dont know how to do it.

---

### Post by rbprogrammer on 2007-11-06
well, to compile it i think you need the java jdk installed and to run it i think you need the java jre installed.. are both of those installed on your computer??

also, i think jcreator is only for windows.. your running it on windows? right?

---

### Post by yakovyarmo on 2007-11-06
yes both of them are installed , and yes i need to switch to windows every time i want to use JCreator.

---

### Post by Zugzwang on 2007-11-07
So you have several possibilities:

- Use a "major" IDE like netbeans or Eclipse - Install them via the package manager
- You could try BlueJ as well: [http://www.bluej.org](http://www.bluej.org)
- You can also work without IDE from the command line. 

For the last case:

So if you've got your .java-File from your class,  copy it into a directory, open a terminal, switch to that folder and type "javac JavaFile.java" (replace JavaFile.java with the actual name of the file). It will compile the java-File for you. If the java-file has a package-declaration in its first line, you need to put in in a folder structure that fits to the package name. For example if the package name is $net.example.cool" and the Class is called CoolExample then you need to out "CoolExample.java" into a sub-directory net/example/cool and then compile it via "javac net/example/cool/CoolExample.java".

If the class you compiled has a main(String[] args)-method, you can run it afterwards by typeing "java net/example/cool/CoolExample". Note that you have to be in the correct directory so "net/example/cool/" actually refers to the position of the files.

---

### Post by rabies on 2008-05-23
it's an old thread but I'll reply anyway.. try Geany. [http://geany.uvena.de/](http://geany.uvena.de/) it's even better than jcreator :)

---

### Post by LaRoza on 2008-05-23
> **yakovyarmo said:**
> my problem is pretty simple.
i am working with *.java file that i am getting from the university.
i want to compile and run just the *.java file and i dont know how to do it.

The solution is simple, see the sticky where a thread exists on how to compile and run Java programs.

---

### Post by scphan on 2009-01-17
which ide is available for java that similar to jcreator?

- no need to create and build 'projects'
- opens any .java file and allows editing and compiling/running just that one file without needing to put it in a project

---

### Post by xxxlam on 2010-11-25
Let me change the criteria specially that this (also) my problem.

I want to compile and run a single *.java file from Ubuntu.
Yes, I installed Netbeans and some other packages to make this work, but what I need is a 'light weight' IDE. (Maybe a plug-in for GEdit)
I don't want to create a project; a single file is enough.

Many thanks guys in advance. :)

---

