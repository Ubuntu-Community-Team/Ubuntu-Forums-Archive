---
title: "What do YOU think of single vs. multiple routine exit points?"
date: 2007-12-04
forum: Programming Talk
---

### Post by Sporkman on 2007-12-04
[http://www.regdeveloper.co.uk/2007/12/04/multiple_exit_wounds/](http://www.regdeveloper.co.uk/2007/12/04/multiple_exit_wounds/)

> **Bloody code!**

By Matt Stephens, the Agile Iconoclast
Published Tuesday 4th December 2007 00:32 GMT

It's amazing how some good practices limp on for decades beyond their expiration date. I still encounter people who insist that a method should have only one point of return - as if we're all still littering our code with GOTOs, and the concept of a "black-box" function was never invented.

The way these same people go on about multiple exit points, you'd think they were headlining in one of the grislier episodes of ER trying to patch up the latest guest-star casualty while predicting dire consequences for the patient as they lie, bleeding to death.

People who prefer the single exit point ([http://discuss.fogcreek.com/joelonsoftware/default.asp?cmd=show&ixPost=31001](http://discuss.fogcreek.com/joelonsoftware/default.asp?cmd=show&ixPost=31001)) tend to feel very strongly about it. But the reasons they give have never struck me as especially convincing. The following stream of generic reasons reminds me of the cookie-cutter platitudes that they roll out at the end of the more nauseating US TV series that seek to emulate ER, over the soul-grinding background warble of James Blunt:

   1. Bailing out early causes resource leaks. That's why we have the "finally" block. (If you're determined to have a single exit point, finally is the only way to achieve it. But purists take note, System.exit() still gets around it.)
   2. Multiple exit points make code harder to refactor. Yes, because simpler, clearer code is always harder to maintain.
   3. Multiple exit points is a return to GOTO and spaghetti code. Ironically, it's single-exit-point code that's the anachronism. The whole reason this misguided principle came about was the reaction to spaghetti code that was structured programming ([http://c2.com/cgi/wiki?StructuredProgramming](http://c2.com/cgi/wiki?StructuredProgramming)). In modern languages and runtimes, single-exit-point code is outmoded and can even be dangerous. For example, the ubiquity of exceptions means that no method is ever guaranteed to have a single exit point. Code as if it is, and you're asking to be caught out.
   4. Bailing out early creates an invisible "else" clause. What rubbish. A guard clause such as this:

if (account == null) return;

at the top of a method is much clearer, than:

if (account != null)
{ // 20 lines of code
// (that are totally irrelevant if account is null)
// later...
}
// and out we pop

Sometimes, trying to weave your code into a single return point results in setting of pointless flags and excessive nesting of "if..else" conditions. It's like wrapping a paper napkin around a seven-dimensional helix and trying to read the agile documentation off it. Figuring out whether each block of code is relevant to the current program state becomes a game of lining up the curly braces to figure out where each clause finishes.

It's easier to simply say: "Hey, I'm halfway through a method but I'm done. I'm outa here!" Artificially stretching the program flow to the end of the method just results in misleading code: implying that a block of code is relevant to a given state when the runtime really has no business still noodling around in there. If it's time to exit a method, exit the method already.

Adhering to an outdated maxim like "single exit point" results in a "one size fits all" approach to programming, which is hardly a good thing. But religiously hacking in multiple return points would of course be bad as well. If in doubt, go for the simpler, more expressive option which best communicates what the code means. It's more an article of faith than anything else. It's important to be able to take a step back and make a rational judgement call: this alone helps sort out the thinkers from the believers.

---

### Post by LaRoza on 2007-12-04
In my limited experience, multiple exit points make sense if done very early and for a good reason.

Randomly scattering them throughout code is probably a bad idea, but they can be useful, especially if they make the code more clear.

---

### Post by Wybiral on 2007-12-04
It depends... It's OK to make exceptions to the "good practice" rules when you're writing low-level software. If it's more efficient, some programs are OK to sacrifice "good practice" in order to achieve the performance they require.

That being said, most of us aren't writing such performance critical code as to warrant abandoning good practice. IMO, unless performance is critical, if your code requires GOTO, premature exits, globals, lack of exception catches/throws (if your languages supports them). Then you probably did something wrong during the design process.

---

### Post by CptPicard on 2007-12-04
I am *so* in support of the arguments expressed in the OP. Religiously avoiding "premature" exits leads to needlessly complicated code. Of course if, for some clean-up reason, you *shouldn't* exit inside of the function, then you shouldn't. But that's a call for the programmer to make.

Personally I have always found that if your function arrives at some returnable state at some point, it's just cleaner to return it immediately without saving state and explicitly unwinding out of your logic so that you can then return the stored state at the end. It's just confusing to wait like that.

I actually had a TA complain to me about this during a project we were doing for school... she came from business school and had been told that there ought to be just one return at the end of the function. She was pretty adamant about this in the face of like 6 of us CS majors, so we took a quick poll of students and other TAs and found that "immediate return" was favoured by a huge majority.

---

### Post by raul_ on 2007-12-04
If it makes sense I always make multiple return points. I don't see anything wrong with it. actually I find it pretty straightforward.

I think that the reason one's code is messy, it's because it's a mess everywhere, not just the return points. So, early planning is as valid as for the rest of the code. 

I think there is no unquestionable rule in programming, just things that work. They can be easier or harder to read, to maintain, to extend, but in the end, all that matters is that it works and it does what it's asked.

And if efficiency is asked, you should do the math with it too ;)

---

### Post by evymetal on 2007-12-04
If you've got a functional design or an itterative function then I would definately use multiple exit points.

For longer, non itterative code I often avooid it - I don't know why but it just doesn't "feel" right sometimes, I guess I am worried that I will later add an important manipulation at the end of the function, it will run fine, until the 1 time in a million that a particular condition is met, the function returns early, and that final transformation isn't done. This is especially true with numerics.

---

### Post by slavik on 2007-12-05
if statements cause your code to branch.

---

### Post by samjh on 2007-12-05
Agreed with the article author.

I've never fully understood the reasons behind single-exit-point-only doctrine.  Sometimes multiple exit points result in clear and simpler code.

There is the obvious caveat that developers need to be careful about the manner and positioning of their exit statements, but that always applies anyway.

---

### Post by bobrocks on 2007-12-05
Agree with the article author.

I much prefer to work with neat code that contains multiple exit points than messy code that has just one, I don't have any problems understanding it.

---

### Post by Wybiral on 2007-12-05
> **samjh said:**
> I've never fully understood the reasons behind single-exit-point-only doctrine.

IMO it's a convention. The same way indentation conventions and naming conventions don't actually HURT the program, but they make the code more manageable by having a set of guidelines. The problem is that they're too easy to abuse and result in a form of spaghetti code (where you can't trace the return point of a function) and can often create misleading results during the testing and debugging process. The way I see it, it's OK to use them when you have to. But if you do, you need to comment very explicitly how and why it's being used.

I also think another reason is that in most languages (but certainly not all), it just smells bad. It's a good sign that your code isn't modular enough or that you went about your design in a non-transparent way. It's fine when you need the efficiency, or when you write yourself into a corner, but it might be a sign that you need to step back and look at your design for a second, because there's probably a more elegant way.

But, I also think it applies more to higher-level languages. In most low-level languages it's probably going to be much more acceptable than in higher-level languages (where there are almost certainly more elegant and readable solutions). I'd say the same goes for things like globals, lack of exceptions, and goto's as well.

---

### Post by tyoc on 2007-12-05
Some times this days I see that I the same and the same over each exit point, not only a simple return statement, but a serie of things aplied before exit make the exist a funcion (or a call) doesnt make sense, thus grouping similar exits can be good practice IMHO, and you can easely check 1 exit instead of differents, when you have "easy" return procedures, it is OK to have them all the way.

Anyway, about the bad desicions for check return codes, I suguest reading this entry on my blog :P [http://tyoc.nonlogic.org/blog/20/11/2007/siendo-positivo-en-el-codigo/](http://tyoc.nonlogic.org/blog/20/11/2007/siendo-positivo-en-el-codigo/) for a resume (because is in spanish), always try to be to the point or "positive" to the point you want to achieve, tus you will avoid premature exits, sparsed exits, and more code writed that doesnt make clear what is the objetive of all that insane checks.

---

### Post by CptPicard on 2007-12-05
> The problem is that they're too easy to abuse and result in a form of spaghetti code (where you can't trace the return point of a function)

What are easy to abuse? Conventions? :) Sorry, I'm not exactly sure which side you're arguing but let's assume you mean the multiple returns...

In multiple return points finding both the return point and state are simple, just find the return statement. Without multiple returns, I find that the state of the routine itself tends to become contrived for the simple purpose of maintaining state until the one return point at the end, and at the end, you may even have to write some kind of a branching structure for the sole purpose of realizing the correct return value.

> I also think another reason is that in most languages (but certainly not all), it just smells bad. It's a good sign that your code isn't modular enough or that you went about your design in a non-transparent way.

Design shouldn't have much to do this, as every multiple return point function can be written in terms of single return. On the other hand, I find it difficult to visualize a design that seeks to avoid the need of multiple return states/values altogether by splitting functions into smaller chunks, and ending up something that is neccessarily good from an architectural point of view. Number of return points is a readability/aesthetics issue that should thus be orthogonal to overall architecture issues, as the function's goodness should be judged solely on the basis of whether it, looked at from the outside, performs some logical, reasonably isolated operation.

> But, I also think it applies more to higher-level languages. In most low-level languages it's probably going to be much more acceptable than in higher-level languages (where there are almost certainly more elegant and readable solutions).

In higher level languages returning early is even more acceptable because higher-level languages do more of the cleanup after you.

Seriously, I have a lot of recursive code in particular that is way easier to read when you just yield a value as soon as you can without bothering the reader any further than neccessary :)

