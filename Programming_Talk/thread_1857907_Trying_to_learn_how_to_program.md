---
title: "Trying to learn how to program"
date: 2011-10-11
forum: Programming Talk
---

### Post by orphanlast on 2011-10-11
I'm thinking about learning how to program stuff... In fact. I'm thinking about taking on a project that is probably bigger than I can swallow.

What's a good programming language that doesn't require a plug in for Windows (people keep suggesting python, but I had to install a plugin to run a program running python). I want a solid programming language. 

And if possible, what's a good compiler? I would really like to have a visual compiler. Something like Google App Inventor [http://www.appinventorbeta.com/about/](http://www.appinventorbeta.com/about/) ... again, if that's possible.

I'm so sick of hearing about a program and conceptualizing how it would work. And then I use it and realize "oh... it can't do this or this or this... I thought it did..." and then after about five years and five different new releases of the same program, they finally put those functions in and everyone calls them brilliant and revolutionary. I seriously think up this crap years and years before these people do. Why not make something to show them how its done.

---

### Post by searchfgold6789 on 2011-10-11
C and its variants - doesn't require a plugin necessarily and runs on Windows but hard to learn. I bet there are many tools out there to help your program using C, C# or C++. It's pretty much the "standard" program language and has been for a long time.

---

### Post by orphanlast on 2011-10-15
I've been researching high and low for a compiler or IDE similar to Google app inventor and the closest thing that I can come up with is Microsoft Visual C++. And yet is still seems to fall short.

Has anyone ever given any thought to making something like this for PC's? Are there any suggestions people might have for something like this out in the current market? Is anyone working on something like this as a fun pet project?

I think there'd be a high demand for it. If someone doesn't jump on it now, I guarantee eventually people are going to and when it does, it's going to be big.

---

