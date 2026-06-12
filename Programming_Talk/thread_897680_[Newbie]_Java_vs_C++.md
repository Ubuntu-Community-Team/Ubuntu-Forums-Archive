---
title: "[Newbie] Java vs C++"
date: 2008-08-22
forum: Programming Talk
---

### Post by aGor on 2008-08-22
Hello all!

I am a newbie when it comes to programming.
I know a little C++ (VERY little I guess), and I have a hard time learning it.

I was thinking of learning Java first, instead of C++.
My goal is to master a lot of different programming languages, so starting with something that's a bit easier wouldn't be a bad idea I guess.

And, what books about Java (for newbies!) would you recommend?

Thanks in advance.

---

### Post by StOoZ on 2008-08-22
to master alot of languages? why? you wont master alot of languages that easy.

stick to one language for now , if you want something "easy" (relatively easy...I don't know it , but thats what most people say) go with python

---

### Post by Wybiral on 2008-08-22
> Java vs C++

](*,)

---

### Post by aGor on 2008-08-22
Because programming is a subject that interests me, and by mastering alot of languages, I can choose what suits the best for my project :>

---

### Post by jimi_hendrix on 2008-08-22
im a beginer too but heres what you should do...pick a simple language and learn the basics then pick the type of programming that intrests you then move twards that type of programming

---

### Post by pmasiar on 2008-08-22
We just had 3 flamewars about exactly this question: what is best language for a beginner.

So will this start yet another one? We shall see. For reasons why, read (warning: long and heated, like this one is likely going to be)

[Lessons about biases learned from language flamewars](http://ubuntuforums.org/showthread.php?t=896087)

[It's not wrong not knowing, but it's wrong not wanting to know.](http://ubuntuforums.org/showthread.php?t=890695)

[[Recommend] Which Next Language Suits My Skill Set?](http://ubuntuforums.org/showthread.php?t=894995)

Or if you want to save time and skip reading, just start with Python, then learn both C++ and Java: after Python it would make more sense.

---

### Post by Reiger on 2008-08-22
Regardless wether or not you do Python first or later or not at all...

If you're a beginner programmer you may want to do Java first before you do C++ because of the fact that Java is 'safe' compared to C++. Which is to say: if you mess up bad you won't hose your system with Java but you might just wreck it with C++.

---

### Post by CptPicard on 2008-08-22
> **Reiger said:**
> Which is to say: if you mess up bad you won't hose your system with Java but you might just wreck it with C++.

Well, hardly. The worst thing that n00b gets is a segfault which is annoying enough :)

You're right though, OP should do definitely do Java instead of C++.

---

### Post by nrs on 2008-08-22
> **Reiger said:**
> 
If you're a beginner programmer you may want to do Java first before you do C++ because of the fact that Java is 'safe' compared to C++. Which is to say: if you mess up bad you won't hose your system with Java but you might just wreck it with C++.

Can you tell me how a beginner might hose his system with C++?

---

### Post by tribaal on 2008-08-22
Whatever language you choose, I think the most important is to learn and master programming *concepts*, not programming languages.

Important concepts (other than basic loops, branches...), in no particular order:
- Object-oriented programming
- Design patterns
- Memory management (pointers...)
- Recursivity
- Data structures (stacks, queues, trees...)
I guess the list can go on for a while, that's just on top of my head.

Some languages fit theses general ideas more than others (you can't manage memory as finely in Java than what you can do in C++ for example), but some concepts like design patters and Object-oriented programming can be learned indifferently in C++, Java, Python, Ruby...

Learning how to program, just pick whatever language you fancy, and start doing stuff with it :) Then learning new languages become increasingly easy as the concepts you learned are still valid - it comes down to a different syntax more or less.

I hope you'll have many years of perseverance and fun - you'll need both in equal parts :)

- Trib'

---

### Post by LaRoza on 2008-08-22
> **tribaal said:**
> 
Important concepts (other than basic loops, branches...), in no particular order:
- Object-oriented programming
- Design patterns
- Memory management (pointers...)
- Recursivity
- Data structures (stacks, queues, trees...)
I guess the list can go on for a while, that's just on top of my head.


Well, that would depend on the language. Some languages don't support recursive functions and some languages don't support loops. I think structured programming is more important than OO programming and would suggest that first. A structured program is almost always good, an OO program often has unneeded objects because the programmer feels a need to use them (see beginner challenges, some weird objects there!)

Programmatically, there is no big difference between Java or C++ (the only thing would be the lack of a GC).

For the OP, I suggest you read the stickies and my wiki. There are guides for learning and discussions on what is good for beginners.

---

### Post by nrs on 2008-08-22
Now that I understand where the Python Mafia is coming from, and that they're not shouting "omg write a kernel in python!#!$", I agree with them. You spend less time learning about language idiosyncracies (though there are still some bafflers) and more time learning things like logic, design patterns, etc, etc.

---

### Post by tribaal on 2008-08-22
> Well, that would depend on the language.

Totally - That's what I wanted to express with my memory management example in my previous post, I should have picked a better example.

My point is still valid I believe, learning programming concepts is more important than learning programming languages.

As to what concepts one should learn first, I concur with you, I'd learn structured programming first, but OO concepts are important to learn too. 
I try to be as language-agnostic as I can, since I wish to remain a professional programmer for a long time :)

