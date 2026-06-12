---
title: "A Grand Discussion of General Programming Thoughts"
date: 2009-01-31
forum: Programming Talk
---

### Post by eye208 on 2009-01-31
> **Wovaki said:**
> So my question is:
Which programming language would you reccomend, and why?
C.

Recently I heard someone say: "C is the rock upon which the church of IT is built."

And it's true. The vast majority of applications and libraries for Linux is written in C. Linux itself is written in C. C remains the most popular programming language, especially for open source projects. And by "popular" I mean: the most frequently _used_ one. You may hear lots of talk about languages such as Python for sure, but talk is not code. Check out your favorite applications. Which language was used to build them? There's a 95% chance that it wasn't Python.

[January Headline: C is the TIOBE Programming Language of 2008!](http://www.tiobe.com/tiobe_index/index.htm)
[C dominated 2008's open-source project nursery](http://www.theregister.co.uk/2009/01/21/open_source_projects_08/)

---

### Post by Wybiral on 2009-01-31
> **eye208 said:**
> C.

Recently I heard someone say: "C is the rock upon which the church of IT is built."

And it's true. The vast majority of applications and libraries for Linux is written in C. Linux itself is written in C. C remains the most popular programming language, especially for open source projects. And by "popular" I mean: the most frequently _used_ one. You may hear lots of talk about languages such as Python for sure, but talk is not code. Check out your favorite applications. Which language was used to build them? There's a 95% chance that it wasn't Python.

[January Headline: C is the TIOBE Programming Language of 2008!](http://www.tiobe.com/tiobe_index/index.htm)
[C dominated 2008's open-source project nursery](http://www.theregister.co.uk/2009/01/21/open_source_projects_08/)

This is true, essentially, it's our current foundation. But I'm more interested in building elaborate and elegant things on top of it, not mucking around in foundation code.

If your world revolves around writing low-level code and libraries, C is great. But when your world revolves around, say, server-side web development or interfacing with complicated databases... C is far from great.

---

### Post by CptPicard on 2009-01-31
Or, uh, if you're just simply interested in how to express programs in general. Programming is about giving formal specifications of (Turing-)computable functions in some language with some syntax plus semantics. It has nothing to do with the machine per se -- whatever makes the language do its stuff could be a magic abacus, for all I care. All those machines would be Turing-complete, so they are completely interchangeable, at least until we get to quantum computers or some sort of fundamental architecture changes...

The fascinating bit about it is how much of it can be "trivially handled" by the machine, and how much of it requires actual human intelligence and input. It's the latter that actually counts in the big scheme of things, and therefore, the more abstract we can get, the more useful the language is for expressing whatever we wish to model. It "gets to the point" better. 

Lisp is a great example... it was created as a notation to write down computations for scientific papers, until a grad student figured out he could write an actual evaluator for it. (Why did scientists not express their algorithms in assembly if it is so special? Think...)

---

### Post by eye208 on 2009-01-31
> **Wybiral said:**
> But I'm more interested in building elaborate and elegant things on top of it, not mucking around in foundation code.
Whatever you're interested in, you're not the OP. Please read his post. I think he said that he's interested in application development for Linux.

> If your world revolves around writing low-level code and libraries, C is great. But when your world revolves around, say, server-side web development or interfacing with complicated databases... C is far from great.
It's a common misconception that C is only for low-level programming tasks. Search the APT database for package names ending in "-dev". There are C APIs for pretty much everything. Database access, GUI programming, image processing, 2D/3D graphics, sound, video, network protocols, scientific math, etc., you name it.

It's all there, even the most obscure stuff that you have never heard of before. For example, just recently I had to deal with SSA subtitle files, and guess what, there is already a C library for rendering them. None of that high level language fluff (Python etc.) would have helped me out there. If you want to get things done in Linux, you have to learn C. And then, optionally, C++.

Knowledge of C and its related tools will help you even at times when you are not programming. It will help you understand build procedures, compile other people's programs from source, resolve dependencies etc. You'll be in control and less dependent on your Linux distributor.

---

### Post by CptPicard on 2009-01-31
> **bruce89 said:**
> Python wasn't first or even second in scripting languages.

When considering language popularity, there are two factors at play: sometimes popularity is a genuine sign of goodness, but the flipside is that "most programmers are average", therefore, they need an average language.

Nearly *all* of the most competent and insightful hackers I know are Lispers (and know a lot of other languages too), for example, but just a few of all the hackers I know are Lispers. The Lispers tend to have good ideas regarding about solution strategies in any language for some given problem, but the others tend to focus more on detail-knowledge of a particular technology.

---

### Post by eye208 on 2009-01-31
I recommend judging programming languages by output, not by people. The competent hackers seem to like LISP for the same reason they like [Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) and [LOLCODE](http://en.wikipedia.org/wiki/LOLCODE). And that reason has nothing to do with productivity.

---

### Post by nvteighen on 2009-02-01
> **eye208 said:**
> I recommend judging programming languages by output, not by people. The competent hackers seem to like LISP for the same reason they like [Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) and [LOLCODE](http://en.wikipedia.org/wiki/LOLCODE). And that reason has nothing to do with productivity.
Which is...?

---

### Post by CptPicard on 2009-02-01
> **eye208 said:**
> I recommend judging programming languages by output, not by people. The competent hackers seem to like LISP for the same reason they like [Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) and [LOLCODE](http://en.wikipedia.org/wiki/LOLCODE). And that reason has nothing to do with productivity.

That's one of the more preposterous comparisons I've ever heard, but I really would like to hear you fill in the rest of the argument, too.

May I ask what your experience is outside of writing C, so that I'm not just wasting time on someone obviously just blowing hot air and trolling for the fun of it?

---

### Post by fiddler616 on 2009-02-01
> **eye208 said:**
> I recommend judging programming languages by output, not by people. The competent hackers seem to like LISP for the same reason they like [Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) and [LOLCODE](http://en.wikipedia.org/wiki/LOLCODE). And that reason has nothing to do with productivity.
I've gotten the vibe of "Lisp makes me a better programmer" and "<insert esoteric language here> is kind of funny/entertaining/interesting"
In short: [citation needed]

---

### Post by CptPicard on 2009-02-01
> **fiddler616 said:**
> I've gotten the vibe of "Lisp makes me a better programmer"

Yes, it indeed does. You can cite John McCarthy, Paul Graham and me ;) Better yet, you can see for yourself.

> 
 and "<insert esoteric language here> is kind of funny/entertaining/interesting"

Esoteric languages that go out of their way to produce obscurity and weirdness are totally different from languages that seek to use an economical (small) set of strong, general primitives... but really, eye208 is either not serious or he lacks some really fundamental ability to discern between logical and illogical language designs...

---

### Post by fiddler616 on 2009-02-01
> **CptPicard said:**
> Yes, it indeed does. You can cite John McCarthy, Paul Graham and me ;) Better yet, you can see for yourself.
Don't forget ESR.

---

### Post by Cracauer on 2009-02-01
Lisp as in Common Lisp code out in the real world is usually the most goal-oriented code you can find (Scheme code can be different and me more of a pointer-proover experiment).

To me, C++ feels like the language people created to deliberately get interesting puzzles to solve. I can spend all my day researching why some construct that looks insane and - on the surface - looks like somebody just bailed out of thinking hard to get it right actually makes perfect sense after you learn all the history.

I only program in C++ if I get payed by time, not by project done. Lines of code might work, too, though.

---

### Post by fiddler616 on 2009-02-01
> **Cracauer said:**
>  Lines of code might work, too, though.
It's at moments like these when you don't use Python. And do use the
[PHP]def function()
{
    doStuff();
}[/PHP]
indentation style. :)

---

### Post by CptPicard on 2009-02-01
> **Cracauer said:**
> Lisp as in Common Lisp code out in the real world is usually the most goal-oriented code you can find (Scheme code can be different and me more of a pointer-proover experiment).

I find it absolutely fascinating that Lisp is 20 years older than C (1958 vs 1978 ) and still, pretty much in the first decade of computing, they already figured out how to create a language that both encompasses pretty much *everything* any later languages did as special cases and also built it using next to no syntax at all. And in a syntax that is homogenous enough to actually let you write front-end compilers for any language structures you might want to create. It really is a tour de force of *clear thinking* that impresses me just more and more I use it -- it's got all you need, and no more.

Algol and pals (later in that family, C) was a total regression... time was not ripe yet I suppose. And the AI Winter and Lisp's association with AI research did not help.

In the minimalist-elegance vein, I need to push Scheme a little (again, for the other readers' benefit) -- I do fully understand the practical considerations that make CL a more pragmatic language, but Scheme really pushes the minimalism to a really nice extreme. Plus, call/cc completes the only substantial gap CL has left when language concepts are concerned -- one gets exceptions and coroutines/generators from call/cc (as you know).

---

### Post by jimi_hendrix on 2009-02-01
> **fiddler616 said:**
> It's at moments like these when you don't use Python. And do use the

lets not go down that path again
> 
[php]def function()
{
    doStuff();
}[/php]indentation style. :)

i find this style more readable anyway (if your payed by lines of code, squeezing in a few functions that just call other functions might be nice :))

---

### Post by fiddler616 on 2009-02-01
> **jimi_hendrix said:**
> 
i find this style more readable anyway
Me too, by a lot, but I was trying to not say that in case it was considered flame-baiting :)

---

### Post by Mason Whitaker on 2009-02-01
Boa Constructor is a good Python graphical programming interface.

---

### Post by nvteighen on 2009-02-01
> **Cracauer said:**
> 
To me, C++ feels like the language people created to deliberately get interesting puzzles to solve. I can spend all my day researching why some construct that looks insane and - on the surface - looks like somebody just bailed out of thinking hard to get it right actually makes perfect sense after you learn all the history.


Ok, but isn't programming about solve things instead of creating more problems than you have?

> **fiddler616 said:**
> It's at moments like these when you don't use Python. And do use the
[PHP]def function()
{
    doStuff();
}[/PHP]
indentation style. :)

LOL... Curly-braced Python! Sadly, Python has no macros in order to do this.

---

### Post by Cracauer on 2009-02-01
> **nvteighen said:**
> Ok, but isn't programming about solve things instead of creating more problems than you have?


Face it, 99% of the problems we solve when sitting on our computer we wouldn't have without the computer in the first place.

In the case of C++ I think it's one big prank so that puzzle enthusiasts can spend work time on puzzling and having a good excuse to not get work done :)

---

### Post by Wybiral on 2009-02-01
> **slavik said:**
> Was the OP's question ever answered? If so move on. If you are not intending on answering the OP's questions (whatever they may be) move on.

We could always talk about Perl, if you'd like?

---

### Post by fiddler616 on 2009-02-01
> **nvteighen said:**
> LOL... Curly-braced Python! Sadly, Python has no macros in order to do this.
Fail, I was deliberately trying to not make that Python (since I'd just mentioned not using it). I guesss it'd be 'public static void' instead of 'def'...oh well.
And I'd say a lot more than 1% of the problems solved with computers relate to non-computer issues. Math/science alone is a good 10% or so.

@slavik Are you sure you want to restrict constructive, relevant-to-the-subforum, intelligent discussion that happens to take place on a solved thread? If you want, I can just make a new thread and call it "A Grand Discussion of General Programming Thoughts"...

@Wybiral XD

---

### Post by slavik on 2009-02-01
> **fiddler616 said:**
> Fail, I was deliberately trying to not make that Python (since I'd just mentioned not using it). I guesss it'd be 'public static void' instead of 'def'...oh well.
And I'd say a lot more than 1% of the problems solved with computers relate to non-computer issues. Math/science alone is a good 10% or so.

@slavik Are you sure you want to restrict constructive, relevant-to-the-subforum, intelligent discussion that happens to take place on a solved thread? If you want, I can just make a new thread and call it "A Grand Discussion of General Programming Thoughts"...

@Wybiral XD
yes, please do ..

---

### Post by fiddler616 on 2009-02-01
...the continuation of the apparently-offtopic portion of the "Ubuntu Programming" thread.
Current discussions include whether C++ is for puzzle people, braces in Python, defining a function in a bracey language, and what percentage of problems solved by computers would never have existed if computers didn't exist in the first place.
Cheers.

---

### Post by fiddler616 on 2009-02-01
Announcement: Please move all not-immediately-relevant-to-the-OP discussion [here]("http://ubuntuforums.org/showthread.php?t=1057544").
Edit: Slavik just got +1 cool-moderator points for merging that into this thread, but with a different title. So disregard that link.

---

### Post by jespdj on 2009-02-02
Which programming language you should use? It depends, ofcourse.

**Use the right tool for the job**, and there's no such thing as a single tool which is optimal for any kind of job.

---

### Post by aj_ on 2009-02-02
Perhaps it's because I am a novice programmer, but I fail to see why one would want to develop in C over C++. I was under the impression that you can compile pure C in a C++ compiler. So why not do so, and take advantage of the better type safety, namespaces, etc.?

---

### Post by maximinus_uk on 2009-02-02
> **aj_ said:**
> Perhaps it's because I am a novice programmer, but I fail to see why one would want to develop in C over C++. I was under the impression that you can compile pure C in a C++ compiler. So why not do so, and take advantage of the better type safety, namespaces, etc.?

Now I must first admit to usually using either Lisp or Python in day to day programming, but I do sometimes I have to use C, and I choose it over C++ for these reasons:

1: Usually I'm using C because it's close to the hardware. The added features of C++ take me further away from that.

2: C is a small language. I find it 'fits in the head' when I am programming. C++ fails this standard.

C serves a purpose, and for that purpose it's very good. But for the most part, C and C++ in particular just seem like the hard way to go about it. I should know, I spent 10 years with C/C++ until moving to Linux in '99 and learning Perl put me on the right path :D

---

### Post by CptPicard on 2009-02-02
A couple of classic threads that need to be mentioned and everyone should be reading because otherwise this is a rehash:

[http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794)
[http://ubuntuforums.org/showthread.php?t=890695](http://ubuntuforums.org/showthread.php?t=890695)

A lot of important stuff said there already. In particular, the some guys' interesting strategy of "complete denial and keep demanding proof" is, in retrospect, talented trolling. :)

---

### Post by Kilon on 2009-02-02
> **jespdj said:**
> Which programming language you should use? It depends, ofcourse.

**Use the right tool for the job**, and there's no such thing as a single tool which is optimal for any kind of job.

This argument is a bit non practical. Learning a new tool for each time we deal with a different task ? Why there is no optimal tool for any kind of job ? Who says that ? Who defines what is optimal ?

---

### Post by slavik on 2009-02-02
I slightly modified your post for an easier reply ...

> **Kilon said:**
> This argument is a bit non practical.
1. Learning a new tool for each time we deal with a different task ?
2. Why there is no optimal tool for any kind of job ?
3. Who says that ?
4. Who defines what is optimal ?

1. Only if whatever you have in your toolbox does not quiet fit the job. Text processing in C is much more of a pain than with Perl.
2. No idea, I would guess that it is impossible to create a perfect language.
3. 30-40 years of Computer Science.
4. People who solve the problems, but I am sure that is not exatly what you mean since it is impossible to have an optimal language for any job (because it's impossible to prove that a language is optimal, you can prove an optimal algorithm, but not a language).

I've done CGI in C which accessed MySQL ... it's fun for about 5 minutes, then it becomes very tedious very fast.

---

### Post by Kilon on 2009-02-02
> 1. Only if whatever you have in your toolbox does not quiet fit the job. Text processing in C is much more of a pain than with Perl.

Even if it does not "quite fit" a single task , why the language is not optimal ? Why not find workarounds like libraries or IDEs that make the job easier ? Wont those tools make the language mucm more optimal ?

> 2. No idea, I would guess that it is impossible to create a perfect language.


Is optimal the same as perfect ?

> 
3. 30-40 years of Computer Science.

Can computer Science speak by itself ?

> 4. People who solve the problems, but I am sure that is not exatly what you mean since it is impossible to have an optimal language for any job (because it's impossible to prove that a language is optimal, you can prove an optimal algorithm, but not a language).


Why you can prove an optimal algorithm and not an optimal language ? Why it is impossible to have an optimal language for any job. 

I think we have a circular argument here like " the chicken made the egg or the egg made the chicken " 

The answer to those question is not "There is no optimal language for any kind of task " , the right answer is there " A computer language can be optimal for any kind of task if the tools that accompany the language can compensate any of the languages shortcomings ".

---

### Post by CptPicard on 2009-02-02
The "optimal tool for any job" question is really very interesting and something I have been thinking about a lot... 

I really think the idea that everything is job-dependent is just used to fudge issues and avoid the question. Most language development aims at finding better general purpose programming languages. Now, there may not be "one language to provably rule them all" and some approaches are rather opposite to each other (imperative vs. pure-functional), but aiming for better general-purpose languages is what we're after, so apparently there is some objective idea there.

We want to solve problems and model "things" with computational concepts, and then express all that in the language. The fact that we have joke languages such as Brainfuck also proves that people can certainly understand when a language does *not* fulfill criteria for good general-purposeness... there has to be the opposite to this too :)

---

### Post by maximinus_uk on 2009-02-02
1: Anybody who has invested time and effort into learning more than 1 language can see that some are more optimal, or 'a better fit' than others. Perl is better than C for text processing because it's like a major portion of the language is built for this task. You can get a C regex lib I suppose but it's like using a sports car as a family carrier; sure it'll be faster and it will get the job done but in every other way will just cause pain.

2: Optimal is not perfect. The perfect language does not exist.

3: Can computer science speak by itself? Yes

4: An algorithm is mathematical, so we can prove these things. Almost all languages are computationally equal though, if you can do it Scheme you can do it in brainfuck. But is brainfuck as usefull as Scheme?

> The answer to those question is not "There is no optimal language for any kind of task " , the right answer is there " A computer language can be optimal for any kind of task if the tools that accompany the language can compensate any of the languages shortcomings ".

If a language is optimal or not for a given task is open to argument; deciding if a language is obviously NOT optimal is usually pretty easy. Take this for example, to reverse the lines of foo.txt and output to bar.txt:

perl -e 'print reverse <>' foo.txt > bat.txt

Try doing that in C. Not hard, but not ceratinly not as easy as this. Is perl optimal? Maybe Ruby or Python are slightly better. May fav. language, Lisp, is certainly not optional for this!

---

### Post by slavik on 2009-02-02
Brainfuck is not a joke language. It answered a very real problem. The problem being: Create a Turing complete language for which you can write the smallest compiler possible. Brainfuck has been proven to be Turing complete and the compiler for it is less than 200 bytes.

When you have a domain specific language (vs. something more general purpose), the language can make safe assumptions that reduce the amount of code you have to write. Think of it this way: you have a text file with a specific field and record separators (output from "ls -l" or from "ps auxwww"). There are 3 ways to process this data if you want to get a single field or a DB type lookup: cut, awk or write your own script in Perl/PHP/Python/Ruby. For the simpler task of just getting a certain field (like PID of some process depending on options it was given when started), cut and awk fit the bill much better because they split up the text for you and you just ask them to get what you want. With P3R, you have to manipulate the data before you get it to a state where you just ask for things. But if you try to do something more complicated with this data like looking up what files they have open and the size and type of those files, now it becomes very difficult to do this with cut/awk and you have to resort to something bigger, P3R or shell script.

---

### Post by maximinus_uk on 2009-02-02
> **CptPicard said:**
> The "optimal tool for any job" question is really very interesting and something I have been thinking about a lot... 

I really think the idea that everything is job-dependent is just used to fudge issues and avoid the question. Most language development aims at finding better general purpose programming languages. Now, there may not be "one language to provably rule them all" and some approaches are rather opposite to each other (imperative vs. pure-functional), but aiming for better general-purpose languages is what we're after, so apparently there is some objective idea there.

We want to solve problems and model "things" with computational concepts, and then express all that in the language. The fact that we have joke languages such as Brainfuck also proves that people can certainly understand when a language does *not* fulfill criteria for good general-purposeness... there has to be the opposite to this too :)

I think it would be very very hard indeed  to credit 'the most optimal tool'. Firstly, what metric are you testing with? Least LOC? Most human-readable? Quickest to type out? Least prone to errors?

I think there are 2 steps; there is *the language in which you find it easiest to solve the essential problem*, which could one of many really, depending on the problem at hand.
Then there is the *language best for expressing this algorithm*, another thing altogether.

As a very simple example, I wrote some genetic programming stuff last month in Python, of all things. Something that normally needs as much CPU speed as you can get. But I needed to see what actually worked first, and the easiest answer to that was Python.
Sure it looked like the ugliest hack-fest you ever saw, but a few days of work with python enabled me to see that the algo I was trying out wasn't going to work. I estimate it would have taken me a month of C to discover (and maybe 1 1/2 weeks of Lisp, before you ask!)

---

### Post by Kilon on 2009-02-02
> **maximinus_uk said:**
> I think it would be very very hard indeed  to credit 'the most optimal tool'. Firstly, what metric are you testing with? Least LOC? Most human-readable? Quickest to type out? Least prone to errors?



I do not think it is hard at all. As matter of fact it is very easy , you take most of the areas that computer languages are you used for, you see how the language provides solution to the problem and then compare with relevant approaches of other computer languages. Then you put a grade , and then you add up and divide all the grades to find the average . If the average is pretty high then the language is "optimal for any kind of task" if it is not then it is not optimal at all. 

Very easy.

---

### Post by maximinus_uk on 2009-02-02
> **Kilon said:**
> I do not think it is hard at all. As matter of fact it is very easy , you take most of the areas that computer languages are you used for, you see how the language provides solution to the problem and then compare with relevant approaches of other computer languages. Then you put a grade , and then you add up and divide all the grades to find the average . If the average is pretty high then the language is "optimal for any kind of task" if it is not then it is not optimal at all. 

Very easy.

The hard part is how you grade. If the 2 of us are going to come to some agreement on 'the most optimal language for a given task X' then we need to have some metric which we both agree on for all problems, and that is not trivial.

If I was to compare "kilons quicksort" with "maximinus's bubble sort" I could *prove* that your quicksort was a better solution because we can measure the amount of computations involved. With a language, what are we comparing?

---

### Post by mike_g on 2009-02-02
> Brainfuck is not a joke language. It answered a very real problem. The problem being: Create a Turing complete language for which you can write the smallest compiler possible. Brainfuck has been proven to be Turing complete and the compiler for it is less than 200 bytes.
Fair enough, it solved a problem, but it seems like a pointless problem to me. I cant see anyone doing anything useful with it.

---

### Post by maximinus_uk on 2009-02-02
> **mike_g said:**
> Fair enough, it solved a problem, but it seems like a pointless problem to me. I cant see anyone doing anything useful with it.

Actually, very (very!) simple languages are useful in genetic programming ([http://en.wikipedia.org/wiki/Genetic_programming]("http://en.wikipedia.org/wiki/Genetic_programming")) which is my particular field.

Since pretty much ALL code generated by this process is unreadable (like perl on acid), you may as well start with the simplest language you can get to make your code easier. After all, it's dead easy to implement brainfuck. Try and quickly implement Lisp!

---

### Post by Kilon on 2009-02-02
> **maximinus_uk said:**
> The hard part is how you grade. If the 2 of us are going to come to some agreement on 'the most optimal language for a given task X' then we need to have some metric which we both agree on for all problems, and that is not trivial.

If I was to compare "kilons quicksort" with "maximinus's bubble sort" I could *prove* that your quicksort was a better solution because we can measure the amount of computations involved. With a language, what are we comparing?

It could take some considerable time, but it wont be hard only time consuming because you will need to check many diffirent circumstances and problems. 

Pretty much as you do in math , compare and exam things that you can draw logical conclusions and those conclusion can apply in practice and give predictable results . 

One thing could be readability , amount of time it takes to complete a task, available resources , ability to be cross platform etc. etc.

---

### Post by maximinus_uk on 2009-02-02
> **Kilon said:**
> Pretty much as you do in math , compare and exam things that you can draw logical conclusion and those conclusion can apply in practice and give predictable results . 

One thing could be readability , amount of time it takes to complete a task, available resources etc. etc.

Define 'readability'. Is &#20320;&#22909;&#12290;&#25105;&#26159;&#33521;&#22269;&#20154; readable to you? Because it is for me. I would think that the only things you could be rigourous about would be:

1: The speed of program execution, given a regular input
2: The byte size of the source code
3: The byte size of the program after compilation
4: Memory usage of the code

Anything else is subjective, and by 'optimal' I assume we mean 'ease of solving the given problem' which is highly subjective!

---

### Post by Kilon on 2009-02-02
> **maximinus_uk said:**
> Define 'readability'. Is &#20320;&#22909;&#12290;&#25105;&#26159;&#33521;&#22269;&#20154; readable to you? Because it is for me. I would think that the only things you could be rigourous about would be:

1: The speed of program execution, given a regular input
2: The byte size of the source code
3: The byte size of the program after compilation
4: Memory usage of the code

Anything else is subjective, and by 'optimal' I assume we mean 'ease of solving the given problem' which is highly subjective!

Readability is not difficult to define at all. It the resemblance with English language ( I do not think you will find computer languages written in Chinese or other asian language  any time soon). Readability also means that the source is easy to read, which can be for various reasons like , lines of code, good commenting , good structure etc. etc.

---

### Post by CptPicard on 2009-02-02
> **maximinus_uk said:**
> I think it would be very very hard indeed  to credit 'the most optimal tool'. Firstly, what metric are you testing with? Least LOC? Most human-readable? Quickest to type out? Least prone to errors?

IMO the requirement for a hard metric is also a way to just simply avoid the big issue... there probably is no hard metric for the question itself, but what you mention there are side-effects and outcomes of using the optimal language. The optimal language probably is concise in terms of LOC, it is human-readable (not in the COBOL sense I hope), because of those things it's fast to type out, and because it "makes sense", it helps you avoid errors.

In the end, one just needs to rely on experience and the "feel" of the language... I willingly admit that it is hard to exactly quantify what it is in Lisp that makes it more suitable for "problem-solving in general" than, say, machine code. It has something to do with "expressing abstract concepts better". You need to practically execute the asm in your head using the model of the machine to "see what it does", while in Lisp you can *look at what is being said**right there in code. And not only that, Lisp does this also by using computationally relevant concepts, and does not simply supply a library saying "do X by calling Y".

> 
I think there are 2 steps; there is *the language in which you find it easiest to solve the essential problem*, which could one of many really, depending on the problem at hand.

IMO if the problem/algorithm is so relevant to choice of language then we already run the risk of moving towards problem-specific languages and away from general-purpose languages... the optimal language is one where you find it easiest/most efficient to express a solution to a problem in general. Programming-abstractions really exist on their own and by putting them together you get solutions to specific problems. This is why languages where you have strong base abstractions and a flexible way of combining them are close to the optimal language in my worldview...


> Something that normally needs as much CPU speed as you can get. But I needed to see what actually worked first, and the easiest answer to that was Python.

I know the feeling, I do that all the time. But I don't really consider running time to be such an important issue when considering what things are good from a programming language design standpoint. I mean, if you could have ignored just simple speed, don't you think that it is possible that your GA in Python would not have been an ugly hackfest?

---

### Post by maximinus_uk on 2009-02-02
> **CptPicard said:**
> ....if you could have ignored just simple speed, don't you think that it is possible that your GA in Python would not have been an ugly hackfest?

If it wasn't for the speed issue, my python code would read like Shakespeare ;)

When I have a hard problem to conquer I often think to myself 'If I only had an hour to get this working, what would I do?'. I then spend an hour coding. When finally it all works I make it look nice - i.e. I brute force the problem first *then* I make it a bit nicer.

Sometimes you look at code and think 'good lord, it's consing like crazy!' but then again you think 'but it's working like clockwork' and relax a little.


I do agree that the whole issue of 'optimal' is mainly down to experience and feel though. It's highly subjective, but I do think there's more to it than just being Turing-complete. It's just so very easy (why don't we all use brainfuck?!) and so very hard to pinpoint at the same time!

---

### Post by aj_ on 2009-02-02
CptPicard, I read much of those threads you linked, and now I am more confused than ever. Do people stubbornly cling to C because they believe procedural programming is superior to OO, or as a result of some romantic notion that C is the one true language? I decided on C++ as my first language mostly because I was susceptible to the argument that the OO approach is necessary as programs become larger and more complex. I also wanted to learn a bit about what was going on under the hood, so I opted against interpreted languages.

So the real pertinent question in all this is is not whether C is dying or not, but if procedural programming is. Is a beginner doing himself a disservice by starting out with the C approach? And if so, why do I see so much C++ hatred on this and other forums? What other OO language is there that forces you to at least have a basic notion of what is going on behind the curtains? Shouldn't every programmer know what is happening at the memory/registers level?

---

### Post by maximinus_uk on 2009-02-02
> **aj_ said:**
> CptPicard, I read much of those threads you linked, and now I am more confused than ever. Do people stubbornly cling to C because they believe procedural programming is superior to OO, or as a result of some romantic notion that C is the one true language? I decided on C++ as my first language mostly because I was susceptible to the argument that the OO approach is necessary as programs become larger and more complex. I also wanted to learn a bit about what was going on under the hood, so I opted against interpreted languages.

So the real pertinent question in all this is is not whether C is dying or not, but if procedural programming is. Is a beginner doing himself a disservice by starting out with the C approach? And if so, why do I see so much C++ hatred on this and other forums? What other OO language is there that forces you to at least have a basic notion of what is going on behind the curtains? Shouldn't every programmer know what is happening at the memory/registers level?

Very simple answer: 'Behind the curtains' things are not OO. It is useful to know how code works at the register level, but not so easy to code there. OO techniques are useful, but coding for speed is not usually needed.

My advice: Learn C by all means. Learn OO from something else: Python, Ruby or even Javascript (even Objective-C, if you have too!)

---

### Post by Kilon on 2009-02-02
> **aj_ said:**
> 
So the real pertinent question in all this is is not whether C is dying or not, but if procedural programming is 

C and C++ is dead. Not dying. But because C/C++ is a huge programming language which has monopolized software for decades it will take some time till it shrinks to a minimum. Probably at least a decade. Like all things cannot last forever and it has been around for sometime , the world moves on to languages more adapt to modern needs. 

Should a beginner learn C or C++ ? I always said "why not?". C/C++ are not beginner friendly and never they were considered to be so , but there are loads of examples of beginners felling in love with either C or C++. But a beginner should take into consideration that C and C++ is no longer consider the same way as it was considered a decade ago and that is for a reason. Still C/C++ is  a highly useful computer language.

Should someone knows what happens under the hood ? My advice is to avoid it , it can be a huge waste of time. Knowing the inner workings of a computer wont make you produce more efficient code , also may lead  in doing things that are either useless or even harmful . I studied assembly for some time and then went on studying the whole "under the hood thing" , I really felt moving like a turtle. 

I took one step back from the whole situation and saw that I did not gain anything significant proportionate to the huge effort i was putting in understanding the whole low lever mechanics. I was almost terrified when I found out that I was not actually coding at all. Of course there are situation where knowing the "inner-workings" can help greatly and of course going low level can be loads of fun.

---

### Post by CptPicard on 2009-02-02
> **aj_ said:**
> or as a result of some romantic notion that C is the one true language?

Well, there indeed tends to be this kind of a romantic notion especially from those guys who just flat out deny for some reason anything else except C has a reason to exist other than to serve as a crutch. It's just a combination of idle boasting ("I am smart enough to code it all in asm") and inability to understand some of the high-level concepts ("what is a closure?", after hundreds of posts of arguing, no less).

The grossest misunderstanding usually has to do with imagining that C is somehow genuinely computationally more powerful than all the rest and then the other languages just build libraries in order to *hide* some of this power (that for some reason seems to be linked to machine-level details).

> So the real pertinent question in all this is is not whether C is dying or not, but if procedural programming is.

It's not dying, and it is a straw man to suggest anyone is saying it is. :) The whole point is that it seems to be the "there is only C" people vs. those who actually do something else, too, and appreciate it.

> Is a beginner doing himself a disservice by starting out with the C approach?

A total beginner? Hmm... yes, I would say so. C makes a pretty good second or third language though.

> And if so, why do I see so much C++ hatred on this and other forums?

Because for a lot of experienced programmers even, C++ introduces more complexity that is seen as unnecessary when it is compared to what it brings to the table. You really need to remember that C and C++ are rather different beasts, although their most general premise is the same.

> Shouldn't every programmer know what is happening at the memory/registers level?

Yes. But IMO every programmer should also be perfectly aware that for example lambda calculus, which "the other basic theoretical model of computation" (the other is the Turing Machine), has nothing to do with register/RAM machines, which is an equivalent model but with more "implementation detail".

When thinking about problem-solving with a program, I really never, never have thought of stuff in terms of registers, unless I am specifically implementing in terms of them. I do think a lot in terms of functions and how to apply them to transform some data items, though. Should be easy to decide what kind of approach has been more fruitful for me, then...

---

### Post by nvteighen on 2009-02-02
> **CptPicard said:**
> 
We want to solve problems and model "things" with computational concepts, and then express all that in the language. The fact that we have joke languages such as Brainfuck also proves that people can certainly understand when a language does *not* fulfill criteria for good general-purposeness... there has to be the opposite to this too :)

There you strike a very interesting point... I believe the best criterion is the efficiency that programming language shows in achieving the goal it was designed for (what I call "efficiency"). But also the goal is important.

For example: BASIC was designed as a general-purpose programming language for beginners and amateur programming. Did it achieve its goal? Sort of... just the "beginners" part because it failed miserably as a general-purpose language as it didn't support structured programming. So, two possibilities: change or peril. Some extended BASIC and there we had QBASIC, BASIC-A, GW-BASIC, VB, etc. But at the end, only VB survived and the rest died because they were no longer useful.

Artificial languages (which include programming languages) are a matter of efficiency. Esperanto was created because Zamenhof considered natural languages not to be "efficient" enough to be international languages and Interlingua, as an improved international language because Esperanto didn't work for some people... C was designed because a higher-level and portable langauge was needed for the UNIX project, Perl was created as a text-processing language... etc. etc. etc.

So, what's BF's goal? If it was to be the Turing-complete language with the smallest possible compiler, then it is just a language to satisfy a temporal, personal need. After that need is over, then it starts to search for a new goal or it perils... and now it serves as a joke language (Who uses it for a serious project? Why would you post a BF code? Possibly, just to annoy someone and have some fun).

---

### Post by aj_ on 2009-02-02
Ok, if I am to understand you all clearly, it would be counterproductive to learn C/asm unless I had aspirations to work at the kernel-level?

Why can't there be an OO language that is appropriate for systems programming? Are the OO features intrinsically 'high-level' (in terms of overhead)?

---

### Post by CptPicard on 2009-02-02
> **aj_ said:**
> Ok, if I am to understand you all clearly, it would be counterproductive to learn C/asm unless I had aspirations to work at the kernel-level?

It is probably never outright counterproductive to learn anything, but the big question is of course what your current level of expertise is, and therefore, what is the most efficient thing to learn next.

I would never tell anyone *not* to learn C/asm, and in particular out of anyone who is supposed to be a well-rounded hacker, I would expect knowledge of both. They are not conceptually "hard", but the pre-requisites are better learned in a higher-level language IMO. And after having learned them, it is time again to move somewhere else for further insight into what everything is all about. Getting intellectually stuck on the low level is what not to do.

> 
Why can't there be an OO language that is appropriate for systems programming? Are the OO features intrinsically 'high-level' (in terms of overhead)?

In some sense, yes... but OO is a rather general concept. You can do kind-of OOP in C, and I find that I usually end up hacking together some kind of OOP-system for anything in C that is non-trivial.  Then again I feel that C++ is such a beast exactly because it tries to provide higher-level functionality in a rather low-level context, and that there is some kind of mismatch there that is hard to bridge.

Now, garbage collection in particular is something that is a very good thing in a system that is very strongly object-oriented, because this way your objects have a much more independent lifecycle -- in a non-GC environment, some object is always responsible for cleaning up other objects (if they're on the heap... the other option is the object's lifecycle being tied to the stack ofc), and if you think of the way OOP was originally conceived -- objects sending each other "messages", it is much better to do away with explicit "go away now" messages that someone has to actually remember to send...

---

### Post by Cracauer on 2009-02-02
> **eye208 said:**
> C.


Great opener, but alas...

> **eye208 said:**
> 
Recently I heard someone say: "C is the rock upon which the church of IT is built."


Yeah, exactly. Kind of explains some of the mess, eh? :)

> **eye208 said:**
> 
And it's true. The vast majority of applications and libraries for Linux is written in C. Linux itself is written in C. C remains the most popular programming language, especially for open source projects. And by "popular" I mean: the most frequently _used_ one. You may hear lots of talk about languages such as Python for sure, but talk is not code. Check out your favorite applications. Which language was used to build them? There's a 95% chance that it wasn't Python.


Yeah, but hand-rolling your own hashtables every time you need them isn't good fun.

The reason why it's so popular is that the foundations (kernel, X11) has a C API. That's all.

> **eye208 said:**
> 
[January Headline: C is the TIOBE Programming Language of 2008!](http://www.tiobe.com/tiobe_index/index.htm)
[C dominated 2008's open-source project nursery](http://www.theregister.co.uk/2009/01/21/open_source_projects_08/)

You won't turn out to be one of those write-only forum users, do you?

---

### Post by Cracauer on 2009-02-02
> **aj_ said:**
> CptPicard, I read much of those threads you linked, and now I am more confused than ever. Do people stubbornly cling to C because they believe procedural programming is superior to OO, or as a result of some romantic notion that C is the one true language? 

But things like the Linux or FreeBSD kernel clearly use an object-oriented approach to their architecture. As does Gtk, for example.

They use C, but the thing is that if you hand-tinker small fragments of code enough it really doesn't add any overhead to roll your own OO in C.

That's what people don't understand: you can do OO programming in C, it just takes more time. For code that is being worked on very intensely line by line it's practical to just roll your own OO.

---

### Post by aj_ on 2009-02-02
> **Cracauer said:**
> But things like the Linux or FreeBSD kernel clearly use an object-oriented approach to their architecture. As does Gtk, for example.

They use C, but the thing is that if you hand-tinker small fragments of code enough it really doesn't add any overhead to roll your own OO in C.

That's what people don't understand: you can do OO programming in C, it just takes more time. For code that is being worked on very intensely line by line it's practical to just roll your own OO.

Suddenly, you've made everything much clearer. Thank you :).

I blame my C++ book that claims you have to 'unlearn' much of C to learn C++. I think that was the source of my confusion.

---

### Post by CptPicard on 2009-02-02
> **aj_ said:**
> 
I blame my C++ book that claims you have to 'unlearn' much of C to learn C++. I think that was the source of my confusion.

It is in some sense true. In order to write idiomatic C++ you really should avoid transferring all of your C habits...

---

### Post by aj_ on 2009-02-02
> **CptPicard said:**
> It is in some sense true. In order to write idiomatic C++ you really should avoid transferring all of your C habits...

I understand that it's true, but it made me think, stupidly perhaps, that OOP was unfeasible or undesirable in C.

edit: and I just noticed that you had talked about OOP in C in your previous reply. Don't know how I missed it.

---

### Post by CptPicard on 2009-02-02
> **aj_ said:**
> I understand that it's true, but it made me think, stupidly perhaps, that OOP was unfeasible or undesirable in C.

Actually I would go so far as to say that for a beginner OOP in C can be more illuminating and educational than OOP in C++. C++ really makes the whole concept seem much more complex than what it actually is. Add to that the marketers of OOP that we got with Java and all those buzzwords, and the fact that there are so many more design pattern books to sell with Java/C++ style languages, because there are more OOP problems to actually solve with those languages.. (why this is so, is something worth thinking about)

---

### Post by eye208 on 2009-02-03
> **Cracauer said:**
> Yeah, but hand-rolling your own hashtables every time you need them isn't good fun.
[http://freshmeat.net/projects/libghthash/](http://freshmeat.net/projects/libghthash/)

---

### Post by maximinus_uk on 2009-02-03
Going back to optimal languages, I had a think about this morning over my coffee.

Firstly imagine the N-dimensional set of all possible outputs for your language (I believe this to be an countable infinite value). Now imagine another M-dimensional set, every single possible program for a given language (for most languages, this again would be a countable infinite number).

In both sets, you can define how far apart two members of a set are. Eg.

```
print "Hello"
print "Hello!"
```

are very close, compared to

```
print "Hello"
a=b^3
```

Are far apart. You can also map the difference between the outputs, close:

```
4
6
```

Or far apart:

```
3.141
Hello, World!
```

Now I believe that more optimal languages are less brittle to changes in code. So a small change in an optimal language will be closer to the output than that of a small change in a brittle language.

If you look at brainfuck or machine code, small changes in the original code can wildly change the output. This is less so in languages like Python or Lisp.

Now you may reason 'how the hell do you check this crap'? But I've studied genetic programming, where essentially you let the computer evolve code to a correct answer. Big problem is you have to build a language to run in a VM, so to start with I invented a real simple version of machine code. It didn't work because although I could evolve solutions to small problems, changing the code given to the VM just slightly caused the code to break regularly.

When I wrote a variant of Lisp for this task however, evolution became easier because the language itself was less brittle; and it didn't make any real difference what the problem domain was.

However, I don'y know wether this is quantifiable or even correct, I'm just floating out ideas here.

---

### Post by CptPicard on 2009-02-03
> **maximinus_uk said:**
> When I wrote a variant of Lisp for this task however, evolution became easier because the language itself was less brittle; and it didn't make any real difference what the problem domain was.

I am not surprised... I guess you were essentially evolving abstract syntax trees which are much more robust to GP-style changes instead of machine code which breaks violenty with smallest change. It is an interesting idea you've got there... it does somehow tie into the language expressing the concepts that are there in the problem instead of how to compute the result using the machine. The computational procedure is easy to break, the the concepts just get rearranged but they are still valid higher-level concepts.

---

### Post by nvteighen on 2009-02-03
> **maximinus_uk said:**
> 
Now I believe that more optimal languages are less brittle to changes in code. So a small change in an optimal language will be closer to the output than that of a small change in a brittle language.

If you look at brainfuck or machine code, small changes in the original code can wildly change the output. This is less so in languages like Python or Lisp.

Hmm... Ok, but that's from a computational point of view. From a linguistic point of view (which is what I can talk about more or less), the output is irrelevant, as you interpret the source code and it's that which is written in the programming language.

So, a small change in Python will probably not change the output a lot (e.g. change a + for a -), but the code may be semantically totally different.

From a linguistic point of view, the optimal programming language would be the one able to perfectly map the human's concepts into a semantical system of verbal symbols. The problem is that such a language would be a natural one and therefore, a non-specialized language... Artificial languages are specialized for some task besides concepts communication, so they're created that way that they achieve some goal, usually by losing a lot of the expressiveness natural languages have. So, this what we could call the "artificial language paradox": the best artificial language would be a natural one.

> However, I don'y know wether this is quantifiable or even correct, I'm just floating out ideas here.

That's the idea. Me too! :D

---

### Post by Reiger on 2009-02-03
> **nvteighen said:**
> From a linguistic point of view, the optimal programming language would be the one able to perfectly map the human's concepts into a semantical system of verbal symbols. The problem is that such a language would be a natural one and therefore, a non-specialized language... Artificial languages are specialized for some task besides concepts communication, so they're created that way that they achieve some goal, usually by losing a lot of the expressiveness natural languages have. So, this what we could call the "artificial language paradox": the best artificial language would be a natural one.

That's not quite true. You of all people, being a linguist, should know that if there is something humans often fail at; it would be expressing their thoughts in a natural language (and often their mother tongue at that). :)

Natural languages tend to have this very, very, nasty feature called "figures of speech", and worse: ambiguity. It is ironic that if we are to agree a natural language is the best for mapping complex patterns of thought called algorithms to complex sub-patterns of though called sub-algorithms (because that is all you ever do when programming anyway) we should acknowledge that C++ with its 'undefined behaviour' nicely captures the essence of 'natural languages'. ;)

---

### Post by Kilon on 2009-02-03
> **Reiger said:**
> That's not quite true. You of all people, being a linguist, should know that if there is something humans often fail at; it would be expressing their thoughts in a natural language (and often their mother tongue at that). :)

Natural languages tend to have this very, very, nasty feature called "figures of speech", and worse: ambiguity. It is ironic that if we are to agree a natural language is the best for mapping complex patterns of thought called algorithms to complex sub-patterns of though called sub-algorithms (because that is all you ever do when programming anyway) we should acknowledge that C++ with its 'undefined behaviour' nicely captures the essence of 'natural languages'. ;)

I do not buy this .... 

For me intelligent VMs are the way to go.  "ambiguity" is not only something  not to be avoided but also pretty much where future is and what makes human intelligence so important. The ability to perceive something in "general terms" is crucial for flexible decision making. 

No C++ in that area , is still anchored to the past .

---

### Post by nvteighen on 2009-02-03
> **Reiger said:**
> That's not quite true. You of all people, being a linguist, should know that if there is something humans often fail at; it would be expressing their thoughts in a natural language (and often their mother tongue at that). :)

Natural languages tend to have this very, very, nasty feature called "figures of speech", and worse: ambiguity. It is ironic that if we are to agree a natural language is the best for mapping complex patterns of thought called algorithms to complex sub-patterns of though called sub-algorithms (because that is all you ever do when programming anyway) we should acknowledge that C++ with its 'undefined behaviour' nicely captures the essence of 'natural languages'. ;)

Why is ambiguity considered a flaw in natural languages? It's just there: languages are not meant to be logical, they are meant to communicate. And even being ambiguous, people can communicate with each other perfectly the most of the time. "Figures of speech" are there as a natural expressive resource and be careful: these are not restricted to poetry. Why do we relate "high" to "good" (e.g. in "high quality")? That's a metaphor, which is a very productive lexical mechanism... There are also metonimical patterns... one is eponyms: why do we call Morse to that thing Samuel Morse invented? All these tend to economy: express more in less.

What I said is that artificial languages specialize themselves by losing expressiveness and not taking account of all the abstraction power the human language has to offer. Because if it tried to be absolutely expressive, then it would not be specialized.

---

### Post by Reiger on 2009-02-03
I don't think ambiguity is a _flaw_ per se; but if you want to map out algorithms you pretty much require a well-understood definition of what you are doing. Hence, for instance, why Mathematical proof (valid proof) can be so darned tricky to write down. 

Ambiguity kind of spoils the fun (or it is where the fun begins) when you realise a certain program does not work (a certain message is not received as intended) because of ambiguity; one of the best examples of how ambiguity can lead to unwelcome results is the 'bad joke'. 

Figures of speech create ambiguity, because the semantics of the sentence cannot be fully appreciated unless the figure of speech is _recognised_ and it is perfectly possible for a figure of speech to be perceived even when it is not intended.

So this is why I do not think that a full fledged natural language works out so well in practice. And I would not be surprised if similar considerations lay at the heart of jargon.

---

### Post by deepclutch on 2009-02-04
why C++ recommended whenever the mention of C ?C is still useful.

---

### Post by Wybiral on 2009-02-04
> **maximinus_uk said:**
> After all, it's dead easy to implement brainfuck. Try and quickly implement Lisp!

Lisp is a ridiculously simple language to implement... Go read [SICP]("http://mitpress.mit.edu/sicp/").

---

### Post by CptPicard on 2009-02-04
> **Wybiral said:**
> Lisp is a ridiculously simple language to implement... Go read [SICP]("http://mitpress.mit.edu/sicp/").

+1

Actually, whenever you need some kind of internal language -- think "evaluatable data structures" -- it is likely to essentially be a lisp, even though you were not intentionally aiming for one. Thus, [Greenspun's Tenth Rule]("http://en.wikipedia.org/wiki/Greenspun%27s_Tenth_Rule").

No wonder GCC's intermediate representation is a CPS lisp. Think about it -- GCC transforms everything from any front-end to a lisp first, then mangles that for optimizations etc, and then that is serialized into machine code at the back-end. Now, this seems like a strong endorsement for lisp being the ultimate language :)

---

### Post by maximinus_uk on 2009-02-04
> **Wybiral said:**
> Lisp is a ridiculously simple language to implement... Go read [SICP]("http://mitpress.mit.edu/sicp/").

Mmmmm.... Well I've implemented a few languages in my time, including Brainfuck and a lisp.

I'll agree that the parser and lexer for a lisp are trivial but from then on it starts to get a little tricky. Things are garbage collection are quite complex topics in themselves.

Now Brainfuck, that really *is* trivial to implement. I reckon you could do in 5 minutes easily.

---

### Post by fiddler616 on 2009-02-04
Back to optimal languages:
I feel like it boils down to coding for flexibility vs. coding for expressiveness, both of which have merits.

---

### Post by Wybiral on 2009-02-04
> **maximinus_uk said:**
> Mmmmm.... Well I've implemented a few languages in my time, including Brainfuck and a lisp.

I'll agree that the parser and lexer for a lisp are trivial but from then on it starts to get a little tricky. Things are garbage collection are quite complex topics in themselves.

Now Brainfuck, that really *is* trivial to implement. I reckon you could do in 5 minutes easily.

Well, you don't have to implement a garbage collector yourself if you're implementing lisp in a language that has garbage collection :) Or you could use a GC library to handle that for you, that's not really part of implementing the actual language. What constitutes the language for me is expression evaluation, which for lisp is exceedingly simple.

But if you're implementing lisp specifically as a means of evaluating expressions (as I imagine you would be doing for what you said your intentions were), then no garbage collection is necessary at all... And neither is parsing (why generate the code when you can just build some list constructs at runtime and run them through an "eval" function that recursively applies cars to cdrs?)

Look, lisp...
```

def seval(expr):
    if isinstance(expr, tuple):
        return apply(seval(expr[0]), map(seval, expr[1:]))
    return expr

from operator import add, mul

print seval((add, (mul, 2, 3), 2))

```

---

### Post by Cracauer on 2009-02-04
Most people implementing simple interpreters either implement it in a language that's already GCed (cheaters :) or they use the Boehm GC.

Lisp != Lisp.

I don't like all these smallish Scheme implementations.

Implementing a moloch like Common Lisp is a little more challenging. Even parsing isn't that simple anymore. Reader macros can drive you nuts, then there quote, komma, backquote. Dot. &key &body. Oh my.

But hey it beats C++ :)

---

### Post by Wybiral on 2009-02-05
> **Cracauer said:**
> Most people implementing simple interpreters either implement it in a language that's already GCed (cheaters :) or they use the Boehm GC.

Lisp != Lisp.

I don't like all these smallish Scheme implementations.

Implementing a moloch like Common Lisp is a little more challenging. Even parsing isn't that simple anymore. Reader macros can drive you nuts, then there quote, komma, backquote. Dot. &key &body. Oh my.

But hey it beats C++ :)

Right, I was responding to someone who mentioned languages that are simple enough to use in genetic-programming, which Lisp is actually a very logical choice (considering it IS an expression tree).

But, common-lisp isn't "lisp" any more than clojure is "lisp"
And if you just need to implement a basic lisp expression evaluator, it's actually quite simple.

Extending that to use an environment isn't difficult at all... Then you make some basic primitives like "lambda"... It's an incredibly basic language at heart, it doesn't need all the special symbols and macro-jazz to be "lisp"

---

### Post by CptPicard on 2009-02-05
> **fiddler616 said:**
> 
I feel like it boils down to coding for flexibility vs. coding for expressiveness, both of which have merits.

IMO in an optimal language flexibility and expressiveness are the same thing...

---

### Post by maximinus_uk on 2009-02-05
Well I'm not going to argue the point, Lisp is easier to implement than a lot of other languages. I just checked and my 'lisp in python' is 1186 LOC, (not a great metric I know) so not *that* much code

The hard part comes from just writing all the built-in functions, and coping with all the edge conditions.

In my GP coding, it is very important that a program almost never crashes. For example, (/ 5 0) gives 5 in my lisp. This means another load of code you have to layer on to everything.

I contrast that with languages like Brainfuck, which I assume would be more like 20 LOC and implementable in about 5 minutes.

Of course, like many computer programs, most of the time you could classify them all as being 'easy to program' but what bogs you down is literally implementing it - all of it! - bug free ;)

---

