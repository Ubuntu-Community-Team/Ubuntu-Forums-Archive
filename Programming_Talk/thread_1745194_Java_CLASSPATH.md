---
title: "Java CLASSPATH ?"
date: 2011-04-30
forum: Programming Talk
---

### Post by Z.K. on 2011-04-30
I entered echo $CLASSPATH from the command line and received a blank line.  I did not actually print a path of any kind or give an error.  Does this mean the CLASSPATH is not set and if so how do I set it properly?

:?

---

### Post by NovaAesa on 2011-04-30
You are correct, this means it's not set. To set, use:
```
export CLASSPATH=/path/to/wherever
```

---

### Post by Z.K. on 2011-04-30
> **NovaAesa said:**
> You are correct, this means it's not set. To set, use:
```
export CLASSPATH=/path/to/wherever
```

Thanks, that is what I thought.

---

### Post by jespdj on 2011-05-04
It's better not to set a global CLASSPATH environment variable, because it affects all Java programs that you'd run on your computer.

Instead, use the -cp option on the command line to specify the classpath for the program you're running. For example:

java -cp myproject/classes org.myproject.MyProgram

(where your compiled *.class files are in the directory myproject/classes).

---

### Post by Kelvari on 2011-09-03
> **NovaAesa said:**
> You are correct, this means it's not set. To set, use:
```
export CLASSPATH=/path/to/wherever
```

I tried that, and there was no change in the $CLASSPATH command. Should it be run with sudo to set it, or is there something else that I need to do? I'm asking as I need to have a specific .jar file for a class in school, and can't even compile my assignments if I can't get Java to recognize the .jar file.

---

### Post by dwhitney67 on 2011-09-03
> **Kelvari said:**
> I tried that, and there was no change in the $CLASSPATH command. Should it be run with sudo to set it, or is there something else that I need to do? I'm asking as I need to have a specific .jar file for a class in school, and can't even compile my assignments if I can't get Java to recognize the .jar file.

Why not employ jespdj's advice, and use the -cp option when you are compiling your code?

Something like:
```

javac -cp /path/to/specific.jar App.java

```

---

