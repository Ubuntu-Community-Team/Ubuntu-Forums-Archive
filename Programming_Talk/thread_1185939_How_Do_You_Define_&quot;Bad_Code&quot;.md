---
title: "How Do You Define &quot;Bad Code&quot;?"
date: 2009-06-12
forum: Programming Talk
---

### Post by Sinkingships7 on 2009-06-12
Since the beginning of programming, this definition has changed after every abstraction level. Why? Simple: we keep finding more ways to [write bad code]("http://www.exmsft.com/~hanss/badcode.htm"). And now, through the power of encapsulation and the such, we can now write bad code for everyone to use, whether or not they know it!

On to a more serious note now. Many developers, programmers, and hackers have different points of view on what defines "bad code". Jeff Atwood made a blog post back in '06 containing a comprehensive list of bad design choices, which he labeled ["Code Smells"]("http://www.codinghorror.com/blog/archives/000589.html").

So, I'm interested. How do YOU define "bad code"? Just what is it that makes certain code... bad? Examples are more than welcome. Flames are not.

---

### Post by Mirge on 2009-06-12
Example of bad code:

```

#!/usr/bin/perl -w

put anything else you want here.

```

Naaahhh I'm just kidding, I couldn't resist. Didn't we just go over bad code definitions & examples in another thread?

---

### Post by Sinkingships7 on 2009-06-12
> **Mirge said:**
> Example of bad code:

```

#!/usr/bin/perl -w

put anything else you want here.

```

:D
> **Mirge said:**
> 
Didn't we just go over bad code definitions & examples in another thread?

Sorta kinda. If it's the thread I'm thinking of, it was completely off-topic, which is my initial reason for making this post.

---

### Post by Mirge on 2009-06-12
That's true. Well, I guess I wouldn't really "define" bad code as something specific, but here are some things that can bother me:

1. Lack of comments explaining what code is supposed to do (especially in larger projects)
2. Lack of proper indenting/whitespace (readability).
3. Repeating the same bit of code over & over without utilizing a function/subroutine.
4. System calls when the program was meant to be portable.
5. Purposely generating obfuscated code just to show how cool you are.

---

### Post by jflaker on 2009-06-12
spaghetti code:
Code that is top-down programming that branches with goto's.  Is not very structured and uses the different variable for the same thing, as if the programmer lost track of what variables were used and where.

no comments:
I need to guess and hope to understand the code.  There are several ways to program things, some overly complex and others that seem incomplete, but they usually never are what I expect.

and my BIGGEST PET PEEVE!:
HARD CODING values that have the possibility to change.
Yes, if some value has the possibility of changing in the future, NEVER, EVER, EVER, EVER, EVER, EVER hard code this value into the compiled object.  Not only do I need to open the program and change it (I usually make it a soft-coded value), but now I must bring the program through the quality control process and get all sorts of signatures before I can promote it to a production environment (that is in business) or just test the heck out of it just to make sure I didn't break something.

---

### Post by Mirge on 2009-06-12
> **jflaker said:**
> spaghetti code:
**Code that is top-down programming that branches with goto's.  Is not very structured and uses the different variable for the same thing, as if the programmer lost track of what variables were used and where.**


Amen.

---

### Post by dunkar70 on 2009-06-12
I would consider bad code to be anything that does not live up to the expectations set by the author. If I write a snippet for my own internal use, who cares how I do it? If I provide that code to others, I should set expectations for how it should be used and what issues it may have. The idea of open source is that anyone else can improve what we start. Let a neophyte start a new (and possibly brilliant) idea, then let experienced developers with best practices refine the ideas to create a scalable and stable product.

---

### Post by Sinkingships7 on 2009-06-12
> **dunkar70 said:**
> I would consider bad code to be anything that does not live up to the expectations set by the author. If I write a snippet for my own internal use, who cares how I do it? If I provide that code to others, I should set expectations for how it should be used and what issues it may have. The idea of open source is that anyone else can improve what we start. Let a neophyte start a new (and possibly brilliant) idea, then let experienced developers with best practices refine the ideas to create a scalable and stable product.

Decent approach. So, you do not believe that there is really any guidelines which every developer, beginner or not, should follow?

---

### Post by amauk on 2009-06-12
- Functions / methods that try to do too much at once
- Misuse of the preprocessor (C / C++)
- Mixing up coding styles / naming conventions
- stuff in header files that should be in the source files (or vice versa)

---

### Post by oldsoundguy on 2009-06-12
If you are interested in seeing the results of very bad code, fire up Firefox in Ubuntu and go look at some of the auctions on eBay that use various "auction frameworks and templates" instead of the sellers writing their own and testing it before releasing it.  And that is just HTML, not INSTRUCTIONAL CODE!!  If mistakes can be made, someone will make them!! LOL

(the problems with audio and video in Ubuntu are another great example of code gone bad! .. I lost sound on three different computers a few months back with a borked update .. both analog and digital. BTW .. and they have yet to correct the issue.  Things were fine for a LONG time before that!)

So, BAD code does exist in the real world and we see it every day!

Only thing, in Linux, most of the time it does not eat the computer or the OS .. we just get a flat tire. And some good guy/gal comes along to help fix it.

That can't be said for MS .. there things DIE and can not be brought back to life because ONLY MS can work on it!

---

### Post by dunkar70 on 2009-06-12
Within any organization or group, there are usually a set of best practices that allow for faster and easier integration or modification. In the open-source arena, there are too many disparate groups with different agendas and purposes to have one global (and detailed) set of rules. There can be a set of best practices at a generic level, but each group will customize their own set of rules. Consider XML as a generic set of best practices with WML, SMIL, and other XML-based markup languages as purpose-specific with refined rules. 

