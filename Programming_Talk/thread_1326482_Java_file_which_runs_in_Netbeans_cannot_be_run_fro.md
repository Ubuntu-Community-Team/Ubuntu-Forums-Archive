---
title: "Java file which runs in Netbeans cannot be run from terminal..."
date: 2009-11-14
forum: Programming Talk
---

### Post by emigrant on 2009-11-14
hi all.
a java file which i can run from Netbeans cannot be run from the terminal.
though i can compile it without an error from the terminal, when i run it i get the following error:

```

$javac Averager.java 
$ java Averager 
Exception in thread "main" java.lang.NoClassDefFoundError: Averager (wrong name: javainsixdays/Averager)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: Averager. Program will exit.

```

iv added this path to my bashrc (not sure whether this is correct)

```
PATH=$PATH:/usr/lib/jvm/java-6-openjdk/jre/bin/java
```

---

### Post by januzi on 2009-11-14
I'm not sure, but:
> 
Exception in thread "main" java.lang.NoClassDefFoundError: Averager (wrong name: javainsixdays/Averager)
gives a clue. Could You post class definition from the Averager.java ? Just few lines with the 
> 
public class Averager {


You could check:
> 
java -cp . package/MainClass

or
> 
java -jar file.jar


---

### Post by emigrant on 2009-11-14
here is the full code.
by the way, in my first post i forgot to pass the command line arguments.
but even if i pass them, still i get the same error.

```

package javainsixdays;

public class Averager {

    public static void main (String arg[])
    {
        int sum=0;
        if(arg.length>0)
        {
            System.out.println("The inputs are: ");
            for(int i=0; i<arg.length; i++)
            {
                sum=sum+Integer.parseInt(arg[i]);
                System.out.print(arg[i]+" ");
            }

            System.out.println();
            System.out.println("Sum is: "+sum);
            System.out.println("Average is: "+ (float)sum/arg.length);
        }

    }

}
```

---

### Post by januzi on 2009-11-14
In that case: [http://www.jarticles.com/package/package_eng.html](http://www.jarticles.com/package/package_eng.html)

---

### Post by doas777 on 2009-11-14
what exactly are you typing into the terminal?
is it
```
java -jar <jarfilename>
```

---

### Post by emigrant on 2009-11-14
> **doas777 said:**
> what exactly are you typing into the terminal?
is it
```
java -jar <jarfilename>
```

no im typing
```

javac Averager.java
java Averager 22, 55, 77, 77
```

---

### Post by doas777 on 2009-11-14
try cd ing into the directory, and add ./ to be begining of each filename

---

### Post by PaulM1985 on 2009-11-14
Since your file is in a package called javainsixdays (this is from the line:
package javainsixdays;
), 

the file needs to be in a folder called javainsixdays.

To run your program you need to be in the folder which contains javainsixdays and then use:
java javainsixdays/Averager

So for example, in a folder "My Files" create a folder "javainsixdays".  Put Averager.java in the folder javainsixdays.  Navigate in the terminal to the "My Files" folder.  Use the command:

javac javainsixdays/*.java

to compile all files

java javainsixdays/Averager

to run your program.

Paul

---

### Post by emigrant on 2009-11-14
> **PaulM1985 said:**
> Since your file is in a package called javainsixdays (this is from the line:
package javainsixdays;
), 

the file needs to be in a folder called javainsixdays.

To run your program you need to be in the folder which contains javainsixdays and then use:
java javainsixdays/Averager

So for example, in a folder "My Files" create a folder "javainsixdays".  Put Averager.java in the folder javainsixdays.  Navigate in the terminal to the "My Files" folder.  Use the command:

javac javainsixdays/*.java

to compile all files

java javainsixdays/Averager

to run your program.

Paul

yes, this worked. 
thank you very much all you guys. :)

---

### Post by emigrant on 2009-11-14
so i see, that if i need to just run a single file in the desktop, i just need to comment out the package name.
:)

---

### Post by PaulM1985 on 2009-11-14
> **emigrant said:**
> so i see, that if i need to just run a single file in the desktop, i just need to comment out the package name.
:)

Thats right.

It may be useful to look into packages.  They can be useful as there is an access modifier that limits access only to packages.  I guess you probably know about public and private already, but there is a "default" access modifier for packages.  This can be really useful when structuring large programs and creating components.

Paul

---

### Post by Rishav123 on 2012-08-05
It helped me a lot tooo...........
Thanks:):P:KS

---

