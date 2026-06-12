---
title: "Comments In Open Source Projects"
date: 2011-05-30
forum: Programming Talk
---

### Post by ve4cib on 2011-05-30
This is a question directed mainly at developers and maintainers of open-source projects, but feel free to chime in with an opinion even if you don't fit into that category.

My question is: how heavily should the code be commented?

When you download the source for an open-source project what do you expect in the way of comments?  Do you want function summaries in the headers, in the source, both, or neither?


I've recently created a project on Google Code.  It's an embedded OS for use with Robotis robot kits, so it's intended for a fairly narrow audience, and I can probably safely assume that anyone using it will be a reasonably competent C programmer.

Obviously things like structs and functions should be documented explaining what they're for and how they're used, but how much in-line documentation is generally seen as "good?"


I've seen both extremes in various open-source projects I've run into.  Some have zero comments in the code, others have paragraphs and paragraphs of it.

Personally I don't see either extreme as being useful, and I'm aiming for something in the middle.  If the code looks complicated then toss in a one-liner explaining (briefly) what's going on.

I think I've got a good idea of what I think is good, but given the variation amongst programmers I figured I'd toss the question out there and get some feedback from someone else.

---

### Post by muteXe on 2011-05-30
> 
Personally I don't see either extreme as being useful, and I'm aiming for something in the middle. If the code looks complicated then toss in a one-liner explaining (briefly) what's going on.

I pretty much agree with that.

Also, I don't know why you specifically talk about open source projects. I expect I'd write the same comments in both open source and commercial projects.

---

### Post by juancarlospaco on 2011-05-30
As much as possible, if it becomes too big, just provide the link to such resource, like:

# for comments see: [www.myopensourceapp.org/doc/modules/some-module.html](www.myopensourceapp.org/doc/modules/some-module.html)

---

### Post by ve4cib on 2011-05-30
> **muteXe said:**
> I don't know why you specifically talk about open source projects. I expect I'd write the same comments in both open source and commercial projects.

It was easier to frame the question in terms of my current situation by talking about open-source.  But you're right, the same logic should apply to commercial software as well.

Unfortunately I have run into one or two cases where the commercial version of a piece of software is all nicely documented, but the open-source version (same software, but dual-licensed) has the comments stripped out upon release.  Very annoying.


@juancarlospaco: that's a good suggestion.

---

### Post by indefinitearticle on 2011-05-30
I think it's more important in an open source environment than a commercial one because of the dependency on collaboration. If the code is not commented well, the ability of other programmers to easily and effectively continue work is hampered.

In terms of length, I'd rather see paragraphs than nothing, but I think the general consensus you'll find is exactly what you've described.

---

### Post by SmilePiper on 2011-05-30
I like to write out the variable names rather than abreviate them.  This saves a lot of explanations, because the purpose of the variables is more obvious.

---

### Post by hakermania on 2011-05-31
> **juancarlospaco said:**
> As much as possible, if it becomes too big, just provide the link to such resource, like:

# for comments see: [www.myopensourceapp.org/doc/modules/some-module.html]("http://www.myopensourceapp.org/doc/modules/some-module.html")


No, bad one, i'd like to be able to see the comments while being offline :/

---

### Post by DangerOnTheRanger on 2011-05-31
I think a good mix of code/comments is with around 40-45% of your non-blank lines being comments. Yes, that sounds like a lot, but it's always good to put yourself in the shoes of someone who knows your respective programming language, but has no knowledge of the libraries you're using.

Here's my personal set of guidelines:

[LIST]
[*]Paragraphs over one-liners
[*]Explanation of 3rd-party libraries over assumed knowledge of said libraries
[*]Explanation of custom/exotic algorithms over RT*M :)
[*]Readability over short line count
[*]Obvious stuff should not be commented
[*]Although "obvious" must first be defined
[/LIST]
For you Pythonistas out there: No, I'm no Tim Peters, but I came pretty close :)

---

### Post by StephenF on 2011-05-31
The comments don't run and if you write too many they become a bigger maintenance task than the code itself and turn into a huge distraction from the innate structure of the code.

A comment at the top of each module explaining what it does and its overall role in the program is useful. A remark that explains what a line of code did last year is not.

---

### Post by ve4cib on 2011-06-01
So here's a sample of my code.  The functions are used for setting up and using semaphores/mutexes.  (Since this is an OS for an embedded system I can't just use a POSIX mutex, so the OS has its own -- very simple -- implementation.)

**kernel.h** *excerpt only*
[php]
typedef struct semaphore
{
    int8_t value;
    uint8_t waitList[MAXIMUM_TASKS];
    uint8_t queueLength;
    uint8_t lockedBy;
} Semaphore;

...