What one person might consider a best practice may be impractical or oddly inappropriate for another. I certainly do not have all the answers, but when people start to define rules as absolutes, we lose flexibility and agility.

---

### Post by soltanis on 2009-06-13
At the risk of being one voice in an exploding topic, I have one criterion for "bad code":

Code I cannot understand after I've read it.

Pretty broad-encompassing (and dependent on things like my intelligence and alertness level), but I don't care about structure, organization, comments, whatever -- if I can't understand it, I don't like it.

---

### Post by lykwydchykyn on 2009-06-13
If it has a comment at the top with my name and email address, it's probably bad code.

No matter how much I aspire to stay organized, I always walk away from a project feeling a little soiled by what I've written.  Especially if it's PHP.

---

### Post by TheBuzzSaw on 2009-06-13
bad code:
```
if (x > 10)
    return true;
else
    return false;
```

good code:
```
return x > 10;
```

---

### Post by jimi_hendrix on 2009-06-13
anything in VB

---

### Post by Mordred on 2009-06-13
I am mostly programming in C.

Bad code for me is code:

1. That uses global variables everywhere.
Some people consider function arguments to be optional :(
This makes code unreadable and very hard to debug.

2. Lack of comments. I am working as a programmer in a large
company and have seen already quite some source files with literally 
no comments except for some commented out code.

3. Which brings me to the next one, some programmers just do not trust
their version system so they leave redundant code commented out or
under #ifdef BLAHBLAHBLAH #endif.

4. Hard coded values are of course also a great annoyance updating a 
source file with hard coded values is always very 'exciting' ;)

5. Code that has no clear interfaces between the different sub-blocks.
All to often I see all functions of a source file to be exported in
the header file. A header file needs to contain the bare minimum for
other sub-blocks to use this module.

Anyway, just my 2 cents, feel free to disagree :D

---

### Post by benj1 on 2009-06-13
> **soltanis said:**
> At the risk of being one voice in an exploding topic, I have one criterion for "bad code":

Code I cannot understand after I've read it.

Pretty broad-encompassing (and dependent on things like my intelligence and alertness level), but I don't care about structure, organization, comments, whatever -- if I can't understand it, I don't like it.

to be fair most of it does ultimately boil down to readability(even the examples you cite as not caring about), the only other i can think of that is separate is efficiency (in program execution), and even then i suspect more often than not readable code is efficient code.

---

