---
title: "[SOLVED] Programming languages advice requested - newbie looking for new languages"
date: 2008-10-19
forum: Programming Talk
---

### Post by alberto ferreira on 2008-10-19
I know bash quite well now, I'd like to learn something that could be really useful but I feel that it's yet too soon for C++ 


Basically I'm looking for a language with lots of power (that allows me do do advanced stuff -- automating my computer as much as possible) yet simple (easier than C++) AND fast! -- lol, I know that these requirements aren't compatible but I'd like to have some input from you.
Which language(s) do you reccomend for me, taking into account that I'm looking for an intermediate language between bash and my final destination:C++

I don't want to learn perl, I've tried python for an hour and I love it! However it appears to be slower than bash :$?? Is this true?

---

### Post by mssever on 2008-10-19
> **alberto ferreira said:**
> I don't want to learn perl, I've tried python for an hour and I love it! However it appears to be slower than bash :$?? Is this true?
Python isn't slower than Bash. In bash, you do most things by starting many new processes, each of which has a startup overhead. In Python, you generally do everything in the same process. So, Python is a good choice.

Another good choice is Ruby. Ruby is a bit more Unix-like than Python, and a lot of Ruby just "makes sense" if you have a shell background. There were many times when I was learning Ruby that I was able to guess how to do something without looking it up, because it worked pretty much as I expected.

---

### Post by slavik on 2008-10-19
fork() is pretty fast in Linux due to copy on write for the memory pages involved.

Perl is also worth a look, IMO.
You might want to check out Scheme, also.

---

### Post by pmasiar on 2008-10-19
This kind of questions often pretty quickly descends to full-throttle language religion wars. OP, I recommend you to check sticky, with plenty of opinions, a poll, and many links.

My favorite "first" language is Python, see wiki in my sig for free books and training tasks. 

If you want to compare "look and feel" of many languages quickly, check [http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/) , which shows solutions (printing song: little bit more informative than just plain "hello world") for couple hundreds of languages.

---

### Post by jimi_hendrix on 2008-10-19
id go with a scripting language like the rest said

or if your adventerous (and want to  be confused a little more) try regular C

---

### Post by risu_vk on 2008-10-19
Me too feel python will be a good choice to fit your criteria . But i personally like c++ though it takes some time .As said , this topic is a good one for language war :). Give a try for one day with various options and sample programs .. Yourself will be the best to judge

---

### Post by alberto ferreira on 2008-10-19
I have a few questions:

1-What is fork() ?
2-How does Ruby compare to Python in therms of performance and "power"(going to the lowest level stuff)?

----------

I'm definitely going to check that site and see new languages in the next weekend though I would like to hear some more opinions.

Thanks

---

### Post by jimi_hendrix on 2008-10-19
[fork()]("http://en.wikipedia.org/wiki/Vfork")

there both scripting languages...meaning that they are high up so neither are low level (C/C++ is low level)

---

### Post by LaRoza on 2008-10-19
> **alberto ferreira said:**
> Which language(s) do you reccomend for me, taking into account that I'm looking for an intermediate language between bash and my final destination:C++

I don't want to learn perl, I've tried python for an hour and I love it! However it appears to be slower than bash :$?? Is this true?

Why is C++ the final destination? Don't set upper limits for yourself! You can do better than C++. There is a whole world out there that will take a life time to realise it is impossible to know everything.

Python is different than bash. I don't know why it would be slower. Bash is very limited. Most of its use is to provide a way to use other tools and to pass information along and do decision making.

I suggest you go to my site and use the language selector.

I would immediately think of Python or Scheme, but it is your choice.

---

### Post by mssever on 2008-10-19
> **alberto ferreira said:**
> 2-How does Ruby compare to Python in therms of performance and "power"(going to the lowest level stuff)?
Ruby is slower than Python, though the development version, 1.9, has a new interpreter and is much faster than previous version. I don't know how Ruby 1.9 compares to Python speed-wise. But in most cases, the speed differences are insignificant.

As far as "power" goes, that term means different things to different people. High level languages, such as Ruby and Python, are powerful in the sense that they allow you to express your wishes much more easily.

When it comes to low-level programming, that's what C is for. But I disagree with those who equate low level with power. Most of the time, working at a low level means wasting lots of time pushing bits around, when those tasks can often be done more efficiently by the computer. And even if you do gain increased performance by pushing bits, you'll likely waste enough time doing so, that you lose the benefit of working at a low level language.

Additionally, languages such as Ruby and Python can be easily extended in C if you need that extra speed boost.

---

### Post by jimi_hendrix on 2008-10-19
> **mssever said:**
> As far as "power" goes, that term means different things to different people. High level languages, such as Ruby and Python, are powerful in the sense that they allow you to express your wishes much more easily.

