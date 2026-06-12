---
title: "C Programming language - What kind of information is this - on this web site?"
date: 2011-12-20
forum: Programming Talk
---

### Post by ClientAlive on 2011-12-20
Hi,

The other day someone on one of the irc channels suggested I familiarize myself with all the C libraries (yeah, I'm learining C). This sounded like good advice so I went out and found a resource on the Internet. The information looks like useful information (something I probably ought to be looking at) but I'm not sure what kind of information it is. Is it information about something that goes on behind the scenes? Information about something the compiler does? Information I can acutally use in my code? Or maybe some combination of the above? And how can I apply this information in a way that benefits me?

I asked this same question on that irc channel but the response I got did not address the question. I would still like to find and answer to my question; so, rather than pressure people there, I thought it would be a good idea to post here and ask about it.

Can anyone shed some light on this?

Thanks, much appreciated.

Link to that web page: [http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html](http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html)

---

### Post by jualin on 2011-12-20
The C Libraries are just there to help you. They consist of functions that were already created and that it would save you time. For instance, the standard input/output library (stdio.h) has functions of input and output (printf ...).
[This website]("http://www.cprogramming.com/") should help you.
Hope this helps :)

---

### Post by ClientAlive on 2011-12-20
> **jualin said:**
> The C Libraries are just there to help you. They consist of functions that were already created and that it would save you time. For instance, the standard input/output library (stdio.h) has functions of input and output (printf ...).
[This website]("http://www.cprogramming.com/") should help you.
Hope this helps :)


Awesome! I know of that website you gave. I visit it sometimes (though not all of their info seems to apply to C only).

That's a good example you imply using the <stdio.h> library. Fortunately, some of it's functions I have experience with - so lets roll w/ that ibrary as an example for a second.

In the web page I was asking about, when I look at the section for <stdio.h> I don't see any of the C code (functions) that I'm familiar with for that library. (Like printf, scanf, for, while, if, etc, etc). As a result I have to beleive that the information contained there pertains to something other than the code you use when you write a program. However, I must also believe, because programming language is a human invention, that whatever it is, has a concrete application to something. If that is the case it raises three questions for me that I'm conviced would make a world of differnce in my learning if I knew their answer:

(1) If it is not actual code then what is it?
(2) What does it do; or, to what does it apply (concretely)?
(3) For what it is, how may it's knowledge be of use to me when I write code?

What I'm trying to do here is get a little more organized with the information about C. Rather than skip around whenever a certain question or other comes up - if I could get some comprehensive list in front of me, could put my finger on a "beginning" of C and move forward linearaly from there - then I'd have a framework with which to place parameters on my learning. Classes in school do not do this. They select peices of knowledge they feel you need to learn in that particular class. In the next class you may learn other peices of information; but in the end, it's spotty. What I'm aiming for is something comprehensive (that encompases all of C) and I think I can have that if I just find the right beginning and take the right path(s) from it. I have a gut feeling that the information contained at that site is pertinent to that goal; but, when I saw it, I felt I needed to ask for clarification on it.


Thanks
---------------

Edit:

Hang on, maybe there's something I missed. I did a ctrl+f and searched for "printf" on that page and it is there, under the <stdio.h> section. I did a search on the page for "scanf" and it's there. Perhaps I just made a mistake about what I was looking at. There are a lot of things there which I've never laid eyes on before. Just glad I found out. I can study with confidence now - understanding what it is I'm looking at.

Thanks jaulin. I appreciate it man. It was your example that helped me figure it out.

---

### Post by jualin on 2011-12-20
> **ClientAlive said:**
> Awesome! I know of that website you gave. I visit it sometimes (though not all of their info seems to apply to C only).

That's a good example you imply using the <stdio.h> library. Fortunately, some of it's functions I have experience with - so lets roll w/ that ibrary as an example for a second.

In the web page I was asking about, when I look at the section for <stdio.h> I don't see any of the C code (functions) that I'm familiar with for that library. (Like printf, scanf, for, while, if, etc, etc). As a result I have to beleive that the information contained there pertains to something other than the code you use when you write a program. However, I must also believe, because programming language is a human invention, that whatever it is, has a concrete application to something. If that is the case it raises three questions for me that I'm conviced would make a world of differnce in my learning if I knew their answer:

(1) If it is not actual code then what is it?
(2) What does it do; or, to what does it apply (concretely)?
(3) For what it is, how may it's knowledge be of use to me when I write code?

