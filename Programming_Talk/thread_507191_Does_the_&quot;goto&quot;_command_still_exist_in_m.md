---
title: "Does the &quot;goto&quot; command still exist in modern progranning languages?"
date: 2007-07-22
forum: Programming Talk
---

### Post by tc101 on 2007-07-22
I know it is bad programming practice, but does goto even exist in the newer languages such as python, ruby, java, lisp, PHP and so on?

I started out in COBOL 30 years ago and it was one of our main tools.  By the time I got into VB3 about 12 years ago I had read that it was better to avoid it most of the time.  As VB developed over the years everybody stopped using it, but it was still there.  Now, looking at python and ruby I don't even see it any more.  Does it still exist?

---

### Post by Eddie_B on 2007-07-22
Many people say goto is bad programming,  but in my opinion, it really isnt. Ive met many programmers who use it for convenience myself being one and its never let me down.. As for your question, im not sure of the answer..

---

### Post by Wybiral on 2007-07-22
It does in C++

```

#include <iostream>

using namespace std;

int main()
{
    int i = 0;

    some_label:
        cout << i << endl;
        i++;
    if(i<10) goto some_label;

    return 0;
}

```

Not sure why though... I've never ran into a situation where I've ever needed it in a higher level language.

---

### Post by pmasiar on 2007-07-22
Structured programming says you should have one entry point and one exit (so you can handle tasks needed to be done when exiting function in maintainable way). 

To exit loop in a special way you have 'continue' and 'break' statements, which go to beginning and end of the loop, accordingly, so you don;t need GOTO to move around a loop in an 'unstructured" fashion.

One special case when you needed to change your code workflow are exception - when error is detected, and this was the only responsible way to use GOTO before languages had exception handling. But all modern languages allow to define/handle exceptions, so there is no real usecase for old GOTO.

And it is also for the better: you cannot jump around your code flow, so code is maintainable and easier to debug.

That said, there are big differences how exceptions are handled in modern languages: ie Java requires checked exceptions (and famous Java expert Bruce Eckel arguments [Java does not need checked exceptions](http://www.mindview.net/Etc/Discussions/CheckedExceptions) and [C# does not need nor have them](http://www.artima.com/intv/handcuffs.html), which can easily become a pain in the neck and workaround to catch all exceptions (defeating the whole purpose of exceptions) are made. Compared to that, Python's exceptions are much more flexible: you can handle any exception on any level, and if not handled, it will "bubble up" to the caller, and ultimately to the top-level script, and will produce call stack trace if not handled there on runtime. So in pilot testing, you can write the code with handling only the most obvious errors, and add more handling on appropriate levels as you are finishing the code. Because as everybody knows, 80% of any program is proper error handling - with Python, you can write remaining 20% of the code first, and see main processing uncluttered with error handling.

Of course this is touchy topic and undoubtedly a major flamewar will ensue shortly on the topic of how useful are checked exceptions, to which I can tell only one thing: checked exceptions are exactly as good as static typing, if you like one you may like the other, and I prefer to avoid both :-) Two established experts explained why (in  articles linked above), and if someone does not accept *their* arguments, who am I to argument better than them?

Short answer: we don't have GOTO because we don't need it anymore: between exceptions and continue/break, all correct usecases are covered, and none of wrong usage is enabled.

---

### Post by hod139 on 2007-07-22
This should answer your question  :)

**[http://xkcd.com/c292.html](http://xkcd.com/c292.html)**

---

### Post by jfinkels on 2007-07-22
> **hod139 said:**
> This should answer your question  :)

**[http://xkcd.com/c292.html](http://xkcd.com/c292.html)**

Thank you for doing that so that I didn't  have to! :D

---

### Post by Smerity on 2007-07-23
I've only seen [goto in Python]("http://www.entrian.com/goto/") in one place, and that was as an April Fools joke =]

Honestly though mate, most of the higher level languages have much cleaner ways of handling code than having to resort to 'goto' - but I guess if you're so inclined =]

---

### Post by Geekkit on 2007-07-23
> **tc101 said:**
> I know it is bad programming practice, but does goto even exist ...

Yep it sure does. So does crack cocaine. Existence is not a valid endorsement for being acceptable.

---

### Post by gradedcheese on 2007-07-23
Hmm... take a look at almost any Linux driver, often their __init functions :)  You'll see a perfectly legitimate use of goto there.  Also note most of all your cute high-level constructs get turned into the equivalent of goto at the machine/assembly language level anyhow...

Here's an __init from the 8250 serial port driver:

```

static int __init serial8250_init(void)
{
    int ret, i;

    if (nr_uarts > UART_NR)
        nr_uarts = UART_NR;

    printk(KERN_INFO "Serial: 8250/16550 driver $Revision: 1.90 $ "
        "%d ports, IRQ sharing %sabled\n", nr_uarts,
        share_irqs ? "en" : "dis");

    for (i = 0; i < NR_IRQS; i++)
        spin_lock_init(&irq_lists[i].lock);

    ret = uart_register_driver(&serial8250_reg);
    if (ret)
        goto out;

    serial8250_isa_devs = platform_device_alloc("serial8250",
                            PLAT8250_DEV_LEGACY);
    if (!serial8250_isa_devs) {
        ret = -ENOMEM;
        goto unreg_uart_drv;
    }

    ret = platform_device_add(serial8250_isa_devs);
    if (ret)
        goto put_dev;

    serial8250_register_ports(&serial8250_reg, &serial8250_isa_devs->dev);

    ret = platform_driver_register(&serial8250_isa_driver);
    if (ret == 0)
        goto out;

    platform_device_del(serial8250_isa_devs);
 put_dev:
    platform_device_put(serial8250_isa_devs);
 unreg_uart_drv:
    uart_unregister_driver(&serial8250_reg);
 out:
    return ret;
}

```

---

### Post by eentonig on 2007-07-23
The main reason for not using GOTO, or considering it bad habit, are not because the machines can't handle it. But it's because it makes your code difficult te read by others.

And any decent programmer will know how horrible it is when you have to read someone elses code and it's a cluttered mess.

That's why, beside commenting, it's a good practice to build your code with one entry and one exit point. This way, someone else can read your code like a book. From front to cover.

---

### Post by Wybiral on 2007-07-23
> **gradedcheese said:**
> Hmm... take a look at almost any Linux driver, often their __init functions :)  You'll see a perfectly legitimate use of goto there.  Also note most of all your cute high-level constructs get turned into the equivalent of goto at the machine/assembly language level anyhow...

Here's an __init from the 8250 serial port driver:

```

static int __init serial8250_init(void)
{
    int ret, i;

    if (nr_uarts > UART_NR)
        nr_uarts = UART_NR;

    printk(KERN_INFO "Serial: 8250/16550 driver $Revision: 1.90 $ "
        "%d ports, IRQ sharing %sabled\n", nr_uarts,
        share_irqs ? "en" : "dis");

    for (i = 0; i < NR_IRQS; i++)
        spin_lock_init(&irq_lists[i].lock);

    ret = uart_register_driver(&serial8250_reg);
    if (ret)
        goto out;

    serial8250_isa_devs = platform_device_alloc("serial8250",
                            PLAT8250_DEV_LEGACY);
    if (!serial8250_isa_devs) {
        ret = -ENOMEM;
        goto unreg_uart_drv;
    }

    ret = platform_device_add(serial8250_isa_devs);
    if (ret)
        goto put_dev;

    serial8250_register_ports(&serial8250_reg, &serial8250_isa_devs->dev);

    ret = platform_driver_register(&serial8250_isa_driver);
    if (ret == 0)
        goto out;

    platform_device_del(serial8250_isa_devs);
 put_dev:
    platform_device_put(serial8250_isa_devs);
 unreg_uart_drv:
    uart_unregister_driver(&serial8250_reg);
 out:
    return ret;
}

```

