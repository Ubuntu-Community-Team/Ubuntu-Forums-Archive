---
title: "Learning Programming"
date: 2009-06-26
forum: Programming Talk
---

### Post by Ong on 2009-06-26
I am trying to learn programming and after searching for advice, I decided to start with Python. I have no programming experience at all, and would like to ask whether I should learn Python 3 or Python 2.6. From what I heard, they are not compatible with each other. And what good resources are there to learn Python?
Thanks.:)

---

### Post by billgoldberg on 2009-06-26
I would start with Mono.

It's cross platform and a lot faster than python.

---

### Post by dka on 2009-06-26
Python is a nice versatile programming language. The differences between 2.6 and 3 are negligible for what you need since you are a beginner.  If you want to use python go with the latest stable release because it will give you access to additional libraries and bug fixes.

---

### Post by TomR55 on 2009-06-26
I would begin by asking you: What is it you hope to accomplish with programming? In other words, why do you want to "learn programming?" If that sounds like a stupid question consider that depending upon one's viewpoing computer programming is an exercise in theorem proving or in plumbing. Both viewpoints are correct, from within their respective world views. 

If you want to program in order to automate certain activities, then learning a scripting language, such as Python, Ruby, etc., is an ideal introduction. If, on the other hand, you're interesting in designing web sites or some such thing, then your choice of languages might differ. In the unlikely event that you're interesting in programming as a matter of computer science or mathematical inquiry, then Haskell, Scheme or Prolog would be a more appropriate starting point.

Now, I am a computer scientist and have been for nearly 30 years, so I might be somewhat jaded on the topic ... nonetheless, you might do yourself a favor as at least consider some of the questions above.

In either event, I think that you'll find the the Linux OS supports a variety of languages, and one or two will satisfy your needs. In addition to the language (i.e., the compiler/interpreter), you'll also need to choose an appropriate Development Environment, such as Emacs, or any of the freely-available IDEs that you can obtan via Ubuntu's Package Manager.

As always: the decision is your's.

TomR

---

### Post by nobodygh on 2009-06-26
I learned to program using java. What is nice about Java (for beginners) is that you can use any text editor to edit your code with and then compile and execute your own programs via the terminal. Even Gedit(The default text editor in ubuntu) works nicely for this. Sun has nice Java tutorials on their website([www.sun.com](www.sun.com)).

You'll just need to download the java developer Environment. I can't remeber where I got it, but I'll find out if you are interested.

Oh, and remeber: The convention is that your first rogram should print "Helo World" to the screen. But that's just some perk and not obligatory at all

---

### Post by mc4100 on 2009-06-26
> **nobodygh said:**
> I learned to program using java. What is nice about Java (for beginners) is that you can use any text editor to edit your code with and then compile and execute your own programs via the terminal. Even Gedit(The default text editor in ubuntu) works nicely for this.

You can write C with gedit, compile it with gcc via the terminal and run it, too. Nothing special there.

---

### Post by nobodygh on 2009-06-26
True, my bad

---

### Post by .Maleficus. on 2009-06-26
> **mc4100 said:**
> You can write C with gedit, compile it with gcc via the terminal and run it, too. Nothing special there.
I don't know if I've come across *any* language that requires a certain tool to write the code.

Anyways OP, here's one of the [stickies]("http://ubuntuforums.org/showthread.php?t=1006666") from the Programming Talk forum right here on UF.  It might answer some other questions that pop into your head.  Other than that, I'll second the C# (Mono) or Python recommendation.  C# is becoming a very popular language and Python is great for scripting.  You can't really go wrong with either.

---

### Post by muteXe on 2009-06-26
> **billgoldberg said:**
> I would start with Mono.

It's cross platform and a lot faster than python.

Mono ain't a language is it? :S

---

### Post by billgoldberg on 2009-06-26
> **muteXe said:**
> Mono ain't a language is it? :S

You know what I mean.

Take a look here for more:
[http://www.mono-project.com/Languages](http://www.mono-project.com/Languages)

---

### Post by muteXe on 2009-06-26
Yeah ok i'll let you off :)

OP: C# is a nice language to learn if you wanna learn about OO stuff.  If not, I actually think C is quite a nice language to learn as well as they're aren't many keywords to remember.  Plus the linux kernel is written in C if you ever wanna go messing around with that :)

---

### Post by Mighty_Joe on 2009-06-26
> **dka said:**
> Python is a nice versatile programming language. The differences between 2.6 and 3 are negligible for what you need since you are a beginner.  

This. I have a ton of Python scripts and none were impacted by the changes from 2.6 to 3.  You can get a lot done with Python (speaking as a professional Java programmer).  
[Python for Software Design]("http://www.greenteapress.com/thinkpython/") is a great book to start with, the PDF is free.

---

### Post by niteshifter on 2009-06-26
Hi,

Python is an excellent starting point, well suited for learning procedural programming. Some useful texts:

*How To Think Like a Computer Scientist - Learning with Python* is available [here]("http://www.greenteapress.com/thinkpython/thinkCSpy.pdf"). 

*Dive into Python* - included in the repos package of Python (as of Ubuntu 8.04) browse at file:///usr/share/doc/diveintopython/html/index.html, also available online.

And there's [Python's website]("http://python.org/"). Sooner or later you'll want the Library Reference. This is where to get it.

