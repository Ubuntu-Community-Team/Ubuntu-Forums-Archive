---
title: "Java Help Cant Run Programs on Terminal"
date: 2011-08-20
forum: Programming Talk
---

### Post by briigga on 2011-08-20
Hi Everyone

Im having trouble running a java program in the terminal..all googled out..ive seen plenty of people with a similar problem but i cant seem to solve it.

Im using Netbeans and created a simple CashRegisterTester.java file and the class one as well. The program works fine in the IDE. 

[COLOR=Red]Exception in thread "main" java.lang.NoClassDefFoundError: CashRegisterTester
Caused by: java.lang.ClassNotFoundException: CashRegisterTester
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)[/COLOR]

[COLOR=Black]
Am I attempting to run java CashRegisterTester from the wrong directory? I am attempting it from ~/NetBeansProjects/BigJava/src/cashregister$  

[/COLOR][COLOR=Black]where cashregister is the name of my package and my .java files are in there... the .class files are located in ~/NetBeansProjects/BigJava/build/classes/cashregister$

**which by the way is where netbeans decided to put them..im a new java developer and have no idea if there is an easier way to save my files..maybe keep java and class files in a same folder.**

but if i try to run java CashRegisterTester from that dir i get:[/COLOR]


[COLOR=Red]Exception in thread "main" java.lang.NoClassDefFoundError: CashRegisterTester (wrong name: cashregister/CashRegisterTester)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: CashRegisterTester. Program will exit.[/COLOR]

[COLOR=Black]i read somewhere online that this second error meant i had to write: java cashregister.CashRegister but that also did not work.


anyone? been going at this for a while.


Thanks.
[/COLOR]

---

