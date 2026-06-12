---
title: "Trouble programming in java-reading in packages"
date: 2008-06-22
forum: Programming Talk
---

### Post by lordhaworth on 2008-06-22
Hey all,
Im trying to get java fully working on hardy, i can compile and run basic programs fine. When i try to compile a program which involves

import chapman.io.*;

i get the following message 

package chapman.io does not exist

I have read elsewhere that I may need to do something like set the classmark= 'something or other' but not sure what that would be.

Any help on how to get java reading in packages such as this would be appreciated.

---

### Post by apoth on 2008-06-22
What's your directory structure, what command are you running to do the compile?

It's the classpath.

---

### Post by lordhaworth on 2008-06-22
I am using javac 'name'.java to compile

directory structure:
Is this kind of thing what your after?
lordhaworth@the-fort:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-openjdk/jre/bin/java' to provide 'java'.


cheers

---

### Post by Diabolis on 2008-06-22
Packages are actually folders. So what this line **import chapman.io.*;** is saying, is that the classes that must be imported are:

all the classes(*) inside the folder io, which is inside the folder chapman, which is in the same directory where the java class that you are compiling is.

If your package(chapman folder) is not in the same directory, then you'll have to use the classpath.

---

### Post by NormR2 on 2008-06-22
the following is only partially correct:

> which is in the same directory where the java class that you are compiling is.

The import soruce statement lists a path that is to be concatenated to the end of a path in the CLASSPATH to enable the compiler to find a class definition. Since one of the paths in the CLASSPATH should be . (current directory) the above would be true.  
The class definitions are often in jar files. If the jar file is referenced in the -classpath option, then the compiler will look in the jar file for the class on the path: chapman/io/
If the class file is in a folder, then one of the paths in the classpath value must point to a folder with a chapman/io/ subfolder in it.
For example if the class file is in /root/home/me/test/chapman/io/afile.class
then the classpath must include: /root/home/me/test

---

### Post by lordhaworth on 2008-06-22
Thanks all, I understand the problem makes much more sense now. The computer cant locate the folder chapman etc so i think im going to start from scratch.

Thanks again everyone

---

