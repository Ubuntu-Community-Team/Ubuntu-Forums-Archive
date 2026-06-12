---
title: "Check OS in Java"
date: 2006-05-14
forum: Programming Talk
---

### Post by HokeyFry on 2006-05-14
Is there a way to check the operating system you are on in Java?

I am making a mario bros. clone for a java project and am doing it on two computers, one is windows, the other is Ubuntu. I need to specify the OS so I can read the images, which are in different directories than the classes. Unless I am mistaken, Ubuntu will use a '/' for a directory and windows uses '\\', and I need it to automatically specify so I dont have to change the code every time i switch platforms.

---

### Post by neehnahw on 2006-05-14
System.getProperty("os.name") and "os.version"
For more information, see google

---

### Post by yaaarrrgg on 2006-05-14
You can check the os, but this really isn't the best way to do it.  Java already sets the / or \ in the package java.io.File.  Use the variable:

```

File.separator

```

---

### Post by HokeyFry on 2006-05-15
thanks! that really helps me out a lot!

---

