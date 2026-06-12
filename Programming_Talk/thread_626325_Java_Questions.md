---
title: "Java Questions"
date: 2007-11-28
forum: Programming Talk
---

### Post by ameba on 2007-11-28
I

---

### Post by dwhitney67 on 2007-11-29
Use javac to compile Java source code.  Eclipse is an IDE.  Debate has been raging as to what the "I" stands for.

---

### Post by ameba on 2007-11-29
did

---

### Post by ameba on 2007-11-29
so

---

### Post by ameba on 2007-11-29
a

---

### Post by jfinkels on 2007-11-29
To install the Sun Java 6 JDK, type in the terminal (Applications > Accessories > Terminal) ```
sudo aptitude install sun-java6-jdk
```

To install eclipse, type:```
sudo aptitude install eclipse
```

To compile code:```
javac Main.java
``` where "Main.java" is the name of the class file which contains the main method.

To run code, do ```
java Main
``` where "Main" is the name of the class file that contains the main method.

I have never used eclipse, so I don't know anything about it.

---

### Post by ameba on 2007-11-29
i

---

### Post by kpkeerthi on 2007-11-29
These might help. I googled for you.

[http://www.onjava.com/pub/a/onjava/2002/12/11/eclipse.html](http://www.onjava.com/pub/a/onjava/2002/12/11/eclipse.html)
[https://eclipse-tutorial.dev.java.net/eclipse-tutorial/part1.html](https://eclipse-tutorial.dev.java.net/eclipse-tutorial/part1.html)

---

### Post by keeler1 on 2007-11-29
If it has any jdk6 code that wont compile on 1.4.2 then you probably will need to install the Ubuntu restricted extras using the ADD/Remove software.  Importing is quite tricky.

The way I normally do it is create the heirarchy that eclipse would create.  So you need to create the following. (indentation indicates directory structure)

```

<workspace name>           --create a folder for the eclipse workspace
   <Project Name>               --create a project name
       <src>                           --src folder called "src"
            <package name>    --folders for each package in the project
                <java source>    --all you source from the pacage
            <other packages>  
       <bin>                           --folder called "bin"
             <package name>  --folder for each package
                 <java class's>  --class files to go in each package
            <other packages>
```

Once you have the structure.  Open eclipse.  It should ask for the workspace. Navigate to the workspace(the directory you will put your projects in that you created above).  If it doesnt ask for the workspace then go to File->Switch Worspace and change it to the appropriate directory.

Now create a new project with the same project name as the folder your src and bin folders are in.

It should bring all the files and everything in.

At this point you might get build errors because eclipse is probably using gcj instead of sun java 6.  If you were writing things requiring generics or other java 5/6 things you will need to install the Ubuntu restricted extras.

Now go to Window->Preferences->Java->Installed JREs and add sun java 6.  gcj is probably already there.  It will ask you the path.  Mine was /usr/lib/jvm/sun-java-6-1.6.03

Then go to Window->Preferences->Java->Compiler and set compliance level to 6.0. 

You should be all set.

---

### Post by ameba on 2007-11-29
i

---

### Post by jfinkels on 2007-11-29
> **ameba said:**
> i assume i use the terminal like i would use the command prompt for windows
Click on the psychocats.net link in my signature for tutorials, including a basic "What's the terminal?" tutorial.

> **ameba said:**
> i'm not sure how to complie it and run my code
I don't know about eclipse (I'm sure you can find a tutorial on eclipse out there somewhere...or see if there is built-in help), but to compile a .java file without an IDE, open the terminal and type:```
javac YourFile.java
``` where "YourFile.java" is the name of the file containing the main method. To run a .class file, type:```
java YourFile
```where "YourFile" is the name of the class containing the main method.

---

### Post by ameba on 2007-11-29
this

---

### Post by ameba on 2007-11-29
o

---

### Post by jfinkels on 2007-11-29
Hehe, depends what you consider "convenient" :D

---

### Post by CptPicard on 2007-11-29
OP, I do not understand why you insist on Eclipse on Linux when you used just a text editor and javac on Windows.

You need the JDK just as much on Linux as you needed it on Windows, and there is no need to bring Eclipse into the picture unless you specifically want to use the IDE.

Actually, stuff works on Linux almost identically to the way it did on Windows, if I understood correctly how you used to be coding there.

---

### Post by ameba on 2007-11-30
C

---

### Post by ameba on 2007-11-30
"

---

### Post by jfinkels on 2007-11-30
> **ameba said:**
> "Your set up" I mean, what do you use to author applications in java? 
JDK 6 & ......

I use 'emacs' to write Java source files, compile them with 'javac', and run them with 'java'. 

To install emacs, type in the terminal:```
sudo aptitude install emacs
```

To install the Java 6 JDK, type in the terminal" ```
sudo aptitude install sun-java6-jdk
```

To install Java 5 JDK,```
sudo aptitude install sun-java5-jdk
```

To compile .java files, type:```
javac File.java
```

To run .class files, type:```
java File
```

---

### Post by ameba on 2007-11-30
J

---

### Post by ameba on 2007-11-30
I

---

### Post by jfinkels on 2007-11-30
> **ameba said:**
> I need both jdk 6 & 5. Correct?

Most likely you only need one, if you are not restricted by a school assignment, or a job requirement or some other fringe external condition. Most likely, you want the most recent version (6).

The API documentation for version 6 is located here [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

---

### Post by ameba on 2007-11-30
when

---

### Post by jfinkels on 2007-11-30
Make sure you are in the directory that contains your file. To change your current working directory, type:```
cd *directoryname*
``` To view files in the current working directory, type:```
ls
```

Here's an intro to using the terminal and command line [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by ameba on 2007-11-30
I'm

---

### Post by pbrockway2 on 2007-11-30
It looks like your java and javac are not the same version.

You can check what you're using with:```
desktop:~/java$ javac -version
desktop:~/java$ java -version
```

---

### Post by ameba on 2007-11-30
Any

---

### Post by pbrockway2 on 2007-11-30
This is how I set things up (It may not be standard, so others may suggest something better...)

In /usr/bin there are a number of links to the java executable tools (java, javac, jar etc).  You can see them with ```

pbrockway@linuxdeskd6off:/usr/bin$ ls -l ja*
lrwxrwxrwx 1 root root    21 2007-02-25 08:36 jar -> /opt/jdk1.6.0/bin/jar
-rwxr-xr-x 1 root root 11772 2004-10-28 03:03 jasper
lrwxrwxrwx 1 root root    22 2007-02-25 08:35 java -> /opt/jdk1.6.0/bin/java
lrwxrwxrwx 1 root root    23 2007-02-25 08:35 javac -> /opt/jdk1.6.0/bin/javac
pbrockway@linuxdeskd6off:/usr/bin$       

```

The thing is to have all these links point to the correct executables.  In my case these exectables reside in /opt/jdk1.6.0/bin but in your case it will be whereever the JDK was installed.  You can safely delete any links to java, javac and jar (jasper has nothing to do with it) and replace them with links to your JDK installation.  Use the ln command for this.

---

### Post by jfinkels on 2007-12-02
> **ameba said:**
> Any suggestions on how i can fix that

i running javac 1.6.0_03  and

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

Apparently you are using an old, Blackdown version of Java. Did you install Blackdown Java in the past? When given the choice, you don't want Blackdown Java (it's a different implementation from Sun's "official" version; see more here:  [http://en.wikipedia.org/wiki/Blackdown_Java](http://en.wikipedia.org/wiki/Blackdown_Java) ).

There may be two ways of solving this problem. I believe the simplest is to uninstall Blackdown. To see if it is installed, type:```
dpkg -l | grep j2re
```If it is, then type:```
sudo aptitude remove j2re
```If you are still having compile problems after this, you might try to do:```
sudo update-alternatives --config java
``` and ```
sudo update-alternatives --config javac
```These will allow you to choose which java runtime environment binary and which java compiler the system should use, respectively. Make sure they are using the same version of Java.

---

### Post by ameba on 2007-12-02
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by ameba on 2007-12-02
o

---

