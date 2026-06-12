---
title: "Suggestions for beginners"
date: 2007-11-03
forum: Programming Talk
---

### Post by LaRoza on 2007-11-03
People are obsessed with what language to learn, as if there is a wrong language, or you cannot learn more than one.

There are other things I believe that should be done for a beginner, not all of them require new languages to be learned. 

**Please list important steps to learning to program in this thread. It can involve learning a certain language, paradigm or performing certain tasks. Any suggestion for a beginner is welcome.**

For my own advice, I would recommend that after learning a language whatever it happens to be, to learn a language of a different paradigm. If you start out in Python, like many do, study a Lisp (Common Lisp or Scheme), or Haskell. The learning of a functional language is more valuable than learning 10 imperative languages.

Also, learn a low level language. Learning C and Assembly will help you become a more knowledgable programmer, even if you do all your work in Perl, PHP, or Python.

Take time to learn about data structures. You can know a language inside out, but still not be able to write functional programs because data structures are important in all languages. The lists of Haskell, the tuples of Python, and the arrays of C, are not language specific and can be implemented in other languages that do not have such built in data structures.

Learning a language is neccessary to begin, but there is much more than syntax in programming.

---

### Post by pmasiar on 2007-11-03
Syntax is maybe 10% of what you need to learn to become programmer. You need to learn also (not necessarily in this order):

- how to represent object from your problem are in abstract data structures,
- how to represent those abstract data structures in specific data types your language provides,
- how to modularize problem into parts, complete with data and behavior, and make parts interact,
- how to use different languages for different parts (bash, SQL, C++, HTML, AJAX), and how to make all those separate parts work together,
- how to detect and solve problems in your design and bugs, how to go from a symptom of a problem to cause to workaround and/or solution,
- how to interact with users, learn what they need, and explain them what they are getting,
- how to design user interface to your system, usability, and ease of use,
- how to interact with other people in your team, accept and give critique,
- and many more, this is just from top of my head

So you can see, language syntax is in fact the simplest part of becoming a programmer... :-)

---

### Post by Wybiral on 2007-11-04
I think there are two kinds of beginners... Those who know a little about low-level concepts and general computer architecture and those who need to write an application soon. I would offer two separate approaches to these people.

For people who actually know a lot about computers and how they use / manage data, I might suggest starting at assembly. After assembly you can learn some C, then migrate up to languages like Python (where you will be most productive). Then you will probably not have to use C again until you need to optimize a Python application, but you will understand all of the steps along the way which will give you a solid mental framework to view software from. I am also not suggesting you _master_ assembly or C, just that you understand it enough to move on.

For people who need an application soon or are more interested in getting software written than learning the ins-and-outs of programming, I would suggest learning Python first. It's powerful, you can do what you want this week, and it gives you a pretty comprehensive overview of a few different styles of programming. Eventually you can learn how to write modules in C, but you may never need to migrate any lower unless you are uncomfortable with a feature.

Naturally, it depends on you and your goals, but Python is definitely a great medium. It can appeal to low-level developers because it's easy to write libraries for and manage low-level code, and it can appeal to high-level developers because of its ability to morph between procedural, object oriented, and functional programming... All in a clean, minimal language (with an extensive standard library).

---

### Post by j_g on 2007-11-04
I think that some very important things for beginners to learn are those things that will greatly assist you when you advance to writing more complex code. And yet, these are things that most beginner books gloss over or omit.

1) Learn to do proper error checking and handling. If you don't learn it right from the start, odds are good that you'll never learn how to do it right. When I started programming, I did so in order to produce code that was actually going to be used by others in a production environment. For that reason, the code had to be stable. I couldn't afford to not check if a memory allocation succeeded, or not consider if an exception would be raised, or not check if a file operation succeeded, or let the program "exit" without presenting an informative error message what went wrong, or let the program terminate without freeing all resources. Not coincidentally, whenever I see production code that isn't stable, or keels over without any warning, or causes some resource to be "locked" or left in an unusable state until the system is rebooted, or is just plain buggy, the code is invariably written by someone who wasn't taught error handling when he was a beginner.

