---
title: "Opinion on break or return in loops"
date: 2010-09-24
forum: Programming Talk
---

### Post by GuillaumeMG on 2010-09-24
My teachers always told me to avoid using *break* or *return* in loops as this is not good coding habit. Here's an example situation :
```
void f1()
{
    int i;
    for (i = 0; i < 100; i++)
    {
        if (m_randomInt[i] == 42)
            //Some code
        break;
    }
    if (i == 100)
        //Some other code
}
```where m_randomInt is an array of 100 random integrals.

They would tell me to replace it with something like :
```
void f1()
{
    int i;
    bool found;
    while (i < 100 && !found)
    {
        if (m_randomInt[i] == 42)
            //Some code
        i++;
    }
    if (!found)
        //Some other code
}
```This is a fairly simple (and useless) function and its only purpose is to define the kind of *break* I was talking about. I remember coming across cases when using one *break* or *return* instruction would, at least in my point of view, simplify some part of my code greatly.
Now, what's your opinion; when is using *break* acceptable?

---

### Post by James78 on 2010-09-24
Well, I think break, continue, return, etc is acceptable when it follows the KISS rule. If the code looks good, and it's straightforward and simpler than the alternative, then I see no reason why it's a bad thing... Unless someone can give me some technical details on why it might be bad..

You should ask your instructors to explain _why_ it's a bad habit. (I find that lots of instructors seem to have erroneous ridiculous ideas for some reason..)

---

### Post by worksofcraft on 2010-09-24
My opinion is diametrically opposed to that of your teachers.
To me logic that is nested several levels and that tests again for conditions you already tested for is hard to follow.

I like to eliminate all the error conditions first, yes with explicit premature return statements so that I can get down to the real algorithm.

So if you are iterating looking for a something then the moment I find it I'll process it and return.

```

bool do_it(int Start, int End) {
    if (Start >= End) return complain_about_bad_range();

    for (It = Start; It < End; ++It) {
        if (found(It)) return process(It);
    }
    return complain_about_no_it(Start, End);
}

```

well something like that anyway ;)

---

### Post by dirghrabadia on 2010-09-24
Using 'break' would break out of the closest loop, and not any further. So, you have to be a little bit cautious when dealing with nested loops. For example, you got a triply nested loop, now when some operation is completed, like finding integer 42 in the array etc., you might want to quit the triply nested loop and print something, but if you don't be careful, you might end up running the other two loops of the triply nested loop unnecessarily, and getting erroneous results. In other words, make sure you have an idea about the flow of the program, especially. after the execution of 'break' statement. Hope this helps :)

---

### Post by dirghrabadia on 2010-09-24
> **James78 said:**
>  (I find that lots of instructors seem to have erroneous ridiculous ideas for some reason..)

+1.:lolflag:

---

### Post by GuillaumeMG on 2010-09-24
> **James78 said:**
> Well, I think break, continue, return, etc is acceptable when it follows the KISS rule. If the code looks good, and it's straightforward and simpler than the alternative, then I see no reason why it's a bad thing... Unless someone can give me some technical details on why it might be bad..

You should ask your instructors to explain _why_ it's a bad habit. (I find that lots of instructors seem to have erroneous ridiculous ideas for some reason..)

Yeah, forgot the *continue* instruction which they advised me against too. Their argument is that it leads to less readable and maintainable code, they compared it to the GO TO statement. I found this paper about the GO TO statement [http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF](http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF)

---

### Post by schauerlich on 2010-09-24
> **GuillaumeMG said:**
> Yeah, forgot the *continue* instruction which they advised me against too. Their argument is that it leads to less readable and maintainable code, they compared it to the GO TO statement. I found this paper about the GO TO statement [http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF](http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF)

Except a GOTO can pretty much jump anywhere, whereas break and continue are very specific. Yes, as far as what the compiler generates, break and continue are almost certainly jump/GOTO instructions... but then again, so is all control flow. I don't really see the problem, as long as you're sane about it...

---

