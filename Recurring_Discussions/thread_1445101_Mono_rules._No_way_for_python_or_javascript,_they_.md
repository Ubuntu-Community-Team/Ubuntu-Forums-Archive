---
title: "Mono rules. No way for python or javascript, they are poors in performance."
date: 2010-04-02
forum: Recurring Discussions
---

### Post by michaelmartin007 on 2010-04-02
GNOME 3 is near. 

Many many people are against MONO and yet it is the best option in terms of high-level language for programming in addition to being well documented.

LET ME SAY ONE THING. PYTHON WAS NOT CREATED TO BE GOOD IN PERFORMANCE. Despite the many projects to improve their performance I think is not a good option because they do not create it thinking in performance. 

Now, please, LOOK AT VALA LANGUAGE. They created it thinking in performance as C. Vala compile to C and it is very good in performance. Just as good as C. THIS IS BECAUSE THEY CREATED IT TO BE FAST. It is a high level language and has all advantages to be the best for base libraries and applications for Gnome 3.

What is the problem with Vala?
There are few developers who know and develop with it. Still has not reach the 1.0 version. There are no tutorials. Should be good if Vala developers should write good tutorials to teach newbies to program with Vala.

But right now we have mono Gtk # and it is a good alternative. Perhaps the better. I have used KDE for many years. Now I use Gnome. I see how many users and developers say that speed is not important, that Python is a good choice for almost everything. I remember when it was said that gtk+ was better than Qt in performance. Then it was all a question of performance in addition to the issue of the old licenses from Trolltech qt. Now, every day, C has a more limited use. Developers in Gnome use python, javascript ..., languages all very poors in performance.

What happened in Gnome?
Each year more and more developers realize how hard it is to develop and maintain the code in gtk. But they have changed a fast language in performance by python and javascript that are slower. Many people would have to look at the forums for years to see how performance gloried gtk. The more applications in python and javascript entering gnome the more slower will became.

Make room for MONO in Gnome without limits. There are even developers who are developing a compiler to avoid the use of runtime with mono in Gnome. I read it but I can not remember where. Mono is faster but a compiler without use of mono runtime would even be better. Mono is the future of Gnome. It is well documented and there are all sorts of tutorials.

The other two that are wonderful replacements for gtk are Vala and Genie. Genie should be the best dew to be python like when coding but Genie has very few examples and no documentation.

---

### Post by Dayofswords on 2010-04-02
only one gnome app is written in mono, tomboy

