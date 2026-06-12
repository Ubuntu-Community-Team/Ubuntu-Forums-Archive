---
title: "The &quot;Where to Start?&quot; quandary"
date: 2009-12-13
forum: Programming Talk
---

### Post by Datweakfreak on 2009-12-13
Hiya everyone.

A solid three months have passed since I started my Undergraduation in **Electrical and Electronics Engineering**. I'm really interested in programming and stuff, and I get really inspired when I see those projects where people brag with scripts and stuff about developing applications and softwares...Cool stuff, like, for instance, firefox, or utorrent, or media players...It all boils down to some programming language, so there's my reason. :popcorn:

I am accustomed to the basics of **C** and know quite a bit of the basics of **C++** too, as I learnt them both in school. I can develop simple programs like arithmetic calculations, playing around with strings(string.h functions), loops, control structures, etc etc.. :)

Now, this is where my dilemma starts. I'm not sure where I stand - am I a beginner, or am I quite ready to plunge into advanced programming? If so, where do I start? :?

I referred to certain webpages, and **Python** is recommended for 'absolute beginners' almost everywhere. Do I fall under this category, and should I start off with **Python**? Or should I continue with **C**? If I should continue with **C**, please include pointers as to where I can pursue further advancements in my **C** knowledge. Any advice will be much much appreciated. 

Please get me started, or if I've already had the 'start' with school **C**, please give me a springboard to further my programming skills. :D

---

### Post by nvteighen on 2009-12-13
> **Datweakfreak said:**
> 
I am accustomed to the basics of **C** and know quite a bit of the basics of **C++** too, as I learnt them both in school. I can develop simple programs like arithmetic calculations, playing around with strings(string.h functions), loops, control structures, etc etc.. :)

Now, this is where my dilemma starts. I'm not sure where I stand - am I a beginner, or am I quite ready to plunge into advanced programming? If so, where do I start? :?

I referred to certain webpages, and **Python** is recommended for 'absolute beginners' almost everywhere. Do I fall under this category, and should I start off with **Python**? Or should I continue with **C**? If I should continue with **C**, please include pointers as to where I can pursue further advancements in my **C** knowledge. Any advice will be much much appreciated. 

Please get me started, or if I've already had the 'start' with school **C**, please give me a springboard to further my programming skills. :D

You're in a very similar situation to which I was.

I learned Python after C and it was a really enlightening experience. The stickies have a lot of information on resources for learning it, but you'll soonly notice that you won't need anymore because the language is really easy to learn and very simple to use. Exposure to high-level programming will make you see things you very hardly see using a low-level programming language.

But, you should also polish your C and C++ skills; there's always room for improvement.

After Python, I guess you should keep on learning languages depending on what you need. As this isn't your first language, I guess you've already noticed that after you've learned two languages, learning another one gets pretty easy. Why not Perl or Java or Lisp? :)

---

### Post by diesch on 2009-12-13
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html) is a tutorial for programming GUIs using GTK in C and Python - you can use it to learn how to write simple GUIs using GTK and to compare to two languages in respect to this.


In general every programming language has its advantages and disadvantages. Which one you should learn and use depends much on what you want to do and on your personal taste.

---

