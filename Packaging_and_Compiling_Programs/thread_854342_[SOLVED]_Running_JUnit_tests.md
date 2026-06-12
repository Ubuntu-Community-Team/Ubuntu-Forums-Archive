---
title: "[SOLVED] Running JUnit tests"
date: 2008-07-09
forum: Packaging and Compiling Programs
---

### Post by cait on 2008-07-09
I use JUnit tests for a class that I grade for, and I'm trying to make it so I can run them locally. Until now I have used my school's filesystem, which has everything installed already, but my internet connection has been bad lately so I was hoping to move away from that (I'm also not a big fan of importing everything into Eclipse, so I'd rather use command prompt). I've installed java6-jdk and junit4. I can run regular (non-junit) Java programs. However, when I run
```
javac -cp /usr/share/java/junit4-4.3.1.jar BaseTest.java
```
it has the following error:
```
BaseTest.java:18: cannot find symbol
symbol  : class BaseForm
location: class BaseTest
	BaseForm a = new BaseForm();
	^
BaseTest.java:18: cannot find symbol
symbol  : class BaseForm
location: class BaseTest
	BaseForm a = new BaseForm();
	                 ^
2 errors

```
BaseForm.java is the file that I am running tests on, and it is in the same folder as BaseTest.java. This can be fixed by compiling *.java to include this class, but when I do this on the remote server, I can compile just the test file and it automatically finds and compiles all other classes that it needs. Any idea why this is happening?

Using
```
javac -cp /usr/share/java/junit4-4.3.1.jar *.java
```
the program compiles, but then I run it and get:
```
 java -cp /usr/share/java/junit4-4.3.1.jar org.junit.runner.JUnitCore BaseTest
JUnit version 4.3.1
Could not find class: BaseTest

Time: 0

OK (0 tests)

```
For some reason it can't find the class file, which is in the folder I'm in. Again, doing this online on the school's file system, using the same files and commands (just a different path to the junit .jar file) works fine, so maybe something isn't installed as it should be? Or is something still wrong in my path, now that I'm doing it locally? I'd really appreciate any suggestions! Thanks!

---

### Post by gekkio on 2008-07-19
Remember that -cp completely overrides the classpath and doesn't just add stuff to it.
This means that javac will look for classes in junit4-4.3.1.jar but NOT in the current directory.

You must add the current directory to the classpath like this:
```

javac -cp .:/usr/share/java/junit4-4.3.1.jar BaseTest.java

```
This means:
- Compile BaseTest.java
- Search for classes in current directory (.)
- Search for classes in /usr/share/java/junit4-4.3.1.jar

Same thing applies when you're running your test with the java-command.

If you're wondering why it compiles when using *.java, the reason is that *.java includes all the java files in the current directory, and thus javac finds all the classes it needs.
However, it doesn't run, because your java command only finds the JUnit classes, and none of your compiled classes (-> add .: to classpath and it will work).

I recommend you to use some build tool (Ant or Maven), because handling classpaths by hand seriously lowers your productivity (yes, I have compiled some classes with 30+ library jars and manually specified the classpath :)). I'm using Maven nowadays for even simple projects because it really makes things easier when you know how to use it. It'll hurt badly at first but you'll thank yourself later.

---

