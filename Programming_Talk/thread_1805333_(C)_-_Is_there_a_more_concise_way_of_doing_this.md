---
title: "(C) - Is there a more concise way of doing this?"
date: 2011-07-15
forum: Programming Talk
---

### Post by trilobite on 2011-07-15
Hi all. I've been working away at improving my understanding of pointers 
and have been wondering if there is a more concise way of printing a string *one character at a time* (using pointers). 
This is my code so far - 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void test(char *str)
{ 
   char *p = str; 
   int i=0;
   
   while(p[i]!='\0')
   { 
     printf("%c\n", p[i]); 
     i++;
   }                 
}     

int main() 
{   
  char *str = "wonderful"; 
  test(str); 
  return 0;   
}   

``` 

This works, but just wondering if there was a more concise way to do it (with pointers). (It's possible that there may not be a better way...) 
Thanks! 
- trilobite

---

### Post by karlson on 2011-07-15
> **trilobite said:**
> 
```
 
void test(char *str)
{ 
   char *p = str; 
   int i=0;
   
   while(p[i]!='\0')
   { 
     printf("%c\n", p[i]); 
     i++;
   }                 
}     

```


```


void test(const char *str)
{
    while('\0' != *str)
    {
        printf("%c\n", *str);
        ++str;
    }
}

```

---

### Post by trilobite on 2011-07-15
> **karlson said:**
> ```


void test(const char *str)
{
    while('\0' != *str)
    {
        printf("%c\n", *str);
        ++str;
    }
}

```

Hi Karlson - thanks for that! 
That is *much* better!  
( Doh - should have thought of that myself - it's quite obvious when you see it.... ;)  )  
Thanks again - bye for now - 
- trilobite

---

### Post by Bachstelze on 2011-07-15
The compiler optimizes both code to the same assembly, though. ;)

```
firas@aoba ~ % cat test1.c                                           
#include <stdio.h>

void test(char *str)
{ 
   char *p = str; 
   int i=0;
   
   while(p[i]!='\0')
   { 
     printf("%c\n", p[i]); 
     i++;
   }                 
}     
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -m32 -O2 -S test1.c
firas@aoba ~ % cat test2.c                                           
#include <stdio.h>

void test(const char *str)
{
    while('\0' != *str)
    {
        printf("%c\n", *str);
        ++str;
    }
}
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -m32 -O2 -S test2.c 
firas@aoba ~ % diff test1.s test2.s 
firas@aoba ~ % 

```

Not saying you shouldn't know such techniques, but don't overdo it either. You can quickly make your code hard to read for no benefit.

---

### Post by ve4cib on 2011-07-15
You could also do it with a for-loop instead of a while.  No real advantage, but it's another way of doing the same thing.

```

void test(char* str)
{
    char* ptr;
    for(ptr = str; *ptr!='\0'; ptr++)
        printf("%c\n", *ptr);
}
```


*EDIT: replaced NULL with '\0' character in loop evaluation*

---

### Post by Bachstelze on 2011-07-15
> **ve4cib said:**
> You could also do it with a for-loop instead of a while.  No real advantage, but it's another way of doing the same thing.

```

void test(char* str)
{
    char* ptr;
    for(ptr = str; *ptr!=NULL; ptr++)
        printf("%c\n", *ptr);
}
```

Oh God, no.

```
firas@aoba ~ % cat test.c
#include <stdio.h>

void test(char* str)
{
    char* ptr;
    for(ptr = str; *ptr!=NULL; ptr++)
        printf("%c\n", *ptr);
}
firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -c test.c
cc1: warnings being treated as errors
test.c: In function ‘test’:
test.c:6: warning: comparison between pointer and integer

