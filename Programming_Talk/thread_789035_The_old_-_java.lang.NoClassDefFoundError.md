---
title: "The old - java.lang.NoClassDefFoundError"
date: 2008-05-10
forum: Programming Talk
---

### Post by figo2476 on 2008-05-10
In kubuntu and run:

javac -classpath /home/me/projects/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar ./PDFSearch.java
(no error)

java PDFSearch
(complain java.lang.NoClassDefFoundError: pdftron/Common/PDFNetException .)

java -classpath /home/kenpeter/projects/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar PDFSearch
(complain NoClassDefFoundError: PDFSearch - why? I can see the PDFSearch.java and PDFSearch.class are there....) 

java -classpath .;/home/kenpeter/projects/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar PDFSearch
(The options explanation pops up and the .jar file won't run)

---

### Post by figo2476 on 2008-05-10
Thx in advance

---

### Post by NormR2 on 2008-05-10
Could you post the complete output from the java command. It looks like a classpath/package problem, but hard to tell from your edited posting.

Where is the class: pdftron/Common/PDFNetException

What do you mean by: The options explanation pops up and the .jar file won't run)

You run a jar file by:  java -jar <jarfilename>
the jar file must contain a manifest file that gives the name of the program that is to called initially.

Norm

---

### Post by figo2476 on 2008-05-10
run:
java -classpath /home/me/projects/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar PDFSearch

output:
Exception in thread "main" java.lang.NoClassDefFoundError: PDFSearch
Caused by: java.lang.ClassNotFoundException: PDFSearch
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

It doesn't work if I put ".;" in font of the "/home/me/...", even PDFSearch.java and PDFSearch.class are sitting side by side.

---

### Post by figo2476 on 2008-05-10
[http://gary.liang.cs.research.googlepages.com/pdfsearch.tgz](http://gary.liang.cs.research.googlepages.com/pdfsearch.tgz)

I provide a download above.

---

### Post by figo2476 on 2008-05-11
I have fixed the issue to replace ";" with ":"

Another error I got:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no PDFNetC in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at pdftron.PDF.PDFNet.<clinit>(PDFNet.java:17)
        at PDFSearch.main(PDFSearch.java:146)

I assume I need to provide libPDFNetC.so
So I did this inside the main 

System.loadLibrary("/home/me/projects/pdfsearch/lib/PDFNetC/Lib/libPDFNetC.so");


Error:
java.lang.UnsatisfiedLinkError: Directory separator should not appear in library name: /home/kenpeter/projects/pdfsearch/lib/PDFNetC/Lib/libPDFNetC.so
        at java.lang.Runtime.loadLibrary0(Runtime.java:820)
        at java.lang.System.loadLibrary(System.java:1030)
        at PDFSearch.main(PDFSearch.java:131)

---

### Post by NormR2 on 2008-05-11
Sorry, I'm not sure what's happening.
It would help if when you post an error message that came from a command you entered, if you would post the full commandline that caused the error.


>  at PDFSearch.main(PDFSearch.java:131)
What code is at line 131?

---

### Post by figo2476 on 2008-05-11
How to compile:
javac -classpath .:/Users/garyl/Sites/test/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar PDFSearch.java

How to run:
java -classpath .:/Users/garyl/Sites/test/pdfsearch/lib/PDFNetC/Lib/PDFNet.jar PDFSearch


Line 131 is System.loadLibrary("/home/me/projects/pdfsearch/lib/PDFNetC/Lib/libPDFNetC.so");
That means it cannot load the library. Right now I comment it out.

Then Compile and run, I get:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no PDFNetC in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1753)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at pdftron.PDF.PDFNet.<clinit>(PDFNet.java:17)
	at PDFSearch.main(PDFSearch.java:145)

Line 145 is 
PDFNet.initialize();
It means it cannot find the 3rd party library.

---

### Post by NormR2 on 2008-05-12
My doc for the System.loadLibrary() method says its parm is a "libname". Your code shows a path.
Try changing the parm to be just the libname ie libPDFNetC
leave off the path and extension. 
Make sure the library file is in a folder on the PATH environment variable.

---

