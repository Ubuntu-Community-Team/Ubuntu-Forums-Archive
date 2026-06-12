---
title: "First/Best Programming Language"
date: 2011-05-29
forum: Programming Talk
---

### Post by JupiterV2 on 2011-05-29
What should I choose as my first programming language? What is the best programming language to learn?

These questions are asked repeatedly in these Forums and I hope I can give you a relatively definitive answer: 

None. 

Over and over I see experienced programmers giving the same answer. There is not one programming language that is the best. There is no language that is the best at solving every problem. There is no single language which teaches programming techniques better than any other language.

There are, however, languages which are more powerful as a general problem-solving tool (high-level languages) rather than being more suited to a specific task.

Let me break my answer down into sections:

1. No one learns the same way. Some, like myself, learn from the bottom up. We want to not only know how something works but why it works. While I didn't go all the way to the bottom and choose something like Assembly or some microprocessing language, C was the best fit for me. This isn't to suggest that a lower-level language will allow you to understand a higher-level language. For example, understanding C will likely not help you understand how Lisp works. A lot of people suggest Python and Java because they teach a lot of good programming techniques while doing away with the "headache/complexity" of pointers in C. Others suggest languages like Turing which is only used for instructional purposes. Still others suggest not learning any language at all and would have you learn techniques, algorithms and structure first so that you can pick up any language with a lot more ease. Yet another approach is to learn a high-level language like Scheme which takes a minimalist approach to the core language.

2. There is no silver bullet. No one single language should be used to solve all problems. You wouldn't use C to design a webpage. You wouldn't use SQL to write a message daemon. The point is, you need to choose what you want to accomplish, first, before you can choose the "best" language for that particular job.

3. Is the popularity of the language important? The availability of help may be a factor. Whether you're learning in a classroom or you want to be self-taught, then the availability of online help may be a consideration. If you want to learn a language which has a LOT of online help and tutorials then C, C++ and Java are right for you. If you want to program on the web then HTML, XML, SQL, PHP, ASP, etc. Python, Tcl, Lisp, and many other languages also have a lot of online help and tutorials. If you are looking exclusively to learn off these forums, Python might be a good choice (more on this in my next point).

4. Who is your target audience? If you want to write desktop applications for Ubuntu exclusively, then you might look no further than Python. If you need to create native binaries for several platforms, then you may need to look at compiled languages like C or C++. If you need a write once, run anywhere solution then Java or Python may be good choices.

5. Are you serious about being a programmer? If you are, then you won't be learning any one single language. So, in the end, you can't really make a bad choice. There may be better choices over others but no bad choice. All languages can teach you the basic techniques you need, just with varying degrees of difficulty. If you want to find a language which simply pays well, or has a lot of job openings, then again, your first choice doesn't matter. The end of story is, and it might hurt to hear, that no employer wants to hire someone who knows only one language. They need someone who can fill multiple roles, who has experience with solving various problems, and whom has a lot of tools in their tool-belt. If you want to work for a website design company, only knowing HTML isn't going to get you anywhere. You'll need to learn Javascript, PHP, ASP, XML, and several other tools in order to be a good prospective hire. Knowing a good mix of low level (C, C++, etc), high level (Java, Python, etc), and complimentary languages (SQL, Lua, etc) broadens your choices greatly too. Why? What if you need to build an application which requires a low-level language for speed, a high-level language embedded into the application for writing plugins, and a method of accessing a substantial database of information? For example, you want to write a video game which would use C++ for its game logic, Lua for its customizable user interface and SQL for accessing all the data it needs. It is common practice to mix all these techniques, so you need to know them.

So, in the end, there is no right or wrong choice. It can be said, however, that there are good, better, best choices. Both Python and Java are suggested a lot for a first language. While not as abstract as Scheme they allow for a lot more abstraction than C. They are both good, general purpose, tools which run on most platforms. C# seems to be fairly popular as well, especially for Windows developers, and the Mono project has made it increasingly more popular on Linux platforms, too. All three languages have a plethora of tutorials and online help, and allow you to dive right into application development whilst learning the languages themselves.

---

### Post by CptPicard on 2011-05-29
Sorry, I'm in disagreement. Differences in languages can not be brushed aside quite this simplistically. We've been going over this a lot on this forum over the years, just use the search :)

> **JupiterV2 said:**
> 
Over and over I see experienced programmers giving the same answer. There is not one programming language that is the best.

"Use best tool for the job" is a valid position to take if not for the simple reason that not all languages work in the kind of niche they need to be used. 

> 
 There is no language that is the best at solving every problem. 

But it could be said that in the abstract, some languages are more general problem-solving tools than others simply by virtue of having abstractions that fit the space of abstract problems better. This is the argument for the existence of higher-level languages. 

> 
There is no single language which teaches programming techniques better than any other language.

I rarely see this claim being made. Also, if a lot of people didn't believe otherwise, languages such as Scheme would not have been created.

There is a certain strong argument that your tool influences your thinking, you know; I personally find it difficult to believe that something like assembly could be very "informative" in terms of actually formulating problem solutions, while Lisp in all its abstract minimalism facilitates your "thinking about programs" process much more.

> 
1. No one learns the same way. Some, like myself, learn from the bottom up. We want to not only know how something works but why it works.

