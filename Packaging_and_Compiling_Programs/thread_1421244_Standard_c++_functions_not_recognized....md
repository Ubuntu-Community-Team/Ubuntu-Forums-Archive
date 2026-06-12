---
title: "Standard c++ functions not recognized..."
date: 2010-03-04
forum: Packaging and Compiling Programs
---

### Post by kayaksmak on 2010-03-04
So, I'm doing some minor programming for my C++ class in college and I've needed to use atoi() and exit() in a program recently, except it didn't work on my personal machine.  As soon as I tried it on a school computer, it worked perfectly.  

whenever I try to compile a program with either of these in it, g++ prints a message like:
```

tree_test.cpp: In function ‘int main()’:
tree_test.cpp:51: error: ‘exit’ was not declared in this scope

```

... and that was code that was given to me and has compiled before on a different machine than what I'm on right now.  Any ideas on how I can fix this travesty?

Thanks!

---

### Post by SevenMachines on 2010-03-04
newer g++ versions are a bit more strict about having to include headers explicitly. exit and atoi need the cstdlib headers, so 

#include <cstdlib>

should do it

---

### Post by kayaksmak on 2010-03-04
Marvelous!  Wonderful!  I can code again! :p

---

