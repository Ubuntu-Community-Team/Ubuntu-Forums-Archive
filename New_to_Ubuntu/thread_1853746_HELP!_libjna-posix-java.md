---
title: "HELP! libjna-posix-java"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Spadoof on 2011-10-02
Dear readers,

I am in a real pinch and need some assistance. My professor assigned me a Java program that requires the use of the POSIX API function fork();. After reading around, it seems that Java does not support the POSIX library (correct me if i'm wrong). I did find the libjna-posix-java package for Ubuntu, but for some reason I can't get it to work properly. 

Here is what I did:
-Went to Synaptic and installed libjna-posix-java.

Here is my code:

//----------------------------------------------------------
import org.jruby.ext.posix;

class ForkAverage extends java.lang.Object
{
	// Start of Program.
	public static void main (String args[]) throws java.io.IOException
	{

	}

}
//----------------------------------------------------------

Here is the compiler error:

ForkAverage.java:8: package org.jruby.ext does not exist
import org.jruby.ext.posix;
                    ^
1 error

What am I doing wrong???? Please if anyone can help me, I would sincerely appreciate it!

Thanks,
-Spadoof

---

### Post by lykeion on 2011-10-03
1. Change import line to:
import org.jruby.ext.posix.*;

2. Add library to classpath when compiling:
javac -cp .:/usr/share/java/jna-posix.jar ForkAverage.java

Plus you may want to install the doc package too:
sudo apt-get install libjna-posix-java-doc

Then open /usr/share/doc/libjna-posix-java-doc/javadoc/index.html in your browser to read how you would use JNA-POSIX library

---

