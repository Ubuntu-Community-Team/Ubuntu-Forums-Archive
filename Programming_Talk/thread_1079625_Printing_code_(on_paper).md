---
title: "Printing code (on paper)"
date: 2009-02-24
forum: Programming Talk
---

### Post by Flimm on 2009-02-24
What do you all think of printing code (on paper, not to stdout)? Am I crazy for even suggesting it?
One of the bugs I'm having trouble tracking down is giving me a headache, and I feel like having a pen and paper so that I can draw arrows and cross out text and generally scribble code. Maybe it's my fault for not designing the outline of the code on paper in the first place. What do you all think? Does somebody share my craving for good ol' pen and paper? Has anybody ever done this before?

---

### Post by Simian Man on 2009-02-24
Never.  Usually code I struggle with is too long and spread out across too many files for this to be feasible.  I do write out psuedocode on paper to play around with ideas sometimes though.

---

### Post by Tek-E on 2009-02-24
I have done it before. I think it helps sometimes.  But I guess it really all depends on how long the code is.  If you have a 1000+ long program then....I hope you have a lot of paper and time to read through it. lol.

---

### Post by simeon87 on 2009-02-24
I've never done this either; the ability to comment things out is quite valuable :)

---

### Post by drubin on 2009-02-24
basic functions for algorithm analysis maybe...

Never full projects/files.

---

### Post by jimi_hendrix on 2009-02-24
may i recommend a debugger then?

i personally like gdb with a frontend or dare i say it...VS2008 debugger

---

### Post by Can+~ on 2009-02-24
Commenting out lines works just as well, instead of wasting paper.

---

### Post by Can+~ on 2009-02-24
> **jimi_hendrix said:**
> may i recommend a debugger then?

i personally like gdb with a frontend or dare i say it...VS2008 debugger

With eclipse and the cdt plugin you can get a nice front-end for the gdb debugger also.

edit: whoops, I double posted.

---

### Post by drubin on 2009-02-24
> **Can+~ said:**
> Commenting out lines works just as well, instead of wasting paper.

Think of the trees!! :)

---

### Post by Tomosaur on 2009-02-24
I never print out code - I usually just draw squares and arrows to map out what should be happening, then step through to see what **is** happening.

---

### Post by Wybiral on 2009-02-24
If I'm trying to solve a problem and I'm bored at work or something, I'll sometimes write out basic lispy-lambda representations of my problem... But this really has to do with the fact that it provides a good way for me to represent my problem when I can't get to a keyboard. This is also much more about solving a problem than finding/fixing a bug.

I can't see how this would benefit you much, unless you were on a long flight somewhere, you don't have a laptop, and you want to really think about your implementation of some function... But how often does that happen to you?

---

### Post by descendency on 2009-02-24
I write out comments and then write code under them when writing larger programs. (document backwards)

---

### Post by Mr.Macdonald on 2009-02-24
Depends on the language, I wouldn't recommend printing C or C styled languages (unless you are on the go!). I do quite often write Lisp and Python code on paper.

---

### Post by HotCupOfJava on 2009-02-24
Well, if I can narrow a bug down to a particular class or method, I may print out that ONE section to get a better look at it. I find I can take more of the code in all at once when it is on a printed page rather than trying to scroll between lines. And I will make notes on the paper......

---

### Post by sujoy on 2009-02-25
i'd analyse code sections on paper at times, specially when i am not sure how layout should be. but for debugging and testing, comments and a debugger are enough for me.

---

### Post by ssam on 2009-02-25
if you think it will help go for it.

i usually print from gedit, its quite easy to control syntax highlighting, line numbers, line wrapping, etc. also it can print a header with the filename and page number at the top so you don't get lost.

use a small font, possibly use 2 pages to a side in the printer options. unless you are print the whole source of the kernel you should be fine.

re: think of the trees.
think of the energy usage of staring at a screen for a week.

---

### Post by Flimm on 2009-02-25
Well, I did it, I printed two python modules (16 pages) in colour and I read through it all. I managed to find quite a few details that needed to be updated, including docstrings, and I now realise what I need to do to fix that bug. I was waiting at the doctor's, so it was quite relaxing.

---

### Post by HotCupOfJava on 2009-02-25
> **Flimm said:**
>  I was waiting at the doctor's, so it was quite relaxing.

And there you have it. That is a good enough reason for me. Rather than waste time reading some silly mag you were productive and fixed some code.

---

### Post by monkeyking on 2009-02-26
consider using doxygen for getting a overview of a project.

---

### Post by wmcbrine on 2009-02-26
> **HotCupOfJava said:**
> Well, if I can narrow a bug down to a particular class or method, I may print out that ONE section to get a better look at it. I find I can take more of the code in all at once when it is on a printed page rather than trying to scroll between lines. And I will make notes on the paper......This.

I used to do it all the time. Nowadays, I've finally gotten used to doing almost everything on screen. It helps that I've been having a lot of printer problems the last few years. :D But I did it for years before that.

---

### Post by jespdj on 2009-02-26
I never print out source code. Code on paper is much harder to navigate than code in an IDE (the IDE provides things like automatically jumping to the definition or declaration of methods and variables, for example).

---

### Post by Flimm on 2009-02-26
> **monkeyking said:**
> consider using doxygen for getting a overview of a project.
Thanks for that tip, Doxygen looks nice. I should use it to document my code for new contributers.

---

### Post by hessiess on 2009-02-26
I generally don't print code, But LaTeX handles it quite well if I *need* to for whatever reason.

---

### Post by Paul Miller on 2009-02-27
I've done it, but I didn't really like the result.

I use mostly Python, and, while, given sensible indentation that doesn't mix tabs and spaces, it's easy to see where an indented block begins and ends on screen, on paper I find it a little more problematic.  If, for some reason, a block gets broken over two pages, then I'm really annoyed.

I'd say that if the code you want to print is fairly short (like under 10 pages or so), and the formatting is reasonable, then debugging via printout is a reasonable way to go.  I used to have to do this in college (C mostly, but some PDP-11 ASM) when the computer lab hours and my schedule didn't exactly match up, and it worked well enough in that particular case.

---

