---
title: "My first programs -- tell me what you think"
date: 2009-07-19
forum: Programming Talk
---

### Post by vegetarianshrimp on 2009-07-19
Hi everybody,
I've just started learning Python from a book called _Python Programming for the Absolute Beginner: Second Edition_. It's actually quite good. Well, I attached a few programs I made. Tell me what you think.

-VegetarianShrimp

---

### Post by Can+~ on 2009-07-19
The count4you is kinda redundant:

[PHP]for i in range(start, stop +1, by):
    print i,[/PHP]

could be written as:

[PHP]print range(start, stop+1, by)[/PHP]

Also, when dealing with user input, you might as well .strip() in case they left spaces in the input.

Aside from that, and the lack of [FONT="Courier New"]try-except[/FONT], the code is fine.

---

### Post by vegetarianshrimp on 2009-07-19
> **Can+~ said:**
> The count4you is kinda redundant:

[php]for i in range(start, stop +1, by):
    print i,[/php]could be written as:

[php]print range(start, stop+1, by)[/php].
Hmm...didn't notice that. Thanks.

> **Can+~ said:**
> 
Also, when dealing with user input, you might as well .strip() in case they left spaces in the input.

What exactly does that do?

> **Can+~ said:**
>  Aside from that, and the lack of [FONT=Courier New]try-except[/FONT], the code is fine.
I haven't learned about try-except yet, but looking forward to it. 


Thanks for your input!

---

### Post by Can+~ on 2009-07-19
> **vegetarianshrimp said:**
> What exactly does that do?

[mystring.strip("something")]("http://docs.python.org/library/stdtypes.html#str.strip") removes the characters passed on the argument from the string. It defaults to empty space, for example:

Default to space:
[PHP]>>> "       Hello World       ".strip()
'Hello World'[/PHP]

Remove 'a' and 'b':
[PHP]>>> "aaabbaaHello Worldbaaabbb".strip("ab")
'Hello World'[/PHP]

I say this because the user may input something like

[PHP]"y "*enter*[/PHP]

In which case doing, the comparison [FONT="Courier New"]userinput == "y"[/FONT] will fail.

---

### Post by vegetarianshrimp on 2009-07-19
> **Can+~ said:**
> [mystring.strip("something")]("http://docs.python.org/library/stdtypes.html#str.strip") removes the characters passed on the argument from the string. It defaults to empty space,
Oh. so this paired with ___.lower(), .strip() would be very helpful. Thanks

---

### Post by smartbei on 2009-07-20
You might want to check user input - perhaps you are waiting for try...except for this, but you can still check now. It is just more difficult. For example, in the BMI calcultor, if I input a letter instead of a number for my height...

Your party.py file is also programmed quite oddly - why not use a list, and a for loop? It could be far shorter:
```

...
    cart = []
    for amount in range(5):
        item = raw_input("\nWhat would you like to buy? ")
        if item.lower() == 'done':
            break
        else:
            cart.append(item)
...

```
And that's it!

BTW - printing a range looks like:
```

print range(10)
## outputs: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

```
Unless that is what you want, what you had before is probably better. For comparison:
```

for a in range(10):
    print a,
## outputs: 0 1 2 3 4 5 6 7 8 9

```

---

### Post by nvteighen on 2009-07-20
Ok, good.

But I believe you should read about functions now. Functions are the way to give a name to a certain chunk of code (like variables are the way to name a certain chunk of data)... Having the name of something allows you to call it whenever you want, therefore avoiding repetition and other advantages. E.g. when you want a sandwich, you don't have to describe what it is each time you want it... you just say "sandwich"... and if the other person doesn't understand you, you describe it once and tell him that that's called a "sandwich" and afterwards, when you say "sandwich", he'll understand.

This is because in your Party.py, I see that you repeat code in order to do exactly the same action: In case the user is not ready, ask him for more and add that to the cart. First, you use cart as a tuple () instead of a list [], which makes your life harder... (tuples are immutable, while lists are mutable). With little effort, you could change that into a function.

---

### Post by vegetarianshrimp on 2009-07-20
Thanks everyone for your replies, I found them helpful. I'm learning a lot on these forums!

---

### Post by vegetarianshrimp on 2009-07-30
Been a week. bump.

---

### Post by Sockerdrickan on 2009-07-31
> **vegetarianshrimp said:**
> Been a week. bump.
?

---

### Post by Mirge on 2009-07-31
I guess still looking for more feedback. Have you done anything new?

I haven't looked at your programs yet, after nvteighen & Can+~ posted I figured that they thorough enough, as they usually are :D.

---

### Post by veda87 on 2009-07-31
> mystring.strip("something") removes the characters passed on the argument from the string
is there any **C builtin** that would perform operation similar to that of **.strip()**

---

### Post by ibuclaw on 2009-07-31
> **veda87 said:**
> is there any **C builtin** that would perform operation similar to that of **.strip()**

There is nothing in C that can make you do it directly.

But with a few bespoke functions, you can do it.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* Return the length of the maximum trailing segment
   of S which contains only characters in ACCEPT.  */
size_t strrspn (s, accept)
    const char *s;
    const char *accept;
{
    const char *p;
    const char *a;
    size_t count = 0;
    
    for (p = s + strlen(s) - 1; *p != '\0'; --p)
    {
        for (a = accept; *a != '\0'; ++a)
            if (*p == *a)
            break;
        if (*a == '\0')
            return count;
        else
        ++count;
    }

    return count;
}

/* Return a string stripped of the maximum leading and trailing
      segment of S which contains only characters in ACCEPT.  */
char *strip(s, accept)
    const char *s;
    const char *accept;
{
    size_t slen = strlen(s), lead, trail;
    char *ret = malloc(slen + 1);

    if (!accept)
        accept = " \t";

    lead = strspn(s, accept);
    trail = slen - strrspn(s, accept);
    ret = strncpy(ret, s + lead, trail - lead);
  
    return ret;
}

int main()
{
    char *str1 = "         Hello        ";
    char *str2 = "abbabaabbWorldbbaabbaa";

    str1 = strip(str1, NULL);
    str2 = strip(str2, "ab");
    printf("'%s %s'\n", str1, str2);

    return 0;
}

```

edit:  Fixed code, can now compile with -O2 option.

---

### Post by nvteighen on 2009-07-31
> **veda87 said:**
> is there any **C builtin** that would perform operation similar to that of **.strip()**
Just for the record... None of the standard functions is actually built-in... They live in the Standard Library, which is another library. Built-in stuff in C just are the basic data types, the language's syntax and not more than that... that's what the compiler checks and processes. The function calls are resolved by the linker. :)

---

