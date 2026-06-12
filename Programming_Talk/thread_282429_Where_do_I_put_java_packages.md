---
title: "Where do I put java packages?"
date: 2006-10-22
forum: Programming Talk
---

### Post by forteller on 2006-10-22
Hi! I'm using Java 1.5 and I need to use a non-standard package or library. I'm not sure what the correct name is, but I'm talking about those that you import at the start of the source code, like this:```
import java.io.*
```The problem is that I don't know where Java takes the packages/libraries from. Where should I put the .jar file so that Java will find it when I compile the program? I hope you uderstand what I mean, and that someone can help me, I need to know this to do schoolwork!
Thanks! :)

---

### Post by orlox on 2006-10-22
I don't know of a generic way to do it, because I always did it using the eclipse IDE. I'f I remember well, I went to the project properties, then to the project's buildpath, and there there was an option to include an external jar file. To include the things on your java code you must write:

> import packagename.*

where packagename is the name of the package (if the jar has the sources, then they should have a line at the beggining that says "package packagename;")

---

