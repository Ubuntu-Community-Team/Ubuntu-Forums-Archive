---
title: "running simple C programs"
date: 2008-01-15
forum: Programming Talk
---

### Post by JPotter on 2008-01-15
I appologize for the extreme simplicity of this question, but I find any similar posts. I switched over to Ubuntu Linux over the Winter, and I am commited to use it as much as I can. I am taking an advanced C programming course this quarter, and I thought gcc would be great! I only have one, rather pressing, problem. I can't figure out how to get the output from my programs.

after compilation using 

[PHP]gcc -Wall -o hello_world hello_world.c[/PHP]

[PHP]#include <stdio.h>

int main()
{
     printf("%s","Hello World!");
     return 0;
}[/PHP]

I tried to run the program by typing in the output file's name, but I get:

[PHP]bash: hello_world: command not found[/PHP]

so . . . if you don't want to read the top, the question is: How do I run this program, and see the output?

---

### Post by CptPicard on 2008-01-15
The current directory is not in the "path" variable for security reasons. So you need to explicitly give the whole path to the executable, by using "." for "current directory".

```

./your_binary

```

---

### Post by JPotter on 2008-01-15
Thank you!

worked like a charm!

---

