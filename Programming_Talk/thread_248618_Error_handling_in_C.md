---
title: "Error handling in C"
date: 2006-09-01
forum: Programming Talk
---

### Post by scourge on 2006-09-01
As any decent C programmer knows, error handling in C is a bitch, thanks to the absense of exceptions. My current project has now reached the state called "It works perfectly if you use it right", and I'd like to take the next step.

So my first question is, how strictly should I check the return codes of library functions? I know that the 6th commandment for C programmers is
> If a function be advertised to return an error code in the event of difficulties, thou shalt check for that code, yea, even though the checks triple the size of thy code and produce aches in thy typing fingers, for if thou thinkest ``it cannot happen to me'', the gods shall surely punish thee for thy arrogance.

It makes perfect sense to me, but the problem is that obeying it increases the size of my code significantly, makes the code harder to read, and yeah, produces aches in my typing fingers. So should I really check for ALL return codes, including functions such as printf? And what should I do when I encounter an error, short of printing the error description and exiting that is? Currently I only check for malloc errors (and exit if they happen), and file opening/writing errors (which I handle without exiting the program). In many cases there's nothing that my program could do to fix the problem that caused the error, so it seems like I should just write my own wrappers for the basic functions. Or am I wrong?


I've also got another question unrelated to error handling: should I avoid delarations in the middle of a block and in for/while statements? I use C99 which allows this, but almost everyone still seems to delare variables only in the beginning of a block a la C89, even if the code is otherwise incompatible with C89.

Thanks in advance.

---

### Post by JonahRowley on 2006-09-02
Yes, error handling in C is very tedious.  As a rule, I check return values on all IO (except printf to stdout or stderr), all library (libc or other) functions with any argument originating from any user input, and any memory operations (mostly malloc).  Yes, this bloats the code.  No, it doesn't make anything fun.

C is too tedious for me to seriously use anymore.  C++ has many facilities to make these problems go away (abstractions and exceptions), or abandon compiled languages altogether and learn a real programming language like Ruby.

