---
title: "Java compiling error"
date: 2007-06-06
forum: Programming Talk
---

### Post by reidms on 2007-06-06
Hi- I am reading a book on Java 6 and when I try to compile an example typed in the book
```
class VolcanoApplication {
    public static void main(String[] arguments) {
        VolcanoRobot dante = new VolcanoRobot();
        dante.status = “exploring”;
        dante.speed = 2;
        dante.temperature = 510;

        dante.showAttributes();
        System.out.println(“Increasing speed to 3.”);
        dante.speed = 3;
        dante.showAttributes();
        System.out.println(“Changing temperature to 670.”);
        dante.temperature = 670;
        dante.showAttributes();
        System.out.println(“Checking the temperature.”);
        dante.checkTemperature();
        dante.showAttributes();
    }
}

```

I get these errors from javac

```
$ javac VolcanoApplication.java
VolcanoApplication.java:4: illegal character: \8220
        dante.status = “exploring”;
                       ^
VolcanoApplication.java:4: illegal character: \8221
        dante.status = “exploring”;
                                 ^
VolcanoApplication.java:4: not a statement
        dante.status = “exploring”;
                        ^
VolcanoApplication.java:9: illegal character: \8220
        System.out.println(“Increasing speed to 3.”);
                           ^
VolcanoApplication.java:9: ';' expected
        System.out.println(“Increasing speed to 3.”);
                                            ^
VolcanoApplication.java:9: not a statement
        System.out.println(“Increasing speed to 3.”);
                                             ^
VolcanoApplication.java:9: ';' expected
        System.out.println(“Increasing speed to 3.”);
                                               ^
VolcanoApplication.java:9: illegal character: \8221
        System.out.println(“Increasing speed to 3.”);
                                                  ^
VolcanoApplication.java:12: illegal character: \8220
        System.out.println(“Changing temperature to 670.”);
                           ^
VolcanoApplication.java:12: ';' expected
        System.out.println(“Changing temperature to 670.”);
                                                ^
VolcanoApplication.java:12: not a statement
        System.out.println(“Changing temperature to 670.”);
                                                 ^
VolcanoApplication.java:12: ';' expected
        System.out.println(“Changing temperature to 670.”);
                                                   ^
VolcanoApplication.java:12: illegal character: \8221
        System.out.println(“Changing temperature to 670.”);
                                                        ^
VolcanoApplication.java:15: illegal character: \8220
        System.out.println(“Checking the temperature.”);
                           ^
VolcanoApplication.java:15: ';' expected
        System.out.println(“Checking the temperature.”);
                                        ^
VolcanoApplication.java:15: illegal character: \8221
        System.out.println(“Checking the temperature.”);
                                                     ^
VolcanoApplication.java:15: not a statement
        System.out.println(“Checking the temperature.”);
                                                    ^
17 errors
```

What is the problem here?  I typed it exactly like it was listed- quadruple checked it too

I tried compling on Ubuntu Feitsy and Solaris Express DE

---

### Post by meng on 2007-06-06
What text editor did you use to type the program? It doesn't seem to like your quotation marks.

---

### Post by reidms on 2007-06-06
gedit on both operating systems

let me try nano

---

### Post by meng on 2007-06-06
It shouldn't be a gedit problem, although those quotation marks look funny: why are they inclined, not straight up and down like this " ?

---

### Post by reidms on 2007-06-06
Nano gave me this $ java VolcanoApplication1.java
Exception in thread "main" java.lang.NoClassDefFoundError: VolcanoApplication1/java


I do have a weird terminal font- maybe thats why- never notice that about my " though :P

---

### Post by meng on 2007-06-06
well, your opening and closing quotes have different codes (\8220 and \8221) so that's a clue right there, they really ought to be the same character!

---

### Post by reidms on 2007-06-06
Hmmm this is weird.......

here are the contents of the .java file
```
 1: class VolcanoApplication {
 2:     public static void main(String[] arguments) {
 3:         VolcanoRobot dante = new VolcanoRobot();
 4:         dante.status = "exploring";
 5:         dante.speed = 2;
 6:         dante.temperature = 510;
 7:
 8:         dante.showAttributes();
 9:         System.out.println("Increasing speed to 3.");
10:         dante.speed = 3;
11:         dante.showAttributes();
12:         System.out.println("Changing temperature to 670.");
13:         dante.temperature = 670;
14:         dante.showAttributes();
15:         System.out.println("Checking the temperature.");
16:         dante.checkTemperature();
17:         dante.showAttributes();
18:     }
19: }

```

they are normal there-

This is odd- I have this error on two different computers and operating systems though- so it is probably the source code

---