Like I wrote above - it's a fine language to start off with. It's quite a work horse of a language actually. But it doesn't go quite far enough in teaching another aspect of programming. Consider this next part extra credit / advanced:

A well grounded programmer should be familiar with procedural and functional programming. One of (if not the) best texts on the functional side is *The Structure and Interpretation of Computer Programs*, online html [here]("http://mitpress.mit.edu/sicp/full-text/book/book.html"). It uses a dialect of Lisp called Scheme which you should already have via guile - if not, guile is available from the repos.

Now, back to the basics ...

Don't focus on the tools (editors, IDEs) at first. Gedit is right there in your box, use it. To learn how to program is to learn how to think, fancy editors/IDE (auto-completion, in particular) get in the way of this.

---

### Post by bruce2000 on 2009-06-26
> **Ong said:**
> I am trying to learn programming and after searching for advice, I decided to start with Python. I have no programming experience at all, and would like to ask whether I should learn Python 3 or Python 2.6. From what I heard, they are not compatible with each other. And what good resources are there to learn Python?
Thanks.:)

I believe most developers are still using 2.6, so I would go with that.

This site has a good beginner's tutorial:

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Contents]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Contents")

---

### Post by ~sHyLoCk~ on 2009-06-26
> **Ong said:**
> I am trying to learn programming and after searching for advice, I decided to start with Python. I have no programming experience at all, and would like to ask whether I should learn Python 3 or Python 2.6. From what I heard, they are not compatible with each other. And what good resources are there to learn Python?
Thanks.:)

I would recommend you start off with the basics first , e.g. start with C,C++.

---

### Post by gonzomalan on 2009-07-17
> **mc4100 said:**
> You can write C with gedit, compile it with gcc via the terminal and run it, too. Nothing special there.

this answers a question i had exactly, "can gcc compile programs written using gedit?" I'm basically in the same mindset as the OP's first post, except i want to learn C, or possibly C++

now, my question becomes, how to do this in the terminal? assuming i'm learning C. if someone could point me to a tutorial for gcc, and/or recommend a book to learn C, i'd be grateful.

ty in advance.

---

### Post by lisati on 2009-07-17
> **mc4100 said:**
> You can write C with gedit, compile it with gcc via the terminal and run it, too. Nothing special there.

You can use gedit for practically *any* programming language that uses text that the programmer types in.

---

### Post by Koobelakahn on 2009-07-18
I too am getting back into java programming, and im starting to learn Python. I think i would be better with java for now (more exp. with it)
but if you want to learn Python, i have a PDF that i am learning from, and its a really good one
[http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python)
The pdf is called "A Byte of Python" its a good book.

---

### Post by Finalfantasykid on 2009-07-18
> **gonzomalan said:**
> this answers a question i had exactly, "can gcc compile programs written using gedit?" I'm basically in the same mindset as the OP's first post, except i want to learn C, or possibly C++

now, my question becomes, how to do this in the terminal? assuming i'm learning C. if someone could point me to a tutorial for gcc, and/or recommend a book to learn C, i'd be grateful.

ty in advance.

You might want to check this out:

```
man gcc
```

oh and c++ equivalent compiler is it g++.

---

### Post by TrakerJon on 2009-07-18
> **Ong said:**
> I am trying to learn programming and after searching for advice, I decided to start with Python. I have no programming experience at all, and would like to ask whether I should learn Python 3 or Python 2.6. From what I heard, they are not compatible with each other. And what good resources are there to learn Python?
Thanks.:)


You'll find more tutorials on C++ and java and both are used quite frequently in business. Geany is a nice IDE (integrated development environment) and so is jedit. Gedit is installed by default but you may also want the plug-ins. Other than that I recommend learning perl scripting as well.

sudo apt-get install build-essential

sudo apt-get install sun-java6-jdk sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc

sudo apt-get install geany

sudo apt-get install jedit

sudo apt-get install gedit-plugins

---

### Post by Mirge on 2009-07-18
geany is a great lightweight IDE, but I'd recommend getting the latest version (launchpad has a .deb available for easy installation)... rather than the version (0.16?) that the repositories have.

---