The real problem is what to do when you find an error.  Sometimes it's recoverable.  If the user has supplied invalid data, you can recover from that.  The problem is unrolling all the things you've done since beginning with this user data.  This is where exceptions, scope, destructors and auto_ptr comes in handy.  Unfortunately, C has none of these things (well, scope, but only for variable naming).  For complex functions, I use something like the code below (and yes, it uses goto, don't freak out or anything).  It's particularly well-suited for functions that allocate many resources (files, memory, etc).

```

int some_func() {
  if(operation1())
    goto operation1_failed;
  if(operation2())
    goto operation2_failed;
  ...

  return something_the_called_wanted;

/* Note:  These are in reverse order */
operation2_failed:
  /* Free resources allocated by op2 */
operation1_failed:
  /* Free resources allocated by op1 */

failed:
  return something_bad;
}

```

It's reasonably elegant and "unwinds" complex operations well.  Don't let that goto scare you away, there really are acceptable uses of goto if used carefully.

The convention of declaring variables at the top of the block is a good one.  Don't make the reader hunt for that declaration.  For random temp variables needed in very localized places in a function, I often make a "naked" block to contain them.  Something like this:

```

int some_func() {
  int x;
  char* y;
  
  ...
  {
    /* Naked block with some temp variables
     * they will go out of scope at the end of the block */
    int a, b;
    unsigned char c, c2;
    char* p1, p2;
    /* Some ugly piece of code needing all these variables */
  }

  return something;
}

```

The complex action doesn't dump 50 temp variables into the variable declarations, and still has its own variables.  Sometimes, things like this can really help in code readability.

---

### Post by LordHunter317 on 2006-09-02
> **JonahRowley said:**
>  or abandon compiled languages altogether and learn a real programming language like Ruby.Seeing as C can be interpreted and Ruby compiled, this is a non-sequitur.

> This is where exceptions, scope, destructors and auto_ptr comes in handy.  Unfortunately, C has none of these things (well, scope, but only for variable naming).You need to go read up on scope again.  You're confusing the scope of a variable with the lifetime of a variable.  C variables on the stack have the lifetime of the enclosing function, and C variables on the heap are alive until they are specifically deallocated.

> It's particularly well-suited for functions that allocate many resources (files, memory, etc).As a rule, this means your function are substantially too complicated.  You want to limit resourced handled by a function to the bare minimum possible.

Well, that's a lie.  You want to limit the kinds of error conditions that can happen to the bare minimum possible.  This usually means dealing with as few resources as possible.  This also means writing multiple functions around dealing with the resources, to localize the error handling.

In C, it's vitally important for functions to be idempotent.  That means they have no side-effects.  Unfortunately, C is usually too limited to ensure that in many cases.  In which case, you want to limit a function to have as few side effects as possible.

What makes life easy in C is just simply to die whenver you hit a fatal condition.  You can use atexit() to cleanup things that must be cleaned up at shutdown time, but note that many C library implementations are buggy and racy in this situations.  Calling exit() from a signal handler or threaded code in this case may be dangerous depending on the resource being cleaned up.

> The convention of declaring variables at the top of the block is a good one.Err nonsense.  If that were true, C99 would have not **added that ability.**  Declare variables as close as possible to their first usage, if not at their first usage.

> Don't make the reader hunt for that declaration.This means your function is too big.  Make it smaller.

---

### Post by scourge on 2006-09-02
Big thanks to both of you for the replies. It seems that these things aren't obvious even to some more experienced programmers, so I'm glad I posted about it here.


> As a rule, I check return values on all IO (except printf to stdout or stderr), all library (libc or other) functions with any argument originating from any user input, and any memory operations (mostly malloc). Yes, this bloats the code. No, it doesn't make anything fun.


That makes sense, and it's pretty much what I also do: carefully check all user input, never use unsecure functions like gets, and always check that mem allocation works as expected.


> ...It's reasonably elegant and "unwinds" complex operations well. Don't let that goto scare you away, there really are acceptable uses of goto if used carefully.

I don't think I like that code sample too much. I do have one goto in my current project, but it's there only because it's faster and actually makes the function more readable. In the vast majority of cases I'd want to avoid goto. Here's how the same thing could be done without goto:

```
int some_func() {
  if(operation1())
    return error_code_1;
  if(operation2())
    return error_code_2;
  ...

  return 0;
}

return_code = some_func();
if return_code {
  if return_code >= error_code_2)
    /* Free resources allocated by op2 */
  if return_code >= error_code_1)
    /* Free resources allocated by op1 */
  return something_bad;
}

```


> Err nonsense. If that were true, C99 would have not added that ability. Declare variables as close as possible to their first usage, if not at their first usage.

That's what I'm doing now, mainly because it gives me better performance. But splint doesn't accept it, so to debug my code with it I'll have to keep the declarations in the beginning of the block. Are there better tools than splint for statically checking my source code?

---

### Post by LordHunter317 on 2006-09-02
> **scourge said:**
> Here's how the same thing could be done without goto:No, it cannot.

Your style doesn't work for something like this:```
void func()
{
    FILE *fp = fopen("somefile", "r");
    
    if (NULL != fp) {
            char *foo = malloc(BUFSIZ);
    }
}
```Not only would the resources be *inaccessible* even if we returned errors to the calling function, the resources to clean up are inclusive, not exclusive.  If fopen() fails, we have to clean up nothing.  If malloc() failes, we have to close the fp.  If malloc() succeeds, we have to cleanup **both**.  Your code fails to do that.  

Resource cleanup is never exclusive, so if() conditional constructs are insufficent.  

> That's what I'm doing now, mainly because it gives me better performance.No, it shouldn't.  Being able to declare variables at arbitrary places in the function should have no impact on performance.  The compiler should still be allocating all the space required by the function at the entry point.

---

### Post by scourge on 2006-09-02
> Your style doesn't work for something like this:...

You're right of course. I admit to writing my previous post in haste. I was thinking about cleaning up junk that is passed to other functions via pointers. Closing fps and such is easy, and I immediately do that when the fp isn't used anymore. The same applies to the simple malloc'd stuff that I don't have to keep in memory longer than the function call is alive.


> No, it shouldn't. Being able to declare variables at arbitrary places in the function should have no impact on performance. The compiler should still be allocating all the space required by the function at the entry point.

Okay. So the only reason to declare variables close to their first use is readability of the code? In that case I think I'll keep the declarations in the beginning of blocks so that splint would work. I don't have a big number of declarations in any function so readability shouldn't really suffer.

---

### Post by LordHunter317 on 2006-09-02
> **scourge said:**
> Closing fps and such is easy, and I immediately do that when the fp isn't used anymore. The same applies to the simple malloc'd stuff that I don't have to keep in memory longer than the function call is alive.The issue isn't the normal, but abnormal case.  Cleaning up stuff when it's life time normally ends is easy.  Cleaning up stuff when lifetime is abnormally ended is hard if it isn't handled for you.

> Okay. So the only reason to declare variables close to their first use is readability of the code?In C?  Yes.  But don't neglect proper scoping.

---

### Post by JonahRowley on 2006-09-02
> **LordHunter317 said:**
> 
```
int some_func() {
  if(operation1())
    return error_code_1;
  if(operation2())
    return error_code_2;
  ...

  return 0;
}

return_code = some_func();
if return_code {
  if return_code >= error_code_2)
    /* Free resources allocated by op2 */
  if return_code >= error_code_1)
    /* Free resources allocated by op1 */
  return something_bad;
}

