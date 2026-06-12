---
title: "C function wrapper question"
date: 2010-04-08
forum: Programming Talk
---

### Post by mesuhas_sit on 2010-04-08
Hello all..
 
I am experimenting with the C function ( method ) wrapper like this:
 
```

 
#define MY_WRAPPER (X) (my_wrapper_method ( __FILE__,__LINE__,#X,(X)))
 
my_wrapper_method ( char *file , int line , char *call , int return_val )
{
        if ( return_val != 0 )
        {
                 printf ( "Error %d in file %s with method call %s at line %d" , return_val  , file  ,  call , line );
        }
}
main()
{
                MY_WRAPPER ( some_function_call ( arg1 , arg2 , arg3 ) ); 
}

```
 
Now my problem is to find in the MY_WRAPPER macro , the arguments in the function call. Like if there is an error then i want to print my arguments in the function call around which the wrapper is built.
 
Tanx

---

### Post by Compyx on 2010-04-08
I don't quite understand your question. Do you mean you want to have access to the arguments arg1, arg2 and arg3 in my_wrapper_method? I don't think that's possible, at least not in the way you wrote your wrapper.

You could write a wrapper that accepts a pointer to a variadic function returning int (not a macro, an actual function). But that's going to be messy at best.

Another way is to parse the quoted argument X, (char *call) and split that into substrings, one for each argument in the function call.


What problem are you trying to solve? I'm sure there are better ways to solve your problem, rather than (ab)using the preprocessor.

---

### Post by MadCow108 on 2010-04-08
I don't think this is possible with macros (at least in your attempted way above)

but with compiler builtins it _may_ be possible:
this seems like a good starting point
[http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Constructing-Calls.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Constructing-Calls.html)

also have a look how printf is implemented in gcc.
It is also a builtin function and does a remotely similar thing to what you want to do (but at compile time).

---

### Post by mesuhas_sit on 2010-04-08
Tanx for the reply
 
> **Compyx said:**
> What problem are you trying to solve? I'm sure there are better ways to solve your problem, rather than (ab)using the preprocessor.
 
While i was designing this, I thought at runtime if any error has occured, I thought its enough to know my error code and the line number where the error has happened. But now the tricky part is that I really dont have any clue about the values of the arguments that my methods are accepting. I wanted this info for debugging and stuff.
 
This is my problem here, i just want to know the values of the arguments being passed. Is there any good solution to this apart putting printf statements all over the place.
 
Tanx and hope this is enought.

---

### Post by MadCow108 on 2010-04-09
why not use a debugger? (e.g. gdb)

break on the runtime error with a conditional breakpoint and then you can inspect the arguments by hand

there are lots of good tutorials on google

---

### Post by Sporkman on 2010-04-09
```

#define MY_WRAPPER(FCNNAME,ARG1,ARG2,ARG3)  \
if ( FCNNAME (ARG1,ARG2,ARG3)!=0 )          \
{                                           \
   printf ( "Error... etc");                \
}

main()
{
   MY_WRAPPER ( some_function_call, arg1 , arg2 , arg3 ); 
}

```

---

### Post by Compyx on 2010-04-09
> **Sporkman said:**
> ```

#define MY_WRAPPER(FCNNAME,ARG1,ARG2,ARG3)  \
if ( FCNNAME (ARG1,ARG2,ARG3)!=0 )          \
{                                           \
   printf ( "Error... etc");                \
}

main()
{
   MY_WRAPPER ( some_function_call, arg1 , arg2 , arg3 ); 
}

```

I think the OP wanted a generic error handling wrapper, the macro you provide here will work only for functions which take three arguments and return non-0 on error. So you'd need another macro for functions accepting two arguments, and another for a function accepting three argument but returning -1 on error, and so forth. Now add different types for the arguments; you're gonna need a lot of wrappers this way.

C simply lacks the provisions for generic error handling/debugging, you can do a few things with the preprocessor, and you can add debug hooks to your code (my preferred way of debugging), but introspection and generic error handling is not something C was designed for.

That said, a simple:
```

#ifdef DEBUG_ON
#define DEBUG(X) X
#else
#define DEBUG(X)
#endif

```
will go a long way together with a few printf()'s scattered about the place:
```

if (function_call(arg) != 0) {
    DEBUG(printf("%s:%d: call to `function_call' failed with argument '%s',
        __FILE__, __LINE__, arg);)
}

```
You just compile with -DDEBUG_ON when you need debugging enabled.

Another way is to use <assert.h>, it's crude but it can be useful during development. Just remember to use -DNDEBUG when compiling for production use, you wouldn't want to bother your users with 'assertion failed' type messages.
(Though I have seen assertion-type messages while playing Diablo II: `missile fired too far')

---

### Post by Sporkman on 2010-04-09
> **Compyx said:**
> ...and another for a function accepting three argument but returning -1 on error, and so forth..

```

#define MY_WRAPPER(FCNNAME,OKRET,ARG1,ARG2,ARG3)  \
if ( FCNNAME (ARG1,ARG2,ARG3)!=OKRET )            \
{                                                 \
   printf ( "Error... etc");                      \
}

main()
{
   MY_WRAPPER ( some_function_call, 0, arg1 , arg2 , arg3 ); 
}

```

;)

---

### Post by Compyx on 2010-04-09
> **Sporkman said:**
> ```

#define MY_WRAPPER(FCNNAME,OKRET,ARG1,ARG2,ARG3)  \
if ( FCNNAME (ARG1,ARG2,ARG3)!=OKRET )            \
{                                                 \
   printf ( "Error... etc");                      \
}

main()
{
   MY_WRAPPER ( some_function_call, 0, arg1 , arg2 , arg3 ); 
}

```

;)

Heheh, indeed :)

---

### Post by mesuhas_sit on 2010-04-09
Tanx for the reply people.... looks like not a easy way to implement this... 
I am using some of the things like DEBUG_ON but just thinking of a easier way to get the information...

Tanx

---

