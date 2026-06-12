---
title: "C - Program a simple calculator?"
date: 2011-08-18
forum: Programming Talk
---

### Post by jjpcexpert on 2011-08-18
Like it will let you:

(stdout)
Calc: you type 7.5+7.7
 = 15.2
Calc: so on

I have had no success in creating a C program that will:
GCC to ./a.out or specced location
Calculate a user-entered expression
Loop back to start
be Simple (KISS comes to mind)
And it must only use stdio.h and built in C stuff.

So far I have as mysecond.c:
```
#include <stdio.h>

main (){
char calc[5565565] = "default message goes here";
printf("Calculation [0-9, +(add) -(subtract) *(multiply) /(divide)]: ");
scanf("%s",&calc);
double result;
result=printf(calc);
printf("\nYour result was: %lf",result);
main();
}
```Output:
815+815
goes in

815+815
Segmentation fault
goes out

---

### Post by Bachstelze on 2011-08-18
There so many things with this program that are wrong that I don't know where to begin...

But for the segfault, what's the type of &calc, and what does scanf expect?

---

### Post by jjpcexpert on 2011-08-18
> **Bachstelze said:**
> There so many things with this program that are wrong that I don't know where to begin...

But for the segfault, what's the type of &calc, and what does scanf expect?
scanf doesn't care IMHO.
&calc is char.
Please show me how to parse &calc into the user entered expression, then how to assign that as a variable (&result which is l-float)

---

### Post by Arndt on 2011-08-18
> **jjpcexpert said:**
> scanf doesn't care IMHO.
&calc is char.
Please show me how to parse &calc into the user entered expression, then how to assign that as a variable (&result which is l-float)

Why do you have this big number in char calc[5565565]?

But regardless of that, the C runtime system doesn't evaluate arithmetic expressions. You have to write code that takes the string "815 + 816" apart, puts 815 in one variable, 816 in another and then perfoms an addition. And likewise for other operators.

---

### Post by jjpcexpert on 2011-08-18
> **Arndt said:**
> Why do you have this big number in char calc[5565565]?

But regardless of that, the C runtime system doesn't evaluate arithmetic expressions. You have to write code that takes the string "815 + 816" apart, puts 815 in one variable, 816 in another and then perfoms an addition. And likewise for other operators.
For extremely long calculations: a fool proofing mech.

Also, it needs to be in pure C, not C++ or Mono C#.

I need to go read the bc source code.

---

### Post by Arndt on 2011-08-18
> **jjpcexpert said:**
> For extremely long calculations: a fool proofing mech.



It's quite a large array. Do you know that you have such a large stack?
> 
Also, it needs to be in pure C, not C++ or Mono C#.


Your subject line already says so.

---

### Post by jjpcexpert on 2011-08-18
> **Arndt said:**
> It's quite a large array. Do you know that you have such a large stack?

Your subject line already says so.
The updated code, plus a.out for a Pentium 4 (or i686?), are available: [ATTACH]200297[/ATTACH].

