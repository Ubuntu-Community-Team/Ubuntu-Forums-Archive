---
title: "Variable Initialization"
date: 2010-02-08
forum: Programming Talk
---

### Post by newport_j on 2010-02-08
I have a C program that has many sub programs. I want to know how many times a certain subprogram executes. I put a line in that subprogram that says 

repcount = repcount + 1;

where repcount is my counter and I add 1 to it each time the execution enters that subprogram. I initialized repcount in the main program; obviously I do not want to initialize repcount in the subprogram because that would mean that repcount is set back to zero each time I enter the subprogram. 

However, the compiler does not like it saying that repcount has not been initialized - in the subprogram. Well, repcount is a global variable and I initialized in the main program only once. 

How do I remedy this situation since, repcount cannot be initialized in the the subprogram of interest even though the complier complains if I do not initialize it there?

Again, each subprogram is in its own computer file.

How do I correct this?

newport_j

---

### Post by Bachstelze on 2010-02-08
What do you mean by "sub program"?

---

### Post by djbushido on 2010-02-08
I agree. What is a "sub program"? Are you using calls to System("PROGRAM_NAME")? If so, whenever these exit is when you increment the counter.

---

### Post by newport_j on 2010-02-08
Okay, each program including main.c is a subprogram. I have subroutines that each do a function. I am new to c so I call them subprograms. To me a subprogram is either a function or a subroutine. I have these "subprograms" in separate computer files.

Now in one I am trying to count the number of times the execution enters it. So I set up a counter with the line:

repcount = repcount + 1;

so each time the program is entered it will be recorded. Now I must initialize the variable repcount to 0. I clearly cannot do that in the said subprogram with a statement

repcount = 0;

I defined repcount as a global variable. So I thought if I initialized it in the main program (which is traversed only once) then there would be no problem. So I did that. In a beginning line of main, put the command repcount = 1; so it would be initialized only once to 0. 

I also define the variable repcount to be integer outside of a program code like:

int repcount;

Then on compiling, I get the error

error: ‘repcount’ undeclared here (not in a function).

I am not sure what to do the correct this error.

Any help appreciated.

newport_j

---

### Post by napsy on 2010-02-08
c "subrotines" are called "functions". the "computer files" are called "source files" where the file suffix is ".c". "header files" are those files which have a ".h" suffix.

So if I understand correctly, you want to count how many times does a function(which is written in another source file) get called?

---

### Post by dwhitney67 on 2010-02-08
> **newport_j said:**
> Okay, each program including main.c is a subprogram. I have subroutines that each do a function. I am new to c so I call them subprograms. To me a subprogram is either a function or a subroutine. I have these "subprograms" in separate computer files.

Wrong! As I discussed the other day, individual files with a .c extension are referred to as **modules**.  They are not individual programs, much less sub-programs; when linked together, they form ONE program/application.

> **newport_j said:**
> 
Now in one I am trying to count the number of times the execution enters it. So I set up a counter with the line:

repcount = repcount + 1;

so each time the program is entered it will be recorded. Now I must initialize the variable repcount to 0. I clearly cannot do that in the said subprogram with a statement

repcount = 0;

I defined repcount as a global variable. So I thought if I initialized it in the main program (which is traversed only once) then there would be no problem. So I did that. In a beginning line of main, put the command repcount = 1; so it would be initialized only once to 0. 

I also define the variable repcount to be integer outside of a program code like:

int repcount;

Then on compiling, I get the error

error: &#8216;repcount&#8217; undeclared here (not in a function).

I am not sure what to do the correct this error.

Any help appreciated.

newport_j
There are two ways to do this.  You can either declare the variable as global within the module itself (preferably as static -- and I believe I discussed this the other day too!), or you can declare it as static within the function if that is the only place where it is needed.

Option 1 (note this would be done in a .c file):
```

static int repcount = 0;

void myfunction()
{
   ++repcount;   /* shorthand notation for repcount = repcount + 1 */

   ...
}

int get_repcount()
{
   return repcount;
}

```

Option 2 (probably not what you want):
```

void myfunction()
{
   static int repcount = 0;

   ++repcount;

   printf("repcount = %d\n", repcount);
}

```


P.S.  There is a third option; it is similar to Option 1 above, however repcount would not be declared static.  This allows for repcount to be accessible within other modules.  This approach irks a lot of seasoned programmers who know better than to pollute their code with global variables.

