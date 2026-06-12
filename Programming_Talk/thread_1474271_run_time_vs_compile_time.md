---
title: "run time vs compile time"
date: 2010-05-05
forum: Programming Talk
---

### Post by cybo on 2010-05-05
it is really embarrassing to ask this question, since i code for some time now, but i really never understood the difference between run-time and compile-time. for example what is the difference between run-time and compile-time errors? or maybe one variable assignment is done at compile-time as opposed to another variable assignment is done at run-time, what is the difference and more importantly why does it matter?

any help is appreciated.

---

### Post by Queue29 on 2010-05-05
Compile - Time errors are errors which can be caught at compile time, i.e. the compiler won't even compile your code because something is wrong. For example,

```
3 = x;
```

would be a compile time error. A run time error is a logic error. The computer thinks your program is doing just fine, but in fact, your logic is flawed. Say you have an infinite loop, or a recursive call with no base case. Also, stuff that can be caught by exceptions would be run time errors. Like trying to connect to a URL that is down for some reason.

---

### Post by jeffathehutt on 2010-05-05
A compile time error is usually a syntax error that the compiler can detect.  For example, if you mistype the name of a function or variable, the compiler will alert you to the error and you have to fix the error before the compiler can finish.

A run time error is usually a logical one.  For example, you intend to add two numbers but instead you multiply them.  The compiler won't see it as a error, it will just assume you meant to multiply.  But when you run the program, you will get unexpected output due to the logic error.  Generally run time errors are much more difficult to locate and fix, since the compiler can't tell you where the error is located (since the syntax is actually correct). :)

---

### Post by lostinxlation on 2010-05-05
Compile errors are syntax errors, as mentioned.
 
Run time errors occur when your program does something wrong. The simple example is that you divide some number by zero. CPU is going to take divide-by-zero trap and the trap handler might kill the program and exit because divide by 0 shouldn't happen.

---

### Post by soltanis on 2010-05-06
More strictly a run-time error occurs when your program encounters a condition that it couldn't have known of until it actually ran.

For example:
[LIST]
[*]Your program attempts to load a library on startup that doesn't exist
[*]Invalid parameters are encountered while you are processing configuration or input data (and the program didn't guard against those conditions)
[*]Run-time memory becomes corrupted, there is a hardware failure, or there is an I/O error
[/LIST]

This is as opposed to a "bug" which is a human error which causes the program to behave unexpectedly.

---

### Post by alys666 on 2010-05-06
compile time error - the error during your comlier runs. usually it is the syntax error, when compiler cant understand your syntax construction.
for some languages (loke C/C++)also there are link-time errors - when linker cant find some object to link into your binary file. for example some function.
run time errors - error which could occur when your binary file(programm) runs. for example attempt to use pointer to object which is NULL. it is an attempt to work with address 0, but this walue is reserved as pointer which points to nothing.

---

### Post by Compyx on 2010-05-06
Everybody has been talking about errors, but there's another aspect to the distinction between compile-time and run-time: compile-time constants.

Compile-time constants are values the compiler can determine while compiling your source, such as the size of an array or the length of a string constant. Knowing certain values at compile time allows the compiler to optimize things. 

Then there's another type of compile-time constants: those who may or may not exist, depending on the system you're compiling your source on. One such a constant is PATH_MAX (the size a buffer needs to be to hold the return value from getcwd(3) and friends).

On some systems it is a compile-time constant, so you can do stuff like:
```

char pathbuf[PATH_MAX];

```
while on other systems, PATH_MAX isn't known at compile-time, so you need to determine the value at runtime, using pathconf():
```

#define PATH_MAX_GUESS 4096

static char *get_pathbuf(void)
{
#ifdef PATH_MAX
    long pmax = PATH_MAX;
#else
    long pmax = pathconf("/", _PC_PATH_MAX);
#endif
    if (pmax < 0) {
        /* pathconf() didn't know PATH_MAX either, guess */
        pmax = PATH_MAX_GUESS;
    }
    return malloc((size_t)pmax);
}

```

---

### Post by lisati on 2010-05-06
Simple summary:

Some things the computer can work out for itself when your program is compiled, other things have to wait until you run your program.

---

### Post by alys666 on 2010-05-06
> On some systems it is a compile-time constant, so you can do stuff like:
this is not a "special error" this is the error of undeclared object, because of preprocessor.
naturally there are three classes of compile-time errors
1. lexical error, for example - 23foo - this lexem starts as decimal number, but ends with letters. for most languages it is not a number and not an identifier - so lexical analysis reports an error.
2. after lexical analysis there is syntax analysis - does your text follows grammar rules of the language. line 
if a>b then ...
is correct for pascal grammar rules, but incorrect for C-family grammars. So C compiler reports an syntax error, pascal - not.
and third stage is semantic analysis - which checks type conversions, are declared used objects or not, has non void functions return statements...and different bla-bla... this errors are semantic errors.
also there could be errors on code generation stage, if compiler has some code generation restrictions. but it is rare and very special.
but this is details of compilation process and all of this errors are - the compilation time errors.

---

