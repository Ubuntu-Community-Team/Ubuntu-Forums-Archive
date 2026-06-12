---
title: "Explain output of this code"
date: 2010-08-11
forum: Programming Talk
---

### Post by jfreak_ on 2010-08-11
```
 
#include<stdio.h>
void main()
{
int j =4, x;
x= ++j + ++j + ++j;
printf("%d",x);
}

```

expected output is 18 but across compilers , output is 19.  Can anyone give me a reason?

---

### Post by Bachstelze on 2010-08-11
This has undefined behavior. Don't do it.

---

### Post by donsy on 2010-08-11
> **Bachstelze said:**
> This has undefined behavior. Don't do it.
I agree. But one possibility may be that the compiler interprets the expression as: 
x = ++[(++j + ++ j) + ++j]

---

### Post by SevenMachines on 2010-08-11
As mentioned, its undefined behaviour. Computers don't count like we do, as it doesnt know any better since this is unclear, it'll use the registers to get the job done as it sees fit. mine will do this, there will be other ways

> # I've done x= ++j + ++j + ++j;
# How will you do it computer?
movl   $0x4,0x1c(%esp)         # esp = 4 (j=4)
addl   $0x1,0x1c(%esp)    # esp = esp + 1    (do one ++j) 
addl   $0x1,0x1c(%esp)    # esp = esp + 1 (do the other ++j, why not?.. no reason from what you've given me)
mov    0x1c(%esp),%eax  # eax = esp = 6 (store new 'j' copy in eax)
add    %eax,%eax    # eax = eax + eax = 12    ( now do one ++j + ++j)
addl   $0x1,0x1c(%esp)  # esp = esp + 1 = 7 (now do the last ++j)
add    0x1c(%esp),%eax  # eax = eax + esp = 19 (add this to our stored ++j + ++j)
mov    %eax,0x18(%esp)  # eax = esp = 19 (eax is now our result, not what you want?.. oh...)

---

### Post by trent.josephsen on 2010-08-11
I got as far as
```
void main()
```
Oh, look, you've strayed into undefined behavior already.

---

### Post by interval1066 on 2010-08-11
Depends on the compiler, but yeah, this is super crazy risky stuff. To get around the main method signature nonsense, you could use a C++ compiler, like g++, it won't mind your main method signature, but that's not cross-compatible. As for your pre increments, your simply inviting your compiler of choice to do the math in whatever way it sees fit, and in your case, its the wrong thing. In this case by the time it gets around to the first increment its placing 5 in x because its pre-incrementing it before being equal to j... kind of a mind-stretch, not sure how it arrives at that conclusion since its undefined before being equal to j. Not safe code at all. I bet you anything if you try this on borland turbo c or something else you have access to you will get a different result.

---

### Post by Simian Man on 2010-08-11
If you use undefined behaviour in your code the compiler has license to do whatever the hell it wants with it.  It can produce code to delete files off your hard drive in that case and still be standards-compliant.

---

### Post by jfreak_ on 2010-08-12
why is everone saying it's risky? What's the maximum that can happen?

---

### Post by jfreak_ on 2010-08-12
And what makes a piece of code to have undefined behaviour?

---

### Post by TNT1 on 2010-08-12
> **jfreak_ said:**
> why is everone saying it's risky? What's the maximum that can happen?

Yeah, please, somebody, answer...

---

### Post by MadCow108 on 2010-08-12
> **jfreak_ said:**
> why is everone saying it's risky? What's the maximum that can happen?
put it in a calculation for missile guidance or a nuclear reactor...


the reason it's undefined is simple:
Because the C standard says so.

Technical reason is to give compilers more freedom e.g. to do better optimization relying on that the programmer knows what he's doing.
Also see:
[http://en.wikipedia.org/wiki/Sequence_point](http://en.wikipedia.org/wiki/Sequence_point)

C has many such things because the language is so strongly focused on performance (see also strict aliasing).
Higher level languages with other goals mostly define semantics for these situations

---

### Post by jfreak_ on 2010-08-12
> **MadCow108 said:**
> 

the reason it's undefined is simple:
Because the C standard says so.




Sorry for sounding dumb, but whats a C standard?

---

### Post by lisati on 2010-08-12
> **jfreak_ said:**
> Sorry for sounding dumb, but whats a C standard?
You might want to think of it as the "official" version of C.

Have a look here: [http://en.wikipedia.org/wiki/ANSI_C](http://en.wikipedia.org/wiki/ANSI_C)

---

### Post by trent.josephsen on 2010-08-12
> **jfreak_ said:**
> why is everone saying it's risky? What's the maximum that can happen?
The typical answer here is that the compiler could cause demons to fly out of your nose.  However, nasal demons is not the only viable option; it could with equal validity cause a trap representation, overrun a buffer, cause your computer to explode (assuming proper hardware support), or send nuclear missile launch codes to Siberia, obliterating all sentient life on Earth and leaving evolution to come up with a successor to the human race, which will eventually develop computers and a language similar to C, one user of which will make the same mistake, plunging the world once more into darkness and resetting the entire process.  So you see, the future of human evolution depends on you not invoking undefined behavior.

(Okay, so it's not likely that any compiler will do anything so interesting as obliterate humanity.  Most compilers will just evaluate the expression to some value and carry on as if undefined behavior had not been invoked.  The big problem with relying on undefined behavior is that it's not consistent between compilers, versions of compilers, optimization levels, or even between subsequent invocations of the same compiled program.  Doing what you expect is the worst kind of undefined behavior, because it slips by unnoticed until you copy it into some mission-critical software and compile it with different options.  But I digress.)

Don't play with undefined behavior.

---

### Post by interval1066 on 2010-08-12
Think on this example; what is the answer to the mathematical question "x / 0 = ?"

The official, mathematical answer to this question is "undefined". If you don't believe me, look it up. I dare you. 

One committee, which is actually more like a collection of committees, is the ANSI committee, or the American National Standards Institute. These guys create a lot of the standards that define C & C++.

C, like just about every other aspect of computer science, which borrows heavily from mathematics, is written to work to a standard, usually a committee of scholarly type people who write down what the aspect they are writing about is supposed to do; and the implementers, which is anyone who wants to create a technology to use the standard, must follow. If you make the implementation do something that the standards people haven't defined an outcome for, you get "undefined behavior".

What, you think this stuff was dreamt up by a gang of rowdy college kids? Don't answer that.

---

