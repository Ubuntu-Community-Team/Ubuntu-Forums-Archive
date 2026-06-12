---
title: "Reading another's code. Where to start?"
date: 2007-10-26
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-26
I am trying to read some open source program's source code. There can be so many .cpp and .h files. Where should one start when reading someone else's code?

---

### Post by nanotube on 2007-10-26
> **TreeFinger said:**
> I am trying to read some open source program's source code. There can be so many .cpp and .h files. Where should one start when reading someone else's code?

try starting at "main()" :)

seriously, i find that starting from the main and branching out works for me.

---

### Post by TreeFinger on 2007-10-26
How do I find out what .cpp file has the main function?

---

### Post by Compyx on 2007-10-26
Use grep:
```

grep 'main(' *.cpp

```

---

### Post by jpkotta on 2007-10-26
If you have a really big project, use rgrep (recursive grep).

```
rgrep --include=*.[ch]pp --include=*.[ch] <regex> <directory>
```

---

### Post by fyplinux on 2007-10-26
maybe read the documnets first, if they have

---

### Post by g8m on 2007-10-26
In most cases it's quicker to delete the sources and build from scratch.

---

### Post by nanotube on 2007-10-26
> **fyplinux said:**
> maybe read the documnets first, if they have

excellent point! :)

---

### Post by nanotube on 2007-10-26
> **g8m said:**
> In most cases it's quicker to delete the sources and build from scratch.

how can you build anything, if you have deleted the sources? i don't understand what you are saying. like saying "just throw out all the food, and make dinner" :)

---

### Post by g8m on 2007-10-26
> **nanotube said:**
> how can you build anything, if you have deleted the sources? i don't understand what you are saying. like saying "just throw out all the food, and make dinner" :)

Let's take this example. You just love this pizza, but hate the goat cheese they're using. Can you use the pizza, scrape off the goat cheese and add gouda? Or would it be wiser to bake the pizza from scratch using the known ingredients and replace the goat with the cow during the bake process. 

If you don't know the ingredients, scraping of goat would be the only solution, but you problably end up with the goat taste anyway, it't hard to get rid off. If you know the process, i'd prefer a freshly baked pizza with the new recipy.

My point beinig, It;s damn hard reading sources, and " Luke, read the source", never amused me. Thinking source is hard, not only do you have to understand the flow, you have to think three dimensional, adding values to the variables.

But I guess, thinking money, makes this very difficult. It took a year to program, and changing it takes a year to reprogram. The original programmer would probably need just one hour, but you fired him because that seemed cheeper at the time.

---

### Post by hecato on 2007-10-26
There are good programs can be read easily (I havent seen much, but I think bash has nice modularity and organization of files)


[LIST]
[*]Read if there is a reference of the organization of the source files.
[*]See if you can compile with debug flags -DEBUG -DEBUG -DEBUG (some times IIRC that activate a third level of debug messages and so on).
[*]Try to trace it manually, or using a tool I lately have seen valgrind and related (not much thought).
[*]Try to modify a little piece for see if you are really there :), get the idea... you know there are some way tricks there, like a dispatch table of functions (not a if/else blocks or cases), etc, etc.
[*]Have fun reading other people code... if you can with 1 literature, let it, go seek another, then if you can and have learned enough welcome back.
[*]mmmmm, try to think how you will do that, or get the idea why they do that.
[*]try to limit the scope of read (if possible), follow something for example the flow path for the x option.
[*]Make annotations on the contents of the files, and things you find interesting.[/LIST]Dont know, have fun, there are lot of things.

---

### Post by Sporkman on 2007-10-26
> **Compyx said:**
> Use grep:
```

grep 'main(' *.cpp

```

I tend to put a space between "main" & "(" myself. :)

---

### Post by hecato on 2007-10-27
Also[LIST]
[*]print the code a specific file or files in 4 per paper page with line numbers (more readable code) and put "Stapling" (<- is the correct word?) on them. Thus you can[LIST]
[*]Carry it away of computer like going to school, or in the collective
[*]Make Hand annotations in paper (at less I like also work the not computer way)
[*]printing 4 per page also is more cheap, more lines per page thus more info and more compactness of it[/LIST] 
[*]If there no exist a file that explain the organization, get the names of functions, classes and his methods (even that you don't get the hierarchy or pattern apply at first time), the point is to have a *reference of names*.[/LIST]To the moment I have only read and modified 2 sources: nasm and openssh, there are other sources that I have read but not much: bash (very well organized), Ogre3D (for example it doesn't have error handling for X calls IIRC), GCC, Mesa[LIST]
[*]You not always need to understand all the sources in the project, sometimes is enough with a part of them
[*]Also remember that perhaps you are able to read certain part of code, but they are linked with some concepts that perhaps you don't know (mathematical, related to something you don't know and haven't seen in your life?), thus you will not realize "all the thing" without going more far than source (an get some little knowledge about), why that way or other questions about implementation.
[*]Also try to **read them actually**!!!, perhaps you will not able to read them the first time, go with other source and read it (I know that I have already put this, but anyway). Or reread something that you have already read (for see if you discover something new or that you haven't seen before, something that you miss in the design or flow).
[*]Trace it manually where you think, "Im here because this and this success", if you dont get your trace, thus you are probably understanding something wrong or the events that you wait aren't happening at all, or other thing
[*]Codes are not magic! ;), *they perhaps can have at execution some tricky behaviours, but all that you need to understand that is in the source* ;).[/LIST]If I remember another point, I will write it :).

