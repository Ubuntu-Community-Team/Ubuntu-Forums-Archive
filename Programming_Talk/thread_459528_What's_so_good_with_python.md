---
title: "What's so good with python?"
date: 2007-05-30
forum: Programming Talk
---

### Post by malfist on 2007-05-30
I've been looking through this forum for a while and I see python this, python that. Python's great/sweet/awsome/w00t, and I've been wondering about it.
I've been programming for several years now and Java is my home language, I love it. What is so special about Python, I've never programmed in it before (nor in C or Ruby), when I can, I do things in Java but I've learned CSS, PHP, SQL, VB .NET, and am learning C#.

What's so special about python, what I've read (which is very little) is the python is just a fancy way to do bash scripts.

Anyone care to enlighten me?

---

### Post by seamless on 2007-05-30
It can be a fancy way to do bash scripts but it can also do a lot more. It has support for OOP programming and is a very simple language. In many situations (especially learning to program) it is a very good choice. That's certainly not to say it is the be all to end all of languages. However the main reason it gets such high praise is that it is easy. Easy to learn, and easy to work with. The syntax is very well thought out and it removes a lot of &#8220;filler&#8221; code like { and }. Also it has a lot of library support. It's trivial to wrap a C/C++ library to work with Python and in many cases that's not even needed because there is usually a Python module to do what you are looking for.

It's a clear, simple, versatile language with well thought out syntax and has a myriad of libraries that makes it so appealing.

---

### Post by wizardofyendor on 2007-05-30
I've always perfered perl to python, I just find it easier, I think it's what you learn first you like better...

---

### Post by Mirrorball on 2007-05-30
Python is easier to use than C/C++/C#/Java. Think a cleaner PHP and suitable for much more than fancy bash scripts. Most Ubuntu applications (for instance, the installer) were written in Python.

---

### Post by ghostdog74 on 2007-05-30
> **malfist said:**
> I've been looking through this forum for a while and I see python this, python that. Python's great/sweet/awsome/w00t, and I've been wondering about it.
I've been programming for several years now and Java is my home language, I love it. What is so special about Python, I've never programmed in it before (nor in C or Ruby), when I can, I do things in Java but I've learned CSS, PHP, SQL, VB .NET, and am learning C#.

What's so special about python, what I've read (which is very little) is the python is just a fancy way to do bash scripts.

Anyone care to enlighten me?
this question has been asked umpteen times. Why don't you start using it and see for yourself. Start by taking the tutorial by the creator of Python himself, (or any other Python resources, its in the sticky) What other ppl say including myself, doesn't matter at all. In the end, its just your choice. As for my choice, i have chosen to write 
```

#!/usr/bin/python
print "hello world"

```
rather than this:
```

class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}
```
And, yes, that's my choice.

---

### Post by pmasiar on 2007-05-30
Python can do *much more* than just fancy bash script.

All languages are concerned about explaining what needs to be done to a very stupid listener (a computer).
Python is the only pragmatic and usefull language I am aware of what has as a design goal to be readable and understandable by humans first, and computer only as second. Where compilers bends backwards to accomodate humans, not the opposite as other languages. Interestingly, you can keep almost all expresive power of Perl, having none of readability problems of it.

Dynamic typing simplifies programming substantially. Java helps to avoid "spaghetti code", but we have "ravioli code" instead: hundreds of bite-size objects, and you need to "bite" and learn each one to use it properly.

Dynamic exceptions (instead of Java's static checked exceptions)  also allows to handle problems where it makes sense (or ignore them for prototype) and avoid many lines of boilerplate code.

Python has many, many subtle improvements which Java programmer might be not aware (because she learned to live without them), but are so annoying when going from Python to Java. As saying goes, Python is object-oriented; Java is Object-obsessed :-) Ie. It is easy to return multiple objects from Python function (and assign them), in Java you need to create object.

```

def fun1(par1, par2="val1"):
    # par2 has default value if omitted: Java requires 2 definitions
    return par1, par2 # par1 is int, par2 is string

i1, s1 = fun1(5)  # assigning 2 values

```

