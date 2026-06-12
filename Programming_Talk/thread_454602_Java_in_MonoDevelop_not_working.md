---
title: "Java in MonoDevelop not working"
date: 2007-05-25
forum: Programming Talk
---

### Post by georgecm3 on 2007-05-25
I'm trying to do some Java programming in MonoDevelop, and I have the Java plugin installed.
When I try to build a program, I get this error:
```

Building Project: p1.2 Configuration: Debug
Performing main compilation...
The Java addin has not been properly configured.
Please set the location of IKVM in the Java configuration section of MonoDevelop preferences.
Build complete -- 1 error, 0 warnings

```

---

### Post by lukew on 2007-05-31
> **georgecm3 said:**
> I'm trying to do some Java programming in MonoDevelop, and I have the Java plugin installed.
When I try to build a program, I get this error:
```

Building Project: p1.2 Configuration: Debug
Performing main compilation...
The Java addin has not been properly configured.
Please set the location of IKVM in the Java configuration section of MonoDevelop preferences.
Build complete -- 1 error, 0 warnings

```


Have you installed JDK and set the paths into your stem variable PATH?

Also why mono? Eclipse seems to be more popular and i think it support code completion (can someone back me up on this one?).

Netbeans also has drag and drop WYSIWYG GUI development.

---

### Post by kknd on 2007-05-31
For Java, its way better to use NetBeans / Eclipse than MonoDevelop.

MonoDevelop aren't finding the IKVM, you must configure it correctly.

---