### Post by grayrainbow on 2009-12-13
C will be more educational, but if you find C++ suited more for you, you probably could use it also for:
[http://en.wikipedia.org/wiki/Linked_list]("http://en.wikipedia.org/wiki/Linked_list")
[http://en.wikipedia.org/wiki/Tree_(data_structure)]("http://en.wikipedia.org/wiki/Tree_(data_structure)")
[http://en.wikipedia.org/wiki/Modular_programming]("http://en.wikipedia.org/wiki/Modular_programming")
And something extremely important and educational:
[http://tldp.org/]("http://tldp.org/")
Btw, if you going to learn this in school in some point, or if you'll going in more...hmm hardware design path, I would say - Learn C, it's really fun, but don't forget that there's parties a young man must be at :popcorn:

---

### Post by CptPicard on 2009-12-13
> 
am I quite ready to plunge into advanced programming?

Yes, it sounds like you are. Especially considering you're in EE, it is likely you will be programming with pieces of hardware a lot, so it is good you know C. (To the resident C/C++ fanboi crowd: yes I do recognize the relevance of hardware-related languages to hardware-related problems). You will probably be using that mostly in your studies, I suppose.

> 
 If so, where do I start? :?


I suppose you'd be better served just improving your understanding of programming in general... but how to do that is always an individual exercise, it is very hard to tell in which order things should be done. In the end it boils down to actually doing stuff... reading and writing code in various languages. At your phase you want to understand how programming languages are constructed in general and language-independent algorithmics -- that will teach you how to solve problems in general, and how different programming languages map to those problem solutions (and why they do things the way they do). That understanding will then generalize to any specific programming language, provided you understand the "style" the programming language designer has adopted.

> 
I referred to certain webpages, and **Python** is recommended for 'absolute beginners' almost everywhere. Do I fall under this category, and should I start off with **Python**?

No, you're not an absolute beginner, but Python is a good language nevertheless. Not only do you want to have a scripting language in your toolkit anyway (I do a lot of text file-based data manipulation), but Python is very nicely designed for various approaches in program design: A lot of the designs that are almost obvious in Python would be very difficult if not nearly impossible to come across in C... and, writing extensions in C to Python is rather simple. My own C coding is these days almost exclusively as shared object extensions to the Python interpreter -- it lets you code the computationally intense/hardware-or-OS-facing parts in C and keep all the rest in Python.

> 
 Or should I continue with **C**?

C alone is a very small language, there is not much to "continue" about it. However, the question is what you are able to actually do with it, and that does not have much to do with your control of the language itself... you should at least read some C code from existing projects to learn some of the idioms. Checking out C++ more would probably not be a bad choice either.

---

### Post by Datweakfreak on 2009-12-13
Thanks a lot, people. Those replies certainly enlightened me. Based on what I have read, I have understood that python is just an offspring of C, so learning C thoroughly would certainly make it easier for me to learn python, won't it? So I'll just skip python for now, and concentrate on C.

---

### Post by CptPicard on 2009-12-14
> **Datweakfreak said:**
> I have understood that python is just an offspring of C

Not in any sense, no. I can't think of anything that would justify such a statement if one doesn't consider the complete trivialities.

And don't be fooled by the nonsensical argument that "the most popular Python *implementation* is in C so the *language derives* from C" -- it is meaningless what language something is implemented in. It could be anything, or it could be a magic abacus.

> 
so learning C thoroughly would certainly make it easier for me to learn python, won't it?

Well, as I said, there is not much to learn in C. And most concepts in Python do not simply exist in C, so it's hard to learn them from it. From C you learn basic imperative control structures and a handful of rudimentary data types, and that's it. Similarly considered, Python incorporates the same ideas as C does, and more (and does away with some that aren't relevant because of its design).

But, I do not want to make this look like an either-or proposition -- as an EE major you should be able to handle both with ease, and they play nicely together as I said. It's just that the "exclusively focusing on C because it supposedly teaches me other languages" idea is wrong to a varying degree...

---

### Post by wmcbrine on 2009-12-14
A lot of languages are derived from C... Python really isn't one of them... although you can tell that it was designed by someone familiar with C.

---

### Post by CptPicard on 2009-12-14
> **wmcbrine said:**
> although you can tell that it was designed by someone familiar with C.

Yeah, as far as being familiar with C means understanding while loops, assignments and functions ;) (and even the style of that stuff derives from Algol, BCPL... not C. Not that it matters any way)

---

### Post by nvteighen on 2009-12-14
Python is just influenced by C, not derived from. It resembles part of the "C philoshophy" in some places... and sometimes it just borrows stuff and ways-of-doing from the C Standard Library, but nothing else.

---

