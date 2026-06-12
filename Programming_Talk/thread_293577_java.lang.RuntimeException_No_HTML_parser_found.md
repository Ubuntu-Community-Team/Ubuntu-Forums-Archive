---
title: "java.lang.RuntimeException: No HTML parser found"
date: 2006-11-05
forum: Programming Talk
---

### Post by disable2017July14 on 2006-11-05
Hello everybody

At a certain point while running a java applet, there's the following problem:

```
1 of 3Exception in thread "main" java.lang.RuntimeException: No HTML parser found. Make sure that either nekoHTML.jar or Tidy.jar is in the in classpath
        at com.meterware.httpunit.parsing.HTMLParserFactory.getHTMLParser(HTMLParserFactory.java:92)
        at com.meterware.httpunit.HTMLPage.parse(HTMLPage.java:255)
        at com.meterware.httpunit.WebResponse.getReceivedPage(WebResponse.java:1109)
```

I have sun-java5-jre and even sun-java5-jdk installed. I know that running the applet under Mac OS X requires some "java-extensions". What's that exactly or how can I install it under Linux in order to run the programm correctly? How do I get nekoHTML.jar or Tidy.jar into the 'classpath'?

Thanks for advise, Reni

---

### Post by disable2017July14 on 2006-11-05
Allright, now I know a little bit more, but still not enough to get it working...

I put the 2 jar files and all all the extensions (which I also had to copy to the Mac OS X system to get the applet running) into a folder and added the folder to CLASSPATH like this:

```
CLASSPATH=$CLASSPATH:/home/reni/app/Extensions/
export CLASSPATH
echo $CLASSPATH
/home/reni/app/Extensions/
```

So it seems that this worked, but I still get the same error as before... Can anyone please help me? Thanks a lot!!!

---

### Post by cobray on 2006-11-05
You need to do

CLASSPATH=$CLASSPATH:/home/reni/app/Extensions/nekoHTML.jar:/home/reni/app/Extensions/Tidy.jar
export CLASSPATH

You have to use the filename of the jar file. If you extracted the class files into the directory then you can use the directory name in the CLASSPATH

:-|

---

### Post by disable2017July14 on 2006-11-05
Cool, that worked. But now I get that error ](*,) 

```
1 of 3Exception in thread "main" com.meterware.httpunit.WebForm$NoSuchParameterException: No parameter named 'SEITE' is defined in the form
        at com.meterware.httpunit.WebForm.setParameter(WebForm.java:611)
        at com.meterware.httpunit.WebForm.setParameter(WebForm.java:601)
        at app.search(app.java:133)
        at app.main(app.java:73)
```

I really don't know what to do now since there's no hint how to solve it... :confused:

---

