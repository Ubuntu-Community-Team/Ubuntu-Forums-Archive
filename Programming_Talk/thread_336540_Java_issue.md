---
title: "Java issue"
date: 2007-01-11
forum: Programming Talk
---

### Post by Mazen on 2007-01-11
hi all,
i just want to know how to modify the class paths in ubuntu cuz i cannot import in Eclipse when doing java,
ex when i go ```
import java.util.Scanner
``` it does not work!

---

### Post by Tomosaur on 2007-01-11
Recommended is to set $JAVA_HOME to wherever the bin directory is, that seems to be what most java apps use. Eclipse was funny for me too, I just gave up on it in the end (I'm comfortable enough without an IDE, but I used to use it a while back) and now I use JEdit. It doesn't have the features of eclipse by default, but there are tons of plugins which will give you full eclipse-like functinality: a built in CLI, code completion, tabbed editing, doc lookup etc. It's pretty cool.

---

### Post by strangelife on 2007-01-11
I would suggest checking out the website for [Java Programmers]("http://www.java4programmers.com") to get your questions answered !

---

### Post by welshboy on 2007-01-12
According to a book I'm reading, you could put the .jar files into a folder called ext in your java folders, which will be here (if you installed from repos)

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$

According to my book at least, it means that the .jars will be found automatically by the compiler.

However I think you'd need to be a super user to copy files to it

so you'd do
emyr@Wookie:~$sudo cp util.jar /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$

And then that should prompt you for your password, and then copy the jar file to the folder. Then you'll be able to access the jar file in all your java programs.

To edit the CLASSPATH variable, you could either edit your .bashrc if you want to make it just for your user, or the whole system by editing etc/environment

Hope that helps a bit too :S

---

### Post by David Mulligan on 2007-01-14
Better yet add the jar file to your project.

Right click on your project, go to properties->build path->libraries-> add (External) JARs.

Most projects will put a copy of the jar file in a lib(s) dir in the project dir.  eg. myProject/libs/Scanner.jar

Good luck.
David

---

### Post by phossal on 2007-01-14
Unrelated, when I install the JDK/Eclipse and Tomcat, I do it [this way]("http://ubuntuforums.org/showthread.php?t=332674").

When I need to use extensions, like itext or servlets or MySQL-connector, I put the whole jar file in:
<JRE>/lib/ext/. Then I restart eclipse. Adding the extensions to the JRE makes them available to all Java programs, including eclipse. There is a downside, of course, to not importing them into your project. You'll have to make the same extensions available to other machines running your program.

java.util.Scanner isn't an extension, though. If you're getting errors importing it, you need to adjust your JRE or compiler settings in eclipse.


[edit] In fact, some extensions actually warn against importing directly into your project. I believe MySQL-connector is one of them.

---

