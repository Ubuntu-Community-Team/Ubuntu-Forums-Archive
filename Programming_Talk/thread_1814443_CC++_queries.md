---
title: "C/C++ queries"
date: 2011-07-29
forum: Programming Talk
---

### Post by shashanksingh on 2011-07-29
Hi all.
Ive been learning C/C++ concepts lately.
And fiddling around with it.
I've made this common thread where Ill ask my queries. (assuming there will be more to come)

I made a small file, but the abs() function apparently worked without importing he stdlib.h file

It returns a value 1 for non-zero and 0 for zero.
Here's the code

```

#include <stdio.h>
//#include <stdlib.h>

void main()
{
	int a=abs(10.4125);
	printf ("a is %d",a);
}

```

What exactly is THIS abs()??

---

### Post by nvteighen on 2011-07-29
> **shashanksingh said:**
> Hi all.
Ive been learning C/C++ concepts lately.
And fiddling around with it.
I've made this common thread where Ill ask my queries. (assuming there will be more to come)

I made a small file, but the abs() function apparently worked without importing he stdlib.h file

It returns a value 1 for non-zero and 0 for zero.
Here's the code

```

#include <stdio.h>
//#include <stdlib.h>

void main()
{
	int a=abs(10.4125);
	printf ("a is %d",a);
}

```

What exactly is THIS abs()??

Ok, various things.

In modern C (I assume you're using C, as you're #include'ing stdio.h and stdlib.h), main should be declared like this:
```

int main(void)
{
    ...
    return 0; // 0 is "success" usually. Use something else on error
}

```
or, if you want to capture command line arguments:
```

int main(int argc, char **argv)
{
    ...
    return 0;
}

```

Only in *C++* you can go with:
```

int main()
{
   ...
   // implicit 'return 0;'
}

```

That's about main's signature.

Now, about your problem: yes, abs() is declared at stdlib.h and portable C code should explicitly include that header to use that. But as gcc automatically links your program with the C Standard Library, the function is found even though you don't declare it.

Header files just tell the compiler that a certain function exists outside the file, what arguments it takes and what it returns (so that it can check types). Headers don't implement anything (except in C++... but you'll know about this when you learn about templates). External functions are found by the linker when everything has been compiled to object code.

---

### Post by shashanksingh on 2011-07-29
A need help on a few fundamentals....

1. What happens if I use void main instead of int main? I mean where is the return value actually used, and the drawbacks of not returning any value.

2. I needed to be clear on something Im confused at. When I say #include <stdio.h>, I read # means a DIRECTIVE. So am I telling the compiler to just dump in all the code in the beginning of the same file (which i doubt coz in that case, the size would be huge)? Or is just for the compiler to check for the class definations, function usage and the linker will directly put, in binary, the functions Iv'e used? So that doesnt make the object file the exact binary, but similar to a BYTECODE (I used to program in java, got typecast :neutral:)?

3. About my previous doubt, even if gcc dynamically included abs, it is not performing the stdlib abs function here, rather, its just returning me a zero/non-zero value, while I have nowhere defined abs.


Grateful for the patience in answering any of these.

---

### Post by Simian Man on 2011-07-29
> **shashanksingh said:**
> 1. What happens if I use void main instead of int main? I mean where is the return value actually used, and the drawbacks of not returning any value.
It returns the result back to whoever called the program.  Usually this is the shell who ignores the result, but it could be another program.  The return value indicates whether the program was "successful" - however you want to define that.  Returning 0 indicates success and anything else is failure.  Either way you should always declare main as int because the standard says you must.

> **shashanksingh said:**
> 2. I needed to be clear on something Im confused at. When I say #include <stdio.h>, I read # means a DIRECTIVE. So am I telling the compiler to just dump in all the code in the beginning of the same file (which i doubt coz in that case, the size would be huge)? Or is just for the compiler to check for the class definations, function usage and the linker will directly put, in binary, the functions Iv'e used? So that doesnt make the object file the exact binary, but similar to a BYTECODE (I used to program in java, got typecast :neutral:)?
When you #include a file, it DOES actually just copy and paste the header file into your source code.  If you want to see this, compile a file with the -E option to gcc.  This will make gcc dump the pre-processed file to the screen for you to see.

