---
title: "Automatic documentation for C++"
date: 2008-03-04
forum: Programming Talk
---

### Post by kikazaru on 2008-03-04
I want to automatically document some C++ projects in as useful a way as possible... can anyone suggest some useful tools?

Key points:

The projects were not well commented
I want to get an analysis of the class hierachy and as much structural informaton like that as possible

Thoughts so far:

Doxygen just gives me a convenient browser for the header files but doesn't add any structural analyses (is that correct?)
doc++ requires the code to be marked with special comments (is that correct?)

Thanks for any help!

---

### Post by Zugzwang on 2008-03-04
> **kikazaru said:**
> Doxygen just gives me a convenient browser for the header files but doesn't add any structural analyses (is that correct?)

Not entirely. There are such functions as caller and callee graph generation, but they are a little bit limited, especially when polymorphism is being used. But you might give it a try.

---