---

### Post by Bachstelze on 2010-02-08
You can use a counter variable and pass a pointer to it to your functions:

```
firas@itsuki ~ % cat test.c
#include <stdio.h>

int myfunction(int *counter)
{
    (*counter)++;
    printf("Hello, world!\n");
    return 0;
}

int main(void)
{
    int counter = 0;
    myfunction(&counter);
    myfunction(&counter);
    printf("Counter is %d!\n", counter);
    return 0;
}

firas@itsuki ~ % cc -o test test.c
firas@itsuki ~ % ./test
Hello, world!
Hello, world!
Counter is 2!

```

Or make it a global variable:

```
firas@itsuki ~ % cat test.c
#include <stdio.h>

int counter = 0;

int myfunction(ivoid)
{
    counter++;
    printf("Hello, world!\n");
    return 0;
}

int main(void)
{
    myfunction();
    myfunction();
    printf("Counter is %d!\n", counter);
    return 0;
}

firas@itsuki ~ % cc -o test test.c
firas@itsuki ~ % ./test
Hello, world!
Hello, world!
Counter is 2!

```

P.S.: And yes, global variables are a Bad Thing™.

---

### Post by nvteighen on 2010-02-08
Could you please tell us what you're trying to do? Without further information, all we can do is to help you by giving you general advices like "use a (static) global variable" or "use a static local variable", or the like.

I'd go for the static variable options, if you ask me.

Just remember that if you want a global be accessible from one module to the another, you have to use the **extern** keyword... Exactly the same as you would with functions (well... in the case of functions it's optional... but...).

```

/* Module main.c */

extern my_func_somewhere_else(void);
int my_global = 0;

int main(void)
{
    return my_func_somewhere_else();
}

```

```

/* Module somewhere.c */

extern int my_global;

int my_func_somewhere_else(void)
{
    return ++my_global;
}

```

---

### Post by djbushido on 2010-02-08
To be honest, I'm not entirely sure why you are including the "main" file more than once. I can kind of see how you are attempting to use one file for multiple, but I think that there's got to be a better way to do that.
By any means, for one variable like that you are probably best off to avoid a pointer and just make a static local to a function (+1 Globals are a bad idea). But again, please post back what you are trying to do.

---

### Post by newport_j on 2010-02-08
That will work. I am responding to the other comment. I know that global variables are not good. I am looking to time a subprogram module so I can tell how much time it takes up compared to the overall program execution.
 
This is a very time consuming module and I am lookng to optimize it. If I want to do that then I should get its time very much like a code profiler does. A code profiler will not work in my case.
 
 
So in order to time it, I am forced to ue global variables. This modue occurs deep into the program so calling and sending local varaibles is impractical. I am sure it will work, but the bookeeping will be horrendous. The repcount is merely a way for me to use the calculation (tot. time/repcount) to get an average.
 
newport_j

---

### Post by djbushido on 2010-02-08
Here's another trick - compile each "program" separately and use the "time" command - "time YOUR_PROGRAM_NAME" - once the program finishes, it will output run time.

---

### Post by nvteighen on 2010-02-09
Assuming your "subprograms" are modules, what you need is a profiler. I'm not quite familiar with them, but I've seen people using them to measure specific parts of their programs.

If you can't use a profiler, you can use the POSIX API to get the local time and check how many seconds passed. Your "average" (actually, ratio) idea is a smart solution, but not the best, as it won't be measuring time, but secs/calls. The result you'll get won't give you any information on how much time it took for each call to execute, just how much time passed from execution to execution... and you know your program is not the only one executing in your computer...

Now, on something else. Technical terms exist for a reason. When someone comes up here, usually beginners, it's quite normal for them to not know how things are called and we kindly teach them how to talk about programming stuff so they can communicate better with other programmers... Terms are there for us to know what we're talking about. So, please, stop using totally ambiguous and non-existing terminology like "subprograms" because it only confuses the people that is trying to help you; also because of correctness. When you don't know how something is called, it's much better to describe what it is and does rather than coining a new term that's obscure to the rest of us. You don't need to learn everything at once... you don't need to know what a "syntactic closure" is (well, you only need to know that if you're on Scheme), but please try to learn the basic ones like "module", "procedure", "method", "class", "(data) struct(ure)", "linker", "preprocessor", "interpreter", etc.

---

