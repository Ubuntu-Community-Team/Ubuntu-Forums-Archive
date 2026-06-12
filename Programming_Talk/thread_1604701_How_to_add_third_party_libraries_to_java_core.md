---
title: "How to add third party libraries to java core"
date: 2010-10-24
forum: Programming Talk
---

### Post by shankhs on 2010-10-24
Hi,
I am a C dev and learning java mostly by googling and trying the programs in vim.
I found this cool library dom4j but not able to use it, I am getting:
```
dom4j_hello.java:3: package org.dom4j does not exist
import org.dom4j.*;
^
```
So how to get dom4j and other third party libs working with java?
My dev platform is vim.
I tried to google but was not much successful, it seems to be pretty trivial but I am not able to get it :(

Thanks

---

### Post by r-senior on 2010-10-24
The important thing to realise about import is that it's only a convenience in terms of naming. It lets you type class names without package names:

```

package myexample;

import com.widgetmaker.Widget;

public static void main (String ... args) {
    Widget w = new Widget();
}

```

rather than

```

package myexample;

public static void main (String ... args) {
    com.widgetmaker.Widget w = new com.widgetmaker.Widget();
}

```

The classes that are part of the library typically come in a jar (or sometimes zip) file. You need to have this on your classpath for compilation and execution. By default, the classpath is the current directory, so putting your jar file in the same folder as your .java file should work.

If you want to put jars elsewhere, e.g. a common location for all your libraries, you need to know how to manipulate the classpath. If you are using an IDE, there are IDE-specific ways of doing that. If you are using the command line, you can add the your jar file to the CLASSPATH environment variable, or preferably use the -cp (or -classpath, it's the same thing) switch on the compiler and runtime:

$ javac -cp ~/lib/dom4j.jar MyProgram.java
$ java -cp $/lib/dom4j.jar myexample.MyProgram

There are other variations - dig around in the [documentation](http://download.oracle.com/javase/tutorial/essential/environment/paths.html).

Understanding the classpath is critical to Java programming.

As your programs become more complex, needing a range of libraries, you will probably go down the IDE route or use Ant or Maven from the command line to help you manage dependencies and the classpath.

---

### Post by shankhs on 2010-10-24
Thanks a lot!

---

