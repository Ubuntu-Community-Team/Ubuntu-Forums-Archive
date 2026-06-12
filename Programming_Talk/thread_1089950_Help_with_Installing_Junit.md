---
title: "Help with Installing Junit"
date: 2009-03-07
forum: Programming Talk
---

### Post by vandorjw on 2009-03-07
Hey Everyone,

I am working on an assignment that I have to test using Junit.

Junit is installed on my machine I believe, because when I type
>  locate junit 

it spits out many directories that have junit in it.

However, I am supposed to be working with the version 4.5 from
>  [http://sourceforge.net/project/showfiles.php?group_id=15278&package_id=12472](http://sourceforge.net/project/showfiles.php?group_id=15278&package_id=12472) 

I found the installation instructions, however I am having a hard time following them.

> 
Below are the installation steps for installing JUnit:

   1. unzip the junit4.6.zip file
   2. add junit-4.6.jar to the CLASSPATH. For example: set classpath=%classpath%;INSTALL_DIR\junit-4.6.jar;INSTALL_DIR
   3. test the installation by running java org.junit.runner.JUnitCore org.junit.tests.AllTests.

      Notice: that the tests are not contained in the junit-4.6.jar but in the installation directory directly. Therefore make sure that the installation directory is on the class path 

Important: don't install junit-4.6.jar into the extension directory of your JDK installation. If you do so the test class on the files system will not be found. 


I downloaded and extracted the zip file to my home directory and tried

```

export JUNIT=/home/joost/Downloads/Junit/junit4.5

```

however, when I try to compile something using javac it still tells me

```

TestPointT.java:7: package org.junit does not exist
import org.junit.*;
^
TestPointT.java:8: package org.junit does not exist
import static org.junit.Assert.*;
                       ^

```

I was told that I need to edit the ".cshrc" file, but I think that this is for a different shell isn't it? I use bash, so would I need to edit .bashrc?

EDIT:

I tried adding the line 
> 
 set classpath=%classpath%;/home/joost/Downloads/Junit/junit4.5\junit-4.5.jar;/home/joost/Downloads/Junit

to my bashrc file, but that didn't help.

I still get the following error

```

javac -g TestEdgeT.java
TestEdgeT.java:7: package org.junit does not exist
import org.junit.*;
^
TestEdgeT.java:8: package org.junit does not exist
import static org.junit.Assert.*;
                       ^
2 errors
make: *** [TestEdgeT.class] Error 1

```



Thanks - cc7

---

### Post by vandorjw on 2009-03-07
Sorry for seeming impatient, but, anyone?

How do I set the classpath for Java so it sticks

typing
```

 set CLASSPATH=/home/joost/Downloads/Junit/junit4.5/junit-4.5.jar

```
seems to be fine, however when I try to compile using javac. I still get the same results.

---

### Post by HotCupOfJava on 2009-03-07
Don't forget to include the current directory in the classpath by appending ":." to the end of the CLASSPATH. 

```
set CLASSPATH=/home/joost/Downloads/Junit/junit4.5/junit-4.5.jar:.
```

The colon tells the shell you are about to list another directory to put on CLASSPATH, and the period of course indicates whatever the current directory is.

I'm not sure that is what is causing your problem though.....

---

### Post by vandorjw on 2009-03-08
EDIT: I thought It worked. Then, I restarted my computer... this is what I did.

--------------------------------------------------------------------------------------
I renamed the file folders to
junit (versus junit-4.5)

I then proceded to set the classpath to /home/joost/Downloads/Junit/junit/junit.jar:.

and also I had to do this

export CLASSPATH=/home/joost/Downloads/Junit/junit/junit.jar

Everything compiled without problems.

Cheers - CC7

---

### Post by HotCupOfJava on 2009-03-08
Keep in mind that the "export CLASSPATH" is only a temporary resetting of the classpath. Once you close and restart the shell, you will have to do it again. And ALWAYS remember to add the ":." to the end of the statement (I say this only because you don't seem to have it on your example for your export statement..).:)

---

### Post by vandorjw on 2009-03-10
SOLVED: BOTH JUNIT and JAVAC

Thanks for your help HotCupOfJava :)

for junit and javac, the correct paths and syntax for bash were

```

#ADDED TO GET JAVAC TO WORK
export PATH=$PATH:/usr/java/jdk1.6.0_12/bin

#ADDED TO GET JUNIT TO WORK
export CLASSPATH=/home/:/usr/java/junit/junit-4.5.jar

```

After spamming it to .bashrc and restarting, it works permanently

Cheers - CC7

---

