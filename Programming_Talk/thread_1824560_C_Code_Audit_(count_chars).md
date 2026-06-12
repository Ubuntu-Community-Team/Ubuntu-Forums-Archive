---
title: "C Code Audit (count chars)"
date: 2011-08-13
forum: Programming Talk
---

### Post by kevinharper on 2011-08-13
Here's the source:
```

/* Exercise 7, pg. 347
   By: Kevin Harper :: Date: Aug 13, 2011
   Write a program that uses redirection to accept
      input from a disk file, counts the # of times each
      letter occurs in the file, and displays the results
      on the screen.
   Hint: Use 26-member int array. To count characters,
      increment appropriate array element for each char read. */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define LTRS_IN_ALPH 26
#define MAX          41

/* function prototypes */
void clrstdin( char *s );
void inc_tally( int *ltr_array, char ltr );

int main( void )
{
   /* variable declarations */
   int index = 0;

   /* array declarations */
   char usr_string[MAX];
   int ltr_tally[LTRS_IN_ALPH];

   /* initialize both arrays */
   for( index = 0; index < MAX; index++ )
      usr_string[index] = ' ';

   for( index = 0; index < LTRS_IN_ALPH; index++ )
      ltr_tally[index] = 0;

   puts( "Enter string that is less than 40 characters long." );
   fgets( usr_string, MAX, stdin );

   clrstdin( usr_string );

   /* look at each character in usr_string */
   for( index = 0; index < strlen( usr_string ) - 1; index++ )
      /* omit spaces */
      if( usr_string[index] != ' ' && usr_string[index] != '.'
         && usr_string[index] != ',' )
         inc_tally( ltr_tally, usr_string[index] );

   /* display ltr_tally[] */
   for( index = 0; index < LTRS_IN_ALPH; index++ )
   {
      if( index % 5 == 0 && index != 0)
         printf( "\n" );

      printf( "%c: %d\t", index + 97, ltr_tally[index] );
   }

   printf( "\n" );

   return EXIT_SUCCESS;
}
/* clrstdin() clear any leftover chars tha may be in stdin stream */
void clrstdin( char *s )
{
   int ch = 0;

   if( s[ strlen( s ) - 1 ] != '\n' )
      while( ( ch = getchar() ) != '\n' && ch != EOF )
         ;
}

/* inc_tally() increases value of occurance for corresponding
      character */
void inc_tally( int *ltr_array, char ltr )
{
   int dec_val = ltr;

   ltr_array[dec_val - 97] += 1;
}

```

What would you guys do differently?

My questions:
How kosher is it to do what I did in function inc_tally - where I created an int var to store a char value? I'm sure it can be done, but did I do it right? It worked, just wondering if anyone cringed when they saw that.

I am also aware that instead of checking omitting spaces, periods, and commas, I should be omitting anything that isn't a letter (lower or uppercase). At some point I would like to do this program in a way that it looked at all chars in a file until EOF. I just got lazy... the program runs exactly as was asked (whether user types a string or if "./ex7 < input.txt" is ran on command line.

Is it necessary to initialize arrays the way that I have done? What about vars? I have a habit of initializing count/i/index/etc when declared (even when I use them in a for statement). Is this a bad habit? Just annoying/redundant?

What about the argument names? I see a lot of
```

int increase_size( int f, char *s );

```
Is this okay or should they be more descriptive?

---

### Post by Bachstelze on 2011-08-13
```
   /* variable declarations */
   int index = 0;

```

Not really needed. In C99 you can have

```
for (int i=0; i<n; i++)
```

In general it is good practice to have your variables as local as possible. Here the variable i does not exist outside the loop, so you don't have to "keep it" between loops where it is not needed.

```
   /* initialize both arrays */
   for( index = 0; index < MAX; index++ )
      usr_string[index] = ' ';

```

Use memset() if you want to fill a memory area with a constant byte value.

```
   for( index = 0; index < strlen( usr_string ) - 1; index++ )

```

Bad, the string length will be calculated at each iteration, which is a performance killer. Better:

```
int ls = strlen(usr_string);
for (int i=0; i<ls; i++)
```

Also works:

```
for (char *p = usr_string; *p != '\0'; p++)
```