2) Learn to comment code. When I started writing code, that code was meant to be part of a larger project maintained by others. I had to comment the code explicitly so that others could know exactly how it worked and what behavior it exhibited. This also made the code a lot faster for me to update because, even if I hadn't worked with the code in months, I didn't have to "study" the code to remember how it worked. The comments told me right away. Plus, it made it less likely to introduce bugs in updates, because the behavior of the code was already well documented. (ie, If you don't comment that a particular function alters some arg passed to it, you may forget about that, and update your code without taking this into consideration). Beginners who aren't forced to comment their code develop the lazy habit of not ever doing it. It's gotten to be an epidemic in the open source world. This may be one of the biggest obstacles to many open source projects not being updated as fast as they could be. Everyone who wants to work on the code is forced to spend too much time figuring out how the code works, when he should be able to do that more quickly via good comments.

Also, writing good comments improves your ability to write good documentation. Without good docs, other programmers are disinclined to use your software. Right now, I'm working with ALSA, and the documentation is downright horrible. There's no way that someone can use this thing to advantage without extensive study of the original (poorly commented) sources. On the other hand, I've had lots of people use my software to great advantage without ever looking at the sources. The difference is that I give at least as much effort to documentation as I do coding.

3) Learn to "flowchart". You don't have to do the traditional flowchart. I don't. You can do psuedo code, or a detailed description, or whatever. But definitely don't start coding until you've come up with an organized, plain english "layout"  of what your program does and how it is going to do that. This will help you avoid writing spaghetti code (ie, you've done a lot of the organization before you start putting statements together into functions), and avoid having to rewrite the same bit of code numerous times (ie, when you suddenly realize that you forgot to consider something when you initially wrote the code). And the more you rewrite the same code, the more likely you are to introduce bugs.

In conclusion, first come up with an organized, detailed plain english description of what your program will  do, and how you plan to do it. Then, start writing the code, commenting the code, and doing error checking, right from the start.

---

### Post by xtacocorex on 2007-11-04
My suggestion will be to go into learning how to program with an open mind, it will be difficult at first.

Most programming is like solving a math problem; there is a need for understanding logic.

Don't go into programming wanting to write the next great GUI program, start off small and program some math problems that you would normally have a hard time solving by hand after you follow some simple tutorials.

---

### Post by CptPicard on 2007-11-04
There really is no "royal road" to programming so I would be a bit sceptical of the existence of some optimal path to enlightenment. There is so much stuff that is so interrelated on many levels that you reach guru status only by mucking about in all of it for a long, long time. 

I guess the biggest obstacle to becoming proficient is the fact that as a n00b your learning curve is pretty steep and frustration easily sets in. Your speed of learning new stuff increases as you go. So you should definitely start with something that gives you instant gratification... Python is very good for this purpose.

LaRoza is completely correct in stating that there is this odd beginner worry about which language to start in, as if they were wasting effort if they chose wrong... well, they aren't. Any language will do, and you'll have to learn many languages anyway during your education. Actually, a sure sign of a n00b who is not going to cut it is that he keeps on bouncing back and forth between languages, assuming that one would be easier than the one he just didn't get.

Of course, the reason why language choice doesn't really matter is down to the fact they are all theoretically speaking all equally powerful. They just express some things differently. Depending on your problem, you'll want to use one language over another.

The next step is developing your sense of abstraction. Learning different paradigms of languages is important here, as is just simply hitting a textbook for some basic algorithms and data structures. On a high level, programming is just putting pieces together, and actually, most problems are already solved, if you only recognize them when you see them. Building a toolbox of ready-made solutions is crucial, and even more important in the long term than knowing some particular API by heart. Personally this is where I draw the line between one-trick code monkey and genuine computer "scientist" ;)

Also, learn Lisp (Scheme gets my vote). Especially in Scheme you learn a lot from seeing how from extremely simple building blocks you can build all sorts of paradigms... even object-orientation and concurrency. The whole point is that for example OOP is not just some magical ingredient baked into, say "object-oriented languages" but that you can see it in terms of the wider picture of closures in functional languages! You really begin to appreciate the kind of universality in computation regardless of the particular form it takes. Another great feature of Scheme is that it nicely illustrates the interplay of data and computation... code is nested lists, which is data, which can be evaluated through computation. At one extreme is lambda calculus where all is functions... at another extreme would probably be some kind of a syntactic tree you evaluate using some general processing rule.

As soon as you start really "getting" the above paragraph, congrats, you're pretty far along I'd think...

---

### Post by Anzan on 2007-11-04
This is all very useful so far. Thank you.

---

### Post by tyoc on 2007-11-06
Learn to read other people code, if possible in other languages, be curious.

---

### Post by ButteBlues on 2007-11-06
> **tyoc said:**
> Learn to read other people code, if possible in other languages, be curious.
Use a good tool for coding. Don't rely on a bulky IDE to do most of the grunt work for you because you should have a grounding in those concepts. They don't make life easier in the long run, at all.

---

### Post by CptPicard on 2007-11-06
> **ButteBlues said:**
> Use a good tool for coding. Don't rely on a bulky IDE to do most of the grunt work for you because you should have a grounding in those concepts. They don't make life easier in the long run, at all.

Oh, *in the long run* they certainly do. I'd hate to code Java without a code-completing, refactoring, auto-fixing IDE. For a beginner your argument has validity, but I'm certainly not macho enough to ignore the productivity gain I get from either Eclipse or Netbeans. Also, I'm humble enough to admit that I don't know all the APIs (even my own) by heart so getting suggestions is priceless :)

---

### Post by ButteBlues on 2007-11-06
> **CptPicard said:**
> Oh, *in the long run* they certainly do. I'd hate to code Java without a code-completing, refactoring, auto-fixing IDE. For a beginner your argument has validity, but I'm certainly not macho enough to ignore the productivity gain I get from either Eclipse or Netbeans. Also, I'm humble enough to admit that I don't know all the APIs (even my own) by heart so getting suggestions is priceless :)
Automated code refactoring is probably the single worst thing to have been invented in the IDE; it outright encourages sloppy coding practice with the knowledge that "Well, the machine can fix my mistakes for me so I don't need to know how."

---

### Post by CptPicard on 2007-11-06
What do you gain by taking the pain voluntarily? I would never want to work for a company that outright bans tools because it ensures their programmers "know what they are doing".

As a matter of fact, on second thought I might even recommend an IDE to a n00b after they get the basics. It guides them as they code, constantly teaching, and they don't need to waste time browsing the API docs "manually" all the time. After all, if IDEs are for incompetents, then they are almost by definition for beginners :)

