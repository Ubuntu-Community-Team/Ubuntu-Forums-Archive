---
title: "I want to learn more.  Suggestions?"
date: 2008-11-06
forum: Programming Talk
---

### Post by lariosa42 on 2008-11-06
Hello,

I am fairly new to Linux (replaced XP with Ubuntu 5 months ago).  I have since been having a lot of fun with the command line, ssh, etc.  I have also been taking some basic computer-based classes to supplement my math PhD (easy stuff like html, LaTeX, Matlab, Ada).  I am finding that I really enjoy this stuff.  While I will never be a professional programmer (math takes up most of my time), I would really like to learn to as much as I can.  I have been reading through "A Practical Guide to Ubuntu Linux" by Mark G. Sobell which has been helpful.

Some topics I am interested in right now include: how computers and file structures work, how to program in C++, how to master the command line, and learning more about ssh/networking.  There are probably also many things that I don't even know about that I should try to learn.

I will need some comprehensive-but-not-watered-down intro-level material, as well as some resources for when I improve.  Books and websites can be helpful, but some of them are a little too specific.

I am really excited to learn more!  Can anyone suggest some resources or ideas to help get me started?

Thanks in advance!

---

### Post by LaRoza on 2008-11-06
You had vague criteria, so I suggest you try out my site and wiki.

---

### Post by jimi_hendrix on 2008-11-06
> **lariosa42 said:**
> how to program in C++

save this for later...C++ is very complex

---

