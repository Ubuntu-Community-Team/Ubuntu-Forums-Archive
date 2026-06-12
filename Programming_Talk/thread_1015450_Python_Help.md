---
title: "Python Help"
date: 2008-12-18
forum: Programming Talk
---

### Post by Swenghk on 2008-12-18
I was writing a script in Python and I need to know how to return to the top of a conditional statement without using the "continue." For example:

```

security = 0
username = ""
while not username:
    username = raw_input("Username: ")

password = ""
while not password:
    password = raw_input("Password: ")

if username == "seth" and password == "allen":
    print "Welcome, Seth. Security level 5"
    security = 5
elif username == "guest" and password == "guest":
    print "Welcome guest. Security level 1"
    security = 1
else:
    print "Invalid login..."
```


I want to know how to return to the "Username: " prompt if you get an invalid login. Thanks!

---

### Post by mssever on 2008-12-18
> **Swenghk said:**
> I was writing a script in Python and I need to know how to return to the top of a conditional statement without using the "continue." For example:

```

security = 0
username = ""
while not username:
    username = raw_input("Username: ")

password = ""
while not password:
    password = raw_input("Password: ")

if username == "seth" and password == "allen":
    print "Welcome, Seth. Security level 5"
    security = 5
elif username == "guest" and password == "guest":
    print "Welcome guest. Security level 1"
    security = 1
else:
    print "Invalid login..."
```
I want to know how to return to the "Username: " prompt if you get an invalid login. Thanks!
You could wrap everything in a while loop and use break to get out of the loop when login is completed.

---

### Post by mbsullivan on 2008-12-18
Hi Swenghk,

Conceptually, what you want is a "goto", which is not possible in Python. Gotos were intentionally left out of Python, with good reason.

Therefore, you need to start thinking in a new manner when planning code, in order to avoid gotos. I think the easiest way to accomplish what you want would be to put the query code into a function, and recurse to that function again if the input is invalid.

In the future, questions like this may be more appropriate in the "programming" forum.

Let me know if you have any questions!
Mike

---

### Post by mbsullivan on 2008-12-18
Hi Swenghk,

It's not a good idea to double post. I responded to this in the other forum, should you care to check.

Mike

---

### Post by Achetar on 2008-12-18
On a side note you should use multiple hashes like md5,sha1 and sha256 (or write your own) to encrypt the passwords.

---

### Post by digitalvectorz on 2008-12-19
> **mssever said:**
> You could wrap everything in a while loop and use break to get out of the loop when login is completed.

I'd have to agree with this method;  At least as a quick fix for this particular situation.

---

### Post by unutbu on 2008-12-19
[PHP]#!/usr/bin/env python
valid=False
while not valid:
    username = raw_input("Username: ")
    password = raw_input("Password: ")
    if username == "seth" and password == "allen":
        print "Welcome, Seth. Security level 5"
        security = 5
        valid=True
    elif username == "guest" and password == "guest":
        print "Welcome guest. Security level 1"
        security = 1
        valid=True
    else:
        print "Invalid login..."
        valid=False  # Not really needed
[/PHP]

---

### Post by digitalvectorz on 2008-12-19
unutbu, though that code may in fact work, we're trying to keep along the lines of letting the OP overcome some hurdles themselves.  Had your code had comments for the OP to read, I wouldn't necessarily be writing this, but you just blatantly gave him a solution without letting him work the kinks out and learn from his mistakes.

As stated,
> I want to know how to return to the "Username: " prompt if you get an invalid login. Thanks! 
The **how** has been given, the code, was not.  Please use a little more discretion when posting 'solutions.'

Thanks.
dvz

---

