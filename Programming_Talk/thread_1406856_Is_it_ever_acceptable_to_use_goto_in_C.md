---
title: "Is it ever acceptable to use goto in C?"
date: 2010-02-14
forum: Programming Talk
---

### Post by Yes on 2010-02-14
I was reading through some code for writing to an EEPROM using an Atmega microcontroller, and saw that it used goto statements.  I've always been told that I should never, ever use goto in a language like C, but the way it's used here seems to make a lot of sense.  So, I wanted to get some opinions - is goto ever acceptable in programming, or if used correctly could it be considered acceptable?

Here's the code example:

```
int eeprom_read_byte(uint16_t eeaddr, char *buf)
{
  uint8_t n = 0;

restart:
  if (n++ >= MAX_TRIES)
    return -1;

begin:
	// send start cond.
	TWCR = (1 << TWINT) | (1 << TWSTA) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MT_ARB_LOST) goto begin;
	if ( (TW_STATUS != TW_REP_START) && (TW_STATUS != TW_START)) {
		return -1;
	}
	
	// send 0xa0
	// 0xa0 = 1010 000 0
	// 4 bits:   <a..device-indentifier>
	// 3 bits:   <device-address set with chip pins>
	// last bit: <0..write>
	TWDR = 0xa0;
	TWCR = (1 << TWINT) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MT_SLA_NACK) goto restart;
	if (TW_STATUS == TW_MT_ARB_LOST) goto begin;
	if (TW_STATUS != TW_MT_SLA_ACK) goto error;
	
	// send low 8 bits of eeaddr 
	TWDR = eeaddr;
	TWCR = (1 << TWINT) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MT_DATA_NACK) goto restart;
	if (TW_STATUS == TW_MT_ARB_LOST) goto begin;
	if (TW_STATUS != TW_MT_DATA_ACK) goto error;
	
	// send high 8 bits of eeaddr
	TWDR = eeaddr << 8;
	TWCR = (1 << TWINT) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MT_DATA_NACK) goto restart;
	if (TW_STATUS == TW_MT_ARB_LOST) goto begin;
	if (TW_STATUS != TW_MT_DATA_ACK) goto error;
	
	// send start cond.
	TWCR = (1 << TWINT) | (1 << TWSTA) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MT_ARB_LOST) goto begin;
	if ( (TW_STATUS != TW_REP_START) && (TW_STATUS != TW_START)) {
		return -1;
	}

	// send 0xa1
	// 0xa0 = 1010 000 1
	// 4 bits:   <a..device-indentifier>
	// 3 bits:   <device-address set with chip pins>
	// last bit: <1..read>
	TWDR = 0xa1;
	TWCR = (1 << TWINT) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));
	if (TW_STATUS == TW_MR_SLA_NACK) goto quit;
	if (TW_STATUS == TW_MR_ARB_LOST) goto begin;
	if (TW_STATUS != TW_MR_SLA_ACK) goto error;
	
	// start read transmission
	TWCR = (1 << TWINT) | (1 << TWEN);
	while (!(TWCR & (1 << TWINT)));

	switch ((twst = TW_STATUS)) {
		case TW_MR_DATA_NACK:
			// FALLTHROUGH 
		case TW_MR_DATA_ACK:
			*buf = TWDR;
			break;
		default:
			goto error;
	}
	
quit:
	//stop condition
	TWCR = (1 << TWINT) | (1 << TWEN) | (1 << TWSTO);
	return 1;

error:
	//stop condition
	TWCR = (1 << TWINT) | (1 << TWEN) | (1 << TWSTO);
	return -1;
}
```

