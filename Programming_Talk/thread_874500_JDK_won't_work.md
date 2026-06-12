---
title: "JDK won't work"
date: 2008-07-30
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-07-30
Hey All

I'm trying to work on a java project, but my JDK seems to be messed up.  It gives me errors in simple hello world programs or when I do things like create new objects, etc.  I've been working with java for a little while now, so I know that there's no errors in the code it's compiling.  I installed it with ```
 sudo apt-get install sun-java6-jdk
```
I'm getting frustrated with it because I'm pressed for time with this project but can't code.  Can anyone tell me why my JDK isn't working?  
Thanks a lot.

---

### Post by tinny on 2008-07-30
> **the_real_fourthdimension said:**
> Hey All

I'm trying to work on a java project, but my JDK seems to be messed up.  It gives me errors in simple hello world programs or when I do things like create new objects, etc.  I've been working with java for a little while now, so I know that there's no errors in the code it's compiling.  I installed it with ```
 sudo apt-get install sun-java6-jdk
```
I'm getting frustrated with it because I'm pressed for time with this project but can't code.  Can anyone tell me why my JDK isn't working?  
Thanks a lot.

A few things to check.

```

java -version
javac -version

```

Can you post back the output.

Also, are you using an IDE? If so you need to check that the IDE is pointing to the correct java complier and runtime.

---

### Post by the_real_fourthdimension on 2008-07-30
Thanks.
```

me@my-machine:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
me@my-machine:~$ javac -version
javac 1.6.0_06

```
Yeah, I thought it might be just the IDE, but I've tried three of them and compiling via the command line with the same results.  Import statements aren't working, creating new objects gives me compile errors, etc.

---

### Post by Zugzwang on 2008-07-30
> **the_real_fourthdimension said:**
> 
Yeah, I thought it might be just the IDE, but I've tried three of them and compiling via the command line with the same results.  Import statements aren't working, creating new objects gives me compile errors, etc.

Please post a simple hello world you wrote, where you put that file, which command you use for compiling in which directory, which errors you get (please copy&paste) and the contents of your CLASSPATH variable.

---

### Post by the_real_fourthdimension on 2008-07-30
Well, I removed java and purged/reinstalled it again, and now object creation and almost everything else works...  the only thing that is still giving me trouble is importing.  When I try to import the Sacnner class ([http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)), I get ```
The import java.util.Scanner cannot be resolved
```  Is the version of JDK I got working too old to use Scanner?
Thanks.

---

### Post by tinny on 2008-07-30
> **the_real_fourthdimension said:**
> Well, I removed java and purged/reinstalled it again, and now object creation and almost everything else works...  the only thing that is still giving me trouble is importing.  When I try to import the Sacnner class ([http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)), I get ```
The import java.util.Scanner cannot be resolved
```  Is the version of JDK I got working too old to use Scanner?
Thanks.

Your using JDK 6, right? So no its not too old.

Do you get this above problem when compiling at the command line?

---

### Post by hod139 on 2008-07-30
How did you install java?

The following should work and set every thing up correctly.  First, install
```

sudo apt-get install sun-java6-jdk

```
And set up
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by the_real_fourthdimension on 2008-07-30
Compiling this from the command line:```

import java.util.Scanner;
public class test1 {
public static void main(String[] args) {

Scanner sc = new Scanner();
}

}

```
gives me this:
```
test1.java:5: cannot find symbol
symbol  : constructor Scanner()
location: class java.util.Scanner
Scanner sc = new Scanner();
             ^
1 error

```

In eclipse:
```

The import java.util.Scanner cannot be resolved.
Scanner cannot be resolved to a type.

```

and in geany:
```

cannot find symbol
symbol: constructor Scanner()
location: class java.util.Scanner
Scanner sc = new Scanner();
^

```
I used the suggested method to reinstall java before posting this.
Thanks for all the help.  I'm really hoping that I'm just making some stupid mistake that is easy and quick to fix...

---

### Post by tinny on 2008-07-30
> **the_real_fourthdimension said:**
> Compiling this from the command line:```

import java.util.Scanner;
public class test1 {
public static void main(String[] args) {

Scanner sc = new Scanner();
}

}

```
gives me this:
```
test1.java:5: cannot find symbol
symbol  : constructor Scanner()
location: class java.util.Scanner
Scanner sc = new Scanner();
             ^
1 error

```

In eclipse:
```

The import java.util.Scanner cannot be resolved.
Scanner cannot be resolved to a type.

```

and in geany:
```

cannot find symbol
symbol: constructor Scanner()
location: class java.util.Scanner
Scanner sc = new Scanner();
^

```
I used the suggested method to reinstall java before posting this.
Thanks for all the help.  I'm really hoping that I'm just making some stupid mistake that is easy and quick to fix...

Scanner doesnt have a default constructor.

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)

Try using one of the parameterised constructors :)

E.g.
```

new Scanner(System.in);

```

In eclipse this should show up in the "Problems" view.

---