### Post by unutbu on 2008-12-19
I disagree. Learning can be accomplished by sharing code. [http://ubuntuforums.org/showpost.php?p=6140092&postcount=27](http://ubuntuforums.org/showpost.php?p=6140092&postcount=27)

---

### Post by digitalvectorz on 2008-12-19
touche'

---

### Post by fiddler616 on 2008-12-19
+1 for enclosing in a while loop.
Although it seems cleaner to have a
[PHP]
while True:
    #some stuff
    #Oh, it's valid. Let me get out of this loop!
    break[/PHP]

---

### Post by Swenghk on 2008-12-19
That was one of the things I didn't like about Python. The GOTO and LABEL commands were SO helpful in BASIC!

---

### Post by mssever on 2008-12-19
> **Swenghk said:**
> That was one of the things I didn't like about Python. The GOTO and LABEL commands were SO helpful in BASIC!
There are *very* few legitimate reasons to use goto. The overwhelming majority of well-written programs won't use it at all. It's much better to move beyond the 1960s and use more modern techniques. Examples of ways to replace goto include loops and functions.

---

### Post by thornmastr on 2008-12-19
> **unutbu said:**
> I disagree. Learning can be accomplished by sharing code. [http://ubuntuforums.org/showpost.php?p=6140092&postcount=27](http://ubuntuforums.org/showpost.php?p=6140092&postcount=27)

The fact is, unutbu (interesting name) first offered a solution which is (1) viable and (2) easily understood even by a very inexperienced noob. It is, in my opinion, an excellent way to learn. 

If it had been viable but not easily understood, he should offer a detailed explanation.

=R=

---

### Post by pmasiar on 2008-12-19
> **Swenghk said:**
> That was one of the things I didn't like about Python. The GOTO and LABEL commands were SO helpful in BASIC!

You are surely joking, right?

And anyway, Python does have GOTO (as a joke), and even COMEFROM!

[http://entrian.com/goto/](http://entrian.com/goto/)

PS. In fact someone missed it, it is a **JOKE**.

---

### Post by fiddler616 on 2008-12-19
[FONT=Arial][SIZE=2]> **Swenghk said:**
> That was one of the things I didn't like about Python. The GOTO and LABEL commands were SO helpful in BASIC!
I had this very same culture shock over the summer (I actually posted a thread whining about how I'd Google for GOTO in Python and couldn't find it, and did somebody know the syntax?(Shame....))
What I've learned is:
[/SIZE][/FONT] 
[LIST]
[*][FONT=Arial][SIZE=2]GOTO can create *problems* in logic. Readability, maintainability, understanding-by-a-third-party, debugging--they all suffer.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]The answer, as previously mentioned, is to use other logic (while and for)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]You'll figure out more elegant ways, but for now:[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]```
[color=#408080]*#Bad code:*[/color]
LBL Start
user_input [color=#666666]=[/color] [color=#008000]raw_input[/color]([color=#BA2121]"Enter something..."[/color])
[color=#008000]**if**[/color] user_input [color=#666666]=[/color] bad_idea:
    [color=#008000]**print**[/color] [color=#BA2121]"Invalid input"[/color]
    GOTO Start
[color=#408080]*#Proceed with the rest of your life*[/color]

```
can easily be replaced with:
[/SIZE][/FONT][FONT=Arial][SIZE=2]```
[color=#008000]**while**[/color] [color=#008000]True[/color]:
    user_input [color=#666666]=[/color] [color=#008000]raw_input[/color]([color=#BA2121]"Enter something..."[/color])
    [color=#008000]**if**[/color] user_input [color=#666666]!=[/color] bad_idea: [color=#408080]*#Note '!'*[/color]
        [color=#008000]**break**[/color]
    [color=#008000]**else**[/color]
        [color=#008000]**print**[/color] [color=#BA2121]"Invalid input"[/color]
[color=#408080]*#End while*[/color]
[color=#408080]*#Proceed with life*[/color]

```
And there are much more Pythonic ways of dong that, by the way, but it's a bit too late for my brain function at that level.
You see where I'm going, though.
[/SIZE][/FONT]

---

### Post by fiddler616 on 2008-12-19
> **pmasiar said:**
> You are surely joking, right?

And anyway, Python does have GOTO (as a joke), and even COMEFROM!

[http://entrian.com/goto/](http://entrian.com/goto/)

PS. In fact someone missed it, it is a **JOKE**.
Yes, it really does work.
Yes, if you use it the Greater Python Community will hunt you down and amputate your fingers and voicebox, such that you can never program again.
:)

---

### Post by mbsullivan on 2008-12-19
> 
    * GOTO can create problems in logic. Readability, maintainability, understanding-by-a-third-party, debugging--they all suffer.


There are two major arguments, in my thinking, against Goto. The first, coming from a software engineering point of view, is as you said. Liberal uses of goto statements can create so-called "spaghetti code", which suffers from readability and debugging issues. The original case against them, which argues along these lines, was given by Djikstra and can be found [here]("http://www.cs.utexas.edu/users/EWD/transcriptions/EWD02xx/EWD215.html").

Another problem with Goto statements is that they needlessly complicate the control flow of a language, making compilers for that language slower and harder to make. In compiler-speak, gotos can make the control flow of a language *irreducible*, which is not a good thing for compiler writers, or for people who want the generated code to be as optimized as possible.

Mike

---

### Post by fiddler616 on 2008-12-19
> **mbsullivan said:**
> There are two major arguments, in my thinking, against Goto. The first, coming from a software engineering point of view, is as you said. Liberal uses of goto statements can create so-called "spaghetti code", which suffers from readability and debugging issues. The original case against them, which argues along these lines, was given by Djikstra and can be found [here]("http://www.cs.utexas.edu/users/EWD/transcriptions/EWD02xx/EWD215.html").

Another problem with Goto statements is that they needlessly complicate the control flow of a language, making compilers for that language slower and harder to make. In compiler-speak, gotos can make the control flow of a language irreducible, which is not a good thing for compiler writers, or people who want the generated code to be as optimized as possible.

Mike
Thanks--I didn't know the second half. Although, since when do Python programmers lose sleep over the compiler? (Besides semi-interested forays into PyPy, Jython, etc.)?

---

### Post by mbsullivan on 2008-12-19
> Although, since when do Python programmers lose sleep over the compiler?

A simple compiler can only be a good thing :) Fewer bugs, and more time to focus on libraries and new language features.

> Besides semi-interested forays into PyPy, Jython, etc

PyPy, Jython, and especially Psyco seem to work well for speeding up the execution of Python code. I don't use any of them, but then again I don't use Python for scientific programs.

If I did, I'd probably use Psyco. Requires 2 lines of extra code, and you can expect a 5-10x speedup. Sweet!

Mike

---

### Post by pp. on 2008-12-19
> **fiddler616 said:**
> GOTO can create *problems* in logic. Readability, maintainability, understanding-by-a-third-party, 

Actually, the GOTO statement ***is*** the problem, though by no means the only one.

The remedy does, however, not consist of coding programs the same way as before but without using that statement.

Out of the understanding of the fundamental flaw introduced by the GOTO statement grew the discipline or paradigm of structured programming which set the bar for practically all procedural languages in use today.

It is my personal opinion that the discussions and observations which led to those insights later led in a nearly straight line to functional and declarative programming.

---

### Post by unutbu on 2008-12-19
```
% find /usr/src/linux -name '*.c' -exec grep -l 'goto' {} \; | wc
   4717    4717  248564
```

---

### Post by mssever on 2008-12-19
> **unutbu said:**
> ```
% find /usr/src/linux -name '*.c' -exec grep -l 'goto' {} \; | wc
   4717    4717  248564
```
Yes, the kernel is one of the few well-written programs which use goto. Linus has argued that there are some situations where it's useful, and who am I to argue with him?

However, the kernel developers are experienced programmers who know what they're doing. Most rules can be broken if you know what you're doing, but that doesn't mean the rules don't serve a valid purpose. Certainly, newbies have no business even thinking about goto. They should consider it anathema.

---

### Post by pmasiar on 2008-12-19
> **mssever said:**
> Yes, the kernel is one of the few well-written programs which use goto. Linus has argued that there are some situations where it's useful, and who am I to argue with him?

First one arguing **for** GOTO was IIRC Knuth. GOTO is the only **structured** way to handle exception in language with no exception handling, like C (and one more reason to start with a language **with** exceptions).

---

### Post by pp. on 2008-12-20
Once you get over with using GOTO for "normal" programming you will detect that GOTO is unavoidable for some constructs. As far as I am aware those constructs all deal with handling situations which are external to the program containing the GOTO. pmasiar already mentioned one; program inversion would be another one.

---

### Post by nvteighen on 2008-12-20
> **mbsullivan said:**
> 
Another problem with Goto statements is that they needlessly complicate the control flow of a language, making compilers for that language slower and harder to make. In compiler-speak, gotos can make the control flow of a language *irreducible*, which is not a good thing for compiler writers, or for people who want the generated code to be as optimized as possible.


That's why MS QuickBasic 4.5's compiler (bc) didn't accepted to native-compile programs written with GOTO (believe it or not: there was sanity in QB4.5!) If you used GOTO, you were forced to use bytecode compilation.

---

### Post by mssever on 2008-12-20
> **pp. said:**
> Once you get over with using GOTO for "normal" programming you will detect that GOTO is unavoidable for some constructs. As far as I am aware those constructs all deal with handling situations which are external to the program containing the GOTO. pmasiar already mentioned one; program inversion would be another one.
But that's language-dependent. Some languages, such as Python, get by just fine without goto. pmasiar's example is exception handling, but Python--and many other languages--already have built in exception handling. So there's no need for goto in those languages.

As for program inversion, would you care to enlighten me on what that is? I've never encountered the term before, Wikipedia knows nothing about it, and Google's results were unhelpful.

---

### Post by pp. on 2008-12-20
> **mssever said:**
> As for program inversion, would you care to enlighten me on what that is? I've never encountered the term before, Wikipedia knows nothing about it, and Google's results were unhelpful.

Program Inversion is a scheduling technique taught by Michael Jackson in the late seventies, I believe. 

Programming according to Jackson was an extension of Structured Programming. Jackson taught that every program had to exactly represent the structure of the data to be processed. 

The methods taught by Jackson had to cope with programs dealing with data of mutually incompatible structures, so called Structure Clashes. Jackson's solution was a quite elegant reduction of the problem to a selection of scheduling decisions.

Program dismemberment and program inversion were scheduling techniques which transformed programs in a manner which conserved all structural constraints while avoiding applying multitasking techniques to the partial programs.

Given the time when he postulated those techniques and the state of commercially available languages and OSs at the time, his solutions were quite remarkable. Unfortunately, his methods are not well known any more. I attribute the relative obscurity of his methods in part to the fact that he failed to introduce some kind of "algebra" with which to prove that different programs were indeed mappable to the same structure.

Program inversion is googleable,e.g.

[http://comjnl.oxfordjournals.org/cgi/content/abstract/33/2/126](http://comjnl.oxfordjournals.org/cgi/content/abstract/33/2/126)

---

### Post by mssever on 2008-12-20
> **pp. said:**
> Program inversion is googleable,e.g.

[http://comjnl.oxfordjournals.org/cgi/content/abstract/33/2/126](http://comjnl.oxfordjournals.org/cgi/content/abstract/33/2/126)
I guess I still don't understand where program inversion is useful, how it fits with modern programming techniques, and how to do it. (Nothing against the technique; I just don't have enough information.) So I'm not convinced that it's indeed a reason to add goto to languages that don't already have it.

When I said that Google's results were unhelpful, the link you gave illustrates my point. I can't glean much for an abstract, and academic papers aren't the ideal place to go for a overview of a subject; especially when the abstract is the only thing available. (Yes, I know I could see the entire article if I wanted to pony up, but why would I waste my money paying to read an article of unknown value?) All the Google results I looked at were similar in nature.

---

### Post by unutbu on 2008-12-20
Is inversion of control ([http://en.wikipedia.org/wiki/Inversion_of_Control](http://en.wikipedia.org/wiki/Inversion_of_Control)) the same thing as program inversion?

Is gtk event handling an example of program inversion?

---

### Post by pmasiar on 2008-12-20
> **pp. said:**
> Program Inversion is a scheduling technique taught by Michael Jackson in the late seventies, I believe. 

...

The methods taught by Jackson had to cope with programs dealing with data of mutually incompatible structures, so called Structure Clashes. 

I did not bother to grok fully what P.I. is, but maybe OOP and design patterns have more modern solution for the same problem (and whithout GOTO)? 

One hint might be that OOP is here to stay, while Jackson method is half-forgotten?

---

### Post by pp. on 2008-12-20
> **mssever said:**
> the link you gave illustrates my point.

Sorry; I now realise that the link is useful to people who already know the principles involved.

> **unutbu said:**
> Is inversion of control ([http://en.wikipedia.org/wiki/Inversion_of_Control](http://en.wikipedia.org/wiki/Inversion_of_Control)) the same thing as program inversion?

Not at all; it's just a chance resemblance.

> **pmasiar said:**
> I did not bother to grok fully what P.I. is, but maybe OOP and design patterns have more modern solution for the same problem (and whithout GOTO)? 

One hint might be that OOP is here to stay, while Jackson method is half-forgotten?

I don't want to start yet another method war. Still, Jackson's approach did solve a few problems which still plague OOP nowadays. It's a pity that Jackson never realised that languages like Simula and Smalltalk were much nearer to what he envisioned than the ASM and COBOL solutions he tried to push.

There are a few problems which still plague OOP. One of those is the sequence in which to send messages to an object. While the vast majority of messages can be sent at any time during the lifetime of an object, there are some messages which change the internal state of an object in such a way that some messages may become no longer applicable while others might become so. 

The methods introduced by Jackson are very well suited to address this kind of problems (among other things). Two of his works (Principles of Program Design and Principles of System Design) are worth reading even if not all parts of his solutions appear to be applicable today.

In a nutshell, the technique of Program Inversion formulated by Jackson constituted a very light weight variant of multithreading which could be implemented in practically every language then in use by judicious use of a GOTO. It was quite fascinating to observe how you could transform a well structured program into an well formed inverted program by using that much maligned verb.

From what I read, I think Occam could be very close to achieving what Jackson wanted.

---

### Post by fiddler616 on 2008-12-20
> **mbsullivan said:**
> 
PyPy, Jython, and especially Psyco seem to work well for speeding up the execution of Python code. I don't use any of them, but then again I don't use Python for scientific programs.

If I did, I'd probably use Psyco. Requires 2 lines of extra code, and you can expect a 5-10x speedup. Sweet!

Mike
Really? I'd always heard that CPython was faster than PyPy, Jython and IronPython.

I've heard good things about Psyco on these forums...although I haven't really looked into it since nothing I do is *that* speed-critical. And isn't there another one? Shed Skin or something? (My internet's too slow to warrant Googling...darn airports)

---

