---
title: "Java error code...."
date: 2008-09-24
forum: Programming Talk
---

### Post by brian77095 on 2008-09-24
I compiled this java program in windows and it worked there but, when I try to execute it in Ubuntu I get the following error codes...

Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner
   at A1ga4003893.<clinit>(A1ga4003893.java:12)
   at java.lang.Class.initializeClass(libgcj.so.81)


here is the program...

import java.util.*;

public class A1ga4003893

{

     static Scanner console = new Scanner(System.in);

     public static void main(String[] args)

     {

	int length;

	int width;

	

	System.out.println("Enter two numbers separated by spaces Length and Width of your rectangle.");

	length = console.nextInt();

	width = console.nextInt();

	System.out.println("Area = " + (length * width));

	System.out.println("Perimeter = " + ((2 * length) + (2 * width)));

     }

}


Like I said it work with its class file in win. but not in Ubuntu...

any help would be great!!!!

---

### Post by tinny on 2008-09-25
This is a classic GNU java runtime problem.

You should use the Sun Java environment.
```

sudo apt-get install sun-java6*

```

---

### Post by brian77095 on 2008-09-25
Great!!! Thanks for the help!!!


uhhh wait...

I am so new newbs call me new....  Could you elaborate a bit?

If I type that string you gave me what will happen?

I am guessing it will install ?? an upgraded java?

thanks again...

---

### Post by tinny on 2008-09-25
> **brian77095 said:**
> Great!!! Thanks for the help!!!


uhhh wait...

I am so new newbs call me new....  Could you elaborate a bit?

If I type that string you gave me what will happen?

I am guessing it will install ?? an upgraded java?

thanks again...

Yep :)

To confirm that it worked:

Type:
```

java -version

```

Output:
```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

Type
```

javac -version

```

Output:
```

javac 1.6.0_06

