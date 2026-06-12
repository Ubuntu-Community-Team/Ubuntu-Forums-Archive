---
title: "Unable to run program outside of NetBeans"
date: 2009-12-02
forum: Programming Talk
---

### Post by dwally89 on 2009-12-02
Hi,

I have written a program which compiles and runs in NetBeans, with no errors, and then when I do "Clean and Build", and try and run the .jar file from the command line by using the command ```
java -jar "D:\Stuff\NetBeansProjects\work\Solitaire\dist\Solitaire.jar"
``` I get the following error:
```
"Unable to read from file"
``` and when I run it with the command ```
java "D:\Stuff\NetBeansProjects\work\Solitaire\dist\Solitaire.jar"

``` I get the error: ```
Exception in thread "main" java.lang.NoClassDefFoundError: D:\Stuff\NetBeansProj
ects\work\Solitaire\dist\Solitaire/jar
Caused by: java.lang.ClassNotFoundException: D:\Stuff\NetBeansProjects\work\Soli
taire\dist\Solitaire.jar
        at java.net.URLClassLoader$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClassInternal(Unknown Source)
Could not find the main class: D:\Stuff\NetBeansProjects\work\Solitaire\dist\Sol
itaire.jar.  Program will exit.
```

Anyone know what to do?

Thanks

---

### Post by Zugzwang on 2009-12-03
.jar files are run with the "-jar" command. If you obtain some error like the one you described, try copying the .jar file to your current directory first. Maybe there's something wrong with the path.

Assuming that you try running it on a Windows machine (which you obviously do due to the windows path):
```

copy "D:\Stuff\NetBeansProjects\work\Solitaire\dist\Solitaire.jar" .
java -jar Solitaire.jar

```

If you try running it in Linux using the command above, then your path is wrong. There is no concept such as drive letters in Linux.

---

### Post by dwally89 on 2009-12-03
OK, latest:

I found out the reason for the "Unable to read from file" message.
My program requires a .txt file for which it needs to be able to write to.
When I do a clean and build, it must be copying the .txt file to the wrong location, meaning that it can't find the file, and therefore is unable to run.
After inspecting the .jar file (after all, its just an archive), I could see that the file is in the expected place, but, obviously, this is not where it is looking for the file.

My project is called "Solitaire"
My directory structure is:
1) "Solitaire", in which there are three folders "modifiedTurtle", "Solitaire" and "workingDir"
2) My main class is called "Game.class" which is located in the Solitaire subfolder
3) My .txt file is called "scores.txt" and is located in the subfolder workingDir

When I inspect the .jar file, I see the same directory structure, with the addition of a "META-INF" folder which contains one file called "MANIFEST.MF".

How can I properly refer to my file (scores.txt) in my program, so that after doing clean and build, the .jar file runs successfully?

Thanks

---

### Post by Zugzwang on 2009-12-03
> **dwally89 said:**
> 
How can I properly refer to my file (scores.txt) in my program, so that after doing clean and build, the .jar file runs successfully?


That can be done using something like this: [http://mindprod.com/jgloss/getresourceasstream.html](http://mindprod.com/jgloss/getresourceasstream.html)

---

### Post by dwally89 on 2009-12-03
Thanks, but my problem is, I don't know where it is looking in when it tries to find "scores.txt".

Where does it look by default?

---

### Post by Zugzwang on 2009-12-03
> **dwally89 said:**
> Where does it look by default?

In the current directory.

For example, if you run "java -jar ~/Test.jar" while being in the directory "/tmp", it searches for the file in "/tmp".

---

### Post by doas777 on 2009-12-03
wouldn't it always be in
```
../workingdir/scores.txt
```?

---

### Post by dwally89 on 2009-12-03
Solved

---

