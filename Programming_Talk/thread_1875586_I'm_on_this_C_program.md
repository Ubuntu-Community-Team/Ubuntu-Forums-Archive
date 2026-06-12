---
title: "I'm on this C program"
date: 2011-11-05
forum: Programming Talk
---

### Post by ClientAlive on 2011-11-05
Hi,

The assignment is already passed and I submitted what I had (a non-functioning program). I still want to understand what the problem is though and don't have any way to contact anyone over the weekend. I was hoping someone here might take a peek and offer me some guidance so that maybe I can move forward. Below I've pasted the content of something I wrote earlier that describes the situation a little and I've attached my source code. If anyone could help I would really appreciate it. I've been really struggling over the last 3 weeks now. I don't believe this (programming) is out of my reach, I'm just running into these walls and don't know where to turn for help.

Thanks in advance for taking the time to read this. Thanks for any help.

> 
I'm stuck with this program and I can not, for the life of me, understand what the problem could be. I read the part in our book on the "for repetition" on pp. 103, 104. I went back over all our notes (repeatedly), watched the videos (multiple times), and examined every letter, space, parenthesis, quote mark, you name it in this small, simple source document. Everything I see in there lines up precisely to all that I have read, seen, come to understand, whatever. It compiles fine. There is no-thing out of place that I can find. The conditions of the for loop follow the exact format and specifications described in our book.

My second for loop (the first one inside the outer loop) did not seem to be getting executed at all. That was supposed to be the one for the spaces (as indicated by the comment next to it). To troubleshoot the program I made the first printf statement (on line 44 in my editor) "printf("x");" and the second one (on line 49 in my editor) "printf("y");"  I figured that by doing so I could compile and run it that way and 'actually see' what was printed to the screen or not. Compiled and ran it just like that (just as it is in the file I've attached . . . ). Only "y" s print to the screen. To make absolutely certain (and to check whether there is something to do with C language where you can't have more than one for loop  next to each other) I completely removed the for loop containing the y, compiled and ran it like that. Now nothing printed to the screen except the vertical space of what appeared to be 7 lines worth. I thought maybe there was something to the order (which of the two inner loops comes first - I was thinking about how something can "fall through" in switch statements). I reversed the order so that the one containing the y came first then the one with the x. Compiled and ran it. Still, only "y" s printed to the screen (and those Y's are all the maximum number on each and every one of the seven lines anyway).

I'm completely out of ideas. I've looked for information in all the places I know to look and feel like I have nowhere to turn. This is what happens with me lately. I end up spending a tremendous amount of time on something that really shouldn't take that long and still don't meet the deadline. I can't get the time back, so I fail in my other classes as well. I want, desperately, to get this right but I can not see where anything is out of place regarding spelling or format. I want with every fibre of my being to be involved with program development (to program). I like it. I mean I really like it. Between the book, the videos, and the notes I thought I understood how the for loop works very, very well. What am I missing here?

Another thing I might note. in the third for loop (counting down from the top, line 47 in my editor). I had, had the third condition, the counter, set to "k += 2"  --so that it read "for (k = 1;  k <= 13 ; k += 2)"  just before attaching the file I sent . . . The value of that number was the only difference between my previous trial (compiling and running it) and the last trial, just before sending the first . . . on this, that came from the exact file I attached  . . . The difference in results between the two was the number of Y's that were printed on one line. With "k += 2" it seems to print 7 Y's on every line whereas with "k += 1" it prints 13 on every line.

I should also probably mention that I had only been concentrating on producing the triangled, top part of the tree at this time. I had intended to go in and add the trunk (like I think was mentioned in our assignment description) once I got that working.


---

### Post by lisati on 2011-11-05
Here's the line where I think the problem could be:
```
for (j = 6; j <= 0; j += 1)
```
A more seasoned C programmer might be able to correct me if I'm mistaken: the loop will only be executed if j<=0, but j=6, which is >0.

---

### Post by docbop on 2011-11-05
That's a real simple assigment and you need to work thru it.  First you did state what your problem is.  People aren't/shouldn't write your homework for you.  Working thru this is how you learn to program.

I would say first work it out on paper, grab a sheet a paper and work thru your loop counts for stars and spaces.   Then work on the code to print out just the first line of output.  Get that working now get two lines.  After that the rest should be simple.

Remember good programming is 80% design/planning and 20% coding.   

When you have specific problems post again.

---

### Post by ClientAlive on 2011-11-05
Right on. That error is something I just didn't notice. I spent about 8 hrs straight on this today and came to a point about an hour ago where I was completely out of ideas. I kept looking at it and looking at it and everything looked fine to me. I couldn't see why it wouldn't just work.

Well thanks for pointing that out to me. And for the encouragement. I'm gonna tackle it again and see what I can do.

In case you were concerned though, the assignment deadline passed at 5 pm this evening (about 7 hrs ago). Whatever I continue to do with it now has nothing to do with my grade in the class, it's just because I want to understand it.

Thanks a whole bunch guys.

:)

---

### Post by squenson on 2011-11-05
A good developer's trick to really understand what your program does is to add some print statements at various places in the code with the various information you want to analyze.

