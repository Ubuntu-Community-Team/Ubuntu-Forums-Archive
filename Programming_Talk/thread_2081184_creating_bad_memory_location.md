---
title: "creating bad memory location"
date: 2012-11-06
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-06
Hey,
I would like to test a certain code piece I have, to know what happens if I increment the pointer to either
a)a bad memory location, or 
b)beyond the last memory location of my system. 

The following code piece to compare 2 strings(s1 and s2) will make my question clear.
```

int strcasecmp(s1, s2)
const char *s1, *s2;
{
        register const u_char
        *us1 = (const u_char *)s1,
        *us2 = (const u_char *)s2;

        while (tolower(*us1) == tolower(*us2++))
        {
                if (*us1++ == '\0')
                        return (0);
        }
        return (tolower(*us1) - tolower(*--us2));
}

```

_Consider_ 
Case : length of the second string is less than the first
Result : us2 gets incremented **beyond** NULL(bad practice, correct ?)
Reason : NULL checking is done only for the first string

I would like to know what happens if the second string looks as follows in memory
{'a','b','c','d','\0',EndOfMemory/BadMemoryLocation}
This code will keep the pointer at EndOfMemory/BadMemoryLocation by the end of the loop. How can I create/simulate such a location, and cause the program to crash ?

Please advise.
Thanks.

---

### Post by Bachstelze on 2012-11-06
The memory that your program seens is NOT your system's memory. It's a virtual memory created by the OS to give your program the impression that it is the only program on the system and has all the memory for itself. There is no good answer to your questions, you have to learn about how the OS manages memory.

In practice, when you try to do funny things with pointers, your program will just crash with a segfault.

---

### Post by IAMTubby on 2012-11-06
> **Bachstelze said:**
> The memory that your program sees is NOT your system's memory.It's a virtual memory created by the OS to give your program the impression that it is the only program on the system and has all the memory for itself
Thanks Bachstelze for the reply.
Can you suggest me a resource from where I can read this topic?

---

### Post by Bachstelze on 2012-11-06
> **IAMTubby said:**
> Thanks Bachstelze for the reply.
Can you suggest me a resource from where I can read this topic?

I believe I have already suggested a certain book on operating systems, I have not changed my mind.

---

