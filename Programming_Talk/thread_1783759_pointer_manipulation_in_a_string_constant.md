---
title: "pointer manipulation in a string constant"
date: 2011-06-16
forum: Programming Talk
---

### Post by jamesbon on 2011-06-16
Here is a program which is working

```
#include<stdio.h>
int main ()
{
char c[]="GATE2011";
char *p=c;
printf("%s",p+p[3]-p[1]);
}

```The output is

```
2011
```
Now comes the problem I am not able to understand the operation ```
p+p[3]-p[1] 
```what is that pointing to?

My understanding is when I declare some thing like

```
char c[]="GATE2011"
```
Then c is a pointer pointing to a string constant and the string begins with G. In next line ```
*p=c;
``` the pointer p is pointing to same address which c is pointing. So how does the above arithmetic work?

---

### Post by dwhitney67 on 2011-06-16
As you probably already know, p points to the beginning of the string.

p[3] is 'E' and p[1] is 'A'.  If you subtract 'A' from 'E', you obtain 4.  It may seem weird, but if you consult with the ASCII table you will realize this is true.

Anyhow, p + 4 references the fourth character into the string.  When printing a string, using %s, the pointer offset is used and all characters are printed until a null-character is found.

Does this make sense now?


P.S.  You can also think of (p + 'E') - 'A'.  The result is the same.  The decimal value for 'E' is 69, whereas for 'A' it is 65.

---

### Post by r-senior on 2011-06-16
p[3] is 'E' and p[1] is 'A'. So p[3] - p[1] subtracts the ASCII code of 'A' (65) from the ASCII code of 'E' (69). 69 - 65 is 4.

So p + p[3] - p[1] adds 4 to the pointer p, making it point at c[4]. This is the '2' in "2011". printf will interpret this as the string starting with '2' up to the terminating '\0', so it prints "2011".

EDIT: too slow ;)

---

### Post by jamesbon on 2011-06-16
Yes **dwhitney67** this makes a lot of sense.Suppose I want to pass on such an array in a function then

among two choices
1)
> char *p="GATE2011";
function (p);

2)>  char p[]="GATE2011";
function(p);

which one is better or is the correct choice?
My understanding is both are doing the same thing or is there a difference in approach 1 and 2?
Given the fact I want to modify the string which I am passing in the function.

The string in both above approaches is a constant there is any difference in it?

---

### Post by dwhitney67 on 2011-06-16
For choice 1, you will not be able to modify the string.  But of course, you are permitted to index into it.

When declaring a string, as in choice 1, it is recommended that you preface the declaration with the keyword 'const'.  It serves as a reminder to the developer that the string cannot be modified.

I should add that choice 1 and 2 are *not* the same.  Choice 2 makes a copy of the string into an array.  Choice 1 merely sets up a pointer to a const string in memory.

P.S.  Declaring a string as const also helps prevent undesirable seg-faults in your application; for example consider the following code (which will crash if executed):
```

void function(char* str)
{
   *str = 'S';
}

int main()
{
   char* p = "some string";

   function(p);

   return 0;
}

```
Now, if I were to declare 'p' as a const char* and also modify function() to tell it to expect a const char* parameter, then the statement in the function where I attempt to modify the first character of 'str' would be flagged as an error by the compiler.

---

### Post by nvteighen on 2011-06-16
> **jamesbon said:**
> Yes **dwhitney67** this makes a lot of sense.Suppose I want to pass on such an array in a function then

among two choices
1)

2)
which one is better or is the correct choice?
My understanding is both are doing the same thing or is there a difference in approach 1 and 2?
Given the fact I want to modify the string which I am passing in the function.

The string in both above approaches is a constant there is any difference in it?

Although dwithney67 already told you the basics, I'll explain a bit further.

When you define a variable, you're doing three things: declaring, allocating and initializing it. Declaring means that you state that that symbol exists and has to be taken in account. Allocating means that memory will be assigned to that name. Initializing means that that memory is actually being filled with a known determined value for the first time (before initialization, that memory chunk surely held some data, but impossible to determine from your program's point of view).

Now, let's take a look on this:
```

char whatever[] = "Hello!";

```

The only "special" thing about that syntax is that the C compiler will determine the array's size automatically and will allocate the amount of space in the stack needed to hold the initial value. This isn't different to:

```

int whatever_again[4] = {2, 11, 0, -1};

```

Just that in that last case, we're setting the size manually (you can use [] here too).

Now, what about this?
```

char *something = "Hello!";

```

Literally, what you're doing there is defining a **pointer**: 1) you declare that a certain pointer-to-char called 'something' exists, 2) you allocate memory for that pointer in the stack (4 bytes in a 32-bit system; in 64-bit, things become less clear), 3) you initialize it... to what? You can't initialize it to the string, because pointers have constant size...

But remember that you declared a pointer. A pointer is a variable that holds a memory address to somewhere. And that string you've written has a place in memory (Hey, didn't you write it? It has to be somewhere!)... well, it is there sitting in your code, waiting. So, the pointer will actually hold the address of that string. But that string is stored in the code, not in the stack, so you can't modify it... it'd be like modifying a function, so that's why it's constant.

More formally, what happens is that in the pointer case, the string is stored in a place that's called the .data section and not in the stack. The .data section is part of the program's code, so it's unmodifiable, while the stack is created in memory... If you ever get into ASM programming, you'll get the technical in and outs, but the effects can be understood without delving into that.

---

### Post by Arndt on 2011-06-16
> **dwhitney67 said:**
> 

P.S.  You can also think of (p + 'E') - 'A'.  The result is the same.  The decimal value for 'E' is 69, whereas for 'A' it is 65.

I think that this is not entirely reliable. p+69 is not necessarily a valid pointer (in the example here, it points beyond the string), and there may exist architectures (segmented ones, for example) where such a pointer cannot even be formed. If I remember correctly, the C standard explicitly allows for a pointer one step beyond the end of valid memory to be formed, but says that others are undefined. This may have changed in the most recent standard, though.

---

### Post by JupiterV2 on 2011-06-16
I think the explicit point is that an array is NOT a pointer, and vice-versa. Unfortunately, C code often appears to blend the lines between the two and leads to a lot of misconceptions. For example:

```
#include <stdio.h>

void my_print (const char *str)
{
  printf ("%s\n", str);
}

int main (void)
{
  char char_array[] = "Hello!";

  my_print (char_array); // notice no address-of (&) operator
  return 0;
}
```

This makes it appear that you can treat an array like a pointer. That's because an array variable in C is actually a pointer to the first index, as others have already stated. You can also index a pointer just like an array.

```
#include <stdio.h>
int main (void)
{
  int x[] = {1,2,3,4}
  int* y = x; // points to element 1 of x

  printf ("%d\n", y[2]); // will output '3', as expected
  return 0;
}
```

The above code makes a lot of assumptions. It assumes that the chunk of memory is contiguous. y[2] == y+2 == (value_at_address y plus 2) == 3. Due to lack of bounds checking in C, this can get quite dangerous and you need to be mindful of it. Second, if your local array is in a different scope than your pointer, you could easily end up pointing to invalid memory, leading to a segfault. Character arrays (strings) can lead to all kinds of issues.

Another example:
```
#include <stdio.h>

int main (void)
{
  int arr[4];
  int *arrptr = arr;

  // the following will produce different sizes
  printf ("sizeof (arr) = %d\n", sizeof (arr));
  printf ("sizeof (arrptr) = %d\n", sizeof (arrptr));
  return 0;
}
```

---