(The full program can be found here: [http://www.captain.at/electronic-atmega-eeprom.php](http://www.captain.at/electronic-atmega-eeprom.php))

---

### Post by Tony Flury on 2010-02-14
Although there are ways of coding this in C without gotos - using a goto within a function to provide a set of simple exit condditions for that function is about the only reasonable use (i.e the error and quit is ok !just! but the begin label in my view is a definite wrong thing to do).

I would want it to be recoded if i was doing the code review.

It might be that is a source code optimisation in order to get minimal code out of the compiler - but i bet most modern compilers would cope far better with a non-goto version.

Use of gotos to jump around to various places (i.e. emulate loops etc), and to jump out of functions etc is a definite no-no.

If you are writing proffesional code, don't use goto.

---

### Post by MadCow108 on 2010-02-14
its wrong to say "never ever use goto"
goto is a fine construct for certain problems, like breaking out of deeply nested loops. It also seems like an ok solution in the code in your post. Although the "faked" loop is a little unusual.

Just take care that your code stays readable as goto allows you to do really nasty stuff.

---

### Post by wmcbrine on 2010-02-14
If it weren't sometimes useful, it wouldn't be in the language. But it's rare. "Never use goto" is a maxim for beginners, so that they learn structured programming... but I think this describes you, no? ;)

I personally have never used goto in C, in thirteen years.

---

### Post by nrs on 2010-02-14
The kernel is littered with them. Trying to avoid them is sound advice, but people saying you should _***NEVER***_ use them are wrong, IMO.

I think the problem is crappy programmers can abuse them -- badly. If you know what you're doing though, they're just as useful as any other feature.

---

### Post by Lux Perpetua on 2010-02-14
If I understand correctly, this code is supposed to run on embedded hardware, not a PC. That imposes heavy constraints, and at some point, the guidelines for good program design take a back seat to those constraints. That might mean using goto **judiciously** for tasks that could in theory be accomplished by the structured control-flow mechanisms (loops or if/else or switch/case) but at an unacceptable cost. I think this particular use of goto might be acceptable. It's clear what the various gotos are doing: (1) to "retry" the current operation (in a couple different ways) or (2) to end the current operation (with or without error). I don't see how to rewrite the function to eliminate those gotos without duplicating some code or using state flags, which might be unacceptable in these circumstances. 

On the other hand, all the gotos *can* actually be eliminated without too much difficulty. Here's one way: ```
int eeprom_read_byte(uint16_t eeaddr, char *buf)
{
    uint8_t n = 1;
    int error = 0;

    while (1) {
        if (n >= MAX_TRIES)
            return -1;

        // send start cond.
        TWCR = (1 << TWINT) | (1 << TWSTA) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MT_ARB_LOST) continue;
        if ( (TW_STATUS != TW_REP_START) && (TW_STATUS != TW_START)) {
            return -1;
        }
	
        // send 0xa0
        // 0xa0 = 1010 000 0
        // 4 bits:   <a..device-indentifier>
        // 3 bits:   <device-address set with chip pins>
        // last bit: <0..write>
        TWDR = 0xa0;
        TWCR = (1 << TWINT) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MT_SLA_NACK) {
            n++;
            continue;
        }
        if (TW_STATUS == TW_MT_ARB_LOST) continue;
        if (TW_STATUS != TW_MT_SLA_ACK) {
            error = 1;
            break;
        }
	
        // send low 8 bits of eeaddr 
        TWDR = eeaddr;
        TWCR = (1 << TWINT) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MT_DATA_NACK) {
            n++;
            continue;
        }
        if (TW_STATUS == TW_MT_ARB_LOST) continue;
        if (TW_STATUS != TW_MT_DATA_ACK) {
            error = 1;
            break;
        }
	
        // send high 8 bits of eeaddr
        TWDR = eeaddr << 8;
        TWCR = (1 << TWINT) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MT_DATA_NACK) {
            n++;
            continue;
        }
        if (TW_STATUS == TW_MT_ARB_LOST) continue;
        if (TW_STATUS != TW_MT_DATA_ACK) {
            error = 1;
            break;
        }
                                                 
        
        // send start cond.
        TWCR = (1 << TWINT) | (1 << TWSTA) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MT_ARB_LOST) continue;
        if ( (TW_STATUS != TW_REP_START) && (TW_STATUS != TW_START)) {
            return -1;
        }

        // send 0xa1
        // 0xa0 = 1010 000 1
        // 4 bits:   <a..device-indentifier>
        // 3 bits:   <device-address set with chip pins>
        // last bit: <1..read>
        TWDR = 0xa1;
        TWCR = (1 << TWINT) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));
        if (TW_STATUS == TW_MR_SLA_NACK) break;
        if (TW_STATUS == TW_MR_ARB_LOST) continue;
        if (TW_STATUS != TW_MR_SLA_ACK) {
            error = 1;
            break;
        }
        
        // start read transmission
        TWCR = (1 << TWINT) | (1 << TWEN);
        while (!(TWCR & (1 << TWINT)));

        switch ((twst = TW_STATUS)) {
        case TW_MR_DATA_NACK:
            // FALLTHROUGH 
        case TW_MR_DATA_ACK:
            *buf = TWDR;
            break;
        default:
            error = 1;
            break;
        }

        if (error) break;
    }

    //stop condition
    TWCR = (1 << TWINT) | (1 << TWEN) | (1 << TWSTO);
    return error? -1 : 1;
}
```As you can see, the code is a little bit longer now, but it's more idiomatic as well, and I think it's also clearer (and can actually be cleaned up even more). Thus, I would use the non-goto version unless it were precluded by performance considerations or hardware constraints. 

To generalize this example, I would avoid goto unless I had a definite reason to use it, i. e., I knew exactly what I was doing. The person who wrote your example code probably knew what he was doing, but the fact that you had to ask your question at all indicates that this is not the case for you. ;) So don't use goto.

---

### Post by howlingmadhowie on 2010-02-14
i can't really see anything wrong with using goto as a sort of "break" to get out of a switch statement.  sometimes refactoring to package functions differently doesn't make much sense. let's say you have the following case:

```