In cases of maximum efficiency, yes, a programmer should be willing to get a little dirty... However, I think anyone who needs to write a driver like that should just do those portions in assembly anyway (the code would be just as readable and jumping around is perfectly normal in assembly).

But if you don't need to squeeze that much out of the code (if it's not a 3d simulation or a driver) then you should not be using goto in C or C++.

---

### Post by LaRoza on 2007-07-23
Some languages, like NASM only use goto like statements.

---

### Post by hod139 on 2007-07-23
> **gradedcheese said:**
> Hmm... take a look at almost any Linux driver, often their __init functions :)  You'll see a perfectly legitimate use of goto there.  Also note most of all your cute high-level constructs get turned into the equivalent of goto at the machine/assembly language level anyhow...

Here's an __init from the 8250 serial port driver:

<snip>


The question was if higher level languages use the goto command, not C or assembly.  Linux drivers are all written in C, which is not a higher level language.  In addition, the only reason to use a goto in C is because C has no exception handling built in (see pmasiar's post), and the only way to handle exceptions is with a goto statement.

---

### Post by LaRoza on 2007-07-23
> **hod139 said:**
> The question was if higher level languages use the goto command, not C or assembly.  Linux drivers are all written in C, which is not a higher level language.  In addition, the only reason to use a goto in C is because C has no exception handling built in (see pmasiar's post), and the only way to handle exceptions is with a goto statement.

Drivers are not all written in C. And C is an HLL.

---

### Post by hod139 on 2007-07-23
> **LaRoza said:**
> Drivers are not all written in C.

What other language (except assembly) is a linux driver written in?

> 
And C is an HLL.
This is debatable and depends on one's own definition of high level; but not worth hijacking the thread over.   It is considered low level because it provides many low-level capabilities, for example low-level access to memory and many instructions that relate directly to machine level instructions.  You, among others, may consider it a high level language simply because it is not machine code and is machine-independent.

For another example, many people do not consider C++ to be a high level language, they consider C++ to be a mid-level language because of its combination of high-level features and C's low level features.  A language like python would fit my description of high level.

---

### Post by LaRoza on 2007-07-23
> 
Linux drivers are all written in C,

Assembly
> **hod139 said:**
> 
A language like python would fit my description of high level.
C was designed as an HLL, so that is what I consider it.

---

### Post by pmasiar on 2007-07-23
> **LaRoza said:**
> Drivers are not all written in C. And C is an HLL.

I would hazard to guess that most of Linux driver code is C, with possibly small snippets of ASM here and there. For anyone competent enough in both C and ASM, C is just better way to write ASM code, and the only reason to dive deep into ASM is when you have bottleneck and want to optimize it, otherwise C is just fine in most cases (and faster to code).

Definition of [HLL](http://en.wikipedia.org/wiki/High-level_programming_language) depends of your value of "high" but most experts agree that [C](http://en.wikipedia.org/wiki/C_%28programming_language%29) was designed as systems programming language (specifically for writing UNIX), which is considered level just above ASM, and therefore "low" compared to other languages with "high" level features like automatic memory allocation etc. C lacks those - and for a reason.

If you consider C "high", what other language is lower? ASM does not count - ASM is mostly mnemonic for binary code. In my experience, all languages have higher concepts and less access to low-level hardware facilities than C.

Read about  [4GL](http://en.wikipedia.org/wiki/Fourth-generation_programming_language) - I used Progress a lot in '90, and let me tell you it is excellent language, *substantially* more productive for database apps than plain SQL. Still used BTW and they are still hiring :-)

---

### Post by LaRoza on 2007-07-23
> **pmasiar said:**
> 
If you consider C "high", what other language is lower? ASM does not count - ASM is mostly mnemonic for binary code. In my experience, all languages have higher concepts and less access to low-level hardware facilities than C.


At the time of its creation, it was HLL, that was in the 70's, so things have changed, of course.

---

### Post by pmasiar on 2007-07-23
> **LaRoza said:**
> At the time of its creation, it was HLL, that was in the 70's, so things have changed, of course.

C was never HLL, even in 1972. Real HLL languages (higher level than original C) around that time: [Algol68](http://en.wikipedia.org/wiki/Algol68), [Prolog](http://en.wikipedia.org/wiki/Prolog) (released '72), [Pascal](http://en.wikipedia.org/wiki/Pascal_%28programming_language%29). Mind you, these were mainstream languages. Prolog is still used (and available from Debian repository). Worth looking into, very different and interesting language BTW :-)

---

### Post by LaRoza on 2007-07-23
> **pmasiar said:**
> C was never HLL, even in 1972. 

I guess it depends on who you ask, one of my books refers to C as a HLL, of course, that book is on asm so maybe the perspective is different. All of my C books also consider C an HLL.

From wikipedia:
> 
Relative Meaning

Note that the terms "high-level" and "low-level" are inherently relative. Originally, assembly language was considered low-level and COBOL, C, etc. were considered high-level, as they allowed the abstractions of functions, variables and expression evaluation, and also that they had to be compiled to assembly before being compiled into machine code. Many programmers today might refer to C as low-level, as it still allows memory to be accessed by address, and provides direct access to the assembly level. For more on this distinction, see C2's page about high-level languages.


---

### Post by MianoSM on 2007-07-23
I miss GOTO. : (

---

### Post by gradedcheese on 2007-07-23
> 
In cases of maximum efficiency, yes, a programmer should be willing to get a little dirty... However, I think anyone who needs to write a driver like that should just do those portions in assembly anyway (the code would be just as readable and jumping around is perfectly normal in assembly).


No, Linux drivers can be compiled for any architecture that Linux can be compiled for.  That's one reason why they're written in C and not in assembly.  If you wrote parts of the driver in x86 assembly, it would be pretty useless on an ARM for example.   

Drivers like that one (almost every Linux driver contains at least a few 'goto' statements) are perfectly good code, I just cited it as a correct use of 'goto'.  That pattern is also pretty common in non-driver code where you need to initialize check and fail on a number of things, and failing out requires that you undo whatever you succeeded in doing beforehand.

---

### Post by Paul Miller on 2007-07-23
The thing about [FONT="Courier New"]goto[/FONT] is that it can make reading programs a lot like reading one of those *Choose Your Own Adventure* books.

In theory, the only control structures one really needs to write any program are [FONT="Courier New"]if[/FONT] and [FONT="Courier New"]goto[/FONT], and, as one or two previous posts have pointed out, in assembler, that's often all you get.  (Okay, most assembly languages give you some form of subroutine call as well, but that's actually just a specialized form of [FONT="Courier New"]goto[/FONT] that saves the stack.)

Here's an exercise:  Take a fairly small C program, say 500 lines or so, and replace all the [FONT="Courier New"]for[/FONT], [FONT="Courier New"]while[/FONT], and [FONT="Courier New"]do ... while[/FONT] loops by [FONT="Courier New"]goto[/FONT], and changing any [FONT="Courier New"]break[/FONT] or [FONT="Courier New"]continue[/FONT] statements to [FONT="Courier New"]goto[/FONT] as well.  What you end up with, assuming you've done it correctly, should be fairly close to the compiler's assembly output if you compile without optimizations --- essentially assembler in C. (If you're feeling really brave, you can manually all the function calls, but I wouldn't suggest going that far.)

The [FONT="Courier New"]goto[/FONT] statements resulting from loops will all be backward jumps.  Since programs are generally intended to be read from top to bottom, this makes the program much harder to comprehend.  If there's a [FONT="Courier New"]break[/FONT] or [FONT="Courier New"]continue[/FONT] somewhere in the mix, those will map to forward jumps, and you'll end up with some *real* spaghetti code.

On the other hand, as previous posters have also pointed out, sometimes a [FONT="Courier New"]goto[/FONT] is the best way to go (no pun intended).  I won't belabor their points, but the key is that you need to take into account the facilities given to you by the language you're working in.  It's called programming *into* a language, rather than programming *in* the language.  in C, using [FONT="Courier New"]goto[/FONT] for exception handling is idiomatic; in Python (for instance), it's unnecessary and would be considered unPythonic even if [FONT="Courier New"]goto[/FONT] were built in to the language.

---

### Post by Torajima on 2007-07-24
As someone who originally programmed in BASIC back in the 80s, I never understand the hate 'goto' receives.

Honestly, it was just our version of a function. Rather than say, re-draw a circle over and over again, we'd just put a chunk of text at the end of the program that draws a circle. Rather than call it with DrawCircle(), we'd "call" it with goto 8000.

In fact, you could make a convincing argument that todays programs... with tons of functions, classes, and interfaces seperated over multiple files... are less readable, and more spaghetti like, than anything we did back in the days of "goto".

Just my opinion...

---

### Post by slavik on 2007-07-24
> **Geekkit said:**
> Yep it sure does. So does crack cocaine. Existence is not a valid endorsement for being acceptable.
added to my signature ^^

@Torajima ... but what I can do today is plit up the program into mutiple source files and *gasp* even create dynamic libraries.

---

### Post by s1ightcrazed on 2007-07-24
**Begin:** Is goto used in higher level (goto middle)
[B]
3rd_sentence:[/B] because it creates messy, almost unreadable code. It certainly (goto counterargument)
[B]
middle:[/B] languages? I haven't run into it at all and I think that it is mainly (goto 3rd_sentence)

**counterargument:** has it's place in learning the history of (goto continued_explanation)

[B]
end:[/B] has disappeared. 

[B]
continued explanation:[/B] earlier programming languages, but largely it (goto end)

---

### Post by pmasiar on 2007-07-24
> **Torajima said:**
> I never understand the hate 'goto' receives.

Honestly, it was just our version of a function. Rather than say, re-draw a circle over and over again, we'd just put a chunk of text at the end of the program that draws a circle. Rather than call it with DrawCircle(), we'd "call" it with goto 8000.

This is not real GOTO: this usage is function call, where you have number instead of function name. You can argue that numbers are simpler that meaningful names, but I bet you use textual domain name instead of IP address to get to most websites, so... :-)

> In fact, you could make a convincing argument that todays programs... with tons of functions, classes, and interfaces seperated over multiple files... are less readable, and more spaghetti like, than anything we did back in the days of "goto".

Some soldiers are still trying to refight battle won (or lost) 25 years ago - so long ago that arguments *proving* supremacy of structured approach are long lost to pre-internet era.

Except of saving some space in drivers, there is no reason for GOTO in modern application programming. I challenge to write a pseudocode of program of say 300 lines (little one) where GOTO would add to easiness of understanding and maintenance. Because nobody can.

And for drivers, there is also vastly superior approach, which is structured and wickedly smarter (and resulting  in even more compact code) and more flexible than ASM: it is FORTH.

---

### Post by Torajima on 2007-07-25
> **pmasiar said:**
> This is not real GOTO: this usage is function call, where you have number instead of function name.

Of course it was "real" GOTO. What do you think most programmers used goto for? GOTO was simply a tool, and like any other tool, it could be abused.

>  You can argue that numbers are simpler that meaningful names, but I bet you use textual domain name instead of IP address to get to most websites, so... :-)

I think you guys are misunderstanding me. I'm not saying it was better in the old days (I sure as heck wouldn't want to give up the power and flexibility of python, c++, etc.), all I'm saying is, that it is pretty hypocritical to gripe about "goto" statements and how they created unstructured code that jumps all over the place, when function calls and object oriented programming allow you to do the exact damn thing!

> Except of saving some space in drivers, there is no reason for GOTO in modern application programming. I challenge to write a pseudocode of program of say 300 lines (little one) where GOTO would add to easiness of understanding and maintenance. Because nobody can.

Nobody can? Here you go...

Nested loops. It's a heck of a lot more understandable to use a single GOTO command to break out of these than use: break; break; break; break;

---

### Post by LaRoza on 2007-07-25
> **Torajima said:**
> 
I think you guys are misunderstanding me. I'm not saying it was better in the old days (I sure as heck wouldn't want to give up the power and flexibility of python, c++, etc.), all I'm saying is, that it is pretty hypocritical to gripe about "goto" statements and how they created unstructured code that jumps all over the place, when function calls and object oriented programming allow you to do the exact damn thing!

Making cryptic code is the fault of the programmer.

All looping constructs can be rewritten using goto, as noted elsewhere. The looping notation is for humans to read and to make things easier. Of course, people can misuse them to.

---

### Post by pmasiar on 2007-07-25
> **Torajima said:**
> Of course it was "real" GOTO. What do you think most programmers used goto for? GOTO was simply a tool, and like any other tool, it could be abused.

Not so. "Real" GOTO was to go without returning. This kind of GOTO s/b called CALL.

> all I'm saying is, that it is pretty hypocritical to gripe about "goto" statements and how they created unstructured code that jumps all over the place, when function calls and object oriented programming allow you to do the exact damn thing!

Not so again. If you CALL a function, after RETURN you return back after the CALL. With GOTO, there is no (simple system supported way) to return back. And *this* is a problem: spaghetti.

> Nested loops. It's a heck of a lot more understandable to use a single GOTO command to break out of these than use: break; break; break; break;

Let's suppose you did it. Now let's add some real-world flavors: In some of the nested loops you need to allocate some resources, which you need to release upon leaving. Now, you need structured breaks, so you return to proper nest level. You cannot? Ahh. Thought so: that is why your code leaks memory like a sieve... :-)

