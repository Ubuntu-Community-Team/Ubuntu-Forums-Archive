---
title: "Eclipse Doesn't Stop at Breakpoints"
date: 2010-10-23
forum: Programming Talk
---

### Post by nova47 on 2010-10-23
There was a post a long time ago about this but it was specific to Java. I've had this problem with both Ruby and Java; I'll be debugging just fine and all the sudden Eclipse just decides one run to not stop at any breakpoints. Does anyone know of a cause or solution for this? Needless to say it is a pretty significant ***pain :-(

Edit: One thing I have noticed is when I click the button that says "Show Supported Breakpoints" all my breakpoints disappear. Dunno what is happening with that. I'm not sure how Eclipse suddenly came to the conclusion that none of my breakpoints were any longer supported.

---

### Post by r-senior on 2010-10-24
I don't know if this is your specific problem, but sometimes Eclipse (and other IDEs) can get confused about what needs to be compiled and what doesn't. 

If I see odd behaviour, like not stopping at breakpoints, or the debugger stepping over lines of code that aren't really code, I go for a project clean (or a Maven clean and build) to ensure the source code I am looking at corresponds to the class files.

---

### Post by nova47 on 2010-10-24
Ya that was my first instinct to. It didn't work though. I got frustrated enough I just deleted Eclipse altogether and re-installed. Not exactly what I would call ideal but it worked.

---