You know, as a matter of theory, lower-level languages do not tell you how or why higher-level languages work. They pretty much can not, as both higher- and lower-level languages are equivalent and implementable in terms of each other; the "underlying" architecture, as far as it is Turing-complete, could be a bunch of hamsters powering an Analytical Engine. Of course compiler and interpreter authoring is a field of its own, but once that problem is solved for a certain architecture, it has been solved for all problems; and I do not really see the solution being particularly relevant in terms of all the other problems that you'll then solve using the interpreter/compiler.

> Still others suggest not learning any language at all and would have you learn techniques, algorithms and structure first so that you can pick up any language with a lot more ease.

I'd suggest learning a highly abstract language such as Scheme as it does away with the details that are not relevant to the development of program-formulation thinking. Architectural details are necessary at some point, but especially in the beginning they just get in the way.

> 5. Are you serious about being a programmer? If you are, then you won't be learning any one single language. So, in the end, you can't really make a bad choice. There may be better choices over others but no bad choice. All languages can teach you the basic techniques you need, just with varying degrees of difficulty.

Well, IMO, choosing an efficient learning curve is important. Also, all languages do not really equivalently teach you the techniques you need; languages like C and a functional-programming language like Haskell make you take rather different approaches to your problem.

However, my position is not to be construed as saying that one "should not" know all the approaches there are; it's just that you'll find it easier to understand what is going on in the other languages after staring with certain languages.

---

### Post by silex89 on 2011-05-29
I have not much expertise when it comes to programming, last year I had to take two programming subjects in the university. We checked out object oriented languages (C# and Javascript) and I felt really comfortable using those languages.

I began trying ArchLinux so I encouraged myself to learn script based programming, but I found more obstacles to overcome...

What I just said is just my point of view and shouldn't be taken as something else


Regards

---

### Post by kgarbutt on 2011-05-29
python. good ide's available. lots of material on the web too.

---

### Post by slavik on 2011-05-29
> **JupiterV2 said:**
> A lot of people suggest Python and Java because they teach a lot of good programming techniques while doing away with the complexity of C.

Show me the moron that ever suggested that C is more complicated than Python/Java. A fool and his brain are soon parted.

---

### Post by JupiterV2 on 2011-05-29
In reverse order:

@Slavik
I don't care to do a search right now to back up my claim but many, incorrectly perhaps, have stated that C is more complex than Python/Java. This assertion is usually when comparing languages with pointers and memory management vs. languages with garbage collection. Right or wrong, the claim is made. I am just trying to state that some suggest it. Perhaps its better to say that C is more dangerous to the ignorant? I don't know...I've never made the claim myself (not to my recollection anyway).

@kgarbutt
This is specifically the "silver bullet" attitude I'm trying to avoid.

@CptPicard
I really appreciate your input and will try to address some of your comments in my original post. I think you raise some very valid points and I hope I can work them into my post to your satisfaction. =) The point of my post was to help reduce the many many posts by people wanting to know what language to learn who aren't in a Comp Sci program (where it's usually decided for them what they are going to learn). It is for those who are want-to-be hobbyists or younger students hoping to learn a language before pursuing formal education on the subject.

---

### Post by unknownPoster on 2011-05-29
> **slavik said:**
> Show me the moron that ever suggested that C is more complicated than Python/Java. A fool and his brain are soon parted.

I agree. C is much more simple than Java or Python, while at the same time much more powerful. What those languages provide is abstraction which hides much of their complexity.

---

### Post by JupiterV2 on 2011-05-29
> **unknownPoster said:**
> I agree. C is much more simple than Java or Python, while at the same time much more powerful. What those languages provide is abstraction which hides much of their complexity.

You help to make my point. Are you arguing that programming in C is more simple than Python, or are you saying the language itself is more simple because of how abstraction allows the complexity of Python to be hidden? If the complexity is hidden, then can it not be said that the language is easier to learn? Yes? No? I don't know, and I don't think anyone who wants to try their hand at programming for the first time will understand this argument either. They just want to know, "What is the least path of resistance to writing an application?" Python seems like a better choice than C for that specific question. Python, though, doesn't teach you how to write an application in C. And vice-versa. However, there are some common principles and techniques which are shared between them. A loop is a loop, a conditional a conditional. Which of the two does a better job at teaching a student those principles? Which language does a better job of teaching someone a sorting algorithm? Should you learn how to create a linked list or use a language with a built-in type which does it for you?

What I think most novices get confused about is the answers experienced users give. It's like watching the following argument: 

Is the letter A better than C? Is C better than A because the letter C is easier to write? It's just a single arc whereas A requires you lift your pen from the paper. Which letter should you learn to write first? A because it comes first in the alphabet? Will A get you closer to writing a sentence or C?

I think this is where a lot of new students get confused. We talk about levels of abstraction to people who don't even know what an object or loop is. We talk about cross-platform compilation to people who don't know what a compiler is. We talk about system libraries and interpreters to people who thought we were talking about programming, not linguistics.

I'm trying to figure out how to provide clarity...and I'm not sure I have. :)

---

### Post by unknownPoster on 2011-05-29
> **JupiterV2 said:**
> 

I'm trying to figure out how to provide clarity...and I'm not sure I have. :)

You can't and you won't.

I've been active on these forums in some form since early 2007. This exact debate/discussion shows up every few weeks and the results are always the same. No agreement is reached.

There is no valid reason for or against learning any non-esoteric programming language.

---

