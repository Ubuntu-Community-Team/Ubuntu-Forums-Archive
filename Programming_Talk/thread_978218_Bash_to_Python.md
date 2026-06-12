---
title: "Bash to Python"
date: 2008-11-10
forum: Programming Talk
---

### Post by Pro-reason on 2008-11-10
Does anyone have any tips for converting Bash scripts to Python?

To my mind, it should even be theoretically possible to automate the conversion.

---

### Post by jimi_hendrix on 2008-11-10
> **Pro-reason said:**
> Does anyone have any tips for converting Bash scripts to Python?

To my mind, it should even be theoretically possible to automate the conversion.

anything is possible if you can think it...but anyway ya it probably can be done...if you know string parsing really well

---

### Post by Greyed on 2008-11-10
In theory it is possible to convert any Turing complete language into any other Turing complete language.

It really isn't possible nor is it desirable.  The methods that bash uses to do things don't map well to Python.  However doing so would not make it a Python script as it would not use things in a Pythonic manner.

As for manual conversion that's simple.  Take what the Bash script is doing and do that in Python.  Don't port the methods of achieving the results, port the results.

A good example would be complex logic in bash that uses recursion to walk a directory tree.  Bash has nothing similar to os.walk() (or the older, os.path.walk()) in Python.  So instead of reimplementing the logic of the directory walk you'd reimplement the desired results using os.walk() as the mechanism.

---

### Post by snova on 2008-11-10
I think you could.

Well, since Bash scripts are mostly just sequences of commands, I imagine most of them would be replaced with calls to a subprocess module. Builtins would have to be replaced with Python equivalents.

As to actually doing it, that would be tricky. In Bash, there is no difference between normal variables and environment variables. Python code would have to figure out which is which, and the answer may not always be obvious.

In addition, shell syntax is not the most easily parsed thing... (To be pronounced "par-sed". :))

Optimizing it to replace things done in Bash that can be done more easily in Python would be quite difficult, involving all kinds of things way past me...

---

### Post by Pro-reason on 2008-11-10
> **Greyed said:**
> 

It really isn't possible nor is it desirable.  The methods that bash uses to do things don't map well to Python.  However doing so would not make it a Python script as it would not use things in a Pythonic manner.

As for manual conversion that's simple.  Take what the Bash script is doing and do that in Python.  Don't port the methods of achieving the results, port the results.


Well, *duh*.  ;)  Of course the best thing to do is to port the result.  The point is that I don't know how.  I am well-versed in bash scripting, but I want to get a programming job.  So, I plan to teach myself Python, and then stuff like Java and C.  I reckoned that a good way of learning the basics of Python would be to rewrite my shell scripts.  

So, I've changed “function” to “def”, “echo” to “print”, and suchlike.  I'm looking for some sort of beginners' guide to Python for people who know bash but not other programming languages.

I also mentioned offhand that it would be cool if the conversion could be done automatically.  Then I could examine the resultant code, and immediately understand it because it would still be my program.  That's just a dream, though.

---

### Post by Greyed on 2008-11-11
> **Pro-reason said:**
> Well, *duh*.  ;)  Of course the best thing to do is to port the result.

I didn't mean it to be snarky.  I was being quite serious.  A common mistake people make after learning one language but before learning another (and this goes for natural languages as well as programming languages) is to think in their first language and try to translate that verbatim into the second language.  The problem is that not everything is a 1:1 translation which is why one should focus on the results, the intent, and not the steps to which that result was achieved. Believe you me, if I had someone tell me that when I was still on my first or second language I would have done a whole lot better.  :D 

> So, I've changed “function” to “def”, “echo” to “print”, and suchlike.  I'm looking for some sort of beginners' guide to Python for people who know bash but not other programming languages.Can't help you there.  My extend of bash is to know enough to get the general idea of what it does and rewrite that in Perl or Python.  I'd say focus less on trying to come at it from a bash perspective and just learn the language.  To be honest you've already grasped the hardest part for lots of people; the shebang.  ;)

Go through the Python tutorial in the official docs.  Also just leave an interpreter open in one window.  Use it to solidify the basic concepts in your head.  In that manner learning bash and Python are not much different since you can play interactively with both of them.

---

### Post by LaRoza on 2008-11-11
> **Pro-reason said:**
> Does anyone have any tips for converting Bash scripts to Python?

