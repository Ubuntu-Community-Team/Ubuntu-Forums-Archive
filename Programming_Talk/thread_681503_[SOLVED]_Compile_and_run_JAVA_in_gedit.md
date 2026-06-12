---
title: "[SOLVED] Compile and run JAVA in gedit"
date: 2008-01-29
forum: Programming Talk
---

### Post by thomas_vergote on 2008-01-29
Hi,

I'm a beginning java programmer (in two days I have my exam) and I use eclipse by default as editor and compiler.
However I want to compile and run my java programs also in gedit, because I love the simplicity of gedit and for a fast check, gedit is excellent...
So I found [this thread]("http://ubuntuforums.org/showthread.php?t=414544") and I am able to compile without any problem, however, running the program just doesn't seem to work out!
This is what I get:
Quote:
> 
Running: /home/thomas/workspace/examenvoorbereiding/src/Tes tSorteren.java
--------------------
Usage: java [-options] class [args...]
(to execute a class)
or java [-options] -jar jarfile [args...]
(to execute a jar file)

where options include:
-client to select the "client" VM
-server to select the "server" VM
-hotspot is a synonym for the "client" VM [deprecated]
The default VM is client.

-cp <class search path of directories and zip/jar files>
-classpath <class search path of directories and zip/jar files>
A : separated list of directories, JAR archives,
and ZIP archives to search for class files.
-D<name>=<value>
set a system property
-verbose[:class|gc|jni]
enable verbose output
-version print product version and exit
-version:<value>
require the specified version to run
-showversion print product version and continue
-jre-restrict-search | -jre-no-restrict-search
include/exclude user private JREs in the version search
-? -help print this help message
-X print help on non-standard options
-ea[:<packagename>...|:<classname>]
-enableassertions[:<packagename>...|:<classname>]
enable assertions
-da[:<packagename>...|:<classname>]
-disableassertions[:<packagename>...|:<classname>]
disable assertions
-esa | -enablesystemassertions
enable system assertions
-dsa | -disablesystemassertions
disable system assertions
Closed: 256
I hope someone can help me get this fixed, I must be doing something wrong and I suppose its something small...

Thanks!

p.s. I posted this message already in the other thread but I think I will get better response if I post it here...

---

### Post by Lord Illidan on 2008-01-29
I noticed that there is a space here :

```
Running:  /home/thomas/workspace/examenvoorbereiding/src/Tes  tSorteren.java
```Perhaps that is the reason for it all?

Also, geany can do this compilation without having to jump through hoops as in gedit.

---

### Post by thomas_vergote on 2008-01-29
The space certainly is'nt the problem, I get the same message for all of my java files, should be something wrong with the tutorial maybe.
I will give geany a try!

---

### Post by thomas_vergote on 2008-01-29
Well, I believe I will just stick with eclipse because with geany, compilation works out also, but if I run I get:
> Exception in thread "main" java.lang.UnsupportedClassVersionError: Woordpuzzel (Unsupported major.minor version 50.0)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:30
I am certain that my code is ok, in eclipse everything just works, to bad it does'nt work in lighter programms, maybe there's some component missing?

---

### Post by Lord Illidan on 2008-01-29
What java version are you using? I use the sunjava6 myself.

---

### Post by thomas_vergote on 2008-01-29
Me to!

---

### Post by Lord Illidan on 2008-01-29
And are you testing simple java programs or big ones full of different source files?

---

### Post by thomas_vergote on 2008-01-29
I've tested small programs and bigger ones but certainly not very complicated!

---

### Post by Lord Illidan on 2008-01-29
Ok, so.. does a hello world program run? Let's test the very very basic.

---

### Post by thomas_vergote on 2008-01-29
No, it just gives the same error...
Compilation works, running not...

---

### Post by Lord Illidan on 2008-01-29
Something wrong in your code, perhaps?

How are you writing your hello world program?

---

### Post by thomas_vergote on 2008-01-29
Well the compilation works just fine: here is my code:
test.java
> 

class test {
	public static void main(String[] args) {
	System.out.println("Hello world");
	}
}


I suppose it's something more 'ubuntu'-related...

---

### Post by Lord Illidan on 2008-01-29
Did you save that as test.java ?
EDIT : Btw. when dealing with code, use PHP /PHP tags, it looks nicer.


[PHP]class test {
	public static void main(String[] args) {
	System.out.println("Hello world");
	}
}[/PHP]

---

### Post by thomas_vergote on 2008-01-29
Yes, otherwise it wouldn't compile, would it?
If I try to run in the terminal it doesn't work either. Also in the terminal, compiling works just fine... 
(ps. thanks in advance for helping!)

---

### Post by Lord Illidan on 2008-01-29
Ok, so what error do you get in the terminal when you run ```
java test
```

---

### Post by thomas_vergote on 2008-01-29
It gives just the same:
> 
thomas@thomas-laptop:~/Bureaublad$ javac test.java
thomas@thomas-laptop:~/Bureaublad$ java test
Exception in thread "main" java.lang.UnsupportedClassVersionError: test (Unsupported major.minor version 50.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)


---

### Post by Lord Illidan on 2008-01-29
Ok. I think the problem is you've got multiple JREs on your system.

Try opening synaptic and removing all jres and jdks except for sun's.

---

### Post by thomas_vergote on 2008-01-29
Wow, you are great! Everything just works now!!
Thanks a lot!

EDIT: and now java also works in firefox (the plugin did'nt work) I must have done some stupid things 3 months ago installing java and ubuntu...

---