When it comes to low-level programming, that's what C is for. But I disagree with those who equate low level with power. Most of the time, working at a low level means wasting lots of time pushing bits around, when those tasks can often be done more efficiently by the computer. And even if you do gain increased performance by pushing bits, you'll likely waste enough time doing so, that you lose the benefit of working at a low level language.

Additionally, languages such as Ruby and Python can be easily extended in C if you need that extra speed boost.

+1

also i think proffesional programs use a combo of high and low level

i know some games uses scripting languages and a low level language like C or C++

---

### Post by alberto ferreira on 2008-10-20
I'm saying that C++ is my final destination because from what I understand it gives you a lot of low level stuff without having to recur to assembly. But if there are easier languages that have better/similar low level control I'd like to know.

I've seen ruby but I think that python is easy enough for my taste. 
So, if there isn't a language that is more powerful than python but with a difficulty level between it (Python) and C++ I'd like to know. Also I feel that perl is too messy for me (don't flame me).

A friend of mine told me about PHP, isn't that inferior to python?

Also, Python isn't considered a scripting language, or is it? Do you recommend for me to learn any scripting language in particular that will be likely to be widespread in the future?

Anyways, I've taken into account all of your opinions and I think I'm going to learn Python because it's clean and I hope it's powerful enough to suit my requirements.

Thanks once again

---

### Post by LaRoza on 2008-10-20
> **alberto ferreira said:**
> I'm saying that C++ is my final destination because from what I understand it gives you a lot of low level stuff without having to recur to assembly. But if there are easier languages that have better/similar low level control I'd like to know.

If you want to go "low level" but not use Assembly, the goal is strange. If you are going to use totally portable languages that can be compiled or used without machine specific code, how can it be "low level"? If you want to do things that are less abstract, like dealing with memory addresses, having only primitive data types, and simplicity, I recommend C. C++ has a standard library (and an STL). Using C methods in C++ is usually discouraged. C++ adds un-needed complexity if that is your goal.

> 
I've seen ruby but I think that python is easy enough for my taste. 
So, if there isn't a language that is more powerful than python but with a difficulty level between it (Python) and C++ I'd like to know. Also I feel that perl is too messy for me (don't flame me).

It depends on what you mean by "power". Python has a mix of paradigms, so it is hard to truly compare. One could say Lisp/Scheme are the highest level languages, but Python supports many similiar Lispy things.

> 
A friend of mine told me about PHP, isn't that inferior to python?

It depends on the criteria.

> 
Also, Python isn't considered a scripting language, or is it? Do you recommend for me to learn any scripting language in particular that will be likely to be widespread in the future?

No. It isn't executed line by line. It is compiled to byte code and run. (Also, you can use interpeters for any language, like I use tcc to run C programs)

---

### Post by mssever on 2008-10-20
> **alberto ferreira said:**
> I'm saying that C++ is my final destination because from what I understand it gives you a lot of low level stuff without having to recur to assembly. But if there are easier languages that have better/similar low level control I'd like to know.Most inexperienced programmers overestimate the value of low-level programming. Aside from those few situations that require it (such as kernels), consider the benefits of a language such as Python:

[LIST=1]
[*]Speed depends on many factors. If your bottleneck is the network, or the database, or the disk, or the user, etc., there's not much you can do about it. If, however, the bottleneck is the program, then you'll usually get the most benefit from adjusting your algorithm. And it's a whole lot faster and easier to change and test algorithms in Python than it is in C++. Much of the time, fixing your algorithm will buy you sufficient speed. In those cases where it doesn't, Python (and Ruby) allows you to write the speed-critical portions in C, while retaining Python's flexibility for the rest of the program. Remember, your program is usually slowed down by only part of its code.
[*]With high-level languages, you can work much faster, and use more natural ways of expressing yourself. This translates into fewer bugs.
[*]There's nothing wrong with mixing languages when appropriate.
[*]You'll learn the most important aspects of programming faster when you don't have to fight low-level rules just to keep a compiler happy.
[*]Python is Ubuntu's preferred language, so you'll probably find better help around here for Python.
[/LIST]
 
> I've seen ruby but I think that python is easy enough for my taste.Fair enough. Just so you realize it's there and might make an easy transition from your current background.
> So, if there isn't a language that is more powerful than python but with a difficulty level between it (Python) and C++ I'd like to know.As I mentioned earlier, the term "power" means different things to different people. So unless you define it for us, we won't know what you mean. > Also I feel that perl is too messy for me (don't flame me).Agreed. :)

> A friend of mine told me about PHP, isn't that inferior to python?In my opinion, yes. While it's certainly possible to write clean code in PHP (as it is in Perl), PHP's design (or lack thereof :)) tends to encourage newbies to follow worst practices. Even if you use a sane programming style, PHP still has its quirks that make life miserable.