To my mind, it should even be theoretically possible to automate the conversion.

Yes, rewrite the logic in Python. Bash scripts are usually short, and depending on the task, it may string together several programs with pipes. This leads to very short bash programs, which take more lines in Python.

Also, the simplest way, would be to use just put the bash script in Python using os.system(), but that is really silly.

---

### Post by Pro-reason on 2008-11-11
> **LaRoza said:**
> Also, the simplest way, would be to use just put the bash script in Python using os.system(), but that is really silly.

Perhaps I could embed each Bash function in Python like that, and change each one to real Python as I learn the language.  I'm anxious to have something that works straight away.  I can optimise it later, as part of an on-going learning process.

One thing I currently do is run a command (e.g. gzip) and then have an *if ... do ... fi* which does one thing or another depending on the exit status of the command.  How would I do that?  (I'm not interested, at this stage, in whether this is the approved way of doing things.)

---

### Post by Pro-reason on 2008-11-11
> **Greyed said:**
> I didn't mean it to be snarky.  I was being quite serious.  A common mistake people make after learning one language but before learning another (and this goes for natural languages as well as programming languages) is to think in their first language and try to translate that verbatim into the second language.  The problem is that not everything is a 1:1 translation which is why one should focus on the results, the intent, and not the steps to which that result was achieved. Believe you me, if I had someone tell me that when I was still on my first or second language I would have done a whole lot better.  :D 
I'm a professional translator and language tutor, so you don't need to lecture me about that sort of thing.  ;-)

I know from long experience how my own brain works when learning, and I know that a crude, 1-1 translation of my script into Python would aid me in comprehending how to do equivalent things in the new language.  Later on, I can develop more elegant expressions of the possibilities of the language.

---

### Post by CptPicard on 2008-11-11
Sorry, but really, "ure doin it rong"... :)

What you are planning will just waste a humongous amount of time trying to hack Python into doing something that it is not suited for, that is, verbatim copies of bash scripts.

> **Pro-reason said:**
> I reckoned that a good way of learning the basics of Python would be to rewrite my shell scripts.

The only way to really properly replace bash as a system scripting language is to write Python, not bash in Python. I can't even begin to think how nasty it will be to run shell tools as subprocesses and manage the pipes under Python and do the parsing and sticking Python data structures somehow there in the middle... you are so much better off having your data as genuine Python data structures all along and calling into appropriate modules instead of shell tools.

Python isn't that hard and is actually a very discoverable language once you get the basics, and your plan actually expects you to be a very skilled Python hacker to begin with so that you can pull of this kind of a duct tape hackery approach.

> 
So, I've changed “function” to “def”, “echo” to “print”, and suchlike.  I'm looking for some sort of beginners' guide to Python for people who know bash but not other programming languages.

That is going to result in awful Python :)

For people who know bash... well... basic ideas of programming have already been learned, so learning those other languages from scratch is the fastest way to get to grips with them.

> 
I also mentioned offhand that it would be cool if the conversion could be done automatically.  Then I could examine the resultant code, and immediately understand it because it would still be my program.

Even if there was such a conversion, the converter would not understand your meaning, and the result would be horrible. I bet you couldn't understand it simply by virtue of it being your program, and it would help you in grokking Python all the less (which you by definition wouldn't understand)...


> **Greyed said:**
>  A common mistake people make after learning one language but before learning another (and this goes for natural languages as well as programming languages) is to think in their first language and try to translate that verbatim into the second language.

+1, and this ties in well with the general arguments we have about differences about languages... the claim that it's just skin deep syntax is just simply plain false regardless of the theoretical basis for having a translator between languages...

> **Pro-reason said:**
>  I'm anxious to have something that works straight away.  I can optimise it later, as part of an on-going learning process.

So if you want something that actually works straight away, write Python. This "optimization" could not be done piecemeal, it would have to mean a complete rewrite to have your data not in pipes between processes but actually in Python.

---

### Post by pmasiar on 2008-11-11
> **Pro-reason said:**
> Well, *duh*.  ;)  Of course the best thing to do is to port the result.  The point is that I don't know how.  I am well-versed in bash scripting, but I want to get a programming job.  So, I plan to teach myself Python,

You are asking wrong question, no wonder that the answers do not make any sense.

