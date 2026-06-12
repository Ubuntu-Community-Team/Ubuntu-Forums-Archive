---
title: "Java refuses to import libraries"
date: 2011-09-27
forum: Programming Talk
---

### Post by cosners on 2011-09-27
Whenever I try to run a program with a library, it always gives me this
```

>javac *.java
FileIO.java:1: ';' expected
import java.util.Scanner
                        ^
1 error
>Exit code: 1

```How do I fix it? The program runs just fine if I don't import any libraries, and I already made sure to install the JDK. I'm using SciTE to edit this program, if that info helps.

The program I was trying to run:
```

import java.util.Scanner

public class FileIO
{
    public static void main (String[] args)
    {
    System.out.println("Enter first and last name.");
    Scanner name = new Scanner (System.in);
    String first = name.next();
    String second = name.next();
    System.out.println("Welcome " + first + " " + second);
    }
    
}

```

---

### Post by karlson on 2011-09-27
> **cosners said:**
> Whenever I try to run a program with a library, it always gives me this
```

>javac *.java
FileIO.java:1: ';' expected
import java.util.Scanner
                        ^
1 error
>Exit code: 1

```

Have you actually tried doing what javac tells you to do?  Namely put a ; at the end of the import statement.

---

