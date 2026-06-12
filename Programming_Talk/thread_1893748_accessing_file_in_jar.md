---
title: "accessing file in jar"
date: 2011-12-11
forum: Programming Talk
---

### Post by jmartrican on 2011-12-11
Hello,

I have a java program that executes using webstart.  The program is in a jar.  The jar contains files that I need to access.  The files are contained in the jar's root directory.  How can I access them?

I tried the following.

```
InputStream is;
is = ClassLoader.getSystemResourceAsStream(dir + fileName);
```

This works when I execute from netbeans.  But when I execute from webstart it fails.  I have used various values for dir including:

```
static String dir = ""; //this works when executing from netbeans
static String dir = "classpath:";
static String dir = "" + File.separator;
static String dir = "classpath:" + File.separator;
```

In other parts of the code I am able to access files within my jar but I am using javaFX code in those sections and javaFX has a specific global variable called __DIR__ that you reference from.

As I type this I am realizing that I could possibly pass the value of __DIR__ to my POJO code.  I'll try that next.  But either way this is a common task and I imagine there exists a clear cut way to do this.

thanks!
jose

---

### Post by jmartrican on 2011-12-11
Problem fixed.

I had to use ClassLoader.getResourceAsStream, instead of ClassLoader.getSystemResourceAsStream.


```
    private static InputStream getInputStream(String name) {
        String fileName = dir + name + ".maplayout";
        System.out.println("in MapLayout.getInputStream, fileName = " + fileName);
        InputStream is;
        try {
            is = Class.forName("map.MapLayout").getClassLoader().getResourceAsStream(fileName);
        } catch (ClassNotFoundException ex) {
            System.out.println("...exception");
            return null;
        }
        return is;
    }
```

---