---

### Post by aks44 on 2007-12-05
I read that article the other day (yesterday?) and IMHO it totally makes sense.

Not much to add to the article, it sums up my opinion quite well.

---

### Post by Lster on 2007-12-05
I have never seen multiple exit points misused to the point where I couldn't follow a program. I use them in many of my own projects when I have to and they are still very readable - even those with thousands of lines and multiple source files. The difference is I use them when it makes sense, not randomly.

---

### Post by achron on 2007-12-05
Having been on the receiving end of "can you make some changes to this code so we can tell WHY the routine is exiting?", I could tell you of the dark side of multiple exit points...

The particular routine in question was 1,500+ lines long (C code) and had 78 separate exit points. 

I'm not against multiple exit points, unless they exist as a manifestation of someone's laziness...

---

### Post by samjh on 2007-12-06
> **achron said:**
> Having been on the receiving end of "can you make some changes to this code so we can tell WHY the routine is exiting?", I could tell you of the dark side of multiple exit points...

The particular routine in question was 1,500+ lines long (C code) and had 78 separate exit points. 

I'm not against multiple exit points, unless they exist as a manifestation of someone's laziness...

Too much of anything can be bad, including multiple exit points.

I think your example is quite extreme, and I don't think any sensible poster here is suggesting that such use of multiple exit points is good.