### Post by stevescripts on 2009-06-13
For a smile or two, and some insight into bad code - take a few minutes
to browse:  [http://www.freevbcode.com/ShowCode.Asp?ID=2547](http://www.freevbcode.com/ShowCode.Asp?ID=2547)  ... tongue in cheek humor with a purpose.

Personally, I like it when code is written as self-documenting as possible, and in a clean consistent style.

For anyone who has never read that essay - enjoy!

Steve

---

### Post by jpkotta on 2009-06-13
Two things I really hate are copy-and-paste code and magic numbers.  

Copy-and-paste code can really refer to two things.  One is that you go on the web and find some snippet of code that does what you want, and just paste it in without completely understanding it.  The other thing, which is arguably not as bad but pisses me off more (because I end up dealing with it more), is repeating yourself in code instead of making a subroutine or loop or something.  It shows a lack of understanding and laziness.  It is almost always harder to understand, and usually ends up being more work later.

Magic numbers are literals that should have been symbols, like
```
for (i = 0; i < 5; i++) {
```
instead of 
```
for (i = 0; i < array_size; i++) {
```

I also hate CamelCase and tabs for indent, but that's just a matter of preference, and I have my editor setup to work well with those anyway.

---

### Post by hessiess on 2009-06-13
Code with absolutly no comments whatsover and uses a lot of global variables.

---

### Post by TheBuzzSaw on 2009-06-13
This is actual code from a friend's program:
```
if (keepPlaying == "no" || keepPlaying == "No" || keepPlaying == "NO")
```
*facepalm*

---

### Post by lykwydchykyn on 2009-06-13
> **TheBuzzSaw said:**
> This is actual code from a friend's program:
```
if (keepPlaying == "no" || keepPlaying == "No" || keepPlaying == "NO")
```
*facepalm*

I guess if I say "nO" I'm just out of luck. ;)

---

### Post by lykwydchykyn on 2009-06-13
> **TheBuzzSaw said:**
> bad code:
```
if (x > 10)
    return true;
else
    return false;
```

good code:
```
return x > 10;
```

I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?

---

### Post by Sinkingships7 on 2009-06-13
> **soltanis said:**
> At the risk of being one voice in an exploding topic, I have one criterion for "bad code":

Code I cannot understand after I've read it.

Pretty broad-encompassing (and dependent on things like my intelligence and alertness level), but I don't care about structure, organization, comments, whatever -- if I can't understand it, I don't like it.

Aye. In fact, this is what it all boils down to. A lot of programmers have the tendency to dislike almost any code that they themselves did not write. In such a world, everyone writes bad code. Would you say that there's any (mostly) universal bad code? Something simply no one should be able to tolerate?

---

### Post by Sinkingships7 on 2009-06-13
> **lykwydchykyn said:**
> I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?

I've always wondered the same thing. When it comes down to optimization, they both are likely to produce the same assembly (and then machine) code. So the "inefficiency" lies in the way it's written and read. But the if(this)return(this)else(return this) method, for me, is easier to read at first glance. The evaluate-and-return-in-one-line method helps for space efficiency, which can make the overall code easier on the eyes.

---

### Post by Sinkingships7 on 2009-06-13
> **jpkotta said:**
> Two things I really hate are copy-and-paste code and magic numbers.  

Copy-and-paste code can really refer to two things.  One is that you go on the web and find some snippet of code that does what you want, and just paste it in without completely understanding it.  The other thing, which is arguably not as bad but pisses me off more (because I end up dealing with it more), is repeating yourself in code instead of making a subroutine or loop or something.  It shows a lack of understanding and laziness.  It is almost always harder to understand, and usually ends up being more work later.

Magic numbers are literals that should have been symbols, like
```
for (i = 0; i < 5; i++) {
```
instead of 
```
for (i = 0; i < array_size; i++) {
```

I also hate CamelCase and tabs for indent, but that's just a matter of preference, and I have my editor setup to work well with those anyway.

How different is copy-paste code from using a library? It's a dangerous method, no doubt, because if you're not smart, you don't know if the code is really any good. Blind faith is something one should not operate on when taking code from others. Also, I say it's weak. Do It Yourself(tm) :p. 

Magic numbers is something I think we can all agree on. Universally speaking, they're a mess at best, and a disaster most of the time.

---

### Post by scourge on 2009-06-13
What I consider bad code, partly because I've made these mistakes myself:

1. Boolean function parameters

When I see code like "foo(false)" I usually have to find the function declaration of "foo" to know what exactly "false" stands for. Now if instead of "false" we had an enum value with a descriptive name I would know what's going on just by looking at the calling code.


2. Singletons

Most programmers agree with me that global variables are bad, but they still use singletons which ARE essentially global variables. I just love it when I have to initialize a bunch of global resources in a specific order before I can safely create or use an object of type X. Maybe X needs database access, but instead of asking for a handle to the database in the constructor, it secretly uses a singleton to get that handle. And what if I forgot to initialize the database? Will the compiler throw an error? Of course not, the application will just crash in some really unfunny way.


3. Untestable code

My previous rant about global state continues. It's sometimes almost impossible to write unit tests for classes that grab their dependencies from global variables or singletons. The same applies to classes that privately allocate their dependencies. Then you can't use dependency injection, which means no mock objects, which means no proper unit tests.

When classes get their dependencies via the constructor, the class isn't just testable, but it's more generic as well.


4. Too many if/switch statements

If your code looks like this:
```

if (vehicle == Truck)
  //
else if (vehicle == Sedan)
  //
else if (vehicle == Tank)
  //

```

... then you should probably replace the mess with inheritance and polymorphism.


5. Misleading documentation

People often put too many implementation details in the documentation/comments. And when the implementation changes (but the interface doesn't) the documentation becomes obsolete and misleading.


6. C/C++ wrappers that make POSIX code look like WinAPI code or vice versa

I used to have code like this in one of my own programs:
```

#ifdef WINDOWS
   #undef CDECL
   #define CDECL __cdecl
#else /* not WINDOWS */
   #define CDECL
   #define HMODULE void*
   #define LoadLibrary(x) dlopen((x), RTLD_LAZY | RTLD_LOCAL)
   #define GetProcAddress dlsym
#endif /* not WINDOWS */

```

I thought it was clever, but it made my cross-platform code look like Windows code.

---

### Post by asbuntu on 2009-06-13
Code that allocates memory, and then does not verify that the allocation succeeded.

Code that allocates memory, and then does something to memory _outside_ of the original allocation.  (The classic "off by 1" problem is but one example.)

Code that forgets to deallocate, or leaks, memory.

Code that deallocates memory and then forgets that it does not own that memory any more, proceeding instead to use it further.

And my favorite (actually more a problem in philosophy), a programmer that says "but the program is working correctly".  This is a case where we tend to think that the portions of the code that we did not modify are perfect, and the truth is far from that.

---

### Post by simeon87 on 2009-06-13
> **lykwydchykyn said:**
> I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?

Multiple return statements in a function is not bad, it's actually a necessary way to elegantly solve certain problems. For example, linear search in an array and return immediately when an element has been found (and a return null; at the end to indicate failure). The example posted by TheBuzzSaw is different because it essentially says that true should be returned when a certain condition is true, and false otherwise. But that's just the same as returning that condition/boolean value right away.

---

### Post by asbuntu on 2009-06-13
> **lykwydchykyn said:**
> I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?

I think the CS teachers are emphasizing the opinion that there should be one way in, and one way out, of any piece of code.  That, I think, goes back to the structured programming paradigm.

*Not that I'm against structured programing - I happen to prefer it but, in a shop with multiple levels of (shall we say) competence, an attempt to be purely structured can be destroyed by someone else not understanding it and placing a period in the wrong place in one of my beautifully crafted COBOL programs.  Oh well.*

More to the point, in my opinion, simplicity is preferred.  I would go for the multiple returns.  The alternate is depending on the (intended) side effect that an assignment/comparison expression does have a value.  As an example...
```

if ((fd = fopen("myfile")) != NULL) {
... do some process
} else {
... handle exception
}

```

is concise, but not clear to everyone.

---

### Post by TheBuzzSaw on 2009-06-13
> **lykwydchykyn said:**
> I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?
No, I was not targeting the fact that there are multiple return statements. I use multiple return statements all the time. It's just silly to test for a condition and return true/false based on that condition and *only* that condition.

---

### Post by jpkotta on 2009-06-13
> **Sinkingships7 said:**
> How different is copy-paste code from using a library? It's a dangerous method, no doubt, because if you're not smart, you don't know if the code is really any good. Blind faith is something one should not operate on when taking code from others. Also, I say it's weak. Do It Yourself(tm) :p.

Well, libraries are encapsulated.  They have a well-defined API and (hopefully) documentation.  And if you can't trust them to be relatively bug-free, then you should DIY.  The only real problem with that type of copy-paste code is if you don't understand it.  If you aren't clever enough to come up with it, but are smart enough to understand it, then it is perfectly fine to use.

---

### Post by TheBuzzSaw on 2009-06-13
The definition of "bad" is too broad here. There are lots of reasons code can be "bad". I've seen code that runs incredibly well, but I could not understand the code to save my life (no comments, bad design, etc.). I've seen code that was gorgeous but riddled with bugs. It all depends on the needs of the program. If you work alone and absolutely positively will not work in a group, ugly code is fine.

---

### Post by markux^Hs on 2009-06-13
Bad code = 95% of all PHP.

---

### Post by Mirge on 2009-06-13
> **markux^Hs said:**
> Bad code = 95% of all PHP.

Was waiting for someone to say it. /yawn would be my response.

---

### Post by bigboy_pdb on 2009-06-13
Anything that affects how well you understand code determines how good/bad the code is in all situations. For example, portability or object oriented design count but they can't be applied to all languages or projects.

The two things that stand out to me are structure and language.

By structure I mean how the code looks and is organized. This would include white space, code length (unnecessarily long code is bad), code reuse, and so forth.

By language I'm referring to syntax and comments. Variable names should be easy to read and understand and there should be comments that are concise, descriptive, well written, and up to date.

A person's understanding of a programming language and level of education affect how well he/she will understand someone else's code and comments. Thus, understanding of a programming language and level of education affect whether or not a person thinks code (in the given language) is good/bad.

---

### Post by bigboy_pdb on 2009-06-13
> **TheBuzzSaw said:**
> bad code:
```
if (x > 10)
    return true;
else
    return false;
```

good code:
```
return x > 10;
```

I completely agree with this. When people write code like this, it indicates they don't understand booleans and boolean operators, they don't understand logic, or both.

**EDIT**: This falls under unnecessarily long code.

---

### Post by bigboy_pdb on 2009-06-14
> **dunkar70 said:**
> I would consider bad code to be anything that does not live up to the expectations set by the author. If I write a snippet for my own internal use, who cares how I do it?

When people don't practice good coding skills, their skills aren't as good (or good at all) when it counts.

> **dunkar70 said:**
> If I provide that code to others, I should set expectations for how it should be used and what issues it may have. The idea of open source is that anyone else can improve what we start. Let a neophyte start a new (and possibly brilliant) idea, then let experienced developers with best practices refine the ideas to create a scalable and stable product.

So in other words, instead of taking a little time to improve your skills you'd prefer to waste a lot time for many other people.

Also, writing crappy code is likely to deter other people from wanting to help you with your project or take it over. Anyone that I've ever known who has ever had to modify or maintain poorly written code prefers to write new code rather than modify it.

---

### Post by ActiveFrost on 2009-06-14
> **markux^Hs said:**
> Bad code = 95% of all PHP.

Bad code or bad coder ? :p

---

### Post by The-ITu on 2009-06-14
in my opinion, bad code it code that you cant tell what it dose just by looking at it.
also probably messy code, unhelpful variable and function names, unreadable English and bad habits

---

### Post by slavik on 2009-06-14
> **TheBuzzSaw said:**
> bad code:
```
if (x > 10)
    return true;
else
    return false;
```

good code:
```
return x > 10;
```

The assumption here is that you are simply returning a boolean value. C does not have true/false or understanding of 'boolean.' Not only that, but what about when youu are returning something completely different (something besides a boolean value)? This is a bad example. A better example is when someone appends to a string in a long loop where string is final (python and java come to mind). Another bad example is when people use cascading id-else where a switch-case works better.

---

### Post by markux^Hs on 2009-06-14
> **ActiveFrost said:**
> Bad code or bad coder ? :p

My bad. PHP isn't inherently bad, although it could be better. Most of the people writing it or awful at it, though.

---

### Post by markux^Hs on 2009-06-14
> **Mirge said:**
> Was waiting for someone to say it. /yawn would be my response.

*Get some sleep, *would be my response to you. ;)

---

### Post by nvteighen on 2009-06-14
Bad code, for me, is:

0. **Which isn't modularized:** Be it OOP or pure-procedural, each class/procedure should do just one task and have a proper interface to make it easy to combine with other stuff in code. If there's no modularization nor clear interfaces, the code will be confusing for sure. Spaghetti code destroys this by skipping the established interfaces with jumps... that's why it's bad.

1. **Which doesn't follow a coherent style:** No matter what coding style you use, but you have to use one. Code written in different styles is confusing, misleading and harder to read.

2. **Too much/too few bad comments:** Self explaining :)

