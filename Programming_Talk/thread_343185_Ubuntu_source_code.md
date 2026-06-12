---
title: "Ubuntu source code"
date: 2007-01-21
forum: Programming Talk
---

### Post by meistercobbman on 2007-01-21
Just a quick question that I couldn't find a definite answer to in other posts... what programming language is used to make Ubuntu, and the programs for it? Also, what is this "packaging" method I've heard about (with Ubuntu Studio) that is *not* programming?

---

### Post by laxmanb on 2007-01-21
mostly C/Python/C++.

Some Java is used in OpenOffice.org

---

### Post by Grey on 2007-01-21
Linux is grown more than developed.  The software comes from all corners of the earth, and is a mish-mash of code written by a great many people.  As a result, languages, styles, and everything else vary greatly with each piece of software included in a distro.  Linux is a fantastic example of a place where too many cooks has not spoiled the broth.

But yeah.  Mostly C/C++ and Python.

Packaging is just when you take a piece of linux software, and put it in a nice package for installing in Ubuntu.  Think of it as an installer for Windows.  It's not technically programming, but if the package gets complicated, it can involve some shell scripting.

---

### Post by meistercobbman on 2007-01-21
cool thanks! i'm going to try learning Python since i've heard so much good things about it. i learned what shell scripting is from wikipedia. 

But now i have a new question: if linux is grown using different programming languages, how do they make it work together?

---

### Post by Grey on 2007-01-21
Well, basically what an operating system does is provide a standard interface for programs running in it.  The really low level stuff is all in machine code.  Just 1s and 0s.  It doesn't matter whether you write your code in C, C++, PASCAL, or Ada.  It will all be compiled into assembly, and then assembled into machine code.

On top of this are interpreters.  The interpreters themselves are written in a lower language, such as C, but they take in a language such as Java or Python, and perform the actions that the source code says to do, without actually compiling it down to machine code.

That being said, pretty much all of the really low level stuff is written in C in Linux.  C++ is not well loved amongst the Linux system programmers, and no other compiled language really has the weight to take C off of its throne.  (The reasons for which are beyond the scope of this post)

---

### Post by laxmanb on 2007-01-21
well... you have to use bindings to get programs written in C/C++ to interact with Python... or any other 2 languages for that matter...

---

### Post by meistercobbman on 2007-01-21
so, if i wanted to make a simple program like a text editor with cool backgrounds than I could use Python or C/C++ but it would be a matter of personal preference and not compatibility. Right?

---

### Post by Grey on 2007-01-21
Yup.

---