Multiple exit points carefully designed for merit is OK.  Multiple exit points written as afterthoughts or because of mere convenience is not.

---

### Post by apoth on 2007-12-06
I think the original article is spot on. I don't mind a return at the start if a parameter is null, or similar. I think it makes the code far more readable.

I'd be unlikely to use multiple returns though unless either it was right at the start like that, or the method itself was so small, perhaps little more than an if-else that anyone reading the code would see all the return points without looking more than a few lines up and down.

---

### Post by tyoc on 2007-12-06
> The difference is I use them when it makes sense, not randomly.Perhaps Im missinterpreting, or streching to much the word "randomly", the fact is that "make sense" is personal tought.

I mean, there is no programmer that put random returns in the function... some like umm "close my eyes, not move up down again and again and where the cursor is put a return value" or some like that. The fact is that what you call "when it make sense" or the other guy "unless they exist as a manifestation of someone's lazines", from the point of view of the programmer writing it there is OK, if not he will not write it there.


From my blog-[post]("http://tyoc.nonlogic.org/blog/20/11/2007/siendo-positivo-en-el-codigo/")

```
 static boolean some(....){
    if( !accion1 ){
        DBGPRINTF("accion 1 cant be done");
        return FALSE;
    } else{
        if(accion2){
            if(accion3){
                //make something with resources of accion1, accion 2 y accion3
                ....
                // Finally after done
                return TRUE;
            } else {
                // free resources for accion1 & 2
               free(accion2);
                return FALSE;
            }
        } else {
            // free resources for accion 1
            free(accion1);
        }
    return FALSE;
     }
}

```Now look at first sight (the above) the complexity of reading the code is big.
¿But what happend if you try to be &#8220;possitive&#8221; in the design for this part of code?, that can be answer easely watching the following code

