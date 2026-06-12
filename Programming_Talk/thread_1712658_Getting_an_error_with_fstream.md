---
title: "Getting an error with fstream"
date: 2011-03-23
forum: Programming Talk
---

### Post by Sandstone on 2011-03-23
Hey i'm new to programming in C and C++. I am currently just working on a random number generator that outputs the numbers to a file. 

I am getting a strange error that I can't figure out. 

```
rand.c:4: fatal error: fstream: No such file or directory
compilation terminated.
```

Here is what I think is the relevant info.

```

#include <stdio>
#include <time>
#include <limits>
#include <fstream>

using namepsace std;

```

---

### Post by Some Penguin on 2011-03-23
You've not bothered to show the command you use to compile the program.

You're not using 'gcc' instead of 'g++', are you?  I'd also be a bit leery of naming a C++ program anything.c, instead of .cpp, as some programs might attempt to infer from the extension and you're clearly doing C++-specific things.

---

### Post by Arndt on 2011-03-23
> **Sandstone said:**
> Hey i'm new to programming in C and C++. I am currently just working on a random number generator that outputs the numbers to a file. 

I am getting a strange error that I can't figure out. 

```
rand.c:4: fatal error: fstream: No such file or directory
compilation terminated.
```

Here is what I think is the relevant info.

```

#include <stdio>
#include <time>
#include <limits>
#include <fstream>

using namepsace std;

```

Is this really a verbatim copy, with the misspelling "namepsace"?

---

### Post by dwhitney67 on 2011-03-23
Also, should be *cstdio* and *ctime*, not *stdio* and *time*.

Next time post a complete program, even if you think that it is trivial.
```

#include <cstdio>
#include <ctime>
#include <limits>
#include <fstream>
int main() {}

```
See very trivial... even a caveman can do it!

---