3. **Poor data abstraction:** Abstraction layers should be clear and useful. I mean, your class or data structure has to be well thought, capable of representing what you want in the best way you've found. Good abstraction is a symptom for good modelling and will lead to good design more easily... When data structures are well abstracted, the algorithms become self-evident (I think Dennis Ritchie said that... I'm not sure).

4. **BASIC:** No matter how well written, abstracted, designed your BASIC program may be. If it's BASIC, it's bad code :)

---

### Post by scourge on 2009-06-14
> **slavik said:**
> The assumption here is that you are simply returning a boolean value. C does not have true/false or understanding of 'boolean.' Not only that, but what about when youu are returning something completely different (something besides a boolean value)? This is a bad example.

C does have a bool data type: [http://www.opengroup.org/onlinepubs/000095399/basedefs/stdbool.h.html](http://www.opengroup.org/onlinepubs/000095399/basedefs/stdbool.h.html)
But even if it didn't, "x > 10" would still be guaranteed to be either 0 or 1. So if "true" is defined as 1 and "false" as 0, like they are in stdbool.h, what's the problem in TheBuzzSaw's example?

---

### Post by CptPicard on 2009-06-14
Bad code often is produced by not understanding the language or tools you're using, and then forcing some flawed mental model of how things "should" work on your language/tools. A good example here is "pythonic"  code... you can pretty much tell from the python someone writes whether they really "get" the language or not.

A few words about the "multiple return statements" issue... we once ran into this in a class I was taking and the teaching assistant felt like multiple return statements were a bad thing (well, she was actually a business major helping teach a software engineering project class)... well, she got voted down by all the geeks plus two CS professors. 

It really boils down to whatever is more readable, but I personally mostly prefer for a function to terminate as soon as possible -- that is, whenever you know what you want to return, you should. Of course, this excludes possible resource-management issues.. sometimes you need to clean up in the end before returning.

Not making use of multiple returns often forces introduction of needless flag variables and branches that can really clutter up the code.

EDIT: and not to mention how in the case of only returning at the end, you need to often really "compute in your head" what that return value actually *is* and how you get there when you're reading the code, and that this can also often require a needless branching and computation at the end of the function to check what sort of state the computation was left in (see the flag variables etc) so that you can first assign the right stuff to your "return value" and then return that in the single return statement...

---

### Post by scourge on 2009-06-14
> **CptPicard said:**
> It really boils down to whatever is more readable, but I personally mostly prefer for a function to terminate as soon as possible -- that is, whenever you know what you want to return, you should. Of course, this excludes possible resource-management issues.. sometimes you need to clean up in the end before returning.

Not making use of multiple returns often forces introduction of needless flag variables and branches that can really clutter up the code.

+1
Returning as soon as possible often results in less bugs, and keeps the indentation level down as well. Same goes for breaking out of loops, which is also considered bad by some people.

---

### Post by fiddler616 on 2009-06-14
As a general rule:

If you're explaining your code to someone, and you find yourself either apologizing, or thinking "Wait a second, why *did* I write that?" it is bad code.

More specifically:

Regarding return statements, my personal pet peeve is:
```

public static int getBigger(int a, int b)
{
    if(a > b)
    {
        return a;
    }
    else
    {
        return b;
    }
}
```
as opposed to:
```

public static int getBigger(int a, int b)
{
    if(a > b)
    {
        return a;
    }
    return b;
    
}
```

this kind of thing happens a lot in my CS class, and it just shows that people don't grok exactly how return statements work.

Speaking of that class, another pet peeve is:
```
while(foo == true)
```
instead of
```
while(foo)
```
and
```
boolean foo = true;
while(foo == true)//infinite loop
```
instead of
```
while(true)
```
or
```
for(;;)
```

And now I'll be quiet before I start quoting the Zen of Python.

---

### Post by s.fox on 2009-06-14
To me "bad code" consists of the following elements:

1)  No comments in the code
2)  Obscure logic that is difficult to follow
3)  Meaningless variable names

