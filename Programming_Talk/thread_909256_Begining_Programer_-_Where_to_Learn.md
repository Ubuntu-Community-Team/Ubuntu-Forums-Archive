---
title: "Begining Programer - Where to Learn?"
date: 2008-09-03
forum: Programming Talk
---

### Post by Bridge51 on 2008-09-03
I'm waiting for my first linux computer to arrive, and I basically I want to learn some fun programming methods. I took a computer science course in college last year, where I 'learned' emacs, and just really basic function programs (f(2) = 17, conditionals, real intro stuff). 

What I'm looking for is where can I go to learn how to write real, usable programming? Or any kind of concepts on compiling/writing programs. I'm only barely exposed to actual programming, though I have a fairly good technical background in computers. Think of me as on the 'Expert of the newbs' level of experience :-) I know a lot compared to people who know nothing :-p.

Thanks for anywhere you point me!

---

### Post by John.Michael.Kane on 2008-09-03
> **Bridge51 said:**
> I'm waiting for my first linux computer to arrive, and I basically I want to learn some fun programming methods. I took a computer science course in college last year, where I 'learned' emacs, and just really basic function programs (f(2) = 17, conditionals, real intro stuff). 

What I'm looking for is where can I go to learn how to write real, usable programming? Or any kind of concepts on compiling/writing programs. I'm only barely exposed to actual programming, though I have a fairly good technical background in computers. Think of me as on the 'Expert of the newbs' level of experience :-) I know a lot compared to people who know nothing :-p.

Thanks for anywhere you point me!

You might want to have a look in the below section. Note the Programming Talk section of the forum can be a bit heated. So be prepared for certain responses, to your questions.
[Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

Also have a look here.
[ How to start: Learning Computer Programming]("http://ubuntuforums.org/showthread.php?t=796494")

---

### Post by swoll1980 on 2008-09-03
[http://ubuntuforums.org/showthread.php?t=796494](http://ubuntuforums.org/showthread.php?t=796494)

---

### Post by Skimbleshanks on 2008-09-03
Since Python is more or less the *de-facto* native language of Linux [Wikibooks]("http://en.wikibooks.org/wiki/Python") is one place to look, also [Wikiversity]("http://en.wikiversity.org/wiki/Wikiversity:Main_Page"), and just to get you started, here's a tiny "HiLo" console program that I wrote in Python. If you feel up to the challenge, try refactoring it in Tk so that it has a GUI!
```
"""

HiLo classic guessing game
Python version by Myscha Aiken (Kittybriton)

I'm posting this in the hope that it might be helpful to anyone learning
Python. If you can already write a "Hello World" program that works,
this program will introduce the principles of test-and-branch, and looping,
two of the most important programming structures.

The user is invited to guess a single digit between 1 and 9,
enter their choice, and see how many goes it takes to get the
correct answer.

Important things to notice in this code:

The library module "random" is accessed to import a single function; randint.

The \n in print strings generates a newline in the output

The "while" <condition> : structure starts a repeating loop.
All the indented statements following the "while" statement,
will be repeated until the <condition> is true.

= assigns a value to a variable
== tests the value of a variable

"""
#-----loads the random-number generator from the library
from random import randint

print "\n\nWelcome to *Hi-Lo*, the classic guessing game\n\n"
pagain=0

#-----starts the main process loop
while pagain == 0 :

    #-----grab a random number
    psecret = randint(1,9)

    #-----ploop will act as the counter for tries
    ploop = 0

    #-----continues to loop until the user has had a reasonable
    #-----number of tries
    while ploop < 10 :
        ploop+=1
        pguess = input("Guess the number (1-9) ")
        if pguess==psecret : ploop=10
        elif pguess<psecret : print "\ntry higher"
        elif pguess>psecret : print"\ntry lower"

    #-----tell the user what the number was, user may not have guessed it!
    print "The secret number was:", psecret

    #-----offer the user a chance to play again
    pagain = input("\n\nPlay again?\nEnter 0 to continue\nAny other digit to exit ")

```

---

### Post by Oldsoldier2003 on 2008-09-03
moved from the Cafe to programming talk. Be gentle on him!

---

### Post by pmasiar on 2008-09-03
Start with Python, see stickies for (long and heated) discussion why.

Wiki in my sig has best selected links: free books, training tasks. Have fun!

---

### Post by ghostdog74 on 2008-09-03
Since you are playing with linux, you should learn shell programming.

---

### Post by LaRoza on 2008-09-03
> **ghostdog74 said:**
> Since you are playing with linux, you should learn shell programming.

The post says she's waiting for a Linux computer. Using a language that is available for many platforms would be better I think.

---

### Post by cmay on 2008-09-03
> though I have a fairly good technical background in computers. Think of me as on the 'Expert of the newbs' level of experience
whit out knowing what language you plan to use or want to use i cant help thinking that maybe you would benefit from a language that is both easy to find on most platforms and sort of a "technical" like c . which i am learning now by the way. c is used for writing drivers and kernel modules and these things. can be used as a all round language also but its not a good beginners language in many cases. but what what ever you want to do in the end i will advise you to search a lot on the internet since there many good books and tutorials and forums devoted to all kinds of things and the things you want to learn or do is bound to be out there if you look long enough. i think learning by doing is the better way always so i suggest you pick a thing you would like to do whit what ever language you want to do whit and then ask around if you run into  problems.
good luck to you. :)

---

### Post by pmasiar on 2008-09-03
OP, you don't know it yet, but answers to your question often descent to a flamewar. Why it happens was discussed in [Lessons about biases learned from language flamewars](http://ubuntuforums.org/showthread.php?t=896087) thread.

So you need to make your own mind.

For record: after Python, I recommend to learn C and more languages. Just relax, guys and gals :-)

