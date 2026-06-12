---
title: "Eclipse and java problem"
date: 2012-02-09
forum: Programming Talk
---

### Post by grizdog on 2012-02-09
I saw similar problems in this forum, but none quite the same.  I am running Ubuntu 10.04, have Helios Eclipse installed and java open sdk 6-20.  I have several programs in the Eclipse workspace and all of them work except this one.  I have looked at the library paths and build configuration and they look fine - java is always visible.

The bit of code that fails is this:

```

public static void main(String[] args) throws IOException {
        
    try {
    File inFile = new File("mcdata.txt");
    } catch (FileNotFoundException e) {
        System.out.println("Data file not present");
    }
        FileInputStream inStream   = new FileInputStream(inFile);
        DataInputStream dataStream = new DataInputStream(inStream);
 
        System.out.println(dataStream.readInt());
    }

```The exception handler has no effect - same result if I comment it out.  The error message I get is this:

> 
Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
    inFile cannot be resolved to a variable
the file mcdata.txt is present in the same directory as the source, but I get the same error if it is not.  I have an import java.io.* statement up at the top.

Thanks for any help

---

### Post by doobrie on 2012-02-09
You have declared inFile in a different scope to where you are trying to use it.  Try declaring inFile outside the try block.  e.g.

```
File inFile = null;
try {
    inFile = new File("mcdata.txt");
} 

etc.
```

---

### Post by nothingspecial on 2012-02-09
*Thread moved to **Programming Talk**.*

---

### Post by grizdog on 2012-02-09
Thank you for the reply

When I take out the exception handler entirely, I get the same error, but also file not found, even though I have the data file in the src and bin directories in the Eclipse workspace.

I'm going to try a second reinstall of Java.

---

### Post by doobrie on 2012-02-09
> **grizdog said:**
> Thank you for the reply

When I take out the exception handler entirely, I get the same error, but also file not found, even though I have the data file in the src and bin directories in the Eclipse workspace.

I'm going to try a second reinstall of Java.

If you are running the code from Eclipse, there is an option in the run configurations dialog to specify the current working directory when running the app.  You must have the mcdata.txt file in this directory otherwise it won't find it.  As a start, I'd recommend putting in the entire path to the .txt file to make sure it is being picked up correctly.

What does your code look like when you've taken the exceptions out?

---

### Post by muteXe on 2012-02-09
Seriously, it doesnt look like it's an install problem!

---

### Post by doobrie on 2012-02-09
> **grizdog said:**
> 
I'm going to try a second reinstall of Java.

You've got a compilation problem, so I don't think a fresh install of Java will make any difference.

---

### Post by grizdog on 2012-02-09
Argh. After I did the new install, I moved the data file to the project directory  (I feel dumb) and it worked.  I have no idea if that was the only problem

Thanks to all.

---

### Post by r-senior on 2012-02-09
This looks like a test project at this stage but you ought to think longer term about using [getResourceAsStream]("http://docs.oracle.com/javase/6/docs/api/java/lang/ClassLoader.html#getResourceAsStream%28java.lang.String%29") to load a resource.

At the moment, you are relying on the working directory of the JVM to locate that file using a relative path. If you were to open a terminal, change to the project's 'bin' directory and try running the program, you'd probably find it doesn't work. If you package it into a JAR file, it definitely won't work.

Using getResourceAsStream is the portable and reliable solution (and no more difficult really):

```
package example;

import java.io.DataInputStream;
import java.io.IOException;
import java.io.InputStream;

public class Driver {

	public static void main(String[] args) throws IOException {
		InputStream in = Driver.class.getResourceAsStream("/data/mcdata.txt");
		if (in != null) {
			DataInputStream dataStream = new DataInputStream(in);
			System.out.println((dataStream.read()));
		}
		else {
			System.err.println("Resource not found");
		}
	}
}

```

The directory structure of the project looks like this (bear in mind, the Driver class is in the example package):

```
src:
data  example

src/data:
mcdata.txt

src/example:
Driver.java

```

---