```

What are you using to code your Java in Ubuntu? Or are you just running this file from the command line?

---

### Post by NovaAesa on 2008-09-25
You should type the string into the terminal window and it will install the java runtimes from Sun. Although I'm not really sure why tinny suggested all those packages. Normally I would just use use:
```
sudo apt-get install sun-java6-bin
```

EDIT: tinny beat me about where to type it :P

---

### Post by tinny on 2008-09-25
> **NovaAesa said:**
> You should type the string into the terminal window and it will install the java runtimes from Sun. Although I'm not really sure why tinny suggested all those packages. Normally I would just use use:
```
sudo apt-get install sun-java6-bin
```

EDIT: tinny beat me about where to type it :P

Shhhhhhh... Im a little lazy :) Im sure that the OP would want the Sun JDK too etc...

---

### Post by jespdj on 2008-09-25
> **brian77095 said:**
> I am so new newbs call me new....  Could you elaborate a bit?
The class java.util.Scanner was added in Java version 5 (or 1.5, Sun has weird version numbers for Java). You were running an older version of Java (most likely Java 1.4) - so it complains that it can't find the class java.util.Scanner that you were trying to use.

---

### Post by tinny on 2008-09-25
> **jespdj said:**
> The class java.util.Scanner was added in Java version 5 (or 1.5, Sun has weird version numbers for Java). You were running an older version of Java (most likely Java 1.4) - so it complains that it can't find the class java.util.Scanner that you were trying to use.

You would think that it is something simple like that. However there does seem to be something weird going on with GNU Java.

Ive seen this problem answered before by installing Sun Java.

---

### Post by jespdj on 2008-09-25
GNU Java is an (incomplete) implementation of Java 1.4, so if he's running GNU Java, he would get a NoClassDefFoundError when trying to use java.util.Scanner.

I wasn't saying that your solution to install Sun Java 6 wasn't good, I was just explaining what the error message means and why it happens if you use a Java version older than Java 5.

---

### Post by brian77095 on 2008-09-27
Thanks everyone for the info!!  I have not done any compileing in Ubuntu yet.  Like I said this program was for a class and with huricane Ike I had a few set backs...

If I do the install of sun java like you said I sould just be able to do a comand like...

cjava (file) to compile it in the CL??

also I cant seem to figure out how to change directories or folders form the CL that have a space....for example...

the folder name is "school stuff"

I have tried cd school stuff  ,  cd school_stuff 

all sorts of things finally I just changed the folder name in GUI to schoolstuff!  LOL that worked..

so if a folder has a space how do you get to in in CL?

---

### Post by brian77095 on 2008-09-27
Hmm  not sure what happend...

I did

:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

then...

:~$ sudo apt-get install sun-java6*

and got...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting sun-javadb-doc for regex 'sun-java6*'
Note, selecting sun-javadb-demo for regex 'sun-java6*'
Note, selecting sun-javadb-client for regex 'sun-java6*'
Note, selecting sun-java5-bin for regex 'sun-java6*'
Note, selecting sun-javadb-core for regex 'sun-java6*'
Note, selecting sun-java5-doc for regex 'sun-java6*'
Note, selecting sun-java6-source for regex 'sun-java6*'
Note, selecting ia32-sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-java5-jdk for regex 'sun-java6*'
Note, selecting sun-java5-jre for regex 'sun-java6*'
Note, selecting sun-javadb-common for regex 'sun-java6*'
Note, selecting sun-java5-src for regex 'sun-java6*'
Note, selecting sun-java5-plugin for regex 'sun-java6*'
Note, selecting sun-java6-bin for regex 'sun-java6*'
Note, selecting sun-java6-javadb for regex 'sun-java6*'
Note, selecting sun-java6-doc for regex 'sun-java6*'
Note, selecting ia32-sun-java6-plugin for regex 'sun-java6*'
Note, selecting sun-java5-fonts for regex 'sun-java6*'
Note, selecting sun-java5-demo for regex 'sun-java6*'
Note, selecting sun-java6-jdk for regex 'sun-java6*'
Note, selecting sun-java6-jre for regex 'sun-java6*'
Note, selecting ia32-sun-java5-bin for regex 'sun-java6*'
Note, selecting sun-javadb-javadoc for regex 'sun-java6*'
Note, selecting sun-java6-src for regex 'sun-java6*'
Note, selecting sun-java6-plugin for regex 'sun-java6*'
Note, selecting ia32-sun-java6-bin for regex 'sun-java6*'
Note, selecting sun-java5-source for regex 'sun-java6*'
Note, selecting sun-java6-fonts for regex 'sun-java6*'
Note, selecting sun-java6-demo for regex 'sun-java6*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java5-fonts: Conflicts: ttf-lucida
  sun-java6-fonts: Conflicts: ttf-lucida
E: Broken packages


followed by...

:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


did I need to uninstall the first java??

---

### Post by myrtle1908 on 2008-09-28
> **brian77095 said:**
> 
If I do the install of sun java like you said I sould just be able to do a comand like...

cjava (file) to compile it in the CL??


No.  The name of the compiler executable is 'javac'.  So to compile a program named 'test.java' you would type:

```
javac test.java
```

> **brian77095 said:**
> 
also I cant seem to figure out how to change directories or folders form the CL that have a space....for example...

the folder name is "school stuff"

I have tried cd school stuff  ,  cd school_stuff 

all sorts of things finally I just changed the folder name in GUI to schoolstuff!  LOL that worked..

so if a folder has a space how do you get to in in CL?

Use quotes ...

```
cd "school stuff"
```

---

### Post by myrtle1908 on 2008-09-28
> **brian77095 said:**
> Hmm  not sure what happend...


---8< snipped >8---


did I need to uninstall the first java??


Try this step-by-step guide to install and configure Ubuntu to use Sun Java.

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

---

### Post by sheazar on 2008-09-28
> **myrtle1908 said:**
> 

Use quotes ...

```
cd "school stuff"
```
You can also use \ 
```
cd school\ stuff
```

But usually I would say you'll probably only need to type ```
cd sch<tab>
``` for tab completion. (to specefy by <tab> you should press tab not write it :))

---

### Post by brian77095 on 2008-09-28
Great stuff!!  I am up and running...:) err sort of programming...

thanks all for the help...

---