### Post by shadylookin on 2011-05-29
I don't suppose someone could claim objectively that there is a "best" language for beginners, but there are languages designed specifically to reduce the learning curve for new programmers. 

Most institutions will teach a higher level language to their new students, and I suspect that it is to help abstract away architecture concerns. Though I suppose it's possible that they just decided to do so randomly.

---

### Post by slavik on 2011-05-29
> **unknownPoster said:**
> I agree. C is much more simple than Java or Python, while at the same time much more powerful. What those languages provide is abstraction which hides much of their complexity.
That is a good way to put it.

Java has something called weak references and strong references. It also has about 6-7 garbage collection algorithms, designed for different types of systems for different trade offs. Java code can still have memory leaks and I have seen where they do. I have seen J2EE code running in a container that causes the container to keep running threads, eventually running out and not responding to any new requests.

---

### Post by Some Penguin on 2011-05-29
> **unknownPoster said:**
> You can't and you won't.

I've been active on these forums in some form since early 2007. This exact debate/discussion shows up every few weeks and the results are always the same. No agreement is reached.

There is no valid reason for or against learning any non-esoteric programming language.

Wouldn't matter even if it agreement WERE reached, the thread was stickied, and the forum instructions pointed people to that very thread in blinking 128-pt red letters. 

It'd still be asked about every couple of days or so by people who don't believe in checking whether anybody's ever asked and been answered, and you'd still get an near-infinite number of language fan-boys reiterating their own preferences in one-line answers with zero rationale.  The threads would accumulate views, and you'd get spambots finding these high-view keyword-happy threads and advertising in them.

---

### Post by ve4cib on 2011-05-30
I'll echo the sentiment that the best programming language for any given task depends greatly on the task at hand.  But the programmer's personal preferences and experience will also influence the decision greatly.

Some surgeons will prefer a #10 blade for a certain incision, and others prefer a #8 for the exact same incision.

Likewise, some programmers will prefer C++ for a given application, while others would see Java as the natural choice.  Two programmers, looking at the same problem come to two different conclusions.  Neither is wrong -- the decision they made was *right for them*.

Some programming languages are tailored by nature or by design to certain families of problems.  For low-level programming, like OS kernels, C or C++ are the natural choices.  C was designed for exactly that purpose, and therefore excels at it.

For application-level programming the number of choices explodes.  C# and Java were designed with application programming in mind.  C++ has historically been employed for this purpose as well.  None of them are the silver bullet of application programming, and -- just to make sure this point gets across -- the decision depends on a combination of the programmer's personal preference (or directives from higher-ups in the organization of which the programmer works), as well as the nature of the program.

In academic/educational settings the nature of the problem is even more nebulously defined than in the generic umbrella of "application programming."  We want to teach someone how to program.  Well, historically being able to program meant you had to understand hardware, so a low-level first approach is often used (e.g. starting with C).  Others see benefits in abstracting away low-level concepts like pointers and memory management at first in favour of teaching algorithms and conceptual data flow.

Both approaches are used in different academic settings, and both produce competent programmers.  The respective institutions tailor their courses to their chosen method of instruction.  Neither is "right" and neither is "wrong."  They're just different.

Ultimately everyone is always going to have a different answer, and will have different reasons for giving that answer.  But for me it's the *reasons* behind those answers that makes the dialogue interesting.  Anyone can say "Learn C first," but that's a useless statement.  Saying "Learn C first because ...," is much more useful because it allows the person asking the question to learn something and make an informed decision.  Or at the very least the explanation may spark some questions.

All that having been said, next time you feel the urge to ask "What program should I use for ___," please take the time to read the stickies or do a google search.  You might just save everybody a lot of time.

---

### Post by ThatCoolGuy220 on 2011-05-30
Though im still on that vagon

I couldnt decide since any of the lenguage i tried gave me a executable file that could be opened with a click....

is very frustrating i couldnt find good tutorials regarding to linux cause all i see is

#include <iostream.h> (Windows library i think)

or

system("pause";) (Wich is also for that)

i know i could use "cin.get();" instead but some stuff is not that easy like to make a window:

#include <window.h>

it doest work it gaves me errors on the compiler.


Sorry for the c++ish but was first lenguage i touched.

---

### Post by unknownPoster on 2011-05-30
> **ThatCoolGuy220 said:**
> Though im still on that vagon

I couldnt decide since any of the lenguage i tried gave me a executable file that could be opened with a click....

is very frustrating i couldnt find good tutorials regarding to linux cause all i see is

#include <iostream.h> (Windows library i think)

or

system("pause";) (Wich is also for that)

i know i could use "cin.get();" instead but some stuff is not that easy like to make a window:

#include <window.h>

it doest work it gaves me errors on the compiler.


Sorry for the c++ish but was first lenguage i touched.

I answered your post in another thread.

#include <iostream> is perfectly well and valid in Linux. But we shouldn't discuss this here.

---

### Post by slavik on 2011-05-30
Maybe we should close all threads of people asking what is the best language to start learning programming with. In the end, none of us can be classified as professional educators. Hence we are not qualified to make the decision of how to educate someone.

On that note, everyone talks about "walking before running" and then suggests python. This is why I promote C as the first language. I also don't believe in instant gratification. Maybe that is because that is how I learned.

---

### Post by nvteighen on 2011-05-30
> **slavik said:**
> 
On that note, everyone talks about "walking before running" and then suggests python. This is why I promote C as the first language. I also don't believe in instant gratification. Maybe that is because that is how I learned.