> Also, Python isn't considered a scripting language, or is it?That's another term that different people use in different ways. I'd say that you can use it as a scripting language if you want, but it's much more than a scripting language. Most of the Ubuntu-specific programs are written in Python, and they go far beyond scripting.

---

### Post by CptPicard on 2008-10-20
> **alberto ferreira said:**
> I'm saying that C++ is my final destination because from what I understand it gives you a lot of low level stuff without having to recur to assembly.

You really have a special technical requirement for that?

> 
 But if there are easier languages that have better/similar low level control I'd like to know.

Low level control is intellectually trivial because the control structures are so rudimentary, yet usually makes you do a lot of work because you must implement higher-level control from scratch for no good reason, and if you've never been exposed to higher-level control in higher-level languages, you'll be hard pressed to figure out from zero what to actually try to implement, because you don't have the "mental ingredients" for that...

> 
So, if there isn't a language that is more powerful than python but with a difficulty level between it (Python) and C++ I'd like to know. Also I feel that perl is too messy for me (don't flame me).

Well, if Python had better lambdas, Python would be even more powerful... Lisp? Way more powerful than C++, too.

> 
Also, Python isn't considered a scripting language, or is it?

Matter of perception. You can script in it, but this kind of distinction is mostly pushed by people who think scripting languages aren't "real" programming languages... and they're wrong of course.

> Anyways, I've taken into account all of your opinions and I think I'm going to learn Python because it's clean and I hope it's powerful enough to suit my requirements.

I would suggest you set your requirements straight first ;)

---

### Post by josir on 2008-10-20
Hi Alberto, I am also searching for a new language in the Linux world. 

I agree also that the requirement mandates the language you are choosing. But if you can choose a single language to the most of the job, you can gain in productivity.

When you are choosing a language, generally performance is not the main issue. If you really need speed, Assembler or C are best option. But the question is: do you really need THAT speed ? Or are you trying to build user friendly and commercial applications?

The main topics for me is: How the community works, how hot is the marketplace, documentation and good app examples.

For now, I am investing my small coins in Python and I am enjoying :)

Good Luck!
Josir Gomes
Rio de Janeiro - Brasil

---

### Post by alberto ferreira on 2008-10-20
By power I meant more access to more low-level  stuff, but now I see that you can go low-level by incorporating C portions of code into python. Can you incorporate C++ portions of code into python also?

One last doubt, C vs C++, whatever one does can ultimately done by the other right? And if I learn one, the syntax of the other is very different or is it close? 
I say this because next year I'm going to college next year and we're going to learn C++
[B]After that will it be worth learning C?
[/B] I say this because  in the future when I have time I want to contribute to the Open source community, and maybe I'd like to modify the linux kernel for personal use and/or educational purposes. In that case if one knows C++ will he understand C ?

I've decided, I'm going for python!
Thanks a lot!

---

### Post by LaRoza on 2008-10-20
> **alberto ferreira said:**
> By power I meant more access to more low-level  stuff, but now I see that you can go low-level by incorporating C portions of code into python. Can you incorporate C++ portions of code into python also?

C++ used in a "low level" manner would just be C.

Using C++ features in Python would be...weird.

> 
One last doubt, C vs C++, whatever one does can ultimately done by the other right? And if I learn one, the syntax of the other is very different or is it close? 

Not really. C++ has a partial compatibility with C, so one could write C code that would compile with a C++ compiler, and one could disable certain C++ features that would mess up certain things, but in the end, C++ isn't C and using like C would be hard.

The syntax for C:

[php]
#include <stdio.h>
/* This is a comment, the above line is a pre-processor directive. */

// This is a comment as well, but it can't span multiple lines. It isn't
// compatible with earlier versions of C, but it is widely supported.
// The below line these comments is a function, that returns an integer, 
// with two arguments named "args" and "argv" of type integer and a point to a pointer (Don't ask, essential, and array of strings)
int main(int args, char ** argv)
{
/* Blocks are defined with braces, but indent for sanities sake.*/

    // Variable declaration, 
    // all variables must be declared (this one is also initialised). The type has to be given.
    // C won't enforce types. Static weak typing...
    int x = 0;
    // All statements end in semi-colons.

    if (x > 1)
    {
        //condition must be enclosed in parenthesis.
    }
    while (1)
    {
        // While loop
    }
    for (x = 0; x < 10; x++)
    {
        //for loop syntax:
        // for (initalise ; condition ; increment/decrement)
        // None are needed, so "for(;;)" is a never ending loop
    }


    return 0;
}
[/php]


> 
After that will it be worth learning C?