```

static boolean some(....){
    if(accion1){
        if(accion2){
            if(accion3){
                // make some with the resources of accion1, accion 2 & accion3
                ....
                // free the resources and return sucessfully
                return TRUE;
            }
            free(accion2);
        }
        free(accion1);
    }
    return FALSE;
}

```accion1, 2, n are to be avaluated to sucessful return, not to check the codes for failure, still I have the cleanings for possible errors, and 1 exit for sucessfull (like before), but 1 exit for failure difference, also see the code is readed like accion1->accion2->accion3 clearly, the first code doesnt have that easy reading. It is a simple guide, code for sucessfull paths, not for the bad paths ;) I call that "code positive" & "to the point".


1 of the answer there (in the linked original post) say some like "the point of 1 exit is to think like that, if you have that in mind it will be more easy to have single point of exit, or if there are more, they will be not as many if you havent take in to account code for 1 exit"

-------------------------------


If you gona have exit for all cases that relate and jump there with goto (because you dont want write the code 1 time and another time, making different points of the code, the same steps for exit), like exit with sucessfull value (in more than 7 places), exit with value OK but with warnings or default values (in more than 4 places), failure (in more than 17 places), etc. Call the labels like that, and jump there for such an exit. only 1 point to refactor, multiple different exit points that are semantically the same exit point **and built-in the code** (aka in the case of failure 17 places replaced with 1 place to modify in-code) (or also you can write a macro... or a function for free resources, at end will be the same (it will exit) but maintability or readeability can take some good or bad of that (like, why make a function for free resources if I want to have the less code?...).
:guitar:


PS: yes, my example is oversimplified, but Im sure than more than 1 in the world code in the first way ;)... go and watch your codes ;) hehehe.

---

### Post by aks44 on 2007-12-06
> **achron said:**
> The particular routine in question was 1,500+ lines long (C code) and had 78 separate exit points.

Heh, in the first place the problem was not with the 78 exit points, but with the 1.5kloc routine. ;)

---

### Post by slavik on 2007-12-07
if (some condition) exit();
if (some other condition) exit();
exit();

becomes:

if (some condition) goto end;
if (some other condition) goto end;
end:
exit();

---

### Post by tyoc on 2007-12-07
You completely miss it...

> the same steps for exitI dont mean exit of exit the program, but exit the function... also Im talking about steps not a single line, see you even need to use {} for the single statement in if clause. I see you only use "step" instead of steps, and also only have 2 points (of 1 line...) instead of 

> like exit with sucessfull value (in more than 7 places), exit with value OK but with warnings or default values (in more than 4 places), failure (in more than 17 places), etc.See if the code for suchs points is (at less and without take the "more than N places"):[LIST]
[*]  sucessful exit is 5 +return lines long: 7*6 = 42
[*] failure like 4 lines +return (2 checks and 2 frees): 17*5 = 85
[*]exit with value OK but with warnings (6 lines): 6*4 = 24[/LIST]Add them 42+85+24 = 151 lines, and a total of 7 + 17+ 6 = 30 equal code points (have you listed some time dont do it 2 times?) with is respecive return (30 of them).

Doing it with gotos, you still have 30 different goto places, but only 6+5+4 lines of code (and they are not repeat all allong the function exits) and only 3 returns plus 3*1 new labels, thus 30+6+5+4+3+3=51 lines of code.

Do your math if you don't trust me.

Also I have said " If you gonna have exit for all cases that relate and jump there with goto", is a suggestion, not a rule, but doing that for a single 4 lines of code for a function that would be ars. Is a way to manage "complexity" and readability ;), Isn't a bad practice from my POV and I also see the maths at all (also the readability, ie, you can have at first sight 3 possible exits that a function can have, and without see the whole repetitive 30 equal code points (ie, if you read them all separate, then you will see, hey some of this code is equal or semantically near the same!!!, which therefore I can conclude that there are 3 semantics exit points, which 7 of them are success, 17 are failure and 6 are workarounds or some like that), and you can see which gotos go to which type of leave the function, ie, you don't need be watching o this exit do the same that the other but in this case, this free is pass because this resource wasn't allocated in that place), also it should be easy to beak in each "goto" like you will do in each return ;), if you really need to debug your code.

