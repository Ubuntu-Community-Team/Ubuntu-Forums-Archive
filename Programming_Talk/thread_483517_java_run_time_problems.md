---
title: "java run time problems"
date: 2007-06-24
forum: Programming Talk
---

### Post by lord bacon on 2007-06-24
i seem to be having a problem with running java Programs from the command line, the programs (only very simple ones to see if this actually works) are compiling okay, but when i try to run them i am getting errors saying it cant find the main class, here is the output:

Exception in thread "main" java.lang.NoClassDefFoundError: Test.class
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: Test.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

the code i was attempting to run was:

public class Test
{
	public static void main (String[] args)
	{
		System.out.println("Test Program output");
	}
}


as you can see it is very simple but i cant get it to run. this used to work using the usual java SDK, but when i installed eclipse it changed somethin somewhere, and now i cant run any programs, why is this happening.

thanks Lord Bacon

---

### Post by samjh on 2007-06-24
You have GCJ set as your default Java environment.

Run this in the terminal:
```
sudo update-alternatives --config java
```
and for good measure:
```
sudo update-alternatives --config javac
```
For each one, select the Java version provided by Sun, not GCJ.

Then recompile your program.

---

### Post by Tomosaur on 2007-06-24
It looks like you're trying to run the program using 'java Test.class'. The actual command you need to type is 'java Test'. Just leave the '.class' off.

I would also suggest you drop gcj and just use Sun's java, it'll save you a lot of headaches later on (and Sun's Java is - or at least, will be soon - GPLd, so if you only want a free Java, then Sun's is just as good, or better, than gcj).

---

### Post by lord bacon on 2007-06-24
Thanks samjh, your idea worked perfectly, everythin is workin fine again. Tamosaur, yea just noticed that i had .class, but the same thing was happening with out it there.. neways, thanks heaps for the help guys..

---

### Post by Ramses de Norre on 2007-06-25
> **samjh said:**
> You have GCJ set as your default Java environment.

Run this in the terminal:
```
sudo update-alternatives --config java
```
and for good measure:
```
sudo update-alternatives --config javac
```
For each one, select the Java version provided by Sun, not GCJ.

Then recompile your program.

**sudo update-java-alternatives -s *<version>*** will take care of all java related packages at once (for instance also javah and javadoc and such), find out your version with the -l switch.

---

### Post by samjh on 2007-06-25
Very cool.  Thanks, Ramses de Norre.

---