### Post by the_real_fourthdimension on 2008-07-31
Thanks!  Now geany and the terminal compile it correctly.  Eclipse, however, still gives me the same errors it gave me before.  The same errors it gave me when I had tried to use the scanner class with an older version of java.  Is it possible that it's pointing to an older version of java?  How do I update it's path?
Thanks a lot!  I feel stupid for those earlier mistakes, but at least they were easliy fixed. :)

---

### Post by ceclauson on 2008-07-31
It might be the case that Eclipse is using an older version of the compiler.  To check and possibly change this, go to Project > Properties, and a dialog should come up.  On the list on the left, select "Java Compiler", and on the right you should see what version of Java you're using.  To change this, click the "Enable Project Specific Settings", and you're good to go.

---

### Post by the_real_fourthdimension on 2008-07-31
Thanks.  I changed that from 5.0 to 6.0 and restarted eclipse, but I'm getting the same error on import java.util.Scanner.  I don't see why it still isn't working.

---

### Post by tinny on 2008-07-31
2 more things to check.

1. Make sure that the "JRE System Library" is setup as a library for your project.

Right click your project "Properties" > "Java build path", libraries lab. You should see "JRE System Library..." if you are setup correctly. If not click "Add library" and add "JRE System Library".

2. Make sure you haven't overridden your workspace complier settings at the project level.

Right click your project "Properties" > "Java Compiler", make sure that "Enable project specific settings" is NOT checked.

Good luck :)

---

### Post by the_real_fourthdimension on 2008-07-31
Hmm...  Both of those seem to be set up correctly...  So that brings up two questions.  One is the obvious how do I fix it, and two - what could I have done to mess things up this badly. :)

---

### Post by the_real_fourthdimension on 2008-08-05
](*,)

---

### Post by tinny on 2008-08-05
Can you post screen shots of the following.

1. "Windows" > "Preferences" > "Java" > "Installed JREs"

2. Right click project > "Properties" > "Java Compiler"

3. Right click project > "Properties" > "Java Build path" > libraries tab.

---

### Post by the_real_fourthdimension on 2008-08-06
Sure.

---

### Post by tinny on 2008-08-06
You are still using the GNU version of the JDK.

In &#8220;Window&#8221; > &#8220;Preferences&#8221; > &#8220;Installed JREs&#8221; you need to &#8220;Add&#8221; the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

---

### Post by the_real_fourthdimension on 2008-08-06
Thank you so much!!!!

---

### Post by tobias-mansson on 2008-10-18
Finally someone with a good answer. Been searching for this answer for ages.

---

### Post by Shin_Gouki2501 on 2008-10-18
I'm still not sure but:
Those "gcj"-stuff really messes up the java experience of many java "newcomers". I hope open jdk will come to ubuntu soon...and that it will work "better".

---

### Post by jac0117 on 2008-11-15
> **tinny said:**
> You are still using the GNU version of the JDK.

In “Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

Thank you.... This worked for me as well

---

### Post by Klayy on 2008-11-16
> **tinny said:**
> You are still using the GNU version of the JDK.

In “Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

Words of wisdom. You saved my life there

---

### Post by The Resident Expert on 2008-11-19
> **Klayy said:**
> Words of wisdom. You saved my life there

Mine as well!

---

### Post by jespdj on 2008-11-19
> **Shin_Gouki2501 said:**
> I'm still not sure but:
Those "gcj"-stuff really messes up the java experience of many java "newcomers". I hope open jdk will come to ubuntu soon...and that it will work "better".
OpenJDK is the default Java on Ubuntu 8.10, and ofcourse it's much better than GNU Java (GCJ).

---

### Post by houedanou on 2008-11-26
> **tinny said:**
> 2 more things to check.

1. Make sure that the "JRE System Library" is setup as a library for your project.

Right click your project "Properties" > "Java build path", libraries lab. You should see "JRE System Library..." if you are setup correctly. If not click "Add library" and add "JRE System Library".

2. Make sure you haven't overridden your workspace complier settings at the project level.

Right click your project "Properties" > "Java Compiler", make sure that "Enable project specific settings" is NOT checked.

Good luck :)

Thank you so much...

---

### Post by uncibex on 2009-04-02
> **tinny said:**
> You are still using the GNU version of the JDK.

In &#8220;Window&#8221; > &#8220;Preferences&#8221; > &#8220;Installed JREs&#8221; you need to &#8220;Add&#8221; the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.
Thank you so much!! Every time I've updated ubuntu I've had to fix this again and have had to just stumble around until I found something that miraculously worked.  I'm so glad to have found someone who knows what's going on!

---

### Post by alchi on 2009-08-17
> **tinny said:**
> You are still using the GNU version of the JDK.

In “Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

That's just what I was lookin for?

Thanx a lot

---

### Post by lixinsbgtf on 2012-04-17
> **tinny said:**
> You are still using the GNU version of the JDK.

In “Window” > “Preferences” > “Installed JREs” you need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.

Thank you so much!!!

---

