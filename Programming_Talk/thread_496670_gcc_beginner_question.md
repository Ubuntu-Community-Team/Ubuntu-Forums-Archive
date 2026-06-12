---
title: "gcc beginner question"
date: 2007-07-09
forum: Programming Talk
---

### Post by phatty420 on 2007-07-09
I am getting a warning while compiling, but the program still compiles and runs as expected.

the error is: *func_ex.c:11:2: warning: no newline at end of file*

the code I am using is:

```

#include <stdio.h>

main()
{
	hello_World();
	return(0);
}
hello_World()
{
	printf("hello world\n");
}

```

I am just experimenting with functions in C. can anyone tell me why that warning is showing, and how I could change the code so that it doesn't show anymore?

---

### Post by meatpan on 2007-07-09
gcc is a complex program, so it helps to post the entire gcc command you used, in addition to the code you are trying to compile.  

That said, are you using  a special IDE, or something more simple like vi?  You should just try putting in a newline (press enter on the last line)  at the end of the file and see if the message persists.

---

### Post by Wybiral on 2007-07-09
Unrelated, but your functions have no type!

```

#include <stdio.h>

main()
{
	hello_World();
	return(0);
}
hello_World()
{
	printf("hello world\n");
}

```

Should be:

```

#include <stdio.h>

void hello_World()
{
	printf("hello world\n");
}

int main()
{
	hello_World();
	return(0);
}

```

It still compiles the other way, but that's how it should look. You also want to declare your function first (unless you prototype it) before using it.

Also, if the compiler complains about a lack of newline at the end of the file, add a newline.

But, that's a warning... Not an error. Warnings are fine, errors wont compile.

Warnings are just there to remind you of how it should look or that something might be wrong, in this case a newline at the end of a source file is standard in C and the compiler is letting you know that.

---

### Post by phatty420 on 2007-07-09
> gcc is a complex program, so it helps to post the entire gcc command you used, in addition to the code you are trying to compile.

The original command was:
```
gcc -o func_ex func_ex.c
```

After that I tried an extra argument (in the name of science 8) ):

```
gcc -o -Wall func_ex func_ex.c
```

This was my compiler output:
```
func_ex.c:11:2: warning: no newline at end of file
func_ex: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o:(.text+0x0): first defined here
func_ex:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o:(.rodata+0x0): first defined here
func_ex: In function `_fini':
/build/buildd/glibc-2.5/build-tree/i386-libc/csu/crti.S:52: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o:/build/buildd/glibc-2.5/build-tree/i386-libc/csu/crti.S:52: first defined here
func_ex:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
func_ex: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o:(.data+0x0): first defined here
func_ex: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.1.2/crtbegin.o:(.data+0x0): first defined here
func_ex: In function `_init':
/build/buildd/glibc-2.5/build-tree/i386-libc/csu/crti.S:36: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o:/build/buildd/glibc-2.5/build-tree/i386-libc/csu/crti.S:36: first defined here
/tmp/ccqrBEIs.o: In function `main':
func_ex.c:(.text+0x0): multiple definition of `main'
func_ex:(.text+0xa4): first defined here
/tmp/ccqrBEIs.o: In function `hello_World':
func_ex.c:(.text+0x24): multiple definition of `hello_World'
func_ex:(.text+0xc8): first defined here
collect2: ld returned 1 exit status

```

hahahaha!

Honestly, I have experience programming in BASIC, and was checking C out.  The example that made me start messing around with functions is this:
```

/******************************************************/
/*                                                    */
/* Program : do nothing                               */
/*                                                    */
/******************************************************/

main()                          /* Main program */
{
  do_nothing();
}

/******************************************************/

do_nothing()                 /* Function called */
{
}

```

Taken from the GCC online tutorial.  So, I just altered it a bit to make a "hello World" example.

---

### Post by Wybiral on 2007-07-09
The function declaration should go before it's used (before main) and you need to declare your functions with a type, in this case "int main()" and "void hello_world()"

---

### Post by lisati on 2007-07-09
> **Wybiral said:**
> The function declaration should go before it's used (before main) and you need to declare your functions with a type, in this case "int main()" and "void hello_world()"

The "int main()" is a good habit to get into. Although it doesn't matter too much in "Hello World" programs, you'll need it when you write programs that might need to tell the OS about success (or otherwise) of what your program is doing.

---

### Post by phatty420 on 2007-07-09
Ok, now this is gonna sound like a major noob question but, if I use 'int main()' every time, will it cause a problem or can I use it for every single C program I write?

Also, I am quite ignorant to how 'void' and 'int' or even types altogether work!  Does anyone know off hand of an article that I could read that will help clarify things a bit for me?


Edit: I finally understand what you meant by return "newline" at the end of file: There can't be a bracket at the bottom of the file.

I kept trying to put a newline character ('\n') at the end of the file!!!  I just hit 'return' at the bottom bracket, and now the are no errors (or warnings)!!

---

### Post by Wybiral on 2007-07-09
> **phatty420 said:**
> Ok, now this is gonna sound like a major noob question but, if I use 'int main()' every time, will it cause a problem or can I use it for every single C program I write?

Also, I am quite ignorant to how 'void' and 'int' or even types altogether work!  Does anyone know off hand of an article that I could read that will help clarify things a bit for me?


Edit: I finally understand what you meant by return "newline" at the end of file: There can't be a bracket at the bottom of the file.

I kept trying to put a newline character ('\n') at the end of the file!!!  I just hit 'return' at the bottom bracket, and now the are no errors (or warnings)!!

