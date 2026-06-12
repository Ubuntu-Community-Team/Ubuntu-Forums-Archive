---
title: "Adding java package."
date: 2007-04-19
forum: Programming Talk
---

### Post by Sportingfan on 2007-04-19
Hi, 

In order to be able to work on a school project, i have to add several classes and jar s to the java class path. How do i do this?

thx

---

### Post by bvucinic on 2007-04-19
you can use the -cp or -classpath switch directly on your command line when launching your application:
```
java -cp somejar.jar exampleClass
```

---

### Post by Sportingfan on 2007-04-19
But i want to add several classes and jars to the class path so this method is not sufficient.

---

### Post by bvucinic on 2007-04-19
if you type java -? you'll get a list of all switches, and:
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
that is, you can put a list of : separated items if you need to.

---

### Post by Sportingfan on 2007-04-19
I don't want to use packages only when i run my program, i also want them to compile my classes in eclipse.

---

### Post by bvucinic on 2007-04-20
In eclipse you have to define in
- Project
-- Properties
in Java Build Path
under the tab "Libraries": 
all the jars folders that you want in your class path

---

### Post by Sportingfan on 2007-04-21
There seems to be a problem when i want to import a folder that contains only classes, not jars.

---

### Post by samjh on 2007-04-21
Exactly what is the problem?

I don't use Eclipse, but I think if anyone is to give a useful answer to your question, they'll need more specific descriptions.

---

### Post by Ramses de Norre on 2007-04-21
Right click your Project > properties > java build path > libraries tab. There you've got different options like "add external jar", "add library" and "add class folder", so that should be pretty intuitive.

---

### Post by Sportingfan on 2007-04-27
Hi,

what i actually want to do, is to add some jars and paths to the system variable classpath. (or that is what i should do in windows) 

for example, i need to add:
folder a, b and c, d.jar, c.jar, e.jar
to the system variable classpath. This way i can also run my application within the terminal.

---

### Post by bvucinic on 2007-04-27
For bash shell:
export CLASSPATH=$CLASSPATH:/java/classes:/home/tchin/myclasses

For tcsh or csh:
set CLASSPATH = ($CLASSPATH /java/classes /home/tchin/myclasses)

These commands can either be typed at the terminal each time you login, or you can add it to your .bashrc for bash shell or .cshrc for csh or tcsh so that each time you login, the CLASSPATH is already set. The $CLASSPATH means to keep the existing CLASSPATH and then append it with the other directories listed. This is helpful if a directory is set in the CLASSPATH by the System Administrator for everyone.

Hope this helps.

---

### Post by Blacktalon on 2007-04-27
Ok, here is some more suggestions:

1.  You can get Eclipse and do it that way.

2. If you don't want Eclipse you will need to edit your "  $: .bash_profile"   and  "  $: .bashrc " then you can specify the paths under CLASSPATH, and another (I can't remember at the moment, I would need to be looking at it and can edit and tell you how in a couple of hours)

3.  Ask your professor.

4.  Say screw it, and go get drunk.


I hope this helps some,
~BT

---

### Post by Sportingfan on 2007-04-28
And what do i have to put in these files?

tx

---

### Post by smokyink on 2009-09-02
I have the same problem...the package name is [easyIO.jar  .]("http://www.uio.no/studier/emner/matnat/ifi/INF1000/h09/undervisningsmateriale/easyio.jar")
And they say that I have to add that package to :

C:\Program Files\Java\jdk1.6.0_11\jre\lib\ext\

But I use ubuntu...
So could someone help me find the path to the .jar packages in ubuntu??
I mean packages such as : java.io.*
So I can use them when  I write my exercises as such:
import easyIO.*

Please if you know help :)

---

### Post by Reiger on 2009-09-02
You download that package to some folder, use whatever IDE you have to import it from *that* folder. It will -if- your IDE does its job well enough also make sure that your executable jar (when you build it) is configured properly with that dependency.

Much better than lumping everything into the ext folder.

---

