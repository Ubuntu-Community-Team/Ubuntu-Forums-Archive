---
title: "No source code is available for type java.lang.NoSuchFieldError"
date: 2011-06-20
forum: Programming Talk
---

### Post by nklatt on 2011-06-20
I'm trying to work with Java and GWT and I'm receiving the following compiler error:

[java] [ERROR] Line 51: No source code is available for type java.lang.NoSuchFieldError; did you forget to inherit a required module?

It's complaining about a core part of the language here, right? Why is it looking for source code for it at all? Is it not finding one of the core jar files? Do I need to point it at something in the ant build.xml file?

For testing purposes, I followed all the [GWT instructions]("http://code.google.com/webtoolkit/gettingstarted.html"), used webAppCreator to generate a "Hello, world." app, and that builds and runs just fine. I added a simple try...catch(NoSuchFieldError err) and it gave me the above error.

I'm new to this Java/GWT stuff so I suspect I'm missing something obvious - I'd love it if you could point out exactly what! :)

Thanks.

---

### Post by Reiger on 2011-06-20
GWT is a Java -> JavaScript translation thing. Which is to say it takes your Java program and spits out a functionally equivalent JavaScript program (modulo some real world issues, probably).

Which is where the help message comes in. I have no particular experience with GWT, but by the looks of it you are not importing something which you need. Literally. Have you tried adding an import declaration like this in the appropriate place(s):
```

import java.lang.NoSuchFieldError;

```

---

### Post by nklatt on 2011-06-20
Yes, I added that as well - no joy.

Did I forget to *inherit* a required module? Maybe that means more than importing or pointing at a jar file?

Thanks for helping.

---

### Post by nklatt on 2011-06-21
Looks like the problem is the client side of a GWT application cannot use certain aspects of Java, which makes perfect sense as that's going to be converted to JavaScript.

[http://code.google.com/webtoolkit/doc/latest/RefJreEmulation.html](http://code.google.com/webtoolkit/doc/latest/RefJreEmulation.html)

(Per cueman in this thread: [https://groups.google.com/forum/#!topic/google-web-toolkit/li5DwBcaH_4](https://groups.google.com/forum/#!topic/google-web-toolkit/li5DwBcaH_4))

If it hadn't been that, it could well have been this:
[http://blog.elitecoderz.net/gwt-and-xml-first-steps-with-comgooglegwtxmlerste-schritte-mit-gwt-und-xml-unter-comgooglegwtxml/2009/05/](http://blog.elitecoderz.net/gwt-and-xml-first-steps-with-comgooglegwtxmlerste-schritte-mit-gwt-und-xml-unter-comgooglegwtxml/2009/05/)

---

