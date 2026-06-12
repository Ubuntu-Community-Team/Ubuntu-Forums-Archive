---
title: "undefined reference to an undefined variable"
date: 2011-06-11
forum: Programming Talk
---

### Post by jamesbon on 2011-06-11
Hi,
here is my piece of code
```
#include<stdio.h>
 main ()
{
        extern int i;
        i=20;
     printf("%d",i);
}

```

When I compile it I get error 
```
ka2.c: In function &#8216;main&#8217;:
ka2.c:6: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
/tmp/ccGXrSE5.o: In function `main':
**ka2.c:(.text+0x6): undefined reference to `i'**
collect2: ld returned 1 exit status
```

I want to know the reason of error in lines which I have bolded.

---

### Post by Barrucadu on 2011-06-11
You are saying 'i' is an extern, but not linking to any files which define it.

---

### Post by simeon87 on 2011-06-11
Why did you define i to be external? It seems to me you just want a local variable i:

```
#include<stdio.h>
 main ()
{
        int i;
        i=20;
     printf("%d",i);
}
```

---

### Post by jamesbon on 2011-06-11
Actually I am trying to understand use of extern so I am using it this way,but I am not yet clear as to why is it not working.As far as I understand using extern I have declared the variable and in next line I have defined.So what is the problem ,I mean why is that error?

---

### Post by schauerlich on 2011-06-11
> **jamesbon said:**
> Actually I am trying to understand use of extern so I am using it this way,but I am not yet clear as to why is it not working.As far as I understand using extern I have declared the variable and in next line I have defined.So what is the problem ,I mean why is that error?

With extern, you're saying "this exists somewhere", not "this exists here". The variable 'i' does not refer to an area of memory unless you link to a module which contains a definition of 'i'.

```
// bar.c
int i;
```

```
// foo.c

#include <stdio.h>

extern int i;

int main(void) {
  i = 20;

  printf("%d\n", i);

  return 0;
}

```

So this works:
```
$ gcc -Wall bar.c foo.c -o foo.out
$ ./foo.out 
20

```

But this doesn't:
```
$ gcc -Wall foo.c -o foo.out
Undefined symbols:
  "_i", referenced from:
      _main in ccsIBLR4.o
      _main in ccsIBLR4.o
ld: symbol(s) not found
collect2: ld returned 1 exit status

```

---

### Post by jamesbon on 2011-06-11
Thanks for the nice explanation.Here is one small article which I was trying to understand with respect to this 
[http://wiki.answers.com/Q/Difference_between_the_definition_and_declaration_of_a_variable_in_c](http://wiki.answers.com/Q/Difference_between_the_definition_and_declaration_of_a_variable_in_c)

the above link says
> For a variable, the definition is the statement that actually allocates memory. For example, the statement: 
long int var; 
is a definition. On the other hand, an extern reference to the same variable: 
extern long int var; 

This has confused me maximum,I got your point that declaring extern will not allocate any memory so it is just a declaration.But what does the statement which I quoted imply?

---

### Post by schauerlich on 2011-06-11
> **jamesbon said:**
> Thanks for the nice explanation.Here is one small article which I was trying to understand with respect to this 
[http://wiki.answers.com/Q/Difference_between_the_definition_and_declaration_of_a_variable_in_c](http://wiki.answers.com/Q/Difference_between_the_definition_and_declaration_of_a_variable_in_c)

the above link says

This has confused me maximum,I got your point that declaring extern will not allocate any memory so it is just a declaration.But what does the statement which I quoted imply?

That article isn't very clear on the difference. Look at [this](http://www.edaboard.com/thread124112.html#post540943) post instead. (I've also edited my post, as it seems i switched the words definition and declaration on accident. Oops).

Basically: defining a variable is like building a box. Declaring a variable is like giving you a piece of paper that tells you what the box looks like. You only need to build the box once, but any time you want to use the box outside of the file in which it was made, you need to tell the compiler what sort of box it needs to go find. The 'extern int i' in foo.c is telling the compiler that it should be looking for a box in some other file that's an integer that's named 'i'.

I hope I didn't stretch that analogy too far.

---

### Post by jamesbon on 2011-06-12
Thanks I am clear now. Declaring some thing as extern is like a strict declaration i.e. compiler does not allocate any memory while declaring and all declarations of a variable are definitions with extern being an exception.

---

### Post by BkkBonanza on 2011-06-12
extern simply means it's not in this file/object module. It does already exist in the program and has to be defined somewhere in order to work.

---

### Post by Arndt on 2011-06-12
> **BkkBonanza said:**
> extern simply means it's not in this file/object module. It does already exist in the program and has to be defined somewhere in order to work.

Well, it's not an error for the entity to be defined in this file. For example, a header file using extern to declare something is typically included in the source file that actually defines it.

---

