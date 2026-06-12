---
title: "[SOLVED] Javac/Java Issues - Cannot find class."
date: 2008-10-02
forum: Programming Talk
---

### Post by benpage26 on 2008-10-02
Hello everyone, 
I've already searched the forum and I can't find a solution to the issue i am having.

I have a class BlogReader that I have written in NetBeans, I have also managed to compile and run it through netbeans.  However, i want my program to accept command-line arguments so it would be much easier if i could launch the program from the command line.

I navigate to the BlogReader/ folder, where BlogReader.java is located and type: ```
javac BlogReader.java
```.

This works fine and creates a .class file, but then when I use ```
java BlogReader
``` i get the following error (i am not typing .class at the end)

```
acws-1062% java BlogReader
Exception in thread "main" java.lang.NoClassDefFoundError: BlogReader (wrong name: BlogReader/BlogReader)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

If i go up a directory and type ```
java BlogReader/BlogReader
``` (this is because the class file is in a directory named BlogReader) it works fine

```
acws-1062% cd ..
acws-1062% ls
BlogReader  CMDTest
acws-1062% java BlogReader/BlogReader
No Arguments Supplied at Command Line!

```


why is this? something to do with class path?  I have tried "java -cp . BlogReader" and i get a similar error to the first.

Can anybody help me please?
Ben

---

### Post by MarkieB on 2008-10-02
no longer participating in ubuntuforums.org

---

### Post by leg on 2008-10-02
Does your BlogReader contain a package statement?

---

### Post by arcanus on 2008-10-02
Make sure that the class name and the file name is the same, could be the problem

EDIT:

No it shouldnt produce that error... Mind posting the content of your .java file in a code block?

---

### Post by jespdj on 2008-10-02
This explains exactly what's wrong:
> Exception in thread "main" java.lang.NoClassDefFoundError: BlogReader **(wrong name: BlogReader/BlogReader)**
Did you put a
```
package BlogReader;
```
in your code?

Your directory structure must match the package structure, and you must be in the correct directory. Probably the easiest thing to get it working is remove the package statement from your source code.

For more information on working with packages, see [Sun's Java Tutorials - Packages](http://java.sun.com/docs/books/tutorial/java/package/index.html).
> **benpage26 said:**
> ```
acws-1062% cd ..
acws-1062% ls
BlogReader  CMDTest
acws-1062% java BlogReader/BlogReader
No Arguments Supplied at Command Line!

```

why is this? something to do with class path?  I have tried "java -cp . BlogReader" and i get a similar error to the first.
Well, what did you expect? You didn't supply any command line arguments to your program, so it's complaining that you didn't supply them. Try:
```
java BlogReader/BlogReader hello
```
Note that "hello" is the command line argument to the Java program here.

---

### Post by benpage26 on 2008-10-02
```
 /*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */
package BlogReader;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.Properties;

/**
 *
 * @author ug73bxp
 */
public class BlogReader {

    private static URL target;

    public static void main(String[] args) {
        
        // Set up Bham Proxy
        useBhamWebcache();

        parseArgs(args); // Decide what to do and do it
    }

    /**
     * Parse the args array to decide what action must be taken, and 
     * take the action required.
     * @param args
     */
    private static void parseArgs(String[] args) {
        // Quit if no arguments
        if (args.length == 0) {
            System.err.println("No Arguments Supplied at Command Line!");
        // TODO: Print Basic help from Here
        } else {
            // Contine if there are arguments
            if (args[0].equals("-k")) {
                // args[1] is the keyword
                System.out.println("Searching Blog for Keyword: " + args[1]);
                System.err.println("NOT YET IMPLEMENTED!");
            } else if (args[0].equals("-u")) {
                // args[1] is a url
                getUrl(args[1]); // TODO: Possible error if no arg after -u
            } else {
                // Assume url is at args[0]
                getUrl(args[0]);
            }
        }

    }

    /**
     * Visits specified url and downloads HTML from that location, aslo prints it
     * to standard output.
     * @param string
     */
    private static void getUrl(String string) {
        try {
            target = new URL(string);
        } catch (MalformedURLException mfue) {
            System.err.println("FATAL ERROR:\nMalformed URL: " + string);
            System.err.println("Make sure that the protocol is recognisable");
        }
    // Url is correctly formed - fetch blog!
        System.err.println("NOT YET IMPLEMENTED");
    }

    /**
     *  Sets system Properties to use bham.ac webcache
     * 
     */
    private static void useBhamWebcache() {
        Properties properties = System.getProperties();
        properties.put("http.proxyHost", "webcache");
        properties.put("http.proxyPort", "3128");
    }
}
```

---

### Post by benpage26 on 2008-10-02
> **MarkieB said:**
> ISTR that when the javac/java versions don't match, you get NoClassDefFoundError

try```
java -version
javac -version
``` to check

Interesting Hypothesis, let me just check.

```
tinky-winky% java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
tinky-winky% javac -version
javac 1.6.0_06
tinky-winky% ls

```
Seems they are the same, but does the "mixed mode" for the java command mean anything could change?  
(Machine name is different because i am at home using remote access, but i have double checked and the problem persists via remote access)

---

### Post by benpage26 on 2008-10-02
> **jespdj said:**
> This explains exactly what's wrong:

Did you put a
```
package BlogReader;
```
in your code?

Your directory structure must match the package structure, and you must be in the correct directory. Probably the easiest thing to get it working is remove the package statement from your source code.

For more information on working with packages, see [Sun's Java Tutorials - Packages](http://java.sun.com/docs/books/tutorial/java/package/index.html).

Well, what did you expect? You didn't supply any command line arguments to your program, so it's complaining that you didn't supply them. Try:
```
java BlogReader/BlogReader hello
```
Note that "hello" is the command line argument to the Java program here.

There is a "package BlogReader" statement in my code. :) but I would rather get it to work without removing the package statement, as wouldn't removing that stop it working in netbeans so well.

Thanks for the link to the tutorial i will read up on that.

And regarding the "no command line args" error i know i didn't supply any arguments, that was to illustrate that the program works when the working directory is the directory above that which contains the .class file.  The error code is generated from within the program I wrote [posted above]("http://ubuntuforums.org/showpost.php?p=5896020&postcount=6").

Thanks also to leg and arcanus (PS sorry for the double post and being a little rude posting just the code block, not sure what i was thinking :D)

---

### Post by jespdj on 2008-10-03
> **benpage26 said:**
> There is a "package BlogReader" statement in my code. :) but I would rather get it to work without removing the package statement, as wouldn't removing that stop it working in netbeans so well.
Then you need to, as I said, make sure that the directory structure matches the package structure, and you must make sure that the base directory is in the classpath.

In other words, your BlogReader.java and BlogReader.class file should be in a directory named BlogReader, and you have to make sure that directory is in the classpath when you run the program. For example:
```

/home/ben$ mkdir BlogReader
/home/ben$ mv BlogReader.java BlogReader/
/home/ben$ javac BlogReader/BlogReader.java

/home/ben$ java BlogReader.BlogReader

# If you are in another directory, make sure the directory that contains the BlogReader directory is in the classpath:

/home/ben/some/other/directory$ java -classpath /home/ben BlogReader.BlogReader

```

---

### Post by benpage26 on 2008-10-15
Thank you everyone for your help :D

I solved it with setting the class path to the correct thing.

---

