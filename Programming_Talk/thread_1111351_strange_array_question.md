---
title: "strange array question"
date: 2009-03-30
forum: Programming Talk
---

### Post by cmay on 2009-03-30
i was working on some different copy rutines i saw in a tutorial and used this as a test basis for trying them out one at the time. before i went to bed i clicked compile and run and to my surprise in this example as it stands now the str2 gets printed even that 1 i get a warning its not even used 2 i am not using it in the program . how can that be. 
[php]
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
    char str[]="w";
    char str2[]="echo hello";
    char command[]={'\0'};
    int i;
    
    for(i=0;i< sizeof str;i++)
         command[i]=str[i]-'\0';
       
    if(system(command)== 0)
       printf("haha");
       
    while((str[i++]=command[i]-'\0'))
           ;
           printf("string is now %s\n",command);   
    return 0;
}
[/php]maybe i am trying to hard to see something and misses the obvius but i simply do not get it. 
thanks for the time.

---

### Post by hanniph on 2009-03-30
I tried to run it and got system("w") executed. System function returned zero so it outputed "haha" and finaly program printed "w" which is the value of command. Have no idea how it can print str2 since its not actually used.

---

### Post by monkeyking on 2009-03-30
I dont understand the problem,
could you post your compile error and a run example.

When I run your program it gives me
```

./a.out
 02:22:35 up 27 days, 51 min,  1 user,  load average: 4,00, 4,00, 4,00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
t****** pts/0    192.38.112.122   02:17    0.00s  1.34s  0.00s ./a.out
hahastring is now w

```

the compile output is

```

g++ -Wall test.c
test.c: In function &#8216;int main(int, char**)&#8217;:
test.c:11: warning: comparison between signed and unsigned integer expressions
test.c:7: warning: unused variable &#8216;str2&#8217;

```

This seems quite normal?

---

### Post by lisati on 2009-03-30
Just a thought: str[2] is not necessarily the same as str2[] 
If you're lucky, it *might* be if the compile & link process ends up with the memory allocated for str2 immediately follows the memory allocated for str, but you can't count on that happening.

---

### Post by dwhitney67 on 2009-03-30
There's only one byte of space allocated for 'command'.  The program appears buggy, thus I wouldn't place too much stock on what output it produces.

Here's my take on it... see comments below:
```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
    char str[]="w";
    char str2[]="echo hello";
    char command[]={'\0'};     /* only one-byte buffer for command */
    int i;
    
    for(i=0;i< sizeof str;i++)    /* str has a sizeof 2 bytes */
         command[i]=str[i]-'\0';  /* let's overflow the command buffer */
       
    if(system(command)== 0)   /* execute the 'w' command */
       printf("haha");        /* system() always returns 0 if it can fork a command, regardless if the command succeeds */
       
    while((str[i++]=command[i]-'\0'))  /* let's pump more crap into a small buffer; 'i' is 2 to start */
           ;
           printf("string is now %s\n",command);  /* either garbage, or maybe str2? */   
    return 0;
}

```

@ cmay -- Why do you post nonsense code like this?  Are you trying to amuse us with your silliness?  Please write some better code.

---

### Post by slavik on 2009-03-30
everything is correct ... what's the misunderstanding?

---

### Post by cmay on 2009-03-31
thanks. 
dwitheny64 explains it i think. 

i was not sure if i wanted to post the example but i decided i rather 
look very stupid once or twice and gain knowledge than pretend i know something dont.

last night i was working on a copy rutine for a bubblesort program and to my surprise it printed out the exact same thing as the command env does. 

so to figure out what was going on i started to find all sorts of strange ways to construct these errors wiht out seeing clearly what it is that happens.

i read this article before and but i dont get it yet
[http://en.wikipedia.org/wiki/Buffer_overflow](http://en.wikipedia.org/wiki/Buffer_overflow)

nevermind its explained in the post by dwhitney and it actually means a lot to me that someone can explain these things. 

thanks.

---

### Post by monkeyking on 2009-03-31
No problem I actually learned that I don't need to enclose the argument to the sizeof operator in brackets.

So you post has been quite good for me.

---