Anyway, I guess you got my point :)

- Trib'

---

### Post by hod139 on 2008-08-22
> **LaRoza said:**
> Some languages don't support recursive functions and some languages don't support loops. 
I've learned about old languages (e.g. old fortran) without recursive method calls, but no looping?  I've never heard of a language that doesn't have looping. 

Maybe I'm being pedantic about the definition of loop, but  all languages that I've ever dealt with or heard of have at least some form of a goto/jump, which is all looping really is

```

loop_start:
 do stuff
goto loop_start

```

I'm only asking because I'm interested if there really is a language that does not allow a set of instructions to be repeated N times, or if I'm not understanding your interpretation of looping.

---

### Post by pmasiar on 2008-08-22
> **nrs said:**
> Now that I understand where the Python Mafia is coming from, and that they're not shouting "omg write a kernel in python!#!$", I agree with them. 

Thank you, but we (if I assume to be a part of the "python mafia") **never** suggested to write kernel in Python. In fact, I always suggested to any beginner to learn C **after learning Python** to really understand how CPU works, or even ASM. But always **after Python**, because Python allows beginner to write programs and learn basics without distracting with irrelevant (for beginner) details like types, typecasting, OOP, and memory management. Yes, they are important to master - but for beginner they are distracting.

So I am glad that yet another UF member actually bothered to read and understand what we say, not what haters say we say.

Thank you.

---

### Post by pmasiar on 2008-08-22
> **hod139 said:**
> I've never heard of a language that doesn't have looping. 