And I don't believe in metaphors. They are arbitrary by nature. Why should C be "walking" and Python "running" or viceversa? I could say Python is "walking" because it's simpler...

Holding this truth to be self-evident, that all Turing-complete programming languages are created equal, it is also self-evident that each one was created with a certain task in mind. In fact, my personal definition of *artificial language* is: language created for a specific task besides expression. Esperanto was created as a tool for universal peace, C was designed to make UNIX possible.

It's true that all Turing-complete languages are equally powerful in the sense that all of them can do the same. But languages are vehicles that allow expressing stuff and programming languages are no exception to this. They provide a certain conceptual or semantical framework that allows you to express a solution for some computable problem. The thing is that, being "optimized" for some goals, the conceptual framework will be biased for that said goal. That's it.

IMO, *teaching* programming is also a goal programming languages can target because it's actually about teaching the minimal and general concepts that drive programming. In other words, the task is expressing things as clear and straightforward as possible for a beginner. And some are better at it than others; of course, all of them can do it in theory. C has some features that makes it acceptable for this task: it *is* simple and straightforward; the problem of C in my opinion is that low-levelness forces you to learn platform-specific details that are only applicable for a certain subset of programming problems. So, *compared* to Python, I'd prefer Python, but *compared* to C++, I'd prefer C. Over all of them I'd prefer something like Scheme, at least for teaching the very foundations of programming (variables, loops, procedures and abstraction).

---

### Post by Petrolea on 2011-05-30
This thread was created to make less discussions about which language is better, easier, less complex, powerful and so on. But it just became one of those threads.

---

### Post by JupiterV2 on 2011-05-30
> **Petrolea said:**
> This thread was created to make less discussions about which language is better, easier, less complex, powerful and so on. But it just became one of those threads.

Ha! Hit it right on the nose!

The thread, and some of the latter posts, demonstrates why these threads keep going on. There is no one right answer, which is exactly my point. No one learns the same way. Not every programmer wants to write applications. I, like Slavik, found C to be the most instructional and entertaining language to learn on. Could there have been a better choice? Maybe, but when I finally sat down and tried to learn C there were a plethora of other languages already out there. I had tried 3 languages prior and didn't get anywhere. C was right for me. Scheme or Python may have been able to teach me things that C couldn't but maybe I never would taken to them. We can argue that the most efficient (hypothetically) path to success is Scheme->Python->C but what if you never get past Scheme? What if they'd started with Python or C, skipping Scheme, would they be a better or worse programmer? Would it be easier or harder for them?

There's no "right" answer. That's exactly the reason why schools all have different methods of teaching, just as *ve4cib* stated.

We won't ever eliminate posts asking the question, "Which language should I learn?" As stated already, many posters won't take the time to do a simple google search or a forum search (there's a button when posting RIGHT BESIDE the Title/Subjust entry too!) before posting. It's a sad reality but one I must accept. I just want to give some confidence or comfort to those with half a brain cell and willing to look that, even if they make a "bad" choice, they're not ruined forever. Yes, maybe it will take longer for you to get to the same place as someone else but maybe that has nothing to do with their choice of language. And, in the end, it doesn't mean they are, or will be, a better programmer than yourself.

---

### Post by Vaphell on 2011-05-30
Agreed, people are predisposed to different things. Some like to investigate things to the deepmost levels and are not discouraged when things break down because it stimulates their inquisitive tinkerer soul, while others need that sweet taste of achieving something practical, with tangible results and that gratification is what keeps them going. When you are a noob needing good mood to make progress, going C route can discourage you for life and what's worse, reinforce the notion that programming is for weirdo nerds of the kind you generally don't invite to your birthday party.

And python and C are both simple but these are different kinds of simplicity. C is like oldschool car - simplicity of construction: simple parts, manual shift, hydraulic everything, easy to fix and tweak once you know the details, while python is like a modern vehicle full of electronics that hides a lot of inner workings from the user and drives itself for the major part - simplicity of use where 'what' is more prominent than 'how'. The former is more powerful once you achieve mastery, while the latter produces satisfying results much faster.

---

### Post by slavik on 2011-05-30
> **nvteighen said:**
> And I don't believe in metaphors. They are arbitrary by nature. Why should C be "walking" and Python "running" or viceversa? I could say Python is "walking" because it's simpler...

Holding this truth to be self-evident, that all Turing-complete programming languages are created equal, it is also self-evident that each one was created with a certain task in mind. In fact, my personal definition of *artificial language* is: language created for a specific task besides expression. Esperanto was created as a tool for universal peace, C was designed to make UNIX possible.

It's true that all Turing-complete languages are equally powerful in the sense that all of them can do the same. But languages are vehicles that allow expressing stuff and programming languages are no exception to this. They provide a certain conceptual or semantical framework that allows you to express a solution for some computable problem. The thing is that, being "optimized" for some goals, the conceptual framework will be biased for that said goal. That's it.

IMO, *teaching* programming is also a goal programming languages can target because it's actually about teaching the minimal and general concepts that drive programming. In other words, the task is expressing things as clear and straightforward as possible for a beginner. And some are better at it than others; of course, all of them can do it in theory. C has some features that makes it acceptable for this task: it *is* simple and straightforward; the problem of C in my opinion is that low-levelness forces you to learn platform-specific details that are only applicable for a certain subset of programming problems. So, *compared* to Python, I'd prefer Python, but *compared* to C++, I'd prefer C. Over all of them I'd prefer something like Scheme, at least for teaching the very foundations of programming (variables, loops, procedures and abstraction).
I have no idea what your point is ... (maybe my reading comprehension is crap).

Not all Turing-complete languages are equal. Turing-complete means that given an infinite amount of time and memory one language can mimic another language. Turing completeness is about computability, not complexity. If it take a language A a billion years to mimic a simple task that a language B does in one second, as far as Turing completeness goes, they are the same. I also don't see how you can claim that a language like Python (which has it's own virtual machine) is simpler than C. I also don't see how you need to know anything about underlying hardware in C. All in all, there is a concept of abstraction, whether it is a library/function in the same language or it is introduced as a new language.

