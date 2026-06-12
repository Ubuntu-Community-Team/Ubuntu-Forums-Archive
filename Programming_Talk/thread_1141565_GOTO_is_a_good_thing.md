---
title: "GOTO is a good thing"
date: 2009-04-28
forum: Programming Talk
---

### Post by soltanis on 2009-04-28
Goto is great for skipping to common sections of code, killing loops, and hell, going somewhere you want to be. Sure, you could do it with flow control statements, and you could also end up getting a mess of temporary variables and flags and nested conditionals, which end up making your code just as hard to read.

And sure, goto makes code difficult to follow, right, just as I'm sure I could make code hard to follow with just about any flow control statement in a given language.

Who's with me on this?

---

### Post by stevescripts on 2009-04-28
well, when there is *NO* other option, GOTO can be a life-saver, that said,

I generally tend to agree with avoiding GOTO at all costs:

[http://en.wikipedia.org/wiki/Goto#Criticism_of_goto_usage](http://en.wikipedia.org/wiki/Goto#Criticism_of_goto_usage)

Just my $.02...

---

### Post by grepgav on 2009-04-28
I would have to disagree with you. Every once and a while a GOTO may be necessary to avoid a really messy solution, but usually the need for a GOTO statement means the program structure needs to be redesigned.

> **soltanis said:**
> Goto is great for skipping to common sections of code, 

A common section of code should really just be a function, method, or subroutine then, no GOTO required and it's easier to read.

> **soltanis said:**
> killing loops,

"killing loops" should happen based on pre/postconditions, checked by the loop structures. That is essentially what you would be doing with a GOTO, but its not as apparent to anybody else who looks at your code.

> **soltanis said:**
> and hell, going somewhere you want to be. 

Not sure what you are getting at here, but with control flow and functions you can pretty well define what the program should be executing without arbitrarily jumping to somewhere else.

---

### Post by Drone022 on 2009-04-28
> the need for a GOTO statement means the program structure needs to be redesigned.

I have never used a GOTO statement in any program I've ever written and I'm not afraid to say it. :D

oh wait....assembly jumps, same thing right?

---

### Post by grepgav on 2009-04-28
> **Drone022 said:**
> I have never used a GOTO statement in any program I've ever written and I'm not afraid to say it. :D

oh wait....assembly jumps, same thing right?

Yeah I have not needed to use a GOTO statement since I used BASIC. I would like to see what an assembly program would look like without jumps :)

---

### Post by CptPicard on 2009-04-28
> **grepgav said:**
> 
"killing loops" should happen based on pre/postconditions, checked by the loop structures.


With perhaps the exception of an occasional break or continue statement... I find them useful sometimes.

---

### Post by grepgav on 2009-04-28
> **CptPicard said:**
> With perhaps the exception of an occasional break or continue statement... I find them useful sometimes.

Yeah I have come across situations like this on occasion when there is some exceptional case in the middle of loop execution. 

I still try and avoid them but I know what you mean, sometimes they are just the solution to the problem.

---

### Post by simeon87 on 2009-04-28
> **grepgav said:**
> Yeah I have come across situations like this on occasion when there is some exceptional case in the middle of loop execution. 

I still try and avoid them but I know what you mean, sometimes they are just the solution to the problem.

Break and continue statements are fine as they merely change the existing flow, goto is not as it almost instantly creates spaghetti code.

---

### Post by jimi_hendrix on 2009-04-28
wow...no it is not

while it can come in handy once in a blue moon, it is not good to use regularely...too hard too follow and too easy to make a bug with

---

### Post by Npl on 2009-04-28
goto is very usefull if you have to deal with lots of errors in plain C and you cant just return after a error, but need cleanup. Think of C++-Exceptions, but done with jumps instead.

Without goto, the code would end up having a crazy amount of nested if/else conditions and duplicated code for cleanup in case of errors. In short it would be hard to read and maintain.. using goto makes for cleaner and easier readable code in that case.