[http://www.ibm.com/developerworks/xml/library/x-tiploop.html](http://www.ibm.com/developerworks/xml/library/x-tiploop.html)

> XSLT is a functional programming language like Haskell or Scheme, and unlike C or Fortran. Thus it has no loops and no mutable variables. Instead, you must replace these constructs with recursion and parameters.

Not only no loops: no variables too. Take that, agnosticists! (not you of course)

> 
XSLT is Turing complete. This means that given sufficient memory, XSLT can calculate anything any other Turing-complete language (such as C++) can calculate. 

Live long, learn and prosper.

---

### Post by jimi_hendrix on 2008-08-22
> **Reiger said:**
> Regardless wether or not you do Python first or later or not at all...

If you're a beginner programmer you may want to do Java first before you do C++ because of the fact that Java is 'safe' compared to C++. Which is to say: if you mess up bad you won't hose your system with Java but you might just wreck it with C++.

how can you wreck your system?

---

### Post by jimi_hendrix on 2008-08-22
> **LaRoza said:**
> some languages don't support loops.

just curious...what language doesnt?

edit: didnt see pmaiser's answer to the same question

---

### Post by hod139 on 2008-08-22
> **pmasiar said:**
> [http://www.ibm.com/developerworks/xml/library/x-tiploop.html](http://www.ibm.com/developerworks/xml/library/x-tiploop.html)



Not only no loops: no variables too. 
Maybe I'm being ultra pedantic, but in my book looping is a subset of recursion.  A language with recursion has, by definition, looping.  

I guess that a distinctions of looping must be made at the paradigm level (functional, imperative, etc).  But, I think, looping must be available in every language.

---

### Post by jimi_hendrix on 2008-08-22
> **hod139 said:**
> 

```

loop_start:
 do stuff
goto loop_start

```


how would that loop terminate though...i only know OO languages with while, if, do, and for loops and ive never used a GOTO

---

### Post by hod139 on 2008-08-22
> **jimi_hendrix said:**
> how would that loop terminate though...i only know OO languages with while, if, do, and for loops and ive never used a GOTO
It wouldn't; but loops don't have to terminate.  My point was just to show how jumps can be used for looping.  Similar to how recursion can be used to perform looping in a functional language (though recursion is more powerful, some things are more difficult to express in a loop than they are to express recursively)

---

### Post by jimi_hendrix on 2008-08-22
then how would you pass the goto line if you wanted to terminate it

---

### Post by peter_brewer on 2008-08-22
You could put an if condition in the goto loop which if true then uses another goto to go somewhere else.  Though there is no reason to use goto's when better looping constructs exist.

---

### Post by pmasiar on 2008-08-22
> **hod139 said:**
> Maybe I'm being ultra pedantic, but in my book looping is a subset of recursion.  A language with recursion has, by definition, looping. 

Your logic does not work. Loop cannot be subset of recursion if there are languages (like good old Fortran) with loops but no recursion.
 
Recursion can replace loop (with quite lot of stretch) but it is not as obvious to beginner as simple loop (and RAM might complain, too :-) )

---

### Post by hod139 on 2008-08-22
> **pmasiar said:**
> Your logic does not work. Loop cannot be subset of recursion if there are languages (like good old Fortran) with loops but no recursion.

Fortran (how I hate thee) does not allow the super-set (recursion), but allows the subset (jumping) .  What's wrong with that logic?

 > 
Recursion can replace loop (with quite lot of stretch) but it is not as obvious to beginner as simple loop (and RAM might complain, too :-) )
Sure, but RAM is cheap :)

---

### Post by CptPicard on 2008-08-22
> **hod139 said:**
> Maybe I'm being ultra pedantic, but in my book looping is a subset of recursion.  A language with recursion has, by definition, looping.  


Umm, yes you are being pedantic because I always have understood a "loop" as being an iterative loop ("for loop").

Of course, a language is not even Turing-complete (IIRC) if it can't express recursive concepts in some way, either with explicit stack with some repetition for top of stack or alternatively recursion.

---

### Post by hod139 on 2008-08-22
> **jimi_hendrix said:**
> then how would you pass the goto line if you wanted to terminate it
When writing that silly example up, I didn't want it to terminate; I just wanted to show a loop using jumps.  It's not a good idea, shouldn't be done, but it is possible and was the only way in older languages.  If you really want to use gotos with loop exit conditions, it would have to look like this:

```

loop_start:
 do stuff
 if done goto loop_exit
goto loop_start

loop_exit:

```

Note, I don't advocate this idea, it was just to show how looping was done with jumps before better idioms became available.

---

### Post by nvteighen on 2008-08-22
Code is the best way to show things:

```

; A Scheme implementation of Python's 'in' operator.

(define in?
  (lambda (data lst)
	(let myloop ((i 0)) ; <-- Start of looping block.
	  (if (>= i (length lst))
		  #f
		  (if (= data (list-ref lst i))
			  #t
			  (myloop (+ i 1))))))) ; <-- Recurse!

```

I was to lazy to think on an example, so I took some piece of code I wrote for something.

