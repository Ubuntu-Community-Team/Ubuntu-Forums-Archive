---
title: "beginner fork() problem"
date: 2008-06-28
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-28
i just had a look at the fork() fn. i read in a manual.it gave a code:
```
int main()
{
printf("line1");
fork();
printf("line2");
}

```

the expected o/p from their side was :
line1line2line2

my output is : line1line2line1line2

but when i am replacing the code with :
```
int main()
{
printf("line1\n");
fork();
printf("line2");
}
```

i get the expected output.why ?

---

### Post by Phristen on 2008-06-28
Adding an \n flushes the output buffer immediately, whereas in your first example the output is flushed at the end of the program in both parent and child.

If you don't wanna add \n, you can manually flush it by calling **fflush(stdout);** before forking.

---

### Post by dexter.deepak on 2008-06-28
thanks.
yet the tutorial said that "the relative value of the next instruction pointer is also copied", that is the next instruction of both the parent and child are same.
this way, the o/p in the first case should have been :
line1line2line2
but mine is 
line1line2line1line2

what about this ?

---

### Post by Phristen on 2008-06-28
> **dexter.deepak said:**
> thanks.
yet the tutorial said that "the relative value of the next instruction pointer is also copied", that is the next instruction of both the parent and child are same.
this way, the o/p in the first case should have been :
line1line2line2
but mine is 
line1line2line1line2

what about this ?
The pointer is copied, but so are all the variables, and output buffers.
At the time you fork, no output has yet been written to screen, but it is still sitting in the buffer.

Maybe I'm not good at explaining :(
Here's the code to demonstrate:[PHP]
int main()
{
printf("line1");
fflush(stdout); // <---- look here
fork();
printf("line2");
}
[/PHP]The o/p of above is line1line2line2

---

### Post by dexter.deepak on 2008-06-29
thanks. i got the point.

---