For example, you could add a statement (I will not give you the exact coding syntax) right after you enter the first loop:
print "Just entered into the first loop. The value of i is:" i

Do the same when you enter the second and third loops.

Then analyze the output. You will better understand which statements your program is executing, the values of the variables, etc.

---

### Post by ClientAlive on 2011-11-05
> **squenson said:**
> A good developer's trick to really understand what your program does is to add some print statements at various places in the code with the various information you want to analyze.

For example, you could add a statement (I will not give you the exact coding syntax) right after you enter the first loop:
print "Just entered into the first loop. The value of i is:" i

Do the same when you enter the second and third loops.

Then analyze the output. You will better understand which statements your program is executing, the values of the variables, etc.


Oh my goodness, how come I never thought of that! I went back and fixed my operator problem with for loop that has that j variable in it. So that for loop executes now. But I must have some real misconception of exactly how a for loop does what it does (step by excruciatingly detailed step). Based on what is actually printed to the screen I can see that there's some kind of odd math going on because of these elements connection w/ one another but can't quite put my finger on it. I'm gonna try what you said and see if I can get some clues. I think I can get it to actually print out the value of the variable at that iteration too. Thanks man.

--------------

Edit:

Dude!! Brother! That is probably the best guidance anyone has ever given me! I can't believe the information I just got from doing that. I think you just gave me a way to learn. OMG!!

---

### Post by ClientAlive on 2011-11-05
I got it fellas. Programming is just weird. The math with a for loop ends up not working in the way you think it would and it's because of the way the for loop executes. Unless you take that into consideration, heck, even if you do take it into consideration . . .   grrrr. It's just nuts.

That trick with adding printf statements around and having it print the value of the variables was amazing. That's what really got me over the hump on this thing. I'm pretty sure I'll be using that trick all the time from now on - at least till I really get the concepts down. You probably saved my college carrer squenson. I'm falling behind in this class and others because of the time it takes out of me. Maybe I actually stand a chance now.

Peace out for now guys. Catch ya' on the flip side.

:D

---

### Post by muteXe on 2011-11-05
What do you mean, the math of a for loop doesn't work in the way you think it would?? Seems fairly logical to me dude.

---

### Post by squenson on 2011-11-05
> **ClientAlive said:**
> You probably saved my college carrer squenson.

:cool: Certainly a little bit exaggerated but nice to read anyway :cool:

---

### Post by docbop on 2011-11-05
> **squenson said:**
> A good developer's trick to really understand what your program does is to add some print statements at various places in the code with the various information you want to analyze.

For example, you could add a statement (I will not give you the exact coding syntax) right after you enter the first loop:
print "Just entered into the first loop. The value of i is:" i

Do the same when you enter the second and third loops.

Then analyze the output. You will better understand which statements your program is executing, the values of the variables, etc.

Being C is a compiled language better to learn to use a debugger so you can step thru the program and watch what happens.   

That the advantage of learning to program in compiled programs so you see how the computer executes your code and how memory and stack work.    When using interpreted languages the using print statements like your talking about is sometimes your only form of debugging.

---

### Post by gsmanners on 2011-11-05
Actually, in many cases, you'll find that logging is your only form of debugging. It's similar in principle to using printf (except that your output goes to a file rather than an open console).

---

### Post by CptPicard on 2011-11-05
> **docbop said:**
> 
That the advantage of learning to program in compiled programs so you see how the computer executes your code and how memory and stack work.    When using interpreted languages the using print statements like your talking about is sometimes your only form of debugging.

Err... when working with a language that is not native-compiled, at best you get full, complete control of the entire execution environment that you can poke around in at will. A live Lisp image is probably the best example of this. A compilation step actually throws away a lot of the semantic information of the code, moving it into a much less readable form, and demanding the addition of debugging symbols into the binary... I really don't see at all how it's supposed to make the code *more* amenable to debugging.

---

### Post by ClientAlive on 2011-11-06
> **muteXe said:**
> What do you mean, the math of a for loop doesn't work in the way you think it would?? Seems fairly logical to me dude.


It is logical as long as you include an understanding of how the for loop executes. When you do though, the math then differs from just straight math. Here's a couple pieces out of my program (what I had to do to make it work). Let's then compare them with what "straight math" would say about the matter.

```

i = 1; i <= 7;

and

k = 1; k <= 2 * i - 1;

```

Using just straight math (where you would not take some outside element into consideration -like how a for loop executes) --one would not think that you would get a first loop through in the variable k.

> 
k <= 2 * i -1, when i begins at a value of 1 would evaluate to k = 2 * 1 - 1 = 0. Now 0 < 1 and the first condition of that for loop says ("k = 1") not k = 0.


So, with the above, we have a problem in the math here. By comparison, with straight math, you would be trying to convince someone that:

> 
k = 1 and k = 0 (this is false)

another way to put this that is perhaps more clear is:

if i = 1 then k = 2 * 1 - 1 = 2 * 0 = 0


But we said that k = 1 already, the program (in C language), as I understand it, reads from top to bottom and left to right. The first constraint in "for (k = 1; k <= 2 * i - 1 . . . " should then be read before the second.

