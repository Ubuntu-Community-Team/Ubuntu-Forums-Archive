---
title: "NOOB - GCC run after compiling"
date: 2007-05-23
forum: Programming Talk
---

### Post by mysttt on 2007-05-23
after installing gcc, issues occur:

gcc -o morning morning.c                ---> no pro about compile&#65292; morning file exists then

but when I run
morning                                             --->it says&#65306; bash: morning: command not found
                                                               which was supposed to be a "Good Morning" printed on the screen


this "morning.c" rather simple

#include <stdio.h>

int main(int argc, char** argv) {

printf("Good Morning\n");

return 0;

} 


So, could u guys help me, what's the problem here? I am totally new in Linux.. Thanks!

---

### Post by WW on 2007-05-23
Put **./** in front of the command:
```

$ ./morning

```

By default, the bash search path (in the evironment variable PATH) does not include the current directory.  Putting ./ in front of the command tells the shell to look for the command in the current directory. (A dot means the current directory.)

---

### Post by mysttt on 2007-05-24
Thanks!

---

