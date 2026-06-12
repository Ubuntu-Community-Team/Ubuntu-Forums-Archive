---
title: "function call sequence diagramming"
date: 2011-06-06
forum: Programming Talk
---

### Post by cybo on 2011-06-06
does anybody know of a tool(or even a methodology) that can diagram function call sequence? something similar to the class inheritance (relationship) diagramming for classes. say function3 calls function2 which calls functions 1 and 0. i'm maintaining large amount of code and even though i'm able to navigate it through ctags, it is still very confusing to see who calls who. it would be very nice to have some sort of a parser which could generate an image, showing which function calls which, get a big picture so to speak. 

any help is appreciated

---

### Post by dargaud on 2011-06-06
Sp basically you want your spaghetti code to _look_ like a plate of spaghetti ?!? Those diagrams are not used for the simple reason that they are not very useful, except in a vaguely artistic sort of way.

---

### Post by DangerOnTheRanger on 2011-06-06
You didn't specify the language this tool is meant to parse, so I don't think anyone can really answer your question until you specify what language you need the tool to parse. 

If you need said tool to parse Python programs, I might be able to throw something together for you.

---

### Post by muteXe on 2011-06-06
Set some breakpoints and examine the call stack?

---

### Post by cybo on 2011-06-06
i'm writing code in C

---