What I'm trying to do here is get a little more organized with the information about C. Rather than skip around whenever a certain question or other comes up - if I could get some comprehensive list in front of me, could put my finger on a "beginning" of C and move forward linearaly from there - then I'd have a framework with which to place parameters on my learning. Classes in school do not do this. They select peices of knowledge they feel you need to learn in that particular class. In the next class you may learn other peices of information; but in the end, it's spotty. What I'm aiming for is something comprehensive (that encompases all of C) and I think I can have that if I just find the right beginning and take the right path(s) from it. I have a gut feeling that the information contained at that site is pertinent to that goal; but, when I saw it, I felt I needed to ask for clarification on it.


Thanks
---------------

Edit:

Hang on, maybe there's something I missed. I did a ctrl+f and searched for "printf" on that page and it is there, under the <stdio.h> section. I did a search on the page for "scanf" and it's there. Perhaps I just made a mistake about what I was looking at. There are a lot of things there which I've never laid eyes on before. Just glad I found out. I can study with confidence now - understanding what it is I'm looking at.

Thanks jaulin. I appreciate it man. It was your example that helped me figure it out.
(1) The libraries have actual code. When you include a library using "#include <library name>" you are linking those pre-made functions to your code so that when you say printf("Hello world"), the compiler knows that there is a "printf()" function in the libraries. Take a look at [this page]("http://www.cplusplus.com/reference/clibrary/cstdio/") for example, which has all the functions that stdio have and how to use them. 
Let's say that you want write text to a file. Instead of you writing a function to do this, you would use a combination of something like [fopen or fputs]("http://www.cplusplus.com/reference/clibrary/cstdio/fopen/"), which are available in the stdio library.
(2) Basically what libraries do is save you time since you don't have to write your own functions to do menial tasks. 
(3) Again, if you know what is available, you can use it instead of trying to figure it out on your own. 
Let me know if this clarified you doubts :)

---

### Post by ClientAlive on 2011-12-21
> **jualin said:**
> (1) The libraries have actual code. When you include a library using "#include <library name>" you are linking those pre-made functions to your code so that when you say printf("Hello world"), the compiler knows that there is a "printf()" function in the libraries. Take a look at [this page]("http://www.cplusplus.com/reference/clibrary/cstdio/") for example, which has all the functions that stdio have and how to use them. 
Let's say that you want write text to a file. Instead of you writing a function to do this, you would use a combination of something like [fopen or fputs]("http://www.cplusplus.com/reference/clibrary/cstdio/fopen/"), which are available in the stdio library.
(2) Basically what libraries do is save you time since you don't have to write your own functions to do menial tasks. 
(3) Again, if you know what is available, you can use it instead of trying to figure it out on your own. 
Let me know if this clarified you doubts :)


Why yes sir, yes it did. Thank you. When I initially posted I wasn't totally aware that I was looking at the actual function calls (function calls, or functions? Because there could be a difference).

I do have one, last question if it's ok. Some of the entries I see on that page look different, syntactically, than I'm used to seeing. For instance, the first three entries under the <stdlib.h> section. These entries are all upper case with an underscore in them. The only function calls I've used (or seen) thus far are all lower case letters, no spaces, one word. Are the entries in that, other syntax, still used as function calls in your code then?

Thanks
--------------------

Edit:

btw, I didn't know that section was there at the site you shared. Their reference section looks very good. I only hope they make a crisp enough distinction between C and C++ as I'm learning C not C++. Thank you for pointing out that area of the site.

---

### Post by nvteighen on 2011-12-21
Sorry, jualin, but you are giving completely incorrect information to the OP.

A C or C++ *library* is a binary file that's compiled in a certain special way such that you can access its functions and other definitions from the "outside". There are two kinds of libraries: static and dynamic. Static libraries are copied into your executable. On the other hand, dynamic ones are "linked" with your program: when you start your program, the OS knows what libraries are needed and loads them if they haven't been loaded into memory yet.

In either case, a library is a binary.

But, how is the compiler instructed about the types a certain library function requires as arguments or what type does it return? There's where header files come in. Header files don't include any code, just forward declarations whose only purpose is to tell the compiler that some function exists and its signature (well, there is an exception: code of C++ template classes and functions are written into header files...). It is the linker, at the fourth and last stage performed by a C and C++ compiler, which then checks the libraries for those external functions (actually, it also does this with all object code files that form your final executable...).

If you want to know how printf is implemented, you'll have to download libc's source code.

---

### Post by ClientAlive on 2011-12-21
> **nvteighen said:**
> Sorry, jualin, but you are giving completely incorrect information to the OP.

A C or C++ *library* is a binary file that's compiled in a certain special way such that you can access its functions and other definitions from the "outside". There are two kinds of libraries: static and dynamic. Static libraries are copied into your executable. On the other hand, dynamic ones are "linked" with your program: when you start your program, the OS knows what libraries are needed and loads them if they haven't been loaded into memory yet.