As for the posters below you. I do not think we have degraded into an argument of what language is best for a beginner ... yet.

In the end, if we compare a bunch of languages together, how do we decide which one is simpler?

Here is a case study using 2 spoken languages, English and Russian (because I speak both).

English:
- borrows heavily from multiple different languages.
- 3 different negative prefixes, proper usage depends on word origin (greek vs. latin vs. german)
- 2 plurality suffixes (ies, s)
- no verb conjugation based on sex of the subject
- far away from being phonetic (what you hear is what you write)
- infrequent usage of diminutives/augmentatives (movie, shorty, hottie, etc)

Russian:
- does not burrow heavily from multiple languages (does burrow from german a lot)
- 2 negative prefixes ('not' and 'a' for greek words)
- 4 plurality suffixes (I am not aware of any rules for which one is correct)
- verbs are conjugated on sex of the subject ('he went' and 'she went' are different)
- close to being phonetic (what you hear is what you write), there are ways of checking many words for proper spelling. for example: sun in russian has an 'L' which is never pronounced, but in the word sunny, the 'L' is pronounced. (As a side note, in Ukrainian, the 'L' is missing in both).
- there is a soft symbol letter and a hard letter symbol which do not have pronunciation which modify the sound of the preceding consonant (they can't follow a vowel).
- diminutives/augmentatives are very easy to apply to any noun

Looking at the above, can you (anyone reading this) tell which language is "inherently simpler"? The reason I bring this up is that most
people, when talking about simplicity will only focus on one part of the language which I believe to be wrong.

---

### Post by nvteighen on 2011-05-31
> **slavik said:**
> I have no idea what your point is ... (maybe my reading comprehension is crap).

...

Looking at the above, can you (anyone reading this) tell which language is "inherently simpler"? The reason I bring this up is that most
people, when talking about simplicity will only focus on one part of the language which I believe to be wrong.

Wasn't that my point? :P We actually agree on the general idea; we disagree in what we respectively consider simpler for the specific task of "first language".

*En fin*... I hope these threads aren't as useless as they seem to us today: constantly bringing the same arguments knowing how everyone will respond. It's almost like Congress :P Call me a dreamer, but hopefully someone can enjoy these threads someday.

---

### Post by JupiterV2 on 2011-05-31
What's funny to me is that the original point of the thread was not so much to tell newbies which language to start with but to say, "Hey, you're not totally boned if you pick the wrong one!" Whatever language gets you to the next step is the one you should learn! No matter how great the language, if you don't like it you won't use it.

---

### Post by zobayer1 on 2011-05-31
I have been programming on python and C++ both for about 2 years, and still I think, C++ is much simpler to write and understand.... :) Clearly, not everyone will agree.

---

### Post by slavik on 2011-05-31
> **JupiterV2 said:**
> What's funny to me is that the original point of the thread was not so much to tell newbies which language to start with but to say, "Hey, you're not totally boned if you pick the wrong one!" Whatever language gets you to the next step is the one you should learn! No matter how great the language, if you don't like it you won't use it.
that's the exact point, until that same newbie comes in and says "I decided to learn language X," instead of everyone saying, go ahead, they start yelling about "go with language A, it's better."

---

### Post by ve4cib on 2011-06-01
> **slavik said:**
> (English vs Russian comparison...)

Looking at the above, can you (anyone reading this) tell which language is "inherently simpler"? The reason I bring this up is that most
people, when talking about simplicity will only focus on one part of the language which I believe to be wrong.

Most linguists will actually agree that English is a horribly complicated language.  It has endless exceptions to every rule, an enormous vocabulary, and verb tenses not found in many other languages. (My personal favourite being "I was going to have had it done by tomorrow, but it won't be finished until next week."  The future-past "tense" is a useful, but very cumbersome concept for many.)

Programming languages are inherently complex.  For any given algorithm there are always multiple ways of implementing it.  Recusion or iteration?  Objects or structs?  Static or instance functions?  If-else-if ladders or switch statements?

This is part of the problem whenever you're learning your first programming language, regardless of what that language is.  Different teachers, textbooks, websites, etc... will have different styles and preferences.  And when you don't know anything about programming and you see these conflicting styles (e.g. a C++ program using printf instead of cout, when your teacher always uses cout) it's easy to get confused.

Any language can be the victim of these intra-language conflicts.  Python can be very Lisp-like with lambda functions and the like, or it can be procedural like C, or object-oriented like Java.  C can look like line-noise, with lots of macros, trinaries, assignments as conditions, all to minimize the number of lines, or it can can be as legible as a well-written procedural Python script.