The array is now only 65536 characters long (64kbytes). Unfortunately, it will not compile on a Commodore 64 :(.

---

### Post by Bachstelze on 2011-08-18
> **jjpcexpert said:**
> scanf doesn't care IMHO.

Yes, it does.

> &calc is char.

No, it is not.

---

### Post by CoreyB. on 2011-08-18
I don't think you are supposed to recursively call main() either.

---

### Post by cgroza on 2011-08-18
Also, with an array of that size, I think your stack will overflow pretty quickly if you call main recursively.

---

### Post by jjpcexpert on 2011-08-19
> **cgroza said:**
> Also, with an array of that size, I think your stack will overflow pretty quickly if you call main recursively.

Oh.

Do I create (main) to operate the first call, then call (real) recursively?

Also, the latest code causes an overflow, an integer negative result, and the wrong result.
```
#include <stdio.h>

int main (){
int calc[1000] = "Checking";
printf("Calculation [0-9, +(add) -(subtract) *(multiply) /(divide)]: ");
scanf("%s",&calc);
double result;
result=&calc;
printf("\nYour result was: %lf",result);
printf("\n");
}
```

---

### Post by lisati on 2011-08-19
"main" has a special meaning: to cut a long story short (omitting a few "behind the scenes" details), it's what gets run when the OS loads your program and starts it. It's not usually meant to be called recursively.

---

### Post by dwhitney67 on 2011-08-19
@ the OP -
> 
*** WARNING - this poster is a(n) 11 year old - please take appropriate adult advice before following any of his advice. Thank you ***


My advice is to peruse through a C Programming Tutorial (eg. [http://www2.its.strath.ac.uk/courses/c/](http://www2.its.strath.ac.uk/courses/c/)) before you take this thread any further.

Your perceptions of what printf(), and perhaps what the C language is capable of doing is not what you think.  Study the example programs in the tutorial, try modifying them as your curiosity develops, and then should you have other questions, feel free to post them on this forum.

---

### Post by NovaAesa on 2011-08-19
I agree with dwhitney67, the task the OP is attempting is not even close to being trivial or easy. I wouldn't advise attempting parsing then executing expressions until you have a large amount of programming experience under your belt.

---

### Post by Arndt on 2011-08-19
> **jjpcexpert said:**
> Oh.

Do I create (main) to operate the first call, then call (real) recursively?

Also, the latest code causes an overflow, an integer negative result, and the wrong result.
```
#include <stdio.h>

int main (){
int calc[1000] = "Checking";
printf("Calculation [0-9, +(add) -(subtract) *(multiply) /(divide)]: ");
scanf("%s",&calc);
double result;
result=&calc;
printf("\nYour result was: %lf",result);
printf("\n");
}
```

You've already been told that there is no expression evaluation done in your code whatsoever, so of course your calculator doesn't work as intended. You have to program the evaluation. Why do you think that 'printf' will evaluate things for you? It prints, that is its only task.

As for your recursive calls, the natural construct in C here is the 'while' loop.

I don't think a very small calculator is beyond a beginner. General parsing of expressions can be a bit much, though.

---

### Post by ve4cib on 2011-08-19
This suggestion has nothing to do with the code itself (which has been covered fairly well already)....

Instead of attempting to create a standard, in-fix calculator (where the operator comes between the numbers being operated on, e.g. 1 + 2) the OP may find it easier to create a re-fix or post-fix calculator.  This is especially true if you want to allow more complex operations, like evaluating "1 + 2 * 3 / 4".  Dealing with orders of operations in an in-fix calculator is a nuisance.

But with a post-fix calculator (where the operation comes *after* the operands -- commonly used in RPN [Reverse Polish Notation) calculators) the order of operations is irrelevant; you evaluate operations in the order they appear in the equation.  Thus "1 + 2 * 3 / 4" becomes "1 2 3 * 4 / +"

Rather than worrying about doing a lot of (potentially complicated) text parsing, you simply read in numbers and push them onto a stack.  When you read in an operation you pop the last two number off the stack and do the operation on them, pushing the result back on.

Just a random thought.  I'm also a big fan of RPN calculators and think everyone should use them, so I may have a slight bias there.

---

### Post by PaulM1985 on 2011-08-19
Why not think about making your program a little simpler, then you can learn the ideas without having to do any parsing of expressions?

Your program could have a flow like this:  (I have put "C" next to things the computer would print and "U" next to things the user would type)

C: Welcome to your calculator.
C: Please enter the first number for the calculation.
U: 25
C: Please enter the operator (+, -, /, *)
U: -
C: Please enter the second number for the calculation.
U: 13
C: Result is 12.

So you read in the information at each step, then evaluate the expression at the end.  You don't need to parse the expression because you force the user into a fixed expression format.

After managing to do this, you might like to make the improvements to move onto things like expression parsing.

You are probably better to make small steps instead of big leaps.

Good luck.

Paul

---

### Post by jjpcexpert on 2011-08-19
You are NOT following my intention. Keep it simple for the Average Joe (788, press PLUS, 788 press ENTER/EQUALS (use brackets if wanted), good answer!), stupid!

---

### Post by jjpcexpert on 2011-08-19
> **ve4cib said:**
> This suggestion has nothing to do with the code itself (which has been covered fairly well already)....

Instead of attempting to create a standard, in-fix calculator (where the operator comes between the numbers being operated on, e.g. 1 + 2) the OP may find it easier to create a re-fix or post-fix calculator.  This is especially true if you want to allow more complex operations, like evaluating "1 + 2 * 3 / 4".  Dealing with orders of operations in an in-fix calculator is a nuisance.

But with a post-fix calculator (where the operation comes *after* the operands -- commonly used in RPN [correction:](Reverse Polish Notation) calculators) the order of operations is irrelevant; you evaluate operations in the order they appear in the equation.  Thus "1 + 2 * 3 / 4" becomes "1 2 3 * 4 / +"

Rather than worrying about doing a lot of (potentially complicated) text parsing, you simply read in numbers and push them onto a stack.  When you read in an operation you pop the last two number off the stack and do the operation on them, pushing the result back on.

Just a random thought.  I'm also a big fan of RPN calculators and think everyone should use them, so I may have a slight bias there.

VERY good idea. Now please tell me how to implement in pure C. Do not provide full source, juts provide an idea of what I need to use. I do not have math.h, as I use Debian.
The bounty is the executable with modified source code to explain how to use reverse Polish notation.

---

### Post by jjpcexpert on 2011-08-19
> **Arndt said:**
> You've already been told that there is no expression evaluation done in your code whatsoever, so of course your calculator doesn't work as intended. You have to program the evaluation. Why do you think that 'printf' will evaluate things for you? It prints, that is its only task.I don't. I think it will print, formatted. Like bash printf (if such thing exists)> 
As for your recursive calls, the natural construct in C here is the 'while' loop.

I don't think a very small calculator is beyond a beginner. General parsing of expressions can be a bit much, though.Lemme try a postfix one. Source code available now.

I used the 'Keritchie' (K&R) code, and added some helpful text.

---

### Post by Arndt on 2011-08-19
> **jjpcexpert said:**
> I don't. I think it will print, formatted. Like bash printf (if such thing exists)


If not in printf, where in your code do you expect the evaluation to happen? In scanf?

Why do you say "if such thing exists"?

---

### Post by PaulM1985 on 2011-08-19
> **jjpcexpert said:**
> You are NOT following my intention. Keep it simple for the Average Joe (788, press PLUS, 788 press ENTER/EQUALS (use brackets if wanted), good answer!), stupid!

I'm sorry.  Did you just call me stupid?

If you don't know too much about programming and don't know how to parse expressions you are likely to get stuck, regularly.  I was simply trying to get you on the right path to learning.

Do what you want.

Paul

---

### Post by nvteighen on 2011-08-19
@OP:

You've received good advice here; some of the people here have decades of programming experience and know quite well what they're talking about. (Not me, though :()

In general, programming consists in building complex systems from simpler blocks. You go creating simple things and slowly build a net of interconnecting functions, objects or whatever. Make each function do just one clearly defined task and connect them by passing values the one to the other (argument lists as input "pipes" and return values as output "pipes").

---

### Post by Bachstelze on 2011-08-19
> **Arndt said:**
> If not in printf, where in your code do you expect the evaluation to happen? In scanf?

Why do you say "if such thing exists"?

In zsh, printf will evaluate the string "2+2" as 4. Not in Bash, though...

```
firas@aoba ~ % printf "%d\n" "2+2"
4
firas@aoba ~ % bash
firas@aoba:~$ printf "%d\n" "2+2"
bash: printf: 2+2: invalid number
2

```

---

### Post by nvteighen on 2011-08-19
> **jjpcexpert said:**
> VERY good idea. Now please tell me how to implement in pure C. Do not provide full source, juts provide an idea of what I need to use. I do not have math.h, as I use Debian.


I also use Debian and I can assure you that math.h lives exactly at /usr/include/math.h

Very possibly, your issue is that you're not linking to the C Math Library. To do that, use the -lm flag when compiling (the -l<name> flag is used for linking... if a library is called libname.so, the flag to use is -lname).

---

### Post by CptPicard on 2011-08-19
Why not take up a language such as Python which would let you concentrate more on building the actual parser -- and understanding it -- than fighting the details of C at the same time, while you're obviously completely out of your depth at both?

---

### Post by cgroza on 2011-08-19
> **CptPicard said:**
> Why not take up a language such as Python which would let you concentrate more on building the actual parser -- and understanding it -- than fighting the details of C at the same time, while you're obviously completely out of your depth at both?
He can also use the interpreter to parse and calculate the expressions for him, leaving him to code only the interface. :D

---

### Post by jjpcexpert on 2011-08-19
I got it! I used code from Kernighan and Ritchie's book of C, but I modified it for ease of use. I even give a Credit notice.

*cue smooth jazz, neoclassical and classical all at once at same bpm*

The code is attached at [ATTACH]200354[/ATTACH]. 

Don't say I didn't give the Keritchie Duo credit!

OT: I am upgrading from VHS to S-VHS. LOL.

---

### Post by jjpcexpert on 2011-08-19
> **Bachstelze said:**
> In zsh, printf will evaluate the string "2+2" as 4. Not in Bash, though...

```
firas@aoba ~ % printf "%d\n" "2+2"
4
firas@aoba ~ % bash
firas@aoba:~$ printf "%d\n" "2+2"
bash: printf: 2+2: invalid number
2

```

Thx for clearing that up. Done though.

[SOLVED]

---

### Post by jjpcexpert on 2011-08-19
> **PaulM1985 said:**
> I'm sorry.  Did you just call me stupid?
No. I quoted a very famous saying:
KEEP IT SIMPLE, STUPID!
otherwise known as KISS.

:(

---

### Post by jjpcexpert on 2011-08-19
> **NovaAesa said:**
> I agree with dwhitney67, the task the OP is attempting is not even close to being trivial or easy. I wouldn't advise attempting parsing then executing expressions until you have a large amount of programming experience under your belt.

I'll read the joint me and K&R code to understand it better.
Thank you for your suggestion.
[SOLVED]

---

### Post by CptPicard on 2011-08-19
> **cgroza said:**
> He can also use the interpreter to parse and calculate the expressions for him, leaving him to code only the interface. :D

The logical part of the parser is the interesting part though. Which he would be able to move onto more easily if he were not using C in the first place.

---

### Post by jjpcexpert on 2011-08-20
> **PaulM1985 said:**
> I'm sorry.  Did you just call me stupid?

If you don't know too much about programming and don't know how to parse expressions you are likely to get stuck, regularly.  I was simply trying to get you on the right path to learning.

Do what you want.

Paul
Also, I know enough BASH to do almost everything I need.
I started out with using the Internet for examples.
I then did a real shebang (pun intended) by using Zenity in my scripts, late into my use of scripts.

My first C program was a form of Hello World.
It consists of:

```
#include <stdio.h>

main () {
     printf("Howdly doodlie!\n");
}
```What an unusual Hello World.
I could also make a string one:
```
#include <stdio.h>

main () {
     char string[100] = "Howdly doodlie!\n"
     printf("%s",string)
}
```Compile and see. It won't harm your PC, and what I have done that is not already copyrighted by someone else is currently public domain - but I reserve the right to remove any rights to the program, so it is "partial public domain" - as I like to call it.

It's just when I get stuck that I need teh internets.

Anywho - I now need to find an infix to suffix converter, and all will be heidly-ho.

My latest calculator is RPN. So no shift-9's or shift-0's.

---

### Post by ve4cib on 2011-08-20
> **jjpcexpert said:**
> VERY good idea. Now please tell me how to implement in pure C. Do not provide full source, juts provide an idea of what I need to use. I do not have math.h, as I use Debian.
The bounty is the executable with modified source code to explain how to use reverse Polish notation.

You wouldn't need math.h if all you want to do is simple addition/subtraction/division/multiplication.  Those operations are standard in C.  But I can guarantee you that you *do* have math.h somewhere.  It's a standard component of C, and Debian will have it -- just like every other Linux distro out there.

Anyway, in very rough pseudo-code, a simple RPN calculator might look something like this:

```

#define STACK_SIZE  255
#define EXPR_LEN    100

main()
{
    // allocate an array that we'll use as the stack
    double rpnStack[STACK_SIZE];

    // keep the index of the "top" of the stack
    int rpnTop = -1;

    // a c-string used to read in numbers and operations
    char expr[EXPR_LEN];

    for(;;)
    {
        printStack(rpnStack, rpnTop);

        // read in either a number or an operation
        printf("> ");
        fgets(expr, EXPR_LEN, stdin);

        // see what was entered
        // there are better ways of checking this, and I'm only dealing
        // with addition and subtraction, but this should give you some ideas
        if(!strcmp(expr,"+"))
        {
            // if an operation was entered evaluate it
            double a = pop(rpnStack, &rpnTop);
            double b = pop(rpnStack, &rpnTop);

            push(a+b, rpnStack, &rpnTop);
        }
        else if (!strcmp(expr,"-"))
        {
            // if an operation was entered evaluate it
            double a = pop(rpnStack, &rpnTop);
            double b = pop(rpnStack, &rpnTop);

            push(a-b, rpnStack, &rpnTop);
        }
        else
        {
            // otherwise we just assume the user entered a number
            // and we push it onto the stack
            push(atod(expr, NULL), rpnStack, &rpnTop);
        }
    }
}

// print out the entire stack
void printStack(double *stack, int top)
{
    int i;
    for(i=0; i<=top; i++)
    {
        printf("%2d  %f\n", i+1, stack[i]);
    }
}

// add a new double to the top of the stack
// note: this does NOT do any checking for buffer overflows
void push(double x, double *stack, int *top)
{
    *top++;
    stack[*top] = x;
}

// remove the top item from the stack and return it
// note: this does not do any checking for buffer underflows or
// empty stacks
double pop(double *stack, int *top)
{
    double x = stack[*top];
    *top--;

    return x;
}
```

Obviously there are some major problems with this code (namely there's no way of preventing buffer overflows if the stack exceeds 255 items, and we're being horribly inefficient when it comes to evaluating if something is an operator or not), but it gives you the general idea.

When using the program you'd see something like this:

```

> 1

1  1
> 5

1  1
2  5
> +

1  6
>
```

(Assuming the user entered the number 1 first, then the number 5, and then entered the + symbol.)

---