Please note that to me working code can also be seen as bad in my criteria.    For example imagine having to update the code without the authors help.

-Ash R

---

### Post by ActiveFrost on 2009-06-14
> **markux^Hs said:**
> My bad. PHP isn't inherently bad, although it could be better. Most of the people writing it or awful at it, though.

Exactly ! It has a lot of features which most of us even don't know ( like working with UNIX signals, template systems, etc. ) - most of the ugly/bad code comes from peoples who want to learn it to make some fast money ( they don't care if their code will be readable by someone else and .. most probably by himself in a few weeks :D ).
I've done a lot of programming in PHP, and .. it's boring ! Maybe that's why we tend to say it's a bad programming language ( fun stuff comes in only by using AJAX, etc. ) :)

---

### Post by lykwydchykyn on 2009-06-14
> **markux^Hs said:**
> My bad. PHP isn't inherently bad, although it could be better. Most of the people writing it or awful at it, though.

Not that I'm a terribly good programmer to begin with, but it seems like even my best piece of PHP feels like a gigantic hack.  I don't think I've ever written anything in PHP that I felt proud to show other programmers.  

I think part of it is that a lot of people learn PHP by injecting bits of dynamic code into an otherwise static HTML document.  You end up with a totally different paradigm of web coding than, say, someone who does CGI scripts.

---

### Post by TheBuzzSaw on 2009-06-14
> **slavik said:**
> The assumption here is that you are simply returning a boolean value. C does not have true/false or understanding of 'boolean.' Not only that, but what about when youu are returning something completely different (something besides a boolean value)? This is a bad example. A better example is when someone appends to a string in a long loop where string is final (python and java come to mind). Another bad example is when people use cascading id-else where a switch-case works better.
This is silly. If you don't want to return a boolean result, my example doesn't even apply. If you want to return something different, why are you even criticizing my example???

My example is from actual code I have seen. My point is that people overcomplicate boolean functions.

---