You will see code like this often if you deal with opening and reading from files for example:
```

success = false;
allocate A
<do something>
if(fail1)
  goto endA;
<do something>
...
if(fail4)
  goto endA;
<do something>
allocate B
if(fail5)
  goto endB;
<do something>
.
.
.
if(fail10)
  goto endB;
// no errors encountered
success = true;

endB:
close/deallocate B

endA:
close/deallocate A

return success;
```
I challenge you to bring this in a more readable form without gotos.

---

### Post by Yacoby on 2009-04-28
> **Npl said:**
> You will see code like this often if you deal with opening and reading from files for example:

[cut]

I challenge you to bring this in a more readable form without gotos.
functions?

---

### Post by Npl on 2009-04-28
> **Yacoby said:**
> functions?You want to pass all local variables down?

---

### Post by Can+~ on 2009-04-28
> **Npl said:**
> You want to pass all local variables down?

Arrays? 

I mean, fail1..10 are expressions that eventually are reduced to a boolean (true or false), you could perfectly do a bool[] and hand the pointer.

[PHP]#include <stdio.h>
#include <stdbool.h>

bool failTest(bool *fail)
{
	bool errorfound = false;
	int i=0;	
	
	for (; i < 10; i++)
		if (fail[i])
		{
			fprintf(stderr, "Error at condition %d", i);
			errorfound = true;
			break;
		}
	
	return errorfound;	
}


int main(int argc, char **argv)
{
	bool fail[10] = {1 == 2, 0, 0, 3 == 1, 5 < 2, 1, 0, 0 == 3, 0, 0};
	
	failTest(fail);
	
	
	return 0;	
}[/PHP]

(Notice that this function has no real purpose and makes no sense in terms of produced results)

---

### Post by Namtabmai on 2009-04-28
> **Can+~ said:**
> Arrays?

struct would be a more flexible choice.

---

### Post by Simian Man on 2009-04-28
```

int func( ) {
   /* local function */
   int end(code) {
     if A, deallocate A
     if B, deallocate B
     return code;
   }

   allocate A
   <do something>
   if(fail1)
      return end(FAIL);
   <do something>
   ...
   if(fail4)
      return end(FAIL);
   <do something>
   allocate B
   if(fail5)
     return end(FAIL);
   <do something>
   .
   .
   .
   if(fail10)
      return end(FAIL);

   // no errors encountered
   return end(SUCCESS);

```

Closures FTW!

---

### Post by Reiger on 2009-04-28
> **Npl said:**
> goto is very usefull if you have to deal with lots of errors in plain C and you cant just return after a error, but need cleanup. Think of C++-Exceptions, but done with jumps instead.

Without goto, the code would end up having a crazy amount of nested if/else conditions and duplicated code for cleanup in case of errors. In short it would be hard to read and maintain.. using goto makes for cleaner and easier readable code in that case.

You will see code like this often if you deal with opening and reading from files for example:
```

success = false;
allocate A
<do something>
if(fail1)
  goto endA;
<do something>
...
if(fail4)
  goto endA;
<do something>
allocate B
if(fail5)
  goto endB;
<do something>
.
.
.
if(fail10)
  goto endB;
// no errors encountered
success = true;

endB:
close/deallocate B

endA:
close/deallocate A

return success;
```
I challenge you to bring this in a more readable form without gotos.

Now, I do not know about C, but most higher level languages support some kind of

do {
[mess-up/succes]
}
while ([predicate: succes? -> continue; fail? -> drop out of the loop])
[clean-up]

Flow-control structure.

At any rate I would avoid Goto's in *any* managed language: it is usually the fastest way to an interpreter-crashin memory-leak. For instance, on TI 83/84 plus you could listen for user input like this (example from an actual program I once saw):
```

Label KCODE;
A = getKeyCode
If(A == 0)
Then
Goto KCODE
End

```
This does the following:
[list="1"]
[*]declare a label (obvious)
[*]branch
[*]Enter block scope (Then)
[*]Jump back to Label
[*]Exit block scope (End)
[/list]