---

### Post by LaRoza on 2008-09-03
> **pmasiar said:**
> Just relax, guys and gals :-)

What about the more ambigious people?

---

### Post by nvteighen on 2008-09-03
> **LaRoza said:**
> What about the more ambigious people?
BASIC-coders? APL-ists? The Patriarch Cult of B and BCPL? (which afterwards derived to the Sacred Cult of C) ALGOL60 users? Interlingua speakers?... COBOL-ists???

---

### Post by LaRoza on 2008-09-03
> **nvteighen said:**
> BASIC-coders? APL-ists? The Patriarch Cult of B and BCPL? (which afterwards derived to the Sacred Cult of C) ALGOL60 users? Interlingua speakers?... COBOL-ists???

[http://en.wikipedia.org/wiki/Hermaphrodites](http://en.wikipedia.org/wiki/Hermaphrodites)

I was just giving pmasiar a hard time (again) about being inclusive.

---

### Post by cmay on 2008-09-03
> You might want to have a look in the below section. Note the Programming Talk section of the forum can be a bit heated. So be prepared for certain responses, to your questions.
Programming Talk
well at least somebody did warn him :)

---

### Post by ghostdog74 on 2008-09-03
> **LaRoza said:**
>  Using a language that is available for many platforms would be better I think.
why do you think shell(bash) is not available in many platforms?

---

### Post by LaRoza on 2008-09-03
> **ghostdog74 said:**
> why do you think shell(bash) is not available in many platforms?

Perhaps I should rephrase that to "A language designed to be used on more than one platform".

Bash is a nice shell, however, it is not the most common or best suited in my experience for cross platform general purpose programming.

---

### Post by nrs on 2008-09-03
> **Skimbleshanks said:**
> Since Python is more or less the *de-facto* native language of Linux
This isn't even close to being true.

---

### Post by ghostdog74 on 2008-09-03
> **Skimbleshanks said:**
> Since Python is more or less the *de-facto* native language of Linux 
i suggest you base this statement on fact.

---

### Post by slavik on 2008-09-03
> **LaRoza said:**
> Perhaps I should rephrase that to "A language designed to be used on more than one platform".

Bash is a nice shell, however, it is not the most common or best suited in my experience for cross platform general purpose programming.
<sarcasm> you mean Java? </sarcasm> :)

---

### Post by pmasiar on 2008-09-03
> **Skimbleshanks said:**
> Since Python is more or less the *de-facto* native language of Linux 

Most utilities are programmed in C, but that's irrelevant. Python is widely considered excellent first programming language (and intro to learning more). C is excellent second language, IMHO.

---

### Post by LaRoza on 2008-09-03
> **slavik said:**
> <sarcasm> you mean Java? </sarcasm> :)

Well, as opposed to bash, yes.

---

### Post by ghostdog74 on 2008-09-03
> **LaRoza said:**
> general purpose programming.
define general purpose programming.

---

### Post by LaRoza on 2008-09-03
> **ghostdog74 said:**
> define general purpose programming.

Programming for a wide variety of tasks, ranging from simple text processing to complex GUI programs and 3d games.

---

### Post by ghostdog74 on 2008-09-03
> **LaRoza said:**
> Programming for a wide variety of tasks, ranging from simple text processing 

A lot of other languages can do these. 

> 
to complex GUI programs and 3d games.
doesn't look general purpose to me. More like specific purpose.

---

### Post by LaRoza on 2008-09-03
> **ghostdog74 said:**
> A lot of other languages can do these. 


doesn't look general purpose to me. More like specific purpose.

I seem to have to spell out everything. "from...to..." means a range. So it is inclusive.

---

### Post by pmasiar on 2008-09-03
> **ghostdog74 said:**
> define general purpose programming.

bash or awk are NOT general-purpose languages, as compared to Python or Ruby, which are. absh/awk are decent in what they do (admin's tasks), but they are not general-purpose.

EDIT: and you know it but making us hard time anyway :-(

---

### Post by CptPicard on 2008-09-03
> **ghostdog74 said:**
> define general purpose programming.

Piping unstructured externally-semantic text between various complex tools with totally different usage isn't it...

---

### Post by ghostdog74 on 2008-09-03
> **pmasiar said:**
> bash or awk are NOT general-purpose languages, as compared to Python or Ruby, which are. absh/awk are decent in what they do (admin's tasks), but they are not general-purpose.

how are they not general purpose? name an example.

> 
EDIT: and you know it but making us hard time anyway :-(
Its not hard at all, you just have to ignore my post because they are for the OP , not you :) Besides, what's the fun in a discussion if there are no opposing views?

---

### Post by ghostdog74 on 2008-09-03
> **CptPicard said:**
> Piping unstructured externally-semantic text between various complex tools with totally different usage isn't it...

for example ?

---

### Post by CptPicard on 2008-09-04
> **ghostdog74 said:**
> for example ?

For example almost *anything*... shell has its place, but you're being totally absurd in suggesting the shell is a viable general-purpose programming environment... almost as bad as Lster suggesting it should all be in assembler.

---

### Post by slavik on 2008-09-04
OP has his answer and I see where this is going ...

thread closed.

OP, if you feel your question wasn't answered, PM me.

---

### Post by LaRoza on 2008-09-04
> **slavik said:**
> OP has his answer and I see where this is going ...

Solved threads aren't closed, but marked solved (usually by the OP).

If it is a recurring discussion, then it is moved to Recurring Discussions.

---