What do we have here is just a procedure that loops (iterates) through a list checking each element against the 'data' parameter. If found, the procedure returns true (#t) and stops looping. If not found, it calls itself recursively, but passing the counter incremented by one as parameter... If we reach the list's length by looping, it means there's no match and we return false (#f).

There's no loop, no goto; just recursion: a local procedure (declared by 'let', I called it 'myloop' but I could call it something else) that calls itself under certain circumstances.

---

### Post by Reiger on 2008-08-22
> **pmasiar said:**
> [http://www.ibm.com/developerworks/xml/library/x-tiploop.html](http://www.ibm.com/developerworks/xml/library/x-tiploop.html)

XSLT does, actually have ways of looping in the sense of iterating (over an object set/collection) ... It has:
[html]
<xsl:for-each select="xpath">
</xsl:for-each>
[/html]

Which is semantically equivalent to:
[PHP]
foreach ($iterable_structure as $iteration) {
}
[/PHP]

Or Java's:

```

for ( Type var : IterableCollectionOfType) {
}

```

---

### Post by Lundis123 on 2008-08-22
<ontopic>
I recommend the book [Learning Java]("http://oreilly.com/catalog/9780596008734/").
Java was my first language and that book really taught me a lot!
</ontopic>

---

### Post by LaRoza on 2008-08-22
> **Lundis123 said:**
> <ontopic>
I recommend the book [Learning Java]("http://oreilly.com/catalog/9780596008734/").
Java was my first language and that book really taught me a lot!
</ontopic>

What has learning Java helped you with in other languages?

---

### Post by Jessehk on 2008-08-22
You're all getting ahead of yourselves.

To the original poster: Java is an excellent choice for a (notice: not **the**, but **a**) first language with respect to library availability to do neat things, community support -- which means lots of resources online, and wide availability of tools and supporting software on many platforms.

The disadvantage to Java? It's not the most well-designed language from a CS perspective. However, I honestly feel that this issue is less significant than this forum would have you believe. Once you understand basic concepts (and I mean **really** basic concepts like conditional statements, loops, the concept of what a program actually **does**), than there's plenty of time to learn the more fun and interesting languages **if it appeals to you to do so**. 

These can include anything really, but popular choices now (all interesting for different reasons: either moving further away or closer to the hardware, a shift in thinking, and others) are C, C++, C#, Python, Perl, Ruby, Common Lisp or Scheme, Haskell, OCaml, etc.

There's plenty of time for all that if you're interested, but don't get overwhelmed.:)

---

### Post by Kadrus on 2008-08-22
> C, C++, C#, Python, Perl, Ruby, Common Lisp or Scheme, Haskell, OCaml, etc.
You added Ocaml ^.^(after editing :-P)

_edit_
*Java vs C++*
Go With [D]("http://en.wikipedia.org/wiki/D_(programming_language)").

---

### Post by Lundis123 on 2008-08-22
> **LaRoza said:**
> What has learning Java helped you with in other languages?

if, while, for, data types, collections, arrays, OOP, regular expressions, how to make GUIs(looked at TKinter and it was pretty much the same as swing), how pics are represented at byte-level, basic XML etc. There are probably more things but that's all I can think of right now. 

The point is, if I wanted to learn java from scratch again, I would love this book. If you know any better books, go ahead and recommend them, but so far I'm the only one who has recommended a book to the OP(I think).

---

### Post by pmasiar on 2008-08-22
> **Lundis123 said:**
> If you know any better books, go ahead and recommend them, but so far I'm the only one who has recommended a book to the OP(I think).

maybe you should check sticky - and recommend OP to do that, to, for more book recommendation.

And maybe we need to reformat sticky so it will be "get info in 5 clicks or less".

---

### Post by jimi_hendrix on 2008-08-22
or have it so that the first time that the user comes to the forum he has to go to sticky...then he gets a cooky that redirects him to the main page after that so he doesnt have to always go to the sticky

---

### Post by LaRoza on 2008-08-22
> **pmasiar said:**
> 
And maybe we need to reformat sticky so it will be "get info in 5 clicks or less".

I will work to flatten it out.

---

### Post by Lundis123 on 2008-08-23
I didn't know there were book recommendations it that sticky, but I found it now. Great thread, it is!

---