### Post by jespdj on 2009-06-14
If you want examples of bad code and other stuff, read... [http://thedailywtf.com/](http://thedailywtf.com/)

---

### Post by Mirge on 2009-06-14
> **lykwydchykyn said:**
> Not that I'm a terribly good programmer to begin with, but it seems like even my best piece of PHP feels like a gigantic hack.  I don't think I've ever written anything in PHP that I felt proud to show other programmers.  

I think part of it is that a lot of people learn PHP by injecting bits of dynamic code into an otherwise static HTML document.  You end up with a totally different paradigm of web coding than, say, someone who does CGI scripts.

Change your style of programming if you aren't comfortable with it.

---

### Post by ibuclaw on 2009-06-14
If this has already been brought up, I apologise.

But this site pretty much has it all when it comes to writing "Bad/Unmaintainable Code": [http://mindprod.com/jgloss/unmain.html](http://mindprod.com/jgloss/unmain.html)

Regards
Iain

---

### Post by phrostbyte on 2009-06-14
> **asbuntu said:**
> Code that allocates memory, and then does not verify that the allocation succeeded.

I can't agree with this one. If you can somehow recover from a bad allocation, then sure, test for it. But most of the time it isn't true IMO. Because lets say you malloc() and it fails, so you get a null pointer. What happens if you deref it? Well the OS will detect this and the program will crash. 

Now if you malloc() and then test for a null pointer, if you can't easily recover from this, often it's GG for your program then anyway. So what are you suppose to do? Keep trying allocation? exit(-1)? I think it's more "user-friendly" to let the OS detect this and close the program with a SIGSIEV in the case malloc() returns null  then the program just mysteriously close some other way.

---

### Post by asbuntu on 2009-06-14
> **phrostbyte said:**
> I can't agree with this one. If you can somehow recover from a bad allocation, then sure, test for it. But most of the time it isn't true IMO. Because lets say you malloc() and it fails, so you get a null pointer. What happens if you deref it? Well the OS will detect this and the program will crash. 


Thank you for your opinion.  That's what makes these forums work.  In my case (the statement of the "rules"), I don't completely agree.  I can argue both ways...

_For the crash..._

If memory is truly in trouble, then you are probably not going to be able to allocate memory to write an error messsage, let alone do a stack trace.  I seem to recall reading in C/C++ Users Journal, paraphrasing, I think, Jeff Plauger, that "a program with memory problems should 'just crash' and let the analyst figure it out."

_Against the crash..._

Part of the problem with memory is that people don't understand virtual fragmentation.  They think - "gee, I've got 4gb, I can't run out of memory", and my virtual aware OS will handle everything.  (Sorry, Charlie - nice try but no cigar!)

Well, for short, quick and dirty, programs (which I've written), I agree.  I allocate, do something, and then just exit, knowing that the OS will delete the process address space anyway.

But for long running programs, such as a web server or a process monitor, its not quite so easy to say "I don't care"...

Here's an example...

Write a program that allocates 100mb chunks of memory, putting each address in an array, until you run out of memory.  On a 4gb address scheme, that works out to slightly less than 40 chunks.  Now, go through and deallocate every other chunk.  At this point, you have 2gb of used memory, 2gb of available memory, and no memory chunk larger than 100mb.  Try to allocate 200mb and see what happens.  (Oops!  Hmmm!)

In a managed memory system like Java or .NET/CLR, things are different.  Unless you play with smart pointers, C/C++ is a problem child when it comes to memory.  You have got to get it right.

Thank you.

---

### Post by phrostbyte on 2009-06-14
> **asbuntu said:**
> Thank you for your opinion.  That's what makes these forums work.  In my case (the statement of the "rules"), I don't completely agree.  I can argue both ways...

_For the crash..._

If memory is truly in trouble, then you are probably not going to be able to allocate memory to write an error messsage, let alone do a stack trace.  I seem to recall reading in C/C++ Users Journal, paraphrasing, I think, Jeff Plauger, that "a program with memory problems should 'just crash' and let the analyst figure it out."

_Against the crash..._

Part of the problem with memory is that people don't understand virtual fragmentation.  They think - "gee, I've got 4gb, I can't run out of memory", and my virtual aware OS will handle everything.  (Sorry, Charlie - nice try but no cigar!)

Well, for short, quick and dirty, programs (which I've written), I agree.  I allocate, do something, and then just exit, knowing that the OS will delete the process address space anyway.

But for long running programs, such as a web server or a process monitor, its not quite so easy to say "I don't care"...

Here's an example...

Write a program that allocates 100mb chunks of memory, putting each address in an array, until you run out of memory.  On a 4gb address scheme, that works out to slightly less than 40 chunks.  Now, go through and deallocate every other chunk.  At this point, you have 2gb of used memory, 2gb of available memory, and no memory chunk larger than 100mb.  Try to allocate 200mb and see what happens.  (Oops!  Hmmm!)

In a managed memory system like Java or .NET/CLR, things are different.  Unless you play with smart pointers, C/C++ is a problem child when it comes to memory.  You have got to get it right.

Thank you.

C/C++ gives you a lot of power and with power comes responsibility. :)

You are right, if you are writing a web server, maybe you should be more aggressive in trying to allocate memory successfully. The problem is sometimes you can't, sometimes you need 100 KB of contiguous memory and if the OS is saying "sorry you can't have that", then you can't really do anything anyway but halt. It's game over for your program if you do a null pointer check or not.

I mean perhaps sometimes you can allocate less, but you might have to have a separate logic path in that case and it can get messy. Some really complex C/C++ programs might even implement their own memory manager, or just use someone else's implementation (eg: smart pointers) so they might avoid fragmentation better, but this is often unfeasible for you and me. 

Anyway null checking it's not something you should do all the time, only in instances it makes sense. That why I don't think not checking for null pointers on a memory allocation is not really "bad code". I think even too many null checks might lead to bad code, because if I see code like "if (ptr == NULL) exit(-1);" after every malloc or new it gets distracting, it's also more assembly code for the CPU to execute. Most of the time a malloc() will complete successfully, unless something really freaky is going on the computer. I think segfaults are more commonly from programming errors, like hitting memory out of bounds, or forgetting to initialize a pointer.. then malloc() or "new" failing anyways.

---

### Post by slavik on 2009-06-14
> **TheBuzzSaw said:**
> This is silly. If you don't want to return a boolean result, my example doesn't even apply. If you want to return something different, why are you even criticizing my example???

My example is from actual code I have seen. My point is that people overcomplicate boolean functions.
point taken.

---

### Post by slavik on 2009-06-14
> **jespdj said:**
> If you want examples of bad code and other stuff, read... [http://thedailywtf.com/](http://thedailywtf.com/)
read this and use it as your "don't do this" guide ;)

---

### Post by phrostbyte on 2009-06-14
> **slavik said:**
> read this and use it as your "don't do this" guide ;)

It's a good site to read if you want to feel smarter. :)

---

### Post by jflaker on 2009-06-15
> **TheBuzzSaw said:**
> This is actual code from a friend's program:
```
if (keepPlaying == "no" || keepPlaying == "No" || keepPlaying == "NO")
```
*facepalm*

You can simply do:
if (ToUpper(KeepPlaying) == "NO")

DONE!  pseudocode, most languages have an uppify function for strings as far as I know...or create one.

---

### Post by xebian on 2009-06-15
> **jflaker said:**
> You can simply do:
if (ToUpper(KeepPlaying) == "NO")

DONE!  pseudocode, most languages have an uppify function for strings as far as I know...or create one.

Actually the original code is better.  Consider this.  Most of the times it's 'no' so with the original code, the call to ToUpper is not necessary because the first test is true right away.

Most compilers are so optimized/efficient the resulting machine code is pretty much the same.

---

### Post by fiddler616 on 2009-06-15
> **xebian said:**
> Actually the original code is better.  Consider this.  Most of the times it's 'no' so with the original code, the call to ToUpper is not necessary because the first test is true right away.

Most compilers are so optimized/efficient the resulting machine code is pretty much the same.
I'm not sure I'm with you on that...
[QUOTE=TheZenOfPython]
Beautiful is better than ugly, [using one function instead of a very long if statement is beautiful]
...Simple is better than complex, [it's also simpler]
...Readability counts[/QUOTE]

I forget who it was that said that "source code is for humans to read, and only incidentally for machines to run." (Knuth? Richie?), but I fully agree with him.

---

### Post by slavik on 2009-06-16
> **xebian said:**
> Actually the original code is better.  Consider this.  Most of the times it's 'no' so with the original code, the call to ToUpper is not necessary because the first test is true right away.

Most compilers are so optimized/efficient the resulting machine code is pretty much the same.
your assumption is on short circuiting.

consider that in ASCII, 'A' is 65, while 'a' is 97. ;)

---

### Post by lisati on 2009-06-16
> **lykwydchykyn said:**
> I understand you're going for elegance here, but on a slightly different note is having multiple return statements in a function necessarily bad code?  I've gone back and forth on this.

CS teachers have always said it was, and marked me down for it if I accidentally did it.  But I see it all the time in real code, articles, documentation, and even textbooks.  I mean, there is always a way to code with only one return statement, but sometimes it seems clearer the "wrong way".

Opinions?
I know I'm a couple of days late with this (only just spotted the thread) but I was taught the "one way in, one way out" approach of structured programming, back in the days before OOP caught on. Depending on my mood at the time and what the program requires, I might do something like this:
```
result=false;
if (some_test)
    result=true;
return result;
```

---

### Post by nvteighen on 2009-06-16
> **xebian said:**
> Actually the original code is better.  Consider this.  Most of the times it's 'no' so with the original code, the call to ToUpper is not necessary because the first test is true right away.

Most compilers are so optimized/efficient the resulting machine code is pretty much the same.
Ok, yes, in terms of efficiency you may be right.

But in terms of expression, the best solution is to use a ToUpper/ToLower function. No matter which.

---

### Post by lisati on 2009-06-16
> **nvteighen said:**
> Ok, yes, in terms of efficiency you may be right.

But in terms of expression, the best solution is to use a ToUpper/ToLower function. No matter which.

I agree that the first solution might be better in terms of efficiency. Having said that, we can't afford to overlook making the program robust and as crash-proof as time and patience permits.

---

### Post by supirman on 2009-06-16
> **Mordred said:**
> I am mostly programming in C.

Bad code for me is code:

1. That uses global variables everywhere.
Some people consider function arguments to be optional :(
This makes code unreadable and very hard to debug.

2. Lack of comments. I am working as a programmer in a large
company and have seen already quite some source files with literally 
no comments except for some commented out code.

3. Which brings me to the next one, some programmers just do not trust
their version system so they leave redundant code commented out or
under #ifdef BLAHBLAHBLAH #endif.

4. Hard coded values are of course also a great annoyance updating a 
source file with hard coded values is always very 'exciting' ;)

5. Code that has no clear interfaces between the different sub-blocks.
All to often I see all functions of a source file to be exported in
the header file. A header file needs to contain the bare minimum for
other sub-blocks to use this module.

Anyway, just my 2 cents, feel free to disagree :D

Where I work, 3 of the 5 software engineers have no formal software training and they all write horrific code doing just the things you've mentioned.  I swear, it seems as though they found a couple of the "how to write unmaintainable code" guides and followed them (probably unknowingly) as coding standards.  The absolute lack of structure, design, logic, etc pisses me off to no end.  

From what I can see, none of them should be paid for writing software as they're utterly clueless.  They never use function parameters and literally everything is at the global scope.  It's the most horrific code I've ever seen.

---

### Post by Reiger on 2009-06-16
> **fiddler616 said:**
> Regarding return statements, my personal pet peeve is:
```

public static int getBigger(int a, int b)
{
    if(a > b)
    {
        return a;
    }
    else
    {
        return b;
    }
}
```
as opposed to:
```

public static int getBigger(int a, int b)
{
    if(a > b)
    {
        return a;
    }
    return b;
    
}
```

this kind of thing happens a lot in my CS class, and it just shows that people don't grok exactly how return statements work.

I find this really depends on the situation. In this case, I'd say what you are doing is essentially as bad as "if(x > 10) return true; else return false;" mentioned earlier. In this particular case there is a language construct to encapsulate decisions like this and its call the ternary operator: you'd write "return (a > b) ? a : b;".

But in other cases you may find that error handling code is required inside the function (say logging an error). There may be many error cases, and when there are I find it more elegant to have each cases encapsulated inside its own block. Which means:
```

if(test) { /* code */
}
elseif() { /* other code */
}
else { /* yet more code */
}

```

Or (in rare circumstances):
```

switch(test)
  case someCase : 
    /* code */
  break;
  case someOther: 
    /* other code */
  break;
  default :
    /* default code */
  break;

```

---

### Post by jflaker on 2009-06-16
> **slavik said:**
> your assumption is on short circuiting.

consider that in ASCII, 'A' is 65, while 'a' is 97. ;)

OK, that works if you stay on a PC, I can also run PHP/MySQL on the AS/400 and now your statement is longer valid...call to an uppify function will work on both systems as the function takes care of the assumptions.  ASCII and EBCDIC have hugely differing character hex values.  97 is 'a' in ASCII but is a '/' in EBCDIC

You should be able to move your code from system to system and have confidence a piece of code will work from platform to platform....

```

<?php
$str = "Mary Had A Little Lamb and She LOVED It So";
$str = strtoupper($str);
echo $str; // Prints MARY HAD A LITTLE LAMB AND SHE LOVED IT SO
?>

```

---

### Post by dunkar70 on 2009-06-17
You are thinking very short-sighted. When people write code and work in communities, they WILL pick up best practices and improve their coding style and skills over time. My suggestion is not that people remain in an infant state, but they will mature over time. I am sure you wrote some horrible code when you first started... should we now believe that you are and will ever be a crappy coder? Have you have provide an idea that helped a project or other people, even when you were still a new programmer?

The biggest problem with "expert" coders is they can become arrogant. New people bring new perspectives and new ways of thinking... you should not discourage these people from participating in a community because you are too arrogant (or honestly busy) to help. There will be others who are willing and able to help.

---

### Post by Mirge on 2009-06-17
> **dunkar70 said:**
> You are thinking very short-sighted. When people write code and work in communities, they WILL pick up best practices and improve their coding style and skills over time. My suggestion is not that people remain in an infant state, but they will mature over time. I am sure you wrote some horrible code when you first started... should we now believe that you are and will ever be a crappy coder? Have you have provide an idea that helped a project or other people, even when you were still a new programmer?

The biggest problem with "expert" coders is they can become arrogant. New people bring new perspectives and new ways of thinking... you should not discourage these people from participating in a community because you are too arrogant (or honestly busy) to help. There will be others who are willing and able to help.

Who are you talking to? Or just responding to the thread in general?

---

### Post by xebian on 2009-06-17
> **fiddler616 said:**
> I'm not sure I'm with you on that...


I forget who it was that said that "source code is for humans to read, and only incidentally for machines to run." (Knuth? Richie?), but I fully agree with him.

You tell me which is more 'human readable'

```
if (keepPlaying == "no" || keepPlaying == "No" || keepPlaying == "NO")

```

 Or this

```
if (ToUpper(KeepPlaying) == "NO")

```

---

### Post by xebian on 2009-06-17
> **slavik said:**
> your assumption is on short circuiting.

consider that in ASCII, 'A' is 65, while 'a' is 97. ;)

