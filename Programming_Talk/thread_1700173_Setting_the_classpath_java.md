---
title: "Setting the classpath java"
date: 2011-03-04
forum: Programming Talk
---

### Post by raac on 2011-03-04
Does anyone know what to do before setting up the classpath? I tried this and

setenv CLASSPATH /path/mysql-connector-java-[ver]-bin.jar:$CLASSPATH

and i got this


CLASSPATH: Undefined variable.

How can I define it?

---

### Post by trozamon on 2011-03-04
What exactly are you trying to do?

If you're trying to import that JAR, why don't you just put it in /usr/lib/jvm/java-6-openjdk/jre/lib/ext.  Then, java will automatically see the JAR.

---

### Post by raac on 2011-03-05
What I'm trying to do is make java connect to a database (mysql).
I've been googling for how to do it? And I found out I have to install a driver before. So, according to MySql website I need to do the following...

"...you can install the driver by placing mysql-connector-java-[version]-bin.jar in your classpath.....For example, under a C shell (csh, tcsh) you would add the Connector/J driver to your CLASSPATH using the following:

shell> setenv CLASSPATH /path/mysql-connector-java-[ver]-bin.jar:$CLASSPATH

....."

But, the website says "Manual for MySQL 5.5", so I don't know if the version I have will work for this

I have version

mysql  Ver 14.14 Distrib 5.1.49, for debian-linux-gnu (i686) using readline 6.1

---

### Post by trozamon on 2011-03-05
If you do what I told you above, it should work.

---

### Post by raac on 2011-03-05
Yes It did work, thank you!!. So basically java executes the files in that directory whenever it needs to do it??



Is there a way to compile a java program in linux and create an executable that anyone can simply double click on it and run the program??

---

### Post by trozamon on 2011-03-05
Yes, java sees files in that directory and allows them to be imported into java programs

As for compiling it into one thing, here's how to do it:

First:

```
 javac yourclass.java
```

Then, open gedit, type:

```
 Main-Class: yourclass
```

Save as manifest.txt in the same spot as your compiled class. Also, press enter after the first line in the manifest, otherwise it may not work.
Next, run:

```
 jar cvmf manifest.txt whateveryouwant.jar yourclass.class
```

There, you should be able to double click on it and run it after setting the executable bit

---

### Post by Some Penguin on 2011-03-05
For larger projects, one needs to remember to include dependencies in the .jar or to instruct the user to set classpath accordingly, of course.

There's also the much rarer alternative of using an AOT (ahead-of-time) compiler.  I don't think there's a lot of AOT compiler development lately; between advances in JIT (just in time) compilation and other runtime optimizations, and the increased availability of higher-performance libraries like Trove for areas where the standard JDK libraries are slower, the performance penalty of using Java bytecode vs AOT'd code has been significantly reduced.  gcj, for instance, apparently never got around to fully supporting Java 1.5.

---

### Post by raac on 2011-03-05
Thanks guys

I'm assuming the executable will be the .jar file, after the command...

jar cvmf manifest.txt whateveryouwant.jar yourclass.class


Ok, I got an exception, let me tell you some info first

The name of the class where I have my main method is

simpleProgram


It is a simple program that i'm using just to test the procedure it only contains this..

public class simpleProgram{

   public static void main (String [] arg){
      System.out.println("This is working");
   }
}



*so my manifest.txt contains

 Main-Class:simpleProgram[enter]      //[enter] means i pressed enter

*the final command that I used is

jar cvmf manifest.txt testing.jar simpleProgram.class


*and I got

java.io.IOException: misplaced continuation line
	at java.util.jar.Attributes.read(Attributes.java:391)
	at java.util.jar.Manifest.read(Manifest.java:199)
	at java.util.jar.Manifest.<init>(Manifest.java:69)
	at sun.tools.jar.Main.run(Main.java:169)
	at sun.tools.jar.Main.main(Main.java:1167)

*Then I tried the manifest.txt with no [enter] and did not work either.

did I miss something?

---

### Post by lykeion on 2011-03-06
The jar command is very picky about the manifest file contents. Make sure it contains this *exactly* (notice space after the semicolon)
```
Main-Class: simpleProgram


```
Read more about using jar here: [http://download.oracle.com/javase/tutorial/deployment/jar/](http://download.oracle.com/javase/tutorial/deployment/jar/)

---

### Post by raac on 2011-03-06
Thanks, you're right jar is picky. This is sort of what I was looking for. I created the jar file and did a chmod on it. It is now an executable, but I can only run it from the command line. I'm saying this because I'm gonna do a GUI program for my girlfriend and she doesn't know much about the terminal. She rathers double click on icons, I double click on the jar file and by default is opened with the archive manager. With what should I open the jar files in order for it execute the program? I tried with OpenJDK Java 6 Runtime, but it didn't work

---

### Post by lykeion on 2011-03-06
I'm not sure about OpenJDK since I'm using Sun Java JDK, and in Nautilus I can right-click jar file and select to Open with Sun Java 6 Runtime and it works fine. 
However the simpleProgram you tried with earlier is not a GUI application, and when running it this way it doesn't do anything, it's only when running it in a terminal you'd see the output.
You could also create simple script in the same dir as the jar file to run it.
```
#!/usr/bin/env bash

# go to dir where this script is
SCRIPT_DIR=$(cd `dirname $0` && pwd)
cd $SCRIPT_DIR

# run the jar file (change name to your jar filename)
java -jar whateveryouwant.jar

# wait for user input before exiting (only necessary for a non-GUI app)
echo "Press enter to quit"
read var
exit 0
```

Right-click the script and make it executable

Then you can create a launcher on the desktop by right-clicking on Desktop > Create Launcher...
Type: Application (change to App in terminal if it's a non-GUI app)
Command: Click Browse and select runScript.sh created earlier

---

### Post by raac on 2011-03-06
Yes, that worked,thank you. I appreciate your help.

---

### Post by danswater on 2011-04-29
It works for me too! Thank you.

---

### Post by jespdj on 2011-04-29
It's advisable to **not** set the CLASSPATH environment variable. Instead, use the -cp option when running your Java program. For example:

java -cp something.jar:somethingelse.jar:. org.mypackage.MyProgram

---

