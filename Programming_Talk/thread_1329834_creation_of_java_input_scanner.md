---
title: "creation of java input scanner"
date: 2009-11-17
forum: Programming Talk
---

### Post by andyb88 on 2009-11-17
I am writing an RMI program in Java for Uni and within the program i need to get some user input. I am doing this using a Scanner
```
Scanner in = new Scanner(System.in);
String line = in.nextLine();
```

When I run the program using NetBeans it runs right through creating the Scanner and waits for enter to be pressed at in.nextLine() (which is exactly what I expect it to do).

But when I run the program in a Ubuntu terminal it waits for the enter key to be pressed when it calls the constructor. Is this 'normal' behaviour within the terminal? I certainly haven't had this problem before. I am running the program using the command ```
java myprogram
```

Thanks in advance for any help,

Andy

---

### Post by NovaAesa on 2009-11-18
No, this is not normal behaviour. It should only wait for enter to pressed once in.nextLine() is called.

Post the exact code you are using and I can test it here if you want.

---

### Post by andyb88 on 2009-11-18
Thanks for getting back to me.

> No, this is not normal behaviour. It should only wait for enter to pressed once in.nextLine() is called.
Thats what I thought. I cant post the whole code because It uses several classes etc but the following code has the same problem.
```
import java.util.Scanner;

public class test {

    public static void main(String args[]) {
	System.out.println("Creating Scanner");
	Scanner in = new Scanner(System.in);
	System.out.println("Created Scanner, type something...");
	String str = in.nextLine();
	System.out.println("You typed: " + str);

    }
}
```
It gets as far as printing "Creating Scanner" and then waits for enter to be pressed, then asks for input and no matter what is typed the value of 'str' is always an empty string.

andy@andy-laptop-ubuntu:~/Desktop$ java test 
Creating Scanner
   *(i had to press enter here....)*
Created Scanner, type something...
SOMETHING
You typed:

---

### Post by dwhitney67 on 2009-11-18
Your code works fine for me.
```

$ javac test.java
$ java test
Creating Scanner
Created Scanner, type something...
this is a test
You typed: this is a test

```

---

### Post by travmanx on 2009-11-18
> **dwhitney67 said:**
> Your code works fine for me.
```

$ javac test.java
$ java test
Creating Scanner
Created Scanner, type something...
this is a test
You typed: this is a test

```

Same here, I used Eclipse and terminal to test it out. Not sure whats wrong with yours. Have you fiddled around with java settings?

See if you have problems this way....

```

import java.util.Scanner;
public class proj1
       {
		 static Scanner in = new Scanner(System.in);
		    public static void main(String args[]) 
                    {

			System.out.println("Created Scanner, type something...");
			String str = in.nextLine();
			System.out.println("You typed: " + str);
		    }
	}

```

Essentially does the same thing, however scanner is called before main is read.

---

### Post by NovaAesa on 2009-11-18
andyb88, I can confirm that the code you posted also works for me.
```

ps@pris:~/Desktop$ javac t.java 
ps@pris:~/Desktop$ java t
Creating Scanner
Created Scanner, type something...
aoeu
You typed: aoeu
ps@pris:~/Desktop$ 

```


EDIT: which java are you using? I.e. what's the output of "java -version"?

---

### Post by CharlesBob on 2010-11-14
[SIZE=3]The solution described above changes the quirky behavior, but does not cure it.  The problem seems to be related to some difference in the terminal application on laptops and netbooks.  Scanner/System.in code which runs as expected on a desktop version of Ubuntu shows the quirky behavior reported by Andy when run on a laptop or netbook.  Ubuntu should fix this.  I am running

java version "1.5.0"
gij (GNU libgcj) version 4.4.3

and

 Ubuntu 10.04 LTS

I can provide more hardware system information upon request.

[/SIZE]

---

### Post by NovaAesa on 2010-11-15
I would suggest testing it with Oracle's JVM. If the problem exists in GNU's version but not Oracle's, please file a bug upstream.

---

### Post by CharlesBob on 2010-11-15
I filed a bug report with Ubuntu.  After further research I have found that the GNU version of JVM seems to be the problem.  Under the GNU version the quirky behavior exists.  I down loaded the OpenJDK JVM and the program behaves correctly.  An analysis of the differences between my desktop and laptop follows.

The results produced by Scanner on a desktop verion of Ubuntu 10.0 differ from those produced on a laptop version.  The laptop version produces results which render the program quirky to use.

This sample program demonstrates the difference in behavior:

import java.util.Scanner;
public class BadScanner
       {
            public static void main(String args[]) 
                    {
                        System.out.println("About to create Scanner");
                        Scanner in = new Scanner(System.in);
            System.out.println("Created Scanner, type something...");
            String str = in.nextLine();
            System.out.println("You typed: " + str + " ...now type something else");
            str = in.nextLine();
            System.out.println("And then you typed: " + str);
            }
    }

*************************************************************************************************

Desktop environment is:

Ubuntu 10.04 LTS - the Lucid Lynx

chuck@Linux-desktop:~/pierce/cs552/test$ javac -version
javac 1.6.0_18

[SIZE=2][COLOR=Navy][COLOR=Red]chuck@Linux-desktop:~/pierce/cs552/test$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.2) (6b18-1.8.2-4ubuntu2)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)[/COLOR]
[/COLOR][/SIZE]
Results of running program on desktop are exactly as expected.

chuck@Linux-desktop:~/pierce/cs552/test$ java BadScanner
About to create Scanner
Created Scanner, type something...
Hello
You typed: Hello ...now type something else
World
And then you typed: World
chuck@Linux-desktop:~/pierce/cs552/test$

*************************************************************************************************

Results of running program on laptop are NOT as expected.  This is from execution of the class file created on the desktop.  (Note also that according to Update Manager laptop system is up to date.)

chuck@chuck-laptop:~/pierce/cs552/test$ java BadScanner
About to create Scanner
Hello
Created Scanner, type something...
World
You typed: Hello ...now type something else
Goodbye
And then you typed: World
chuck@chuck-laptop:~/pierce/cs552/test$

Laptop environment is:

Ubuntu 10.04 LTS - the Lucid Lynx

chuck@chuck-laptop:~/pierce/cs552/test$ javac -version
gcj-4.4 (Ubuntu 4.4.3-1ubuntu2) 4.4.3
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[SIZE=2][COLOR=Red]chuck@chuck-laptop:~/pierce/cs552/test$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/COLOR][/SIZE]

*************************************************************************************************

---