In either case, a library is a binary.

But, how is the compiler instructed about the types a certain library function requires as arguments or what type does it return? There's where header files come in. Header files don't include any code, just forward declarations whose only purpose is to tell the compiler that some function exists and its signature (well, there is an exception: code of C++ template classes and functions are written into header files...). It is the linker, at the fourth and last stage performed by a C and C++ compiler, which then checks the libraries for those external functions (actually, it also does this with all object code files that form your final executable...).

If you want to know how printf is implemented, you'll have to download libc's source code.

Interesting. I had encountered some information about 'static' vs. 'dynamic' libraries very (very) breafly in our book. So, from what you shared, I'm gathering that it is binary that the compiler is linking into your program when compile your code (that code consisting of functions in the standard libraries of course). And I would have to extrapolate from that, that all the standard libraries are static libraries, right? I mean they 'are' the C programming language, right? And a program that's a single file of code, when compiled, has to include information from those libraries in order to produce your binary file.

Again, nvteighen, you're making me think about things I've never had to think about before. There's just so much interesting stuff about this language, about programming altogether. It's got me wondering whether the compiler is basically copy/pasting (in a sense) peices of binary from the standard libraries or if it's creating brand new binary from scratch.

At any rate, I'm chasing rabbits (something I love to do)  :P  I wouldn't 'expect' anyone to join me on the chase but for however long they were to walk with me would be cool.

:D
--------------

Edit:

Oh, but what about that other thing: are some of those other, funny looking entries, function calls as well? I haven't seen that syntax before and am trying to imagine what the code would look like that utilized them.

---

### Post by Barrucadu on 2011-12-21
The standard library is generally linked dynamically.

---

### Post by ve4cib on 2011-12-21
> **ClientAlive said:**
> It's got me wondering whether the compiler is basically copy/pasting (in a sense) peices of binary from the standard libraries or if it's creating brand new binary from scratch.

Assuming you're creating an executable program of your own just to keep things somewhat simplified...

When you compile your program the compiler does the following things (more-or-less):

1- The C preprocessor (CPP) handles all of your #define, #include, etc... statements.  Any place where you use a macro (anything defined with a #define) the CPP will replace the macro with the definition.  Wherever you've included a header file (using #include) the contents of that header file are literally copied-and-pasted into your own code.

2- Each .c file is compiled into an object (.o) file.  This is a binary representation of that block of code.  (Libraries are already compiled into a binary form, usually a .o or .so that is lurking somewhere on your file system; check out the contents of /lib, /usr/lib, etc... to see some of the libraries that are already on your computer.)

3- The linker takes all of your .o files, as well as compiled binaries for any static libraries and mushes them all together into one file: your executable.

When you run your program any dynamic libraries you use are loaded by the OS and made available to your program at run-time.

Using a lot of static libraries will result in your program being bigger, but has the advantage of always using a specific version of the library (the one you compiled with).  Dynamic libraries on the other hand will not affect the size of your binary, but if the end-user has a different version of the library than you did when you compiled they may get errors (or the program will simply fail to run).  Honestly though, don't worry too much about this; it's irrelevant for most purposes.

Finally, I've noticed you seem to be a little confused about "function" vs "function call."  A function is a block of code that gets executed when it is called.  It looks something like this:

```

/* inside my_header.h */
int isEven(int);  // returns TRUE/FALSE if the parameter is even or not


/* inside my_source.c */
int isEven(int number) {
    return number % 2 == 0;
}
```


A function *call* is anyplace inside your source code where you use a function:

```

#include <stdio.h>
#include <my_header.h>
int main(int argc, char** argv) {
    printf("Hello World");  // <-- this is a function call to printf
    
    if( isEven(argc))  // <-- here's a function call to isEven used inside an if statement
        printf("you provided an even number of arguments\n");  // <-- another call to printf
    else
        printf("you provided %n arguments, an odd number\n", argc); // <-- again we call printf, this time with two arguments
    return 0;
}

```

Function names (like variables) can *never* contain spaces.  So when you make a function call the only spaces should be before/after the parentheses, and between the parameters.  A function call always follows the format:

<function name> ( <arguments, separated by commas> )

e.g. printf("Hello World")
e.g. strncpy(dest, src, MAX_STR_LENGTH)

Hopefully this clears things up a little bit?

---