As nvteighen said, header files (mostly) just contain declarations, so putting all of this into your C files doesn't necessarily cause all of those functions to be included in your final program.  It's definitely not any kind of byte code.

> **shashanksingh said:**
> 3. About my previous doubt, even if gcc dynamically included abs, it is not performing the stdlib abs function here, rather, its just returning me a zero/non-zero value, while I have nowhere defined abs.

First of all, abs takes an integer, not a float (use "fabs" for that).  Secondly, I hate to say this, but I have no idea why it returns the wrong result when you don't include stdlib, and the right result when you do.  I get the same behaviour and it makes no sense to me at all.  When I changed the 10.4125 to just 10, then it works with or without the include, but that shouldn't matter.  I'm confused :).

---

### Post by nvteighen on 2011-07-29
> **shashanksingh said:**
> A need help on a few fundamentals....

1. What happens if I use void main instead of int main? I mean where is the return value actually used, and the drawbacks of not returning any value.


The return code is sent back to whatever called your program. It can be the shell, a shell script or some other program that used system(), popen() to call yours. Sometimes, that code is critical for the caller... For example, if your program exits with errors, it may be desirable to stop the shell script that called it... and the only way to do that is by returning some code that the script can check for.

Also, there might be other consequences. The valid signatures of main are defined by the standard... and compilers can only be expected to comply with the standard, not anything else. Using something different than what I referred to in the other post may render your code uncompilable.

> 
2. I needed to be clear on something Im confused at. When I say #include <stdio.h>, I read # means a DIRECTIVE. So am I telling the compiler to just dump in all the code in the beginning of the same file (which i doubt coz in that case, the size would be huge)? Or is just for the compiler to check for the class definations, function usage and the linker will directly put, in binary, the functions Iv'e used? So that doesnt make the object file the exact binary, but similar to a BYTECODE (I used to program in java, got typecast :neutral:)?


The #whatever are **preprocessor** directives. A C program undergoes 4 stages when it's compiled: preprocessing, compilation, assembling and linking. The first 3 stages are performed on each source file **separately**. What follows is long, but simple.

1. **Preprocessing**: as said above it's done to each source file separately. It consists of preparing the source code for compilation, so that all information needed is available. In most cases, it's about #include and macros. All #include does is to paste the header into a *temporary* copy of your source file. But remember that headers don't have code! The code is in an already compiled binary file.

2. **Compilation**: The preprocessed C code is turned into Assembly. For this, the compiler needs to know the definitions for each type, basicially so it can calculate the offsets needed in Assembly. Again, this is done on each module separately... so this is why you need to #include things from start, because when the compiler acts on a module, it doesn't know anything but the preprocessed source file. The declarations in a header file aren't code, they're just "instructions" for the compiler and are discarded at this stage; this is why your example doesn't become a massive MB-sized executable.

3. **Assembling**: Assembly translates 1:1 to native binary code and that's what assembling is about. The output is a so-called "object file", a binary file that's just the translation of your C code.

4. **Linking**: This is done at last, when all object code files have been produced. The linker bundles all object code files into one executable and dynamically links to the libraries you've told it to link... (the Standard Library is linked by default). It's here where functions are actually looked for, because everything is known at this stage; if some function can't be found, the linker will stop and signal an "undefined reference" error.

> 
3. About my previous doubt, even if gcc dynamically included abs, it is not performing the stdlib abs function here, rather, its just returning me a zero/non-zero value, while I have nowhere defined abs.

Grateful for the patience in answering any of these.