short circuiting in expression processing has nothing to do with ASCII ordering.

---

### Post by fiddler616 on 2009-06-17
> **xebian said:**
> You tell me which is more 'human readable'

```
if (keepPlaying == "no" || keepPlaying == "No" || keepPlaying == "NO")

```

 Or this

```
if (ToUpper(KeepPlaying) == "NO")

```
The second one, IMHO.
Somebody reading the second one will see that this is only true for one condition: if KeepPlaying is false. Astute people will see the ToUpper() function and realize it's to protect the user, but that ultimately it has little bearing on the logic of the program.
The first one, though still functional and decipherable, brings the issue of case--which is really rather minor--to a head, and makes a big deal out of it.
One last good point of the second: it's shorter, yet doesn't sacrifice clarity. A final quote from the Zen of Python:
> Sparse is better than dense.

----
Really guys, can we agree to disagree, and move on? This was a good thread until we started flaming about boolean logic.

---

### Post by simeon87 on 2009-06-17
In Python, the first alternative wouldn't be so long by the way (and quite readable):

```

if keepPlaying in ["no", "No", "NO"]:

```

---

### Post by Mirge on 2009-06-17
> **simeon87 said:**
> In Python, the first alternative wouldn't be so long by the way (and quite readable):

```

if keepPlaying in ["no", "No", "NO"]:

```