From your question any reasonable reader (and I completely agree with Greyed) would assume you are after generic way to translate any bash script to Python. Which would be waste of time, because python is higher-level language with many cool concepts making programming in it more productive: your bash-code would very bad (and tricky-hard to debug as CptPicard mentioned) Python code.

Why? because you are working "against the grain". You are doing something you are not supposed to do. Python has rule "there should be one obvious way to do it right". Your's way is not obvious, and so wrong.

Asking right question is half the answer. And your question should be: how a person competent in bash can learn Python quickly? See? 8-)

If you understand basic programming concepts, you can learn basic procedural Python over a weekend, OOP will take you more but you don't need it to be productive - you can safely program for a year by just using existing objects (from library) and arrays of dictionaries for your own "objects".

See wiki in my sig for links, books and training tasks.

And you also should really adjust your attitude: if people's answers do not make sense to you, your question does not make sense to them, and it is **your** fault. Nobody owes you anything, volunteers spend own free time to help you. If I spend minutes to write answer for you,  it is done in gratitude for people who helped me to learn what I know now, it is not related to you personally in any way. It is easier to ignore a jerk than trying to teach him how to behave.

Read "How to ask questions" in my sig, and apologize to Greyed.

**Edit:** I am **not** saying that Pro-reason is a jerk. He cannot be, with such nick ;-)  and I am **not** ignoring him, but trying to answer his question. But I **do** think Pro-reason  should readjust his attitude. Even if he is expert translator, learning different programming language is more about learning different paradigms than just mechanically translating syntax of one language into another.

---

### Post by CptPicard on 2008-11-11
Now, now... I don't think he is being a jerk, just misguided ;)

---

### Post by gomputor on 2008-11-11
> **pmasiar said:**
> Read "How to ask questions" in my sig, and apologize to Greyed.

Hahahaaaaa.......!!!!

---

### Post by Pro-reason on 2008-11-11
OK, since you're determined to be unhelpful, I give up.

---

### Post by CptPicard on 2008-11-11
No, we're not unhelpful, we're just telling you you really are going about it the wrong way. We're professional programmers, no less.. :)

And the really quick answer truly is that no, there is no such thing as an automatic bash to Python converter. It's probably even theoretically impossible, given the variety of tools you may be calling from your bash script. And trying to use such a hypothetical tool would be much more of an effort than actually learning Python.

---

### Post by Pro-reason on 2008-11-11
No, you are unhelpful.  Being l33t programmers is a handicap here.  It makes you pontificate about the purest purist way of doing things, instead of just answering the question.

---

### Post by skillllllz on 2008-11-11
Nothing ever got accomplished by giving up.

This book is free and WILL help you in your endeavor:

[A Byte of Python (Online version)]("http://www.ibiblio.org/g2swap/byteofpython/read/")

[Downloadable PDF]("http://www.ibiblio.org/swaroopch/byteofpython/files/120/byteofpython_120.pdf")


I wish you luck, even though you won't need it. :)

---

### Post by CptPicard on 2008-11-11
> **Pro-reason said:**
> No, you are unhelpful.

No, we actually help you help yourself and stop wasting your time on a dead end solution.

> Being l33t programmers is a handicap here.

What you are suggesting qualifies much better as a l33t solution -- "look!! I'm actually hacking Python to act as bash in between of subprocesses!!". We're being very pragmatic here.

> 
  It makes you pontificate about the purest purist way of doing things, 

No, it is the realist way of doing things.

> instead of just answering the question.

Your question has been answered.

---

### Post by LaRoza on 2008-11-11
> **Pro-reason said:**
> No, you are unhelpful.  Being l33t programmers is a handicap here.  It makes you pontificate about the purest purist way of doing things, instead of just answering the question.

The question is hard to answer.

If it is just bash, not calling other programs, it would be very simple to automate a translation.

However, bash scripts call other programs all the time. Bash scripts are more like glue between other programs.

One could, I suppose, have something that can automatically translate bash into Python, but the shear number of programs that Bash scripts routinely call, it would be quite hard.

---

### Post by snova on 2008-11-11
However much I agree that conversion is the wrong way to go about learning Python, I do think it *could* be done. It would mean using subprocess a lot, and writing Python equivalents to Bash builtins, but besides that I think the biggest challenge would be the parser.

