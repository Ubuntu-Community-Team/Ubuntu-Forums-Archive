---
title: "Kernel compiled &amp; --print-installation-architecture"
date: 2010-03-17
forum: Packaging and Compiling Programs
---

### Post by gyurman on 2010-03-17
Hello,
I have own build kernel. But when I want to dpkg -i then I got an error.
```
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
```
What can I do? Have you any idea? Help me. Thanks

---

### Post by SevenMachines on 2010-03-19
its not a critical problem obviously (yet!), you might want to check your packaging and change the call to the newer '--print-architecture' version though. it'll be in one of those debian/ scripts somewhere

---

### Post by Wulfeous on 2010-03-27
This happened to me too! :( 

I'm too noobish to know where to go to change it. wish it said. 

Rather.. I wish it just accepted the old command as well as the new one to avoid this problem.

---

### Post by gyurman on 2010-04-05
Have it anybody an idea? I wan't compile new kernel for me. Please help

---

### Post by gmargo on 2010-04-05
Did you take the advice of SevenMachines?  What kernel are you talking about? And where did you get it?

---

### Post by gyurman on 2010-04-06
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Need use new method, don't old.

---