function myfunc():
  dispatch (var):
    case A: do_stuff()
    case B: do_other_stuff()
    case C: some_more_stuff()
    default:  bit_more_stuff()

  do_this_before_leaving_function()

```

then i can understand using a goto to jump to the last line of the function because i think it would be clearer (a bit like call/cc in scheme, rather than having to figure out what the last computed value is, which is sometimes quite unclear).

of course you could write this example as:

```

function myfunc():
  _dispatch_func(var)
  do_this_before_leaving_function()

private function _dispatch_func(var):
  dispatch(var):
    case A: return do_stuff()
    case B: return do_other_stuff()
    case C: return some_more_stuff()
    default: return bit_more_stuff()

```

but you'd be forced to create another arbitrary function for it.

when i think about goto what i notice is that it can be used to break the view of programs in imperative programming languages as being tree structures.

---

### Post by gil_johnson on 2010-02-14
[QUOTE=Yes;8825853]I was reading through some code for writing to an EEPROM using an Atmega microcontroller, and saw that it used goto statements.  I've always been told that I should never, ever use goto in a language like C, but the way it's used here seems to make a lot of sense.  So, I wanted to get some opinions - is goto ever acceptable in programming, or if used correctly could it be considered acceptable?

[snip code]
There is a pretty good article in Wikipedia on "GOTO." Section 2, "Criticism and decline," contains the following passage:

"Probably the most famous criticism of GOTO is a 1968 letter by Edsger Dijkstra called Go To Statement Considered Harmful.[4] In that letter Dijkstra argued that unrestricted GOTO statements should be abolished from higher-level languages because they complicated the task of analyzing and verifying the correctness of programs (particularly those involving loops). An alternative viewpoint is presented in Donald Knuth's Structured Programming with go to Statements [5] which analyzes many common programming tasks and finds that in some of them GOTO is the optimal language construct to use."

One important point is that Dijkstra criticized *unrestricted* GOTO statements. Any instruction that jumps around in code can be done with GOTO, for instance break, continue, and loops, but these are well defined and restricted jumps. Knuth argues that programmers who know what they are doing can use GOTO safely for the various examples given in other posts.

So, if you (and anyone who reuses your code) are as careful as Donald Knuth, go ahead and use them.
Gil

---

### Post by pbrane on 2010-02-14
A *goto* is an unconditional jump. Sometimes there is no other way out. I think *goto's* should be used only when you know that you have to and understand why you have to.


As others have pointed out a control structure or loop is preferable. In the case of this particular code I think *goto* is probably not necessary. I'm not that familiar with the ATmega microcontroller so it could be that the error handling using *goto* is necessary.

---

### Post by nvteighen on 2010-02-15
> **howlingmadhowie said:**
> i can't really see anything wrong with using goto as a sort of "break" to get out of a switch statement.  sometimes refactoring to package functions differently doesn't make much sense. let's say you have the following case:

```

function myfunc():
  dispatch (var):
    case A: do_stuff()
    case B: do_other_stuff()
    case C: some_more_stuff()
    default:  bit_more_stuff()

  do_this_before_leaving_function()

