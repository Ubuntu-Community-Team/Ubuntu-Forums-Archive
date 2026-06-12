---
title: "Code::Blocks : can't open a new project"
date: 2009-12-27
forum: Programming Talk
---

### Post by sharaq on 2009-12-27
I'm using codeblocks in karmic 64-bit...
and i cant't open a new project. It gives an error message saying that it cant create the relevant directories.

> Couldn't create the project directory:
c_progrm/Hello/

soo.... i used the terminal and opened codeblocks with root permission. then it worked. 

Now when ever i want to build a new project i have to run it using a terminal... 
 ```
**$ sudo codeblocks %F**
```
it's quite OK... but is there a workaround for this.

---

### Post by Queue29 on 2009-12-27
How did you install code::blocks? 
Where are you saving your project files?

---

### Post by sharaq on 2009-12-27
using synaptic.
phew....!!!
your question enlightened me. the default directory is somewhere in root so i just changed it. thanks a lot for asking me that question.

 problem solved.

---