With the 15Mhz or so processor and the 24Kb memory and the fact *all* data available to your BASIC program *must* be loaded in the 24Kb RAM (so there goes about 5Kb for even a simple program as the variables don't come cheap either); this thechnique will produce almost certainly an error within seconds. The message will be about that certain code could not be reached (namely the outermost End statements) due to lack of memory: for what happens is that you end up with stack overflow due to the recursive creation of Then/End blocks.

Equivalent code restructured to a simple loop:
```

K = 0
While(K == 0)
K = getKeyCode
End

```

Which runs in constant stack & memory size (and will happily run for hours).

---

### Post by cabalas on 2009-04-28
In the general case I try to avoid goto like the plague as I've found that it is a good indication that the [code smells]("http://en.wikipedia.org/wiki/Code_smell"), now I'm not saying there isn't a good legitimate use for goto - I just haven't found it yet.

Saying that I've always enjoyed this quote from Linus Torvalds:

> I _like_ using goto's every once in a while: it can often mess up the gcc optimizer just enough to get better code out of it.

For the life of me though I can't remember where I originally came across it.

---

### Post by scottuss on 2009-04-28
I've never had a problem with g....

---

### Post by samjh on 2009-04-28
> **scottuss said:**
> I've never had a problem with g....

I've never had a problem with g either.

Goto, on the other hand, is a pain in the ****.

There are three types of people who think that goto statements are good:
1. Programming novices who don't know enough to write good code, but know enough to make them dangerous.
2. Programmers who has only written textbook programs, or never had to maintain crap code written by others.
3. Die-hard assembly programmers from pre-1970s.

Frankly, the only times one should ever use goto or goto-like statements are:
- Assembly jumps.
- Loop break/continue when conditional tests produce more dangerous code.
- Switch breaks in some languages (some languages force the use of breaks in switch conditionals).

---

### Post by Reiger on 2009-04-28
> **cabalas said:**
> For the life of me though I can't remember where I originally came across it.

Almighty Google knows a possible source? [http://lkml.indiana.edu/hypermail/linux/kernel/9507/0475.html](http://lkml.indiana.edu/hypermail/linux/kernel/9507/0475.html)

---

### Post by cabalas on 2009-04-28
> **Reiger said:**
> Almighty Google knows a possible source? [http://lkml.indiana.edu/hypermail/linux/kernel/9507/0475.html](http://lkml.indiana.edu/hypermail/linux/kernel/9507/0475.html)

Yeah, I shouldn't have been so lazy and googled for it, I'll come up with a good excuse for it at some point.  That does look like it was the original source of it, but I think I found it on one of those page of linus quotes type things. 

Anyway thanks for hunting it down.

---

### Post by bluelamp999 on 2009-04-28
> **grepgav said:**
> Yeah I have come across situations like this on occasion when there is some exceptional case in the middle of loop execution. 

I still try and avoid them but I know what you mean, sometimes they are just the solution to the problem.

As a professional developer I have to agree with the above...

It would be lovely to redesign the loop/logic to preclude GOTOs but sometimes it's just the easiest (i.e. quickest) way to code for a particular situation.

Of course, try writing anything in Visual Basic without "On Error Goto ErrorHandlerThingy"

---

### Post by kpatz on 2009-04-28
I haven't used a goto in years.  In Visual Basic (original and .NET), C, C++, etc.

About the only time I can see using one is if you need to bail out of a deeply nested loop without exiting a function, a goto is the simplest/cleanest way to do it.  That said, I've never needed to even do that.

Any other use leads to spaghetti.

---

### Post by scottuss on 2009-04-28
> **bluelamp999 said:**
> As a professional developer I have to agree with the above...

It would be lovely to redesign the loop/logic to preclude GOTOs but sometimes it's just the easiest (i.e. quickest) way to code for a particular situation.

Of course, try writing anything in Visual Basic without "On Error Goto ErrorHandlerThingy"

Last time I used VB.net I didn't need to use any GOTO statements.. Needless to say I ditched using VB.net a long time ago!

---

### Post by lisati on 2009-04-28
If using ASM, I can't see a way to avoid goto-like statements on occasion. There are usually more elegant ways of doing things in a HLL.

In a similar discussion in these forums, I once came across a link to this page: [http://www.fortran.com/come_from.html](http://www.fortran.com/come_from.html)

---

### Post by slavik on 2009-04-28
So, what are we adding to this 20 year old discussion?

---

### Post by days_of_ruin on 2009-04-28
> **slavik said:**
> So, what are we adding to this 20 year old discussion?

This thread will officially once and for all decide whether GOTO
is good or evil. The InterwebZ are looking to us to decide.

---

### Post by bluelamp999 on 2009-04-28
> **scottuss said:**
> Last time I used VB.net I didn't need to use any GOTO statements.. Needless to say I ditched using VB.net a long time ago!

Of course, I should have pointed out earlier that one is referring to the venerable (and surprisingly prevalent in the "Real World") Visual Basic 6.0

---

### Post by samjh on 2009-04-29
> **slavik said:**
> So, what are we adding to this 20 year old discussion?

As much as most other dead horse discussion on this forum... absolutely nothing! :)

It's what forums are for, isn't it? ;)

On the topic of breaking out of loops, it reminds me of the basic loop structure in Ada, which is an everlasting loop:
```
loop
    Put_Line("This is a loop that never ends...");
end loop;
```
Within which the programmer adds an exit condition:
```
loop
    exit when Annoyance > 10;
    Put_Line("This is a loop that never ends...");
    Annoyance := Annoyance + 1;
end loop;
```
From whence more elegant derivatives are created...
```
for Annoyance in Integer 1..10 loop
    Put_Line("This is a loop that will inevitably end.");
end loop;
```
```
while Annoyance <= 10 loop
    Put_Line("This is a loop that should end somewhere.");
    Annoyance := Annoyance + 1;
end loop;
```

---

### Post by soltanis on 2009-04-29
I dunno. I suppose I'm fighting a losing battle here; but I can't shake the feeling that while conceptually yes, make a subroutine or a function, my sense of efficiency (don't pounce on me at once) is insulted. Calling another function means you're going to have to enter another execution frame and push the arguments to the function, then jump to the function, have it unload the arguments and then start doing things.

Well I suppose that's what inline functions are for (except of course in languages where convenient things like that don't exist).

I am really just frustrated that languages don't have Lisp macros, I suppose. Retyping code is one hell of a drag, and macros really solve that problem pretty efficiently. And in a non-inefficient way. GOTO seemed like the easy solution there.

Feel free to close the thread.

---

### Post by grepgav on 2009-04-29
> **soltanis said:**
> I dunno. I suppose I'm fighting a losing battle here; but I can't shake the feeling that while conceptually yes, make a subroutine or a function, **my sense of efficiency (don't pounce on me at once) is insulted. Calling another function means you're going to have to enter another execution frame and push the arguments to the function, then jump to the function, have it unload the arguments and then start doing things.**

Well I suppose that's what inline functions are for (except of course in languages where convenient things like that don't exist).

I am really just frustrated that languages don't have Lisp macros, I suppose. Retyping code is one hell of a drag, and macros really solve that problem pretty efficiently. And in a non-inefficient way. GOTO seemed like the easy solution there.

Feel free to close the thread.

Interesting argument... but at least stack operations are fast!

---

### Post by eye208 on 2009-04-29
> **soltanis said:**
> I dunno. I suppose I'm fighting a losing battle here; but I can't shake the feeling that while conceptually yes, make a subroutine or a function, my sense of efficiency (don't pounce on me at once) is insulted. Calling another function means you're going to have to enter another execution frame and push the arguments to the function, then jump to the function, have it unload the arguments and then start doing things.
If you require the same piece of code at several places in a program, how is GOTO supposed to help you? If you jump to a subroutine using GOTO, there is no return address to jump back to. Even if you write your program in assembly language, calling a subroutine means entering another frame of execution because the return address will be put on the stack.

If pushing function arguments on the stack seems inefficient to you, put your variables in a data structure or class object and pass it to the function via pointer or reference.

There's only one application of GOTO that makes sense: error handling in languages without exception support, such as C. For example, if you have a function with several nested loops, and an error occurs in the innermost loop, GOTO helps to quickly exit all the loops and jump to a piece of clean-up code before returning to the function caller. In C++ you would use *throw* and *try/catch* instead.

---

### Post by maheshjr2000 on 2009-04-29
> **cabalas said:**
> In the general case I try to avoid goto like the plague as I've found that it is a good indication that the [code smells]("http://en.wikipedia.org/wiki/Code_smell"), now I'm not saying there isn't a good legitimate use for goto - I just haven't found it yet.

Saying that I've always enjoyed this quote from Linus Torvalds:



For the life of me though I can't remember where I originally came across it.

Is g really that bad?

---

### Post by Marco A on 2009-04-29
.

---

### Post by Yacoby on 2009-04-29
> **Marco A said:**
> The weekend past writing a small program for processing images, I needed a routine to compute the Fourier Transform on a set of numbers.

On the Netlib repository I found a routine written in 1968 by R.C. Singleton.

[http://www.netlib.org/go/fft.f]("http://www.netlib.org/go/fft.f")

Now I understand why GOTOs are bad. Ug.

That code is horrible. If you were to translate it to c, most of it could end up in loops and/or inlined functions

```
   90 m=m+1
      nfac(m)=nfac(j)
      j=j-1
      if(j .ne. 0) go to 90

```

Which makes it a lot more readable due to indentation, and removing the random jumps which don't describe anything.
```

do{
      m+=1
      nfac(m)=nfac(j)
      j -= 1
}while ( j .ne. 0 )

```

> **Marco A said:**
> 
It's fast.  It does Fourier Transform on thousands of points quite fast.

That code it's full of goto's.

I doubt he could have made the algorithm so fast without them.

There aren't many good uses for goto, but there's the case it provides for efficiency in the special application.
Which is an assumption. It is quite possible that the compiler would compile the code with the loop, and the code with the goto to exactly the same thing.

---

### Post by eye208 on 2009-04-29
> **Marco A said:**
> That code it's full of goto's.
Of course it is. In 1968, IF and GO TO were the only way to control program flow in Fortran.

There was no ELSE, no END IF, no DO WHILE / END DO, no SELECT CASE. All these were introduced later.

---

### Post by ajackson on 2009-04-29
In my opinion (to stop anyone accusing me of portraying something as fact), there can be occasions where use of GOTO is OK **but** those are exceptions rather than the rule.

Where you can you should design your routines to avoid the use of GOTO. You could argue that the exception catching systems in a lot of languages are heavily masked GOTOs, maybe they are as in essence they do interrupt the flow like a GOTO does.

So is GOTO a good thing? Probably not but it should be avoided where possible (IMHO).

---

### Post by lisati on 2009-04-29
Surely the goal here is to encourage the writing of good code, whatever "good" might mean. This can include code that is easy to maintain, code that gets the job done efficiently, or even just code that gets the job done at least reasonably well.

Constructs like while/wend (or while/do, do/until or whatever syntax the language you're using demands) exist for the programmer's benefit, to help in the production of good code, without the pitfalls that "goto" can bring, even if the compiler produces output equivalent to a well-written loop using goto-like statements. Those of us who have maintained existing code would usually prefer spaghetti on our dinner plates, not on the screen.

---

### Post by CptPicard on 2009-04-29
> **soltanis said:**
> my sense of efficiency (don't pounce on me at once) is insulted. Calling another function means you're going to have to enter another execution frame and push the arguments to the function

Wow... an extreme case of "premature optimization" there. Programming languages are there as conceptual tools. If we were to follow this kind of reasoning, I guess we would never get anywhere beyond designing specialized logic circuits. But I guess some people just can't see beyond aggressive minimization of constant factors in the running time...

Interesting that you would refer to Lisp macros though right afterwards...

EDIT: One of the few really good pro-GOTO arguments I've ever read is the implementation of state machines. Also, from the functional-programming perspective, it is instructive to consider that continuations are essentially a form of functional GOTO...

---

### Post by raydeen on 2009-04-29
I haven't used a GOTO for anything since my days in Atari BASIC and GW BASIC and then it was only for running the main loop of the program. DO/WHILE/WEND wasn't there (or I never learned it until later). Anything else was a subroutine or BREAK/END statement based on a condition.

Friends don't let friends use GOTO.

---

### Post by eye208 on 2009-04-29
Out of curiosity, I sent these two samples through GCC:
```
int main() {
        int a, b;
        a = 0;
        for (b = 0; b < 10; b++) a += b;
        return a;
}
```
```
int main() {
        int a, b;
        a = 0;
        b = 0;
        goto label2;
label1:
        a += b++;
label2:
        if (b < 10) goto label1;
        return a;
}
```
The assembly output generated by GCC was exactly the same:
```
main:
        leal    4(%esp), %ecx
        andl    $-16, %esp
        pushl   -4(%ecx)
        pushl   %ebp
        movl    %esp, %ebp
        pushl   %ecx
        subl    $16, %esp
        movl    $0, -12(%ebp)
        movl    $0, -8(%ebp)
        jmp     .L2
.L3:
        movl    -8(%ebp), %eax
        addl    %eax, -12(%ebp)
        addl    $1, -8(%ebp)
.L2:
        cmpl    $9, -8(%ebp)
        jle     .L3
        movl    -12(%ebp), %eax
        addl    $16, %esp
        popl    %ecx
        popl    %ebp
        leal    -4(%ecx), %esp
        ret
```
Even after changing the compiler optimization level, there was no difference between the results. At level 3, GCC removed the loop and precalculated the return value in both cases. I think it is safe to assume that GOTO provides no performance advantage at all, as far as GNU C/C++ is concerned.

---

### Post by soltanis on 2009-04-29
> **CptPicard said:**
> Wow... an extreme case of "premature optimization" there.

I've been told this is bad. Bottlenecks, indeed, appear in places where you least expect them.

> **CptPicard said:**
> 
Interesting that you would refer to Lisp macros though right afterwards...

This post was motivated by my frustration with rewriting the same statement in the handling section of a branching conditional in Python. If Python had goto, it would've shortened my typing by a meager amount.

If Python had lisp macros, it would've been...a lot shorter.

---

### Post by Can+~ on 2009-04-29
> **soltanis said:**
> This post was motivated by my frustration with rewriting the same statement in the handling section of a branching conditional in Python. If Python had goto, it would've shortened my typing by a meager amount.

If Python had lisp macros, it would've been...a lot shorter.

Maybe you should've started the thread there; like "Is there a better way of doing ______?".

And who cares about memory consumption anyway? I mean, trying to save every single bit of space using primitive syntax is not better, optimization is applied where it's due and as late as possible.

---

### Post by soltanis on 2009-04-29
That would've been a good idea. I disagree with you on the subject of memory consumption, though, even though it has nothing to do with my problem (my problems were laziness and hubris, which as it turns out are actually virtues). Memory isn't free, programmers should at least acknowledge this fact when they're writing their applications.

---

### Post by simeon87 on 2009-04-29
> **soltanis said:**
> That would've been a good idea. I disagree with you on the subject of memory consumption, though, even though it has nothing to do with my problem (my problems were laziness and hubris, which as it turns out are actually virtues). Memory isn't free, programmers should at least acknowledge this fact when they're writing their applications.

I think the point is that readability and maintainability of the code should not be sacrificed for a small memory gain. In many situations memory usage isn't critical which allows the developer to write the code in a more readable way and the application still does what it needs to do.

---

### Post by Simian Man on 2009-04-29
> **soltanis said:**
> This post was motivated by my frustration with rewriting the same statement in the handling section of a branching conditional in Python. If Python had goto, it would've shortened my typing by a meager amount.

But Python does have closures.  Everybody ignored my solution to this problem, but it is, in my opinion, the cleanest solution to this problem and one that I use myself in C, Ocaml and Python all the time.

---

### Post by Can+~ on 2009-04-29
> **soltanis said:**
> Memory isn't free, programmers should at least acknowledge this fact when they're writing their applications.

And I acknowledge that fact, and realize that there's no point on sacrificing that amount of readability in goto() instead of using a function.

I choose easy to understand code than fast code any day of the week, if I were a developer of heavy duty or very specialized algorithms I would favour speed over readability, usually optimizing/changing algorithms rather than saving every bit with tricks like this.

---