Don't know what's called there, then. And this is a great reason to avoid these kind of things: this is called "undefined behavior" and it's a programmer's worst nightmere... (when things work or don't but because of some unknown consequence). If you want to use a function, always include the header where it's been declared.

Also, always use -Wall when compiling; it turns all warnings on and helps to spot things that are very likely to induce undefined behavior. If you used that, you'd know that you can't use abs() on a float (it's declared: int abs(int)).

Hope this helps.

---

### Post by nvteighen on 2011-07-29
> **Simian Man said:**
> 
First of all, abs takes an integer, not a float (use "fabs" for that).  Secondly, I hate to say this, but I have no idea why it returns the wrong result when you don't include stdlib, and the right result when you do.  I get the same behaviour and it makes no sense to me at all.  When I changed the 10.4125 to just 10, then it works with or without the include, but that shouldn't matter.  I'm confused :).

What did you expect? ("Schweppes"). As soon as you do something that doesn't comply with the standard, anything can happen! ;)

---

### Post by Simian Man on 2011-07-29
After thinking about it a little more, I have an explanation for the abs issue.  The reason is that, when you don't declare a function in C, the compiler guesses the signature of the function from the usage.  In this case, since you pass a float to abs, the compiler assumes that abs takes a float as a parameter and passes the bits making up the floating point representation of 10.4125 to the function.  Then the linker finds the function abs and links to it.  The end result is that abs expects to have an integer, but instead got a float.  For whatever reason the floating point representation of 10.4125 was mapped to 1.

When you declare the function abs by including stdlib.h, the compiler can see that abs is supposed to take an integer, so it casts 10.4125 to an integer first.  When this is done, then abs returns the expected result of 10.  That was quite a tricky problem you found for a beginner :).

> **nvteighen said:**
> What did you expect? ("Schweppes"). As soon as you do something that doesn't comply with the standard, anything can happen! ;)
Always good advice :).

---

### Post by shashanksingh on 2011-07-29
Helped is an understatement.
:D

Thanks a lot. Really eloberated, I find these formus much more apt than googling. :)

I may need some time to digest this thoroughly, ill bump in any more queries...

---

### Post by Bachstelze on 2011-07-29
As for why abs() returns 1, basically the catch is that when you don't include stdlib.h, the compiler does not know that it expects an int as its argument, and since you're giving it a float, it assumes you know what you are doing and that the function takes a float as its argument. It then does some complicated assembly with the movsd instruction that I would need to analyse further, but supposedly it would work fine if abs() was taking a float as it's argument, but does not work with a function that expects an int.