### Post by karlson on 2011-12-21
> **ClientAlive said:**
> Interesting. I had encountered some information about 'static' vs. 'dynamic' libraries very (very) breafly in our book. So, from what you shared, I'm gathering that it is binary that the compiler is linking into your program when compile your code (that code consisting of functions in the standard libraries of course). And I would have to extrapolate from that, that all the standard libraries are static libraries, right?


They can be either.  Difference is that when linked static libraries will include code for functions defined in the library into your binary and dynamic will simply provide a link to a shared object(binary) that has the definition in it.

> I mean they 'are' the C programming language, right? And a program that's a single file of code, when compiled, has to include information from those libraries in order to produce your binary file.


Yes the linker will link the libraries to your binary the program doesn't have to include any information from any library as long as you are not using the functions defined in those libraries.

> 
Again, nvteighen, you're making me think about things I've never had to think about before. There's just so much interesting stuff about this language, about programming altogether. It's got me wondering whether the compiler is basically copy/pasting (in a sense) peices of binary from the standard libraries or if it's creating brand new binary from scratch.


I think you are confusing things.  The library functions that you will use are with rare exception already compiled so the compiler doesn't have to recreate them it just has to produce enough information for the linker to be able to tell where the address for the function actually lies.


> 
Oh, but what about that other thing: are some of those other, funny looking entries, function calls as well? I haven't seen that syntax before and am trying to imagine what the code would look like that utilized them.

Which ones?

---

### Post by ClientAlive on 2011-12-21
Sorry guys. When attempting to edit a spelling mistake I must have clicked a wrong button by mistake. The real response is in the post below.

---

### Post by ClientAlive on 2011-12-21
> **ve4cib said:**
> Assuming you're creating an executable program of your own just to keep things somewhat simplified...

When you compile your program the compiler does the following things (more-or-less):

1- The C preprocessor (CPP) handles all of your #define, #include, etc... statements.  Any place where you use a macro (anything defined with a #define) the CPP will replace the macro with the definition.  Wherever you've included a header file (using #include) the contents of that header file are literally copied-and-pasted into your own code.

2- Each .c file is compiled into an object (.o) file.  This is a binary representation of that block of code.  (Libraries are already compiled into a binary form, usually a .o or .so that is lurking somewhere on your file system; check out the contents of /lib, /usr/lib, etc... to see some of the libraries that are already on your computer.)

3- The linker takes all of your .o files, as well as compiled binaries for any static libraries and mushes them all together into one file: your executable.

When you run your program any dynamic libraries you use are loaded by the OS and made available to your program at run-time.

Using a lot of static libraries will result in your program being bigger, but has the advantage of always using a specific version of the library (the one you compiled with).  Dynamic libraries on the other hand will not affect the size of your binary, but if the end-user has a different version of the library than you did when you compiled they may get errors (or the program will simply fail to run).  Honestly though, don't worry too much about this; it's irrelevant for most purposes.


> **ve4cib said:**
> 
Finally, I've noticed you seem to be a little confused about "function" vs "function call."  A function is a block of code that gets executed when it is called.  It looks something like this:


I thought I understood the difference between a function and a function call but the variety of ways in which function calls can be used in code is whole other story. for instance:


> **ve4cib said:**
> 
    if( isEven(argc))  // <-- here's a function call to isEven used inside an if statement


Is a new one.


> **ve4cib said:**
> 
        printf("you provided an even number of arguments\n");  // <-- another call to printf
    else
        printf("you provided %n arguments, an odd number\n", argc); // <-- again we call printf, this time with two arguments
    return 0;
}
[/code]


But that I've done before.

I end up doing a lot of trial and error to learn these different ways things can be used (varieties of algorith I suppose). It's tedious and very time consuming.


> **ve4cib said:**
> 
Hopefully this clears things up a little bit?


You know, I hate to say it - I love my prof - but all this is 1,000 times more than she ever did for me.


[B]> **karlson said:**
> 
Which ones?
[/B]

For instance:

In the section for <limits.h> here: [http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#limits.h](http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#limits.h)

Every entry in that section shows a syntax using all capital letters with an underscore. There are no parenthesis involved and no semicolon at the end. Up to this point I have only worked with a handful of function calls from the <stdio.h> library; and, by comparrison, the syntax for those has been of one of two varieties - all lower case, one word, contians parenthisis, sometimes a semicolonn at the end sometimes not.

[The only reason I'm describing these differences is to point out the recognition of differences. That recognition leads me to the more practical; and, more important, question: "how," "when," and "why."]

So when I looked that this new information (the examples shown in the <limits.h> library, for instance) I wondered if (1) it was something you ever actually wrote into your code file, and (2) what it would look like if you did.

On another note, which I'm uncertain is a 'different' note or not - there are also some entries I see that are defined as "macro." There are two such entries in the <stdarg.h> library, shown here: [http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#stdarg.h](http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#stdarg.h)

I noticed that the syntax used in those examples is of another type (is it right to try and "type" them? But, if only for the sake of communicating... ) The sysntax in those two examples is all lower case, contains an underscore, and something new is contained within the parenthesis - an additional element, separated by a space. For an example of this thing I called "an additional element" look at the "ap" inside the parenthesis of "void va_start(va_list ap, lastarg);".

ve4cib provided a peice of information I just saw when I read it a few minutes ago.

> **ve4cib said:**
> 
1- The C preprocessor (CPP) handles all of your #define...  statements.  Any place where you use a **macro (anything defined with a #define)...**


With that in mind I'll take a stab and ask...

Would all entries shown for all of the C standard libraries, which are defined as "macro" - then be written in code like this?

```

/*For Example*/

<#define void va_start(va_list ap, lastarg);>

```

A correction would provide me understanding on the concrete application of this detail. It's just a detail though and an abstraction from the more general, initial question about this.

The more general question took into consideration all of the entries in all the libraries. I had noticed differences in syntax which allerted me to possible differences in use (conrete application within code with a special focus on syntax within the code - not just conceptual).

From identifying differences I had hoped to discover practical application. Even just a simple familiarity would enable me to be comfortable stretching myself even further. I could begin to experiment with my code and see what this or that new thing does, what I'm doing (or what I'm doing incorrectly), and ultimately improve my skills.


Thanks

---

### Post by karlson on 2011-12-21
> **ClientAlive said:**
> 
In the section for <limits.h> here: [http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#limits.h](http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html#limits.h)

Every entry in that section shows a syntax using all capital letters with an underscore. There are no parenthesis involved and no semicolon at the end. Up to this point I have only worked with a handful of function calls from the <stdio.h> library; and, by comparrison, the syntax for those has been of one of two varieties - all lower case, one word, contians parenthisis, sometimes a semicolonn at the end sometimes not.


As **ve4cib** pointed out those are macros, which are lexically substituted by the compiler every place they are used.  In case of limits.h they are simply constants. 
> 
So when I looked that this new information (the examples shown in the <limits.h> library, for instance) I wondered if (1) it was something you ever actually wrote into your code file, and (2) what it would look like if you did.


You mean macros?  Yes rarely you would use it.  More often you would use them to make sure that your header is only processed once.  Constructs like:
```

#ifndef MACRO
#define MACRO

....

#endif

```


> 

Would all entries shown for all of the C standard libraries, which are defined as "macro" - then be written in code like this?

```

/*For Example*/

<#define void va_start(va_list ap, lastarg);>

```



No the code would look like this:

```

#define va_start(v,l)   __builtin_va_start(v,l)

```

This one is actually from the GLIBC's stdarg.h.

In addition MACROs are not "typed".  Macro is a lexical substitution of a MACRO for it's value.  Namely any reference to any macro will look like this after the preprocessor is done.
```

va_start(varargs, lastarg);

```
would look like:
```

__builtin_va_list(varargs, lastarg);

```

---

### Post by Barrucadu on 2011-12-22
> **ClientAlive said:**
> 

[...]

Is a new one.

Function calls can be used in any expressions. I think you may be overcomplicating things somewhat - rather than learn every single place in which you may use something, learn the rules that govern its use, then you will be able to look at new things in the future and *know* whether you can or can't use something.

---

### Post by ClientAlive on 2011-12-23
> **Barrucadu said:**
> Function calls can be used in any expressions. I think you may be overcomplicating things somewhat - rather than learn every single place in which you may use something, learn the rules that govern its use, then you will be able to look at new things in the future and *know* whether you can or can't use something.


I think I let it intimidate me a little bit. I just came to the close of my first ever programming class. The first few weeks of the class were super easy and I let myself be fooled. Somewhere about the middle of the class I just remember spending countless hours trying to work out what should have been very simple, easy code. In the end it came down to really stupid little issues like which line came first in sequence or forgetting to initialize a variable to zero or something. Suffice it to say I got really bogged down and I just didn't want to go through that again. (Though I'm sure there'll always be a challenge). I'm sure you're righ Barrucadu and I am getting more comfortable and making less mistakes. I just wanted to take these few weeks in between semesters to learn as many details, memorize as much as I could, practice, etc to help me be more prepared for my next class. I will try to focus on that - what you mentioned.

Honestly though, I really don't see how they're going to teach me even a sliver of what I should know in a year and a half of school. And out of that only a couple classes are on C programming, the rest are in other areas of computer science. It really is up to me to learn what I need to know.

---

