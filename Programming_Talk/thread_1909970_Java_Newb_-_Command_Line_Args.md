---
title: "Java Newb - Command Line Args"
date: 2012-01-16
forum: Programming Talk
---

### Post by beegary on 2012-01-16
I am trying to adjust a program written in java and am failing miserably, I would appreciate any help.
 
The program consists of 5 .java files which are compiled using javac, the program is then executed by calling a class of one of the .java files, I think then all the other classes (? =  the other .java files) are then referenced inside this first one.
 
I would like to pass a command line argument that would be referenced in all of the classes that are executed. 
 
```
public class Test {
    public static void main (String[] args) {
        String H = args[0] }
    }
}

```

Am I headed along the right path?

---

### Post by KdotJ on 2012-01-16
You're heading in the right direction. However, in the snippet you provided, that command line argument (that you have assigned to the variable H) is only availabile inside that main method... not outside of it, and definately not available in any other class. But yes, the way you have captured the command line argument is correct.

Just as a side note, 'H' is not a good name for a variable. They should be meaningful names and in Java variables generally start with a lowercase letter. But that's not really a big issue.

Edit: That syntax is slightly wrong. The variable assignment line should end with a semicolon, and you have an extra closing brace there too.

---

### Post by beegary on 2012-01-16
Cheers Kdot
Sorry I wrote that quickly as the code is quite complex, the variable is named a bit better than that!!
Is it possible to make the variable available in other classes?
 
Would I be better off creating a new class that captures the paramter then reference it with all the others? 
Sounds more sensible but obviously would require more java knowledge.
 
I will rty to learn java properly in the future, just trying to trouble shoot soemthing...

---

### Post by dethorpe on 2012-01-16
One way (and may well be other or better ways) would be to pass the variable to the constructor of each class created (along with any other parameters), they could then store it in there own class variable and then reference it as required. e.g:
 
**Main class:**
 
```
 
public class Test {
    String commandArg;
    public static void main (String[] args) {
        commandArg = args[0] 
 
        // create object of another class and pass it the arg
        SubTest mySubTest  = new SubTest(commandArg);
    }
}

```
 
**Another class used by main class:**
 
```
 
public class SubTest {
    String commandArg;
 
    // constructor
    SubTest (String arg) {
        commandArg = arg;
    }
 
    // a method that does something
    public void myMethod() {
       // do some stuff here. Can use commandArg as required.
 
    }
}

```

---

### Post by ofnuts on 2012-01-16
> **beegary said:**
> I am trying to adjust a program written in java and am failing miserably, I would appreciate any help.
 
The program consists of 5 .java files which are compiled using javac, the program is then executed by calling a class of one of the .java files, I think then all the other classes (? =  the other .java files) are then referenced inside this first one.
 
I would like to pass a command line argument that would be referenced in all of the classes that are executed. 
 
```
public class Test {
    public static void main (String[] args) {
        String H = args[0] }
    }
}

```Am I headed along the right path?
If your arguments are of very general use (log level...), it makes sense to define system properties instead of using command line args. I.e. Instead of
```
java YourClass some_argument
```use:
```
java -Dname=value YourClass
```and then anywhere in the code you can retrieve "value" using:
```
value=System.getProperty("name")
```

---

### Post by beegary on 2012-01-16
> **ofnuts said:**
> If your arguments are of very general use (log level...), it makes sense to define system properties instead of using command line args. I.e. Instead of
```
java YourClass some_argument
```use:
```
java -Dname=value YourClass
```and then anywhere in the code you can retrieve "value" using:
```
value=System.getProperty("name")
```

Thank you all for your replies. I will give ofnuts last suggestion a go

---

### Post by imachavel on 2012-01-17
I'm still newbing it up with this:

java helloworld.java
Exception in thread "main" java.lang.NoClassDefFoundError: helloworld/java
Caused by: java.lang.ClassNotFoundException: helloworld.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: helloworld.java. Program will exit.

haha. with python I think I had it down a little better, I was trying to create variable where x = y and both are the same, for example, in terminal I type and get a return that says:

python myfirstprog.py
Success!

hahaha I'm still newbing, I forgot I changed that to a code that one is greater then the other. Oh well, if anyone has some code they want me to test, feel free to pm me, but really at your own risk as you will probably explain more to me how to implement your code then any actual code testing :popcorn:

---

### Post by ofnuts on 2012-01-17
> **imachavel said:**
> I'm still newbing it up with this:

java helloworld.java
Exception in thread "main" java.lang.NoClassDefFoundError: helloworld/java
Caused by: java.lang.ClassNotFoundException: helloworld.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: helloworld.java. Program will exit.

haha. with python I think I had it down a little better, I was trying to create variable where x = y and both are the same, for example, in terminal I type and get a return that says:

python myfirstprog.py
Success!

hahaha I'm still newbing, I forgot I changed that to a code that one is greater then the other. Oh well, if anyone has some code they want me to test, feel free to pm me, but really at your own risk as you will probably explain more to me how to implement your code then any actual code testing :popcorn:

For Java, your helloworld.java file shoul dbe compiled using "javac". This produce a helloworld.class file. You can then execute it using "java helloworld" (don't specify the ".class", its implicit here).

---

### Post by imachavel on 2012-01-17
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld.class
javac: invalid flag: helloworld.class
Usage: javac <options> <source files>
use -help for a list of possible options
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ ls
danel


no luck, I renamed it from .class to .java despite you saying not to. I got this advice:

javac <filename>
ls (you'll see a .class file)
java <class file>[FONT=Verdana]

java hellworld.java
Exception in thread "main" java.lang.NoClassDefFoundError: hellworld/java
Caused by: java.lang.ClassNotFoundException: hellworld.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: hellworld.java. Program will exit.


still nothing. errrr..... OP did you solve the problem? Don't want to derail the thread here :KS
[/FONT]

---

### Post by ofnuts on 2012-01-17
> **imachavel said:**
> danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld.class
javac: invalid flag: helloworld.class
Usage: javac <options> <source files>
use -help for a list of possible options
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ javac helloworld
error: Class names, 'helloworld', are only accepted if annotation processing is explicitly requested
1 error
danel@danel-Dimension-4700:/home$ ls
danel


no luck, I renamed it from .class to .java despite you saying not to. I got this advice:

javac <filename>
ls (you'll see a .class file)
java <class file>[FONT=Verdana]

java hellworld.java
Exception in thread "main" java.lang.NoClassDefFoundError: hellworld/java
Caused by: java.lang.ClassNotFoundException: hellworld.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: hellworld.java. Program will exit.


still nothing. errrr..... OP did you solve the problem? Don't want to derail the thread here :KS
[/FONT]

Tried "javac helloworld.java" ?

---

### Post by beegary on 2012-01-18
> **ofnuts said:**
> If your arguments are of very general use (log level...), it makes sense to define system properties instead of using command line args. I.e. Instead of
```
java YourClass some_argument
```use:
```
java -Dname=value YourClass
```and then anywhere in the code you can retrieve "value" using:
```
value=System.getProperty("name")
```
 
OFNUTS!!!! Thank you so much, that fixed my problem.
WOOOOHOOOO

---

