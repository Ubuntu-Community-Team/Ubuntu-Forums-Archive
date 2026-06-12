---
title: "Little challenge in C"
date: 2008-04-14
forum: Programming Talk
---

### Post by KedDeK on 2008-04-14
Consider the following C function

```
void youwin_1(int x, char *s)
{
    volatile char a;
    char buf[20];
    a=x;
    strcpy(buf,s);
    a-=x;
    if (a==4)
        printf("You win!\n");
} 
```

You have to find a way to call youwin_1 function so that it prints "You win!".

Lets see if anyone can get it.

---

### Post by Wybiral on 2008-04-14
It's in white to avoid spoiling it: [COLOR="White"]youwin_1(0, "xxxxxxxxxxxxxxxxxxxx\x04");[/COLOR]

---

### Post by slash2314 on 2008-04-14
I also made it in white so not to spoil it: [COLOR="White"]youwin_1(28,"1111111111111111111  ");[/COLOR]

---

### Post by Tuna-Fish on 2008-04-14
> **Wybiral said:**
> It's in white to avoid spoiling it: [COLOR="White"]youwin_1(0, "xxxxxxxxxxxxxxxxxxxx\x04");[/COLOR]

Doesn't work, at least on my machine. Now, if you made it:
```

void youwin_1(int x, char *s)
{
    char buf[20];
    volatile char a; // a-ha!
     a=x;
    strcpy(buf,s);
    a-=x;
    if (a==4)
        printf("You win!\n");
}

```
Instead, I could make it work.

---

### Post by WW on 2008-04-14
This is probably not what you had in mind...

---

### Post by Wybiral on 2008-04-14
> **WW said:**
> This is probably not what you had in mind...

lol. Nice!

---

### Post by dwhitney67 on 2008-04-15
Getting the code to print out "You Win!" is one thing, however the security risk of writing bad code is probably more important, and perhaps that should be discussed.

Never copy a buffer of unknown size into a fix-length array using strcpy().  Use strncpy() instead.  In fact, the usage of strcpy() is frowned upon in most development projects.

---

### Post by KedDeK on 2008-04-15
First two solutions don't work. I also thought about the issue Tuna-Fish mentions, but as that was cheating I didn't even try it... :P

So yes WW, that was what I expected. Maybe there is other way, though?

**EDIT:** first solution works if compiling with  -fno-stack-protector flag. How can that be? So it seems that the variable a is allocated after the buffer...

---

### Post by Wybiral on 2008-04-15
My solution should work on intel machines. Yes, you need to disable the stack protection (same with slash2314's).

You know that most stacks move downward in memory, right? :)

If that's not what you were going for, what is?

---

### Post by Cappy on 2008-04-15
You can also mess with the function's return address on the stack. To do this you need the buf[20]'s starting position. 

From there you can write a C program that is just ```
printf("You win!\n");
```
then you convert the compiled program into byte format.

You fill up the rest of the string with 0's (or code to halt the program if you want) until you reach the return address and then you overwrite the return address with the starting address of buf[20]. Now when the program returns from the function it will print the new string "You win!" (rather than the one in the original program's code).

A much easier method is to overwrite the stack and point the return address to the ```
printf("You win!\n");
``` in the code.

By the way, here is what the stack looks like:
[ char buf[20] (20 bytes)....................char a(1 byte) **[RETURN ADDRESS]** int x (4 bytes) .... char *s

---

### Post by Wybiral on 2008-04-17
> **Cappy said:**
>  ... 

Yes, there are a ton of interesting things you can do with overflow... Which is exactly why it's so dangerous. Unfortunately, it's a very common bug in C code that often goes unnoticed (until someone *tries* to overflow it).

---

