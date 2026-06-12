---
title: "Java: Where to place these javax folders"
date: 2009-02-04
forum: Programming Talk
---

### Post by balagosa on 2009-02-04
[JSR 82 (Java Bluetooth)]("http://www.jsr82.com/")

[JSR 82 Download]("http://jcp.org/en/jsr/detail?id=82")
This downloader website gives you a folder named "javax" with two subfolders in it, namely: bluetooth, and microedition. I have read just a tip of the JSR 82 documentation but there is no instruction where to place the folders.

My goal:

To be able to do this, without errors
```

include <javax.bluetooth.*>

```

I tried searching my $JAVA_HOME, but there are no javax folders located in $JAVA_HOME except for Class documentations. I have found a temporary solution though, that is through the "package" decleration. But I want to make it permanent, I want to include these files to the library for javax.

---

### Post by jespdj on 2009-02-04
You can put them anywhere you like, and you have to put them in your classpath if you want to use them. You can do that by setting the environment variable CLASSPATH to the base directory where you put those javax directories, or by using the "-cp" switch on the command line:
```

# To compile:
javac -cp /some/directory:. MySource.java

# To run:
java -cp /some/directory:. MySource

```
Your import statement should look like this:
```
include javax.bluetooth.*;
```
The angle bracket syntax is not valid Java.

---

### Post by balagosa on 2009-02-04
Yeah I forgot about the bracket syntax. I was coding C++ while typing this Topic.

hmmm....just like the package implementation, it is temporary. By Permanent I mean...

For Example, Using Netbeans. Try typing at the top of the file "import javax." and let Auto-Complete suggest some continuations for your code.

This is what I want to achieve. Will there be any way that I can achieve this?

---

### Post by cl333r on 2009-02-04
For every Java program from any IDE at any time to be able to use your libraries without having to configure path(s) to your libraries, you can drop your libraries (which are .jar files) into the "ext" folder of the JRE, in Ubuntu the path to it is:
/usr/lib/jvm/java-6-sun/jre/lib/ext

Drop them there and forget about configuring classpath(s).

PS: to drop them there you'll of course need root access

---

### Post by balagosa on 2009-02-04
> **cl333r said:**
> For every Java program from any IDE at any time to be able to use your libraries without having to configure path(s) to your libraries, you can drop your libraries (which are .jar files) into the "ext" folder of the JRE, in Ubuntu the path to it is:
/usr/lib/jvm/java-6-sun/jre/lib/ext

Drop them there and forget about configuring classpath(s).

PS: to drop them there you'll of course need root access

This will be closer to what I want. I will be looking into this. I will give you a feedback later.

-----------------------------------------------------------------------------------------------------

After testing the new jar file which I named as "bluez.jar" and stored it in the above address you specified. I still get errors, nothing pops out which is concerned with "bluez". I have a feeling I am doing something wrong here.

---