Exaplain it in other way, is like if (I will write some pseudo-nothing here:

```

val func(arg1, ..., argn){
    LeaveRegister(NORMALEXIT)
    LeaveRegister(DEFAULTEXIT)
    LeaveRegister(FAILURE)
    LeaveRegister(WARNINGEXIT)
    LeaveRegister(WORKAROUND)
    LeaveRegister(HACKEDVALUESEXIT)

    ...
    // complex function with exits: 15 normal, 7 default, 23 failures, 13 warning exits, 11 work arounds, 4 hacked values (corner cases??)
    // 1 example like
    some fune code
    {
        more fun
        return NORMALEXIT
    }
    ....
}

```LeaveRegister is "undefined" but for show the point, it can be a goto, a macro, a clear function, etc...

You will call that "organized code" because the code is in a function??? and it will be like call the function for do the clear and return?, you normally introduce "duplicate code" inside a function, why the so normal procedure/steps for leave a function isn't like that, you see, reduction of duplication in functions work, specific gotos for leave a function when there is to much duplicate exit procedure/steps is good to.


Now, going furter, perhaps you can argee that, my normal returns doesnt have "equal shape", then take the necesary steps for make them generic, I mean, if you have inner locals allocated (like inside for, if else), liberate them in place, also perhaps you are passing a inner local to deep, and repeating the allocation of the same local acros different if, elses, fors, whiles... you know that when you do some like
```

...
if(boolean){
    struct sz *z;
    float x;
    ...
    free(z);
    return x;
}else if(boolean){
    struct sz *z;
    float x;
    ...
    free(z);
    return x;
}else{
    float x;
    ...
    return x;
}
...
```You are being lazy? I mean you write them in place, because you dont want to go up and put them outside?, at end, you will duplicate your work 2.5 times in this specific case, and move the returns and frees inside the logic of if else block.

 I'msupposing for more large and repetitive function and more than 1 line for clean an exit than the above simple example of some tiny lines, but that tiny lines can be coded as for example like:

```
    struct sz *z
    float x

    if(boolean){
        ...
        x = value1;
        ...
        goto FREEANDEXIT;
    }else if(boolean){
        ...
        x = value1;
        ...
        goto FREEANDEXIT;
    }else{
        ...
        x = value1;
        ...
        goto EXIT:
    }
FREEANDEXIT:
    if(z)
        free(z)
EXIT:
    return x
```Now supose to have fun that you need liberate 10 different resources z1, z2, z3, z4, z5, z6, z7, z8, z9, z10 before you leave, and checking if they are allocated?, Im sure you can group similar deallocation procedures for reasemble the FREEANDEXIT and EXIT labels, remember that you can have more than 1 return, the point is not to have exactly only 1 return for a complex funciton, but to reduce the complexity of analyze the exit points in a simple way (and almost all in the same place), also with labels, you can give them more meaning that FREEANDEXIT, like SUCESSFULL

For example (supose I have a complex function), if I pass you **alone** the lines and I say, Im having problems with this lines, it doesnt return the correct value in x and after some time, the program crash

```

    RELEASEIF(t);
    RELEASEIF(z);
    return x;

```There is no semantic if this is successful or failure, you need to know the code path for get the meaning if sucessfull or not.

But if I give you
```

SUCESSFULL:
    RELEASEIF(t);
    RELEASEIF(z);
    return x;

or

SUCESSFULL:
FAILURE:
     RELEASEIF(t);
     RELEASEIF(z);
     return x;

```This alone are more informative be itself. But still you need to check the code path not for know the meaning for get there, but for search the bug,




---> Also please note, that this thought related, is not the same that what I called here "positive code" (check for sucessfull, not for failure) & "to the point" (go with the more short path to the result... being positive) that can also reduce the number of exits from my POV, even if possible and help readability and "understan"ability to read the code, combine both "positive code" & "to the point" with semantically equal exits for a function (in fact is "not a problem" to have many exit points, but I think help something like the concept of " LeaveRegister(NORMALEXIT)" and that in this case can be implemented with the simple and "discrete" usage of goto...).

As a fact, I normally don't use that style, but little times I can refactor repetitive end things like that, when they extend the code much and it make sense do it the other way (is like doing a **[COLOR=Black]mini-function[/COLOR]** for clear in certain conditions... but instead of "**call it**", you "**name it**" -->goto name), but I try more to code positive and to the point, thought I take care of it, sometimes I watch me don't doing it like that.

---

### Post by tyoc on 2007-12-07
Now that I have clarificated my POV on this subject, I think I can get over the arguments 

> 1. Bailing out early causes resource leaks. That's why we have the "finally" block. (If you're determined to have a single exit point, finally is the only way to achieve it. But purists take note, System.exit() still gets around it.)
I don't get this... the same as exit, we can call it, but we are getting out of a function, not from a program...