void initSemaphore(volatile Semaphore *semaphore, uint8_t value);
void lockSemaphore(volatile Semaphore *semaphore);
void unlockSemaphore(volatile Semaphore *semaphore);

...
[/php]

**kernel.c** *excerpt only*
[php]
...

// blocking semaphore with priority and niceness
// internal semantics of semaphore reversed for simple array indexing
void initSemaphore(volatile Semaphore *semaphore, uint8_t value)
{
    semaphore->value = -value;
    semaphore->lockedBy = thread[IDLE].tid;  // initially semaphore is owned by the idle task
    semaphore->queueLength = 0;  // nobody's waiting in line yet
} // initSemaphore


// note: do not call lockSemaphore within an interrupt context
// lock a semaphore if it is unlocked or we own the lock
// otherwise queue the current thread and wait
void lockSemaphore(volatile Semaphore *semaphore)
{
    cli();

    if (semaphore->value >= 0)   // the semaphore is currently locked
    {
        if(semaphore->lockedBy == thread[currentThread].tid)
        {
            semaphore->value++;
        }
        else
        {
            // insert in order of priority and niceness
            uint8_t x;

            for (x = 0; x < semaphore->queueLength; x++)
            {
                if ( thread[currentThread].priority > thread[ semaphore->waitList[x] ].priority &&
                        thread[currentThread].niceness < thread[ semaphore->waitList[x] ].niceness )
                {
                    uint8_t temp_task = semaphore->waitList[x];
                    uint8_t i;

                    for (i = x + 1; i < semaphore->queueLength; i++)
                    {
                        uint8_t swap = semaphore->waitList[i];
                        semaphore->waitList[i] = temp_task;
                        temp_task = swap;
                    }
                    semaphore->waitList[i] = temp_task;

                    break;
                }
            }

            semaphore->waitList[x] = currentThread;
            thread[currentThread].state = BLOCKED;

            semaphore->queueLength++;
        }
    }
    else // the semaphore is currently available
    {
        semaphore->value++;
        semaphore->lockedBy = thread[currentThread].tid;
    }

    sei();

    while (thread[currentThread].state == BLOCKED)
    {
        asm volatile("nop"::);
    }
} // lockSemaphore

// unlock a semaphore and dequeue a waiting thread if necessary
void unlockSemaphore(volatile Semaphore *semaphore)
{

    cli();

    semaphore->value--;

    if (semaphore->value < 0 && semaphore->queueLength>0)
    {
        // we just unlocked the semaphore and there is 1+ thread waiting to lock it

        uint8_t x;
        thread[semaphore->waitList[0]].state = READY;
        semaphore->lockedBy = thread[semaphore->waitList[0]].tid;
        semaphore->queueLength--;

        for(x=1; x<=semaphore->queueLength; x++)
            semaphore->waitList[x-1] = semaphore->waitList[x];
    }
    else if (semaphore->value < 0)
    {
        // the semaphore is unlocked and there is no queue of other threads wanting it
        semaphore->lockedBy = IDLE;
    }

    sei();
} // unlockSemaphore

...
[/php]

A few specific questions, if you have the time...

If you downloaded this code and wanted to work with it would you find this level of commenting useful?  Too much?  Too little?

Do the variable names make sense to you (granted that this is largely taken out of context)?

Do you mind that the function prototypes in the header are *not* documented, but have descriptions in the source where they're implemented?  Would you prefer it the other way around?  Or descriptions in both places?

---

### Post by Some Penguin on 2011-06-01
> **ve4cib said:**
> So here's a sample of my code.  The functions are used for setting up and using semaphores/mutexes.  (Since this is an OS for an embedded system I can't just use a POSIX mutex, so the OS has its own -- very simple -- implementation.)

**kernel.h** *excerpt only*

It's useful to document a structure or function declaration in the header file; ideally, somebody shouldn't necessarily have to go line by line through the implementation in order to understand what the API is about.  

This is a only guideline, of course.   At one extreme, for completely internal structures that are useful for implementation-specific code, which may change arbitrarily, and should not be externally used, there may simply be comments noting this and pointers to design notes or something else; at another extreme, if you're implementing a library for partial differential equations over a distributed system, most users would prefer to read a documented API rather than be required to examine your implementation.  This is particularly true once your code is been used a bit and prospective new users would like to believe that it actually does what you claim it does trusting that horrible discrepancies would have been noticed by earlier users, so that they focus their attention on their own system and not yours.

Re: your semaphore, "value" in particular is vague; if you're going to use fields like that, it's nice to document what they are values *of* (e.g. what is the range of possible values?  how should it be interpreted?)

```

typedef struct semaphore
{
    int8_t value;
    uint8_t waitList[MAXIMUM_TASKS];
    uint8_t queueLength;
    uint8_t lockedBy;
} Semaphore;

...

```