### Post by IAMTubby on 2012-11-06
> **Bachstelze said:**
> I believe I have already suggested a certain book on operating systems, I have not changed my mind.
I'm sorry Bachstelze, it's Tannenbaum. I'll go and grab a copy of it.
Can I just confirm this ? Which of these books shall I invest on ?
1. [http://www.amazon.com/Modern-Operating-Systems-3rd-Edition/dp/0136006639/ref=sr_1_1?ie=UTF8&qid=1352204752&sr=8-1&keywords=operating+systems+tannenbaum](http://www.amazon.com/Modern-Operating-Systems-3rd-Edition/dp/0136006639/ref=sr_1_1?ie=UTF8&qid=1352204752&sr=8-1&keywords=operating+systems+tannenbaum)
2. [http://www.amazon.com/Operating-Systems-Design-Implementation-Edition/dp/0131429388/ref=sr_1_2?ie=UTF8&qid=1352204752&sr=8-2&keywords=operating+systems+tannenbaum](http://www.amazon.com/Operating-Systems-Design-Implementation-Edition/dp/0131429388/ref=sr_1_2?ie=UTF8&qid=1352204752&sr=8-2&keywords=operating+systems+tannenbaum)

Can you also suggest me a book to get a Unix approach of operating systems ? Can I go ahead and buy "The Design of the UNIX Operating System" by  Maurice J. Bach ?

Thanks and sorry for the trouble.

---

### Post by Bachstelze on 2012-11-06
> **IAMTubby said:**
> I'm sorry Bachstelze, it's Tannenbaum.

No, it's Silberschatz. ;) [http://www.amazon.com/dp/0470128720/](http://www.amazon.com/dp/0470128720/) If you don't want to spend too much, the 6th or 7th edition is fine as well. I don't know the book you mentioned but it pretty old, I'm not sure how relevant it is to modern operating systems. For Linux, you might want to look at the Documentation folder of the kernel source, it probably has some good references.

---

### Post by Impavidus on 2012-11-07
> **IAMTubby said:**
> _Consider_ 
Case : length of the second string is less than the first
Result : us2 gets incremented **beyond** NULL(bad practice, correct ?)
Reason : NULL checking is done only for the first string

I would like to know what happens if the second string looks as follows in memory
{'a','b','c','d','\0',EndOfMemory/BadMemoryLocation}
This code will keep the pointer at EndOfMemory/BadMemoryLocation by the end of the loop. How can I create/simulate such a location, and cause the program to crash ?

Please advise.
Thanks.
To gave a reply to the original question: this will work fine. Indeed, when the second string is shorter than the first, us2 will point to some invalid location when the loop terminates, but it is restored to pointing to '\0' before it is dereferenced.

In general, dereferencing bad pointers gives segmentation faults or bus errors, unless it pointed to some random location also in use by your program, leading to reading or modifying random data and particularly nasty bugs.

---

### Post by IAMTubby on 2012-11-07
> **Impavidus said:**
> 
In general, dereferencing bad pointers gives segmentation faults or bus errors
Thanks Impavidus for the reply.
That's again my question, can I **create** a bad pointer **on purpose** just to see that segmentation faults / bus errors would occur.

---

### Post by Bachstelze on 2012-11-08
> **IAMTubby said:**
> 
That's again my question, can I **create** a bad pointer **on purpose** just to see that segmentation faults / bus errors would occur.

Sure. A pointer is essentially an integer, so just throw some random value:

```
#include <stdio.h>

int main(void)
{
    unsigned char *p = 1234567;
    printf("Byte is: %2x\n", *p);
}
```

---

### Post by IAMTubby on 2012-11-08
> **Bachstelze said:**
> Sure. A pointer is essentially an integer, so just throw some random value:

Thanks Bachstelze, that's useful.
But I wanted something in such a way that even if you don't access the value at that location(dereference) but only traverse to that location, you still get an error.

As in something like,
p = p++; where p reaches that "bad location" gives you an error.

Is that possible or am I asking for something unreasonable?

Thanks.

---

### Post by spjackson on 2012-11-08
> **IAMTubby said:**
> 
As in something like,
p = p++; where p reaches that "bad location" gives you an error.

Is that possible or am I asking for something unreasonable?


In C it is not an error for a pointer to be given a value that does not correspond to a valid address. It is only an error to **dereference** a pointer that holds such a value. The following will run forever without error.
```

for (char * p = 0; ; p++) ;

``` 
The following is also a well-formed program.
```

int main()
{
    char * p; // unitialised, holds an arbitrary value, which may be an invalid address.
    return 0;
}

```

---

### Post by Bachstelze on 2012-11-08
> **IAMTubby said:**
> Thanks Bachstelze, that's useful.
But I wanted something in such a way that even if you don't access the value at that location(dereference) but only traverse to that location, you still get an error.

As in something like,
p = p++; where p reaches that "bad location" gives you an error.

Is that possible or am I asking for something unreasonable?

Thanks.

You seem to be confused about what a pointer is. It is really just an integer, so it is not an error to give it any value. There is no "traversal", whatever you mean by that, involved when assigning a value to a pointer; it is like writing an address on a piece of paper, you can do it without actually going there.

---

### Post by IAMTubby on 2012-11-08
> **spjackson said:**
> In C it is not an error for a pointer to be given a value that does not correspond to a valid address. It is only an error to **dereference** a pointer that holds such a value. The following will run forever without error.
```

for (char * p = 0; ; p++) ;

``` 
The following is also a well-formed program.
```

int main()
{
    char * p; // unitialised, holds an arbitrary value, which may be an invalid address.
    return 0;
}

```
Thanks a lot spjackson. 
I understand. The 2 code examples made things clear.


> **Bachstelze said:**
> it is like writing an address on a piece of paper, you can do it without actually going there.
Thanks Bachstelze, I understand. Nice example about writing down a random address on a piece of paper.

---