---

### Post by pmasiar on 2007-11-06
I support CptPicard. Of course is important to eventually learn working without the crutches of IDE, so you can fix code without it if you need. But to avoid it entirely just does not make sense. If IDE increases coder's productivity, only coder who does not care about productivity would not use it, IMHO. pain is good if you gain something, but pain without the gain? 

And some tools are just required. I certainly would not work on Java/Struts without MyEclipse plugin - and it is not that I did not tried to use Struts without it, with bare Eclipse. But Struts is to freakishly over-engineered, it is hard to do it by plain editor.

---

### Post by slavik on 2007-11-06
1. Learning a programming language is very similar to learning another spoken language. Figure out what you want to say and translate it into a programming language (one professor believes that learning to program is easier for people who speak 2 or more languages).

2. Understand the level below the one you work at. If you work in Python, understand C. If you work in Java, understand C++. If you work in C, understand assembly ... and etcetera. (Note: understanding doesn't mean being an expert.)

3. Learn how to use vim/Emacs. Chances are it will be impossible for you to find a system on which either one doesn't run (if it is a modern desktop system).

---

### Post by aks44 on 2007-11-06
> **slavik said:**
> 1. Learning a programming language is very similar to learning another spoken language. Figure out what you want to say and translate it into a programming language (one professor believes that learning to program is easier for people who speak 2 or more languages).

I can't agree more. To continue the metaphor, I'd even add that the younger you start learning & the more you practice, the easier it is to think in *any* language without the need for translation.
Obviously this is more true for natural languages (well, at least more "natural", no pun intended), but even for computational languages one can come to a point where you express your thoughts almost natively in the target language.
Disclaimer: it may take years of practice. :)

I for one do believe that knowing several natural languages is just as useful as knowing several programming languages, both make your mind more flexible and that's all what really counts in the end.

---

### Post by ThinkBuntu on 2007-11-06
Learn how to use **for** loops early. I found that basic features of programming like this are non-obvious to the average person, and my natural way of thinking was always to use a huge series of **if**, **then**, **else** statements.

Also, try using the language to solve practical problems. Create a To Do list program, or any variety of things. If you build websites, this is easy. For example, I was writing a web form today, and needed a field for the Date (for a a date of birth field). I started to do the usual
```
<select name="date">
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
<!-- And so on, through 31 -->
```
When I stopped myself and used this code instead:
```

<?php
for ($date = 1; $date <= 31; $date++) {
    echo "<option value='$date'>$date</option>";
}
?>
```
Saved my fingers a lot of work, easier to maintain, etc.

---

### Post by ButteBlues on 2007-11-06
> **pmasiar said:**
> I support CptPicard. Of course is important to eventually learn working without the crutches of IDE, so you can fix code without it if you need. But to avoid it entirely just does not make sense. If IDE increases coder's productivity, only coder who does not care about productivity would not use it, IMHO. pain is good if you gain something, but pain without the gain?

> **CptPicard said:**
> What do you gain by taking the pain voluntarily? I would never want to work for a company that outright bans tools because it ensures their programmers "know what they are doing".

As a matter of fact, on second thought I might even recommend an IDE to a n00b after they get the basics. It guides them as they code, constantly teaching, and they don't need to waste time browsing the API docs "manually" all the time. After all, if IDEs are for incompetents, then they are almost by definition for beginners :)

It's not without gain at all.

Think of it like this: Dreamweaver is for all intents and purposes an IDE, just with a slightly different focus than most IDEs (in that it can do WYSIWYG type stuff), but that doesn't affect the process a whole lot. Anyway, we all know what kind of awful, terrible, hideous chaff code that Dreamweaver produces - and people who do use it end up with often non-compliant or outright ugly code in their sites. It isn't that IDEs can't write proper code - they can. It's that the IDE doesn't have the human sort of thinking to step back and say "Is that the most beautiful, most logical way I could've written that code?"

IDEs will nearly always produce the *right* code on a literal level, yes; however, they will not step back and ask if there was a better, cleaner, more elegant way to do it. When the IDE tells a user that this code is what they want, they're missing out on a key aspect of development: self-revision. In all reality, coding should be akin to writing a good essay or speech in that the original first draft is the easy bit: the hard part is spending hours scrutinizing every detail in your work to make sure that it is really of the quality one should expect. IDEs generally completely circumvent this.

When users are taught to code in an IDE they generally completely miss out on why asking ourselves this question as we code is entirely critical to producing good results. This is why I'm very much opposed to IDEs.

Newer users especially should be learning and using these concepts *constantly*, and IDEs don't force one - let alone encourage one - to use them.


Edit: ThinkBuntu reminded me of something else every programmer should be excellent at: recursion!

Example from The Little Schemer:
```
(define member?
  (lambda (a lat)
    (cond
      ((null? lat) #f)
      (else (or (eq? (car lat) a)
                (member? a lat))))))
```

---

### Post by nhandler on 2007-11-07
The biggest suggestion I have is to set goals for yourself. If you don't have any reason to program, you will stop when you run into your first problem. As a result, you will never learn. If you set a goal, you have a reason to program (to complete the goal). From there, you can ask for help on forums/google when something doesn't work.

