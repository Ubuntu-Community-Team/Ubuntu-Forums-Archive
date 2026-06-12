---
title: "adding the xalan jar to my classpath"
date: 2008-05-08
forum: Programming Talk
---

### Post by badperson on 2008-05-08
Hi,

I have xalan installed on my machine. If I type
xalan -v on a console, I get this:

```
Xalan version 1.10.0
Xerces version 2.7.0

```

but when I try to run a stylesheet with the following command:

 java org.apache.xalan.xslt.Process -IN SparrowCreekDevil.xml -XSL test.xsl -OUT test.txt

I get this:
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/xalan/xslt/Process

```

I gather this means I need to add it to my classpath, but I"m not sure how to do this. 
thanks, 
bp

---

### Post by badperson on 2008-05-08
figured it out, 

added this to my .bashrc file:

CLASSPATH=$CLASSPATH:/usr/share/java/xalan2.jar
bp

---

### Post by ahvargas on 2008-05-09
That is not the best way to do that, becouse now all your java apps will run with that jar in the cp.

You can try -cp option to run your program.

---