> How kosher is it to do what I did in function inc_tally - where I created an int var to store a char value? I'm sure it can be done, but did I do it right? It worked, just wondering if anyone cringed when they saw that.

It's OK, but you don't really need an int. A char is an integer too, so you can do the arithmetic directly on the char value.


> Is it necessary to initialize arrays the way that I have done? What about vars? I have a habit of initializing count/i/index/etc when declared (even when I use them in a for statement). Is this a bad habit? Just annoying/redundant?

No one is going to frown at you for "initializing too much". It's better to initialize when it is not needed than the other way around.


> What about the argument names? I see a lot of
Code:

int increase_size( int f, char *s );

Is this okay or should they be more descriptive?

s for a string is ok (since it's a char* there's little ambiguity), but f is less obvious.

> I am also aware that instead of checking omitting spaces, periods, and commas, I should be omitting anything that isn't a letter (lower or uppercase). At some point I would like to do this program in a way that it looked at all chars in a file until EOF. I just got lazy...

Being lazy is a bad thing. Right now you don't do any checking on the input value, so if a malicious user enters a character other than a-z, you will get an out-of-bounds array access, essentially a buffer overflow.

---

### Post by kevinharper on 2011-08-14
I've been checking out quite a bit of C code in the past few days and noticed you did something that is very common... you used "i" in your for loop. I see a lot of i's and x's.

I use index or count depending on what I will do. Is it cleaner, "understood" to use i and x instead of a more descriptive word?

I will definitely look into memset().

Thanks for letting me know about the "performance killer". I rewrote this program like 3 times and every prior version had it like you suggested. I was having serious issues with the output and trimmed it down quite a bit (unfortunately this was one of those times where less code is bad). I am pretty sure I was passing the wrong array ptr and that's where my output issues were coming from.

As for initialization... I got into the habit of initializing EVERYTHING (including count/index) when declaring them because of a professor I had for my first CIS class. It program design (or something like that) in Pascal. And he was HUGE on this. Good to know that it's okay. I will get away from initializing count/index that will be used in for loops, though.

About "lazy being bad"... You are right. And I actually felt guilty and had to mention it. In fact, I wasn't checking for anything other than spaces when I first ran the program. Then I saved two sentences on the input file and the program simply crashed (returned to the command line w/out any output). That's when I added commas and periods.

I'll add a function that will also capture capital letters and another that will disregard anything that isn't a letter. I'll post the code sometime tomorrow.

Bachstelze, are you a software developer/engineer?

---

### Post by Bachstelze on 2011-08-14
> **kevinharper said:**
> I've been checking out quite a bit of C code in the past few days and noticed you did something that is very common... you used "i" in your for loop. I see a lot of i's and x's.

I use index or count depending on what I will do. Is it cleaner, "understood" to use i and x instead of a more descriptive word?

i is pretty much a universal convention. So much that when C99 introduced complex numbers, they defined the imaginary unit as I, not i. Using a longer name is, well, longer. ;)

> 
Bachstelze, are you a software developer/engineer?

Nope, just a student. But since I'm mostly interested in low-level stuff like embedded systems/OSs/security, I do a lot of C (you could pretty much say I *only* do C).

---

### Post by JupiterV2 on 2011-08-14
An interesting piece of information, as I have been scolded in these very forums over pre-mature optimization.

Take the following code:

```
#include <stdio.h>
#include <string.h>

int main (int argc, char *argv[])
{
    for (int i = 0; i < strlen (argv[0]); i++) {
        printf ("%c", argv[0][i]);
    }
    printf ("\n");

    return 1;
}
```

It produces the following 687 byte assembly output on my machine (x86):
```
	.file	"asm.c"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	pushl	%ebx
	subl	$44, %esp
	movl	$0, 28(%esp)
	jmp	.L2
.L3:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	28(%esp), %eax
	leal	(%edx,%eax), %eax
	movzbl	(%eax), %eax
	movsbl	%al,%eax
	movl	%eax, (%esp)
	call	putchar
	addl	$1, 28(%esp)
.L2:
	movl	28(%esp), %ebx
	movl	12(%ebp), %eax
	movl	(%eax), %eax
	movl	%eax, (%esp)
	call	strlen
	cmpl	%eax, %ebx
	jb	.L3
	movl	$10, (%esp)
	call	putchar
	movl	$1, %eax
	addl	$44, %esp
	popl	%ebx
	movl	%ebp, %esp
	popl	%ebp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5"
	.section	.note.GNU-stack,"",@progbits
```