> **nvteighen said:**
> 
Also, always use -Wall when compiling; it turns all warnings on and helps to spot things that are very likely to induce undefined behavior. If you used that, you'd know that you can't use abs() on a float (it's declared: int abs(int)).

As I said in another thread, even use -pedantic -Wall -Werror. -pedantic turns on more warnings, some of them are more warnings of bad practice than outright errors (for example declaring variables and not using them), but they always make sense and following them is always a good idea. -Werror is more about "saving you from yourself", because it's very easy to ignore warnings, like "To hell with warning, I've been coding this big function for two hours, I want to test it right now, I can get rid of warnings later." IMO this is not the right attitude, and if there are warnings, you should fix the problem immediately, not "later". If you compile with -Werror, you don't have a choice: you won't get your program util you get rid of all the warnings.

---

### Post by shashanksingh on 2011-07-29
Ok, just let me know if I got this somewhat right.

```
#include <stdio.h>

int main()
{
    int a=10;
    printf("%d",a);
}

```

If we consider the above simple C file...

1.The pre-processor will just dump all the DECLERATIONS that are required for compiler, and not necessarily the DEFINITIONS, which are somewhere else, or directly in a compiled binary. I saw a lot of "extern" references when I did gcc -E, so I think it just lets the compiler know the offsets, the parameter passing, giving it a valid API(sort of) of the actual binary somewhere.

2. The compiler checks this (API), defines offcodes for my own DEFINED LOCAL variables and functions making sure if it feels it should work fine.

3. The ASSEMBLER makes a BINARY code which is in assembly language of the above.

4. The linker then links it to all the required functions to get the resultant binary. A doubt here.
When I say LINKING, I assume my printf function would be in /usr/lib/somewhere, or somewhere in the RAM (BINARY), and the LINKER will basically BRING TOGETHER all the BINARY BLOCKS needed together (from the standard and explicitly mentioned libraries), and make the STANDALONE executable. STANDALONE as in LITERALLY. It wont need any more references from anywhere I suppose.

---

### Post by Bachstelze on 2011-07-29
> **shashanksingh said:**
> 
1.The pre-processor will just dump all the DECLERATIONS that are required for compiler, and not necessarily the DEFINITIONS, which are somewhere else, or directly in a compiled binary. I saw a lot of "extern" references when I did gcc -E, so I think it just lets the compiler know the offsets, the parameter passing, giving it a valid API(sort of) of the actual binary somewhere.

Right. The declarations are not strictly required, but I can't think of any reasonable use case where omitting them would make sense, so they might as well be.

> 3. The ASSEMBLER makes a BINARY code which is in assembly language of the above.

No, the binary is a binary, it is not really in any "language".

> 4. The linker then links it to all the required functions to get the resultant binary. A doubt here.
When I say LINKING, I assume my printf function would be in /usr/lib/somewhere, or somewhere in the RAM (BINARY), and the LINKER will basically BRING TOGETHER all the BINARY BLOCKS needed together (from the standard and explicitly mentioned libraries), and make the STANDALONE executable. STANDALONE as in LITERALLY. It wont need any more references from anywhere I suppose.

This is not entirely true. The executable may still need dynamic libraries, and actually it does if you compile it with the default settings in Ubuntu:

```
firas@itsuki ~ % cat test.c                                         
#include <stdio.h>

int main()
{
    int a=10;
    printf("%d",a);
}
firas@itsuki ~ % gcc -std=c99 -pedantic -Wall -Werror -o test test.c 
firas@itsuki ~ % ldd test
        linux-gate.so.1 =>  (0x00bc4000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00cbe000)
        /lib/ld-linux.so.2 (0x001e7000)

```

Notice for example that the standard library (libc) is dynamically linked. This makes sense: you don't want to embed the whole standard library into your program just for one function.

---

### Post by Arndt on 2011-07-29
> **Bachstelze said:**
> 
```

firas@itsuki ~ % ldd test
        linux-gate.so.1 =>  (0x00bc4000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00cbe000)
        /lib/ld-linux.so.2 (0x001e7000)

```

Notice for example that the standard library (libc) is dynamically linked. This makes sense: you don't want to embed the whole standard library into your program just for one function.

What happens when you link statically is not that you get the whole library added - the linker picks only those object files from the archive that are needed. That may still be a lot, and/or you may want your program to take advantage of improvements in the standard library without relinking, so there are still good points to dynamic linking.

---

### Post by Bachstelze on 2011-07-29
Actually, the code posted in OP prints 1 only when compiled in 64 bit mode, in 32 bit mode it prints 858993459:

```
firas@aoba ~ % cat test.c 
#include <stdio.h>
//#include <stdlib.h>

int main(void)
{
	int a=abs(10.4125);
	printf ("a is %d\n",a);
}

firas@aoba ~ % cc -o test64 test.c 
firas@aoba ~ % cc -m32 -o test32 test.c
firas@aoba ~ % ./test32 
a is 858993459
firas@aoba ~ % ./test64 
a is 1
```

In the 32 bit case, the value is indeed the binary value representing 10.4125 (actually its lower 32 bits because it is a double) read as an integer:

```
firas@aoba ~ % cc -S -m32 -o test32.s test.c
firas@aoba ~ % cat test32.s 
	.cstring
LC1:
	.ascii "a is %d\12\0"
	.text
.globl _main
_main:
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ebx
	subl	$36, %esp
	call	L3
"L00000000001$pb":
L3:
	popl	%ebx
	leal	LC0-"L00000000001$pb"(%ebx), %eax
	movsd	(%eax), %xmm0
	movsd	%xmm0, (%esp)
	call	_abs
	movl	%eax, -12(%ebp)
	movl	-12(%ebp), %eax
	movl	%eax, 4(%esp)
	leal	LC1-"L00000000001$pb"(%ebx), %eax
	movl	%eax, (%esp)
	call	_printf
	addl	$36, %esp
	popl	%ebx
	leave
	ret
	.literal8
	.align 3
LC0:
	.long	858993459
	.long	1076155187
	.subsections_via_symbols

```

On 64 bit however it is a different picture. The 64 bit architecture seems to work differently from the 32-bit one as far as parameter passing is concerned. Apparently it seems to behave more like MIPS and ARM, in that parameters are not passed via the stack but directly in registers:

```
firas@aoba ~ % cc -S -o test64.s test.c     
firas@aoba ~ % cat test64.s 
	.cstring
LC1:
	.ascii "a is %d\12\0"
	.text
.globl _main
_main:
LFB3:
	pushq	%rbp
LCFI0:
	movq	%rsp, %rbp
LCFI1:
	subq	$16, %rsp
LCFI2:
	movsd	LC0(%rip), %xmm0
	movl	$1, %eax
	call	_abs
	movl	%eax, -4(%rbp)
	movl	-4(%rbp), %esi
	leaq	LC1(%rip), %rdi
	movl	$0, %eax
	call	_printf
	leave
	ret
LFE3:
	.literal8
	.align 3
LC0:
	.long	858993459
	.long	1076155187
	.section __TEXT,__eh_frame,coalesced,no_toc+strip_static_syms+live_support
EH_frame1:
	.set L$set$0,LECIE1-LSCIE1
	.long L$set$0
LSCIE1:
	.long	0x0
	.byte	0x1
	.ascii "zR\0"
	.byte	0x1
	.byte	0x78
	.byte	0x10
	.byte	0x1
	.byte	0x10
	.byte	0xc
	.byte	0x7
	.byte	0x8
	.byte	0x90
	.byte	0x1
	.align 3
LECIE1:
.globl _main.eh
_main.eh:
LSFDE1:
	.set L$set$1,LEFDE1-LASFDE1
	.long L$set$1
LASFDE1:
	.long	LASFDE1-EH_frame1
	.quad	LFB3-.
	.set L$set$2,LFE3-LFB3
	.quad L$set$2
	.byte	0x0
	.byte	0x4
	.set L$set$3,LCFI0-LFB3
	.long L$set$3
	.byte	0xe
	.byte	0x10
	.byte	0x86
	.byte	0x2
	.byte	0x4
	.set L$set$4,LCFI1-LCFI0
	.long L$set$4
	.byte	0xd
	.byte	0x6
	.align 3
LEFDE1:
	.subsections_via_symbols

```

So the program loads the double value in register xmm0, thinking that the callee expects its parameter in that register, and puts 1 in register eax (not sure why). Since the callee expects an int, it gets it from eax, and thus gets the value of 1, and proceeds as usual: abs(1) is 1.

---

### Post by shashanksingh on 2011-07-31
@Batchstelze (I don't know how to tag people in posts)

I didn't get the advanced stuff, but now the process is much more clear to me. One doubt: if I follow the same process in Linux and in Windows separately, will the .obj file just before the linking process be the same? Is the difference created at the linking stage among-st their executable's?

---

### Post by ziekfiguur on 2011-07-31
@Bachstelze: 64bit intel/amd processors have 8 extra general purpose registers compared to 32bit processors, since passing the values in registers means the memory doesn't need to be accessed as much this can make programs quite a lot more efficient. So, the calling convention for 64bit machines was adapted a bit. Also, the binary format is usually called machine language.

@shashanksingh: in your last version, you are still missing a return statement. If you pass the --static option to your linker it will use a static library (if a static version is available) so you can reduce dependencies a bit. 
Generally windows executables use a different format from linux, and their object files are different as well.

One last thing, in C/C++ people don't usually talk about queries but statements, not really important but it may help to know when you're googling something.

---

### Post by Bachstelze on 2011-07-31
> **ziekfiguur said:**
> 
@shashanksingh: in your last version, you are still missing a return statement.

return is optional in main() in C99. An omitted return implicitly means "return 0;".

---

### Post by nvteighen on 2011-07-31
> **Bachstelze said:**
> return is optional in main() in C99. An omitted return implicitly means "return 0;".

I didn't know that; it was surely "backported" from C++ (not sure whether "backport" is the proper term here...).

I guess I won't rely on that and keep returning 0 explicitly, but it's always good to learn something new :)

---

### Post by shashanksingh on 2011-08-03
```

int main()
{
	char str[]={'H','e','l','l','o','\n'};
	char *p=&str;
	int a=10;
	int *i=&a;
	printf("Value of a is %d",*i);

	while(*p!='\0')
	{
		printf("%c",*p);
		p++;
	}

	return 1;
}

```

Compilation:
```

In function ‘main’:
warning: initialization from incompatible pointer type

```

Output:
```

Value of a is 10Hello

```

Now I didn't get what exactly the warning means.
Is it saying I cant initialize pointer i as

char *i=&a;

also, my character array doesn't have a '\0', so theoretically, that should be an infinite loop.
But it doesn't happen to be so.
??

---

### Post by shashanksingh on 2011-08-03
Apart from the previous post, I was also curious about this thing.

Can't there be a situation where the compiler can get confused between the * for multiplication and * for Pointing??(pointers)


Couldn't they have used some other symbol?

---

### Post by nvteighen on 2011-08-03
> **shashanksingh said:**
> 

[...]

Now I didn't get what exactly the warning means.
Is it saying I cant initialize pointer i as

char *i=&a;


The error is on line 5: *char *p = &str;*. I'll try not to confuse you too much, but you have to think of strings/arrays as *convertible* to pointers; *str* is already a pointer (to the string's first element)... So, with &str you're taking the address of that "pointer"... i.e. you're attempting to create a pointer to a pointer (a double pointer, char **). If you wanted to point to *str*, you should do:

