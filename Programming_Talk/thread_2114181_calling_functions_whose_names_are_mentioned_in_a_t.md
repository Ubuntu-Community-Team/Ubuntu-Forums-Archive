---
title: "calling functions whose names are mentioned in a text file"
date: 2013-02-09
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-09
Hello,
 I was just thinking about this scenario. 
There is a C code having, say 100 functions defined.
There is a text file having names of 5 of those functions. 

I want to call only those 5 functions from among the 100. 

So, basically, function names to call are coming as input from a text file.

Is there something that can be done **without** using an if-else construct in the C code, as in, not something like
```

if(strcmp(line_read_from_file, "fun1")
 fun1(); 
else if(strcmp(line_read_from_file, "fun2")
 fun2(); 

```
but something intelligent/automated. I know of function pointers, but don't know how to apply it here. 

Thanks :)

---

### Post by Tony Flury on 2013-02-09
The name of a function is not available readily at runtime in a C program, so the best way would be to build a table that associates a string (I.e. a name) with a function pointer, and search for the name in the table.

---

### Post by IAMTubby on 2013-02-09
> **Tony Flury said:**
> The name of a function is not available readily at runtime in a C program, so the best way would be to build a table that associates a string (I.e. a name) with a function pointer, and search for the name in the table.
Tony Flury, I need some time to think about the reply.
But I did a mistake here, I posted on 2 separate threads thinking that my earlier thread was not created.

Admin, if possible, please delete the thread at [http://ubuntuforums.org/showthread.php?t=2114181](http://ubuntuforums.org/showthread.php?t=2114181)

Tony Flury, I'm sorry, quoting you here, so that others get to read your reply.

---

### Post by r-senior on 2013-02-09
I'd agree with Tony's suggestion of a lookup table of function pointers, so probably an array of structs containing a name and function pointer. An [associative array]("http://en.wikipedia.org/wiki/Associative_array"), aka a dictionary or map, would be more efficient than scanning through an array looking for matches. (C++ has an associative array implementation in the standard libraries).

If you want something more esoteric that doesn't involve building an associative array in C, a lexical analyzer like [Lex]("http://en.wikipedia.org/wiki/Lex_(software)") can handle that without much effort:

*functions.l*
```
%{
#include <stdio.h>

void function1();
void function2();
void function3();
void function4();
%}

%option noyywrap

%%
one             function1();
two             function2();
three           function3();
four            function4();
[[:space:]]+    /* ignore whitespace */
%%

void function1()
{
    puts("called function one");
}

void function2()
{
    puts("called function two");
}

void function3()
{
    puts("called function three");
}

void function4()
{
    puts("called function four");
}

int main()
{
    yylex();
}

```

Lex builds a lexical analyzer as would be used in writing a programming language. When it finds "tokens" in the input, it can invoke a little block of code. In a real programming language, these blocks of code would pass these tokens to a parser for further processing but all you need to do is call them.

The yylex() function provided by Lex scans the input and when it finds a token that matches one of the rules between the two "%%" delimiters, it calls the associated function. I added a rule to match whitespace and ignore it because by default Lex will just echo it.

This would be a sample run. (You'd need flex installed, which is a modern implementation of Lex).

```
$ make functions
lex  -t functions.l > functions.c
gcc    -c -o functions.o functions.c
gcc   functions.o   -o functions
rm functions.o functions.c
$ cat input.txt
one
three
$ ./functions < input.txt
called function one
called function three
$ vi input.txt # edited the "source" file
$ cat input.txt
one
three
four
$ ./functions < input.txt
called function one
called function three
called function four

```

So input.txt is your "source" file that contains the functions you want to invoke (note the names don't have to match but they could). When Lex sees the tokens that correspond to your functions, it invokes them. The functions could be in a separate .c file, they don't have to go in the Lex source.

---

### Post by Bachstelze on 2013-02-10
> **IAMTubby said:**
> 
 I was just thinking about this scenario. 


Why?

---