Bachstelze improved version (my code, his fix)...
```
#include <stdio.h>
#include <string.h>

int main (int argc, char *argv[])
{
    int len = strlen (argv[0]);
    for (int i = 0; i < len; i++) {
        printf ("%c", argv[0][i]);
    }
    printf ("\n");

    return 1;
}
```
...correctly optimizes the code slightly, giving a 652 byte assembly file:
```
	.file	"asm.c"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	subl	$32, %esp
	movl	12(%ebp), %eax
	movl	(%eax), %eax
	movl	%eax, (%esp)
	call	strlen
	movl	%eax, 28(%esp)
	movl	$0, 24(%esp)
	jmp	.L2
.L3:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	24(%esp), %eax
	leal	(%edx,%eax), %eax
	movzbl	(%eax), %eax
	movsbl	%al,%eax
	movl	%eax, (%esp)
	call	putchar
	addl	$1, 24(%esp)
.L2:
	movl	24(%esp), %eax
	cmpl	28(%esp), %eax
	jl	.L3
	movl	$10, (%esp)
	call	putchar
	movl	$1, %eax
	leave
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5"
	.section	.note.GNU-stack,"",@progbits
```

However, the most efficient method turns out to be:
```
#include <stdio.h>

int main (int argc, char *argv[])
{
    for (int i = 0; i < sizeof (argv[0]) / sizeof (char); i++) {
        printf ("%c", argv[0][i]);
    }
    printf ("\n");

    return 1;
}
```

Assembly (555 bytes): 
```
	.file	"asm3.c"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	subl	$32, %esp
	movl	$0, 28(%esp)
	jmp	.L2
.L3:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	28(%esp), %eax
	leal	(%edx,%eax), %eax
	movzbl	(%eax), %eax
	movsbl	%al,%eax
	movl	%eax, (%esp)
	call	putchar
	addl	$1, 28(%esp)
.L2:
	movl	28(%esp), %eax
	cmpl	$3, %eax
	jbe	.L3
	movl	$10, (%esp)
	call	putchar
	movl	$1, %eax
	leave
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5"
	.section	.note.GNU-stack,"",@progbits
```

This flies in the face of the suggested fix when compared to the following:
```
#include <stdio.h>

int main (int argc, char *argv[])
{
    int len = sizeof (argv[0]) / sizeof (char);
    
    for (int i = 0; i < len; i++) {
        printf ("%c", argv[0][i]);
    }
    printf ("\n");

    return 1;
}
```

...which results in a 579 bytes of assembly:
```
	.file	"asm4.c"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	subl	$32, %esp
	movl	$4, 28(%esp)
	movl	$0, 24(%esp)
	jmp	.L2
.L3:
	movl	12(%ebp), %eax
	movl	(%eax), %edx
	movl	24(%esp), %eax
	leal	(%edx,%eax), %eax
	movzbl	(%eax), %eax
	movsbl	%al,%eax
	movl	%eax, (%esp)
	call	putchar
	addl	$1, 24(%esp)
.L2:
	movl	24(%esp), %eax
	cmpl	28(%esp), %eax
	jl	.L3
	movl	$10, (%esp)
	call	putchar
	movl	$1, %eax
	leave
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5"
	.section	.note.GNU-stack,"",@progbits
```

Why? In the case that Bachstelze gives, the compiler can't optimize the strlen() function properly and, as he says, calls strlen() each time the loop iterates. However, in the second instance the compiler is smart enough to realize that the result is the same in each instance of the loop and produces more efficient code than the optimized version.

The lesson? Careful prematurely optimizing. In the end, your loop could be so inconsequential that the few extra lines of assembly have no bearing on the entirety of your program and sometimes, like in the second case, trying to be "clever" actually results in poorer performance.

---

### Post by Bachstelze on 2011-08-14
You are using sizeof(string). Bad. Here it works because argv[0] is a constant, but look at this:

```
firas@wakaba ~ % cat test.c                                         
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
    char buf[256];
    fputs("Enter a string: ", stdout);
    fgets(buf, 256, stdin);
    fputs("Entered string is: ", stdout);
    for (int i=0; i < sizeof(buf) / sizeof(char); i++) {
        putchar(buf[i]);
    }
    putchar('\n');
    return EXIT_SUCCESS;
}
firas@wakaba ~ % gcc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@wakaba ~ % ./test                                             
Enter a string: supercalifragilisticexpialidocious
Entered string is: supercalifragilisticexpialidocious
&#65533;3&#65533;n&#65533;&#65533;y&#65533;n@&#65533;u&#65533;&#65533;X&#65533;u&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;np@#@h&#65533;u&#65533;&#65533;&#65533;@h[ &#65533;np@&#65533;@

```

sizeof(buf) is 256, so it will print 256 characters, regardless of the length of the string. sizeof is not a synonym for strlen! Even in your case, sizeof(argv[0]) will be strlen(argv[0])+1 because of the null byte, so you will have an unwanted null byte in the output.

And if the buffer is allocated with malloc it's even worse, sizeof(buf) will always be sizeof(char*)!

Also the size of the assembly is hardly a good indication of how efficient the code is (unless your primary concern is space, which is not the case on a standard computer).

---

### Post by JupiterV2 on 2011-08-14
> **Bachstelze said:**
> ...

sizeof(buf) is 256, so it will print 256 characters, regardless of the length of the string. sizeof is not a synonym for strlen! Even in your case, sizeof(argv[0]) will be strlen(argv[0])+1 because of the null byte, so you will have an unwanted null byte in the output.

And if the buffer is allocated with malloc it's even worse, sizeof(buf) will always be sizeof(char*)!

Also the size of the assembly is hardly a good indication of how efficient the code is (unless your primary concern is space, which is not the case on a standard computer).

Actually, argv[0] is a pointer too so it evaluates to 4. That's what you get for writing code late at night and not testing it first before you post it. 

Irregardless of the poor code, the point remains the same. You must be careful of what you're optimizing and in this case the assembly tells the tail. If the compiler optimizes the for loop so that the function called becomes a constant you'll not only avoid the speed loss but also the gain size improvement. If, however, this code is only called once in the lifetime of the program or is never called on anything large enough to cause a performance issue then the optimization in either case was pointless. Better to write your code first and look at optimization of bottle-necks in the code using a profiler. Space, incidently, would be a concern if you were working on an embedded system.

---

### Post by Bachstelze on 2011-08-14
> **JupiterV2 said:**
> 
Irregardless of the poor code, the point remains the same. You must be careful of what you're optimizing and in this case the assembly tells the tail. If the compiler optimizes the for loop so that the function called becomes a constant you'll not only avoid the speed loss but also the gain size improvement. If, however, this code is only called once in the lifetime of the program or is never called on anything large enough to cause a performance issue then the optimization in either case was pointless. Better to write your code first and look at optimization of bottle-necks in the code using a profiler. Space, incidently, would be a concern if you were working on an embedded system.

I know all that, thank you very much. And the fact of the matter is that if you do

```
for (int i=0; i<strlen(s); i++)
```

The compiler may not always be able to fgure out whether or not the length of the string will change, and if in doubt, will not optimize the value of strlen(s) as a constant. So if you, the programmer, know for sure that it will never change, why take chances? Just optimize it yourself. The compiler can't see everything, sometimes you need to give it some hints.

So what, actually, was your point with this wall of text? That one should do absolutely zero optimization like the one above, and only do it after runnng the program in a profiler and whatnot? If it was, I call ******** on it. Such non-invasive, obvious optimizations should always be done directly when writing the code, there is no excuse apart from newbieness for not doing it.

And I know a lot about embedded systems as well. Actually, I made an AES encryption box in pure assembly out of an Elan SC520 microcontroller just last week. How is that relevant? You don't honestly believe kevinharper is programming on an embedded system, do you? Besides even if he were, the CPU cycles eaten by the repeated calls to strlen far outweigh the minimal size gain.

---

### Post by kevinharper on 2011-08-14
I appreciate all of your guys' feedback.

@JupiterV2 I post my code here precisely because I know it's bad. I want to improve it. I am open to suggestions and think this is one of the easiest ways to go about it.

