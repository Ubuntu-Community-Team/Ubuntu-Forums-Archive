---
title: "Netbeans Panel Property Window Error?"
date: 2011-08-09
forum: Programming Talk
---

### Post by tdrusk on 2011-08-09
I made a video of what is happening. Basically, the window keeps growing. is there any way to fix this? I know I can access the same information from the side panel, but it is odd that this is a problem.

[http://blip.tv/tdrusk/netbeans-error-5454340](http://blip.tv/tdrusk/netbeans-error-5454340)

---

### Post by sgogoi on 2011-08-10
Tried to run the following code in Netbeans... as CppApplication_2
Build Successful 168ms, Run failed 386 ms...
Don't understand why.... works fine in MS Windows Dev C++

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** argv) {
    
    char *s = "hello, world";
    char *t, *temp=t;
    
    while(*t++=*s++);
    while(*temp)
        printf("%c", *temp++);

    return (EXIT_SUCCESS);
}

---

### Post by Zugzwang on 2011-08-10
@OP: Looks like a bug. Have you checked the bug tracker of Netbeans if there is already some similarly sounding entry in it? If no, you could add it with some instruction how to let it appear.

@sgogoi: Please open up a new thread next time. You code has some flaws, and you are lucky that it happened to work on *your computer* in Windows. However, the program is likely to fail on other computers. I suggest the following: Try to add "-Wall" as a compiler flag to the compilation options. Search the web on how to do this with Netbeans. This will give you extra warnings that make your problem apparent even when compiling. Then, if that doesn't help you, try running the debugger to check where things go wrong. Alternatively, you can use the tool valgrind to find the bug. Search the forum for a usage example.

---