I know my english is not quite well, but yes, I like to talk about this things, in fact, I can redirect people to: [http://www.ogre3d.org/phpBB2/viewtopic.php?p=236192#236192](http://www.ogre3d.org/phpBB2/viewtopic.php?p=236192#236192)

> 
   2. Multiple exit points make code harder to refactor. Yes, because simpler, clearer code is always harder to maintain.
 Still don't get what he say, he mean, he call simpler to have repetitive parts of code in a large function instead of have a function for call it (yes I know there is no "LeaveRegister(NORMALEXIT)", but we can work with what we have at hand). From my anteiror maths, they are about 42+85+24 = 151 lines of code, and a total of 7 + 17+ 6 = 30 equal code points, **suppose** that the function is about 700 to 1000 lines thus it will be from **21%** to **15.1%** aprox of the actual code of the func, if you do it for this specific case in the other way, you will have 30+6+5+4+3+3=51 lines of code that will be from **7%** to **5.1%** of actual code, how is that **21%** to **15.1%**  of code is more easy to maintain than  **7%** to **5.1%** of actual code... because it is almost equal?, Im sure if you don't have good memory, you will fail if you add 1 extra resource, and you forget it put in 1 place of that repetitive code. 

[COLOR=Red][COLOR=Blue]The anterior calculation is wrong, because I assume that the code was 700 to 1000 lines including exit steps (thus reducing the actual code doing other work that is not free), but there are 151 - 51 lines = 100 lines of extra code doing other work. Thus not being "fair". I will change the calculation rules to the follow, we have working code for the same function implemented in 1000 lines and 700 lines of code not doing exit steps plus the exits lines

a) 151 lines of exit at different points, or
b) use the source look and handle the semanticall same exits with goto (like the "LeaveRegister(NORMALEXIT)" that we dont have. Also that look like exceptions lol... work it with what you have... or your lang provide you).

Thus the case for 1000+ 151 and 700 + 151 are **13%** and **17%**
Thus the case for 1000+51 and 700+51  are **4%** and **6%**

See that being more less code it go up the % (being unmutable the count of those lines).

-> Still dont see how he guarantee [/COLOR][/COLOR]that maintaining **13% or 17%** of sparse code in the functions is more easy than maintain **4% or 6%** of condensed code, with spared entry points. (is sparsed or spared?)
I think that multiple exit points are only simple and easy to modify if you code "positive and to the point" I will show it in the next number.

"Yes, because simpler, clearer code is always harder to maintain.", I think it should be more easy, is a contradiction other way... "simpler and clearer" should be more easy to maintain (how he get to the conclusion than "simpler and clearer == harder to maintain"???), is a real contradiction think other way... **_what is harder_** is to get to a "simpler and clearer code" and the proof is this real thing ;) of all this argumentation :P.