And no, Bachstelze... I'm not on an embedded system.

I've just now learned what "premature optimization" is...

Question: On a larger scale, is it better to have optimized performance or very clean code?
(Assuming that: "Premature optimization" is a phrase used to describe a situation where a programmer lets performance considerations affect the design of a piece of code. This can result in a design that is not as clean as it could have been or code that is incorrect, because the code is complicated by the optimization and the programmer is distracted by optimizing.")

---

### Post by Arndt on 2011-08-14
Some additional comments:

You define MAX instead of using the number 41 literally, which is good, but you still have the number 40 in the prompt to the user. You should use MAX there too.

You have the number 97 in several places; this is better expressed with 'a'.

You have the expression usr_string[index] four times in three lines. The compiler will optimize so the access is only done once, but to make it easier to read, you can introduce a temporary variable.

It may be a good idea to give the constant 5 a name too - it may be valuable later to see easily that this is a value that can be changed, otherwise it will get lost in the code, so to speak.

LTRS_IN_ALPH can be computed: it's 'z'-'a'+1.

What happens to upper case letters?

---

### Post by Arndt on 2011-08-14
> **kevinharper said:**
> Ubuntu: Because rebooting is ONLY for installing hardware 

Or for updating the kernel.

---

### Post by kevinharper on 2011-08-14
> **Arndt said:**
> 
You define MAX instead of using the number 41 literally, which is good, but you still have the number 40 in the prompt to the user. You should use MAX there too.

so my prompt to the user should really be a printf and I should have %d instead of 40 and then use MAX - 1?

> 
You have the number 97 in several places; this is better expressed with 'a'.

Are you saying that in the following instances:
```

printf( "%c: %d\t", index + 97, ltr_tally[index] );

```
and
```

ltr_array[dec_val - 97] += 1;

```
I can simply replace 97 w/ an a and the arithmetic will be done automatically? Is this what Bachstelze meant when he said "It's OK, but you don't really need an int. A char is an integer too, so you can do the arithmetic directly on the char value"?
> 
You have the expression usr_string[index] four times in three lines. The compiler will optimize so the access is only done once, but to make it easier to read, you can introduce a temporary variable.

Good call. Something like the following then?
```

usr_string_length = strlen(usr_string);

for( index = 0; index < usr_string_length - 1; index++ )
{
   usr_string_val = usr_string[index];

      /* omit spaces */
      if( usr_string_val != ' ' && usr_string_val != '.'
         && usr_string_val != ',' )
         inc_tally( ltr_tally, usr_string[index] );
}

```
> 
It may be a good idea to give the constant 5 a name too - it may be valuable later to see easily that this is a value that can be changed, otherwise it will get lost in the code, so to speak.

Sounds good... it's the # of columns for the display... Maybe:
```

#define COLS 5

```
And just use COLS instead of 5. I like that.

> 
LTRS_IN_ALPH can be computed: it's 'z'-'a'+1.

Very cool. I guess this sort of makes me realize that one of my previous questions about character arithmetic will be "YES". But will wait for you to confirm.

> 
What happens to upper case letters?

At this point, WHO KNOWS. XD... I will clean this up quite a bit actually before I continue on w/ C. I have gotten lots of ideas from your guys' suggestions.

> 
Or for updating the kernel.

Too much of a noob to be messing around w/ my kernel.

---

### Post by Bachstelze on 2011-08-15
> **kevinharper said:**
> 
Question: On a larger scale, is it better to have optimized performance or very clean code?
(Assuming that: "Premature optimization" is a phrase used to describe a situation where a programmer lets performance considerations affect the design of a piece of code. This can result in a design that is not as clean as it could have been or code that is incorrect, because the code is complicated by the optimization and the programmer is distracted by optimizing.")

Your assumption on what "premature optimization" means is correct, but sometimes as JupiterV2 demonstrated it's not only a matter of design but of correctness: the programmer does optimizations that he thinks are equivalent to the original code but actually aren't, and the program will not work correctly anymore.

As for your question, there is no clear-cut answer in general, but we can safely say that the strlen optimization in question is no less clean than the unoptimized version and therefore should always be done.

> **kevinharper said:**
> 
Are you saying that in the following instances:
```

printf( "%c: %d\t", index + 97, ltr_tally[index] );

```
and
```

ltr_array[dec_val - 97] += 1;

```
I can simply replace 97 w/ an a and the arithmetic will be done automatically? Is this what Bachstelze meant when he said "It's OK, but you don't really need an int. A char is an integer too, so you can do the arithmetic directly on the char value"?

No, you replace 97 with 'a' (single quotes). As I said, a character is an integer, so a character constant is an integer constant whose value is the ASCII code of the character in question.

> Good call. Something like the following then?
```

usr_string_length = strlen(usr_string);

for( index = 0; index < usr_string_length - 1; index++ )
{
   usr_string_val = usr_string[index];

      /* omit spaces */
      if( usr_string_val != ' ' && usr_string_val != '.'
         && usr_string_val != ',' )
         inc_tally( ltr_tally, usr_string[index] );
}

```

I don't think this one is necessary. You add a new variable without any real benefit (unlike the strlen case when the benefit is better performance).

> Very cool. I guess this sort of makes me realize that one of my previous questions about character arithmetic will be "YES". But will wait for you to confirm.

I wouldn't do that either. Too convoluted for my liking, and once again no real benefit. It's not like the number of letters in the alphabet will change any time soon.

---

### Post by Arndt on 2011-08-15
> **Bachstelze said:**
> 

I wouldn't do that either. Too convoluted for my liking, and once again no real benefit. It's not like the number of letters in the alphabet will change any time soon.

In my language, the alphabet has 29 letters. Now, admittedly, the number 26 is so well-known that it almost documents itself. Still, if you want to collect letters of both cases, the number will be 52, which is not as obvious to the eye. But a comment will do fine, as well.

---

### Post by kevinharper on 2011-08-15
Here is the revised code:
```

/* Exercise 7, pg. 347
   By: Kevin Harper :: Date: Aug 13, 2011
   Write a program that uses redirection to accept
      input from a disk file, counts the # of times each
      letter occurs in the file, and displays the results
      on the screen.
   Hint: Use 26-member int array. To count characters,
      increment appropriate array element for each char read. */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define LTRS_IN_ALPH 26
#define MAX          41
#define COLS         5

/* function prototypes */
void clrstdin( char *s );
void inc_tally( int *ltr_array, char ltr );

int main( void )
{
   /* variable declarations */
   int i,
       usr_string_length = 0;

   /* array declarations */
   char usr_string[MAX];
   int ltr_tally[LTRS_IN_ALPH];

   /* initialize both arrays */
   for( i = 0; i < MAX; i++ )
      usr_string[i] = ' ';

   for( i = 0; i < LTRS_IN_ALPH; i++ )
      ltr_tally[i] = 0;

   puts( "Enter string that is less than 40 characters long." );
   fgets( usr_string, MAX, stdin );

   clrstdin( usr_string );

   usr_string_length = strlen( usr_string );

   /* look at each character in usr_string */
   for( i = 0; i < usr_string_length - 1; i++ )
      /* omit spaces */
      if( ( usr_string[i] >= 'a' && usr_string[i] <= 'z' ) ||
          ( usr_string[i] >= 'A' && usr_string[i] <= 'Z' ) )
         inc_tally( ltr_tally, usr_string[i] );

   /* display ltr_tally[] */
   for( i = 0; i < LTRS_IN_ALPH; i++ )
   {
      if( i % COLS == 0 && i != 0)
         printf( "\n" );

      printf( "%c: %d\t", i + 'a', ltr_tally[i] );
   }

   printf( "\n" );

   return EXIT_SUCCESS;
}
/* clrstdin() clear any leftover chars tha may be in stdin stream */
void clrstdin( char *s )
{
   int ch = 0;

   if( s[ strlen( s ) - 1 ] != '\n' )
      while( ( ch = getchar() ) != '\n' && ch != EOF )
         ;
}

/* inc_tally() increases value of occurance for corresponding
      character */
void inc_tally( int *ltr_array, char ltr )
{
   int dec_val = ltr;

   if( ltr >= 'A' && ltr <= 'Z' )
      dec_val += 32;

   ltr_array[dec_val - 'a'] += 1;
}

```

Hope I've made someone proud. The changes were VERY easy to make, thanks for the simple explanations, guys.

Here is a list of changes:
changed index to i
didn't initialize i when declared
defined COLS constant to 5 (number of output columns)
added usr_string_length variable and used it in for loop
am now looking for 'a' - 'z' && 'A' - 'Z' in usr_string
inc_tally() adds 32 to 'A' - 'Z' to make lowercase

---

### Post by Bachstelze on 2011-08-15
```
   int i,
       usr_string_length = 0;
```

If you're going to initialize everything, I would also intialize i for consistency. Though I insist that declaring i in the loop is cleaner to me (last time I mention it, promise).

```
   for( i = 0; i < usr_string_length - 1; i++ )
```

The -1 is to omit the newline, I presume, but what if the string does not end with a newline?

---

### Post by kevinharper on 2011-08-15
I think I'm about to get slapped... but I thought you meant that I could INITIALIZE in the for loop. I wasn't aware (thanks to that awesomeness of a book I was reading) that the first arg in a for loop was also used as a declaration. Your suggestion makes it so much cleaner and eliminates my "whether to initialize or not" problem.

> 
but what if the string does not end with a newline?

I thought fgets() only retrieves a string AFTER a newline has been hard-entered by the user - which is how I have been testing this code.

I guess what you are eluding to is that I should go ahead and get that last char and test for it. Then do what I please w/ some conditional test. Right? Yeah.. pretty sure you'll say "yes."

Seriously... :P Address for me to send tuition. Your comments/suggestions are pure gold.

---

### Post by Bachstelze on 2011-08-15
> **kevinharper said:**
> 
I thought fgets() only retrieves a string AFTER a newline has been hard-entered by the user - which is how I have been testing this code.

That is true if the user does as you instruct and enters less than 40 characters. However, what if the user inadvertently enters 40 characters or more? If the user does not realise he has entered one (or more) too many characters, he will expect the program to count all the characters in the string, which the program will not do. At the very least, I would make the program print a warning if too many characters were entered (which is the case if and only if the last character of the string is not a newline).

> Seriously... :P Address for me to send tuition. Your comments/suggestions are pure gold.

Address donations to the [Children's Tumor Foundation](http://www.ctf.org/). ;)

---

### Post by kevinharper on 2011-08-15
I promise I logged on to let you know I realized that this was the case if 40+ chars were entered! It takes me a while but eventually it comes to me. :(

I like the idea of the warning. Will make that happen. It'll say something like "You've exceeded the maximum allowed characters. Everything beyond 40 chars will be removed. Type Y if this is okay or N of it is not. Put all of that in a while loop and I have myself a nice little control feature.

Question... If I wanted to get ALL lines from a file (beyond the first newline - which is what I think I have right now)... Would I simply get from string[0] to string[i] = '\n' and append (output) each new row (line) grabbed?

Something like:
```

while( fgets( name, MAX, stdin ) != EOF )

```
Wait... fgets return ptr of type char, in this case, right? So instead of EOF (which I believe, from previous conversations, is an int), I should use NULL?

PS: Already involved w/ helping kids w/ cancer (published research - leukemia related). Check me out on PubMed: [http://www.ncbi.nlm.nih.gov/pubmed/21565177](http://www.ncbi.nlm.nih.gov/pubmed/21565177)

So uhm... Yeahhh... If you ever decide to take up molecular biology or biochemistry ;) let me know.

---

### Post by Bachstelze on 2011-08-15
> **kevinharper said:**
> 
Question... If I wanted to get ALL lines from a file (beyond the first newline - which is what I think I have right now)... Would I simply get from string[0] to string[i] = '\n' and append (output) each new row (line) grabbed?

Something like:
```

while( fgets( name, MAX, stdin ) != EOF )

```
Wait... fgets return ptr of type char, in this case, right? So instead of EOF (which I believe, from previous conversations, is an int), I should use NULL?


Yes, with a catch. fgets returns NULL in two cases: if EOF occurred before any data could be read or if there was an error. From man fgets:

> The fgets() and gets() functions do not distinguish between end-of-file and error; callers must use feof(3) and ferror(3) to determine which occurred.

Otherwise your idea if good: get a line, process it, get the next one, and so on until there are no lines to be read. However if you read from a file it is even more important than you check for long lines. Ideally, you would be able to process lines of any length, but you would need malloc/realloc to do that simply, so you must wait until you know about those.

---

### Post by kevinharper on 2011-08-15
Yeah.. the book talked about malloc() for a couple of paragraphs and mostly raised more doubts than answers. I know it's very useful, just not sure how to make and "unlimited" size allocation with it. But I won't worry about that for now.

Okay... The next problem has to do with reading a file w/ multiple lines. It asks to modify what I previously posted into being able to read other source files and printing the code w/ #s at the beginning of each new row.

I will assume that no code wraps so that should be a max width of chars of 255. Won't bother putting that code up. I have a very good idea of what to do from what's happened on this thread.

Thanks. Will now mark it as "solved".

---

### Post by kevinharper on 2011-08-16
Yeah... I promised I wasn't going to post anything but I did it so quickly and it was without problems (except that I used a '{' instead of a '(' for a function call). :)

Here's the code for a program that reads another file (.c source file) and prints out the code w/ line numbers).

```

/* Exercise 14.9, pg. 347
   By: Kevin Harper :: Date: Aug 15, 2011
   Write a program that prints C source files.
   Get source through redirection & use fprintf() to print.
   Print line number at beginning of each line. */

/* HINT: Get a line at a time, print formatted line number,
            followed by tab and string. */

#include <stdio.h>
#include <stdlib.h>

#define CHARS_IN_ROW 256 /* 255 chars + 1 for newline */

/* function prototypes */
void print_num_row( void );

int main( void )
{
   /* array declarations */
   char buffer[CHARS_IN_ROW];

   while( fgets( buffer, CHARS_IN_ROW, stdin ) != NULL )
   {
      print_num_row();
      fprintf( stdout, "%s", buffer );
   }

   return EXIT_SUCCESS;
}

/* print_num_row() prints the corresponding row/line
      number and a tab */
void print_num_row( void )
{
   static int row_num = 1;

   printf( "%d:\t", row_num );

   row_num++;
}

```

Question: I feel like all functions should return something. Is this not right? I feel cheap just calling a function to print. I feel like I should get an int value from print_num_row() and have main() print it. Thoughts?

---

### Post by Bachstelze on 2011-08-16
```
#define CHARS_IN_ROW 256 /* 255 chars + 1 for newline */
```

254 characters + 1 for newline + 1 for the terminating null. ;)

> Question: I feel like all functions should return something. Is this not right?

This is right in mathematics (and in pure functional programming), but not in C. In C you can have functions that return void (aka nothing), and it's perfectly OK. I think it's a bit pointless to make a separate function for that, though, I would just do

```
int main( void )
{
   /* line counter */
   int n = 1;
   /* array declarations */
   char buffer[CHARS_IN_ROW];

   while( fgets( buffer, CHARS_IN_ROW, stdin ) != NULL )
   {
      printf( "%d\t%s", n++, buffer );
   }

   return EXIT_SUCCESS;
}
```

Also it's redundant to fprintf to stdout, just use printf.

---

### Post by kevinharper on 2011-08-16
> 
In C you can have functions that return void (aka nothing), and it's perfectly OK

Right.. I knew I had heard somewhere not to do that, but it wasn't related to C. Thanks for clearing that up. And yes, I would have preferred to have done it in main() but the problem asked for it... as it did for fprintf() specifically. I think it's getting ready to introduce accessing files and what not.

Very cool.. Thanks.

---

### Post by Bachstelze on 2011-08-16
Actually never mind what I said earlier. In this case you can make it handle long lines without malloc/realloc, since if you have a long line you can just process each part of it separately (you would need malloc if you needed to have the whole line stored in memory):

```
int main( void )
{
   /* line counter */
   int n = 1;
   /* array declarations */
   char buffer[CHARS_IN_ROW];

   fputs("1\t", stdout);
   while( fgets( buffer, CHARS_IN_ROW, stdin ) != NULL )
   {
      fputs( buffer, stdout );

      /* newline */
      if (buffer[strlen(buffer)-1] == '\n') {
           printf("%d\t", ++n);
      }
   }

   return EXIT_SUCCESS;
}
```

---