### Post by Pagh on 2008-11-06
@OP Hey if I were you - I would start by learning a nice scripting language like perl or python. (perl tutorial: [http://wwwacs.gantep.edu.tr/docs/perl-ebook/](http://wwwacs.gantep.edu.tr/docs/perl-ebook/) Python tutorial: [http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)).

This is a perfect way (that's my opinion at least) to ready yourself for the challenge of learning C++ while learning more about computers, Ubuntu and Linux in general (including the terminal :-D). 

@jimi_hendrix  I totally agree - C++ is not a good choice as your 1st language - start out with something more simple and then go on to C++ (A good page that i learned my cpp from: [http://newdata.box.sk/bx/c/](http://newdata.box.sk/bx/c/) - this tutorial covers basis c++ (exclusive GUI="Graphical User Interface" - for that i recommend QT4 or WXwidget search google for their home pages where you will find documentation and tutorials). When you have learned basic C++ and gotten used to it i recommend the book - "Effective C++" by Scott Meyers - (you can most likely buy it on amazon or something like that) It meant to improve the way you work as a C++ programmer.

Hope this covers all of your questions - if not then remember: "Wikipedia, Google and forums are your friends :lolflag:" 

All the best (and very good luck) - Kasper Roland Pagh, Denmark.


Ps. Notice that this i only my opinion on the matter - someone might have completely other opinions regarding what languages you should learn or what resources to learn from. Learn from everyone and create you own opinion :-D

Pps. Sorry for my bad English - hope you were able to comprehend me :-)

---

### Post by jimi_hendrix on 2008-11-06
well like Pagh said i would recommend python or perl or any other simple language that gets stuff done and is popular i personally dont like python but thats just my opinion...you might like i though

---

### Post by lifestream on 2008-11-06
> **jimi_hendrix said:**
> save this for later...C++ is very complex

**Don't** save this for later  :) You won't regret it. It's hard, but you sound like you got the smarts to handle it.

I know many people whose first language was C++, myself included, and we're doing just fine. Oh, did I mention that, unlike yourself, none of us is going for a math PhD? :)

I recommend these fantastic free C++ books:
[http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)
Which you can buy, OR [download for free]("http://www.mindview.net/Books/DownloadSites").

---

### Post by slavik on 2008-11-07
since you are into mathematics, I would suggest Haskell, because it is a language following the functional paradigm (functions and symbols, like math, no variables and such stuff).

---

### Post by CptPicard on 2008-11-07
+1 for Haskell... C++ really is much too steeped in the "software engineering" side of things. For a mathematician, functional languages come much more naturally and allow looking at problems from a high-level abstract perspective.

Then there's Lisp... it's more of a "linguist's language" in some sense but is in the functional family as well (though Common Lisp is very clearly multi-paradigm).

If you want to look at stuff from the "finding sets of values that satisfy predicates" direction, check out Prolog.

---

### Post by lariosa42 on 2008-11-07
Wow!  Thanks to everyone for the tips.  I hadn't even thought about starting with Perl, Lisp, or Python, and I hadn't even heard of Haskell or Prolog.  

lifestream-
Thanks for the encouragement--I might take a peak at C++ just to see for myself how tough it is, and also so that I know what I will be up against.

Pagh-
Thank you for all of the resources.  I will definitely check these out.

Thanks again everyone.  I can't wait to get started!

---

### Post by Delever on 2008-11-07
> **jimi_hendrix said:**
> save this for later...C++ is very complex

I keep hearing that all the time, yet I myself had to learn basics of assembler language as part of computer architecture course at first semester. It helped to understand many concepts early on, which would be impossible to see using high level programming language.

C++ may be deep to dig into at first, but basic C is definitively rewarding if you are seeking to learn more (asm is out of question, it was pain).

---

### Post by fiddler616 on 2008-11-07
Though I'm a huge Python fan myself, I don't really think it's the right programming language for *you*. It seems more like it'd be a good third or fourth language, IMHO.

---

### Post by CptPicard on 2008-11-07
This is the age-old discussion, but it's worth reiterating, so... :)

> **Delever said:**
> I keep hearing that all the time, yet I myself had to learn basics of assembler language as part of computer architecture course at first semester.

Actually, assembler or C are not "difficult" in the sense C++ is difficult -- both asm and C are "small" languages, which are used in a somewhat straightforward way. Asm and C are not even really "hard" per se, but just make you do a lot of work to get stuff done because you have to build stuff from scratch. In C++ there is much more "idioms, paradigms, design patterns" what have you you have to master before you are competent in the language, and are able to recognize all the ways you can trip up with it.

> 
 It helped to understand many concepts early on, which would be impossible to see using high level programming language.

Actually, as the programmer only just sees and uses a contract of what the language promises to do when something is written in it, the underlying machine is somewhat irrelevant. For example, the concept of pointers is meaningless in higher-level languages for good reason, as the pointer itself is a technical concept... computationally speaking, the higher-level concepts of indirection, arrays, pass-by-reference are handled in more abstract ways in HLLs.

I would even go as far as say that you do not necessarily need to understand these concepts you get from computer architecture class.

However, in HLLs you learn concepts that do not exist in low level languages .... for example, the closure is a rather deep and powerful concept straight out of formal logic.

---

### Post by mattarios on 2008-11-07
yes it is indeed complex

---

### Post by Delever on 2008-11-07
> **CptPicard said:**
> This is the age-old discussion, but it's worth reiterating, so... :)


He said he wants to learn more... ;)

---

### Post by LaRoza on 2008-11-07
> **lariosa42 said:**
> 
I am fairly new to Linux (replaced XP with Ubuntu 5 months ago).  I have since been having a lot of fun with the command line, ssh, etc.  I have also been taking some basic computer-based classes to supplement my math PhD (easy stuff like html, LaTeX, Matlab, Ada).

I just re-tested this, and its results are on target I think. It was written by a genius, so I suggest you try it out: [http://laroza.freehostia.com/home/apps/programming/index.php](http://laroza.freehostia.com/home/apps/programming/index.php)

(Ok, Ok, but it does work)

>  I am finding that I really enjoy this stuff.  While I will never be a professional programmer (math takes up most of my time), I would really like to learn to as much as I can.

You are like me, except the math taking up most of my time (I have a different major). You may end up a professional programmer, but programming is a valuable tool. You may end up using it for your own use, and it will be much more useful to you than working on projects for other people. 

> 
Some topics I am interested in right now include: how computers and file structures work, how to program in C++, how to master the command line, and learning more about ssh/networking.  There are probably also many things that I don't even know about that I should try to learn.

It seems C++ is the focus of many people wanting to learn. C++ is a commonly used language, but it is hardly special. For general knowledge, wikipedia is a great place to start. Just follow the links that catch your interest as you learn. 

> 
I will need some comprehensive-but-not-watered-down intro-level material, as well as some resources for when I improve.  Books and websites can be helpful, but some of them are a little too specific.


Try the language selector and wikipedia.

---

### Post by CptPicard on 2008-11-07
> **LaRoza said:**
> You may end up using it for your own use, and it will be much more useful to you than working on projects for other people. 


+1

Programming is at its greatest when you can apply yourself through it instead of being a code monkey. In particular for a math PhD I can imagine programming should be a great skill, it allows one to really apply the theory to interesting, and sometimes *profitable* applications :)

---

### Post by LaRoza on 2008-11-07
> **CptPicard said:**
> +1

Programming is at its greatest when you can apply yourself through it instead of being a code monkey. In particular for a math PhD I can imagine programming should be a great skill, it allows one to really apply the theory to interesting, and sometimes *profitable* applications :)

It reminds me of: [http://thedailywtf.com/Articles/It_0x27_s_CAD-tastic!.aspx](http://thedailywtf.com/Articles/It_0x27_s_CAD-tastic!.aspx)

Ignore the C++ part, but look at the professor's personal program.

---

### Post by pmasiar on 2008-11-07
> **fiddler616 said:**
> Though I'm a huge Python fan myself, I don't really think it's the right programming language for *you*. It seems more like it'd be a good third or fourth language, IMHO.

Python would be **excellent** match for OP, it was designed to be used by experts who are not CompSci only.

Playing with different kinds of data structures: Python is much simpler than anything else, and more fun.
Quickly massage some text files: Python (and Perl) rule.

See wiki in my sig for links and training tasks.

For different perspective, consider also Forth, or it's newer cousin, Factor: as mathematician, you should like it's concatenative nature. Enjoy!

---

### Post by pmasiar on 2008-11-07
> **LaRoza said:**
> You may end up a professional programmer, but programming is a valuable tool. You may end up using it for your own use, and it will be much more useful to you than working on projects for other people. 

I would strongly recommend against moving to CompSci. Computers are tools - Astronomy is about stars, they don't have 'telescope science'. Computers are just **much** more complicated, but  majority of CompSci is engineering and just good old skills of a craftsman. You are much better off **owning** the problem area and either writing your own programs, or working with group of career programmers to solve **your** problems.

If you want to switch to something else, where your math background is a plus, consider biostatistics instead.

---

### Post by CptPicard on 2008-11-07
> **pmasiar said:**
> I would strongly/ recommend against moving to CompSci. Computers are tools

IMO CS makes a nice minor subject for a mathematician. It's a tool, and it's good to have a good understanding of the tool from the (genuine) CS perspective.

> 
 - Astronomy is about stars, they don't have 'telescope science'.

Exactly, CS is not about computers but about computability. Most CS degrees are dumbed down these days, but doesn't mean we should go along and have any understanding for that. :)

> 
 Computers are just **much** more complicated, but  majority of CompSci is engineering and just good old skills of a craftsman.

IMO CompSci and Computer *Engineering* which is a field of electrical engineering should be kept separate. A Computer Engineer just needs to wire up a CPU and give us the instruction set thank you very much. But then again I am a known CS purist ;)

> You are much better off **owning** the problem area and either writing your own programs, or working with group of career programmers to solve **your** problems.

This is very true. Interestingly though CS is such a crossover science that you most often indeed end up working in some totally different domain where you just apply CS theory to whatever other theory you happen to be dealing with. The universality of CS is its charm in a sense, at least for me. You can pick up just about any field and start considering its computational implications and limitations. For example I have been playing around with algorithmic game theory recently a lot, and there is this remarkable insight that if some economic mechanism is not computable as per computability theory, it is not even *realistic* because it would mean that a bunch of real world people could not actually run the algorithm that produces the result!

---

### Post by lariosa42 on 2008-11-09
Thanks again to everyone.  The Language Selector was especially helpful (thanks LaRoza!).  After considering all of the helpful comments above, it looks like Python and C/C++ would be a good direction for me at first (although I will certainly try out the languages mentioned above).  Python should provide some motivation, and has the added benefit of being the language that Sage uses (Sage is one of the best open-source math programs).  Also, since I'm the kind of guy who likes to dig in deep and get the full story even if it takes some extra time, I think it would be worth it to me to learn C/C++ (learning Assembler sounds interesting, but I think I would be getting in a little too deep for now).

Can anyone recommend a good book on C or C++?  Also, I understand that C++ is sort of an enhanced version of C (I'm thinking maybe C++ is to C as LaTeX is to TeX).  Which is more common?  Which is more versatile?  If I know everything about C++, will I know everything about C, or vise-versa?  Thanks again for your help.

---

### Post by ad_267 on 2008-11-09
> **lariosa42 said:**
> Thanks again to everyone.  The Language Selector was especially helpful (thanks LaRoza!).  After considering all of the helpful comments above, it looks like Python and C/C++ would be a good direction for me at first (although I will certainly try out the languages mentioned above).  Python should provide some motivation, and has the added benefit of being the language that Sage uses (Sage is one of the best open-source math programs).  Also, since I'm the kind of guy who likes to dig in deep and get the full story even if it takes some extra time, I think it would be worth it to me to learn C/C++ (learning Assembler sounds interesting, but I think I would be getting in a little too deep for now).

Can anyone recommend a good book on C or C++?  Also, I understand that C++ is sort of an enhanced version of C (I'm thinking maybe C++ is to C as LaTeX is to TeX).  Which is more common?  Which is more versatile?  If I know everything about C++, will I know everything about C, or vise-versa?  Thanks again for your help.

C and C++ are really quite different and are used differently. C is a lot simpler and more for low level number crunching or writing drivers. Many Gnome applications are also written in C. C++ is an object oriented programming language and is used for larger applications, so I guess it sort of is like TeX and LaTeX. If you know everything about C you wouldn't know much about C++, and if you know everything about C++, you might now most things about C but the programming style is completely different. Someone else can probably explain that a lot better.

If you want to use Python for mathematics then these sites might be worth a read:
[http://scipy.org/Documentation](http://scipy.org/Documentation)
[http://www.scipy.org/NumPy_for_Matlab_Users](http://www.scipy.org/NumPy_for_Matlab_Users)
[http://matplotlib.sourceforge.net/](http://matplotlib.sourceforge.net/)
[http://wiki.sympy.org/wiki/Main_Page](http://wiki.sympy.org/wiki/Main_Page)

[R]("http://www.r-project.org/") is something you might want to check out if you do any statistics (r-recommended package). Also if you're after something for LaTeX editing I've found the LaTeX plugin for Gedit very useful. Another cool thing is this plugin for Inkscape if you want to make any diagrams with it [http://www.elisanet.fi/ptvirtan/software/textext/](http://www.elisanet.fi/ptvirtan/software/textext/)

---

### Post by CptPicard on 2008-11-09
> **lariosa42 said:**
> Python and C/C++ would be a good direction for me at first (although I will certainly try out the languages mentioned above).

If you insist on either C or C++, then by all means pick C. You can use it with Python, and it gives you "down to hardware" view. C++ brings in a lot of object-oriented abstraction which at least in my view makes it a beast of a language -- you get all that and then some in a more convenient package in Python.

> 
Also, since I'm the kind of guy who likes to dig in deep and get the full story even if it takes some extra time, I think it would be worth it to me to learn C/C++

Just don't fall into believing in the typical beginner myth that lower-level programming is somehow more the "real deal" -- you see it here a lot and it is unfortunate. For a mathematician I am certain that a language that at least allows for higher-order functions would be much more satisfying as it will allow you to handle problems and programs expressed in a much, much more natural and clear style.

Actually, even "real" theoretical computer science is much more at home in functional programming languages than the imperative ones...

> (learning Assembler sounds interesting, but I think I would be getting in a little too deep for now).

From Assembler you just really need to know the basic idea. Program is bytes in RAM which consists of opcodes which are the most rudimentary CPU-level instructions (stuff like adding, multiplying, bit operations..). There are registers in the CPU which are a small set of "variables" and then you can shove stuff between registers and RAM. Opcodes operate on registers -- typically either one register or pair of registers (or register plus literal value). Run your list of opcodes against registers and RAM and you've executed your program.

Asm learned, nothing more to it. ;)

---