Also, the hardest part about programming in any language is getting the right mind set. The best way to practice this is through pseudocode (google it if you don't know what it means). Simply write out various programs using pseudocode. Then, while learning to program, turn your pseudocode into real code. This will help you get the right mindset and learn to program.

---

### Post by pmasiar on 2007-11-07
> **Cheater said:**
> If you set a goal, you have a reason to program (to complete the goal).

exactly

> The best way to practice this is through pseudocode 

Python is **executable** pseudocode :-)

---

### Post by pmasiar on 2007-11-07
> **ButteBlues said:**
> Dreamweaver is for all intents and purposes an IDE, just with a slightly different focus than most IDEs (in that it can do WYSIWYG type stuff), 

I disagree. Dreamweaver is WYSIWYG webpage GUI tool. IDE, like eclipse, **always** shows the source code, just helps me to write and refactor it faster. There is no hiding.

HTML is not a programming language, tool to simplify HTML design cannot be considered IDE in my understanding of what programming IDE is - with HTML there is no programming at all.

---

### Post by Perpetual on 2007-11-07
For someone who has no knowledge of coding but wants to learn, do all of you suggest going to school for beginners or is coding something one can teach themselves?

If it is something a person can teach themselves, what language is 'best' to learn first and is there a 'bible' of sorts for that language to get a person going in the right direction?

---

### Post by LaRoza on 2007-11-07
> **Perpetual said:**
> For someone who has no knowledge of coding but wants to learn, do all of you suggest going to school for beginners or is coding something one can teach themselves?

If it is something a person can teach themselves, what language is 'best' to learn first and is there a 'bible' of sorts for that language to get a person going in the right direction?

Teach yourself. 

My wiki will help you, probably. 

I would suggest Python, because it will teach common programming concepts in a syntax that is easier to understand. After learning Python, learn other languages should be easier.

---

### Post by pmasiar on 2007-11-07
My wiki has links to tutorials especially for beginners, and training tasks to help you learn more.  Tasks are selected as to be simple (no GUI needed) etc.

The only way how to learn programming is to program. Python is very suitable for beginners, more than almost any other language, and best from "mainstream" languages.

---

### Post by Perpetual on 2007-11-07
LaRoza, pmasiar, thanks a lot for the response.  Will be doing some reading.

Thanks!

---

### Post by ButteBlues on 2007-11-07
> **pmasiar said:**
> I disagree. Dreamweaver is WYSIWYG webpage GUI tool. IDE, like eclipse, **always** shows the source code, just helps me to write and refactor it faster. There is no hiding.

HTML is not a programming language, tool to simplify HTML design cannot be considered IDE in my understanding of what programming IDE is - with HTML there is no programming at all.
The function of the applications and its relation to the format of output (since Dreamweaver handles PHP + HTML) is exactly the same and the comparison remains valid.

---

### Post by slavik on 2007-11-10
HTML IMO is much like TeX ... a type setting language.

---

### Post by intelligentfool on 2007-11-16
after reading this thread, i'd like to start learning python. my question would be though are most FOSS apps written in python? Ie. Firefox, Pidgin, Open Office, etc etc.? what about Ubuntu itself? after i get some basics, i'd really like to start volunteering some time for those projects.

---

### Post by pmasiar on 2007-11-16
1) Some apps are in Python, but not all. Most "huge apps" like Firefox and OpenOffice are written in C or C++, you need to check every project.

2) Those ""huge apps" are so vast (million lines of code) that it is near impossible for a beginner to comprehend them - so i would recommend to start with some smaller projects. Wiki in my sig has links to training tasks.

3) "Ubuntu itself" prefers to use Python, but app distributed within ubuntu can use any language **developers of that project** prefer.

4) Don't think that Python is the last language you learn as professional programmer - it is the first, is rather useful for 80% of what you can do, but it is not end-all. Only if you end up as non-programmer (scientist or something), Python might cover 100% of your limited needs. As such, is very good first language. No other language (like C, Java, Fortran or PHP) could serve as your only language, but Python, with some stretch, can.

---

### Post by Kadrus on 2007-11-18
> **intelligentfool said:**
> after reading this thread, i'd like to start learning python. my question would be though are most FOSS apps written in python? Ie. Firefox, Pidgin, Open Office, etc etc.? what about Ubuntu itself? after i get some basics, i'd really like to start volunteering some time for those projects.
Big projects,like operating systems are mainly built with C...Python is a strong language and you can develop with it some good projects..

---

### Post by charlie763 on 2007-11-19
> **intelligentfool said:**
> after reading this thread, i'd like to start learning python. my question would be though are most FOSS apps written in python? Ie. Firefox, Pidgin, Open Office, etc etc.? what about Ubuntu itself? after i get some basics, i'd really like to start volunteering some time for those projects.

In college I had taken two programming courses; one c++ based and one Java based. I remember all the brackets and terms that I didn't understand to be distracting and confusing. A few years later I started hearing about Python. After looking at how easy it is to understand, I was hooked.

After a few days I jumped right into learning how to make GUI applications after seeing how easy it is to do with Glade and Python.

I would recommend to any novice programmer that they give Python a try. The syntax is easy to understand and it's not too difficult to make GUI applications.