> 
3. Multiple exit points is a return to GOTO and spaghetti code. Ironically, it's single-exit-point code that's the anachronism. The whole reason this misguided principle came about was the reaction to spaghetti code that was structured programming ([http://c2.com/cgi/wiki?StructuredProgramming](http://c2.com/cgi/wiki?StructuredProgramming)). In modern languages and runtimes, single-exit-point code is outmoded and can even be dangerous. For example, the ubiquity of exceptions means that no method is ever guaranteed to have a single exit point. Code as if it is, and you're asking to be caught out.
funny that about "ubiquity" hehe, First I redirect again to: [http://www.ogre3d.org/phpBB2/viewtopic.php?p=236192#236192](http://www.ogre3d.org/phpBB2/viewtopic.php?p=236192#236192) and I remember you about my bad English, Ironically is "ubiquity" refer in back to "exceptions a hided goto" thingy called in that thread, LOL.

Structured programming are only named gotos, they have give name to common structures of goto for you not to fail and terminate doing spaggetti code (is a syntactic sugar :P... taking it in the context of gotos like back support), at end all go to the machine, and the machine only know how to goto to the next instruction, it is very primitive.

It is dangerous, because exceptions make you jump out :P of the normall flow (that sound familiar??) (a goto with a disfraz/mask of guard function in the stack? aka try, catch, finally?, you see more sintactic sugar over goto, like is structured programming in some way :P), even I found a patent on implementing exceptions that include directly the word goto (hope the linked doc still is there in the link).

> 
   4. Bailing out early creates an invisible "else" clause. What rubbish. A guard clause such as this:

if (account == null) return;

at the top of a method is much clearer, than:

if (account != null)
{ // 20 lines of code
// (that are totally irrelevant if account is null)
// later...
}
// and out we popWhat this guy dont see is the fact that the assertion
> creates an invisible "else" clauseis a fact.

Then he argee
>  // 20 lines of code
// (that are totally irrelevant if account is null)
// later...Yes, what a observation!, that fact is because it has to do with the code result we are seeking, if it is not null we can proceed.

Do you remember what I call "code positive" & "to the point"?


```

the article
function(p){
   if(p == NULL) return;
   // else { // hided else
   // do work with p and related stuff
   ...
   // } hided else close
}

the other way, I also be more explicit and name it "positive code" & "to the point"
function(p){
   if(p != NULL){
      // do work with p and related stuff
      ...
      return;
   }
   // else { // hided else
   // this hided else as a matter of fact, doesnt contain code
   // } hided else close
}

```The point here is that people tend to generalize... a simple function and a simple line that rule all other posible functions and size of them and internal behaviour...

But playinf fair with this little rules... aka extending his example (note that is not a case of internal check of values, but check of args....)

```

the article (ok, is not writed there, but an extension of my mind... trying to be more explicit)
function(p1, p2, p3){
   if(p1 == NULL) return;
   // else { // hided else for p1
   if(p2 == NULL) return;
   // else { // hided else for p2
   if(p3 == NULL) return;
   // else { // hided else for p3
   // do work with p and related stuff
   ...
   // } hided else close for p3
   // } hided else close for p2
   // } hided else close for p1
}

the other way, I also be more explicit and name it "positive code" & "to the point"
function(p1, p2, p3){
   if(p1 != NULL){
      if(p2 != NULL){
         if(p3 != NULL){
            // do work with p and related stuff
            ...
            return;
         }
         // else { // hided else for p3
         // } hided else close for p3
      }
      // else { // hided else for p2
      // } hided else close for p2
   }
   // else { // hided else for p1
   // } hided else close for p1
}

```Coding with "positive coding" and "to the point", you dont get any jumps, because the "hided elses" make you jump, you are actually going direct to the calculation and without take those "hided" jumps. You will only jump 1 time (not 3 because it need skeep 3 returns at start) if and only if there exist a invalid pointer. and also you have 2 exit points for this case, 1 sucessful (and direct without intermediate jumps) and 1 fail because any of the 3 is invalid. (Yes you can code the check for pointers in a single if clause and both samples will have near the same code... still the check for nulls firs and then calculate will have an extra jump before do calculation, dont trust me?? let see it


```

the article (my generalization with his rules)
function(p1, p2, p3){
   if(p1 == NULL || p2 == NULL || p3 == NULL) return;
   // else { // hided else for p1 & p2 & p3
   // do work with p and related stuff
   ...
   // } hided else close for p1 & p2 & p3
}

the other way, I also be more explicit and name it "positive code" & "to the point"
function(p1, p2, p3){
   if(p1 != NULL && p2 != NULL && p3 != NULL){
      // do work with p and related stuff
      ...
      return;
   }
   // else { // hided else for p1 & p2 & p3
   // } hided else close for p1 & p2 & p3
}

```OK OK, perhaps you will say, OK I get the point of that "hided else clausule" and the hided extra jump that is the real impact of that hided else clause, but what if you strip  those comments and show the funcitons? for your pleasure:

```

article
function(p){
   if(p == NULL) return;
   // do work with p and related stuff
   ...
}

"positive code" & "to the point"
function(p){
   if(p != NULL){
      // do work with p and related stuff
      ...
      //return; // see that even I dont need this return here!!!
   }
}

```continue with the more large example:
```

article (generalization)
function(p1, p2, p3){
   if(p1 == NULL) return;
   if(p2 == NULL) return;
   if(p3 == NULL) return;
   // do work with p and related stuff
   ...
}

"positive code" & "to the point"
function(p1, p2, p3){
   if(p1 != NULL){
      if(p2 != NULL){
         if(p3 != NULL){
            // do work with p and related stuff
            ...
            //return; // see that again I dont need this return.. (OK the guyis not returning values, so do I
         }
      }
   }
}

``````

article (generalization)
function(p1, p2, p3){
   if(p1 == NULL || p2 == NULL || p3 == NULL) return;
   // do work with p and related stuff
   ...
}

"positive code" & "to the point"
function(p1, p2, p3){
   if(p1 != NULL && p2 != NULL && p3 != NULL){
      // do work with p and related stuff
      ...
      //return; // O yea, again, I dont need this return!!! .. (OK the guyis not returning values, so do I
   }
}

```I guess that is all in my part, opinions?? :P.:guitar:
to large?? 2 post in a row?? I need go1 sleep and greet morfeo? :P

blah, "another proof" about the else clause.

```

void f(int *p){
    if(p) return;
    else {
    p = (int*) 0x45;
    }
}

/*
void f(int *p){
    if(p) return;
    else ;
    p = (int*) 0x45;
}
*/


/*
void f(int *p){
    if(p) return;
    p = (int*) 0x45;
}
*/

int main(){
    int *i = (int*)0x10000;
    f(i);
    return (int)i;
}

```make the a.out and check the md5sum for both programms, changing the implementation of f for 1 of the others, same result for this simple function.

---

### Post by slavik on 2007-12-07
```

void free_wrapper(int n, void *arg) {
  free(*arg);
}

blah = malloc(some_ram)
if (blah) on_exit(&free_wrapper, blah);

...
//somewhere in code:
exit(0); // or return 0; (from main)

```

how is that for cleaning up resources?

---

### Post by tyoc on 2007-12-07
It is about program termination not about function termination.

It will be nice from my POV if on_exit functions registrants can be attached to the current running function not to the current running process, **but** instead of being called in reverse order of register, it will be called only the wrapper that is indicated like return SUCESWRAPPER or return FAILUREWRAPPER, we have gotos for do this, you can name the end and "call it"/"name it", semantically take it like a little-inner-built-function for exit on certain semantics (that perhaps relate more or less to presiscely more than 1 exit point in that function).

Exiting from program is not the same of exit a function, in a program you can have multiple threads, but a thread can only execute 1 function at a time, thus there is a big difference exiting from a function than from a programm.


And rememmber that is only a suguestion, if you really have a function like 700 or 1000 lines of more of actual code not related to exit function steps & cleanup, plus another + 100 lines of steps here and there, hopefully doing some refactor can cut the exit code to a 1/3 or at less < +100 lines of extra repetitive exparsed code in a large function. Also I suguest use the "code positive" & "to the point".

"Positive" has no defined meaning until the programmer define it, supose I wanth to check stricmp for the 2 string being > than the 1, thus you have already defined what is the positive path now get there "to the point"

pseudo-nothing:
```

stricmp(s1, s2) 
   is 0 return FALSE
   is > 0 return FALSE
   is< 0 return TRUE

```Dont do that, why check the paths that doesnt mean nothing to our positive aproach?, you see, even you first check for what we dont want!!!

```

 stricmp(s1, s2) 
   is< 0 return TRUE
  return FALSE
 
```You see "positive" to what we want, check if s2 > s1, it even dont need those extra "checks"... return to post 18 [http://ubuntuforums.org/showpost.php?p=3902723&postcount=18](http://ubuntuforums.org/showpost.php?p=3902723&postcount=18) and you see that people normally code like that, they dont have in mind "positive code", they have in mind check all the returns for failure and do more complex and extra lines doing that, still without check directly for the "bad codes", you know that if you dont get "to the point" in the "positive code", then something has fail, thus is time to check it, not before

In other words is an application to code of lazyness... or how is called? that which evaluate some code only when is needed, we dont need unsucesfull (extra code for manage it) results untill we will recover, but first, we will try to get to the point being positive about the path, if that positive path can't be terminated, is time to watch the errors.

If you try to paint, do it, if you can't, check why you can't, if you gona open by example 4 files, open them, if you fail to open 1, but you need the 4, thus the positive shortest path has fail, but if not necesary, do something with the other 3 that mean that positive code has not failed completely, but has get in a short path to a point that you can work with 3 files, I think is not need be nested if like in the example above, is something (I repeat myself) like try to get in the more short path to what you want to achieve, if not possible, is time to do all the needed checks. I will try to exemplify that later.

---

