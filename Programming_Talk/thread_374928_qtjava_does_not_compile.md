---
title: "qtjava does not compile"
date: 2007-03-03
forum: Programming Talk
---

### Post by Rizado on 2007-03-03
I've been trying to get some of the qtjava examples to run but it just wont. When I try to compile ScribbleWindow I do: ```
javac -cp /usr/share/java/qtjava.jar ScribbleWindow.java
```It seem to work and there's no error messages but when trying to run it with ```
java -cp /usr/share/java/qtjava.jar ScribbleWindow
``` All I get is:

```
Exception in thread "main" java.lang.NoClassDefFoundError: ScribbleWindow
```

I've tried many examples but none of them work. They all give me the same error message. (Except for the last word) Does anyone know how to solve this?

EDIT: Suddenly it works! I made a link from /usr/lib/jni/libqtjava to /usr/lib and I can compile it in NetBeans now. But it still doesn't work by running javac and java.

---

### Post by kaamos on 2007-03-03
try this
```

export LD_LIBRARY_PATH="/usr/lib:/usr/lib/jni/libqtjava"
java -cp .:/usr/share/java/qtjava.jar ScribbleWindow

```

The export might not even be needed.

---

### Post by Rizado on 2007-03-03
Nope, still doesn't work. Have tried different library paths but it does nothing. The strange thing is I can compile in netbeans and bluej.

---

### Post by Rizado on 2007-03-04
I wonder if there are any tutorials on using qtjava? Just a few examples with explanations.

---