So I'm guessing the difference in math is the difference in whether you understand and take into consideration --how a for loop works in the first place. If you do take how a for loop executes into consideration, that's when you see how it could happen and why. Now I'm not certain that what I'm about to claim is accurate but it is the only way I can understand how that loop (the one in variable k) would execute a first time at all. Here are two different possibilities of how a for loop might work (in more detail than I've seen in our book or notes or anywhere else yet) that I can think of and that would allow this mess to work.


> 
Claim Option 1:

The first time it enters the loop it looks at that first constraint ("k = 1") and just executes a loop without even comparing it to the second constraint. It doesn't do a comparison with that second constraint until beginning the second loop.



> 
Claim Option 2:

It does compare the first and second constraint on the first time entering the loop but because it's generally possible to set the first constraint to 0 and still have the loop execute, it doesn't really matter if the second constraint equals 0 on that first time around. By equaling 0 on the first time around 0 <= 2 (in the "k <=  . . . ") constraint  and it somehow overrides the first constraint even thought the two numbers don't equal one another --so it still evaluates it to true anyway -even though it's kind of like fudging to do so.



Now I see that not understanding (in excruciating, mind numbing detail) how a function executes (or any function in any programming language for that matter) is the crux of ALL failure in learning programming. What that means to me is that it's probably really really important that I come to some final understanding whether it is "Claim Option 1", "Claim Option 2", or some other thing entirely that is going on with a for loop (and do the same with ever function I ever learn in programming). In the absence of that I don't see how I could possibly succeed.

Please forgive me if my terminology is a bit off. I'm doing the best I can with what I have to work with. Please let me know if it is, I can try to do better.

Anyone care to entertain this?

---

### Post by Barrucadu on 2011-11-06
"k = 2 * 1 - 1" is 1, not 0.

---

### Post by squenson on 2011-11-06
> **Barrucadu said:**
> "k = 2 * 1 - 1" is 1, not 0.... and this is why your inner loop is executed once when i is equal to 1!

---

### Post by gateway67 on 2011-11-06
> **ClientAlive said:**
> 
Anyone care to entertain this?
[http://www.mathgoodies.com/lessons/vol7/order_operations.html](http://www.mathgoodies.com/lessons/vol7/order_operations.html)

---

### Post by docbop on 2011-11-06
> **CptPicard said:**
> Err... when working with a language that is not native-compiled, at best you get full, complete control of the entire execution environment that you can poke around in at will. A live Lisp image is probably the best example of this. A compilation step actually throws away a lot of the semantic information of the code, moving it into a much less readable form, and demanding the addition of debugging symbols into the binary... I really don't see at all how it's supposed to make the code *more* amenable to debugging.

Most C compiler support symbolic debuggers that give you the option of stepping thru your source or drilling down to the assembler generated.

I only working in LISP once ages ago, but I didn't think it compiled down to a binary like C that it compiled to an intermediary that linked to runtime lib at execution.  That is how it can do runtime compiling that other languages can't.

---

### Post by CptPicard on 2011-11-06
> **docbop said:**
> Most C compiler support symbolic debuggers that give you the option of stepping thru your source or drilling down to the assembler generated.

Yes of course, but it's still in a fundamental sense a more complex situation to having complete control of the running environment as you can achieve in interpreters. That is, I do not as a matter of principle understand the claim that native binaries are easier to debug. It seems to be the contrary no matter if you can do symbolic debugging. Of course the interpreter needs to have appropriate hooks in place, and most of the time they do.

I do understand I'm picking nits, but still. ;)

> 
I only working in LISP once ages ago, but I didn't think it compiled down to a binary like C that it compiled to an intermediary that linked to runtime lib at execution.  That is how it can do runtime compiling that other languages can't.

IMO, compiling down to a binary is not any kind of a "requirement" here.

But anyway, although it's irrelevant, this completely depends on implementation. SBCL does compile to native, and the native compiler even does more involved compilation depending on how much you annotate your source, giving the compiler more knowledge of the involved types and so on. At the extreme, you can write almost C-ish Lisp that compiles to readable assembly.

I can never imagine debugging a Lisp program through the compilation result though; it's much more sane to do it far more abstractly, investigating the stuff in your program at the REPL and using the (much higher-level) SBCL debugging facilities.

---

### Post by Bachstelze on 2011-11-06
@ClientAlive: Before understanding for loops, try to understand while loops. Then you can "mentally" convert your for loops to while loops and it will all make sense.

---

### Post by ClientAlive on 2011-11-06
> **Barrucadu said:**
> "k = 2 * 1 - 1" is 1, not 0.


OMG! I'm so embarrased. I've studied up into calculus math and you'd think I'd know what the stinking order of operations is. Oh wow. I'm a complete dumbass. Thanks for pointing that out though. lol.

:P

---

### Post by ClientAlive on 2011-11-06
> **Bachstelze said:**
> @ClientAlive: Before understanding for loops, try to understand while loops. Then you can "mentally" convert your for loops to while loops and it will all make sense.

Right on. I'm gonna look for some decent info. Flow charts and such on the different loops. I'll try to picture what your saying and see what it gets me.

;)

---