```


Er... You usually would use "break" for doing that... :p

On goto... The issue is actually to state that goto should be used with extreme care and only after everything else has failed because, as it is an unrestricted jump, well... it's quite easy to make a mess with it. Moreover, people defending loops as flow controlling constructs don't have any problem with break/continue, which also are jumps... but restricted ones, so there are less chances to have your code transformed into spaghetti (yumi!). Exceptions are also jumps... but, again, restricted. (Sometimes goto and longjmp() are used in C to implement a basic exception system).

The issue is not about the concept of jumps, but about making people aware that they are meant for certain specific situations and that there are certain jumps that are designed to overcome the code's structure... something most people are likely not to ever need...

---

### Post by howlingmadhowie on 2010-02-15
> **nvteighen said:**
> Er... You usually would use "break" for doing that... :p

The issue is not about the concept of jumps, but about making people aware that they are meant for certain specific situations and that there are certain jumps that are designed to overcome the code's structure... something most people are likely not to ever need...

i don't tend to write "break" in pseudo-code because it should be automatic anyway. it's a big bug in C syntax that you have to write "break" explicitly inside cases. it also makes it quite unclear (at first glance) where you are breaking to. 

i think gotos are the only sane way of implementing a sort of internal return inside a function, the sort of thing you can do in scheme like this:

```

(define myfunc
  (lambbda ()
    (+ 3 (call/cc (lambda (return)
           (return 5))))))

```

which escapes back up the function tree. there is usually no way of doing this (gracefully) in C.

---

### Post by BenAshton24 on 2010-02-15
> **Yes said:**
> Is it ever acceptable to use goto in C?
If you are a perfectionist and you want to be able to sleep at night then I would say no :P A good structure and a well thought out design is always preferable in my opinion. I think that they're good for testing your code before you go and restructure the whole section because you didn't plan it properly in the first place... but not really for anything else.

---

### Post by howlingmadhowie on 2010-02-15
> **BenAshton24 said:**
> If you are a perfectionist and you want to be able to sleep at night then I would say no :P A good structure and a well thought out design is always preferable in my opinion. I think that they're good for testing your code before you go and restructure the whole section because you didn't plan it properly in the first place... but not really for anything else.

the thing is, you are automatically equating not using goto with a good structure and a well thought out design. why? what is inherently wrong with goto?

---

### Post by napsy on 2010-02-15
goto is perfectly fine for getting out of nested loops and jumping to error handling. The problem is when it is used by inexperienced programmers and can lead to unreadable (spaghetti) code.

---

### Post by Reiger on 2010-02-15
Goto should be avoided. That is not the same as eliminated.

A major reason for avoiding Goto is that it is easy to create a memory leak. Here's some Basic that reads input from keyboard (TI BASIC to be precise):

```

: Label KC
: K = getKeyCode()
: If (K == 0)
: Then
: Goto KC
: End

```

This is problematic because if you let this code run a loooong time (i.e. inside some loop and your users goes away and gets himself a cup of coffee) you end up with a &#8220;massive&#8221; memory leak: you keep pushing reference points (code address for the program to continue at when the Goto instruction finished) into the memory and even when you finally push a button there remains a residue of memory that is no longer referred to but neither is it freed up ('cause you hit End and continue with normal program flow at which point all the other dead Ends are never resolved). On a TI calculator this usually results in a Memory Error because you only have, say, 24KB of RAM total to play with and that needs to cover the code of your pogram and any variables/objects in use as well (variables are not erased on exit, they are kept in memory). And variables like K take up 14 Bytes there...

By contrast:
```

: K=getKeyCode()
: While (K == 0)
: K=getKeyCode()
: End

```
Can run for indefinite amounts of time without exhausting memory.

---

### Post by CptPicard on 2010-02-15
Just an interesting aside regarding goto, Knuth and Dijkstra... Knuth always was one of these people who insisted on using machine language to demonstrate things, while Dijkstra is the  famous "computer science as astronomy" guy who always stressed code clarity and in particular the ability to prove an algorithm's correctness. It is an interesting difference.

Also, funny that Scheme was pulled into this -- continuation passing is indeed a kind of very high-level functional "goto" especially in the case where the tail-calls are involved. In a worthy functional language, they are of course optimized away, so essentially if it were compiled all the way down, you'd get jump instructions (test this on SBCL).

There was last week this thread of the one guy who had this horrible looking BASIC piece of code and that had to be translated into C... if I had had to do that myself, I would have approached it with Gambit (a Scheme-to-C compiler) and have written continuation-passes for the GOTOs and NEXTs...

---

### Post by nvteighen on 2010-02-15
> **howlingmadhowie said:**
> i don't tend to write "break" in pseudo-code because it should be automatic anyway. it's a big bug in C syntax that you have to write "break" explicitly inside cases. it also makes it quite unclear (at first glance) where you are breaking to. 

i think gotos are the only sane way of implementing a sort of internal return inside a function, the sort of thing you can do in scheme like this:

```

