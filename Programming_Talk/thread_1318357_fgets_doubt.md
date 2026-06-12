---
title: "fgets doubt"
date: 2009-11-07
forum: Programming Talk
---

### Post by masterof14 on 2009-11-07
Hi 

I'm writing a script for my programming classes and I'm having a small problem maybe someone can help me 

somewhere in my script comes:

while(fgets(line, 1024, stdin) != NULL)                    
    {
        sscanf(line, "%s", command); 
        if(strcmp(command, "exit")==0)                        
        {
            /*MY DOUBT*/;
        }
        else

/*some more script*/
} /* end of while*/

printf("Goodbye!");

When I write "exit" he should exit the while cycle. I already tried
 [I]return (-1)
return(0) and
return EOF[/I]

one more thing: I'm not allowed to use the break command. Any clue?

---

### Post by Can+~ on 2009-11-07
> **masterof14 said:**
> one more thing: I'm not allowed to use the break command. Any clue?

Assuming that your code works fine, how about adding a boolean value and just flip it?

[PHP]#include <stdbool.h>

...

bool running=true;
while(... && running)
{
    ...
    ...
    if (...)
        running = false;
}[/PHP]

---

### Post by masterof14 on 2009-11-07
well I'm only allowed to use ANSI C :S

---

### Post by Can+~ on 2009-11-07
[PHP]char running = 1;
while(... && running) 
{
    ...
    ...
    if (...)
        running = true;
}[/PHP]

Same thing, stdbool is just a typedef and two #defines (true 1 and false 0).

---

### Post by Arndt on 2009-11-07
> **masterof14 said:**
> Hi 

I'm writing a script for my programming classes and I'm having a small problem maybe someone can help me 

somewhere in my script comes:

while(fgets(line, 1024, stdin) != NULL)                    
    {
        sscanf(line, "%s", command); 
        if(strcmp(command, "exit")==0)                        
        {
            /*MY DOUBT*/;
        }
        else

/*some more script*/
} /* end of while*/

printf("Goodbye!");

When I write "exit" he should exit the while cycle. I already tried
 [I]return (-1)
return(0) and
return EOF[/I]

one more thing: I'm not allowed to use the break command. Any clue?

If 'break' is the only thing you're not allowed to use, why not use 'goto'?

---

### Post by MindSz on 2009-11-07
How about:

```
while(fgets(line, 1024, stdin) != NULL)
{
  sscanf(line, "%s", command);
  if(strcmp(command, "exit")==0)
  {
    printf("Goodbye!\n");
    return 0;
  }
  else
  {
    /*some more script*/
  } /* end of while*/
```

If you exit the program when you encounter "exit" then it should work. Instead, if you need to exit to another state of the program, then you can place the code inside a function which returns a value upon completion.

---

### Post by dwhitney67 on 2009-11-07
> **masterof14 said:**
> Hi 
...
one more thing: I'm not allowed to use the break command. Any clue?

Read this...
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

From your question concerning:
```

/*MY DOUBT*/;

```
a simple 'break' statement ought to suffice,

P.S.  Oh, you cannot use a break!  Well then consider using a flag variable that is either set to a zero (0) or a one (1).  Programmers tend to call this a 'semaphore' or a boolean 'flag'.

---

