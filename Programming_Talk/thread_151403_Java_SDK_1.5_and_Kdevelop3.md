---
title: "Java SDK 1.5 and Kdevelop3"
date: 2006-03-27
forum: Programming Talk
---

### Post by SadaraX on 2006-03-27
Hello. I am trying to get kdevelop version 3.2.3 working working with writing Java programs. Specifically I am trying to get it working with Java 1.5. I've been writing C/C++ for years in Kdevelop3, so I'd like to keep it around and not go with Eclipse (just for familiarity sake). 

These are simple apps I writing, just for a class I am taking. They are not going to use any GTK or QT graphics, and in fact nothing really fancy at all. I just need very basic java writing. However, I am having trouble getting anything to compile in Kdevelop3. :( I suspect I am probably not creating a project correctly. 

Here's what I do. 

1) I am start up Kdevelop in multi-language mode, 
2) Select Java -> Ant Project -> Application
3) It pops up with some very basic looking code for the standard "Hello World" program
4) The code is literally this:

```

class Main{

    public static void main( String[] args ){
        System.out.println( "Hello, world!" );
    }
}
```

So, I add the standard at the very top of my code:

```

import java.util.*;
import java.io.*;

```

and then hit compile. It gives me an error about missing a program called 'ant', so I apt-get install ant, and try to compile again. 

I get this message: "Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/lib/tools.jar"

I am pretty confused by this point, so I make sure I've got some basics for java installed on the system to try to solve the problem. I run "apt-get install gcj sun-j2re1.5 sun-j2sdk1.5" but nothing helps, I continue to get the same error. I would really love some help with getting my project compiled. :)

---

### Post by mlind on 2006-03-28
Try *sudo update-alternatives --config java* and change to java 1.5.
Some programs may also need variable JAVA_HOME to be specified.

*java -version* should output Sun's Java, not Gnu's.

---

### Post by SadaraX on 2006-03-28
Thanks, that was really helpful. When I defined the JAVA_HOME variable, and made that change, it worked really well. Now I have another problem, but its really only a slight thing. 

Now I got my simple hello world program to compile, but I am having trouble executing it to see if it works properly. I open a console and move to the directory where the build has output a .class file. Here is my console output of my attempts to execute this program:

```

java ./Main.class
Exception in thread "main" java.lang.NoClassDefFoundError: //Main/class
java Main.class
Exception in thread "main" java.lang.NoClassDefFoundError: Main/class
java Main
Exception in thread "main" java.lang.NoClassDefFoundError: Main

```

Even using the jdb, all I can tell is that it cannot find the class that I can see right in front of me! ](*,) So I guess the next question is how to execute this .class file?

---

### Post by Drakx on 2006-03-28
[QUOTE=SadaraX]Thanks, that was really helpful. When I defined the JAVA_HOME variable, and made that change, it worked really well. Now I have another problem, but its really only a slight thing. 

Now I got my simple hello world program to compile, but I am having trouble executing it to see if it works properly. I open a console and move to the directory where the build has output a .class file. Here is my console output of my attempts to execute this program:

```

java ./Main.class
Exception in thread "main" java.lang.NoClassDefFoundError: //Main/class
java Main.class
Exception in thread "main" java.lang.NoClassDefFoundError: Main/class
java Main
Exception in thread "main" java.lang.NoClassDefFoundError: Main

```

Even using the jdb, all I can tell is that it cannot find the class that I can see right in front of me! ](*,) So I guess the next question is how to execute this .class file?[/QUOTE]

Try 

```
java Main
```

works a treat :), btw what tutorial are you using/following?

---