Also above, it might be noted how you're using lockedBy to signal not-locked-at-all; you're indicating the idle thread.  Using a uint8_t prevents one obvious otherwise-alternative (a negative thread id, for instance); depending on the system somebody might reasonably have expected thread 0, however.

If instead somebody shouldn't be counting on particular interpretations of the fields because they may be subject to change and that /only/ your functions have the ability to reliably use them, a comment warning them to that effect would be appropriate.



Again, in code below -- value should be renamed or explained.
```

void initSemaphore(volatile Semaphore *semaphore, uint8_t value);
void lockSemaphore(volatile Semaphore *semaphore);
void unlockSemaphore(volatile Semaphore *semaphore);

...

```

**kernel.c** *excerpt only*
```

...

// blocking semaphore with priority and niceness
// internal semantics of semaphore reversed for simple array indexing
void initSemaphore(volatile Semaphore *semaphore, uint8_t value)
{
    semaphore->value = -value;
    semaphore->lockedBy = thread[IDLE].tid;  // initially semaphore is owned by the idle task
    semaphore->queueLength = 0;  // nobody's waiting in line yet
} // initSemaphore

```

Some of the comments are overkill.  The end of the function is obvious, as is the 'queueLength = 0', and the lockedBy ... is fine.    Ditto 'initially'.

"Blocking semaphore with priority and niceness" sounds like it belongs in the header, unless for some reason priority and niceness should not be counted upon by the user. 

"Internal semantics of semaphore reversed for simple array indexing" is obscure.


```

// note: do not call lockSemaphore within an interrupt context
// lock a semaphore if it is unlocked or we own the lock
// otherwise queue the current thread and wait

```

For something fairly serious like that warning, it'd be good to establish some convention.  Oh, and this probably belongs in the header file, too, since not everybody reads the source.

```

void lockSemaphore(volatile Semaphore *semaphore)
{
    cli();

    if (semaphore->value >= 0)   // the semaphore is currently locked
    {
        if(semaphore->lockedBy == thread[currentThread].tid)
        {
            semaphore->value++;
        }
        else
        {
            // insert in order of priority and niceness
            uint8_t x;

            for (x = 0; x < semaphore->queueLength; x++)
            {
                if ( thread[currentThread].priority > thread[ semaphore->waitList[x] ].priority &&
                        thread[currentThread].niceness < thread[ semaphore->waitList[x] ].niceness )

```

Side note; I am inclined to be suspicious of the above comparisons.   You're comparing (A1,B1) with (A2,B2).  What if (A1 < A2) but (B1 >= B2)?  Then neither pair comes before the other?

```

                {
                    uint8_t temp_task = semaphore->waitList[x];
                    uint8_t i;

                    for (i = x + 1; i < semaphore->queueLength; i++)
                    {
                        uint8_t swap = semaphore->waitList[i];
                        semaphore->waitList[i] = temp_task;
                        temp_task = swap;
                    }
                    semaphore->waitList[i] = temp_task;

                    break;
                }
            }

            semaphore->waitList[x] = currentThread;
            thread[currentThread].state = BLOCKED;

            semaphore->queueLength++;
        }
    }
    else // the semaphore is currently available
    {
        semaphore->value++;
        semaphore->lockedBy = thread[currentThread].tid;
    }

    sei();

    while (thread[currentThread].state == BLOCKED)
    {
        asm volatile("nop"::);
    }
} // lockSemaphore

```

The //lockSemaphore is again not particularly necessary these days, since IDEs and many text editors are excellent at matching braces and the like, and these functions are not particularly tangled

```

// unlock a semaphore and dequeue a waiting thread if necessary
void unlockSemaphore(volatile Semaphore *semaphore)
{

    cli();

    semaphore->value--;

    if (semaphore->value < 0 && semaphore->queueLength>0)
    {
        // we just unlocked the semaphore and there is 1+ thread waiting to lock it

        uint8_t x;
        thread[semaphore->waitList[0]].state = READY;
        semaphore->lockedBy = thread[semaphore->waitList[0]].tid;
        semaphore->queueLength--;

        for(x=1; x<=semaphore->queueLength; x++)
            semaphore->waitList[x-1] = semaphore->waitList[x];
    }
    else if (semaphore->value < 0)
    {
        // the semaphore is unlocked and there is no queue of other threads wanting it
        semaphore->lockedBy = IDLE;
    }


```
Side note:  you're doing  'if (A && B) {1} else if (A) {2}'.  Both A and B are purely functional -- no effect just by checking.  Unless the value of A might change between comparisons, this is equivalent to "if (A) { if (B) {1} else {2} }" which then leads to a "else { // !A }" block if appropriate.

[/code]
```

    sei();
} // unlockSemaphore

...

```

---