Anyone interested in working with Glade and Python should checkout this Python application my brother and I have been developing: [Gladex]("http://www.openphysics.org/~gladex/"). We just [announced]("http://ubuntuforums.org/showthread.php?t=617152") the release of Gladex 0.4.1 today. You can use it as a programming tool and use the code to help learn from. If you would like to help with a project, you would certainly be welcome to participate.

---

### Post by shawnhcorey on 2007-11-23
If you are a beginner, I would suggest a modern language like Perl, Python, or Ruby.  They have several advantages.
[LIST]
[*] Their data types are closer to how people think about information than other languages.
[*] They're popular enough so you can get answers to your questions quickly.
[*] They do not enforce pre-allocation of memory.
[*] They automatically deallocate freed memory (for the most part).  Don't worry if you don't understand this.  Choosing one of these language is because you don't have to understand this.
[/LIST]
Of course, each one have its own problems, which can give you the feeling that what tripped you up was a deliberate trap.  It isn't.  It's just that the language was created before the problem was known.

Some of the differences between these languages are:
[LIST]
[*] Python has a clean syntax for simple problems but complex problems have complex solutions (just like every other language).
[*] Perl, at first, looks noisy, but the "noise" gives hints about what is happening.
[*] Ruby is object-oriented but objects are not the only way to think about programming.  (If they were, everybody would have adopted them by now.)
[/LIST]
As a beginner, I would not worry about other languages.  They all have their strengths and weaknesses.  But if you learn one language, learning others is much easier.  Everything you learn in one language can be transferred to another, except for the syntax.  The trick is to figure out the syntax to make the program do what you want it to. :)

---

### Post by Chayak on 2007-12-11
Well my real introduction to programming was when I was given the job of working with AUVs (Autonomous Underwater Vehicles) It wasn't any standard code but it was C based so I kinda got my head around the conceps and learned by playing with the simulator how to program the vehicle.

I'm currently, if slowly, learing C because I want to and things like spacecraft flight computers, AUVs, UAVs, and robotics have always facinated me and C appears to be the standard that much of the equipment works on with most of the code running on hardware level or VxWorks.  I have noticed some linux showing up here and there but for the moment VxWorks has the lions share.

Anyone know any good resources for C?  I really should get around to taking classes on it since I learn better that way.  I've been looking for an online course though I haven't found anything that's got me to shell out the cash for yet.

---

### Post by samjh on 2007-12-11
> **Chayak said:**
> I'm currently, if slowly, learing C because I want to and things like spacecraft flight computers, AUVs, UAVsYou should learn Ada for that.  It's the most popular programming language for aerospace and avionics systems.

On second thoughts, perhaps it would be better to learn C first: it's a simpler language.

Anyway, if you want to have a look at Ada, I've written a first-step tutorial for Ada on LaRoza's wiki: [http://laroza.wikidot.com/ada](http://laroza.wikidot.com/ada)
A slightly more complex example in the first post in this thread: [http://ubuntuforums.org/showthread.php?t=497579](http://ubuntuforums.org/showthread.php?t=497579)

More stuff:
Intro information: [http://en.wikipedia.org/wiki/Ada_(programming_language](http://en.wikipedia.org/wiki/Ada_(programming_language))
Comprehensive wiki-book: [http://en.wikibooks.org/wiki/Ada_Programming](http://en.wikibooks.org/wiki/Ada_Programming)

> Anyone know any good resources for C?  I really should get around to taking classes on it since I learn better that way.  I've been looking for an online course though I haven't found anything that's got me to shell out the cash for yet.A lot of online C tutorials are dodgy, often teaching non-standard C.

The C tutorial here isn't too bad: [http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)
But beware!  The first line of the first program should read:
[FONT="Courier New"]#include <stdio.h>[/FONT]

Good luck.

---

### Post by Balazs_noob on 2008-01-20
maybe this will be helpful for a few people too ;)
[http://users.actcom.co.il/~choo/lupg/essays/becoming-a-real-programmer.html](http://users.actcom.co.il/~choo/lupg/essays/becoming-a-real-programmer.html)

---

### Post by Kivech on 2008-02-24
Coming from a professional development background and having grown to executive level in software development, I see a couple of fundamental errors being made in the OpenSource community.

The biggest one of this I personally consider poor planning. You cannot code without proper planning. Others already emphasized the importance of proper documentation, version management, etc. I'd like to point out planning of the phases of a software development cycle.

These are roughly the phases one needs to take into consideration:

1) An **idea** is born. (wouldn't it be neat if I were to make this or that kind of software).

2) Make a **rough sketch** of how it should work. A simple flow diagram of any sort will work (can be made up by yourself, as long as you make some sort of sketch of how you would like the program to work).

3) **Analyze** if your sketch makes sense, if it would work in the **environment** in which it has to work (technically) and if it works for the ones who need to work with it (**the users**), even if that user is just you.
*In a professional environment one would analyze first, but if your project is a small one, you can do it in this order just as much. For larger projects however, make your analysis first.*

4) Make your first **design** of your program. This can be simple, or complex. Better to start with something simple though.

5) Through out all of this don't forget to **document** your concepts, your ideas and your layout of your modules/software. Even small notes will do for this at the beginning, but once you get to designing, you need to seriously document your project. *Usually you spend 60% of your developing time on documenting your project!*

6) Now is a good time to start **coding**. You'll notice that on the go you will repeat most of these steps, as programming is in a lot of ways a repeating cycle.