### Post by smokyink on 2009-09-03
> **Reiger said:**
> You download that package to some folder, use whatever IDE you have to import it from *that* folder. It will -if- your IDE does its job well enough also make sure that your executable jar (when you build it) is configured properly with that dependency.

Much better than lumping everything into the ext folder.

I'm sorry but I don't understand what you explained:(
what is IDE??

I'm quite a noob.

Can you possibly tell me the fastest and simplest way to do that, because I have to do my homework with it:D also I have to do it on both my Ubuntu computers and on my eee900(Xandros).

By the way I  copied the files in the directory, but when I try to compile a program it says:

ex241.java:1: package easyio does not exist
import easyio.*;
^
I work mainly with gedit and from the console...

---

### Post by Reiger on 2009-09-03
IDE is an acronym that stands for: Integrated Development Environment. Tools like Eclipse & Netbeans.

But you don't use one. Well, you can of course tinker with the classpath (-cp) variable by hand.

Say you have a directory structure like this:
```

 <project> (the project dir)
     |-<src> (the source dir)
     |-<lib> (the libraries dir)
         |-[lib1.jar] (library required in jar form)
         |-[lib2.jar] (library required in jar form)
     |-<bin> (the binary dir)

```

Then you should be able to compile/run by adding a -cp switch like this: ```
-cp ../lib/lib1.jar:../lib/lib2.jar
```

Notice how this is structured: the -cp switch is relative to whatever the directory you are invoking the java compiler/vm from which is usually the directory of your <main> class/jar file. Every dependency of your program not found in that folder/jar file must be listed on the classpath as a colon seperated list of URL's/path's referring to either .jar files or directories. (Jar files are pretty much zipped directories.)

For the purpose of running your program as a single item to (double) left-click on a desktop or otherwise invoke; you can learn how to write manifest files and create JAR files yourself. The SUN website has a good tutorial on this, and among the topics covered is how you can construct your Manifest file so that people do not have to supply a -cp switch any longer (it involves altering the value of the Classpath entry in that Manifest file).

---

### Post by smokyink on 2009-09-04
OK.I'm a bit of a noob so I have to do my exercises using easyIO.jar...

Here is more specificly what I need to do:

I ahve my source file:

```
import easyIO.*;

 class ex241
  {
   public static void main(String[] args)
    {
     Out skjerm = new Out();
     skjerm.outln('A');
     skjerm.outln("Canis familiaris betyr hund");
     skjerm.outln(15);
     skjerm.outln(3.1415, 2);  //Bruk to desimaler
    }
  }

```


When I try :
```
javac ex241.java
```

I get :
```

ex241.java:1: package easyIO does not exist
import easyIO.*;
^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
     ^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
                      ^
3 errors

```

When I try it the way that you just showed me
it compiles it...

```
 javac ex241.java -cp /home/user/Desktop/i1000/lib/easyio.jar

```

but when I try running the program I get:
```

..........:~/Desktop/i1000$ java ex241 
Exception in thread "main" java.lang.NoClassDefFoundError: easyIO/Out
    at ex241.main(ex241.java:7)
Caused by: java.lang.ClassNotFoundException: easyIO.Out
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 1 more

```

I have seen that before and dont really know what it is :confused:
Any suggestions to what to do??:shock:

---

### Post by smokyink on 2009-09-04
YEEESSS finaly I got it!!!!!\\:D/

I compile with

```
......@......:~/Desktop/i1000$ javac ex1.java -cp /home/user/Desktop/i1000/lib/easyio.jar
```


Here is how I solved my problem:

on my desktop I have:
```
Desktop/i1000

```
I created
```
Desktop/i1000/lib
```
containing package easyIO.jar

my program is in Desktop/i1000

Also I extracted easyIO.jar 
and copied the easyIO folder with its contens as such:
```
Desktop/i1000/easyIO
```

So when I run the program it finds the easyIO folder with the custom classes that It needs.

:biggrin::popcorn::KS

Thanks for all the help :KS

---

