---
title: "Java programming error - NoSuchMethodError: main"
date: 2007-02-24
forum: Programming Talk
---

### Post by solarjeep on 2007-02-24
I've searched the forums for similar problems but none seem the same scenario as mine, just the same outcome (same error message).

I'm using java version 1.6.  I'm learning java.  I've been writing several simple programs for several days.  They compile fine.  Run fine.  Until today.  

I create a new program, compile it with no errors.  Run it and get this error:

"Exception in thread "main" java.lang.NoSuchMethodError: main"

I run a program that I created, compiled and ran yesterday and it runs fine again today.  If I recompile it (no errors) it won't run.  Same error message.

Here is one of the programs copied from my Root.java file (this is from a book I'm using to learn Java):

```

class Root {
	public static void main(String[] arguments){
		int number = 625;
		System.out.println("The square root of "
		+ number
		+ " is "
		+ Math.sqrt(number) ) ;
	}
}


```

The most important thing is that everything was working fine yesterday.  Same programs today run unless I recompile them.  I haven't changed anything.   Help!

---

### Post by Ragazzo on 2007-02-24
How are you compiling and trying to run it?

---

### Post by solarjeep on 2007-02-24
from console:

compile:

javac Root.java

run:

java Root

I'm in the directory with the *.java and *.class files.  This is the same way I've been doing it for a week now without a problem.

---

### Post by Enselic on 2007-02-24
Make sure the compiler and the VM have the same (major) version, i.e. compare javac -version with java -version. If you use 1.6, both compiler and VM should be of this version.

---

### Post by solarjeep on 2007-02-24
ok, I checked that.  Here's the output (I'm not sure the proper way to "quote" this here I hope this is right.

checking java version output =

```

java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode)

```

checking javac version output =

```

javac -version
javac 1.6.0

```

---

### Post by solarjeep on 2007-02-24
On a wild guess - 

I created a source file in a different folder.  It compiled AND ran correctly.  
Hmm.  
So, I went to my original folder and deleted all the files in it (about 40 files).  Created a new program and it compiled and ran correctly.  Created a couple more and no problems.  Moved all the original files back to the original folder.  Tried to compile and run programs - I get the same error as before.  Delete all the files but one or two, they compile and run with no errors.  

This is wierd.  It seems that there is a limit to the number of files I can have in a folder until I start getting errors in running a java program.  I'm not sure what the threshold is (between 6 and 40). What's the connection?

I'm not going to mark this as resolved yet since I have only found a workaround not a solution.  Anyone have any ideas?

---

### Post by dxxvi on 2007-02-25
What does 

echo $CLASSPATH

say?

---

### Post by Ragazzo on 2007-02-25
Do you have only one class per file (public and non-public)? For example if you have

Test.java:
```

class Test { 
  public static void main(String[] args) {
    System.out.println("hello world");
  }
}

```

Test2.java
```

class Test2 {
  public static void main(String[] args) {
  }
}
class Test {
}

```

~> javac Test.java
~> java Test
hello world
~> javac Test2.java
~> java Test
Exception in thread "main" java.lang.NoSuchMethodError: main

---

### Post by solarjeep on 2007-02-25
> **dxxvi said:**
> What does 

echo $CLASSPATH

say?

I get nothing.  A blank line then back to prompt.

---

### Post by solarjeep on 2007-02-25
> **Ragazzo said:**
> Do you have only one class per file (public and non-public)? 

Yes, only one class per file.  Everything I have done so far is very basic.

---

### Post by Ragazzo on 2007-02-25
> **solarjeep said:**
> Yes, only one class per file.  Everything I have done so far is very basic.

If you run "javap -verbose Root" and "javap -verbose OldRoot", where Root is the non-working version and OldRoot is the working one, it should print some info about the class files. Look for **SourceFile**, **minor version** and **major version** at the top of the listing and check if there is any difference in them.

---

