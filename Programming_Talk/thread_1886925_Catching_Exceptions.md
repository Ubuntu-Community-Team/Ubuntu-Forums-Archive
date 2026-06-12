---
title: "Catching Exceptions"
date: 2011-11-25
forum: Programming Talk
---

### Post by robotz421 on 2011-11-25
I would be very appreciative if someone could tell me how to fix this program.  It is supposed to trap the divide by zero error every time through the loop, but instead it only traps once and on the second iteration of the loop it crashes with a floating point error.  If you could post corrected code it would probably avoid any need for follow up questions.  Here is the program:

```

#include <signal.h> 
#include <stdio.h>
#include <stdlib.h>
#include <setjmp.h>

using namespace std; 

jmp_buf return_to_top_level;

void termination_handler(int signum)
{
    longjmp (return_to_top_level, 1);
}
 
int main() 
{
    struct sigaction new_action;

    // Set up the structure to specify the new action.
    new_action.sa_handler = termination_handler;
    sigemptyset(&new_action.sa_mask);
    new_action.sa_flags = 0;

    int x,y;

    for( x = 0; x < 10; x++ )
    { 
        if (sigaction(SIGFPE, &new_action, NULL ) == -1 )
        {
            printf( "Could not set signal handler for SIGFPE\n" );
            exit( -1 );
        }

        if (setjmp( return_to_top_level ))
            puts ( "Back at main loop....\n" );
        else
        {
            puts( "About to divide by zero\n" );
            y = 1/0;
        }
    }

    exit( 0 ); 
} 

```

---

### Post by ziekfiguur on 2011-11-26
Don't use stdlib.h, stdio.h or any kind of jump in C++, in C++ use cstdlib, iostream for I/O and exceptions for error catching.
The code you have is C, you should remove the line with `using namespace std;' and compile with gcc
Also, you should read the manual for setjmp, it states: "The stack context will be invalidated  if  the  function  which  called setjmp() returns."
So, you will have to reinitialize return_to_toplevel.
Note though that jumps in most languages including C are considered A Bad Thing and should generally be avoided if at all possible.

---

### Post by robotz421 on 2011-11-26
Thanks for your response.  Lol, yes I have a habit of mixing C and C++.  It comes from learning programming back in the 80s before there was such a thing as C++, or at least it was not well known.  I have never had any problems with it before.  However I did as you suggested and removed the namespace line, renamed the file from main.cpp to main.c and recompiled.  I got the same results.

The function which calls setjump here is main and it does not return until the program ends.  I believe I am reinitializing return_to_top_level every time through the loop when I call setjump( return_to_top_level ) am I not?

Yes I know jumps are considered bad, I have even read "Gotos considered harmful" (google the phrase if you don't know it, some interesting computing history there.)  However if I explain what I am trying to do I think you will understand the need for it:  I am trying to write a language interpreter that will allow the user to make mistakes and recover gracefully, print an error message and go back into the interpret loop.  Many language environments need to do this.

I have tried to use exceptions for catching errors but some errors, such as floating point errors, don't seem to be caught by try/catch blocks under Ubuntu (and presumably other Linuxes.)  Instead they send a signal to the program and the default behavior is to end the program with an error message.  Exceptions were my original approach but I think I am going to have to use both approaches to catch all of the errors.

If you know how to catch a floating point error in a try/catch block, or have any other thoughts I would be happy to hear them.

---

### Post by trent.josephsen on 2011-11-26
Okay, first question:  are you going to use C or C++?  Pick one and use it right; don't mix them up, you're just asking for trouble.

If you're dead set on using an exception-handling model, C++ will be a better choice.  If you want to use C, it's generally going to be far easier and cleaner to do error checking instead.  setjmp/longjmp aren't designed for complicated stuff, and they're the most powerful tool for exception handling available in C.

---

### Post by robotz421 on 2011-11-26
Well if you force me to choose between C and C++ I will pick whichever one makes it easier to solve this problem although I am not sure which one that is so I'll let you choose if you know a solution.   Just as an aside, most C++ compilers I have used seem quite happy to compile a mixture of the two and in many years of programming I have never run into a problem that could be pinned down to mixing them but I am not against code purity if you insist.  I don't want to have to resort to error checking because it would involve adding a large amount of code and testing/debugging/maintaining it all as well as slowing down program execution by a large factor for simple operations. 

Just so we are not confusing ourselves, exception handling ( i.e. try/catch blocks) in Ubuntu does not seem to be meant to catch the kinds of errors I am referring to here ( floating point errors, dereferencing null pointers, etc., essentially most things that would normally crash the program) unless there is something about them that I don't know about.  My original program (not the example I posted here) does all of the problematic stuff within try/catch blocks but the program (or probably more correctly, the operating system) just merrily sends FPE or whatever signals that kill the program instead of transferring control to the catch block.  MSVC as I understand it does trap these kinds of errors in catch blocks which is a method I much prefer but I am not ready to go to the dark side yet.  What we are talking about here is more signal handling than exception handling (unless we can change that somehow), and I apologize for getting the title wrong in my first post.  The exception handling mechanism may be useful however, if it can be pressed into service.

---

### Post by trent.josephsen on 2011-11-26
> **robotz421 said:**
> Well if you force me to choose between C and C++ I will pick whichever one makes it easier to solve this problem although I am not sure which one that is so I'll let you choose if you know a solution.
When your job is driving a screw, I shouldn't have to force you to choose between using a hammer or a screwdriver.  However, you certainly shouldn't try to use them both at once.

> Just as an aside, most C++ compilers I have used seem quite happy to compile a mixture of the two
Well, yeah, but that doesn't mean you *should*.  Compilers will also happily let you name your variables after food, but try maintaining a thousand lines of code that looks like
```
qsort(eggplant, spinach, bacon, pancake);
```
and you'll soon understand the importance of writing code that follows more rules than just the ones imposed by a compiler.

Floating point errors and null pointer dereferencing are exactly the kind of thing C *isn't* designed to handle gracefully.  Both invoke undefined behavior and you're playing with fire to assume otherwise.  Your options, standard-wise, are error checking or some other language.  C++?  I wouldn't feel comfortable speaking as if I were an expert; maybe somebody else can shed some light.

You sure you're not looking for Java?

---

### Post by GeneralZod on 2011-11-26
One area in particular where C and C++ don't play nicely together is (surprise!) with setjmp and longjmp: longjmp does not perform the destruction of automatic objects as it jumps back up the stack (whereas C++ exceptions do), which is very probably Undefined Behaviour (Edit: yep - 18.7.4).

---

### Post by robotz421 on 2011-11-26
Okay, let's forget about the mixed code thing and assume we are writing  in C XOR C++ before we lose sight of the point of the thread.  I would  like to stay with one of the two since they are the most efficient  languages when compared with options like Java, hotspot compiling  notwithstanding, and, although I can code in Java, I really don't like  it (been that way ever since I saw a hello world program and noticed the  number of qualifiers before the main routine.)  Most of my code is  already completed so I would really like to avoid porting it.  What I would like is a small example program, something like the one I  posted, but which successfully generates and catches a floating point  exception multiple times.  I realize I am trying to do something a  little out of the ordinary here but I think it can be done.

Here is another idea: I simplified my code down to where there was nothing in the signal handler so all it does is return, and removed the for loop from main and replaced with just y = 1/0;

By single stepping the program I found that when division is executed,  the handler is called, but oddly enough, it returns to the division  operation instead of after it so that the division is executed again,  calling the handler and we have an infinite loop.  There is no setjmp or longjmp in this code so that is not an issue.

Now I have been doing some searching on the web and I found this code for a handler:

```