### Post by meng on 2007-06-06
Try using this file (you'll have to rename it to .java)

---

### Post by reidms on 2007-06-06
Thanks for your time meng

here is the output now

```
$ cd ./Desktop
$ javac VolcanoApplication.java
VolcanoApplication.java:3: cannot find symbol
symbol  : class VolcanoRobot
location: class VolcanoApplication
        VolcanoRobot dante = new VolcanoRobot();
        ^
VolcanoApplication.java:3: cannot find symbol
symbol  : class VolcanoRobot
location: class VolcanoApplication
        VolcanoRobot dante = new VolcanoRobot();
                                 ^
2 errors

```

---

### Post by meng on 2007-06-06
Yeah I had that too. Are you sure that's the complete program? You need to define a class VolcanoRobot (which will contain methods including showAttributes), otherwise the program won't compile

---

### Post by reidms on 2007-06-06
I am not to keen on OOP yet- but there was a class- but what the book says is that the class is just a template and applications are derived from it- the class was this

VolcanoRobot.class
```
 1: class VolcanoRobot {
 2:     String status;
 3:     int speed;
 4:     float temperature;
 5:
 6:     void checkTemperature() {
 7:         if (temperature > 660) {
 8:             status = “returning home”;
 9:             speed = 5;
10:         }
11:     }
12:
13:    void showAttributes() {
14:         System.out.println(“Status: “ + status);
15:         System.out.println(“Speed: “ + speed);
16:         System.out.println(“Temperature: “ + temperature);
17:    }
18: }

```

---

### Post by meng on 2007-06-06
Yes you need this code! Note that you still have funny quotation marks ...
What you can do is compile VolcanoRobot.java
then compile VolcanoApplication.java (it will look for VolcanoRobot ...)

---

### Post by reidms on 2007-06-06
Sorry- I am a newb...I mis understood what a class was- and I am still a bit unsure.

They way I thought it was was a class was just a template, and an object was created from the class

:P

Let me recompile once more- thanks for your patience!

---

### Post by reidms on 2007-06-06
Atlast-  VolcanoRobot.class
I had to open VolcanoRobot.java and replace all the quotes

but upon execution i get this
```
$ java VolcanoApplication
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(Unknown Source)
        at java.security.SecureClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.access$100(Unknown Source)
        at java.net.URLClassLoader$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClassInternal(Unknown Source)
```

Any help here?  I think it means something about .class is set to a wrong JDK version or something

---

### Post by Ramses de Norre on 2007-06-07
What's the output of these:
```
java -version
javac -version
```
And if you make an object of the class VolcanoRobot, that class needs to be in your software system. So you need to compile that class in the same directory of your VolcanoApplication class if you want to use it. Otherwise your jre doesn't know the type VolcanoRobot.

---

### Post by samjh on 2007-06-07
First, recreate the source files VolcanoRobot.java and VolcanoApplication.java, and replace those strange quotation marks with the proper quotation marks.

Second, delete any .class files in the directory where the .java files are.

Third, check what kind of Java you have by typing:
```
java -version
javac -version
```They should say java or javac version 1.6.0.

Third, compile VolcanoApplication.java; the javac compiler will automatically compile VolcanoRobot.java as well.

Fourth, run VolcanoApplication.

Let us know what happens.

(I've successfully compiled your source files and have run the VolcanoApplication class.  The quotation marks caused problems, but everything else was fine.)

---

### Post by reidms on 2007-06-07
Thanks for your time guys-

I have 1.5 of Java
and 1.6 of Javac

but I have 1.6 of Java installed- I just need to select it-

just ran
```
 sudo update-alternatives --config java
```
to select-

now let me recompile

and I now get his error

```
$ javac VolcanoApplication.java
$ java VolcanoApplication.class
Exception in thread "main" java.lang.NoClassDefFoundError: VolcanoApplication/class

```

---

### Post by Gwasanaethau on 2007-06-07
> **reidms said:**
> Thanks for your time guys-

I have 1.5 of Java
and 1.6 of Javac

but I have 1.6 of Java installed- I just need to select it-

just ran
```
 sudo update-alternatives --config java
```
to select-

now let me recompile

and I now get his error

```
$ javac VolcanoApplication.java
$ java VolcanoApplication.class
Exception in thread "main" java.lang.NoClassDefFoundError: VolcanoApplication/class

```

Hiya there,

To run the Java programme, you don't need to put '.class' on the end. The command should be just:

```
java VolcanoApplication
```

Hopefully that should work. ;)

Gwasanaethau

---

### Post by reidms on 2007-06-07
Yep it works now :P

As you can see- I am probably going to be a horrible Java Programmer lol


Thanks all for your time.

---

### Post by Gwasanaethau on 2007-06-07
> **reidms said:**
> …As you can see- I am probably going to be a horrible Java Programmer lol…

Not at all! I only know because I made that mistake when I first ran a Java programme too! I think it's something everyone does… ;)

---

### Post by Ramses de Norre on 2007-06-07
> **reidms said:**
> Thanks for your time guys-

I have 1.5 of Java
and 1.6 of Javac

but I have 1.6 of Java installed- I just need to select it-

just ran
```
 sudo update-alternatives --config java
```
to select-

You might want to use **sudo update-java-alternatives -s *version*** which will set all related programs to the right version and will save you trouble later, you can find the right version with **update-java-alternatives -l**.
And believe me, I made such stupid mistake too when I started with java, you'll get used to it if you continue using it.

---

### Post by reidms on 2007-06-07
Thanks for the command Ramses de Norre

After diving into Java- I only understand about 10 percent right now about the OOP lol but I guess I will get the hang of it.

Java has alot more structure than C/C++ which I guess is better once you get through all the class structure and etc.

Thanks all for your time and help

---

### Post by Ramses de Norre on 2007-06-07
> **reidms said:**
> Thanks for the command Ramses de Norre

After diving into Java- I only understand about 10 percent right now about the OOP lol but I guess I will get the hang of it.

Java has alot more structure than C/C++ which I guess is better once you get through all the class structure and etc.

Thanks all for your time and help

OOP is very abstract when you first see it... But someday a world of elegance and relevance will open up, at that point you understand the concept ;)

---

### Post by reidms on 2007-06-07
I hope so :P

---

