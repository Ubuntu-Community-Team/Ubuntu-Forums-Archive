---
title: "java compilation problem"
date: 2008-05-10
forum: Programming Talk
---

### Post by evaristegalois on 2008-05-10
I just installed NetBeans 5.5 to learn how to write GUI programs. So far I am having a lot of fun. There is one thing that bothers me, however. I put together a program that runs successfully inside NetBeans but when I try to compile the .java file on the command line I get lots of error messages that all look like this:

> AddCheque.java:137: package org.jdesktop.layout does not exist org.jdesktop.layout.GroupLayout layout = new org.jdesktop.layout.GroupLayout(getContentPane());

And even when I try to just run the class file on the command line that NetBeans produced without a hitch I get the following error message:

> Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/layout/GroupLayout$Group

What's happening and how can I make these programs work on the command line (where obviously I need them if I want to use them elsewhere)?

---

### Post by NormR2 on 2008-05-10
You need to set the -classpath option to point to the jar file that contains the missing file/classes such as: org.jdesktop.layout....

Sorry, I don't know netbeans to help you find where it hides the jar files it uses.

Norm

---

### Post by evaristegalois on 2008-05-12
All right. I searched for the jar file (org-jdesktop-layout.jar) and found it in /usr/share/netbeans/5.5/platform6/modules/. I ran the command 

> CLASSPATH=/usr/share/netbeans/5.5/platform6/modules/; export CLASSPATH

to add the jar files to my CLASSPATH. echo $CLASSPATH now renders

> /usr/share/netbeans/5.5/platform6/modules/


The error messages remain as described above.

> package org.jdesktop.layout does not exist
        org.jdesktop.layout.GroupLayout layout = new org.jdesktop.layout.GroupLayout(getContentPane());


---

### Post by Tomosaur on 2008-05-12
> **evaristegalois said:**
> I just installed NetBeans 5.5 to learn how to write GUI programs. So far I am having a lot of fun. There is one thing that bothers me, however. I put together a program that runs successfully inside NetBeans but when I try to compile the .java file on the command line I get lots of error messages that all look like this:


And even when I try to just run the class file on the command line that NetBeans produced without a hitch I get the following error message:



What's happening and how can I make these programs work on the command line (where obviously I need them if I want to use them elsewhere)?

I think this is an issue with deprecation between Java 6 and Java 5 (well, a 'modification', if you want to call it that).

What you need to do is to the following:
1: Create a directory in the 'dist' directory if your netBeans project, and call it 'lib'.
2: Search for, and copy the following two files to this lib directory:
```
org-jdesktop-layout.jar
swing-layout-1.0.1.jar (This may be somewhere in the .eclipse directory of your home directory.)
```3: Try to run the program in the dist directory via the command-line - it should now work. Compiling the program from the command line is a different story - but since you've built the project with netBeans, you should be using Ant rather than just using the 'javac' command. Go to the main project directory via the command line (it should contain a file called 'build.xml'), and then just type 'ant' - your project should then be compiled correctly.

Generally speaking, if you're going to develop your project (particularly more complex projects) via an IDE such as netBeans, but want to distribute it and compile it on different machines, you should use Ant - as it makes life a hell of a lot easier.

If you want to provide a build of your software, you will need to copy the entire 'dist' directory (including your new 'lib' subdirectory). I think you can get netBeans to include the required libraries in the distributable .jar file (Or even modify the build.xml file so that Ant does this for you regardless of the IDE you're using), but you'll have to read up on how to do that yourself as I'm not 100% sure.

---

### Post by NormR2 on 2008-05-12
I guess I need to be more explicit.
To use the -classpath option of the javac command, enter:

```
javac -classpath  /usr/share/netbeans/5.5/platform6/modules/org-jdesktop-layout.jar
<java-source>
```

Your setting of the CLASSPATH envir var didn't give the jar file filename. The javac command doesn't know to look in a folder and find any and all jar files to search thru to resolve references.
You must tell the javac command which jar files to look in.

When you post error messages, please copy the full text of what you entered and the error messages from the command. Seeing the whole thing help[LEFT][/LEFT]s understand what is wrong.

---

### Post by marco.kellershoff on 2008-10-29
I don't know if this fits in here, but I had nearly the same error message when trying to make a executable.jar file from my .java program out of eclipse (myeclipse) and as a java-newbie I googled my *** off..

I tried thousands of methods.. nothing worked for me.. maybe because I am to dumb to understand what the posters want me (or in this case, the original thread-starter) to do..

After hours of trying, I found a method that worked for me.. hopefully for all other java-newbies out there too:

In Eclipse we do have a a so called Package Explorer, where the Projects are listed.

In my project "JavaBlubb" there are three subfolders "src", "JRE...", "Refere..." and "lib".. what we need is the only the src directory.. where my .java is located..

So we are going to make a .jar.file by clicking (in the menu-bar)
"FILE" -> "EXPORT" -> "JAVA" -> "JAR FILE" click on "NEXT"

Click through the tree-navigation an search your .java application and tick it..

After that your going to tick the following options on:
- Export generated class files and ressources
- Export java source files and ressources (not necessary)

Select the export location of your .jar file now.

- Compress the contents of the .jar file
- Add directory entries

Click on "NEXT"

Tick the following options:
- Export class files with compile errors
- Export class files with compile warnings

Click on "NEXT"

Tick the following options:
- Generate the manifest file
- - Save the manifest in the workspace
- - Select the save path for your manifest file
- Seal the JAR
- Select the class of the application entry point:
- - Browse the class and select it

Click on finish

Now we have a MANIFEST file.. that file needs to be edited.. we can do that by opening it with Eclipse out of the package explorer..

Add the following line in the manifest file:
```
Class-Path: lib/swing-layout-1.0.2.jar
```

and make sure you have an empty line in the manifest file at the end...

Now you have to repeat the same procedure as mentioned above, but at the point where you can choose between generating a MANIFEST file or using an existing MANIFEST file from the workspace, you have to choose the edited MANIFEST file... and hit finish..

All we have to do now:

Download the libary "swing-layout-1.0.2.jar" (try to hit [google]("http://www.google.com/search?q=swing-layout-1.0.2.jar") for that - actually I found it [here]("http://www.ibiblio.org/maven/net.java.dev.swing-layout/jars/"), but I cannot guarantee that it'll stay there, so try to hit google, if this link isn't working for you anymore..) and save it to a folder called "lib" in the same directory where your generated JAR file is located.. 

That's all folks :)

---

