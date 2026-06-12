---
title: "Problems setting up IDE"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by Charles2531 on 2013-06-15
I've been using Ubuntu (12.04) for almost 2 weeks now. I set it up with wubi so that I can run windows if necessary, but I love it so much that I've hardly ever done so. There are only two problems that I've encountered so far that I haven't been able to find solutions to online. Both of these problems are with the Code::Blocks IDE. I've been programming with C++ for several years now and I decided to install an IDE that I'm very familiar with, but when I tried to get some things working, I ran into some problems.

First, I tried to set up GLUT. Regardless of how many tutorials I find on the internet on how to set it up, it does not work. If I create a GLUT project, it asks me to locate GLUT, but whatever file I tell it to go to, it always gives me the same answer; "The path you entered seems valid, but the wizard can't locate the include directory. This wizard cannot continue." If I try it without setting up a GLUT project and instead just linking the files, when I try to build the project, the debugger gives me a long list of errors stating that every statement with a GLUT function are all undefined references. Regardless of which one of these I try, and regardless of what tutorial/help page that I've checked for solutions to this problem so far, I haven't been able to find any solutions that work for me.

The second problem that I've found occurs when I try to compile something that does not include anything that isn't included with the compiler already. The programs compile, but when I run them, I get the following message:

sh: 1: /media/Misc/code/c++/Math/bin/Debug/Math: Permission denied

Process returned 126 (0x7E)   execution time : 0.001 s
Press ENTER to continue.


If anyone can give me ways to solve either problem, it would be appreciated.

---

### Post by Isamu715 on 2013-06-15
Looks like */media/Misc/code/c++/Math/bin/Debug/Math* is not set as executable. Run this in a terminal and see if the problem persists:
```
chmod +x /media/Misc/code/c++/Math/bin/Debug/Math
```

---

### Post by steeldriver on 2013-06-15
... just a thought, but is /media/Misc a mounted NTFS volume? if so, it likely won't understand Unix permissions - otherwise, the compiler *should* produce an executable that's actually executable without the need to manually chmod it

---

### Post by monkeybrain2012 on 2013-06-15
> **Charles2531 said:**
> I've been using Ubuntu (12.04) for almost 2 weeks now. I set it up with wubi so that I can run windows if necessary, but I love it so much that I've hardly ever done so. There are only two problems that I've encountered so far that I haven't been able to find solutions to online. Both of these problems are with the Code::Blocks IDE. I've been programming with C++ for several years now and I decided to install an IDE that I'm very familiar with, but when I tried to get some things working, I ran into some problems.

.

WUBI is meant to be a demo. If you are spending most of your time in Ubuntu and keeping Windows just in case why don't you do it the other way around? Wipe WIndows and give Ubuntu full reign and then install Windows in VirtualBox so you can run it if necessary. That would make a lot more sense.

---

### Post by Charles2531 on 2013-06-16
I tried this. It doesn't appear to have done anything.

---

### Post by Charles2531 on 2013-06-16
> **Isamu715 said:**
> Looks like */media/Misc/code/c++/Math/bin/Debug/Math* is not set as executable. Run this in a terminal and see if the problem persists:
```
chmod +x /media/Misc/code/c++/Math/bin/Debug/Math
```

I tried this. It doesn't appear to have done anything.

---