Regardless of whatever language you learn first, a lot of the concepts will transfer over to your second, third, and nth language.  The more languages you learn the easier it is to learn more.

---

### Post by slavik on 2011-06-01
> **ve4cib said:**
> ...Programming languages are inherently complex.  For any given algorithm there are always multiple ways of implementing it.  Recusion or iteration?  Objects or structs?  Static or instance functions?  If-else-if ladders or switch statements?...

Recusion or iteration:

All iterations can be recursions, but not all recursions can be iterations.

Objects or structs:

An object is a declared struct definition which has not only variables (state) but also functions (behavior).

Static or instance functions:

Static functions will only be in memory once! (Same for static variables, which make code no re-entrant)

If-else-if ladders or switch statements:

A single if-else is a subtraction and a jump. A switch is a subtraction, a memory lookup and then a jump. So, if you have more than 2 nested if-else statements, use switch (unless you need to do 2 comparisons in one statement).

---

### Post by ve4cib on 2011-06-01
> **slavik said:**
> Recusion or iteration:

All iterations can be recursions, but not all recursions can be iterations.

Objects or structs:

An object is a declared struct definition which has not only variables (state) but also functions (behavior).

Static or instance functions:

Static functions will only be in memory once! (Same for static variables, which make code no re-entrant)

If-else-if ladders or switch statements:

A single if-else is a subtraction and a jump. A switch is a subtraction, a memory lookup and then a jump. So, if you have more than 2 nested if-else statements, use switch (unless you need to do 2 comparisons in one statement).

Not entirely sure what your point there is.  I'm well aware of the differences between all of the various things I mentioned.  My point ws that, for the purposes of implementing an arbitrary program, you can freely choose to use recursion or iteration as an example.

(Incidenttally I believe you are mistaken when you say than not all recursions can be turned into iterations.  Can you give an example to back up this claim?)

More specifically, one sample program might implement a quicksort using iteration and a stack object.  Another quicksort could use recursion instead.  They're both quicksorts, but are written in completely different-looking ways.  To a beginner that kind of difference in "dialects" can be quite confusing.

---

### Post by psusi on 2011-06-01
I learned C, then asm, then C++, then when I got to college, learned Java.  I finally broke down and learned python recently, and I have to say, it is a great language.  It is far easier to read and understand, easier to learn, and much more expressive than C or C++.  You are able to accomplish a lot with far less effort than it would take in C/C++.  I therefore, recommend learning python first.

---

### Post by CptPicard on 2011-06-01
> **ve4cib said:**
> 
(Incidenttally I believe you are mistaken when you say than not all recursions can be turned into iterations.  Can you give an example to back up this claim?)

Depends on whether you're willing to allow for an external stack. If yes, all recursions can be turned into iterations; if no, only tail-call recursions are doable.

---

### Post by slavik on 2011-06-01
> **psusi said:**
> I learned C, then asm, then C++, then when I got to college, learned Java.  I finally broke down and learned python recently, and I have to say, it is a great language.  It is far easier to read and understand, easier to learn, and much more expressive than C or C++.  You are able to accomplish a lot with far less effort than it would take in C/C++.  I therefore, recommend learning python first.
And that is why you are ruining this thread. In case you haven't noticed, we are not discussing specific languages.

As for when recursion cannot be turned into an iteration ... graph traversal. Now, if you say that the iteration can have a stack, then that is what recursion is.

---

### Post by ve4cib on 2011-06-02
> **slavik said:**
> As for when recursion cannot be turned into an iteration ... graph traversal. Now, if you say that the iteration can have a stack, then that is what recursion is.

I was defining "iteration" to mean "code written using for/while loops, with whatever additional data structures are necessary for the algorithm to function (e.g. stacks, queues, heaps, trees, etc...), instead of explicit function recursion."

So I think we're saying the same thing, just using different definitions for the same term -- another flaw of languages!

---

### Post by hoboy on 2011-06-02
First/Best Programming Language ?
This is an impossible question to answer, look at universities and colleges round the world they use different first languages, even in the same country the first languages are not the same, yes you will hear many philosophical explanations, 99% are opinionated, but that is the only way to answer unanswerable questions.

---

### Post by ThatCoolGuy220 on 2011-06-02
I think there is no better cause all them have a big learning curve and there no easy solution.

I learned this after looking several times for something I will be doing on the future and not actually putting any effort on learning....


I think you shouldn't learn a language for an specific action, but for various actions.

And also like SLAVIK said there is not instant gratification, at all and I learned this the bad way.

now I'm putting more time actually trying to figure out how to do new stuff with a code I learned from a tutorial...


(My anecdote:)
Its like WarHawk you can spend time looking for tutorials or searching if pro flight mode its better than normal mode, or you can actually play and don't ask too much on how to begin but actually how to make your aim better and playing and applying that knowledge at the same time....

maybe if you put enough practice and time you could be a General on few months....

" IIAir_LeoII : I was good but there will be better out there" 

"-Air Marshal-" 



And sometimes also is that the solution is that there's no solution.




Sorry if it sounded like poetry, was cause  the rain inspired me

---

### Post by __Sun__ on 2011-06-02
> **JupiterV2 said:**
> You help to make my point. Are you arguing that programming in C is more simple than Python, or are you saying the language itself is more simple because of how abstraction allows the complexity of Python to be hidden? If the complexity is hidden, then can it not be said that the language is easier to learn? Yes? No? I don't know, and I don't think anyone who wants to try their hand at 