I am by no means a theorist, but practically, I think it could be done.

---

### Post by Pro-reason on 2008-11-11
> **snova said:**
> However much I agree that conversion is the wrong way to go about learning Python, I do think it *could* be done. It would mean using subprocess a lot, and writing Python equivalents to Bash builtins, but besides that I think the biggest challenge would be the parser.

I am by no means a theorist, but practically, I think it could be done.

OK.  Thanks for not preaching like the others!  Any ideas as to how it could be done?

I gave an example before.  How can I, in Python, do the equivalent of the following:

```

gunzip "$file"
if [ $? == 0 ]; then
    echo "Yay!  That worked."
else 
    echo "Oops, I didn't manage to uncompress that."
fi

```

That is to say, how can I check the exit status of an external command?

It might also be helpful to learn a more Pythonic way of manipulating the file, but I still want to know how to do it in this way.  Dogma about "one obvious way" is of no interest to me.

---

### Post by CptPicard on 2008-11-11
Of course converting the basic bash builtins would be the trivial part, and the converter would never be worth the "learning experience"... but the problem is that most of bash scripts consist of pipes putting together outside processes... so managing that would be the hard part, and it would go beyond any learning exercise...

---

### Post by snova on 2008-11-11
> **Pro-reason said:**
> OK.  Thanks for not preaching like the others!  Any ideas as to how it could be done?

Did I come across that way? Sorry to say, that was an accident. I was musing on the possibilities of a converter, but I agree with everybody else that it would be useless and detrimental to your Python experience.

> **Pro-reason said:**
> I gave an example before.  How can I, in Python, do the equivalent of the following:

```

gunzip "$file"
if [ $? == 0 ]; then
    echo "Yay!  That worked."
else 
    echo "Oops, I didn't manage to uncompress that."
fi

```

That is to say, how can I check the exit status of an external command?

It might also be helpful to learn a more Pythonic way of manipulating the file, but I still want to know how to do it in this way.  Dogma about "one obvious way" is of no interest to me.

Hmm... The Python way would be to use the compression module for Gzip, and catch any exceptions. Quite simple.

The Bash-to-Python way would be to start gunzip in a subprocess, wait for completion, and grab the return code. Then check it's equivalency to 0 and print the appropriate message. Not nearly as pretty.

---

### Post by Pro-reason on 2008-11-11
> **snova said:**
> 
Hmm... The Python way would be to use the compression module for Gzip, and catch any exceptions. Quite simple.

The Bash-to-Python way would be to start gunzip in a subprocess, wait for completion, and grab the return code. Then check it's equivalency to 0 and print the appropriate message. Not nearly as pretty.

I was asking for the actual code.  That's why I made the example so simple.

---

### Post by CptPicard on 2008-11-11
The problem is that the example is not simple. In particular, it forces you to learn, simply within this supposedly "simple" example, a lot of Python stuff that is way beyond the beginner stuff you need to begin with!

---

### Post by snova on 2008-11-11
> **Pro-reason said:**
> I was asking for the actual code.  That's why I made the example so simple.

I haven't a clue how to use the decompression modules, nor do I recall usage of the subprocess interface. By the looks of it, you'd be interested in the 'gzip' module, though, for this particular example...

---

### Post by CptPicard on 2008-11-11
> **snova said:**
> By the looks of it, you'd be interested in the 'gzip' module, though, for this particular example...

No he's not... he wants to run gzip as the subprocess and catch the exit code and then maybe handle the unzipped data from pipe.

Interesting, is it not, that even experienced Python hackers can't really just readily produce the "simple" code required, but would rather refer to something more Pythonic.. ;)

---

### Post by Greyed on 2008-11-11
> **CptPicard said:**
> Interesting, is it not, that even experienced Python hackers can't really just readily produce the "simple" code required, but would rather refer to something more Pythonic.. ;)

At least in my case it is because I prefer to do as much in Python as possible.  I've written in an environment where fork/exec calls could make or break the run time of a script.  As such my os.system() and Popen fu are weak.

> **Pro-reason said:**
> I was asking for the actual code.  That's why I made the example so simple.

Simple... in Bash.  Which is what we've been getting at.

Here's an untested, off the cuff direct translation:
[php]
import os
result = os.system("gunzip somefile")
if not result:
    print("Yay!")
else:
    print("boo!")
