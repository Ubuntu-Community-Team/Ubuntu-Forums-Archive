---
title: "Issues with MonoDevelop-Java on Xubuntu..."
date: 2006-07-29
forum: Programming Talk
---

### Post by deepspring on 2006-07-29
Hi Guys,

I've been trying to get MonoDevelop-Java to work and all I keep getting when I try to build a simple "hello, world!" app is this:

```
Building Solution HelloWorld

Building Project: HelloWorld Configuration: Debug
Performing main compilation...
The Java addin has not been properly configured.
Please set the location of IKVM in the Java configuration section of MonoDevelop preferences.
Build complete -- 1 error, 0 warnings

---------------------- Done ----------------------

Build: 1 error, 0 warnings

```

When I try and compile it from the command line using javac, it compiles successfully, without drama.

Any help is greatly appreciated...

---

### Post by deepspring on 2006-07-30
Update.

I've gotten ikvm to work in MonoDevelop, now I'm getting these errors:

```

Building Solution HelloWorld

Building Project: HelloWorld Configuration: Debug
Performing main compilation...
Generating reference stubs ...
Compiling Java source code ...
/home/scott/Projects/HelloWorld/HelloWorld/application.java:6: package cli.System does not exist
import cli.System.*;
^
/home/scott/Projects/HelloWorld/HelloWorld/application.java:10: cannot find symbol
symbol  : method WriteLine(java.lang.String)
location: class java.lang.System
        System.WriteLine ("Hello, World!");
              ^
2 errors
Build complete -- 2 errors, 0 warnings

---------------------- Done ----------------------

Build: 2 errors, 0 warnings

```

---

### Post by sehe on 2007-07-19
> **deepspring said:**
> Update.

I've gotten ikvm to work in MonoDevelop, now I'm getting these errors:


How? I have the same problem

```

GOT IT: Preferences/java, ikvm location to /usr/lib/ikvm on my system

```

---

### Post by rekahsoft on 2007-07-19
I recommend using Netbeans for Java development..it is BY FAR the best :P

---