```

char *p = str;

```

But always keep in mind that despite being convertible the one to the other, arrays and pointers aren't the same. So, while the compiler knows that sizeof(str) is 7 bytes ("Hello\n\0"), sizeof(p) will be whatever size a word in your computer is (4 bytes in 32-bit; 8 bytes in 64-bit). (Please note that sizeof() is **not** a function, but a **compile-time operator**, i.e. it gets "called" when compiling). 

> 
also, my character array doesn't have a '\0', so theoretically, that should be an infinite loop.
But it doesn't happen to be so.
??

Ok, the array syntax is equivalent to the string syntax. '\0' is added anyways.

> **shashanksingh said:**
> Apart from the previous post, I was also curious about this thing.

Can't there be a situation where the compiler can get confused between the * for multiplication and * for Pointing??(pointers)

Couldn't they have used some other symbol?

It's hard to find one. The compiler will interpret * when used as a binary operator and as dereferencing when used as unary. That seems to be a mutually exclusive, so I don't see any ambiguity.

P.D: Next time, please open a new thread when you've got a new unrelated question; it helps people who later might search the forums.

---

### Post by GeneralZod on 2011-08-03
> **nvteighen said:**
> 
Ok, the array syntax is equivalent to the string syntax. '\0' is added anyways.


I get garbage printed out after "HELLO" (in fact, with a bit of jiggery-pokery, I can get it to print out the contents of a different, unrelated string after "HELLO"!), so I don't think this is the case: it seems the OP is triggering Udefined Behaviour, and just "got lucky" :)

