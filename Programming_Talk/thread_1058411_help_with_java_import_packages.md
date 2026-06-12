---
title: "help with java import packages"
date: 2009-02-02
forum: Programming Talk
---

### Post by DFord425 on 2009-02-02
I recently downloaded the source code for a project and when i open it in eclipse, i get two compile errors. There are two import statements that cannot be resolved, and they do not seem to be specific to the project. The two import statements are:
```

import com.sun.org.apache.xerces.internal.parsers.DOMParser;
import com.sun.org.apache.xerces.internal.xni.parser.XMLParseException;

```
And only the come.sun.org has the red line underneath it in eclipse. Does anyone have any ideas where i can find those packages? I am running java 6 if that matters.

---

### Post by snova on 2009-02-02
I would guess it's supposed to look like this:

```

import org.apache.xerces.internal.parsers.DOMParser;
import org.apache.xerces.internal.xni.parser.XMLParseException;

```

Looks right according to the Xerces JAR I have...

---

### Post by DFord425 on 2009-02-02
Does that come with Java 6 or do i need to get the JAR seperatly?

---

### Post by myrtle1908 on 2009-02-02
Get it here ... [http://archive.apache.org/dist/xml/xerces-j/Xerces-J-bin.1.4.4.tar.gz](http://archive.apache.org/dist/xml/xerces-j/Xerces-J-bin.1.4.4.tar.gz)

---

### Post by snova on 2009-02-02
I thought it was in libxerces2-java (/usr/share/java/xercesImpl.jar), but upon closer inspection, I can't find this class at all...

Googling a bit finds several references to com.sun.org.apache.xerces... but they don't really make sense to me (I'm not much of a Java programmer).

Edit: myrtle1908 was faster than me. :P Maybe that'll help, I don't know.

---

### Post by DFord425 on 2009-02-02
Thanks, is there a certain directory i have to untar it to? OR can i just do it to any directory and add it to the $PATH.

---

### Post by myrtle1908 on 2009-02-02
Actually it may be this one [http://xerces.apache.org/xerces2-j/api.html](http://xerces.apache.org/xerces2-j/api.html)

---

### Post by jespdj on 2009-02-03
> **DFord425 said:**
> The two import statements are:
```

import com.sun.org.apache.xerces.internal.parsers.DOMParser;
import com.sun.org.apache.xerces.internal.xni.parser.XMLParseException;

```
Bad! :( You should tell the developers of that project that they [should not use 'sun' packages](http://java.sun.com/products/jdk/faq/faq-sun-packages.html). Those packages are internal to the JDK, and are not meant to be used by programs directly.

---