---

### Post by pmasiar on 2007-10-27
> **g8m said:**
> Let's take this example. You just love this pizza, but hate the goat cheese they're using. Can you use the pizza, scrape off the goat cheese and add gouda? 

Really bad analogy if I can tell. Making small change in a big program is very often the simplest a cheapest way to proceed. Throwing away working code is almost always mistake. Of course it depends how big change you need to make: the bigger part is to be replaced, the less is makes sense to keep old code. 

> My point beinig, It;s damn hard reading sources, 

No it is not. It depends on quality control when accepting the code, If you have coding standards, reading code of other people is not much harder than your own.

>  not only do you have to understand the flow, you have to think three dimensional, adding values to the variables.

Of course. But your new code has all the bugs which were fixed in old code.

---

### Post by hecato on 2007-10-28
> 
But I guess, thinking money, makes this very difficult. It took a year to program, and changing it takes a year to reprogram. The original programmer would probably need just one hour, but you fired him because that seemed cheeper at the time.
It depend on a lot of factors, 1 of them "luck"... I dont trust in luck (at less the normal sense) lol. Other can be knowledge and prior work related to read other people code, know how to do reading (or some like that), and know that perhaps you will find fun things or things that you haven't seen before ;), or have seen them but not used implemented that way and get to them.

When some one hired me for modify openssh, I get and explanation of my boss all that was to confusing some like "scared", but after some time, I see that those things was only assumptions and ignorance of the code, there was other approach, and after convince boss of let me do it thus following that path I realize that there where no point in have those modifications inside the openssh code, thus I managed to modify only little specific parts of openssh, and not all the madness that appear at first sight (and that was suggested), also winning more easy integration with a new version with openssh (little code to modify... little lines!), but those little modifications took some time :) to "get where and what and why", yes perhaps to a person that know before hand openssh code internals and more if is developing it and also the other project that where trying to "interface it", it would  do it more fast, no doubt. 

But other persons apart of the original authors can grasp "estrange" code (of others, estrange because you don't know it), at the end, code is something to be read be humans ;). Also I learned some things, I don't have the list that I put above, I collected some points in that work, and this thread remember me a little of what I do and "tricks" that I learn or see actually implemented in openssh, like a dispatch of functions via a table in 3 different configurations for each version of the protocol (that was fun) thought I don't get it completely all the cases, but I get the idea and first time was like a wall and after understand some of it, was only a interesting way to do things, before I know functions pointer, but haven't seen them actually doing something like that.


I must admit that I don't know all the internals of openssh or if I can contribute something actually to it, but I have some idea of how is organized and how it works in some specific places. Also I haven't mess with the encryption algorithms (like also suggested at first time by boss ;)).
 Perhap later... lol. I quote me in this case
> You not always need to understand _all_ the sources in the project, sometimes is enough with a part of themI guess it depend in how wide really the modification is (not in expectation based in ignorance of others code). And how well you can locate it. (I have read lot of code, but actually only modify like 3 to 5, 7 functions, and only some lines, and added 1 global variable IIRC (yea blame me :P)... lol!!! and perhaps that work can also be reduced).

---

### Post by g8m on 2007-10-28
> **pmasiar said:**
> Really bad analogy if I can tell..

No it is not.

> **pmasiar said:**
> 
No it is not. It depends on quality control when accepting the code, If you have coding standards, reading code of other people is not much harder than your own
.

Yes it is. At least for me. Even with quality control stamps on the code, I have a really hard time reading the kernel source.

---

### Post by evymetal on 2007-10-31
> **hecato said:**
> Also[LIST]
[*]print the code a specific file or files in 4 per paper page with line numbers (more readable code) and put "Stapling" (<- is the correct word?) on them. Thus you can[LIST]
[*]Carry it away of computer like going to school, or in the collective
[*]Make Hand annotations in paper (at less I like also work the not computer way)
[*]printing 4 per page also is more cheap, more lines per page thus more info and more compactness of it[/LIST] 


Wow, "Carry it away of computer" ? Not sure I understand the idea of going away from a computer, lol. 

Seriously, though. If you like reading (I don't - dyslexia means I read things much faster when they are on a backlit screen than on paper, and I get a headache after about 15 minutes if I'm reading paper based things) then this is a good idea. 