(define myfunc
  (lambbda ()
    (+ 3 (call/cc (lambda (return)
           (return 5))))))

```

which escapes back up the function tree. there is usually no way of doing this (gracefully) in C.

Hm... Such a case is actually not a good example of what call/cc is meant to be used for...

```

;; Standard Scheme... It should work with any implementation.

(define continuation 0)

(define (add number1 number2)
  (+ number1
     (call-with-current-continuation
      (lambda (cc)
        (set! continuation cc)
        (cc number2)))))

(add 6 7)
(continuation 8) ; equal to (add 6 8)

```

Ok, this is also very basic, but shows better what call/cc is meant to do. call/cc captures the whole state of computation in a certain point of execution so you can, for example, save it in a place. It's much more than a goto, which just is able to return to a place in code, but it allows you to recreate the whole program's state in a certain moment... like you were effectively time-travelling to the past. Used in functional programming, you could be able to, for example, pass down a computational state of an external tail-recursive loop into an inner one and viceversa... But, as the idea of state computations implies the idea of state, this is usually used in imperative-style Scheme... (well, you could use streams... if someone manages to create a stream of continuations, he'll certainly be my Lisp god together with Lars Nostdal... I can't even imagine how one would ever think of managing that :P).

call/cc is, IMO, galaxies away from goto because it works as a runtime object, not as a compile-time thing. It's completely safe for the program's structure because it works by implying there's a structure (well, you have to take the continuation from somewhere, right?) and by reconstructing the whole stack in order to preserve things as they were but in an encapsulated way. In goto, there's nothing of this.

---

### Post by CptPicard on 2010-02-15
> **nvteighen said:**
> Hm... Such a case is actually not a good example of what call/cc is meant to be used for...


Yes, it is a good (one specific kind of) example... :) it is a so-called "escape continuation", which, in many other languages, are implemented as exceptions.

---

### Post by nvteighen on 2010-02-15
> **CptPicard said:**
> Yes, it is a good (one specific kind of) example... :) it is a so-called "escape continuation", which, in many other languages, are implemented as exceptions.

Hm... well, a bit too specific to my taste :P The issue is that call/cc is one of those concepts you have to illustrate with real code, not with *ad hoc* examples. Both howlingmadhowie's and mine are that simple that call/cc becomes totally redundant and unnecessary just to make our point.

Anyway, it's a sign of good health that in these forums we can talk about call/cc... :D

---

### Post by CptPicard on 2010-02-15
Well, the escape continuation is probably the simplest demonstration of call/cc, and it also is recognizable as an exception/longjmp to people who aren't used to continuations.

Of course, when it comes to learning continuations in general, I personally found it much more informative just to do manual continuation passing a little first... you just always select your next function at runtime and call it at tail position, and keep that up ad inifitum, and interestingly, you're working with computed gotos of sort, but in a much more understandable functional framework... call/cc is easier to understand on top of that, considering that you can just grab the *current* continuation like that and turn your "computation right here with a hole in it" into an ad hoc function...

EDIT: And to continue my slight objection, nvteighen... in pure-functional programming, the continuation is a value like any other that gets passed around... the escape continuation demonstrates essentially "the" way to use call/cc in that sort of a context...

---

### Post by nvteighen on 2010-02-15
> **CptPicard said:**
> 
EDIT: And to continue my slight objection, nvteighen... in pure-functional programming, the continuation is a value like any other that gets passed around... the escape continuation demonstrates essentially "the" way to use call/cc in that sort of a context...

Yup... but isn't it a sort of state? I'd love to see pure-functional code using call/cc (besides the "escape continuation" one)... never seen it yet :(

---

### Post by Reiger on 2010-02-15
In function programming it is an idiom with its own name: Continuation Passing Style (CPS).

In Haskell it's really simple:
```

-- type signature of parse would be &#8220;String -> Maybe Command&#8221; 

processInput str p_success p_fail= exec (parse str)
       where
          exec (Just Command) = p_success Command
          exec (Nothing)      = p_fail str

```

EDIT: The reason why I bring up Haskell here is that CPS reminds me of the &#8220;Yet Another Haskell Tutorial&#8221; by Daumé which was my introduction to it.

---

