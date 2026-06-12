---
title: "how to run java on ubuntu?"
date: 2008-12-31
forum: Programming Talk
---

### Post by m.balakrishnan on 2008-12-31
i wrote following program

[B][I]#import.java.io.*;
class bala
{
public static void main(String args[])IOException
{
 system.out.println("krishna");
}
}[/I][/B]

i can this program but i can't run this program, while i run this program it shows following message. 

[B]The program 'javac' can be found in the following packages:
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * jikes-kaffe
 * java-gcj-compat-dev
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found[/B]

[COLOR="Red"]what will i do?[/COLOR]

---

### Post by TheOrangePeanut on 2008-12-31
sudo apt-get install sun-java6-jdk

---

### Post by m.balakrishnan on 2008-12-31
thank u

---

### Post by m.balakrishnan on 2008-12-31
i done as you said, but now it has some error.
[COLOR="Red"]what will i do?[/COLOR]
 javac sam.java

[B]javac: file not found: sam.java
Usage: javac <options> <source files>
use -help for a list of possible options[/B]

then

[B]java sam
Exception in thread "main" java.lang.NoClassDefFoundError: sam
[/B]

---

### Post by tinny on 2008-12-31
Your file should be named "bala.java" not "sam.java".

The file name needs to be the same name as the class.

Also 

system.out.println("krishna"); 

need to be upper case for System.

E.g.

System.out.println("krishna");

---

### Post by jespdj on 2008-12-31
Also, you should not have a # in front of the import statement.

And this:
```
public static void main(String args[])IOException
```
should be:
```
public static void main(String args[]) throws IOException
```
Or simply:
```
public static void main(String args[])
```
Because there's no code in your main() method that throws an IOException.

---

### Post by shadylookin on 2008-12-31
> #import.java.io.*;
shouldn't have the # sign this isn't C includes

> 
public static void main(String args[])IOException
IOException shouldn't be there because it won't throw one

> 
system.out.println("krishna");
 
System.out.println("krishna");

System is capitalized

you need to save this as bala.java then you need to compile
**javac bala.java** and it will compile to bala.class then run it with **java bala**

if you're still having issues be sure you're using sun java
**sudo update-alternatives --config java** and select the one that's sun java

---