void catch_fpe(int sig, int code, struct sigcontext *scp) 
       { 
                 scp->sc_pc += INSTRUCTION_SIZE; 
                 caught_fp_exception = 1; 
       }

```The idea here is that we change the sigcontext a little before we  return, allowing the program to continue by moving the program counter  forward past the y=1/0; line.  Now if we also set a flag variable in the  handler to indicate an error had occurred, we could put some code to  check it and repair the problem following the division in the main  routine.

The problem with this code is that it won't compile on  my system.  The compiler says that scp doesn't have an sc_pc field.   Apparently this code is from a different POSIX environment.  I have  looked through the definition of struct sigcontext on my machine but it  doesn't have anything that looks obviously like a program counter to  me.  I am wondering if this idea can be modified to work on my  machine.

Now anticipating objections, I realize that modifying the program counter is highly unorthodox and I would prefer a solution using a longjmp or a try/catch block.
[FONT=monospace]

[/FONT]

---

### Post by trent.josephsen on 2011-11-27
[QUOTE=sigaction(2)]
       According  to  POSIX,  the  behavior of a process is undefined after it
       ignores a SIGFPE, SIGILL, or SIGSEGV signal that was not  generated  by
       kill(2)  or  raise(3).   **Integer division by zero has undefined result.**
       On some architectures it will generate a SIGFPE signal.  (Also dividing
       the  most  negative  integer by -1 may generate SIGFPE.)  [B]Ignoring this
       signal might lead to an endless loop.[/B][/QUOTE]

Basically, you're seeing expected behavior for an architecture where integer division by zero generates SIGFPE (which isn't guaranteed even by POSIX).  Any attempt to fix this in a standards-compliant way that doesn't start with error checking is doomed.

One way to "fix" this with minimal code re-writing is to assert() the denominator before every expression that could divide by zero.  (If you are really determined you could even try to recover from that by handling SIGABRT, but I don't know if that would avoid the problems you're facing -- probably not.)

---

### Post by robotz421 on 2011-11-27
Actually I am not ignoring the signal, I am trapping it (this is my current approach anyway) which is different.  Also I am not trying to fix this in a standards compliant way.  Any way that works on my machine will be fine by me. 

You are aware that assert() generates a message and then aborts the program?  It's a great tool for debugging but would be shooting yourself in the foot if your goal is to keep the program running.  

I found this [http://www.glenmccl.com/ansi_032.htm](http://www.glenmccl.com/ansi_032.htm) page which talks about signal handling and has this to say:

>  In C++ Newsletter issue #015 it was mentioned that C++ exceptions are not related to operating system signals.  In other words, if an operating system signal occurs (such as an attempt to reference an invalid address, or an interrupt keystroke from the terminal running the program), it will not be mapped into a C++ exception; rather, the signal will have to be handled by the techniques described in the C standard library, which is included by reference into the C++ standard library.  These C standard library techniques are defined by the <signal.h> header (which becomes header <csignal> in the C++ standard library). 

so the C/C++ distinction is moot on the point of signal handling, it's all the same stuff.

---

### Post by trent.josephsen on 2011-11-27
I've done my best.

---

### Post by robotz421 on 2011-11-27
Thanks for your replies.  I still think it can be done and am not giving up yet.

---