---

### Post by Tony Flury on 2011-08-03
> **shashanksingh said:**
> ```

int main()
{
	char str[]={'H','e','l','l','o','\n'};
... code snipped ..

```

Output:
```

Value of a is 10Hello

```

also, my character array doesn't have a '\0', so theoretically, that should be an infinite loop.
But it doesn't happen to be so.
??
Here you are creating a 6 character array and placing those 6 characters in it - since you don't list a '\0' then you don't add one in. You got lucky that a '\0' character (i.e. something that could be interpreted as a '\0') existed in memory somewhere after your 'o' character that allowed your loop to terminate.

a safer way to initialise your character array is : 

```

char str[]= "Hello\n";

```

Since you are using a string literal here the '\0' is included and your string will be 7 characters long. 

P.S : I think my c code snippet is correct - C is not my first language.

---

### Post by Bachstelze on 2011-08-03
> **shashanksingh said:**
> 
Can't there be a situation where the compiler can get confused between the * for multiplication and * for Pointing??(pointers)

No, because multipilication takes exactly one *, so if you have something like a***b, the leftmost * will represent multiplication and all others will represent dereference, so it will be interpreted as a*(**b). If b is not a "double pointer", an error will be thrown because you cannot dereference something that is not a pointer, nor multiply pointers.

---

### Post by nvteighen on 2011-08-03
> **GeneralZod said:**
> I get garbage printed out after "HELLO" (in fact, with a bit of jiggery-pokery, I can get it to print out the contents of a different, unrelated string after "HELLO"!), so I don't think this is the case: it seems the OP is triggering Udefined Behaviour, and just "got lucky" :)

You're right, my mistake. That's what happens when one posts without using a compiler to test one's own claims; I should be more careful sometimes... :-|

---