### Post by GuillaumeMG on 2010-09-24
> **dirghrabadia said:**
> Using 'break' would break out of the closest  loop, and not any further. So, you have to be a little bit cautious  when dealing with nested loops. For example, you got a triply nested  loop, now when some operation is completed, like finding integer 42 in  the array etc., you might want to quit the triply nested loop and print  something, but if you don't be careful, you might end up running the  other two loops of the triply nested loop unnecessarily, and getting  erroneous results. In other words, make sure you have an idea about the  flow of the program, especially. after the execution of 'break'  statement. Hope this helps :smile:
Part of their point is that, in the case of the triply nested loop for example, the program will always be easier to follow when using the right condition and no *break* or *continue* instruction.

---

### Post by GuillaumeMG on 2010-09-24
> **schauerlich said:**
> Except a GOTO can pretty much jump anywhere, whereas break and continue are very specific. Yes, as far as what the compiler generates, break and continue are almost certainly jump/GOTO instructions... but then again, so is all control flow. I don't really see the problem, as long as you're sane about it...
  I reiterate I completely agree with you, my teachers are the one that doesn't :P

---

### Post by mp035 on 2010-09-24
For readability break and continue are worlds away from GOTO, break and continue both tell the (human) reader which way the program flow is jumping, whereas GOTO can jump anywhere.  

break says "ok we're done here, lets get out"

continue says "ok this isn't what I want, lets try the next one"

goto heads off quietly to a secret position.

---

### Post by lisati on 2010-09-24
With suitable sanity checking before the loop, a suitable condition for the loop, and carefully thought out contents of the loop (e.g. not trying to do too much at once), many headaches can be avoided.

One thing I don't like seeing is something like this:
```
while (1)
{
//some code
}

```
It seems to defeat the purpose of using "while" in the first place!

---

### Post by mp035 on 2010-09-24
while (1) is a way of making your jump direction readable
```

while(1)
{
    if (some_conditions)
    {
        continue; // you know i'm jumping back to while
    }
    
    if (some_other_conditions)
    {
        break; //you know i'm jumping forward to the end of the loop
    }

    if (even_more_conditions)
    {
        goto label;  // you have no idea where i'm going.
    }
}

```

---

### Post by James78 on 2010-09-24
> **lisati said:**
> With suitable sanity checking before the loop, a suitable condition for the loop, and carefully thought out contents of the loop (e.g. not trying to do too much at once), many headaches can be avoided.

One thing I don't like seeing is something like this:
```
while (1)
{
//some code
}

```
It seems to defeat the purpose of using "while" in the first place!
while(1) feels wrong too me, but while(true) feels right. :D

---

### Post by StephenF on 2010-09-24
> **James78 said:**
> while(1) feels wrong too me, but while(true) feels right. :D
1 what and TRUE could be anything. That's why I like [noparse]for(;;)[/noparse] without any statements inside.

Anyway I don't see anything wrong with using goto with a meaningful label name to break out of a triple nested loop.

If you can eliminate a goto with a loop then loop, obviously. I guess the main reason goto is forbidden is because it's a tempting trap for the computing novice who is likely to be thinking in a stepwise flowchart manner rather than viewing the problem as systems within systems. The goto statement then becomes part of the novice's comfort zone.

Teachers are a problem I think when they say never ever use goto and the real reason is because it hampers the teaching of structured programming rather than it breaks structure in a program. Some teachers don't understand this and reflexively hate on goto for no other reason than that's what they were taught to do and it appears some in this thread will be doing the same. My teacher said....

And another thing, control variables are stupid since all they do is soft code a goto which means congrats you made a goto but one prone to bugs that runs more slowly, introduces an unnecessary variable, and is even less readable than those pesky gotos that reduce readability.

[COLOR="Gray"]This thread is now about the goto statement.[/COLOR] :-\"

---

### Post by GuillaumeMG on 2010-09-24
> **StephenF said:**
>  Some teachers don't understand this and reflexively hate on goto for no other reason than that's what they were taught to do and it appears some in this thread will be doing the same. My teacher said....

Well, IHMO, going out in forums asking for input isn't exactly "doing what we're taught to do" without questioning anything.

---

### Post by lisati on 2010-09-24
"while(1)" and "while(true)" etc. don't sit comfortably with me because they look too much like deliberate infinite loops, which can be hard to debug. 

