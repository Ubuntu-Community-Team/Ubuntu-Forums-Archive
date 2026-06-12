---
title: "NoClassDefFoundError pops out of nowhere"
date: 2009-12-12
forum: Programming Talk
---

### Post by Flimm on 2009-12-12
I'm trying to learn [iText](http://itextpdf.com), so I created a small file named PDFTest.java:
[php]import com.itextpdf.text.pdf.*;

public class PDFTest
{
    
  public static void main(String args[]) throws java.io.IOException
  {
    PdfReader reader = new PdfReader("/home/user/Documents/test.pdf");
    System.out.println("number of pages: " + reader.getNumberOfPages());
  }
}[/php]
I compile the file using: ```
javac -cp iText.jar PDFTest.java
```
It compiles successively, but I get this error when I try to run the result:
```
$ java PDFTest 
Exception in thread "main" java.lang.NoClassDefFoundError: com/itextpdf/text/pdf/PdfReader
	at PDFTest.main(PDFTest.java:8)
Caused by: java.lang.ClassNotFoundException: com.itextpdf.text.pdf.PdfReader
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 1 more
```
I'm using java-6-sun (Ubuntu 9.10) and the latest version of iText library (5.0.0) downloaded from the site. Any idea on what's gone wrong?

---

### Post by Zugzwang on 2009-12-12
When running, you need to add the library to the class path as well:
```

java -cp iText.jar PDFTest

```

---

### Post by Flimm on 2009-12-12
> **Zugzwang said:**
> When running, you need to add the library to the class path as well:
```

java -cp iText.jar PDFTest

```
Thanks, I didn't think of that.
Unfortunately, that's not quite the solution, as I get this error:
```
$ java -cp iText.jar PDFTest
Exception in thread "main" java.lang.NoClassDefFoundError: PDFTest
Caused by: java.lang.ClassNotFoundException: PDFTest
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: PDFTest.  Program will exit.
```

Turns out, I need to include the current directory. This works perfectly:```
$ javac -cp .:iText.jar PDFTest.java
$ java -cp .:iText.jar PDFTest
number of pages: 2
$ 
```

---