```

NULL is a pointer. Never assume it to be anything else, or to have any specific value.

---

### Post by ve4cib on 2011-07-16
> **Bachstelze said:**
> Oh God, no.

...

NULL is a pointer. Never assume it to be anything else, or to have any specific value.


Yes, you are correct.  I should have proof-read my code more properly.  I've fixed it with the '\0' character instead.

---

### Post by lucasart on 2011-07-16
> **trilobite said:**
> Hi all. I've been working away at improving my understanding of pointers 
and have been wondering if there is a more concise way of printing a string *one character at a time* (using pointers). 
This is my code so far - 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void test(char *str)
{ 
   char *p = str; 
   int i=0;
   
   while(p[i]!='\0')
   { 
     printf("%c\n", p[i]); 
     i++;
   }                 
}     

int main() 
{   
  char *str = "wonderful"; 
  test(str); 
  return 0;   
}   

```This works, but just wondering if there was a more concise way to do it (with pointers). (It's possible that there may not be a better way...) 
Thanks! 
- trilobite
shorter than ever!
```

void test(const char *s)
{
  while (*s)
    printf("%c\n", *s++);
}

```Note that:
1/ thanks to compiler optimizations both versions are probably the same once compiled, so yours is probably just as fast at runtime.
2/ use the const keyword as much as possible, this is a safeguard against common programming errors. here the s variable is a const char *, meaning a variable pointer to a constant memory. so s++ is legal, but *s and more generally *(s+i) or if you prefer s[i] cannot be modified (compile error).

---

### Post by karlson on 2011-07-16
> **Bachstelze said:**
> 
Not saying you shouldn't know such techniques, but don't overdo it either. You can quickly make your code hard to read for no benefit.

Amen to that.

---

### Post by TheBuzzSaw on 2011-07-16
Heh, I was wondering when someone would post the compact version in lucasart's post. Well done. :]

---

### Post by Bachstelze on 2011-07-16
```
  while (*s)
```

Some people would consider this bad practice, and replace it with:

```
  while (*s != 0)
```

The reason being that [font=monospace]while (*s)[/font] gives the impression that *s semantically represents a boolean (i.e. the result of some test that can only be true or false), making the code harder to understand when it actually represents an integer that we test for equality to 0.

*EDIT:* Example for "some people":

> Never use non-boolean values implicitly as booleans in an if, while, or for statement. Instead, explicitly compare with or against the appropriate zero value for the type. For example, use

  if (p != NULL)
  if (strcmp(foo, bar) == 0)

rather than

  if (p)
  if (!strcmp(foo, bar))

There's no inefficiency with the former statements -- the compiler knows what it's doing -- and it's a lot clearer, when reading code, what you mean, and what the type of your variable is. (This one may be controversial. The 'if (p)' and '!strcmp' idioms are awfully common, but they obfuscate code without adding anything useful.)

Note, though, that if a function does return a boolean value, using it directly in a boolean expression is entirely appropriate, and explicitly testing it != 0 (or worse, explicitly testing it == 1) is a bad idea. 

[http://www.cs.columbia.edu/~hgs/etc/coding-style.html](http://www.cs.columbia.edu/~hgs/etc/coding-style.html)

---

### Post by TheBuzzSaw on 2011-07-16
While I agree with your position on the matter in general, I disagree in this specific instance. Personally, I can mentally process code much faster using all these shorthand methods. I abhor seeing "== 0", "== NULL", or "!= 0" anywhere it is unnecessary. It reinforces the concept that an if or while statement looks for anything but a zero (false) in order for it to be true.

---

### Post by lucasart on 2011-07-17
> **Bachstelze said:**
> ```
  while (*s)
```Some people would consider this bad practice, and replace it with:

```
  while (*s != 0)
```The reason being that [FONT=monospace]while (*s)[/FONT] gives the impression that *s semantically represents a boolean

Sorry, but for once I have to disagree with you. I'm writing C code and I thing as *s as a char, which it is. And booleans are really int in C. So the intent is really
```

while ((int)(*s))

```but this is a useless cast. In practice my code is perfectly ISO compliant (C89 and C99), and I find (*s) more readable than ('\0' != *s)

Besides, I can use your own argument against you , and say that
```
  while (*s != 0)
```
is dubious, because 0 is an int, and *s is a char, and you're doing an implicit int cast. Even though in compiled form after compiler optimizations, all those versions most like lead to equal assembly code.

---

### Post by Bachstelze on 2011-07-17
> **lucasart said:**
> Sorry, but for once I have to disagree with you. I'm writing C code and I thing as *s as a char, which it is.

No need for the aggressive tone. If you can see something like

```
while (*s)
```

and infer the type of *s, good for you. It's not obvious to me, and some very knowledgeable people agree. You are certainly not obliged to, I was just mentioning it.

> **lucasart said:**
> 
```
  while (*s != 0)
```
is dubious,

Actually, that's precisely what [font=monospace]while (*s)[/font] means:

> 6.8.5 Iteration statements

Syntax
1 iteration-statement:
while ( expression ) statement
do statement while ( expression ) ;
for ( expressionopt ; expressionopt ; expressionopt ) statement
for ( declaration expressionopt ; expressionopt ) statement

Semantics
4 An iteration statement causes a statement called the loop body to be executed repeatedly until **the controlling expression compares equal to 0**. The repetition occurs regardless of whether the loop body is entered from the iteration statement or by a jump.

---

### Post by TheBuzzSaw on 2011-07-17
Actually, 0 is almost typeless. You can do stuff like:
[php]int* ptr = 0; [/php]
but you cannot do:
[php]int* ptr = 1; [/php]

0 gets special treatment.

---

### Post by Bachstelze on 2011-07-17
> **TheBuzzSaw said:**
> Actually, 0 is almost typeless. You can do stuff like:
[php]int* ptr = 0; [/php]
but you cannot do:
[php]int* ptr = 1; [/php]

0 gets special treatment.

0 is only special in that it can also denote a null pointer. More precisely:

> 6.3.2.3 Pointers

3 An integer constant expression with the value 0, or such an expression cast to type void *, is called a null pointer constant. If a null pointer constant is converted to a pointer type, the resulting pointer, called a null pointer, is guaranteed to compare unequal to a pointer to any object or function.

0 is an integer constant and also a null pointer constant. That does not change its type, which is always int (unless you put a u or l prefix before it). Note that 0 is not the *only* null pointer constant: (void*)0 is also a null pointer constant, but has type void*. Both null pointer constants are equivalent only in pointer contexts, so

```
int *p = 0;
```

and

```
int *p = (void*)0;
```

are equivalent, but

```
int n = 0;
```

and

```
int n = (void*)0;
```

are obviously not. Also note that

> 7.17 Common definitions <stddef.h>

1 The following types and macros are defined in the standard header <stddef.h>. Some are also defined in other headers, as noted in their respective subclauses.
3 The macros are
NULL
which expands to an implementation-defined null pointer constant

So NULL expands to either 0 or (void*)0, at the implementer's discretion. As a result

```
int n = NULL;
```

may work on some implementations (but is obviously a bad idea).

---

### Post by Bachstelze on 2011-07-17
By the way, this is why [font=monospace]if (p)[/font] instead of [font=monospace]if (p != NULL)[/font] when p is a pointer works and is perfectly legal (style considerations put aside). [font=monospace]if (p)[/font] explicitly means [font=monospace]if (p != 0)[/font]. Since p is a pointer, the compiler recognizes that we are in a pointer context, and treats 0 as a null pointer constant, so the if statement will be considered false if and only if p is a null pointer.

> 6.5.9 Equality operators

Syntax
1 equality-expression:
relational-expression
equality-expression == relational-expression
equality-expression != relational-expression

Constraints
2 One of the following shall hold:
&#8212; both operands have arithmetic type;
&#8212; both operands are pointers to qualified or unqualified versions of compatible types;
&#8212; one operand is a pointer to an object or incomplete type and the other is a pointer to a qualified or unqualified version of void; or
**&#8212; one operand is a pointer and the other is a null pointer constant.**

Semantics
5 Otherwise, at least one operand is a pointer. **If one operand is a pointer and the other is a null pointer constant, the null pointer constant is converted to the type of the pointer.** If one operand is a pointer to an object or incomplete type and the other is a pointer to a qualified or unqualified version of void, the former is converted to the type of the latter.
6 Two pointers compare equal if and only if **both are null pointers**, both are pointers to the same object (including a pointer to an object and a subobject at its beginning) or function, both are pointers to one past the last element of the same array object, or one is a pointer to one past the end of one array object and the other is a pointer to the start of a different array object that happens to immediately follow the first array object in the address space.

Only the "both are null pointers" case may hold in 6 since the converted null pointer constant is a null pointer, and all the other cases require two non-null pointers.

---

### Post by ve4cib on 2011-07-17
> **Bachstelze said:**
> If you can see something like

```
while (*s)
```

and infer the type of *s, good for you. It's not obvious to me, and some very knowledgeable people agree. You are certainly not obliged to, I was just mentioning it.

I'm not entirely sure that being able to distinguish the type simply from looking at the loop's condition is even relevant.  After all, a char is effectively just a 1-byte integer.  Without any kind of context *s could be a char, a uint8_t (aka unsigned char), an int, a short, a double, a float, or anything else.

Out of context that loop just says that we're looping until the value at that address is zero.  We don't even know if we're incrementing or decrementing an array index, or if we're simply storing the result of some calculation at that specific address.

This leads to three recommendations I've found useful:

1- clearly defined & named variables.  Whenever possible give your variables meaningful names so that anyone could read the code and infer their use.  Put comments at their declarations to explain what they will be used for if it's not obvious from the name.  And try to declare your variables in one place so they're easier to find.  Variables declared on-the-fly can be a nuisance to read through, since you can't just skip to the top of the function to see what type something is declared as.

2- Insert comments before large blocks of code that explain what that block does (assuming it's not obvious to someone of moderate skill if they look at the entire block).

3- Use for-loops when you're iterating through something (like a string), and while loops the rest of the time.

```
while(*s)
```
is pretty ambiguous.  What is s, and how is it being used in the loop?

```
for(char *s = str_param; *s; s++)
```
is much clearer since we can see how we're moving through the array, and how we're using it to control the exit condition.
(In this case *s != '\0' might be nicer, but still optional)

---

### Post by Bachstelze on 2011-07-17
> **ve4cib said:**
> I'm not entirely sure that being able to distinguish the type simply from looking at the loop's condition is even relevant.

Actually, that's the whole point. ;) When you have a long piece of code, the variable definitions may not be visible on the same screen as the loop expression, so you are left with only the loop to figure out what the variable does (unless you want to continually skip back and forth). Comparing it to 0 to me makes it clear that it is an integer (if it is a pointer I compare it to NULL). I don't care whether it's an int or a char, that can generally be inferred from the loop body and is often irrelevant anyway. Determining whether it's a pointer or an integer, however, can be less obvious.

---

### Post by Lux Perpetua on 2011-07-17
All right, I'll be the one to ask the obvious question: why are you all using printf, a beast of a function, for the simple task of printing a single character?
```
void test(const char *s) {
    while (*s) putchar(*(s++));
}
```

---

### Post by Bachstelze on 2011-07-17
Obvious answer: your function is not equivalent to OP's. For the sake of the argument, I will assume you meant:

```
void test(const char *s)
{
    while (*s) {
        putchar(*(s++));
        putchar('\n');
    }
}
```

and I will answer with another obvious question: do you honestly think it makes the slightest meaningful difference in the case at hand? If anything, it's worse because it adds a line.

---

### Post by ve4cib on 2011-07-17
> **Bachstelze said:**
> Obvious answer: your function is not equivalent to OP's. For the sake of the argument, I will assume you meant:

```
void test(const char *s)
{
    while (*s) {
        putchar(*(s++));
        putchar('\n');
    }
}
```

and I will answer with another obvious question: do you honestly think it makes the slightest meaningful difference in the case at hand? If anything, it's worse because it adds a line.

I'm going to go out and say that adding a line of code isn't what makes the second version bad.  Adding lines of code doesn't really matter.  e.g. putchar(*(s++)); vs putchar(*s); s++;  Some might argue that breaking things up so that each line does exactly 1 thing makes the code more readable.

What matters in this case is the addition of a second, unnecessary function call.  Why call the same function twice, when you can call just one function that does exactly what you need it to do?

---

### Post by Bachstelze on 2011-07-17
> **ve4cib said:**
> 
What matters in this case is the addition of a second, unnecessary function call.  Why call the same function twice, when you can call just one function that does exactly what you need it to do?

I don't think the number of function calls matters a lot. I haven't studied the code of the functions, but it wouldn't surprise me if two calls to putchar consumed fewer CPU cycles than one call to printf. As I said in my latest post, I don't think the difference will be significant, but that's presumably what Lux Perpetua meant when he said "a beast of a function".

---

### Post by Lux Perpetua on 2011-07-17
> **Bachstelze said:**
> Obvious answer: your function is not equivalent to OP's. You're totally right; I was careless. In that case, I could go either way: one printf or two putchars, though the former is more "concise" (since that's what the thread is about). For speed, on the other hand, there is no contest (at least on my system): the printf version is almost 3 times as slow as the one with two putchars.

---