Operator overloading allows you to create intuitive objects which "just work". 

Ahh, so many little details. Just try it. :-)

---

### Post by TreeFinger on 2007-05-31
If you are interested in Python I would check out [this site]("http://www.dickbaldwin.com/toc.htm"). The creator, Richard Baldwin, has a great way of teaching the language. He says through out the tutorial that he is mainly into java and the way he goes about teaching Python is for someone to use it with Java.

I have just started programming so don't put me down on anything.

---

### Post by AZzKikR on 2007-05-31
I am school, work and homebrewn Java guy too. I've been into Pythoning myself since I read that Python is a primary language used in Ubuntu. I'd like to commit something to the Ubuntu community using Python one day, so that's why I am learning the language.

There is some truth in what pmasiar said: Python is object oriented, and Java is object-obsessed. I love Java, really. But I also begin to love Python for it's simplicity. 

If I am going to write something for Linux, I want it to be easily installed and executed without too much hassle. Since Python is already included with a standard Ubuntu distribution, I would prefer that. But Java will always be my primary, most used language (because of my job etc.).

Start doing the tutorial, and you'll see how easy and w00t it can be :)

---

### Post by AnRa on 2007-05-31
Python is a multi-paradigm programming language :)

---

### Post by kknd on 2007-05-31
Python has many good things borrowed from functional languages, and is more simple than other languages! I like it,  but I still preffer Java =)

---

### Post by ankursethi on 2007-05-31
With Python you can -
1. Write fancy bash-like scripts
2. Write fancier text processing systems (like you can do in Perl)
3. Write desktop applications
4. Write simple games using SDL
5. Write web based AJAX apps
6. Crunch insanely large numbers
7. "glue" applications together
8. Write quick and dirty prototype apps and then later translate them into C/C++/Java

Therefore it is a multi-paradigm language. But Python lacks in terms of speed of execution. This is where Java and C# beat it. I hope the dev team does something to improve execution time in v3.0 (also called Python 3000).

---

### Post by ghostdog74 on 2007-05-31
> **ankursethi said:**
> 
But Python lacks in terms of speed of execution. 
where did you get this information? pls substantiate it.

---

