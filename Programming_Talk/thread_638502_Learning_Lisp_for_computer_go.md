---
title: "Learning Lisp for computer go"
date: 2007-12-12
forum: Programming Talk
---

### Post by dumbsnake on 2007-12-12
Hey,

    I searched the forum and found a few posts about how to use Lisp, but none of them really answered my questions.  I come from a very solid background in C++ and I've learned a few other languages as well, but it is time for me to learn lisp.

I am going to be working on a program to play the game go (I've previously written this in C++).  I will need access to libraries for dealing with sockets or files (not both).  I don't need any other features.  Speed will eventually be important, but for now learning is most important.

How should I learn the language?  What dielect should I use... etc...  I honestly don't even know what the right questions are and I've been trying to figure this out with little success.  Help will be much appreciated.

Thanks in advance.

---

### Post by pmasiar on 2007-12-12
We had an expert Lisp hacker around before, but he left after some heavy-handed extinguishing of one flamewar, sadly. You can still find and MSG him: lnodstal. He said he prefer to be around usenet forums instead. Or you can start from wikipedia and wikiversity articles about Lisp.

Go is hard, good luck with that!

---

### Post by wolfbone on 2007-12-12
Learning Scheme:

[http://www.swiss.csail.mit.edu/classes/6.001/abelson-sussman-lectures/](http://www.swiss.csail.mit.edu/classes/6.001/abelson-sussman-lectures/)
[videos and textbook]
[http://www.plt-scheme.org/](http://www.plt-scheme.org/)
[DrScheme environment suitable for learning and another textbook]

Learning Common Lisp:

[http://common-lisp.net/~dlw/LispSurvey.html](http://common-lisp.net/~dlw/LispSurvey.html)
[See the Common Lisp Textbooks Available On-Line and Resources sections]

It is probably much easier to learn and use Scheme than Common Lisp. Later on you may prefer the CL way of doing things and e.g. the excellent CL+Emacs+SLIME environment, but either way you'll find that the various different implementations of Scheme and CL have quite widely varying relative advantages and disadvantages.

Speedwise, I wouldn't worry at all though:  [http://norvig.com/python-lisp.html](http://norvig.com/python-lisp.html) [table comparing various languages to C++ half way down the page] What you'd typically do in Common Lisp is write your code as structurally efficiently as possible first, and maybe later go back and put typing hints in for the compiler. For Scheme, you should check out the individual implementations for information on how each deals with issues of efficiency and speed.

---

### Post by skeeterbug on 2007-12-12
[http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)

You can use common lisp (clisp) to go along with this online book.

---

### Post by Majorix on 2007-12-12
> **dumbsnake said:**
> Hey,

    I searched the forum and found a few posts about how to use Lisp, but none of them really answered my questions.  I come from a very solid background in C++ and I've learned a few other languages as well, but it is time for me to learn lisp.

I am going to be working on a program to play the game go (I've previously written this in C++).  I will need access to libraries for dealing with sockets or files (not both).  I don't need any other features.  Speed will eventually be important, but for now learning is most important.

How should I learn the language?  What dielect should I use... etc...  I honestly don't even know what the right questions are and I've been trying to figure this out with little success.  Help will be much appreciated.

Thanks in advance.

Hi, have you checked the stickied thread called "Linux Programming Reference"? There you can find links to Common Lisp tutorials and books.

On a side note, is the reward for a program that can beat a human in Go still valid?

---

### Post by dumbsnake on 2007-12-12
The reward is no longer valid, but we aren't much closer.  It is more for fun that I'm doing this.  I'm not convinced it is even possible with current computers.  Anyway, thanks everyone for your help.  I think I will start with scheme.  I weighed everything posted here and on the computer-go list I asked a similar question on.

Thanks for your help!  I will be looking through all the links you all suggested.

---