The style of programming I was taught (back in the day when Pascal was new enough to still be cool as a first langauge) prefers something like "while (!finished)" or "do until (finished)"

---

### Post by fct on 2010-09-24
> **GuillaumeMG said:**
> My teachers always told me to avoid using *break* or *return* in loops as this is not good coding habit. Here's an example situation :
```
void f1()
{
    int i;
    for (i = 0; i < 100; i++)
    {
        if (m_randomInt[i] == 42)
            //Some code
        break;
    }
    if (i == 100)
        //Some other code
}
```where m_randomInt is an array of 100 random integrals.

They would tell me to replace it with something like :
```
void f1()
{
    int i;
    bool found;
    while (i < 100 && !found)
    {
        if (m_randomInt[i] == 42)
            //Some code
        i++;
    }
    if (!found)
        //Some other code
}
```This is a fairly simple (and useless) function and its only purpose is to define the kind of *break* I was talking about. I remember coming across cases when using one *break* or *return* instruction would, at least in my point of view, simplify some part of my code greatly.
Now, what's your opinion; when is using *break* acceptable?

Your teachers are indoctrinating a subjective appreciation. A correct use of "break" is effective, optimal and more readable than code with unnecessary flags.

So just nod and do it as they ask to pass the grades, then do whatever you have once you're free. :P

---