7) Once you have (a part of your) program finished, you need to start **testing** it. This is one of the most work intensive phases, since it incorporates going through all steps continuously every time you run into a problem with your software. Btw, don't forget to **document** any changes you make.

8) And once you think it is done, you start throwing it into the outside world to go for your first **beta**.

Most of all: **start simple** You'll gain better experience when starting easy and not frustrating yourself with overly complex projects. The "hello world" is a good start if you never coded before. Nothing to be ashamed of here. I started like that also when I was 12 years old on one of the first personal computers out there (this was pre Commodore 64 age, for those who knew those).

Anyway, coding is really one of the smallest parts of all the programming you do. Make sure you have a plan. Don't worry if you have to change it, even multiple times, but make one. It will give you a direction and keep you from loosing track of your project.

Lastly: **Have fun!** Some people forget that programming can be quite fun, even if you follow all the rules people lay out in these threads. Nothing more rewarding than making a good application that helps dozens of people that you made from scratch.

Kivech

---

### Post by Fbot1 on 2008-02-24
> **Kivech said:**
> Coming from a professional development background and having grown to executive level in software development, I see a couple of fundamental errors being made in the OpenSource community.

The biggest one of this I personally consider poor planning. You cannot code without proper planning. Others already emphasized the importance of proper documentation, version management, etc. I'd like to point out planning of the phases of a software development cycle.

These are roughly the phases one needs to take into consideration:

1) An **idea** is born. (wouldn't it be neat if I were to make this or that kind of software).

2) Make a **rough sketch** of how it should work. A simple flow diagram of any sort will work (can be made up by yourself, as long as you make some sort of sketch of how you would like the program to work).

3) **Analyze** if your sketch makes sense, if it would work in the **environment** in which it has to work (technically) and if it works for the ones who need to work with it (**the users**), even if that user is just you.
*In a professional environment one would analyze first, but if your project is a small one, you can do it in this order just as much. For larger projects however, make your analysis first.*

4) Make your first **design** of your program. This can be simple, or complex. Better to start with something simple though.

5) Through out all of this don't forget to **document** your concepts, your ideas and your layout of your modules/software. Even small notes will do for this at the beginning, but once you get to designing, you need to seriously document your project. *Usually you spend 60% of your developing time on documenting your project!*

6) Now is a good time to start **coding**. You'll notice that on the go you will repeat most of these steps, as programming is in a lot of ways a repeating cycle.

7) Once you have (a part of your) program finished, you need to start **testing** it. This is one of the most work intensive phases, since it incorporates going through all steps continuously every time you run into a problem with your software. Btw, don't forget to **document** any changes you make.

8) And once you think it is done, you start throwing it into the outside world to go for your first **beta**.


To be fair that's hard to effectively do in a vast environment like open source development.

---

### Post by slavik on 2008-02-24
Combined with the fact that FOSS is never a 'production version' (iow: done).

---

### Post by pmasiar on 2008-02-24
Kivech, you basically described [Waterfall model](http://en.wikipedia.org/wiki/Waterfall_model), which is slowly becoming obsolete approach even for  ["Enterprisey"](http://en.wikipedia.org/wiki/Enterprisey) systems.

For open source, more appropriate approach is [Agile programming](http://en.wikipedia.org/wiki/Agile_programming). Of course it does not diminish role of documenting or testing - but it shows that you add couple of features per iteration, and do many, many iterations, not "one step delivery" of whole product.

---

### Post by DrMega on 2008-02-24
> **Kivech said:**
> 
1) An **idea** is born. (wouldn't it be neat if I were to make this or that kind of software).

I am also a professional developer (in Windows). In my experience there is ALWAYS a step before your point 1. I suggest:

0. A requirement has been identified. Having identified a requirement, this then leads on to your step 1 (but all the while keeping the focus on the original requirement).

---

### Post by LaRoza on 2008-02-24
> **DrMega said:**
> I am also a professional developer (in Windows). In my experience there is ALWAYS a step before your point 1. I suggest:

0. A requirement has been identified. Having identified a requirement, this then leads on to your step 1 (but all the while keeping the focus on the original requirement).

And in between 0 and 1 is the search for existing projects.

---

### Post by pmasiar on 2008-02-24
and step -1: itch. :-)

I start with itch: there should be a better way to do "it", whatever the "it" is. Then I start thinking what the real problem is, research existing solutions, evaluate them, and then decide for learning to customize existing one, patch/enhance, or create new one.

But in Open Source software, it all starts with a personal itch. :-) We don't need to stinking marketoids to come up with an idea. :-)

---

### Post by DrMega on 2008-02-25
> **pmasiar said:**
> and step -1: itch. :-)

I start with itch: there should be a better way to do "it", whatever the "it" is. Then I start thinking what the real problem is, research existing solutions, evaluate them, and then decide for learning to customize existing one, patch/enhance, or create new one.

But in Open Source software, it all starts with a personal itch. :-) We don't need to stinking marketoids to come up with an idea. :-)

The same is true in commercial development, but with more restrictions. If it is more cost effective to by an API or framework than it would to develop from scratch, then that's the way to go.

I always say the art of being a good developer is not simply about having the ability to write good code in your language of choice, it is about knowing how to choose the tools/resources available, and knowing when to write you own code as opposed to buy it in (or in open source, build on somebody elses).