OK, you said you come from the BASIC world, right?

In most BASIC languages variables are postfixed with a: #, %, or $ to denote that it's a float (real number with decimal), int (non decimal number), or string (a block of text or characters).

In C however, there are no postfix identifiers.

"int" for example is an integer. It's a non-decimal number. What you are doing when you say "int main()" is saying that the function "main" returns an "int" which is what the operating system expects. This is why you use "return(0)" at the end of "main" (to send a 0 back to the OS, which generally means that everything went fine with no errors).

But, other functions can return values too, not just "main" returning an "int". However, some functions don't want to return anything, such as your "hello_world" so they are of type "void" (void as in... nothing. Pretty easy to remember)

If you've never used "printf" to print an integer, here is the format:
```

printf("%i \n", 10);

```
That will print "10" then a newline.

Knowing this... You can mess with functions returning various values such as:

```

#include <stdio.h>

int one()
{
    return 1;
}

int main()
{
    printf("%i \n", one());
    return(0);
}

```

And naturally combining function parameters and return values you can construct useful functions such as:

```

#include <stdio.h>

int add(int a, int b)
{
    return a + b;
}

int main()
{
    printf("%i \n", add(10, 20));
    return(0);
}

```

This is why I say it's important to always declare functions with return types... And if they return nothing, use the void type. It makes for much clearer and more standard C code.

---

### Post by phatty420 on 2007-07-09
Ahh, thank you very much that clarifies alot actually!!

First I was thinking that 'int' when used before main() meant initialize or initiate.  I knew that 'int' was also used to declare variables of type integer, so I was confused at when to use 'int' which way!!  I really didn't (and still not as much as I would like to) understand the whole 'return(0)" concept, so it was really confusing for me!!

> In most BASIC languages variables are postfixed with a: #, %, or $

Yes, and in BASIC languages you can use any letter identifier.  Is it the same for C, or do I have to use '%i' specifically for an integer?

---

### Post by Wybiral on 2007-07-09
> **phatty420 said:**
> Yes, and in BASIC languages you can use any letter identifier.  Is it the same for C, or do I have to use '%i' specifically for an integer?

Nope. In C that is specified when you declare the variable...

int a;
is the same as
DIM a%

float a;
is the same as
DIM a#

char *a;
is... well similar to...
DIM a$

The strings are different (the "char *" type) because they aren't a built-in type in C, they're just an array of characters (which logically makes a "string".

Try...

```

#include <stdio.h>

int one()
{
    return 1;
}

int main()
{
    int two;
    two = one() + 1;
    printf("%i \n", two);
    return(0);
}

```

"two" is a variable of type "int" which is similar to the BASIC "%" type.

The "return(0)" is there because "main" is a function... It's what the OS calls, and it expects it to return an integer.

You can actually view the int from the command line in Linux using the command: "echo $?"

So try this... Run this program from the command line:

```

int main()
{
    return 7;
}

```

Then immediately after running it type this in the command line:

```

echo $?

```

It should echo 7!

That's why main should always be type "int".

---

### Post by phatty420 on 2007-07-09
Ok, I have two quick questions about you last post.  

1) What is the '%i' used for?

2) Why aren't there any parentheses around the 7 in 'return 7;'?

---

### Post by Wybiral on 2007-07-09
> **phatty420 said:**
> Ok, I have two quick questions about you last post.  

1) What is the '%i' used for?

2) Why aren't there any parentheses around the 7 in 'return 7;'?

"%" has a whole different purpose in C then in BASIC. "%" in C is the remainder of a division.

For function returns, you don't need to use parenthesis... Some people do to fit the scheme of the language, but I don't usually because "return" isn't a function itself (so why use the function notation)

Basically:

return 10;
Is the same as 
return (10);

and...

return a;
is the same as
return(a);

It's up to you.

---

### Post by phatty420 on 2007-07-09
> "%" has a whole different purpose in C then in BASIC. "%" in C is the remainder of a division.

I'm sorry the 'i' is hard to see, let me clarify my question a bit more:

I asked previously:
> do I have to use '%i' specifically for an integer?

because you used 
```
%i
```

in place of the integer, and in this example:
```
printf("%i \n", two);
```

the ' i ' in ' % i ' is not declared :S

---

### Post by Wybiral on 2007-07-09
OHHH... Sorry, I didn't realize you meant in the "printf" function...

OK...

The "%i" is in the string if you notice, that's what tells the "printf" function how to format your text.


Try this...

```

#include <stdio.h>

int main()
{
    printf("%i people came, and only %i people left.\n", 100, 50);
    return 0;
}

```

Notice how "%i" is used each time I need an integer in the string? Then, after the format string is given, each variable is passed in order of use. Other then "%i" you can also use "%f" and "%s" for float and string. Check this out...

```

#include <stdio.h>

int main()
{
    int   people  = 1000;
    float percent = 10.5;
    char  *bob    = "Hello everyone!";
    
    printf("Of %i people, %f percent stayed. Bob says, '%s'. \n", people, percent, bob);
    return 0;
}

```

The "%i", "%f", and "%s" are just placeholders in the "printf" function's format string that tell it where to put the data given afterwards.

---

### Post by phatty420 on 2007-07-09
WOAH!!! I get it!  So instead of using the actual variable, you use the "place-holders" then, print the variables after the statement.  Ok, Thanks alot.  I appreciate you taking the time to respond, and I think you have help to break the learning barrier I've had at trying to learn by comparison (which just isn't working) between BASIC and C.

---

