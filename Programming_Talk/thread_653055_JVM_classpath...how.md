---
title: "JVM classpath...how??"
date: 2007-12-29
forum: Programming Talk
---

### Post by asimmittal on 2007-12-29
Hey,

I have looked at quite a few threads before finally posting this up. I dunno what I'm doing wrong.

[COLOR="SeaGreen"]
asim@asim-laptop:~$ cd /media/hda6/Codes/Java/
asim@asim-laptop:/media/hda6/Codes/Java$ java Ascii_Chart
Exception in thread "main" java.lang.ClassFormatError: Ascii_Chart (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
asim@asim-laptop:/media/hda6/Codes/Java$

[/COLOR]

now I've been using java on windows, and this kinda reply would mean only one thing - classpath is not set.

I have downloaded jdk1.6 from the java.sun download page. It was a .bin file which i unpacked in the terminal. The result was the "jdk1.6_03" folder which i have placed in some remote directory. I then proceeded to set my path (by editing .bashrc) to my jdk directory. 

Everything was fine... javac command was now being recognized. However, every time I use "java", it throws the classpath exception. Then I tried altering the /etc/environment file. Same result... no change.

Can anyone please help me out. I'm running a Dapper on a Pentium4 processor. 

P.S: I installed netbeans ide, and specified my java directory. If i execute a file there, within the IDE - it does everything perfectly. But I want to use the command line only. Please help

---

### Post by Kadrus on 2007-12-29
> **asimmittal said:**
> Hey,

I have looked at quite a few threads before finally posting this up. I dunno what I'm doing wrong.

[COLOR="SeaGreen"]
asim@asim-laptop:~$ cd /media/hda6/Codes/Java/
asim@asim-laptop:/media/hda6/Codes/Java$ java Ascii_Chart
Exception in thread "main" java.lang.ClassFormatError: Ascii_Chart (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
asim@asim-laptop:/media/hda6/Codes/Java$

[/COLOR]

now I've been using java on windows, and this kinda reply would mean only one thing - classpath is not set.

I have downloaded jdk1.6 from the java.sun download page. It was a .bin file which i unpacked in the terminal. The result was the "jdk1.6_03" folder which i have placed in some remote directory. I then proceeded to set my path (by editing .bashrc) to my jdk directory. 

Everything was fine... javac command was now being recognized. However, every time I use "java", it throws the classpath exception. Then I tried altering the /etc/environment file. Same result... no change.

Can anyone please help me out. I'm running a Dapper on a Pentium4 processor. 

P.S: I installed netbeans ide, and specified my java directory. If i execute a file there, within the IDE - it does everything perfectly. But I want to use the command line only. Please help
Euuh...I am going to try to help you from the beginning..
Open terminal and type:
```
sudo apt-get install sun-java6-jdk
```
This should install Java..
Now let's compile something:
```

class Test{
public static void main(String args[])
{
System.out.prinltn("Test");
}
}

```
I am not a Java programmer...so there might me a mistake in her.e.
save the file test.java..
Open terminal and type:
```
javac test.java
```
then type:
```
java Test
```
This should do it..
I hope this helped you  :)

---

### Post by amo-ej1 on 2007-12-29
Your java version is not correct, it uses the gcj and not your freshly installed jdk (to verify this type java -version in a console).

---

### Post by asimmittal on 2007-12-29
[COLOR="MediumTurquoise"]
asim@asim-laptop:/media/hda6/Codes/Java$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 287 not upgraded.
asim@asim-laptop:/media/hda6/Codes/Java$ javac Ascii_Chart.java
asim@asim-laptop:/media/hda6/Codes/Java$ java Ascii_Chart
Exception in thread "main" java.lang.ClassFormatError: Ascii_Chart (unrecognized  class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
asim@asim-laptop:/media/hda6/Codes/Java$

[/COLOR]

There i did just as you said... nothing happened. Oh  I had gotten the sun-java6-jdk package beforehand. but still java is not being recognized

---

### Post by asimmittal on 2007-12-29
I did it...

actually ubuntu provides its own jvm (some gij)

if u type:
      sudo update-alternatives --config java

you'll get all the versions of JVM installed on your machine. It'll show you a list of jvm's like this:

 Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-6-sun/jre/bin/java

And ask you to select one. The one with '*' marked next to it is the one being used by default. Before I changed mine, my machine was using #2 and not #3 (the one provided by sun). So i switched it to #3... and voila!!

Thanks

---

### Post by Kadrus on 2007-12-29
> **asimmittal said:**
> I did it...

actually ubuntu provides its own jvm (some gij)

if u type:
      sudo update-alternatives --config java

you'll get all the versions of JVM installed on your machine. It'll show you a list of jvm's like this:

 Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-6-sun/jre/bin/java

And ask you to select one. The one with '*' marked next to it is the one being used by default. Before I changed mine, my machine was using #2 and not #3 (the one provided by sun). So i switched it to #3... and voila!!

Thanks
Glad your problem got fixed :)

---