Yes. No need to learn what you are going to be taught right? Learn C on your own first. You'll get C++ when you take the class. If you know it already, you will be wasting time and probably bored.

> 
In that case if one knows C++ will he understand C ?

No.

---

### Post by CptPicard on 2008-10-20
> **alberto ferreira said:**
> By power I meant more access to more low-level  stuff

Mind you, this is a very restricted definition of "power" -- a lot of the very fascinatingly powerful things about programming languages are actually available only in languages that have at least some kind of runtime environment.

In my view, one can always learn the low level stuff in due time ("when you need it"), but the real "education" as programmer comes from higher-level languages. For example, I can do low-level things just fine, but I try not to ... and the things that make me go "whoah" are almost never written in low level languages.

For low-level access "when you need it", C is compact and very usable.

> 
but now I see that you can go low-level by incorporating C portions of code into python. Can you incorporate C++ portions of code into python also?

The problem with C++ is that C++ binaries are not binary compatible with C binaries, which is a bit of a standard... I've never tried it, but it would probably be difficult.

> 
One last doubt, C vs C++, whatever one does can ultimately done by the other right?

Anything you can do in any Turing-complete language can ultimately be done in any other Turing-complete language... but that's not a very informative statement. ;)

> 
 And if I learn one, the syntax of the other is very different or is it close? 

Syntax is close, actual usage is somewhat different.


> In that case if one knows C++ will he understand C ?

Yes. C is *superficially* a subset of C++.

---

### Post by LaRoza on 2008-10-20
> **CptPicard said:**
> 
Yes. C is *superficially* a subset of C++.

Actually, it isn't anymore, even superficially. Some keywords and concepts are subtley different.

---

### Post by jimi_hendrix on 2008-10-20
> **LaRoza said:**
> Actually, it isn't anymore, even superficially. Some keywords and concepts are subtley different.

example?

on windows (which i am on normally because i do my homework on it (printer reasons) and im too lazy to switch afterwards)

[this]("http://www.cprogramming.com/compilers.html") site gives all C++ compilers for C

but for *nix it recommends gcc for C

---

### Post by LaRoza on 2008-10-20
> **jimi_hendrix said:**
> example?


structs

Also, passing by reference.

---

### Post by Steveway on 2008-10-20
As for the scripting-language part.
Python adapts very easily.
I just wrote a simple script in python that checks my CPU-temperature and changes the CPU-governor to powersave if the temperature rises above 70 °C and to ondemand if it is at 52 °C or lower.
So if you see this program and someone says this is python, then he would think that python is a scripting-language, which is partly true.
But if you look at, for example, exaile and show it to someone and say that that is python then he would not think that it is a scripting-language, wich is also partly true.
So it depends.
Also here is my script:
```
#!/usr/bin/env python
#license: GPL/V3 or newer
#author: Stefan Murawski; steveway1@googlemail.com
import os
import sys
initialiaze = 'Pytempwatcher is started.'
maxtemp = '70'
oktemp = '52'
print(initialiaze)
while True:
#Check temperature and save it in temp1
    temp1 = os.popen("acpi -t | grep 'Thermal 0'").read()
#Use split to get only the temperature
    temp2 = temp1.strip('Thermal 0: ok,. degrees C\n')
    if temp2 >= maxtemp:
        os.system('sudo cpufreq-selector -g powersave &')
    if temp2 <= oktemp:
        os.system('sudo cpufreq-selector -g ondemand &')
```
Note: This script needs sudo-privilegies to change the cpu-governor.

---

### Post by alberto ferreira on 2008-10-20
OK, thanks everyone, I'm going to learn Python for now and if I have time in the summer vacations I will try learning C.

:)

---

### Post by jimi_hendrix on 2008-10-20
> **alberto ferreira said:**
> OK, thanks everyone, I'm going to learn Python for now and if I have time in the summer vacations I will try learning C.

:)

if you learn python well C wont be very hard

you should be able to do a lot of things quickly in it

but later on it does get a lot harder...

---

### Post by pmasiar on 2008-10-20
> **alberto ferreira said:**
> By power I meant more access to more low-level  stuff

no wonder we disagree, if we call different thing using the same name ;-)

> Can you incorporate C++ portions of code into python also?

Yes, there are libraries to generate wrappers translating C++ calls to C and back:  Boost.Python

> I say this because next year I'm going to college next year and we're going to learn C++

Learn Python by yourself to gain different perspective

---

### Post by sheto on 2008-10-21
If you are a bit adventurous, try out Java.

---

### Post by nvteighen on 2008-10-21
> **sheto said:**
> If you are a bit adventurous, try out Java.
If you're adventurous, try B... :)

(B: the ancestor of C)

---