Is the letter A better than C? Is C better than A because the letter C is easier to write? 
I'm trying to figure out how to provide clarity...and I'm not sure I have. :)

In terms of language complexity C is simpler than Python.
However, achieving a solution with C is harder than it may be in interpreted languages such as Python or AWK. That is what you must understand, and that is the difference betwixt the twain.

C code eventually becomes complex, even though the language is simple.
This is one of the major problem and advantage of C (as some call it).
Python, in sharp contrast to C, usually has shorter and less complex code - ideal for beginners.

C++ makes things easier than C does, that is why most industries have completely ignored ISO/IEC 9899:1999 C. This explains why there are so few C99 compilers yet so many C++ compilers for the yet-to-be finalised C++0x standard.
But as computing speed is increasing hour by hour, the day will soon dawn when C will no longer be deemed necessary for producing regular applications.

Now, going back on topic. *To a learner and a student, a simple language is best which doesn't limit the thinking of the student but helps in expanding it.* Therefore, interpreted languages are - I believe - best. I personally think both scheme and python to be a good choice, since all of the language needn't be learned to explore the basics of programming.

C must never be used as a teaching language. Should the need arrive to make the student aware of the compile-link-execute cycle and produce fast applications which directly translate to assembly then I suggest a higher level language such as Fortran 2008 or Ada to be used instead. I would lean more towards Ada as it is very elegant and a friendly reminiscent of Pascal, not to mention beginner friendly. Many researches has been done on Ada as a teachings language and it has proved to be the better of most languages.

---

### Post by zobayer1 on 2011-06-02
In most of the educational institutions, C is still the first choice, and it is deemed that, if someone can learn C, then he is able to learn any other language pretty easily. And for most of the CS departments, C is thought because they are very close to pseudocodes of different algorithms and I think another obvious reason for it is, teachers have learnt C not python or some other interpretive language. Also, compiler based languages are always preferred, and interpretive ones are often ignored. My university course have this sequence: C -> asm, mips, java -> C++, web languages like php, js --> whatever u like for compiler labs.

---

### Post by ThatCoolGuy220 on 2011-06-02
I'm going to study that too on university its very interesting I just hope my teacher don't make change my Ubuntu for W*****

---

### Post by zobayer1 on 2011-06-02
> **ThatCoolGuy220 said:**
> I'm going to study that too on university its very interesting I just hope my teacher don't make change my Ubuntu for W*****

