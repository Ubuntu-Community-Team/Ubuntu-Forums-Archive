---
title: "SIGSEGV while opening a file for reading (also has a big array)"
date: 2009-11-04
forum: Programming Talk
---

### Post by Dragonfi on 2009-11-04
Hi,

I spent the last few hours debugging my program, but still not sure about what's the problem. I managed to condense it into a 10 line program:
[PHP]
#include<stdio.h>

int main()
{    
    FILE* fp;
    fp = fopen("wtf.c", "r");
    fclose(fp);
    double m[2097152];
    return 0;
}
[/PHP]
I noticed that if I comment out either fopen (and fclose) or the declaration of m, the program runs fine.

Is it a limitation on the maximum amount of memory a program can use, or something different I missed?

If it is a memory limitation, how can I get past it?

I also ran it trough gdb, code follows:
```

Program received signal SIGSEGV, Segmentation fault.
0x000000000040057f in main () at wtf.c:6
6	    fp = fopen("wtf.c", "r");

```

Thanks in advance.

---

### Post by Arndt on 2009-11-04
> **Dragonfi said:**
> Hi,

I spent the last few hours debugging my program, but still not sure about what's the problem. I managed to condense it into a 10 line program:
[PHP]
#include<stdio.h>

int main()
{    
    FILE* fp;
    fp = fopen("wtf.c", "r");
    fclose(fp);
    double m[2097152];
    return 0;
}
[/PHP]
I noticed that if I comment out either fopen (and fclose) or the declaration of m, the program runs fine.

Is it a limitation on the maximum amount of memory a program can use, or something different I missed?

If it is a memory limitation, how can I get past it?

I also ran it trough gdb, code follows:
```

Program received signal SIGSEGV, Segmentation fault.
0x000000000040057f in main () at wtf.c:6
6	    fp = fopen("wtf.c", "r");

```

Thanks in advance.

You can't count on so much memory being available on the stack. You can declare m static, or allocate it with malloc.

---

### Post by ravindra.rajaram on 2009-11-04
The reply might sound dumb ..but Try this:
#include<stdio.h>

```
int main()
{    
    FILE* fp=NULL;
    fp = fopen("wtf.c", "r");
    if(fp == NULL)
        return 1;
    fclose(fp);
    double m[2097152];
    return 0;
}  
```

---

### Post by Dragonfi on 2009-11-04
Thank you, Arndt, for pointing out the possible problem, I hope I understand right. You mean the problem is that, when I call fopen(), the entire m array is pushed on the stack, and obviously the array is much bigger than the stack.

From this I understand how static or making it global would solve the problem, but how is malloc different?
(EDIT: Does malloc() works fine here, because it allocates the memory "globally"?) 

If there is further reading about theese topics, feel free to point me towards them.

ravindra.rajaram: thanks for pointing out, how to properly check if the file opened successfully.

---

### Post by Arndt on 2009-11-04
> **Dragonfi said:**
> Thank you, Arndt, for pointing out the possible problem, I hope I understand right. You mean the problem is that, when I call fopen(), the entire m array is pushed on the stack, and obviously the array is much bigger than the stack.

From this I understand how static or making it global would solve the problem, but how is malloc different? 

If there is further reading about theese topics, feel free to point me towards them.

Also: thank you for pointing out, how to properly check if the file opened successfully.

I don't know exactly what happens in your program. The behaviour for stack overflow is simply undefined. Probably the stack pointer is shifted to allocate m, which in itself will not fail, but then the variable fp will be accessed far outside the actual stack given to the program by the kernel. Or the variables local to the fopen function.

malloc doesn't allocate on the stack; it allocates on the heap, which is the same general arena as for global variables.

To check whether fopen succeeded, check whether a NULL pointer was returned. Read more about this in the manual page for fopen.

---

### Post by Dragonfi on 2009-11-04
Thank you for the reply, I finished this part of my program and it runs well now. I think I will need to read up on the stack and the heap to clear the things up for me, but you gave all the critical information I needed.

---