---

### Post by artificialsteve on 2008-03-03
> **shawnhcorey said:**
> If you are a beginner, I would suggest a modern language like Perl, Python, or Ruby.  They have several advantages.
[LIST]
[*] Their data types are closer to how people think about information than other languages.)

I am new to the programming world, but not to computers.  I wish programming could be less like the english/logical way that I think about information, because now that i have seen what's out there, I am getting more and more impatient with the extra time I have to spend figuring out and catering my application to all of the high-level abstraction and proprietary complexity of new languages. I mean, if I can get to point b, starting at point a, who needs to develop it into a 'class of object tag cloud xhtml.net proto-blah blah blah'.....maybe I should just learn assembly language and code in my room by my self.....

* that wasn't directed at you, but inspired by it shawn.

---

### Post by pmasiar on 2008-03-03
> **artificialsteve said:**
> because now that i have seen what's out there, I am getting more and more impatient with the extra time I have to spend figuring out and catering my application to all of the high-level abstraction and proprietary complexity of new languages. I mean, if I can get to point b, starting at point a, who needs to develop it into a 'class of object tag cloud xhtml.net proto-blah blah blah'

You did not mentioned what your experience is, but it seems to be limited by C#/Java. Perl, Ruby and especially Python is exactly like you want: no need to define classes just to return multiple scalars, no need to use OOP at all if your task does not require it. 

In Python, you can completely ignore OOP and program in procedural way if you prefer it that way, and use existing objects if and when you need them.

As I like to jest, Python is Object-oriented, not Object-obsessed like Java is. :-)

---

### Post by Zugzwang on 2008-03-03
> **artificialsteve said:**
> [...] I mean, if I can get to point b, starting at point a, who needs to develop it into a 'class of object tag cloud xhtml.net proto-blah blah blah'.....maybe I should just learn assembly language and code in my room by my self.....

I agree that all this necessary frameworking for every program looks horrible at first, but it isn't as bad as you think about it. Take java for example. A "hello world" example is given in the following thread: [http://ubuntuforums.org/showthread.php?t=713622]("http://ubuntuforums.org/showthread.php?t=713622").
You need 6 lines of code for just one "core" line. That's a 1:6 ratio which is quite bad. But this is only the case because we're dealing with a trivial program. As soon as it gets interesting, it's not so bad any longer. But probably the worst thing about it is that beginners in Java simply have to accept that you have to put all this class stuff in your source before you can do anything with it. Python's approach is probably more pragmatic here (and so was BASIC in the good old days :)).

However, if you reach the point that you're doing non-trivial stuff, the frameworking isn't so bad after all. For the trivial stuff, you can often make copy&paste programming from a Python script or even use the command line utilities.

---

### Post by artificialsteve on 2008-03-07
> **pmasiar said:**
> 
In Python, you can completely ignore OOP and program in procedural way if you prefer it that way, and use existing objects if and when you need them.
)

Hey, thanks for responding to my post. I have been mainly obsessed with cURL, and PHP, since my first web programming gigs have been very demanding on the client-side laziness factor. For example, right now I am making a web form that logs into my client's secure account, accesses three files per day, closes them, puts them into a resource/handle, and spits them out into a custom made spreadsheet application, with conditional formatting etc...I have only been doing this stuff for about 5 months, so I really don't have an opinion on Python, yet from what I have read around here, it's quite popular indeed. 
I am a 'path of least resistance' personality, so cURL/libcURL have been very exciting to discover! Would anyone recommend Python as a full-on web dev tool? Thanks, and as always, i'm reading and reading and reading.

---

### Post by pmasiar on 2008-03-07
> **artificialsteve said:**
> right now I am making a web form that logs into my client's secure account, accesses three files per day, closes them, puts them into a resource/handle, and spits them out into a custom made spreadsheet application, with conditional formatting etc...

urllib can fetch you HTML page, BeautifulSoup can parse it, and there are many ways to format it in Python.

>  Would anyone recommend Python as a full-on web dev tool? 