### Post by 3rdalbum on 2011-10-15
Runtime Revolution. Not free, but "compiles" to multiple platforms and uses a language similar to Hypertalk (from Apple's Hypercard). Has an interface designer.

It's a little bit lower-level than App Inventor, because you do write code in Runtime Revolution, but it's very easy to write in.

---

### Post by CptPicard on 2011-10-15
You already have a few concepts rather wrong or at least you call them by odd names. A "plugin"? Do you mean the Python interpreter?

And calling Google App Inventor a "compiler"... well, it's some sort of an IDE-style application building environment.

IMO, many beginners have this odd idea that they must have a "solid" language that does not require a runtime; and then they seem to be accepting something much more than the Python runtime they just shunned.

It is the old strange attitude that sometimes manifests itself in the idea that the closer to the hardware you are, the more "real" your programming is, and that as a beginner you'll be a Real Man if you just try to start all the way from the bootloader, as if it really teaches you something of value.

A beginner is not going to be learning valuable things fast starting from C. This is not to even say that C is particularly incredibly "hard"; it's just "hard" in a non-helpful way -- that is, there is lots of nitty-gritty that gets in the way of gaining an understanding of the big picture of programming. It is, in my view, far easier to dig down from the large scale than vice versa, as the low level details are just specifics of architecture and so on, and not the big huge truths that apply across all programming.

So I would say you just stick to Python, it's a very good starting point. May want to take a look at Java or C# as well; and if you're really adventurous, Scheme.

---

### Post by orphanlast on 2011-10-15
> **CptPicard said:**
> You already have a few concepts rather wrong or at least you call them by odd names. A "plugin"? Do you mean the Python interpreter? 

Yes

>  And calling Google App Inventor a "compiler"... well, it's some sort of an IDE-style application building environment. 

After doing a bit more research I figured that out, my second post is a little more knowledgeable about that.

> I would say you just stick to Python, it's a very good starting point. May want to take a look at Java or C# as well; and if you're really adventurous, Scheme.

Thanks -- I've been thinking for a little while and blender is made with Python. So it does have some diversity. But would it not help to have an IDE to at least assist or shortcut some steps? Especially as a crutch for someone starting out until they can stand on their own. Because it helps to be able to see something get developed as you're learning. Otherwise it can feel like you're just at a freakin' stand still and that's just frustrating.

If you think it'd be of any assistance, what Java based IDE would you recommend?

---

### Post by Zeta-K on 2011-10-15
Read this first:
[http://www.hellboundhackers.org/articles/884-selecting-your-first-programming-language.html](http://www.hellboundhackers.org/articles/884-selecting-your-first-programming-language.html)




Then one of these if applicable:

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

[http://download.oracle.com/javase/tutorial/tutorialLearningPaths.html#newtojava](http://download.oracle.com/javase/tutorial/tutorialLearningPaths.html#newtojava)

[http://cpp-tutorial.cpp4u.com/](http://cpp-tutorial.cpp4u.com/)

---

### Post by CptPicard on 2011-10-15
> **orphanlast said:**
> 
Thanks -- I've been thinking for a little while and blender is made with Python.

Blender probably uses Python as some sort of scripting/UI language, but it would be impossible to actually write the rendering stuff in Python... too slow. The core stuff is probably C. But this does not mean that C is in some sense "more powerful" than Python... it just means that it compiles down to faster execution, so in a case where you need the speed, you'd prefer C. The actual problems in code are the same; you just need to start using a language that requires more drudgery if execution speed is a requirement.

> But would it not help to have an IDE to at least assist or shortcut some steps? Especially as a crutch for someone starting out until they can stand on their own.

It depends... IDEs are very useful for languages with more "ceremony" such as Java. I do like having the ability of the IDE to tell me what some object can do, and the ability to automatically refactor, etc.

But it could also be argued that these functions of the IDE are both enabled and *made neccessary* by the character of the language. In Python you need much less verbose declaration in the first place. This means that Python code is easier to work with as there is less of it; on the other hand, the IDE does not have as much stuff in the language to work with to help you. But, in the end, you might need "less help" from the IDE with a language like Python!

The runtime environment in Python is very useful btw... get used to the interactive shell. There is nothing like it in compiled languages.

> 
If you think it'd be of any assistance, what Java based IDE would you recommend?

Well it's either Eclipse or Netbeans of course. Both have their adherents. I use Eclipse professionally every day, but personally prefer Netbeans; its integration to the various tools is just beautiful, but Eclipse of course has more plugins... which tend to break alarmingly often.

---

### Post by thatguruguy on 2011-10-15
Personally, I'd still suggest Python.

Yes, you have to install the Python interpreter to use it on Windows.  However, your users don't, because there is the [py2exe]("http://www.py2exe.org/") extension which will create a regular distributable Windows .exe out of the program to make in Python.

---

### Post by Zeta-K on 2011-10-15
I personally love Python. It's useful when you need to quickly write a tool, but it doesn't necessarily have to be resource-efficient. For an example of an entire program written in Python, look at Frets on Fire. That's not how you'd generally use Python, however.

---

### Post by CptPicard on 2011-10-15
> **Zeta-K said:**
> Read this first:
[http://www.hellboundhackers.org/articles/884-selecting-your-first-programming-language.html](http://www.hellboundhackers.org/articles/884-selecting-your-first-programming-language.html)

The article succumbs to a lot of the fallacies regarding the differences between low- and high-level languages though. Just consider the "you lose speed and power but..." kind of attitude... yes, C executes faster. It's also somewhat uninformative about the higher-scale structure of programs. You'd have to essentially write an interpreter from ground up to get the stuff in higher-level languages, and in particular a n00b is not going to do that. It's much better to start with a higher-level language, which both expose you to nearly all of the stuff in the lower-level languages, plus directly to the things that are possible in a programming language.

At least they recognize that in higher-level languages you can get "some uncommon things done" -- what is actually possible in a programming language if you're not tied to the hardware as tightly as possible, is impressive -- just think of continuations, for example. 

> **thatguruguy said:**
> 
Yes, you have to install the Python interpreter to use it on Windows.  However, your users don't, because there is the [py2exe]("http://www.py2exe.org/") extension which will create a regular distributable Windows .exe out of the program to make in Python.

It's such a huge pity Windows does not have a proper dependency management system like Linux does.

---

### Post by orphanlast on 2011-10-15
Hey thanks for the help.

---

### Post by nvteighen on 2011-10-15
There's something I wanted to add to CptPicard's contribution.

Be also aware that the little programs you'll be doing when learning your first steps will be that simple that the speed advantages C or C++ give you will be of no use for you and force you to do things that are meant to make the program faster when you actually don't need that at this stage (I'm thinking specifically about static typing).

IMO, this is an important point, because people like CptPicard or me use to argue in favor of using a high-level language as first language for theoretical reasons, but there is also this very practical reason too. Learn the general concepts of programming (variable, loops, basic algorithms, abstraction into data and procedures) which you'll use in all languages and then you should be able to learn the specifics of low-level programming.

Not that the opposite is not possible, but at least from our experience with people in these forums, what CptPicard or I propose has had its good results.

---

### Post by orphanlast on 2011-10-16
Yeah -- I've found some good material. However I've found that the IDLE that's actually on the Python website doesn't assign a numeric value to each line that you're typing. I'm not even sure if that could be considered a "compiler" but I understand that maybe an IDE might not be the best step right now -- but is there possibly a more comprehensive "compiler" (if that's what the IDLE is) that I could use. One that highlights errors as your typing (for example) assigns numeric values to each line you're typing. One won't just continue writing on one singular line forever if you're making a #comment but make the line thicker than the others, and give better instructions for why something won't launch?

---

### Post by llanitedave on 2011-10-16
For Python, you can use fairly basic text editors such as gedit or Kate -- they'll supply line numbers.  There are also dedicated Python editors such as SPE, Eric, and BoaConstructor, of which I prefer SPE of the three.

For myself, I use Geany -- it's pretty straightforward and has all the necessary features for Python, although it's a general purpose IDE.  The more complex and fancy IDEs that have been mentioned here, such as Eclipse and Netbeans, and some that haven't such as EMACS, are also all Python capable.

So don't let a dissatisfaction with IDLE hold you back.

---

### Post by juancarlospaco on 2011-10-16
Use Python and [http://www.ninja-ide.org](http://www.ninja-ide.org)

---

### Post by orphanlast on 2011-10-16
Oh yeah. I have Blender too. It seems like with each release the program keeps looking better and better, however, that doesn't mean I'm any closer to understanding the thing.

---

### Post by 11jmb on 2011-10-17
I think that a lot of you guys are leaving out one important point about C/C++ as a first language: it requires you educate yourself about whats going on "under the hood"

there are different goals to keep in mind: yes, if you want to get up and running in a short amount of time, programming useful and fun applications, Python is certainly a great option. If, however, you are looking to put some serious time into it and learn how to be a strong and versatile programmer, I would suggest turning towards C (and then C++ when you are ready to learn about OO)

There is more to C than just speed. It is a great teaching tool

---

### Post by PaulM1985 on 2011-10-17
> **11jmb said:**
> I think that a lot of you guys are leaving out one important point about C/C++ as a first language: it requires you educate yourself about whats going on "under the hood"

there are different goals to keep in mind: yes, if you want to get up and running in a short amount of time, programming useful and fun applications, Python is certainly a great option. If, however, you are looking to put some serious time into it and learn how to be a strong and versatile programmer, I would suggest turning towards C (and then C++ when you are ready to learn about OO)

There is more to C than just speed. It is a great teaching tool

Knowing what is going on is useful and C & C++ are very important languages to know when it comes to the world of work, but I think for a person who is going to teach themselves there are too many things that are going to get in the way of learning with those languages.

If you make it very difficult to get going, you will experience a high drop out rate.  I think getting started is important, then afterwards you can go indepth on what is happening underneath.

Paul

---

### Post by 11jmb on 2011-10-17
> **PaulM1985 said:**
> Knowing what is going on is useful and C & C++ are very important languages to know when it comes to the world of work, but I think for a person who is going to teach themselves there are too many things that are going to get in the way of learning with those languages.

If you make it very difficult to get going, you will experience a high drop out rate.  I think getting started is important, then afterwards you can go indepth on what is happening underneath.

Paul

I agree, and I think the "top-down" approach of using a language like Java or Python is very useful. I just wanted to point out to the thread that C would be a great next step in the learning process once a basic understanding has been developed.

---

### Post by 11jmb on 2011-10-17
Also, to further explain what I said about C being a good 1st language, that is directed at somebody who is at least 95% sure that he/she wants to be a real programmer.

If you are unsure or just want to learn something fun and interesting, then my vote goes to Python as well

---

### Post by CptPicard on 2011-10-17
> **11jmb said:**
> Also, to further explain what I said about C being a good 1st language, that is directed at somebody who is at least 95% sure that he/she wants to be a real programmer.

If you are unsure or just want to learn something fun and interesting, then my vote goes to Python as well

Oh, *the real programmer* argument. ;)

I would like to point you over to [the low-level vs. high-level language thread]("http://ubuntuforums.org/showthread.php?t=851794") that is an old classic on this subject so that one doesn't need to rehash everything that was said back there, back then. It's a sufficiently long treatment on this as it is :)

But putting it briefly; C is not in any sense any more "real" programming than Python is. There is a Turing-complete language that could be running on top of any kind of hardware, and then what you do is apply the tools given by that language to solve a problem. All such languages are theoretically equally strong; they just give you different kinds of ways to give general descriptions of computational things. A lot of very interesting computational "things" are only describable in higher-level languages, and anyway, they remove a lot of the dull, intellectually mostly uninteresting machine-handleable stuff.

Most importantly, lower-level languages' "under the hood" picture does not really "inform" the higher-level picture. At its extreme I could give you a long line of ones and zeroes, and you couldn't make heads or tails of it. It tells you absolutely nothing of the program. On the other hand, higher-level languages' more descriptive structures really mold your view of the problem; I find that when I do have to do the work of writing things in languages like C or even the relatively high-level Java, I architecture around the patterns that are more easily discovered in HLLs, although the actual language features might not always be present. Sometimes they can be emulated somehow.

In the end, if you insist on coding in terms of a C-like language, Python allows that too. It won't be particularly pretty Python though ;)

That said, the only sense in which I would subscribe into the "real programmer" argument is the one where you really need to be able to handle various programming languages without getting stuck on the particulars of the language. You'd be surprised how intellectually rewarding and challenging in particular the higher-level languages are simply because of the concepts they contain, and how much they help in developing this kind of language-agnostic mental abstraction of programming.

---

### Post by karlson on 2011-10-17
> **PaulM1985 said:**
> If you make it very difficult to get going, you will experience a high drop out rate.

Learning to program without learning the theory leads to the glut of software developers akin to the Internet boom.  C, C++, Java that requires a developer to think about types, data structures, etc.

Python while a good language hides a lot of things from you that are important to understand.

> I think getting started is important, then afterwards you can go indepth on what is happening underneath.


Problem is a lot of people don't.

But I think that this is a discussion for a different thread.

---

### Post by 11jmb on 2011-10-17
Jean Luc,

Just to be clear, I LOVE programming in Python. It is a phenomenal language, and it is a lot of fun. Also, you are 100% right when you say that high-level languages are better for teaching the broad concepts of computer science.

On the other hand, I think it is just as important to know how your program behaves as "a long line of ones and zeros" which, I argue, is best learned through experience programming in C and assembly.

When I used the term "real programmer" I did not intend to tie that phrase to a specific language. A great programmer needs to understand his/her code, be it 100 lines of Python or 500 lines of C, and know how the computer is going to handle it.

I believe that too much abstraction inhibits learning. As another example, it is better for a physics student to learn calc/diffeq than to just memorize a bunch of equations without being able to derive them.

---

### Post by digrejzo on 2011-10-17
uhm, hello guys!

for those tl;dr guys, skip the next paragraph.
I somewhat thought I could benefit from a thread like this, but then you guys started the whole approach to programming and semantics, which doesn't really answer my question.
the thing is, I'm studying Librarianship and Information Science (Faculty of Philology) and we went through the basics of HTML/CSS, LaTeX, and now we're doing VBA and macros in general. I really don't see how I can benefit from VBA, but oh well. I always wanted to do something a bit more serious, so I am for, God knows which time (I hope it's the last), trying to find out which programming language to learn and make good use of the time spent learning. 

I have some knowledge of C++ (which I did in high school 2-3 years ago, and never tried it again, so it's a kind of a fresh start, but I still recognize the syntax etc), finished the [python "newbie" tutorial]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python"), I'm fairly good at HTML/CSS (which are not programming languages) and LaTeX, so I understand the basics of programming. a friend of mine recommended JavaScript, so I'm not sure which way to turn right now.
should I continue the python, maybe learn basics of JS and work my way from there, or go back to C++ or maybe something else?

I really love how python works, and its' ease of use.
basically, I wanna create GUI applications, from basic "guess a number" to something more complex. sorry for the whole "life story" part of the post, but it's only for the purpose of clarifying my problem.

cheers!

---

### Post by 11jmb on 2011-10-17
Thank you for clarifying your problem :) it makes answering your question much easier.

I would say Python for somebody like you. JS is very specific to web development, where Python is much more versatile. Based on your needs, a top-down learning approach will be useful because you can learn how to develop working products in less time. After a year or two of experiences with high-level programming, though, don't be shy about learning some C if you are interested.

---

### Post by karlson on 2011-10-17
> **digrejzo said:**
> uhm, hello guys!

for those tl;dr guys, skip the next paragraph.
[snip]
I have some knowledge of C++ (which I did in high school 2-3 years ago, and never tried it again, so it's a kind of a fresh start, but I still recognize the syntax etc), finished the [python "newbie" tutorial]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python"), I'm fairly good at HTML/CSS (which are not programming languages) and LaTeX, so I understand the basics of programming. a friend of mine recommended JavaScript, so I'm not sure which way to turn right now.
should I continue the python, maybe learn basics of JS and work my way from there, or go back to C++ or maybe something else?
[snip]
cheers!

Usually to posts like this I would always suggest that before you start learning a programming language of any sort understand what your goals are.

The goal of "I want to write a GUI application" is great but what will this application do?  What are the requirements for it?  If all it will do is display "Hello" the user presses a button and the word changes to "World" then the choice of programming language becomes any language that can do this for you(Python, Perl, Java, C, C++, Haskell, etc).  If you are doing the same program for the web browser then PHP, JS, etc would be better..

If you choose to implement some sort of DB with GUI frontend where performance is not quite as relevant then Python is a good choice, but if you need to have something with Real Time network driven updates with millisecond response times on data updates with a GUI just to present this info and be able to freeze it in a snapshot then I would suggest Java but probably C or C++.

In most cases however I see these discussions seem to go in an opposite direction let's start with learning a programming language and then apply it to a task

Sorry for the rant but if Y2K and the Internet boom taught anyone anything that was that this was a wrong approach to learning...

---

### Post by nvteighen on 2011-10-18
> **11jmb said:**
> 
I believe that too much abstraction inhibits learning. As another example, it is better for a physics student to learn calc/diffeq than to just memorize a bunch of equations without being able to derive them.

I don't see how memorizing a bunch of equations is equivalent to too much abstraction. That's just stupidity.

When CptPicard, I myself or others speak of abstraction, we're taking for granted that programming is a "how-to" kind of knowledge, not of one the "what" kind (OMG, I've paraphrased Kant in an internet forum!?). This means that, unlike Physics, the abstraction isn't encapsulated in a set of declarations (equations), but in a set of building blocks you have to learn *how to use*.

In my particular POV of a linguist:

I've always said that programming languages have the specific feature of being languages with a highly productive "neological" system for creating new code-specific lexicons from the very small intial built-in lexicon. It's the huge degree of productivity which set them aside from natural languages (where such productivity would be counter-productive, as they're meant to be communication protocols, i.e. they have to be more or less stable but yet flexible). But in all other respects, learning how to program is equivalent to learn a language... you learn a syntactic component, you learn a lexicon and there's a semantic interface which is simulated by the computer, but could be your own mind too. That's why the comparison with learning Physics equations doesn't hold, IMO.

---

### Post by CptPicard on 2011-10-18
> **11jmb said:**
> 
Just to be clear, I LOVE programming in Python. It is a phenomenal language, and it is a lot of fun. Also, you are 100% right when you say that high-level languages are better for teaching the broad concepts of computer science.

And, in general, a kind of "mental mapping" of problems to code, because they have a broader, more refined and thought out toolkit of solution "patterns", if you will.

It is this "mindset" of programming that one wants to be learning when one is learning how to program, and that is why higher-level languages take you directly into it instead of you having to build it from the ground up -- which I do not even believe is in any sense likely to happen. It is not only that the learning curve is easier -- you generally develop the *end product* programmer's mind much faster with a high-level language. 

> 
I think it is just as important to know how your program behaves as "a long line of ones and zeros" which, I argue, is best learned through experience programming in C and assembly.

This is more of a practical engineering need on a specific architecture. It's not that the view isn't valid, but I have always taken a more abstract (that is, less physically concrete, not "dumbed down" as it is often misunderstood) "programming languages as program descriptions" view.

The ones-and-zeroes form is just another take on formulating computations, and it's a particularly unhelpful one for humans at that.

> 
When I used the term "real programmer" I did not intend to tie that phrase to a specific language. A great programmer needs to understand his/her code, be it 100 lines of Python or 500 lines of C, and know how the computer is going to handle it.

I agree with the first part, and somewhat with the second. In particular, a great programmer is going to view whatever he is working on not in terms of the language he has at hand, although it constrains his immediate choices, but in terms of how he sees the problem's structure in his head and how that maps into whatever language he is using. Languages that encompass more patterns like this are more effective at building the mental model; how to implement those patterns in languages that lack the immediate facilities follow more easily than I guess you think, especially after you have some *very* general language such as Lisp under your belt -- it's essentially an interpreter-writing language.

> I believe that too much abstraction inhibits learning. As another example, it is better for a physics student to learn calc/diffeq than to just memorize a bunch of equations without being able to derive them.

Nvteighen's points were good, but let's give it a go...

No, it's not about rote learning and just doing things "without understanding". It is a common misconception that HLLs somehow just give you things you "memorize" and then you blindly type stuff into the machine and it does magic. Specifically, you claim that the lower-level languages somehow tell "how it *really* works" and that is then supposed to inform the programmer "more deeply" about what is being coded.

This is wrong; I'm going to offer a somewhat strong version of the thesis that I've been evolving here in these debates in the past five years.

Programming languages are more equivalent than makers of this claim appreciate. The underlying machine architecture genuinely *does not matter* one bit in the big picture; it could be hamsters running on wheels, connected to some machine-translateable mapping into any human-interface-language. 

A corollary to this that all programming languages require the same sort of human input we need to fill the gap between computers programming themselves and what we have now. The variable that we can work on is the representation of the language; and while we juggle that variable around, we're remarkably free to choose between representations while remaining equivalent in the sense that the underlying machine could be anything that is also computationally equivalent (Turing-complete).

One has to also realize that the creation of the mapping from the user-interface language to the actual physical implementation is a *one-off* problem which is well understood in interpreter and compiler theory; the result is a *general purpose* programming language that can solve *any* problem. 

So because there is this barrier between the low and the high levels saying that it could be *anything* down there (it could be Javascript interpreting your C), and you still can achieve everything programming languages (theoretically speaking) can, it is actually impossible that knowing of the low level of the architecture could in any sense inform you of how you should be structuring your program. This is why I am in general very skeptical of the claims that LLLs teach you how to do things better than HLLs because they "lack stuff", forcing you to implement the (one-off) mapping. HLLs actually *include* the LLL stuff, and then some -- and most importantly, those included things are not comparable to library calls that just do magic; they are genuinely building blocks you combine to achieve new ideas and concepts -- and those stick around for your mental usage later on.

---

### Post by 11jmb on 2011-10-18
> **CptPicard said:**
> The underlying machine architecture genuinely *does not matter* one bit in the big picture

Well i think I found the root of our disagreement :)

There are plenty of situations where developing towards a target architecture is necessary such as OS and embedded system development. 

Where we seem to disagree is that I believe that it is important for programmers to understand how this process differs from high-level development. 

This is certainly more of an engineer's world-view, and while the target architecture and runtime efficiency do not have to be a developer's sole focus, I think everybody should keep it in mind.

---

### Post by CptPicard on 2011-10-18
> **11jmb said:**
> Well i think I found the root of our disagreement :)

Yes, indeed... I am "willing to disagree" on this. I perfectly well understand that architecture-specific cases are... well, specific. When you are dealing with a particular problem, you deal with that problem. However, I'd hazard stating that the actual issues you'll deal even architecture-specifically are ones you would have confronted generally.

> 
There are plenty of situations where developing towards a target architecture is necessary such as OS and embedded system development. 


Which are special cases and as such not particularly interesting in the big picture. Most importantly, they do not "inform" the big picture, or, the HLLS.

> 
Where we seem to disagree is that I believe that it is important for programmers to understand how this process differs from high-level development. 

It seems to me that where we disagree is where I think where it is important for programmers to understand where it all just integrates; where there is no difference, but where just abstractly understanding rules. That's where it clicks. The low-level is not in any sense special in general unless we fix a particular architecture.


> 
This is certainly more of an engineer's world-view, and while the target architecture and runtime efficiency do not have to be a developer's sole focus, I think everybody should keep it in mind.

Well, Big-Oh runtime efficiency is in the end game the important part of anything when talking of this. Within hardware you can only squeeze out constants without algorithm-level insight; and when distribution and large-scale scalability becomes important, understanding what actually counts in the structure of the problem, is the important part.

---

### Post by JDShu on 2011-10-18
Wouldn't a C-like language give you better insight into memory allocation and usage? I've seen a question here where the implementation of cpython gave strange results only understandable if you have some idea of how memory management works.

---

### Post by karlson on 2011-10-18
> **JDShu said:**
> Wouldn't a C-like language give you better insight into memory allocation and usage?

Yes but...

> I've seen a question here where the implementation of cpython gave strange results only understandable if you have some idea of how memory management works.

The question is what is the purpose of the application you are trying to develop?  Do you need to be able to address certain locations in memory or is the performance of your application will not be significantly impacted by passing stuff by value if we are talking about C derivatives.

As I mentioned before the idea is to know what you need to get accomplished and what the requirements are and that will drive what you will need to know to do that.

---

### Post by scitron on 2011-10-18
For a complete beginner is makes little sense to get bogged down in concerns about efficiency and an algorithms use of computer time and memory.

Indeed first we understand a concept as an abstraction and that later the realization of it might be more efficient with one particular language or another.

If at minimum Python had type inference it would be a more respectable language and not usually seen as the "scripting language".

---

### Post by juancarlospaco on 2011-10-18
You can convert python into C/C++ code and/or binary...

---

### Post by orphanlast on 2011-10-18
Actually the theory is what I'm interested in at this point. Because I have tutorials I'm going through that are discussing some stuff I don't really comprehend. 

From what I've read, "Python allows the programmer to approach a program using multiple philosophies in the program development" and I have no idea what that means. 

I think it's normal for start-out-programmers to begin with text based programs -- somewhat like a terminal like dos. But I think that it takes a whole different paradigm shift to go from that to create something like Blender or an actual GUI. So, I'm curious what you guys suggest on regards to reading about the theory and the philosophical approaches to making a program. I think that if I read a lot of content like that, I'd be able to comprehend the code a bit more.

Take this for example:

```
a = 0           
while a < 10:   
    a = a + 1   
 in: a = a + 1! 
    print(a)
``` 

This gets the sucker to count to 10. You assign the a to zero then tell it that it's always less than ten (though I don't know what the ":" thing tells it to do). But the in: "a=a+1" part baffles me. Because all you're telling it to do now is add 1. There's no part in this where you tell it to repeat the process up until it reaches 10. Then of course you tell it to tell you what "a" is and so it counts to ten. 

If there wasn't a tutorial specifically on this, I would have no idea how to do that. Maybe understanding the programming philosophy might help out a bit.

---

### Post by karlson on 2011-10-18
> **orphanlast said:**
> From what I've read, "Python allows the programmer to approach a program using multiple philosophies in the program development" and I have no idea what that means.


Could be wrong but I think they mean being able to use imperative, object-oriented, and functional paradigms

> 
I think it's normal for start-out-programmers to begin with text based programs -- somewhat like a terminal like dos. But I think that it takes a whole different paradigm shift to go from that to create something like Blender or an actual GUI. So, I'm curious what you guys suggest on regards to reading about the theory and the philosophical approaches to making a program. I think that if I read a lot of content like that, I'd be able to comprehend the code a bit more.


Algorithms?  Data Structures?  Design Patterns?

> 
Take this for example:

a = 0           
while a < 10:   
    a = a + 1   
 in: a = a + 1! 
    print(a) 

This gets the sucker to count to 10.

There is something missing or something extra in this code.  ipython don't like it.
>  then tell it that it's always less than ten (though I don't know what the ":" thing tells it to do).

It tells it that the following indented code belongs to the loop.
> 
 But the in: "a=a+1" part baffles me. Because all you're telling it to do now is add 1. There's no part in this where you tell it to repeat the process up until it reaches 10. Then of course you tell it to tell you what "a" is and so it counts to ten.

That's what "while a<10:" is.  Think of it as English or any other language construct of "While Mom was looking away I was stealing cookies from the cookie jar.".
> 
If there wasn't a tutorial specifically on this, I would have no idea how to do that. Maybe understanding the programming philosophy might help out a bit.

This has nothing to do with philosophy but with understanding of programming language constructs like loops in this case.

---

### Post by orphanlast on 2011-10-19
> **karlson said:**
> Algorithms?  Data Structures?  Design Patterns? 

Yeah see, I have no idea what you're asking.

>  There is something missing or something extra in this code.  ipython don't like it. 

It's not indented correctly. I included the correct indentations but it's not going through correctly in the forum.

>  It tells it that the following indented code belongs to the loop. 

That's what "while a<10:" is.  Think of it as English or any other language construct of "While Mom was looking away I was stealing cookies from the cookie jar."

so "while" is telling it to do a process. And basically the ":" is like the "unquote" for the "while" statement? If I'm making any sense here?

But stealing cookies isn't necessarily a loop. It could be a one step process. So would you say that in programming python "while" is consistently telling it to loop a process?

I ask because I read the wikipedia page about python. It seems to be the jack of all trades in the programming world. I think the wikipedia page said that Python differs from "perl" (I think) in that Perl has an open structure that allows for many different ways to accomplish the same task, but python states that there's only one specific right way. Personally, I think that makes it a little daunting because you have to program each task exactly the same and exactly with the correct logic, which can be hard to learn but once you've gotten the rhythm of this "one way to program a task" then in the long run it saves time. Especially if you're working on someone else's project. 

I'm digressing a bit, but if there's only one right way to code something in Python, wouldn't that mean that since "while" is used as a loop in this case it'd be a loop in every case?

>  This has nothing to do with philosophy but with understanding of programming language constructs like loops in this case.

Well... this is what I've done with everything that I've found complicated on a computer. I research it and go through the motions, not knowing what the hell I'm doing and sometimes I get frustrated and other times I just keep doing it and doing it without any care in the world and then I just quit for a while, either out of frustration or disinterest. 

But then, in that time off, I realize I know how to do this stuff. Something just starts to click. I'd realize I now know the terminology everyone's using and I have no idea where I learned it other than "internet". (That's how I learned HTML in middle school back when dirt was invented back around 1998. It's also how I learned photoshop two years ago).

Would you say that this approach would work? Because it just seems like there's such a vast amount of information that people are trying to dumb down for the beginner tutorials but still wind up throwing the mountain on you. Because I can see myself getting into that rhythm.

---

### Post by lisati on 2011-10-19
> **orphanlast said:**
> 
It's not indented correctly. I included the correct indentations but it's not going through correctly in the forum.


Easily fixed with the use of [noparse]```

```[/noparse] tags, which I have added for you.

---

### Post by karlson on 2011-10-19
> **orphanlast said:**
> Yeah see, I have no idea what you're asking.

Precisely.  You seem as most people who have asked the same question here be more concerned about learning the methodology of some language for doing certain things, like displaying windows, buttons, processing actions of button press, etc.
That's all nice to know but without the fundamental building blocks that are language agnostic like Data Structures, Algorithms and Design Patterns you won't be able to write something decent beyond "Hello World!" with a Quit button (may be a little more complex but you get where I am going with this)
> 
It's not indented correctly. I included the correct indentations but it's not going through correctly in the forum.

Tried with many different variations of indentation didn't work with any of them.
> 
so "while" is telling it to do a process. And basically the ":" is like the "unquote" for the "while" statement? If I'm making any sense here?

Not really. If you write it like this: "While Mom was looking away**,** I was stealing cookies from the cookie jar."
It's the comma basically stating that "action" begins here.

> 
But stealing cookies isn't necessarily a loop. It could be a one step process. So would you say that in programming python "while" is consistently telling it to loop a process?

"While Mom was looking away I was stealing cookies by taking one cookie at a time from a jar".  Looks better?
> 
I ask because I read the wikipedia page about python. It seems to be the jack of all trades in the programming world.


Not sure I understand what you mean here.

> I think the wikipedia page said that Python differs from "perl" (I think) in that Perl has an open structure that allows for many different ways to accomplish the same task, but python states that there's only one specific right way. Personally, I think that makes it a little daunting because you have to program each task exactly the same and exactly with the correct logic, which can be hard to learn but once you've gotten the rhythm of this "one way to program a task" then in the long run it saves time. Especially if you're working on someone else's project.

This was referring to Syntax only.
> 
I'm digressing a bit, but if there's only one right way to code something in Python, wouldn't that mean that since "while" is used as a loop in this case it'd be a loop in every case?


I don't know of any language that uses "while" for any other purpose then a loop.

> Well... this is what I've done with everything that I've found complicated on a computer. I research it and go through the motions, not knowing what the hell I'm doing and sometimes I get frustrated and other times I just keep doing it and doing it without any care in the world and then I just quit for a while, either out of frustration or disinterest. 

But then, in that time off, I realize I know how to do this stuff. Something just starts to click. I'd realize I now know the terminology everyone's using and I have no idea where I learned it other than "internet". (That's how I learned HTML in middle school back when dirt was invented back around 1998. It's also how I learned photoshop two years ago).

Would you say that this approach would work? Because it just seems like there's such a vast amount of information that people are trying to dumb down for the beginner tutorials but still wind up throwing the mountain on you. Because I can see myself getting into that rhythm.

Approaches to learning are yours and yours alone, the question that you should ask yourself is: What's my goal?  Am I learning this to understand what other people are talking about to keep up with a conversation?  Am I learning this to understand the subject?

Once you figure this out your path of what to learn will become clear and then you can use your approach to learning to retain the knowledge.

---

### Post by llanitedave on 2011-10-19
> **digrejzo said:**
> uhm, hello guys!

for those tl;dr guys, skip the next paragraph.
I somewhat thought I could benefit from a thread like this, but then you guys started the whole approach to programming and semantics, which doesn't really answer my question.
the thing is, I'm studying Librarianship and Information Science (Faculty of Philology) and we went through the basics of HTML/CSS, LaTeX, and now we're doing VBA and macros in general. I really don't see how I can benefit from VBA, but oh well. I always wanted to do something a bit more serious, so I am for, God knows which time (I hope it's the last), trying to find out which programming language to learn and make good use of the time spent learning. 

I have some knowledge of C++ (which I did in high school 2-3 years ago, and never tried it again, so it's a kind of a fresh start, but I still recognize the syntax etc), finished the [python "newbie" tutorial]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python"), I'm fairly good at HTML/CSS (which are not programming languages) and LaTeX, so I understand the basics of programming. a friend of mine recommended JavaScript, so I'm not sure which way to turn right now.
should I continue the python, maybe learn basics of JS and work my way from there, or go back to C++ or maybe something else?

I really love how python works, and its' ease of use.
basically, I wanna create GUI applications, from basic "guess a number" to something more complex. sorry for the whole "life story" part of the post, but it's only for the purpose of clarifying my problem.

cheers!

I'd say the answer depends on how you feel about html/css.  Do you enjoy it?  Do you want to keep using it?

Further, do you want your GUI's to be browser based?  Are your applications going to be self-contained or are you going to be doing file handling and manipulation?

If the latter, Python is probably your best bet.  If you're more interested in browser-based applications, I'd recommend Javascript.

Thing is, both are fairly easy languages to learn, so if you have trouble deciding, there's no reason you can't learn both.

---

### Post by digrejzo on 2011-10-25
finishing *"A Byte Of Python*" in a day or two, it's been fun and interesting so far.
later, I'll start working on "*Invent your own computer games with Python*" by Al Sweigart.
the more I know, the more I like Python and the way stuff works. it's awesome. =)

---

### Post by Vgui on 2011-10-25
I saw a whole lot of Python, but also a brief mention of Java IDEs. Back when I was learning Java I used BlueJ ([http://www.bluej.org/](http://www.bluej.org/)) which is a simpler IDE specifically designed for helping a person learn programming. It can be a nice step before moving on to Eclipse/Netbeans/IntelliJ.

Good luck with your learning. Programming sure is fun to figure out and realize you can wrangle the computer to do lots of cool stuff.

---