### Post by StephenF on 2010-09-24
Totally on topic.
[http://kerneltrap.org/node/553/2131](http://kerneltrap.org/node/553/2131)

---

### Post by worseisworser on 2010-09-24
> **GuillaumeMG said:**
> My teachers always told me to avoid using *break* or *return* in loops as this is not good coding habit. Here's an example situation :
```
void f1()
{
    int i;
    for (i = 0; i < 100; i++)
    {
        if (m_randomInt[i] == 42)
            //Some code
        break;
    }
    if (i == 100)
        //Some other code
}
```where m_randomInt is an array of 100 random integrals.



I would use (or create) a different iteration construct and avoid break altogether in this case.

Something like this:

```

CL-USER> (defun f1 ()
           (let ((random-integers (loop :repeat 100 :collect (random 100))))
             (if (some (lambda (x) (= x 42))
                       random-integers)
                 (write-line "some code (42 was found)")
                 (write-line "some other code (42 was not found)"))
             (format t "random-integers: ~A~%" random-integers)))
F1
CL-USER> (f1)
some code (42 was found)
random-integers: (14 26 8 42 25 29 42 11 49 70 24 78 7 39 0 22 0 18 14 26
                  17 13 59 90 93 22 48 37 52 26 6 43 17 2 95 43 96 76 0 68
                  70 64 55 21 77 22 37 89 85 40 31 60 91 90 59 33 85 44 90
                  3 53 71 17 33 18 32 40 54 4 55 27 24 24 15 95 93 81 72
                  17 36 18 0 31 69 62 54 43 28 50 76 76 57 74 64 12 50 34
                  9 14 19)
NIL
CL-USER> (f1)
some other code (42 was not found)
random-integers: (67 43 69 25 0 53 27 94 90 39 2 67 83 97 5 45 58 68 71 65
                  72 37 58 11 5 97 28 59 96 18 19 34 93 39 27 15 39 37 13
                  43 9 61 1 57 78 23 44 56 6 49 64 22 83 97 84 50 27 74 23
                  95 62 60 17 9 25 85 91 69 72 22 57 81 40 98 8 32 51 6 72
                  55 52 82 85 78 31 45 75 10 10 26 52 97 71 31 29 85 91 63
                  25 8)
NIL
CL-USER> 

```

( *some* is described here: [http://static.nostdal.org/hyperspec/Body/f_everyc.htm](http://static.nostdal.org/hyperspec/Body/f_everyc.htm) )

---

### Post by nvteighen on 2010-09-24
Those teachers' attitude reminds me of the one of the Real Academia Española and the Academie Française of trying to regulate how people should talk in Spanish and French, respectively. You know, nobody really cares less and people just talk the way they know they will be understood by the addressee.

Ok, that could sound a bit weird and off-topic, but it isn't. Programming languages have some elements you can use to "speak" about what you want. You can use them however you like, but you should try to be clear in your expression: just because Perl allows you to really convoluted stuff, you shouldn't write Perl code that way... write it in a way people (including yourself) will understand it better and will be able to the most sense of it... and I include mantaining under the notion of "understanding": if some code is written in a messy way, mantainance is more difficult not because the language became harder all of a sudden, but because the writer expressed himself in an unclear way.

So, one should **always** be suspicious of statements like "break is bad", "goto is bad", "the notation 'char array[]' is bad", etc. It depends on the context. Ok, there is a big correlation between messy code and abuse of "goto", but it's its **abuse** which brings up messy code. Insightful statements would be "unneeded gotos lead to modularity be broken", "'char array[]' is misleading because it allocates a pointer not an array by using array syntax", etc. But well, it's up to people to use that stuff correctly or wrongly...

---

### Post by VernonA on 2010-09-24
You teacher is trying to make you a good programmer, and so is driving you down a harder path than normal in the same way any instructor forces students to do hard stuff which they'll probably never use again! Certainly, most would agree that excessive use of jumps in code is the sign of a bad programmer. However, as mentioned, the real aim of the game is to write code which flows smoothly. Every jump can disrupt the flow unless it is the only sensible thing to do, in which case use. A good jump is certainly better than writing something convoluted just to avoid it. Where I work, we have code guidelines which have stood us in good stead. They deal with specifics (like we have a globally accessible header file which contains things like:
    #define FOREVER  for( ; ; )
so we can write:
```
    FOREVER
    {...
    }
```
and we all know that we're in an infinite loop.) The guide also offers general advice, like don't nest anything more than about three levels deep, if it doesn't fit on line break it up, don't use GOTOs, do use return, break and continue to make code easier to read, and so on.
Thus, for example, we consider a well-written function to look like:
```
errCode  myBigFunc(...)
{
   int status = openfile(..);
   if (status != E_SUCCESS) return status;

   status = read( handle, buff );
   if (status != E_SUCCESS) return status;

   // if we get here, then we know we have something useful to
   // process, and we are still at the first level of indenting

   FOREVER
   {
       status = process( buff );
       if (status != E_SUCCESS) break;

       status = read( buff );
       if (status != E_SUCCESS) break;
    }

    // If we reached end-of-file, we have successfully processed it
    if (status == E_END_OF_FILE) status = E_SUCCESS;

    close( handle );
    return status;
}

```Note how we can't just return on error inside the loop because we need to close the file. The break statement handles this nicely and reads well (ie if something is wrong we need to break out of the normal flow of read, process, read, process...)

There are many other ways to write the above, and a common one is:
```
    int status;

    if ( (status = openFile()) == E_SUCCESS)
    {
        if ((status = read(handle..)) == E_SUCCESS)
        {
            while (status == E_SUCCESS)
            {
                process( buff );

                status = read( ... );
            }
        }
        close( handle );
    }
    return status;

```This looks OK whilst it's small, but the indentation gets a bit overwhelming as the code starts to grow (and it always does!). It read well, in that if you successfully open the file, then you read it, if you successfully read then you process, and so on. I don't think it reads well enough to recommend it over the first way however.

To conclude, if you use break and continue to deliberately alter the flow of code when something exceptional occurs, good programmers will be perfectly happy with that since it is what they would expect. If you use jumps just to get from one part of a function to another, then that is just confusing and wrong.
Rgds,
Vernon

---

### Post by Bachstelze on 2010-09-24
> **GuillaumeMG said:**
> Yeah, forgot the *continue* instruction which they advised me against too. Their argument is that it leads to less readable and maintainable code, they compared it to the GO TO statement. I found this paper about the GO TO statement [http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF](http://www.cs.utexas.edu/users/EWD/ewd02xx/EWD215.PDF)

"Any if-statement is essentially a goto, as are all structured loops. And sometimes structure is good, when it is good you should use it. And sometimes structure is BAD, and gets into the way, and a goto is just much clearer."

-- Linus Torvalds

---

### Post by eeperson on 2010-09-24
I think the three constructs discussed (break, continue, goto) are not equally 'bad'.

I think continue is always useless.  Anytime I see something of the form:

```

for(...) {
  if(...) {
    //do some stuff...
    continue;
  }

  //do some other stuff...
}

```

I think it is better served by something like:

```

for(...) {
  if(...) {
    //do some stuff...
  } else {
    //do some other stuff...
  }
}

```

I think goto should be avoided but has its uses.  Although, these 'uses' usually means that a language is missing a feature that would solve the problem much better.  For example, it is common in C to use goto for error handling because the language lacks exceptions.

I think break is a feature that all languages with imperative looping should have.  It is frequently the most straightforward way to end an imperative loop early.

---

### Post by StephenF on 2010-09-24
> **eeperson said:**
> I think goto should be avoided but has its uses.  Although, these 'uses' usually means that a language is missing a feature that would solve the problem much better.  For example, it is common in C to use goto for error handling because the language lacks exceptions.
What is an exception but a structured longjmp on steroids? The goto is restricted to within the confines of a function whereas an exception throw can be nested several functions deep so you can't connect a throw with a particular catch in the way you can guarantee a goto hits a certain label.

It's more of a [COMEFROM]("http://en.wikipedia.org/wiki/COMEFROM") in some respects.

---

### Post by VernonA on 2010-09-24
FYI, I knew a programmer who really liked GOTOs, and he used to have his own header file which (IIRC) set-up:
```
#define  START:       do {
#define  END:         } while (0);
#define  GOTO_START   continue;
#define  GOTO_END     break;

```This allowed him to write constructs like:
```
    ..some code..
START:
    ..do some stuff..
    if (do it again) GOTO_START;
    .. more stuff..
    if (finished) GOTO_END;
    ..more stuff..
END:
    ..more stuff..

```Of course, I would not recommend it!

---

### Post by eeperson on 2010-09-24
> **StephenF said:**
> What is an exception but a structured longjmp on steroids? The goto is restricted to within the confines of a function whereas an exception throw can be nested several functions deep so you can't connect a throw with a particular catch in the way you can guarantee a goto hits a certain label.

It's more of a [COMEFROM]("http://en.wikipedia.org/wiki/COMEFROM") in some respects.

Your absolutely right.  It is basically a "structured longjmp on steroids".  However, it is the 'structured' part that keep it sane and the 'steroids' part that makes it more useful.  Well implemented exceptions give you a complete stack trace so you always know exactly where it came from.  On the other hand you can have multiple gotos for the same label and have no idea which one it came from.

---

### Post by endotherm on 2010-09-24
this is the best argument against the break statement that I know of
[http://www5.in.tum.de/~huckle/attcrash1.htm](http://www5.in.tum.de/~huckle/attcrash1.htm)

this is also why most modern languages won't allow case statements to fall through more than one case.

---

### Post by Bachstelze on 2010-09-24
> **endotherm said:**
> this is the best argument against the break statement that I know of
[http://www5.in.tum.de/~huckle/attcrash1.htm](http://www5.in.tum.de/~huckle/attcrash1.htm)


Is that sarcasm? :p This doesn't look like an argument about "break" to me, and even if it was, it certainly wouldn't be "the best".  What does this mean?

> The mistake is that the programmer thought that the break statement applied to the if statement in the above passage, was clearly never exercised.

---

### Post by endotherm on 2010-09-24
> **Bachstelze said:**
> Is that sarcasm? :p This doesn't look like an argument about "break" to me, and even if it was, it certainly wouldn't be "the best".  What does this mean?
the code  that abstract is based on took out AT&T's national telephone network do to a single line of code in a single network switch. granted, it's the coders fault, but it;s a high risk construct.
[http://en.wikipedia.org/wiki/Downtime#Famous_outages](http://en.wikipedia.org/wiki/Downtime#Famous_outages)

---

### Post by lisati on 2010-09-24
> **StephenF said:**
> 
It's more of a [COMEFROM]("http://en.wikipedia.org/wiki/COMEFROM") in some respects.

I was waiting for someone to mention "[ComeFrom]("http://www.fortran.com/come_from.html")"

---