```


Now I don't like this at all.  What you've done is take cleanup out of the function that should be cleaning it up and it's now a burden of the caller.  This means repeating cleanup code wherever you'll be calling some_func(), or wrapping some_func() in yet another function.  Seems pretty silly just to avoid a goto.  If you're really afraid of goto, use something like this.

```

int some_func() {
  int error = 0;

  if(op1()) {
    error = 1;
  }
  if( error == 0 && op2() ) {
    error = 2;
  }
  ...

  switch(error) {
  case 0:
    return something_good;
  case 2:
    /* Deallocate op2's resrouces */
    /* Fallthrough */
  case 1:
    /* Deallocate op1's resources */
  default:
    return something_bad;
  }

  /* You might need a bogus return statement here to supress a compiler warning */
}

```

I think that's horribly silly to avoid a goto.

As for breaking the function up, that doesn't always make sense.  Imagine a network program that also writes to a file and parses a URL from user input.  First operation, malloc a struct to hold the parsed data.  This can be abstracted with a function, but that has no bearing on this function.  Second operation, parse the user data and store it in the struct.  Third operation, open the socket and connect.  Fourth operation, open the file you'll be writing to.  Four operations, all of which can fail, none of which should be split into seperate functions.

---

### Post by LordHunter317 on 2006-09-02
> **JonahRowley said:**
> As for breaking the function up, that doesn't always make sense. It frequently does.

> This can be abstracted with a function, but that has no bearing on this function.Sure, it does.  It minimizes the amount of cleanup code required at the higher level and could *remove it competely*.  If you have to have the URL in order to perform the rest of the operation, then the code to present the parsed URL can exit() at will.  Cleanup code is greately reduced.

> Second operation, parse the user data and store it in the struct.This definitely should be seperate.  Here's why:[list][*]Not all of the memory required to read the input into buffers is required to parse the data.[*]None of the memory  (if any) required to do the parsing is required at the higher level.[/list]Proper resource management dictates both of those resources will be cleaned up before passing the parsed URL to the network code.  So, no, you're already quite quite wrong.

> Third operation, open the socket and connect.This process will have several resources that need to be cleaned up before you're really ready to connect to the server.  Proper handling of DNS and lookups and such requires transient resources totally irrelevant to actually reading data from the server and writing it to a file.

> Four operations, all of which can fail, none of which should be split into seperate functions.You'er totally wrong.  You haven't properly considered the scenario you've presented.

---

### Post by LordHunter317 on 2006-09-02
Also, as a note, I didn't post that code.  Please be more careful in your attributions in the future.

---