Even with my hatred of reading I have to admit I still print-off for bug-fixing large functions - you just can't see all of the code on a screen. You could also try opening up two copies of the source so you can keep the calling function open while you look at a function it's calling.

---

### Post by bfhicks on 2007-10-31
Personally, I wouldn't listen to anything g8m has said.

The whole idea behind open-source software and object oriented programming is so that you don't HAVE to throw stuff away. It makes no sense to re-invent the wheel!

When working with an open-source project, or proprietary software with a company, the biggest thing that can help, at least from my experience -- with a proprietary software base consisting of millions of lines of code and in-house API -- is to not get discouraged by complexity or number of lines of code. When I first looked at some of the code base, I was overwhelmed. Having UML diagrams, dependency charts, flow charts, can all help with this. Loading some code up in a debugger and stepping through the program can be very useful in many situations also.

Another key, learn what is good and bad from what you read. You will quickly learn that some software is very easily followed -- not just because it lacks complexity but b/c it was written to be READ by humans, not just by computers. It seems, today, that many programmers fall in love with this "one line does it all" deal, when an 8 line code segment would be much easier to follow.

If the software doesn't have good comments, uses bad function/class naming, and is written in a confusing format, I would suggest to make a request for someone else or attempt to make it better.

Don't try to absorb the entire program and everything that is going on -- your brain can't handle it (unless you are an exception). The whole idea behind good programming is designing software that is modularized so that your brain only has to focus on one thing at a time.

but i ramble...

---

### Post by tyoc on 2007-10-31
> Seriously, though. If you like reading (I don't - dyslexia means I read things much faster when they are on a backlit screen than on paper, and I get a headache after about 15 minutes if I'm reading paper based things) then this is a good idea.I don't like reading, I only have go from first to end of at much like 3 books in my life... and they where not "big" stories, perhaps not more than 200 pages, even perhaps less than 100. But yes, I have used that technique of 4source pages per page for do annotations, annotate functions, doing documentation (in my own interpretation) for an unknown module. It also help to have 2 places to see the code, 1 on screen 1 on paper, it also help to say "o yea, I have seen that function there", group functions by functionality and so on (with colors, etc, etc, bla, blah :P).

> If the software doesn't have good comments, uses bad function/class naming, and is written in a confusing format, I would suggest to make a request for someone else or attempt to make it better.haha, I have to read and understand a code with [antipattern]("http://en.wikipedia.org/wiki/Anti-pattern") style ;), some of them I remember in top of my head are: lava flow, extra complexity, god object (aka doing all ala C in an object), and so on. I suggest a complete re engineering that time, perhaps that was to much (or not?), but they didn't take that path. I was able to understand major part of it, and also was able to think of a better way, but people there think that re engineering mean "add features" ;). The interesting about that program is that it was running or it work.

---

### Post by khughitt on 2008-01-12
[Doxygen]("http://www.stack.nl/~dimitri/doxygen/") is another useful tool that can help you to understand code. Even if the authors didn't already comment the code for Doxygen, it is still able to give you some useful information about the structure of the classes,etc.

---

### Post by nfm on 2008-02-21
I was just about to post a new thread about doxygen :\
Does anybody have simple instruction on how to get started with doxygen? I tried it a while ago and I was unsuccessful , probably because of being time limited or I missed something. I would like to get started with simple program such as Hello World in C Lang.

---

### Post by cb951303 on 2008-02-21
g8m: what's the purpose of open source if we're gonna build everything from scratch?

---

### Post by Zwack on 2008-02-21
Some useful suggestions above...

My usual answer... It depends...

1) Why are you wanting to read the source code?

If it's a learning experience then start small and work up.  Try reading one function and understanding it.  Write some pseudocode for it that seems to do what it does.  Then try another and so on.  Eventually you will have a full documented pseudocode for the application...  You should know what ti does and why.  If you don't understand part of it, then give up... Find a different part, come back later.  If something seems tricky but interesting try writing your own code that works the same way as a test.  See what the results are.

If you're trying to modify some behaviour then you should look for the part that is most relevant and work back from there.  If it's Open Source try contacting the developers, don't say "fix this for me" but "This does that, and I was wondering where in the source I should look for that bit?"  and they might help you.  They might not... but it's worth asking.  Particularly as you're not asking them to do more than tell you where to start looking.

2) Print it out... It's easier than trying to get your annotations off of your computer screen.  :)  And it may be more portable.  Don't print the whole thing at once, just do it in chunks.

3) If something is unclear to you try mentally stepping through it... Or run it through a debugger.  If you still don't get it come back later.

As for the other comments about Pizza... A bad program (open or closed source) is like a pizza, hard to modify and you may not like the results.  A good program is more like a Lego castle, you can take it apart and rebuild it... you may have some spare bits, you may have made a large change or a small change, but you can reuse large pieces without tearing the whole thing down.

I hope that this helps,

Z.

---

