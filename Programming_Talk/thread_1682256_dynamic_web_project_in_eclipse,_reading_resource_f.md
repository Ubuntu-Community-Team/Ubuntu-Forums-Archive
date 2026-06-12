---
title: "dynamic web project in eclipse, reading resource file"
date: 2011-02-05
forum: Programming Talk
---

### Post by badperson on 2011-02-05
Hi,
I have a dynamic web web project, and in it I have a class that has some simple static methods, one of which is to read params from a config file. 

In the utility class, which is located under the source folder under com.somepackage, I create a new file object: 

```
File configFile = new File("config/config.xml");
```

When I run it, I get a null pointer...it says the file location doesn't exist. 

The config folder is under WebContent. 

I've tried various things; WebContent/config/config.xml, ./config/config.xml, etc...

What's the best way to grab that file? 
thanks!
bp

---

### Post by myrtle1908 on 2011-02-05
You need to call getRealPath() from the ServletContext to obtain the physical path from the relative path.

```
File f = new File(getServletContext().getRealPath(relativePath));
```

[http://download.oracle.com/javaee/1.3/api/javax/servlet/ServletContext.html#getRealPath(java.lang.String](http://download.oracle.com/javaee/1.3/api/javax/servlet/ServletContext.html#getRealPath(java.lang.String))

---

### Post by badperson on 2011-02-05
schweeeet....that did it!:guitar:

thanks!
bp

---