As someone else pointed out, what about nO? :)

---

### Post by simeon87 on 2009-06-17
> **Mirge said:**
> As someone else pointed out, what about nO? :)

Ok, one more string in the list then - that would cover all four possible combinations :P Using an uppercase function would be fine, I'm only pointing out that it's not that long in Python.

---

### Post by Mirge on 2009-06-17
> **simeon87 said:**
> Ok, one more string in the list then - that would cover all four possible combinations :P Using an uppercase function would be fine, I'm only pointing out that it's not that long in Python.

Heh I know, I was just messin around. Though, the original topic of the thread was "bad code", not "bad code in python" :).

---

### Post by jflaker on 2009-06-17
> **xebian said:**
> short circuiting in expression processing has nothing to do with ASCII ordering.

But is doesn't work on a non-PC system.  You assume that it will run on a pc server, but if someone implements this code on a iSeries which is EBCDIC based, not ascii...all ascii assumptions stop working and the application falls over.

---

### Post by jpkotta on 2009-06-17
> **simeon87 said:**
> Ok, one more string in the list then - that would cover all four possible combinations :P Using an uppercase function would be fine, I'm only pointing out that it's not that long in Python.

It would be if you were checking for "yes".  2^{len(string)} does not scale well at all.  Also, almost nothing is very long in Python, if you do it pythonically.  

This is actually one of my pet peeves of code.  I wouldn't go so far as to call it bad, but it is annoyingly verbose and inelegant.

---