edit: see [http://live.gnome.org/GNOME3Myths#GNOME_3.0_depends_on_Mono.21](http://live.gnome.org/GNOME3Myths#GNOME_3.0_depends_on_Mono.21)

i use what works for me, as long as it doesn't constantly freeze or have basically no features, i dont care for performance, as long as it does the job right and in a timely manner

---

### Post by uljanow on 2010-04-02
I was skeptical, but you benchmarks convinced me.

---

### Post by The Cog on 2010-04-03
I'm not putting Microsoft mono on any computer of mine. So as far as I'm concerned, the performance of any app that requires mono would be "doesn't work", except that it doesn't even get past "won't install because it conflicts with mononono".

---

### Post by Psumi on 2010-04-03
Clippy > "You seem to be poor in grammar, would you like help with that?"

---

### Post by kaivalagi on 2010-04-03
I currently use Gnote instead of Tomboy to not have any mono requirements....so far. We'll see what requirements Gnome 3.0 will bring

Python is everywhere so why try and argue for something that is sparingly used? How would we remove all the python dependencies?

A bit late to the party maybe?

Python performs well enough for me...and where are your benchmarks giving a proof to what you say anyway?

---

### Post by kevCast on 2010-04-04
You trade abstraction for performance. If you were really concerned for performance, you'd write your own DE in assembly.

---

### Post by Ric_NYC on 2010-04-05
If you trust this kind of deal:

>  The company did not provide an amount for how much in invoices Novell sent to Linux shops in the quarter and did not talk about how much of the **Microsoft certificates for SUSE Linux**:shock: had been distributed, or more importantly, what the renewal rate was on the certificates that Microsoft's customers activated three years ago and which came up for renewal.


[www.theregister.co.uk/2010/02/26/novell_q1_f2010_numbers/](www.theregister.co.uk/2010/02/26/novell_q1_f2010_numbers/)

---

### Post by zekopeko on 2010-04-06
> **Ric_NYC said:**
> If you trust this kind of deal:

[www.theregister.co.uk/2010/02/26/novell_q1_f2010_numbers/](www.theregister.co.uk/2010/02/26/novell_q1_f2010_numbers/)

Do you even understand what you quoted?

---

### Post by juancarlospaco on 2010-04-06
**Python is part of LSB** *(Linux Standard Base)*

If you dont like Python stay away from Linux.

---

### Post by gnomeuser on 2010-04-06
> **juancarlospaco said:**
> **Python is part of LSB** *(Linux Standard Base)*

If you dont like Python stay away from Linux.

X is part of "failed non-standard", if you don't like X stay away from Y.

Why what a fine argument. Now remind me how the LSB is even remotely a worthwhile standard that brings with it any improvement to Linux as a whole nor to ISVs. Never the less one we should actively be supporting.

That being said the OP didn't say that python have a place, just that one shouldn't pick it for performance and that relying on it for a desktop e.g. would likely be a poor choice compared to other available options.

---

### Post by juancarlospaco on 2010-04-06
LSB is not failed, is a BASE, and Ubuntu is compliant, try :

lsb_release -a

Im waiting for the versions 4.x

---

### Post by kaivalagi on 2010-04-07
Interesting discussion but where are the benchmarks to hold up the argument?

I half believe the "message" but won't be remotely behind it if the performance of Mono isn't proved to be far superior to Python/Ruby/Lua etc...

I like C# as a language, it makes sense and has a good deal of useful features, I've just not bought into the performance bit yet...any external links maybe with a range of equivalent processing tasks compared?

I do remember when the .net framework came out, and there were discussions of it's poor performance in comparison to "compiled directly to native" languages/frameworks then. Now it seems there is an argument of Mono versus run time interpreted languages such as Python. Surely with today's hardware processing capabilities it is pretty much irrelevant just like the initial argument against .net? If you truly want performance then surely you'd look at using C/C++ for core libraries anyway?

I don't want an argument, just a good topical discussion :)

Regards

---

### Post by zekopeko on 2010-04-07
> **kaivalagi said:**
> Interesting discussion but where are the benchmarks to hold up the argument?

I half believe the "message" but won't be remotely behind it if the performance of Mono isn't proved to be far superior to Python/Ruby/Lua etc...

I like C# as a language, it makes sense and has a good deal of useful features, I've just not bought into the performance bit yet...any external links maybe with a range of equivalent processing tasks compared?

I do remember when the .net framework came out, and there were discussions of it's poor performance in comparison to "compiled directly to native" languages/frameworks then. Now it seems there is an argument of Mono versus run time interpreted languages such as Python. Surely with today's hardware processing capabilities it is pretty much irrelevant just like the initial argument against .net? If you truly want performance then surely you'd look at using C/C++ for core libraries anyway?

I don't want an argument, just a good topical discussion :)

Regards

[Here you go]("http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=csharp&lang2=python"). You can play with all kinds of benchmarks there.

---

### Post by kaivalagi on 2010-04-08
Very interesting, quite an increase in performance when compared to Python...

Now all the developers of python apps just need to port them over to c# :)

Thanks for the link

Cheers

---

### Post by gnomeuser on 2010-04-08
> **zekopeko said:**
> [Here you go]("http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=csharp&lang2=python"). You can play with all kinds of benchmarks there.

I believe these tests are quite outdated (at least the last time I checked they were using Mono 1.2.x). The fair comparison for pure performance might be using Mono 2.6 or even Mono with the LLVM backend (which is about 30% faster). 

Likewise for Python comparing it to Unladen Swallow and Python 3 might be interesting.

There simply aren't any recent benchmarks which are reliable and representative of the real world. 

That being said, Mono has excellent performance which continues to improve over time, improvements which will benefit all applications and Ubuntu has one of the best maintained Mono stacks available. Users should find their Mono experience here the best of breed. If one likes the Python syntax there is even the option of using something like Boo or IronPython to leverage the benefits of both.

---

### Post by zekopeko on 2010-04-08
> **gnomeuser said:**
> I believe these tests are quite outdated (at least the last time I checked they were using Mono 1.2.x). The fair comparison for pure performance might be using Mono 2.6 or even Mono with the LLVM backend (which is about 30% faster). 

Likewise for Python comparing it to Unladen Swallow and Python 3 might be interesting.

There simply aren't any recent benchmarks which are reliable and representative of the real world.

This is the new benchmark. There is still the old one but it has OBSOLETE written all over it. if you click on C#/Mono and navigate to the source file for the benchmark you get [this]("http://shootout.alioth.debian.org/u32/program.php?test=binarytrees&lang=csharp&id=2"). Scroll down and you will see he is using Mono 2.6.1.

So try it out.

> 
That being said, Mono has excellent performance which continues to improve over time, improvements which will benefit all applications and Ubuntu has one of the best maintained Mono stacks available. Users should find their Mono experience here the best of breed. If one likes the Python syntax there is even the option of using something like Boo or IronPython to leverage the benefits of both.

Hear hear.

---

### Post by zekopeko on 2010-04-08
> **kaivalagi said:**
> Very interesting, quite an increase in performance when compared to Python...

Now all the developers of python apps just need to port them over to c# :)

Thanks for the link

Cheers

Or they could run it on top of Mono. Mono supports a whole plethora of languages that can run on top of it (Python, Ruby, Java etc).

---

### Post by kaivalagi on 2010-04-09
> **zekopeko said:**
> Or they could run it on top of Mono. Mono supports a whole plethora of languages that can run on top of it (Python, Ruby, Java etc).

But what good would that achieve, I suspect running a python app through IronPython in Mono would be slower than through the native python interpreter? Does IronPython require the python dependencies to be installed too, I would assume so?

Still, interesting stuff none the less...

---

### Post by gnomeuser on 2010-04-09
> **kaivalagi said:**
> But what good would that achieve, I suspect running a python app through IronPython in Mono would be slower than through the native python interpreter? Does IronPython require the python dependencies to be installed too, I would assume so?

Still, interesting stuff none the less...

Actually the IronPython implementation is faster for a number of things and the IronPython guys have a stated goal of knowing how fast they are as well as to improve (the stated aim is to be at least twice as fast as CPython)

[http://ironpython.codeplex.com/wikipage?title=IP261Net40VsCPy26Perf&referringTitle=IronPython%20Performance](http://ironpython.codeplex.com/wikipage?title=IP261Net40VsCPy26Perf&referringTitle=IronPython%20Performance)

---

### Post by CraigPaleo on 2010-10-03
> **Dayofswords said:**
> only one gnome app is written in mono, tomboy

edit: see [http://live.gnome.org/GNOME3Myths#GNOME_3.0_depends_on_Mono.21](http://live.gnome.org/GNOME3Myths#GNOME_3.0_depends_on_Mono.21)

i use what works for me, as long as it doesn't constantly freeze or have basically no features, i dont care for performance, as long as it does the job right and in a timely manner

I'm pretty sure they're saying Tomboy is the only mono app included with Gnome. There are a ton of Mono apps. [http://www.mono-project.com/Software](http://www.mono-project.com/Software)

---

### Post by directhex on 2010-10-03
> **The Cog said:**
> I'm not putting Microsoft mono on any computer of mine. So as far as I'm concerned, the performance of any app that requires mono would be "doesn't work", except that it doesn't even get past "won't install because it conflicts with mononono".

Mononono is written by people who don't understand Linux so no, you're wrong. Tomboy and mononono install side-by-side fine.

---