I would! :-) Django and TurboGears are popular frameworks. They are both different from PHP in sense that instead of mixing all in one file as PHP hackers usually do (clean programming in PHP is possible but not common), they nudge developer into  using [Model-view-controller](http://en.wikipedia.org/wiki/Model_view_controller) design pattern, resulting in much cleaner and maintainable code. But it is painless: ie TG will create running "hello world" application using best practices, so if you just enhance it, best structure is preserved.

---

### Post by artificialsteve on 2008-03-07
> **pmasiar said:**
> urllib can fetch you HTML page, BeautifulSoup can parse it, and there are many ways to format it in Python.



I would! :-) Django and TurboGears are popular frameworks. They are both different from PHP in sense that instead of mixing all in one file as PHP hackers usually do (clean programming in PHP is possible but not common), they nudge developer into  using [Model-view-controller](http://en.wikipedia.org/wiki/Model_view_controller) design pattern, resulting in much cleaner and maintainable code. But it is painless: ie TG will create running "hello world" application using best practices, so if you just enhance it, best structure is preserved.

I will check this out! Thanks.

---

### Post by Kivech on 2008-03-07
> **pmasiar said:**
> Kivech, you basically described [Waterfall model](http://en.wikipedia.org/wiki/Waterfall_model), which is slowly becoming obsolete approach even for  ["Enterprisey"](http://en.wikipedia.org/wiki/Enterprisey) systems.

For open source, more appropriate approach is [Agile programming](http://en.wikipedia.org/wiki/Agile_programming). Of course it does not diminish role of documenting or testing - but it shows that you add couple of features per iteration, and do many, many iterations, not "one step delivery" of whole product.

Well, yes, of course it's the waterfall model. I for sure know that you are using that in your Agile programming. Or are you telling me that you don't design, analyse, code and test?
It doesn't matter in how small chunks you split it up, it matters that you make sure you do your project properly, and I'm convinced, especially for starters, the waterfall model is a good way to learn how to program in a responsible way.

Not doing so, especially for inexperienced programmers usually leads to "spagetti hell", hence the reason I would let beginners use this approach instead of the one you are suggesting.
For advanced programmers, sure, but not for those who have no dicipline in documenting and proper design, not to mention maintenance. Who will take over a project that is not properly documented?

Anyway, take it the way you want. I really don't think it is getting obsolete, since even if you split programming up in smaller chunks, one still uses these steps. Skip one of them, and you end up with a questionable quality product. But that's just my opinion.

Edit: Had another quick look at the definition of agile programming and it basically underlines what it is I'm emphasizing. However, even if the emphasis is put on prototyping (which is basically what we are talking about here) you need to document.

I cannot emphasize this enough. If there is anything lacking in the OS community it is the dicipline to document properly. Far too often it is not clear how things work due to this, and that is only from a user's perspective, let's not even talk about the code.
The main aim of the waterfall model (or any other project management model for that matter: think Prince2) is to make sure that certain basic steps are followed. In this case "control" of the project is the most important factor. 
All these guides are to make sure that the project remains under control. That also means for the future. 

If I make a program and it works now, in a year from now it might have to be changed. Let's say I get killed in an accident in the mean time, someone else will have to take over. Without proper documentation (project definition, analysis, documentation, tests, etc.) it will be quite a daunting task for anyone. Probably, in a lot of cases, it's better to start from scratch. Which in the end costs a lot of time and effort. Worse, the original program will be a waste.

So, better to prevent those things from happening, also for the maker of the program itself (do you still remember the exact structure of your first software product?), by documenting properly and following a decent project routine.
Even your "Agile Programming" method is like that. It just cuts the development cycle in smaller bits (something that is pretty common, even when they didn't have a fancy name for it yet, they used to do this).

I would say that Agile Programming just aims to listen better to the customer than in other models. Yet, even though they might not have been formally incorporated in older models, that doesn't mean it was not part of the workwise of those developers. For sure in my practice as a developer it always has been. Prototyping seems to me something that is used in this as well.

Anyway, enough about the development theories. Maybe you can tell I'm passionate about the subject. :lolflag:

My point was just: use structure and document.

Kivech

---

### Post by pmasiar on 2008-03-07
It is not about skipping steps. Waterfall is about one iteration - one chance to hit or miss. Agile process is about taking repeated measurements, repeated tries, learning in the process what solutions should be. Learning for programmers, and also for customers.

As they say: it is easy to walk on water and code according to specifications - if both are frozen solid. :-) But if they are fluid, it is much harder.

---

### Post by Kivech on 2008-03-07
> **pmasiar said:**
> It is not about skipping steps. Waterfall is about one iteration - one chance to hit or miss. Agile process is about taking repeated measurements, repeated tries, learning in the process what solutions should be. Learning for programmers, and also for customers.

As they say: it is easy to walk on water and code according to specifications - if both are frozen solid. :-) But if they are fluid, it is much harder.

Hehe, nice quote.

I don't think the waterfall model is about one hit or miss at all. One goes through several cycles in one development cycle. Maybe that is not strictly the doctrine of the model, but in my professional experience it works like that. One never just does one hit or miss run. 
Honestly, I've been in the business for quite some time now, but never have I seen it applied like that though. Wouldn't make sense to me either.

Anyway, not saying I don't agree with you. I just see the waterfall model as a dynamic one. One run per iteration, and yet, one should have several itterations per project.

Btw, nice to run into someone who's a bit more into the theory behind the developing as well. ;)

Kivech

---

### Post by CptPicard on 2008-03-07
My main client and me have this sort of vodka-fall-and-err-and-redevelop-and-redo kind of mutual assured destruction development model. Every few months we get together, get drunk, talk about the next few months' worth of work. Something gets done, eventually we find out that we disagree about what is to be done and how, then we shout at each other, find out that we have way too much to lose if the project fails, we make up, we find a way to make it work... both take a bit of losses to what we expected and then everything is great again and we start over.

Our discussions can be interesting as he is a Mensa member who quit engineering studies early because of "late puberty" (around 25 or so), but he's really great at his own domain... and I'm the more formally educated type who is trying to follow his "practical" reasoning and turn it into actual efficient working code. It works great, it's not agile, but it's fun and profitable.

---

### Post by PanP5 on 2010-04-09
Can someone please recommend a good book on Unix/Linux OS programming? Something that discusses processes, creating threads, zombie processes, etc?

***EDIT***

Ack! Sorry. I found this in the FAQ, but somehow missed the [_"Programming Books" recommendations thread :(_]("http://ubuntuforums.org/showthread.php?t=661754")

---