### Post by seamless on 2007-05-31
Computer Language Benchmarks Game went though and benchmarked a number of languages. [C vs Python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=python&lang2=gcc") Shows that Python is actually very slow. [Here]("http://furryland.org/~mikec/bench/") is another set of benchmarks with full source code right there so you can try it yourself. Conclusion, Python is slow.

Also tools like [Psyco exist]("http://www.ibm.com/developerworks/library/l-psyco.html") in order to increase Python performance in order to bring it closer to C.

---

### Post by ankursethi on 2007-05-31
Well, I use Frostwire, which is written in Java, as a Gnutella client. It's slow, as interpreted/VM-based apps generally are, but only at startup. After that it works okay. I've also used Eclipse.

I also use the Deluge bittorrent client as my default torrent client. Now deluge is very simple and quite minimalistic. It's simpler than Frostwire. At startup I feel no real speed loss, but at runtime there is a slight lag, which, considering Deluge's size, shouldn't really be there. Same goes for Eclipse vs SPE.

Now don't get me wrong here. Python is my favorite language. I'm just telling what I've seen during regular use of Python apps.

---

### Post by pmasiar on 2007-05-31
> **ankursethi said:**
> But Python lacks in terms of speed of execution. This is where Java and C# beat it. 

Properly designed Python code can beat any C#/Java code. How? Don't forget that Python is the glue for C libraries calls. Design your app in Python, find bottleneck 5% of code, reimplement it as C library, link with Python. So you have 95% of C speed in execution, and 95% of Python speed in development.

[PyPy project](http://en.wikipedia.org/wiki/Pypy) is another interesting approach: They developed RPython: subset of Python which is compiled to C.

Edit: I should say "Python-based application" instead of "Python code".

---

### Post by ghostdog74 on 2007-05-31
> **seamless said:**
>  C vs Python Shows that Python is actually very slow. 
wait, you are comparing C against Python?are you sure? 

> 
[Here]("http://furryland.org/~mikec/bench/") is another set of benchmarks with full source code right there so you can try it yourself. 
that's old stuff. what version is Python now?

> 
Conclusion, Python is slow.

Invalid.

---

### Post by seamless on 2007-05-31
> **"pmasiar"]Properly designed Python code can beat any C#/Java code. How? Don't forget that Python is the glue for C libraries calls. Design your app in Python, find bottleneck 5% of code, reimplement it as C library, link with Python. So you have 95% of C speed in execution, and 95% of Python speed in development.[/QUOTE]
You can do the exact same thing with C# and Java. C# has PInvoke to allow for this and Java has JNI. GTK# and SWT are both binding to the native GTK C libraries. Also, Java unlike Python has a hotspot compiler built into the runtime which will give it an additional performance edge in some instances.

In the case of calling C libraries you are no longer looking at the execution time of the language in question. The fact of the matter still remains that Python is slower than C#, Java, C and C++. Due to its design this is true and is one of the reasons it is such a powerful language. Being able to give it raw code and have it execute without compilation is a huge benefit especially in development. 

Python being slow is also a non issue. Like so many interpreted languages and as pmasiar said it can easily call C libraries when needed. Also, in most instances the decrease in execution speed is not an issue because in the case of a desktop application, 99% of the time the application is waiting for user input. Only in a few instances (kernel module) would a faster language be required.

[QUOTE=ghostdog74 said:**
> wait, you are comparing C against Python?are you sure? 


that's old stuff. what version is Python now?


Invalid.
So you're telling me that a string parsed language running on top of a C application that has to translate human readable text into machine code on the fly is faster than a binary that is already in machine code... And you say my conclusions are invalid... Also that's why I included one with full source. Go run the benchmarks youself and provide real number instead of making uneducated assumptions, you are the one who wanted substantiation. If you really feel that Python is so much faster run the tests yourself.

---

### Post by AdamG on 2007-05-31
Geez. 

Python is an interpreted language, and thus is slower than compiled languages. No surprise there. 

But frankly, execution speed, in the vast majority of cases, *doesn't matter*. The important thing is that Python is *fast enough* for today's computers. It is pretty much as fast as an interpreted language can get, which is still a lot slower than most compiled languages. 

I have never run into a circumstance where Python was my bottleneck. I've done Web, desktop and network programming. On web and network programming, the network latency is your bottleneck. For desktop programming, as long as the delay isn't noticable (and with Python, it isn't) the user can't tell the difference between a window taking five thousandths and fifty thousandths of a second to show up. 

And if Python ever *had* been my bottlneck, I could have reached for Psyco, then Pyrex, then CTypes, in that order. 

Simply put, execution speed is not today's bottleneck. Today's bottleneck is the programmer; our productivity and our ability to turn logic into code is the challenge for today's language. Python does this extremely well. The code is well known for being nearly pseudocode-clear. 

I can think of what I want to do, and then write it, in an idiomatic, well-fitting, not-awkward fashion, in Python. I can't say the same about Java... that's the basic reason I turn to Python rather than Java to Get Things Done.

---

### Post by ghostdog74 on 2007-05-31
> **seamless said:**
> 
So you're telling me that a string parsed language running on top of a C application that has to translate human readable text into machine code on the fly is faster than a binary that is already in machine code... 

i am sorry that you don't get me. It is quite understood by people with fair bit of knowledge that programs compiled to executables with C/C++ are undeniably faster than interpreted languages. Its just that i don't know why,in that sense, that you even want to compare C with Python.

> 
And you say my conclusions are invalid... 

I said its invalid, because all the while in your [post]("http://ubuntuforums.org/showpost.php?p=2754819&postcount=13"), there's no mention of any other languages except C. I take it, then, that your conclusions are only based on C vs Python, and nothing else.

> 
Also that's why I included one with full source. Go run the benchmarks youself and provide real number instead of making uneducated assumptions, you are the one who wanted substantiation. If you really feel that Python is so much faster run the tests yourself.
Also, let me reiterate, that site you gave is old. As for the shootout page, i don't know whether to believe it or not (since that site to me, is just for fun), however assuming they are true, there are some areas Python is good for speed, and some are not. Some areas it performs well. so the question i wanna ask you  about your conclusion is, Python is  slower in what sense?

---

### Post by pmasiar on 2007-05-31
So we all basically agree that Python is *the* kick-a$$ language for basically everything except kernel hacking, and fast enough :-)

For me and my boss, the most important speed in our computer apps is *speed to the market*.

Bonus link: [presentation from BlackHat Europe, 2006](http://www.larsen-b.com/Article/222.html) where python was used by black-hat hackers to break into many, many layers of protection of Skype. See also tools at last slide: looks like most of them are in Python. 

So among other usage (Google, NASA, Light and Magic, etc) , Python is the language blackhat hackers use to Get Things Done :-) - and they might know a thing or two about productivity and fast coding :-)

---

### Post by aks44 on 2007-05-31
> **pmasiar said:**
> For me and my boss, the most important speed in our computer apps is *speed to the market*.
Surely we don't work in the same field...
As far as my customers are concerned, a mix of C++ (for it's flexibility and rather acceptable speed) and of raw hand-coded Asm (for some very CPU intensive functions) is the way to go. Raw performance really matters.

Oh, did someone mention GUI apps? Sorry, I only know how to write servers... (but I'm slowly filling that gap)

Different needs, different tools. ;)

---

### Post by pmasiar on 2007-05-31
Hand coded Asm? A rare bird indeed. Less than 1% of applications need that kind of speed, I guess. I am not saying that it is not used - possibly I might be using it right now, but I believe than less than 1% of developers have to work with such harsh constraints, and for rest of us, native (uncompiled) Python speed is good enough :-)

My apps wait for web server and database most of the time and no amount of Asm will make them any faster.

Just curious, what kind of industry requires such kind of  speed?

---

### Post by daxumaming on 2007-05-31
Here's the thing, sometimes Java is slower than Phyton... and sometimes, Phyton is slower than Java... Conclusion: it's in the code!

Going back to the topic, speed of development. Look at ghostdog74's hello world code.. Applications are developed way faster as compared to any language. And I also love Phyton's scalability and flexibility.

---

### Post by seamless on 2007-05-31
> **ghostdog74 said:**
> i am sorry that you don't get me. It is quite understood by people with fair bit of knowledge that programs compiled to executables with C/C++ are undeniably faster than interpreted languages. Its just that i don't know why,in that sense, that you even want to compare C with Python.
To show exactly how slow it actually is using a known baseline.

> **ghostdog74 said:**
> I said its invalid, because all the while in your [post]("http://ubuntuforums.org/showpost.php?p=2754819&postcount=13"), there's no mention of any other languages except C. I take it, then, that your conclusions are only based on C vs Python, and nothing else.
Again to show a known baseline as a reference of comparison. Most people know how fast a C application executes hence why it was used for comparison.

> **ghostdog74 said:**
> Also, let me reiterate, that site you gave is old. As for the shootout page, i don't know whether to believe it or not (since that site to me, is just for fun), however assuming they are true, there are some areas Python is good for speed, and some are not. Some areas it performs well. so the question i wanna ask you  about your conclusion is, Python is  slower in what sense?
In the sense of execution speed which is what the second link shows as compared to other langauges mentioned. Programs are created using a variety of patterns and Python runs slower than any of the listed languages in almost every case. Thus as a whole in a real application which uses many of these pattern the over all Python code will be slower than if it was written in one of the other languages. It may be old but that's why I picked one with source code so you, yourself can run the tests and see that they are still valid even today.

This was all in direct response to you wanting substantiated proof as to how fast or in this case slow Python is in regard to other languages. There is your proof that python is slower. Don't believe me still? Then run the tests from the second link yourself and post the results.

---

### Post by aks44 on 2007-05-31
@pmasiar :
I'm working in the geotechnics field, on a client-server app that does very intensive data analysis (I'm part of the server team, if you didn't already guess).

Don't get me wrong though, almost all the server code is C++.
But the damn thing eats CPU cycles like I breathe, and as a dirty fix we had to heavily optimize a few core analysis functions in order to be able to scale up the number of concurrent clients.

But if the current trend continues (customers connecting more and more clients to servers that were not designed for so much load), we'll soon have to redesign it as a cluster. That would be a good thing IMO : that would allow us to get rid of that unmaintainable assembler code.

---

### Post by Mirrorball on 2007-05-31
Python is often much slower than C/C++. Sometimes it doesn't matter, sometimes it does. I've already made my simulation run more than 10 times faster by translating part of the code from Python to C++.

---

### Post by ghostdog74 on 2007-05-31
> **seamless said:**
> To show exactly how slow it actually is using a known baseline.
there's actually no need to show how slow because i already knew that, after you specified c vs python. You are comparing speed from 2 different categories of languages, one is compiled, the other is interpreted. I thought that you would at least compare Python with Perl or other interpreted languages, but alas. Since you still don't get what i say, let's just stop here.

> 
Again to show a known baseline as a reference of comparison. Most people know how fast a C application executes hence why it was used for comparison.

yup, i bet you yourself already knew that, so why compare C with Python in terms of speed of execution in the first place?

> 
In the sense of execution speed which is what the second link shows as compared to other langauges mentioned. Programs are created using a variety of patterns and Python runs slower than any of the listed languages in almost every case. Thus as a whole in a real application which uses many of these pattern the over all Python code will be slower than if it was written in one of the other languages. It may be old but that's why I picked one with source code so you, yourself can run the tests and see that they are still valid even today.

it seems you are too obsessed with those shootout sites  and about speed. Its pointless to base your perception on those fun sites. Do you know how many competent Python programmers are out there that knows the inside out of the language and has most probably haven't visited that site.? etc? how do you know the people who submitted those codes have already optimized them till the cows come home?

> 
This was all in direct response to you wanting substantiated proof as to how fast or in this case slow Python is in regard to other languages. There is your proof that python is slower. Don't believe me still? Then run the tests from the second link yourself and post the results.

yup, slower in some ways, but not in some others.. that's the whole point. Still don't get it? well this will be my last post to you.

---

### Post by barmazal on 2007-05-31
now ppl say NASA and Google, do you mind explaining what Google and NASA doing with Python because my grand mom has pc with Arch Linux but she plays Sudoku with it.
Python works with AJAX? Every WEB language does. Python wasn't first though.
Python can create "fancy installers on Ubuntu" does this mean it's good?

**pmasiar,** what industry needs C speed? Surely not website with login and few tables dragged out of database.

all professional software industries need this kind of speeds, do you really can imagine high quality 3D game made on Python or high quality audio editor? 
With C you can do whatever you want, with Python you are limited to libraries some guys write on C when not sure those are exactly what you need.

---

### Post by seamless on 2007-06-01
[QUOTE="ghostdog74"]how do you know the people who submitted those codes have already optimized them till the cows come home?[/QUOTE]
Since you seem to know so much about Python and how it operates, why don't you tell me.

[QUOTE="ghostdog74"]I thought that you would at least compare Python with Perl or other interpreted languages, but alas. Since you still don't get what i say, let's just stop here.[/QUOTE]
Maybe you should actually look at what I posted because the second link which is the one I've constantly be referring to specifically compares Python to Perl as well as Java. You are right, since you don't care to actually look at anything I've written and would rather get defensive when someone tells the truth about your favorite language that you don't want to hear. So lets just stop here.

[QUOTE="ghostdog74"]yup, slower in some ways, but not in some others.. that's the whole point. Still don't get it? well this will be my last post to you.[/QUOTE]
yup, slower in many ways, but not in a select few others.. that's the whole point. Still don't get it? well this will be my last post to you too.

---

### Post by brooksbp on 2007-06-01
> **barmazal said:**
> now ppl say NASA and Google, do you mind explaining what Google and NASA doing with Python because my grand mom has pc with Arch Linux but she plays Sudoku with it.
Python works with AJAX? Every WEB language does. Python wasn't first though.
Python can create "fancy installers on Ubuntu" does this mean it's good?

**pmasiar,** what industry needs C speed? Surely not website with login and few tables dragged out of database.

all professional software industries need this kind of speeds, do you really can imagine high quality 3D game made on Python or high quality audio editor? 
With C you can do whatever you want, with Python you are limited to libraries some guys write on C when not sure those are exactly what you need.

Well... if programming languages and query languages were so fast we wouldn't need this wonderful thing called caching.

Facebook uses PHP.  They obviously have an enormous ammount of data in databases.  For cache alone they run roughly 200 servers (4 core AMD64, 16gb RAM).  They run memcached on those machines. That's roughly 3.2 **terrabytes** of cache of websites alone.  Facebook also isn't blazingly fast even with this caching architecture.  So.... do you really thing that 'industry' let alone business really need C speed? Sure do. Even faster. (*I hear someone yelling OCaml in the distance...*)

And in reply to AJAX... AJAX is pretty much independent of any python web development; should be treated as independent development.  Sure there are web application frameworks written in python, and you can manage a server using python, etc... but, the AJAX side of the website is pretty much independent of your server architecture... AJAX = Asynchronous JavaScript and XML... does python really care about JavaScript or XML in web development? In most cases, no. In good practice, no.

---

### Post by barmazal on 2007-06-01
> **brooksbp said:**
> /.....

[COLOR="DarkOrange"]**brooksbp**[/COLOR]

probably i wasn't clear enough but you said more or less the same things i've said.

---

### Post by AZzKikR on 2007-06-01
I don't know what the fuss is all about. It seems like a language war around here. As far as I am concerned, every language has it's pros and cons. As for me, I don't see myself writing a fully loaded 3D game engine in Java or Python. I would see myself writing it in C/C++. I see myself writing scripts, and user interfaces using Java or Python though. Even though C/C++ is also good for writing GUI's, I'd prefer other languages since it's just faster development.

As someone else on this topic has said: computer are getting fast enough - users do not care if a window is shown in 1/1000 seconds, or 1/700 seconds. At least, I don't :)

Different languages exist for different purposes. That is my point of view. Except for C#. Which can burn in hell.

---

### Post by malfist on 2007-06-01
For those who claim interpreted is slower than compiled, look at this:
> 
In a paper written in 1999 by Lutz Prechelt it is outlined that, statistically, programmer efficiency and experience has a bearing many standard deviations greater on run-time and memory usage than language choice. This paper specifically uses Java as a basis for the comparison, due to its then bad reputation.
Source:
[http://en.wikipedia.org/wiki/Java_%28programming_language%29#Performance]("http://en.wikipedia.org/wiki/Java_%28programming_language%29#Performance")
Granted that is from Wikipedia, but that quote is cited to:
> Lutz Prechelt. Technical opinion: comparing Java vs. C/C++ efficiency differences to interpersonal differences. Communications of the ACM, Vol 42, #10, 1999

Have fun.

---

### Post by Mirrorball on 2007-06-01
If the program just opens a window, the choice of programming language doesn't matter and using Python is probably better, because it's easier to use than C. But if a program in C takes a week to run while the same program in Python takes 10 weeks to perform the same calculations, I'd say the choice of programming language matters a lot.

---

### Post by AncientPC on 2007-06-22
> **wizardofyendor said:**
> I've always perfered perl to python, I just find it easier, I think it's what you learn first you like better...

That's not always the case.  I first learned BASIC and then QBASIC and never use those languages today. :)

To be fair, I didn't understand QBASIC's sub-routines (I was 11, cut me some slack) so I had a gazillion GOTO lines for my text-based RPG.

---

### Post by laxmanb on 2007-06-22
The reason is obvious - python is less verbose than Java...

but please don't forget how Java programmers use IDEs with code completion to get over most of the extra verbosity while writing code... while most python programmers use Vi/emacs/Gedit to write code...

---

### Post by pmasiar on 2007-06-22
> **Mirrorball said:**
> But if a program in C takes a week to run while the same program in Python takes 10 weeks to perform the same calculations, 

Absolutely. Or if you need response in real-time (so you cannot use even java - garbage collector has its own mind). Or if you competing with someone else to react on incoming data (computerized stock traders) - you need real compiled language optimized for performance: you need C or C++.

But I would guess that about 90% or programming efforts are outside of such constraints, and Python will be just fine. BTW stock traders use Python or Ruby to manage deployment, generate test data and measure performance.

---

### Post by ablegreen on 2007-06-22
I know Visual Basic, a little of C++, and a little of Java.

I've jiust started learning Python yesterday, and I'm just loving it so far. Check out the A Byte of Python book if you want to learn! I'm 1/4 of the way done and the author is very, VERY good at explaining. Also check out Dive Into Python, too. BTW all these books are free to download. :D So far I can already tell that this language is going to be my favorite. I've done researching before learning, and there isn't really a single negative review on it.

Go here:
[http://pythonology.org/success](http://pythonology.org/success)
and here:
[http://pythonology.org/spotting](http://pythonology.org/spotting)

If you want to know who uses Python in the real world.

---

### Post by vermanshul on 2010-06-18
> **pmasiar said:**
> Python can do *much more* than just fancy bash script.

All languages are concerned about explaining what needs to be done to a very stupid listener (a computer).
Python is the only pragmatic and usefull language I am aware of what has as a design goal to be readable and understandable by humans first, and computer only as second. Where compilers bends backwards to accomodate humans, not the opposite as other languages. Interestingly, you can keep almost all expresive power of Perl, having none of readability problems of it.

Dynamic typing simplifies programming substantially. Java helps to avoid "spaghetti code", but we have "ravioli code" instead: hundreds of bite-size objects, and you need to "bite" and learn each one to use it properly.

Dynamic exceptions (instead of Java's static checked exceptions)  also allows to handle problems where it makes sense (or ignore them for prototype) and avoid many lines of boilerplate code.

Python has many, many subtle improvements which Java programmer might be not aware (because she learned to live without them), but are so annoying when going from Python to Java. As saying goes, Python is object-oriented; Java is Object-obsessed :-) Ie. It is easy to return multiple objects from Python function (and assign them), in Java you need to create object.

```

def fun1(par1, par2="val1"):
    # par2 has default value if omitted: Java requires 2 definitions
    return par1, par2 # par1 is int, par2 is string

i1, s1 = fun1(5)  # assigning 2 values

```

Operator overloading allows you to create intuitive objects which "just work". 

Ahh, so many little details. Just try it. :-)

Hmm...sounds a lot like Ruby to me.

---

### Post by myrtle1908 on 2010-06-18
Talk about digging up one of the most pathetic threads ever from the grave.  The sheer amount of "OMG my Python is bigger than yours" contained within this thread is bordering on childish.  This thread should be returned from whence it came; so much so that I'm ashamed to have posted within it.

---

### Post by simeon87 on 2010-06-18
When I saw the bump, I thought the user specifically registered to start the Ruby/Python flame war.. then I decided not to reply. Apparently I did post in this thread by now.

---

### Post by juancarlospaco on 2010-06-18
```
[B]#!/usr/bin/env python
# -*- coding: utf-8 -*-
# License:      GPL v3
try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" ")
    print(" No PYTHON-PSYCO avaliable, this application will run slower... ")
    print(" ")
    pass[/B]
```

---

### Post by slavik on 2010-06-18
dead things stay dead.

---