[/php]But here's how it probably should be done.  Again, untested.
[php]
import gzip
def gunzip(file='', unfile=''):
    infile = gzip.open(file)
    outfile = open(unfile, "wb")
    while 1:
        data = infile.read(8192)
        if data:
            outfile.write(data)
        else:
            break

try:
    gunzip('somefile', 'uncompressed')
except:
    print('Fail!')
[/php]Takes a lot more, granted.  But there is no fork/exec and your dealing with the gzip directly.  If, for example, it were a log you wanted to parse the entire while loop could be changed to use readline() instead of read() and you can act on those lines directly.

Like I said though, that's just a rough, untested, off-the-cuff example.  I rarely use os.system() or any of the Popen variants.  Any time I do I have to repeat the test/revise cycle a few times to get it to stick in my mind again.  I've used the gzip module I think once ever...  Wait, no, it was the tar module I was using as I was trying to recover a tgz corrupted in a HD crash.

---

### Post by Pro-reason on 2008-11-12
> **Greyed said:**
> 
[php]
import os
result = os.system('gunzip somefile")
if result:
    print("Yay!")
else:
    print("boo!")
[/php]


The "Yay!" and the "boo" are the wrong way round, and you mistyped a quotation mark, but otherwise that works just fine.  Thanks.  I really don't know why it took everyone three pages just to give me this snippet of code.

Now I'll try the long way.

---

### Post by Greyed on 2008-11-12
Ah, right, shell has 0 as "all's good", positive integers as informational and negatives as errors.  Just confirms what I said about not using system calls all that often.  ;)

---

### Post by ghostdog74 on 2008-11-12
> **Pro-reason said:**
> .  I really don't know why it took everyone three pages just to give me this snippet of code.



that's because your question is misleading, at least to me. I thought you are talking about converting bash code to Python code. anyway, If you are looking into a "bash to Python code converter", yes, there's a way, its called a "human being". Otherwise, for the example, just use the gzip module Greyed has shown you. No need to call the shell's gzip tool.

---

### Post by CptPicard on 2008-11-12
> **Pro-reason said:**
> I really don't know why it took everyone three pages just to give me this snippet of code.


I really don't understand what exactly it is that you're learning from this and the bash original that you could not have learned much faster by quickly reading through the very first chapters of any Python tutorial that covers variable assignment, function call and the if statement... the os module is totally irrelevant to that.

---

### Post by Pro-reason on 2008-11-12
> **CptPicard said:**
> I really don't understand what exactly it is that you're learning from this and the bash original that you could not have learned much faster by quickly reading through the very first chapters of any Python tutorial that covers variable assignment, function call and the if statement... the os module is totally irrelevant to that.
You don't need to understand.  You need only answer my question, or remain silent.

Pontificating, and thanking people for agreeing with you, seems to be more fun for you, however.

---

### Post by CptPicard on 2008-11-12
I do not need your permission to speak up, and you are not entitled to anything here. In particular, you are not entitled to having people help you in exactly the ways you expect and demand, especially when those ways seem detrimental to the general goal of advancing your understanding of Python as fast as possible.

This forum is full of people trying to learn programming and often going about it the wrong way. It is much more beneficial to point them in the right directions so that they go with the flow instead of against it. It would be a complete waste of both my and their time if I allowed myself to be "used" in this sense where I'm not allowed to suggest a more efficient approach and instead were made to, bit by bit, just answer specific (misguided, incomplete) questions while the big picture is being ignored.

---

### Post by Flimm on 2008-11-12
> **Pro-reason said:**
> The "Yay!" and the "boo" are the wrong way round, and you mistyped a quotation mark, but otherwise that works just fine.  Thanks.  I really don't know why it took everyone three pages just to give me this snippet of code.Actually, it only took 5 hours or half page for someone to give you this code. You didn't ask someone for to convert the specific bash script you posted to python until the third page.
Let's remember what [your original question](http://ubuntuforums.org/showpost.php?p=6149052&postcount=1) was:
[QUOTE=Pro-reason]Does anyone have any tips for converting Bash scripts to Python?

To my mind, it should even be theoretically possible to automate the conversion.[/QUOTE]

---

### Post by Rocket2DMn on 2008-11-12
This thread has clearly degraded into bashing (no pun intended).  Thread closed.

---

