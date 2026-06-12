---
title: "Scanner class in Eclipse not working"
date: 2009-04-12
forum: Programming Talk
---

### Post by Zebra Lord on 2009-04-12
Hello everyone,
I am a newbie to Linux and also to Java.  However I had installed the latest Java jdk and jre.  I then installed Eclipse using the Add/Remove application.  Eclipse works fine except that some of the classes from the Java API seem to be missing.  For example, Eclipse will allow me to import java.util.*  but not java.util.Scanner.

I know that the Scanner class exists because when I write code which includes a Scanner class in a txt file and compile it in the terminal it works. Does Eclipse use its own compiler or something?

Any help will be appreciated!

---

### Post by chrisjsmith on 2009-04-12
It uses gcj/classpath rather than sun java by default.

You need to put sun java on (install ubuntu-restricted-extras) and configure eclipse to use it:

sudo gedit /etc/eclipse/jdk

move entry "sun-jdk-6" to the top of the list, then restart eclipse.  Modify your project so that it picks up the provided jdk rather than the default one.

This is from memory so it might not be 100% accurate.

---

### Post by Zebra Lord on 2009-04-12
> **chrisjsmith said:**
> It uses gcj/classpath rather than sun java by default.

You need to put sun java on (install ubuntu-restricted-extras) and configure eclipse to use it:

sudo gedit /etc/eclipse/jdk

move entry "sun-jdk-6" to the top of the list, then restart eclipse.  Modify your project so that it picks up the provided jdk rather than the default one.

This is from memory so it might not be 100% accurate.

Thanks for the help but the only file in /etc/eclipse is a java_home txt file.  I opened the file, but /usr/lib/jvm/java-6-sun was already at the top of the list.
Also you said to "Modify your project so that it picks up the provided jdk rather than the default one." Could you please elaborate on how to do that.  Like I said I'm a newbie :P.

---

### Post by doas777 on 2009-04-12
usually, it's been my experience that if you are having trouble resolving the scanner class, then your compliler is useing the 1.4 jdk, not 1.5+.

whats the output of ```

java -version

```?

---

### Post by Zebra Lord on 2009-04-12
this is the output:
"java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)"

the output for javac -version is:
"javac 1.6.0_10"

However I did notice that my output when i typed export did not include a JAVA_HOME path.

---

### Post by doas777 on 2009-04-12
> **Zebra Lord said:**
> this is the output:
"java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)"

the output for javac -version is:
"javac 1.6.0_10"

However I did notice that my output when i typed export did not include a JAVA_HOME path.

I'm sorry, I meant
```
javac -version
```.

your JRE is definelty a good version for the scanner class, so lets check your jdk. also you should make sure that your eclipse settings for the project specify code compliance for 1.5 +.

---

### Post by Zebra Lord on 2009-04-12
I listed my javac -version output in my previous reply but again its:
"javac 1.6.0_10"

---

### Post by doas777 on 2009-04-12
ahh, sorry about that.

open eclipse, and go to Window -> Preferences -> Java -> Compiler, and check your 'Compiler Compliance Settings'. it shoudl be 5.0 or higher.

---

### Post by Zebra Lord on 2009-04-12
I changed the Compiler Compliance Settings to 6 but still no luck

---

### Post by Zebra Lord on 2009-04-12
Nvm guys I figured it out :).  I just right clicked my project file and went to Build Path > Add Libraries. Then I selected JRE System Library and clicked next.  Then I selected the Alternative JRE radio and pasted the address "/usr/lib/jvm/java-6-sun" (it is probably /usr/lib/jvm/java-6-sun-1.6.0.10 for those who haven't created a link.) I just clicked finish then and that fixed it.

Thanks for all your help you guys!  I really appreciate it.

---