---

### Post by Wybiral on 2007-07-25
> **pmasiar said:**
> ... Now let's add some real-world flavors: In some of the nested loops you need to allocate some resources, which you need to release upon leaving. Now, you need structured breaks, so you return to proper nest level. You cannot? Ahh. Thought so: that is why your code leaks memory like a sieve... :-)

This is a very good point... You will likely have an iterator for each level of the loop (and probably some data inside the loop), which will need allocating and freeing (unless you use a bunch of globals... But that's a whole other world of messiness to deal with).

---

### Post by Torajima on 2007-07-25
> **pmasiar said:**
> Not so. "Real" GOTO was to go without returning. This kind of GOTO s/b called CALL.

Now, why would anyone do this? The only legtimate reason I can think of is that you ran out of line numbers, and had to skip to another section of code. But this is a problem with line numbers, and lack of auto renumbering, it's not a goto problem.

> Not so again. If you CALL a function, after RETURN you return back after the CALL. With GOTO, there is no (simple system supported way) to return back. And *this* is a problem: spaghetti.

What crappy language were you using that didn't allow returns after a GOTO? Every version of BASIC I've tried does this. Again, this was the whole point of GOTO... function calls (we called 'em sub-routines).

> Let's suppose you did it. Now let's add some real-world flavors: In some of the nested loops you need to allocate some resources, which you need to release upon leaving. Now, you need structured breaks, so you return to proper nest level. You cannot? Ahh. Thought so: that is why your code leaks memory like a sieve... :-)

Then again, most "modern" languages do the garbage collection for you...

---

### Post by Wybiral on 2007-07-25
A "call" or a "gosub" will allow you to use a "ret" or "return" to jump back (though not with a return value and with no function parameters so it's very limited even with the return).

The "call" or "gosub" requires the instruction pointer be pushed on the stack to denote the return address, while the "goto" or "jump" just changes the instruction pointer without pushing it.

"call" and "ret" are used in assembly to construct functions... But assembly uses the stack wisely to allow for function-scope data and parameters/returns.

But, if you're going to have a return, why not just use a function anyway?

---

### Post by shawnhcorey on 2007-07-25
> **Wybiral said:**
> But, if you're going to have a return, why not just use a function anyway?

There were no functions in BASIC.  Everything was a GOTO or a GOSUB.  The common structure of a BASIC program was to start with a GOTO.  This is because when executing a GOTO or GOSUB, the interpreter always started looking for the line from the beginning of the program.  So, it start with a GOTO, followed by the most commonly called GOSUB.  Followed by the next most common, and so on.  The initiation of the program was last, since it was only done once.

The worst part of BASIC was the ON..GOTO and ON..GOSUB statements.

---

### Post by Torajima on 2007-07-25
> **Wybiral said:**
> A "call" or a "gosub" will allow you to use a "ret" or "return" to jump back (though not with a return value and with no function parameters so it's very limited even with the return).

You didn't need to return values, as all variables in BASIC were global.

Which made things easier at times, but creating a seperate variable for every little for/next loop was a pain in the butt...

---

### Post by shawnhcorey on 2007-07-25
> **Torajima said:**
> You didn't need to return values, as all variables in BASIC were global.

Which made things easier at times, but creating a seperate variable for every little for/next loop was a pain in the butt...

You didn't need to create variables, just use them.  You did need to create arrays, but that's another story.  What was a pain in the butt was keeping track of the variables you used.  If you had a loop with a GOSUB in it, you couldn't use any variable used in the GOSUB (or its GOSUBs).

---

### Post by Wybiral on 2007-07-25
> **Torajima said:**
> You didn't need to return values, as all variables in BASIC were global.

Which made things easier at times, but creating a seperate variable for every little for/next loop was a pain in the butt...

I'll take my function scope data and encapsulation any day.

---

### Post by pmasiar on 2007-07-25
> **Torajima said:**
> What crappy language were you using that didn't allow returns after a GOTO? Every version of BASIC I've tried does this. Again, this was the whole point of GOTO... function calls (we called 'em sub-routines).

LOL here we are. I told you GOTO and CALL are *completely* different, and we are talking about different things.

GOTO in any other standard non-structured language (C, FORTRAN, ALGOL, even COBOL - but I forgot: anything except BASIC - but BASIC, as you just proved, is *not* standard) means "go to a line without remembering how to get back". This is BTW also the GOTO you want to use when leaving insides of a nested loops - whole point was to leave without returning.

And we were arguing that this "GOTO without return" is really bad, messes your code and creates spaghetti. And programmers should use structured approach, CALL  a subroutine (and RETURN  from it back) instead of GOTO a line.

Now, you mention that in your specific non-standard dialect of BASIC, GOTO worked like CALL. I don't remember exactly, but IIRC some BASICs I used differentiated between GOTO and CALL (but used line number for both).

> Then again, most "modern" languages do the garbage collection for you...

No garbage collector can collect object is they have pointers to them, if you leave object scope inproperly. If you do not understand that, and prefer to use crossed fingers to clean your garbage instead of releasing them properly, it tell just about your level of understanding (or ignorance) of fundamental programing concepts. Yes, your code might even run for a while, but it does not mean it is correct or uses good design.

---

### Post by shawnhcorey on 2007-07-25
> **pmasiar said:**
> 
> Then again, most "modern" languages do the garbage collection for you...

No garbage collector can collect object is they have pointers to them, if you leave object scope inproperly. If you do not understand that, and prefer to use crossed fingers to clean your garbage instead of releasing them properly, it tell just about your level of understanding (or ignorance) of fundamental programing concepts. Yes, your code might even run for a while, but it does not mean it is correct or uses good design.

Modern languages like Perl, Python and Ruby do garbage collection automatically.  If you leave the scope, and there are no references to it, it is collected automatically.

---

### Post by Torajima on 2007-07-25
> **pmasiar said:**
> And we were arguing that this "GOTO without return" is really bad, messes your code and creates spaghetti. And programmers should use structured approach, CALL  a subroutine (and RETURN  from it back) instead of GOTO a line.

Alright, I'll agree with you on this... if your language already has a way to call a function or sub-routine, and doesn't use line numbers, GOTO would be pretty useless. I still think, however, my earlier example of escaping nested loops would be a legitmate use of GOTO.

> Now, you mention that in your specific non-standard dialect of BASIC, GOTO worked like CALL. I don't remember exactly, but IIRC some BASICs I used differentiated between GOTO and CALL (but used line number for both).

The two versions of Basic I used the most (Appe II and Atari 8-bit) both used returns with the GOTO statement. If I remember correctly, the Commodore 64 and TRS-80 used return with a GOSUB command.

---

### Post by pmasiar on 2007-07-25
> **shawnhcorey said:**
> Modern languages like Perl, Python and Ruby do garbage collection automatically.  If you leave the scope, and there are no references to it, it is collected automatically.

Exactly. Unstructured GOTO leaves scope without notifying interpreter, so objects will *NOT* be cleaned. Structured exit, BREAK/LEAVE  tells computer to leave the scope and clean memory. That was my point all the time, if you bother to read the thread.

---

### Post by lisati on 2007-07-25
Suggestion: if the use of "goto" makes it easier to make good efficient code that is easy to understand and maintain, use it. Otherwise, as has been pointed out, there are often better ways of achieving results.

BUT: if you're into designing assemblers and compilers and the like, you might find that the occasional use of the machine language equivalent of "GOTO" is unavoidable: how does a "break" in "C" translate into machine code? (mentioned in someone else's post)

EDIT (afterthought): The idea of avoiding "GOTO" in a HLL seems to me to be there to help with describing the solution to a problem in an elegant and efficient way that means something to people, while still allowing the description to be translated into a machine-usable form....

---

### Post by lisati on 2007-07-25
> **Torajima said:**
> As someone who originally programmed in BASIC back in the 80s, I never understand the hate 'goto' receives.

Honestly, it was just our version of a function. Rather than say, re-draw a circle over and over again, we'd just put a chunk of text at the end of the program that draws a circle. Rather than call it with DrawCircle(), we'd "call" it with goto 8000.

In fact, you could make a convincing argument that todays programs... with tons of functions, classes, and interfaces seperated over multiple files... are less readable, and more spaghetti like, than anything we did back in the days of "goto".

Just my opinion...
I'd be more inclined to use a "GOSUB" in this example.

---

### Post by Wybiral on 2007-07-25
> **lisati said:**
> Suggestion: if the use of "goto" makes it easier to make good efficient code that is easy to understand and maintain, use it. Otherwise, as has been pointed out, there are often better ways of achieving results.

BUT: if you're into designing assemblers and compilers and the like, you might find that the occasional use of the machine language equivalent of "GOTO" is unavoidable: how does a "break" in "C" translate into machine code? (mentioned in someone else's post)

EDIT (afterthought): The idea of avoiding "GOTO" in a HLL seems to me to be there to help with describing the solution to a problem in an elegant and efficient way that means something to people, while still allowing the description to be translated into a machine-usable form....

But it's like I was saying earlier... Good assembly code makes use of "call" and "ret" (this is actually how functions are structured in C, this is basically "gosub") not "jmp" (the "goto" equivalent). And it makes use of stack frames to manage it's memory with a paramaters and function scope data... NOT with globals.

Good assembly only uses jumps to branch off for conditions, but this is something that every HLL will already take care of these days. In assembly you have to handle conditions this way, but in a higher level language it almost never makes any sense to handle it this way (with the exception of extreme space constraint, when you let go of standards and write dirty).

When in assembly, write like assembly... But when in HLL, please don't write like assembly.

---

### Post by shawnhcorey on 2007-07-25
> **pmasiar said:**
> Exactly. Unstructured GOTO leaves scope without notifying interpreter, so objects will *NOT* be cleaned. Structured exit, BREAK/LEAVE  tells computer to leave the scope and clean memory. That was my point all the time, if you bother to read the thread.

No, in modern languages, if the program leaves a scope, whether it's lexically or dynamic, and there are no other references to the memory, it is cleaned up.  This is true even if it leaves the scope via a "goto".

The Perl program below is an example.  If the scope was not restored, then the last call to show_var() would still say "inside".

```
#!/usr/bin/perl

use strict;
use warnings;

sub bar {
  show_var();
  goto LOOP;
}

our $var = 'outside';

sub foo {
  local( $var ) = 'inside';
  bar();
}

sub show_var {
  my @caller = caller;
  print "from line $caller[2]: \$var = $var\n";
}

my $done = 0;

LOOP : {
  last if $done;
  $done = 1;

  show_var();
  foo();
}
show_var();


```

---

### Post by Wybiral on 2007-07-25
> **shawnhcorey said:**
> No, in modern languages, if the program leaves a scope, whether it's lexically or dynamic, and there are no other references to the memory, it is cleaned up.  This is true even if it leaves the scope via a "goto".

The Perl program below is an example.  If the scope was not restored, then the last call to show_var() would still say "inside".



I think what he was trying to argue was that creating "functions" with goto (with the "return" as was mentioned earlier) is bad because there is no scope unless you manually clean things up yourself (even then, global variables aren't protected from the scope).

EDIT:

I may have misinterpreted though... I'm not sure...

---

### Post by shawnhcorey on 2007-07-25
> **Wybiral said:**
> I think what he was trying to argue was that creating "functions" with goto (with the "return" as was mentioned earlier) is bad because there is no scope unless you manually clean things up yourself (even then, global variables aren't protected from the scope).

EDIT:

I may have misinterpreted though... I'm not sure...

If the program never changes scope, the memory is cleaned up when a new value is stored in the variable.  If the program changes scope, the memory is cleaned up when it leaves the scope.

What you both don't realize is just how aggressive modern languages are at garbage collection; if it's not in use, it's gone.

---

### Post by slavik on 2007-07-25
> **shawnhcorey said:**
> If the program never changes scope, the memory is cleaned up when a new value is stored in the variable.  If the program changes scope, the memory is cleaned up when it leaves the scope.

What you both don't realize is just how aggressive modern languages are at garbage collection; if it's not in use, it's gone.
here's how java garbage collection works:
- copy anything referenced to a new piece of memory
- change existing references
- wipe the old piece of memory

and aggressive garbage collection would imply calling delete/free everytime something goes out of scope, which is rather slow.

---

### Post by pmasiar on 2007-07-25
> **lisati said:**
> Suggestion: if the use of "goto" makes it easier to make good efficient code that is easy to understand and maintain, use it. ..

And if ie. sand in your eyes helps you to write more romantic love letters,  of course, use it too... :-)

---

### Post by Geekkit on 2007-07-25
> **s1ightcrazed said:**
> **Begin:** Is goto used in higher level (goto middle)
[B]
3rd_sentence:[/B] because it creates messy, almost unreadable code. It certainly (goto counterargument)
[B]
middle:[/B] languages? I haven't run into it at all and I think that it is mainly (goto 3rd_sentence)

**counterargument:** has it's place in learning the history of (goto continued_explanation)

[B]
end:[/B] has disappeared. 

[B]
continued explanation:[/B] earlier programming languages, but largely it (goto end)

I think that this example is the most succinct way to sum it up. I love defenders of the use of GOTO since it means less competition in industry. If you're in a job interview and you don't start laughing hysterically after suggesting that GOTO is a valid programming practice, kiss that interview and job goodbye. No one I know (including myself) would hire you.

---

### Post by gradedcheese on 2007-07-26
Alright, I don't mean to keep dragging this on, but...

> **Geekkit said:**
> I think that this example is the most succinct way to sum it up. I love defenders of the use of GOTO since it means less competition in industry. If you're in a job interview and you don't start laughing hysterically after suggesting that GOTO is a valid programming practice, kiss that interview and job goodbye. No one I know (including myself) would hire you.

So you wouldn't hire any of the Linux kernel people?  Including the ones that wrote the drivers, etc.      I'm not saying that just because they do this, it's alright ...however, the pattern used in the kernel is a perfectly valid one and using it doesn't make you a bad programmer, especially when you're dealing with low-level code.

---

### Post by shawnhcorey on 2007-07-26
> **slavik said:**
> here's how java garbage collection works:
- copy anything referenced to a new piece of memory
- change existing references
- wipe the old piece of memory

and aggressive garbage collection would imply calling delete/free everytime something goes out of scope, which is rather slow.

I doubt if Java does it quite that way.  Try instead:
* Go through all allocated memory and clear its in_use flag.
* Starting with the program's variables and track down all memory references and set their in_use flag.
* Go through all memory and free those that still have their in_use flag clear.

I also suspect that Java uses reference counting to free memory immediately when it's no longer referenced.

---

### Post by Wybiral on 2007-07-26
> **gradedcheese said:**
> Alright, I don't mean to keep dragging this on, but...



So you wouldn't hire any of the Linux kernel people?  Including the ones that wrote the drivers, etc.      I'm not saying that just because they do this, it's alright ...however, the pattern used in the kernel is a perfectly valid one and using it doesn't make you a bad programmer, especially when you're dealing with low-level code.

I'm a huge advocate of optimization (pmasiar will testify to this and say something like "premature optimization is the root of all evil") but, you never want to start off by writing dirty code... Never. You're code gets dirty after you've profiled it and began finding the bottlenecks. If all of your code is dirty, then it's going to become this horrifying mess of nonsense.

I have no problem with people using an optimization like goto in C if (and only if) that was the only solution to get their program at a usable efficiency level (whether speed or size). The problem is when people start writing a program with crap like that... They end up with a mess. You need to optimize after you know where your bottlenecks are going to be, otherwise you're wasting time and writing unreadable programs.

As far as the kernels and the drivers you mentioned... They probably got that way AFTER they were profiled.

---

### Post by hod139 on 2007-07-26
gotos are used in linux drivers not for optimization, but for exception handling.  C does not have a standard way to handle exceptions, so the goto is the only way.  Modern languages have exception handling built in, so the use of the goto is no longer required to serve this function, and it is removed.

---

### Post by pmasiar on 2007-07-26
> **s1ightcrazed said:**
> **Begin:** Is goto used in higher level (goto middle)
[B]
3rd_sentence:[/B] because it creates messy, almost unreadable code. It certainly (goto counterargument)
[B]
middle:[/B] languages? I haven't run into it at all and I think that it is mainly (goto 3rd_sentence)

**counterargument:** has it's place in learning the history of (goto continued_explanation)

[B]
end:[/B] has disappeared. 

[B]
continued explanation:[/B] earlier programming languages, but largely it (goto end)

Hilariously funny, thanks for it. :-D Proves the point beyond any doubt.

But it has a bug (like most spaghetti does): After executing "** end:** has disappeared. " you need EXIT, otherwise it goes to "**continued explanation:**" again, and you have infinite loop :-)

So it proves that GOTO [url=http://en.wikipedia.org/wiki/Considered_Harmful is harmful[/url] yet again. If you can write a bug in less than 10 lines of pseudocode, imagine what will happen in real program :-D

I will sign off with link to [GOTO in wikipedia](http://en.wikipedia.org/wiki/GOTO), where smarter people than average in this forum, explained pro and con. If you don't have enough, go read Dijkstra, and read Knuth, and don't pretend you know something they don't.

---

### Post by LaRoza on 2007-07-26
> **tc101 said:**
> I know it is bad programming practice, but does goto even exist in the newer languages such as python, ruby, java, lisp, PHP and so on?

I started out in COBOL 30 years ago and it was one of our main tools.  By the time I got into VB3 about 12 years ago I had read that it was better to avoid it most of the time.  As VB developed over the years everybody stopped using it, but it was still there.  Now, looking at python and ruby I don't even see it any more.  Does it still exist?

Yes, it exists in some languages, I don't think Python, Ruby, JAVA, and PHP have it and I don't know LISP.

I'm sure if you googled "<language> reserved words", you'd get a clear answer.

Page 5, and here is the answer...

---

### Post by s1ightcrazed on 2007-07-26
> **pmasiar said:**
> Hilariously funny, thanks for it. :-D Proves the point beyond any doubt.

But it has a bug (like most spaghetti does): After executing "** end:** has disappeared. " you need EXIT, otherwise it goes to "**continued explanation:**" again, and you have infinite loop :-)


Actually, the more I think about it, what I should have done was:


```
10  Is goto used in higher level (goto 50)
20
30  because it creates messy, almost unreadable code. It certainly (goto 70)
40  just a bunch of junk
50  languages? I haven't run into it at all and I think that it is mainly (goto 30)
60
70  has it's place in learning the history of (goto 130)
80
90  more and more and more and more junk
100  has disappeared.
110
120
130  earlier programming languages, but largely it (goto  100)
140
150  exit

```

I think that puts it even better.

---

### Post by Wybiral on 2007-07-26
lol, but you forgot to goto 150 after 100! (which possibly highlights the point even more).

---

### Post by shawnhcorey on 2007-07-26
Actually I think the whole discussion became mote when Byte magazine intorduced the COMEFROM statement:

```
10  Is goto used in higher level
20
30  (comefrom 50) because it creates messy, almost unreadable code. It certainly
40  just a bunch of junk
50  (comefrom 10) languages? I haven't run into it at all and I think that it is mainly
60
70  (comefrom 30) has it's place in learning the history of
80
90  more and more and more and more junk
100  (comefrom 130) has disappeared.
110
120
130  (comefrom 70) earlier programming languages, but largely it
140
150  (comefrom 100) exit

```

---

### Post by slavik on 2007-07-26
a better example:

goto:
```

10: i = 0;
//10000 lines of code
...
i++;
goto 10; // infinite loop

```

for loop:
```

for (i=0; i=i; i++) {
//10000 lines of code
}
```

the point is that you need to look at only 1 place for a loop to predict how it will act, without looking throuhg extra code.

---

### Post by shawnhcorey on 2007-07-26
> **slavik said:**
> 
for loop:
```

for (i=0; i=i; i++) {
//10000 lines of code
}
```

the point is that you need to look at only 1 place for a loop to predict how it will act, without looking throuhg extra code.

```
i = 0
repeat {
  // 10_000 lines of code
  i ++;
} until( i == big_num );
```

Duh, what's you point again?

---

### Post by Geekkit on 2007-07-26
> **gradedcheese said:**
> So you wouldn't hire any of the Linux kernel people?

That's not what I said. I said that if anyone (could be kernel programmers, could be Web developers) defended the GOTO statement that they would not pass go nor would they collect $200 (in so many words I said this). I don't care who they are, where they've come from, how many famous peoples' hands they've shook. If they are a proponent of unstructured code they're not welcome.

In the business world time is money and if I have to spend time debugging horrible looking code it costs money, causes me frustration, and wastes other peoples' time. In the business sector it is vital that software be easily (or at least conveniently) reproducible in order to sustain the business. This usually goes further than simply structured code and leans towards design patterns but that's another topic altogether.

---

### Post by slavik on 2007-07-27
> **shawnhcorey said:**
> ```
i = 0
repeat {
  // 10_000 lines of code
  i ++;
} until( i == big_num );
```

Duh, what's you point again?

that is why I don't like do while loops much :)

---

### Post by Torajima on 2007-07-27
> **Geekkit said:**
> That's not what I said. I said that if anyone (could be kernel programmers, could be Web developers) defended the GOTO statement that they would not pass go nor would they collect $200 (in so many words I said this). I don't care who they are, where they've come from, how many famous peoples' hands they've shook. If they are a proponent of unstructured code they're not welcome.

Frankly, I wouldn't want to work for someone whose reading comprehension skills are so poor that he thinks anyone in this thread is proposing that unstructured "spaghetti" code is a good thing.

To sum up my points:

1. GOTO/RETURN was necessary in languages that did not have another way to do function calls.
2. GOTO was necessary in lanuages that used line numbers and did not do auto renumbering.
3. In certain rare instances, GOTO might still be useful today.
4. You can still create spaghetti-like code with function calls and OOP.

---

### Post by shawnhcorey on 2007-07-27
> **Geekkit said:**
> That's not what I said. I said that if anyone (could be kernel programmers, could be Web developers) defended the GOTO statement that they would not pass go nor would they collect $200 (in so many words I said this). I don't care who they are, where they've come from, how many famous peoples' hands they've shook. If they are a proponent of unstructured code they're not welcome.

In the business world time is money and if I have to spend time debugging horrible looking code it costs money, causes me frustration, and wastes other peoples' time. In the business sector it is vital that software be easily (or at least conveniently) reproducible in order to sustain the business. This usually goes further than simply structured code and leans towards design patterns but that's another topic altogether.

I hate to argue with anyone's religion but the fanatic belief of yours is bordering on the paranoia. GOTOs do not cause bad code.  Having had coded before structured coding appear, I can say most programs back then were not spaghetti code; they were organized.  In fact, it was seeing the organization patterns appear again and again that lead to structure coding.  Every structure in structured programming can trace it's history back to a pattern in unstructured coding.

Was causes bad code is the same thing now as then:  management that does not give its programmers enough time to refactor the program.  Everyone is in a hurry to get it done and who cares what it looks like as long as it works.  Eventually you end up in the same place as Netscape did:  totally rewrite the program or watch your market slowly dwindle away until you no longer have the resources for a rewrite.

But to get back to the OP questions.  Don't use GOTO.  There is no need and its abuses lead to trouble.  GOTOs are in all languages because GOTOs have always been in here.  And who knows, someday someone might come up with a technique that absolutely requires GOTO.

---

### Post by LaRoza on 2007-07-27
> **shawnhcorey said:**
> I hate to argue with anyone's religion but the fanatic belief of yours is bordering on the paranoia...

I think the poster meant that if the programmer used goto's in spite of other methods, no when it might be needed, like in the drivers.

---

### Post by qamelian on 2007-07-27
> **Torajima said:**
> What crappy language were you using that didn't allow returns after a GOTO? Every version of BASIC I've tried does this. Again, this was the whole point of GOTO... function calls (we called 'em sub-routines).
Not if you were using BASIC. GOTO stands on its own in all version of BASIC. The RETURN command is used to bounce back from a subroutine called using the GOSUB command. GOTO was most frequently used after a conditional test to skip a section of code that was not necessary if the test returned a value of TRUE. It was always used to jump to a new place in the program flow when there was no requirement to return to the previous place in the code.

---

### Post by qamelian on 2007-07-27
> **Torajima said:**
> 2. GOTO was necessary in lanuages that used line numbers and did not do auto renumbering.

No it wasn't. There was nothing that you could do with GOTO that couldn't also be accomplished with GOSUB:RETURN.

---

### Post by Torajima on 2007-07-27
> **qamelian said:**
> No it wasn't. There was nothing that you could do with GOTO that couldn't also be accomplished with GOSUB:RETURN.

If you were out of space (out of line numbers), there was no reason to return to that section of code... hence the plain old goto.

---

### Post by Torajima on 2007-07-27
> **qamelian said:**
> Not if you were using BASIC. GOTO stands on its own in all version of BASIC. The RETURN command is used to bounce back from a subroutine called using the GOSUB command.

Any ATARI or APPLE II programmers here? I could have sworn RETURN worked with GOTO in both of these versions of BASIC. But according to wikipedia, ATARI BASIC did indeed have a GOSUB command. It's been 17 years since I programmed anything on these machines, so perhaps my memory is faulty and I was simply using GOSUB all along (that's right... I'm man enough to admit when I'm wrong).

---

### Post by Wybiral on 2007-07-27
I'm an assembly programmer myself (and a BASIC refugee) so I've used my fair share of goto and gosub (or jmp and call). In assembly that's all you have. No functions or classes with methods and no premade loops.

Good assembly doesn't spend it's time jumping around, it only uses jmp for conditional branches and uses call + ret for "functions". Good assembly also makes proper use of stack frames to create functions and avoid using global data, this is important when you have no scope.

But, 99.999% of the time you don't need to program in assembly or use assembly-like constructs. I only do it when I need a tiny module or when I'm in the mood for a challenge. It's impractical for most programs when you have access to higher level languages.

Sure, you may need it when you're writing some core part of an OS or a driver, but for common programs... No! It's grossly inefficient for a developer to spend their time manually mapping out loops and functions when a compiler can do the same job instantly. And even worse to have to figure out someone else's code who uses it!

Maybe in an extreme situation where you need to pull some strings... But if you find yourself using it elsewhere, you need to rethink your design strategy.

---

### Post by pmasiar on 2007-07-27
Modern languages don't need GOTO - [COMEFROM](http://c2.com/cgi/wiki?ComeFrom) is better option :-) 

BTW in case someone skipped reading the link, it was a joke - an old joke, from 1984.

> **shawnhcorey said:**
> GOTOs do not cause bad code. ...Was causes bad code is the same thing now as then:  management that does not give its programmers enough time to refactor the program.

GOTO is bad [code smell](http://en.wikipedia.org/wiki/Code_smell) -- or would be if anyone used it nowadays, but luckily most don't.  

GOTO is not bad for code, like guns don't kill people. But if you see area with many guns, you think it is safe there?

>  Don't use GOTO.  There is no need and its abuses lead to trouble.  

100% agree. Just say NO! :-)

> GOTOs are in all languages because GOTOs have always been in here.  

Not so: languages designed by smart people (hint: Python :-) ) don't have it, because there is no need for it: [YAGNI](http://en.wikipedia.org/wiki/YAGNI) principle applies in full. Don't design features into your language which you *know* they are not needed "just in case". Features in language are not free.

GOTO (and also COMEFROM) was implemented only as [April Fools joke](http://entrian.com/goto/)

> And who knows, someday someone might come up with a technique that absolutely requires GOTO.

IIRC (and I am not going waste time to search for link, but I challenge anyone to disprove me) 30 years ago computing scientists proved GOTO is not required and any correct program with GOTO can be transformed to non-GOTO version.

Making place for future use of GOTO is like calling "just a theory, not real fact" theories like Darwin theory, Plate Tectonics theory, Theory of relativity, or Gravitational theory. When something falls, do you look up so be first to notice as "theory of gravity" was disproved? Thought so.

And c2 has [ultimate wisdom about GOTO:](http://c2.com/cgi/wiki?GoTo)

The apprentice uses it without thinking. The journeyman avoids it without thinking. The master uses it thoughtfully.

---

### Post by s1ightcrazed on 2007-07-30
> **Torajima said:**
> Any ATARI or APPLE II programmers here? 

Unfortunately, Yes.

[http://www.videogamecritic.net/xeinfo.htm]("http://www.videogamecritic.net/xeinfo.htm")

This machine represented my first foray into programming, tape drive and all. I do not remember RETURN being used in any manner with subs or otherwise, but I was 11 when this thing came out, and I've lost a few braincells since then. 

God I wish I still had this thing. It really was a blast programming on it, though I think I hearken back out of nostalgia alone.

---

### Post by the_dark_light on 2007-07-30
> **pmasiar said:**
> GOTO (and also COMEFROM) was implemented only as [April Fools joke](http://entrian.com/goto/)

lol, I love that one. GOTO seemed to become the subject of a holy war, no doubt by the inflammatory titled "GOTO Considered Harmful"

At least these GOTOs aren't as bad as classic GOTO - where GOTO referenced a line number (and having to leave gaps for expansion of the program)

Interestingly, I was reading about C#and found that it does indeed have GOTO - Why would Microsoft do this? It isn't needed! :confused:

(Oh well, at least it's not as bad as the Long Jump.  My C/C++ lecturer at Uni showed us how to use GOTO, but only referred to Long jump.  Nobody I know who knows how to use long jump will tell me how it works.  It's almost like it traumatizes everyone who uses it)

---

### Post by shawnhcorey on 2007-07-30
> **the_dark_light said:**
> (Oh well, at least it's not as bad as the Long Jump.  My C/C++ lecturer at Uni showed us how to use GOTO, but only referred to Long jump.  Nobody I know who knows how to use long jump will tell me how it works.  It's almost like it traumatizes everyone who uses it)

The setjmp/longjmp functions of C form a very crude exceptions handler.  setjmp is TRY/CATCH and longjmp is THROW.

```
status = setjmp( Jump_Buffer );
switch (status) {
  /* TRY */
  case 0:
    ...
    break;

  /*CATCH */
  case EXCEPTION_1:
    ...
    break;

  case EXCEPTION_2:
    ...
    break;
}
```
And later:
```
/* THROW */
longjmp( Jump_Buffer, EXCEPTION_n );
```

What gets me is that people think that something like exceptions handling appeared one night, fully-formed and mature, and the next day it was typed into the compiler without errors.

Exception handling was developed over a long and often painful process.  setjmp/longjmp is one of the first and crude attempts.  Before that, other attempts had to use GOTOs.  There was nothing else.

If GOTOs were dropped from structured languages as soon as they came out, you would not have exceptions today.  Emulating them with GOTOs is difficult enough; doing it without GOTOs when you have only a vague concept of what you're trying to achieve is almost impossible.

You can go your entire programming career without using a GOTO.  But if you want to try something new and creative, they are essential to refining the concept.

GOTOs should be including in all programming languages because of their ability to emulate clever concepts like exceptions.

---

### Post by vexorian on 2007-07-30
goto is possibly faster than the alternatives.

But structured programming is better.

Although sometimes you really need goto else you have to add plenty of overhead, want examples?

---

### Post by Fingolfin on 2007-10-01
> **pmasiar said:**
> If you consider C "high", what other language is lower? ASM does not count - ASM is mostly mnemonic for binary code. In my experience, all languages have higher concepts and less access to low-level hardware facilities than C.

Forth?

---

### Post by pmasiar on 2007-10-01
I don't agree Forth being low-level language. 

I know Forth rather well, I love it, (my thesis was Forth implementation for PDP/11, so I could pretend I know Forth inside out, but it was long time ago :-) )

Forth is very high-level language (4GL) or even better framewok for building 4GL domain-specific languages, easily, and with possibility to build new "words" using ASM if you need (as last resort). But more often you don't use ASM, and quite often dont think about stack in terms of numbers, but in terms of objects which addresses are on stack, manipulating them with appropriate words. That's the whole point of productivity: manipulate more abstract objects, to perform more by executing  a single line of code. And this is why verbosity of java is such a killer on productivity, at least for me.

---

### Post by Fingolfin on 2007-10-01
Yeah, that Prolog-like paradigm of building something new (in Forth's case "words") on-the-fly made me for a moment think it could fall into the low-level category. (It is many years since I last ran something called dsForth compiler on MS Win.)
Well, if not Forth, then the answer is: Machine language for Z80A or nothing :)

---

### Post by Coyote21 on 2007-10-01
> **tc101 said:**
> I know it is bad programming practice, but does goto even exist in the newer languages such as python, ruby, java, lisp, PHP and so on?

I started out in COBOL 30 years ago and it was one of our main tools.  By the time I got into VB3 about 12 years ago I had read that it was better to avoid it most of the time.  As VB developed over the years everybody stopped using it, but it was still there.  Now, looking at python and ruby I don't even see it any more.  Does it still exist?

Since no one has answered directly to this question.

It exists on java? 

Yes, but it does nothing, it's just there to avoid that you use it in your own definitions.

It exists on python?

No, not even as an keyword, like in java

It exists in lisp?

I don't think so, since lisp is somewhat an functional language, thus everything is an function, and an program is essentially an set of function calls, that can receive and return functions, as well as other data.

It exists in ruby?

No, not even as an keyword, just like python.

It exists in PHP?

No, at least I didn't find it, on the manuals. (At last, something positive in PHP, besides an cool xml access api, that exists in PHP 5. Since, the database access api is almost as spaghetti code, or even like reinventing the wheel (sure, who need an api for each database, when all or some of them share the same concepts? It wouldn't be simpler to just do something like java jdbc api?)

 I hope this answer to your question, at least part of it, more than the other posts (which are basically discussions, of old programming days :roll: :tongue:)

---

### Post by Seismosaur on 2007-10-01
> **Eddie_B said:**
> Many people say goto is bad programming,  but in my opinion, it really isnt. Ive met many programmers who use it for convenience myself being one and its never let me down.. As for your question, im not sure of the answer..

I think it is only bad when you start using goto in place of functions. The only time i use goto is when i can't think of a way to loop something in a function.

---

### Post by insyzygy on 2007-10-02
Many people here are giving the argument that goto is bad because it makes code hard to read. This is valid, but I think the more cogent argument against goto is that it is very easy to jump into an inconsistent program context
where variables have not been initialized etc. I.e. goto leads to bugs. Abstractly however, goto is very interesting in that it allows  novel ways to control program flow. 

There is an analogue of goto that is used in functional programming languages called continuations which avoid the issue of inconsistent states. 

A simple way of thinking about continuations is that a continuation is the current state of the program. Some languages will let you save the current continuation, and then call it ( i.e. jump to it). The difference between continuations and gotos is that when the saved continuation is called, the program state is reset to what it was when the continuation was saved so that the program is guaranteed
to always jump to a consistent state. 

As an example where this could be used. Consider a webserver whose client is disconnected and then reconnects. By saving the continuation before the disconnect, when the client reconnects, the webserver can jump to the exact state it was in before the disconnect.

Another example is backtracking. I.e. suppose you are searching a data structure. One could use continuations to save the state search down one path, and if that failed jump back up and search down another path. 

Note my description is very rough. 

Unfortunately, only functional languages really support it such as
scheme, haskell,o'caml. Ruby is probably the most mainstream language which supports it.

---

### Post by samjh on 2007-10-02
> **tc101 said:**
> I know it is bad programming practice, but does goto even exist in the newer languages such as python, ruby, java, lisp, PHP and so on?

...

Now, looking at python and ruby I don't even see it any more.  Does it still exist?

Most languages have goto in one form or another.  Even if goto doesn't exist in its pure form (ie. "goto"), it will be there.  The RETURN keyword can be considered a restricted form of goto, as can the BREAK keyword.

---

### Post by pmasiar on 2007-10-02
> **insyzygy said:**
> Abstractly however, goto is very interesting in that it allows  novel ways to control program flow. 

I am the only one who become uneasy when someone suggest "interesting" and "novel" ways to control program flow?

All I can tell, if you use GOTO: [May you live in interesting times](http://en.wikipedia.org/wiki/May_you_live_in_interesting_times)

And I also recommend reading that Terry Pratchett' novel. It is safer to live in boring times :-)

---

### Post by lisati on 2007-10-02
> **samjh said:**
> Most languages have goto in one form or another.  Even if goto doesn't exist in its pure form (ie. "goto"), it will be there.  The RETURN keyword can be considered a restricted form of goto, as can the BREAK keyword.

It is also  sometimes hidden behind constructs such as "while/wend".....  or "while (condition) {}" - the condition is evaluated at the start of the loop, and at the end of an iteration, the machine code equivalent of a "goto" is used to jump back to the test for condition.

---

### Post by insyzygy on 2007-10-03
> All I can tell, if you use GOTO: May you live in interesting times


I don't want to live in interesting times. But I don't mind interesting code.
At least academically, I have seen concise solutions to interesting problems using continuations that I thought were pretty, though admittedly difficult to understand.

I agree that any "interesting ways controlling program flow" make it hard for other people to read it so should be avoided in general on the basis that other people won't be able to understand it easily. 

I don't think anyone has mentioned the famous paper of Donald Knuth
"Structured Programming with Goto Statements."
The entire paper is about goto, and of course Donald Knuth is the master. 
This article interesting in that he discusses  how all flow control mechanisms (if, for, while), etc are gotos, as many people have mentioned. 

Also, Paul Graham's book On Lisp has some chapters near the end where he extensively uses continuations in some interesting ways. 
[http://www.paulgraham.com/onlisptext.html]("http://www.paulgraham.com/onlisptext.html")

There is also an interesting short article 
[http://www.cs.indiana.edu/~jsobel/c455-c511.updated.txt]("http://www.cs.indiana.edu/~jsobel/c455-c511.updated.txt")
about a programming project, where a student started with high level code in scheme, and then transformed it into low level C code with lots of gotos,
essentially compiling it by hand.  (as part of the class the faster your code was the higher your score).

---

### Post by CptPicard on 2007-10-03
> **insyzygy said:**
> I have seen concise solutions to interesting problems using continuations that I thought were pretty, though admittedly difficult to understand.

Continuations are a far more powerful concept... they serve much more of a purpose than a bunch of gotos which are equivalent to expressing the same algorithm in more high-level, understandable terms.

> 
This article interesting in that he discusses  how all flow control mechanisms (if, for, while), etc are gotos, as many people have mentioned. 
...
about a programming project, where a student started with high level code in scheme, and then transformed it into low level C code with lots of gotos,
essentially compiling it by hand.

Of course they're pretty much all gotos in the end, in assembly terms. And you can play compiler all you want, but it doesn't mean that the higher-level structured programming hadn't been born for a reason... after all, the question here is why goto has been ditched in *modern* programming languages :)

---

### Post by eph1973 on 2007-10-03
Not that I'm some guru, but here's what Brian Kernighan and Dennis Richie (the guys who wrote the C Language) have to say about goto:

From "The C Programming Language" by K&G
> C provides the infinitely-abusable goto statement, and labels to branch to.  Formally, the goto is never necessary, and in practice it is almost always easy to write code without it.

They go on to list some code examples for goto, then conclude the section with:
> 
With a few exceptions like those cited here, code that relies on goto statements is generally harder to understand and to maintain than code without gotos.  Although we are not dogmatic about the matter, it does seem that goto statements should be used rarely, if at all.

In their examples, they only used it to exit nested loops for a certain condition (the one that they say it is handy for is exception handling, as pmasiar said).

---

### Post by Wybiral on 2007-10-03
> **CptPicard said:**
> Of course they're pretty much all gotos in the end, in assembly terms. And you can play compiler all you want, but it doesn't mean that the higher-level structured programming hadn't been born for a reason... after all, the question here is why goto has been ditched in *modern* programming languages :)

In fact...

The use of GOTO is even more primitive in modern languages because you don't have direct access to the stack. In assembly you can structure functions and call them/return using GOTO, and pass parameters by allocating space for them on the stack (this same mechanism allows for function scope space). But you don't have that in most modern languages. There was a time and place for GOTO, but that time is over.

---

### Post by Lster on 2007-10-03
I don't think that gotos and structured programming are mutually exclusive.

---

### Post by CptPicard on 2007-10-03
Just introduce some more state... a boolean "done" flag that you set when you're done, and then check for in the loops' conditions. If you're willing to allow "break" you can use that too, but it is not mandatory..

---

### Post by Lster on 2007-10-03
I would find that far more confusing than using a goto...

---

### Post by CptPicard on 2007-10-03
I would have to disagree with that, but that's probably because I'm not used to thinking in terms of gotos. Anyway, your question was how to do it in general :)

Of course, exceptions fulfill a similar role, although certainly you would not use it as a flow control mechanism in your loop example.

---

### Post by Lster on 2007-10-03
I guess that is where we differ... I use assembly quite a lot now so gotos don't bother me. I always liked assembly but didn't start learning it (properly) for quite some time! :)

Lster

---