That's a good thing about universities, they won't try to make you change your Linux, in fact, they will try to make you leave windows .. as you know, system level programming / networking stuffs are not "friendly" in windows environment. But sometimes it may seem to be a real pain, especially for the assembly part, or kernel programming (don't get me wrong, they are pretty interesting but time consuming.. )

And may be this is another reason why they prefer C over others, cause, python is not suitable for these types of programming. Those are for lazy programmers imo, but as you are going to be something deep, you need something more in details..

---

### Post by hoboy on 2011-06-02
When I started to learn programming I was surprised that learning the syntax of the language did not make me a programmer, this was surprising to me.
It is actually such a difficult field, in the same time a very simple one.
It is difficult because it challenge your problem solving, your analysis, creativity abilities, even you have all that you have to be able to translate this into a working system that mean  in working code this is easy said then done.
It is simple because when you understand it and get the discipline, doing it right then it is simple.

---

### Post by __Sun__ on 2011-06-02
> **zobayer1 said:**
> In most of the educational institutions, C is still the first choice, and it is deemed that, if someone can learn C, then he is able to learn any other language pretty easily. And for most of the CS departments, C is thought because they are very close to pseudocodes of different algorithms and I think another obvious reason for it is, teachers have learnt C not python or some other interpretive language. Also, compiler based languages are always preferred, and interpretive ones are often ignored. My university course have this sequence: C -> asm, mips, java -> C++, web languages like php, js --> whatever u like for compiler labs.

My dear boy,

Compiled languages are, of course, preferred to interpreted languages in real-world applications. They are faster. But the trend, as I am witnessing it, is changing. Now the development is being done in easier languages like Python and once the debugging or "first phase" is complete they "change" the application into a, say C++ programme.

This has been done on some Microsoft projects, as I've read on some forums.

Secondly,
Pseudo code, has always and the majority will always appear in a Pascal/ALGOL like language. Some institutions use the C like pseudo code only because it is ubiquitous.

The point here is which language is easy to learn. The thinking that if you know C you can learn any language may very well be correct because C-like languages have now become omnipresent and ubiquitous.

There are much better languages for a beginner than the poor C. Languages which actually detect overflow, unlike C. Languages where the environment is more controlled so the student is not bewildered and nonplussed when something goes wrong. 

Take for example, Ada. It actually tells you there was a arithmetic limitation when you add 4294967296 + 1. C does not and produces the output 1 (on 32 bit systems). You see, what happens now is that the student thinks that his computer can't calculate simple mathematics! He is utterly nonplussed, because C doesn't report any error at all.

There are many flaws with C to bother a beginner with.
There are better alternatives already used at universities, such as Ada or Java.
I am surprised yours is still behind on updating it's course.

There, I have proved only one point as to why C is bad *for a beginner*. Not bad as a programming language but *unfit *for a starter.

Edit: I would like to add that 90% of my programming has been in C. So, on the contrary to hating it I like it. But, as some wise fellow once said *no language is perfect.* Indeed.

---

### Post by JupiterV2 on 2011-06-02
Again, this topic is degenerating into a comparison of A vs. B vs. C vs. Nth language.

The point that many seem to be missing, and I've said it again and again, is that there really isn't any one best language for each and every person. Oh sure, you can have a language that works best for teaching in 90% of the cases but we don't know each individual person and how they think or learn. Python or Lisp might be perfect for most students but some novices will take to C. Or maybe BASIC. Or how about Go? To me, it's whatever takes you to the next step.

The other issue it comes down to is the nebulous question: What makes a programmer good? His contributions to the field? Her ability to reason? Cleanliness of code? All of the above?

If you teach a novice Ada, does that necessarily beget that they'll be a great programmer? Unlikely. No language can boast that. 

What about Shell scripting? Simple and effective. Languages within languages really, when you start to think of what you can do with AWK + Shell. Or Sed + Shell...in many ways, when you start to incorporate other applications into the mix, shell can be very powerful. Yet, I don't think I've ever in my life seen someone suggest they start learning to program in Shell scripting. But, look at that! I'm getting off-topic myself!

I think it was Slavik who said, "Every time a novice says, 'I want to learn this language,'" instead of encouraging them, we argue. "Don't learn THAT language, use THIS language!" And then we never hear from them again. What is this? Trial by fire?

I see though that some ARE getting the point. "What is the first language I should learn?" I think we have to answer with a question: What interests you? Or, what language do you think you'd like?

If, however, someone is asking for our opinion on the matter then let's get in on the debate. "Do you think C# is better than Python?" Argue the pros and cons and let them figure it out. Programming is about problem solving right? They need to solve the problem in their own way.

In the very end, it's not what language you choose to learn. It's the problem solving and problem analysis that set us apart. Will some languages do a better job of it? Sure, maybe. We're talking the Tortoise and the Hare though. Sometimes slow and steady wins the race (sorry for the terrible cliche, I should be ashamed, I know!). It's not always about how fast a Language can "take you there." Python, for example, might get you to writing full-fledged applications faster but that doesn't mean you've learned the skills to be a "good" programmer.

---

### Post by ThatCoolGuy220 on 2011-06-02
I think this conversation can easily be endless

---

### Post by afterman on 2011-06-24
This thread proved incredibly useful to me. Thank you all very much for contributing to it!

---

### Post by branded7k on 2011-10-23
Many good points made in this discussion.  I taught computer sciences at a local community college for over 10 years.  Languages included BASIC, C, C++, COBOL, FORTRAN, etc.  I also have over 25 years of experience in the computer field, supporting both mainframe and micro applications.

Some languages excelled at handling text, others numbers.  Some were fair at both, but had their limits.  I can't tell you the number of times I've written a routine in one language, then picked up the report and routed it to another for further processing.

Before I get to rambling, let me get my two cents in for the main topic here, which is, what would be the best "first" language to learn.  BASIC (Beginners All purpose Symbolic Instruction Code).  Yes, I know, several of you will say, "When was BASIC ever seriously used in a production environment!"  Well, never!  Remember, the goal is to introduce the student to I/O, logic and program constructs.  BASIC does an excellent job of demonstrating these principles.  Also keep in mind the beginning programmer may not have extensive knowledge of processors, memory allocation and storage.  Personally, I love C and C++ but couldn't imagine explaining to a beginner, the concept of indirection, double pointers, classes, polymorphism, inheritance, etc.

---

### Post by CptPicard on 2011-10-24
Here's an interesting website regarding comparing languages to each other:

[http://therighttool.hammerprinciple.com/](http://therighttool.hammerprinciple.com/)

Seems like a lot of the more interesting claims regarding expressiveness etc seem to go exactly like I'd feel about them...

In particular, observe what has been said about C++ vs. Lisps (Scheme, Common Lisp, Clojure) or Haskell...

---

### Post by nvteighen on 2011-10-25
> **CptPicard said:**
> Here's an interesting website regarding comparing languages to each other:

[http://therighttool.hammerprinciple.com/](http://therighttool.hammerprinciple.com/)

Seems like a lot of the more interesting claims regarding expressiveness etc seem to go exactly like I'd feel about them...

In particular, observe what has been said about C++ vs. Lisps (Scheme, Common Lisp, Clojure) or Haskell...

Thanks for the link... Looks quite good :D

---

### Post by nvteighen on 2011-10-25
> **branded7k said:**
> 
Before I get to rambling, let me get my two cents in for the main topic here, which is, what would be the best "first" language to learn.  BASIC (Beginners All purpose Symbolic Instruction Code).  Yes, I know, several of you will say, "When was BASIC ever seriously used in a production environment!"  Well, never!  Remember, the goal is to introduce the student to I/O, logic and program constructs.  BASIC does an excellent job of demonstrating these principles.  Also keep in mind the beginning programmer may not have extensive knowledge of processors, memory allocation and storage.  Personally, I love C and C++ but couldn't imagine explaining to a beginner, the concept of indirection, double pointers, classes, polymorphism, inheritance, etc.

Ok, perhaps this is because you haven't touched Python yet. But many experts are seriously talking about Python as the new BASIC, with the great advantage that you can also use Python for serious programming, because it's quite a good platform (it has its quirks, though... like the non-real multithreading issue).

---