### Post by akoskm on 2011-08-20
First of all you should try to run your class files instead the source ones. So target the build directory.
If your class CashRegisterTester is inside the package cashregister, this would mean that your source code begins like:
```

package cashregister;

public class CashRegisterTester {
...
}

```
then you should try to run it by jumping into the directory where you compiled class files are (in you case this is **~/NetBeansProjects/BigJava/build/classes/** I think, not sure about netbean's file organization), then calling your class by it's full name (package name + class name):
```

java -cp . cashregister.CashRegisterTester

```
.

---

### Post by briigga on 2011-08-20
Awesome! thanks for the reply! 

Can you just tell me what the " -cp . " is for? and say i was already in the directory with the class files 
build/class/cashregister why cant I code: java CashRegisterTester from here? Do i always have to code:


	java -cp . packagename.filename
from build/class

---

### Post by akoskm on 2011-08-20
> **briigga said:**
> Awesome! thanks for the reply! 

Can you just tell me what the " -cp . " is for? and say i was already in the directory with the class files 
build/class/cashregister why cant I code: java CashRegisterTester from here? Do i always have to code:


	java -cp . packagename.filename
from build/class

-cp . is for adding the current directory (pwd) explicitly to the classpath, I always do like that in case of java, some operating systems adding the current dir to classpath others may not.

Yes, you always have to fully qualify your class with packagename + classname, take a look to this structure:
```

build
build/org
build/org/root
build/org/root/GetID.class
build/org/user
build/org/user/GetID.class

```
your classes actually in **build**, the fact that there are *org* and *root* and *user* directories are is just the nature of how java compiler organizes the packages.
So calling GetID of desired users can be done with (yes you can include -cp . too):
```

java org.root.GetID

```
or
```

java org.user.GetID

```.
Of course if there is only one class file in your project there is no point in placing it into a package.

---

### Post by ofnuts on 2011-08-20
> **briigga said:**
> Awesome! thanks for the reply! 

Can you just tell me what the " -cp . " is for? and say i was already in the directory with the class files 
build/class/cashregister why cant I code: java CashRegisterTester from here? Do i always have to code:


    java -cp . packagename.filename
from build/class-cp defines the "classpath, ie where Java looks for .class files (and other stuff like .properties) when executing the code. It contains either directories (java searches for .class in the filesystem), or .JAR files (JAVA takes the class from the JAR).

---

### Post by briigga on 2011-08-20
ok so two other things:

# 1. why is it that I cannot run the java program if im in the following directory (which contains the class files)
NetBeansProjects/BigJava/build/classes/cashregister$

my class files are in the cashregister folder.. i can run java cashregister.CashRegisterTester only if my directory is NetBeansProjects/BigJava/build/classes$



and # 2:

My .java files are in a completely different location:

NetBeansProjects/BigJava/src/cashregister$

from this directory i cannot run javac CashRegisterTester

I get an error message saying it cant find a sybmol. And again my program is fine.

Should i start saving my .java and class files in one folder?

I do appreciate all of your replies.

---

### Post by ofnuts on 2011-08-20
> **briigga said:**
> ok so two other things:

# 1. why is it that I cannot run the java program if im in the following directory (which contains the class files)
NetBeansProjects/BigJava/build/classes/cashregister$

my class files are in the cashregister folder.. i can run java cashregister.CashRegisterTester only if my directory is NetBeansProjects/BigJava/build/classes$



and # 2:

My .java files are in a completely different location:

NetBeansProjects/BigJava/src/cashregister$

from this directory i cannot run javac CashRegisterTester

I get an error message saying it cant find a sybmol. And again my program is fine.

Should i start saving my .java and class files in one folder?

I do appreciate all of your replies.

No... actually a frequent setup is

```

/your/top/directory/
/your/top/directory/net/briigga/cashregister/
/your/top/directory/net/briigga/cashregister/CashRegister.java
/your/top/directory/net/briigga/cashregister/CashRegister.class
/your/top/directory/net/briigga/cashregister/CashRegister.properties
/your/top/directory/net/briigga/cashregister/utilities/
/your/top/directory/net/briigga/cashregister/utilities/SomeUtility.java
/your/top/directory/net/briigga/cashregister/utilities/SomeUtility.class

```
[LIST]
[*]/your/top/directory is the "root" directory under which you keep everything, it is also your current directory to run your code.
[*]/your/top/directory/net/briigga/cashregister/ is the directory for the package
net.briggaa.cashegister and /your/top/directory/net/briigga/cashregister/utilities/ for net.briggaa.cashegister.utilities.
[*].java and .class and other files (properties) are kept in the same directory
[*]To run, from the "root" directory, use the class name "net.briggaa.cashregister.CashRegister
[*]Other classes and files (properties or else) will be resolved properly in that tree, classes by their package names, other files by their path ("/net/briggaa/cashregister/CashRegsiter.properties", or if you are using it from CashRegister,  "CashRegsiter.properties") if loaded as resources (getResrouceAsStream())
[/LIST]
 The benefit of this structure is that when you package as a JAR, the JAR contains the very same structure, minus the .java if you don't distribute the source, and plus a META-INF directory at the top (thta can point to net.briggaa.cashregister.CashRegister as the startup class.

---

### Post by briigga on 2011-08-20
I get what you are saying.

However from my root directory eduardo@eduardo-XPS-M1330:~$ 

i cant code: java NetBeansProjects.BigJava.build.classes.cashregister.CashRegisterTester

it wont work.

and still when im in the  directory where my .java files are located i cant code javac on them. 

Thanks for the reply ill figure it out eventually. just a little frustrating.

---

### Post by ofnuts on 2011-08-20
> **briigga said:**
> I get what you are saying.

However from my root directory eduardo@eduardo-XPS-M1330:~$ 

i cant code: java NetBeansProjects.BigJava.build.classes.cashregister.CashRegisterTester

it wont work.

and still when im in the  directory where my .java files are located i cant code javac on them. 

Thanks for the reply ill figure it out eventually. just a little frustrating.

1) try "java -verbose ... " it will show you what classes it looking for

2) using "NetBeansProjects.BigJava.build.classes.cashregister.CashRegisterTester" won't work because I doubt that at the top of your CashRegisterTester file there is:
```
package NetBeansProjects.BigJava.build.classes.cashregister;
```You need to reconsider the directory tree.

---

### Post by akoskm on 2011-08-21
> **briigga said:**
> I get what you are saying.

However from my root directory eduardo@eduardo-XPS-M1330:~$ 

i cant code: java NetBeansProjects.BigJava.build.classes.cashregister.CashRegisterTester

it wont work.

and still when im in the  directory where my .java files are located i cant code javac on them. 

Thanks for the reply ill figure it out eventually. just a little frustrating.

Please refer to my [last post]("http://ubuntuforums.org/showpost.php?p=11169176&postcount=4") where I already explained where is your build directory and where your package begins from the point of view of your classes.

---

