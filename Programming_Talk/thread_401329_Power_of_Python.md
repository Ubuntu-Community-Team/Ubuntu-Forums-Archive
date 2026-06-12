---
title: "Power of Python"
date: 2007-04-04
forum: Programming Talk
---

### Post by LaRoza on 2007-04-04
Hello, I am new to Ubuntu and interested in learning Python.

UPDATE:

I learned it, and use it all the time.

---

### Post by pmasiar on 2007-04-04
> What can one do with it?

Everything - it is Turing-complete :-) Real-time application are better done in C, but you can integrate C library calls using Python - or write whole app in Python, find 5% code taking 90% of the time, and recode that in C.

> What are its strengths
Easy to learn, develop, read, scales well to bigger problems. Simple is easy, hard is possible.
Flexible data structures. Libraries, community of developers. Shell to test out objects.

> and weaknesses?
Slower than traditional compiled language like C. It might not a an issue: ie for web-based database appliction, most time is used for data access, which is C library call anyway.

> Is it better than VBScript? I hope so.
Most people agree that Python is better. Multiplatform and open, and see strengths above.

> Why does it put so much emphasis on white space instead of {braces}?
Most big projects have coding standards, which recommend to use whitespace like Python, not rely on {braces}, so braces are redundant and might be misleading.

> I would like to learn this language,
[http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

Good luck!

---

### Post by LaRoza on 2007-04-04
Thanks. I will learn it.

However, {braces} are not redundant. What happens if I wanted to send the code in an e-mail, or copy it some where else and the formating is changed?

I must admit, I am used to ending statements with semi-colons; and using {braces}. It is just a preference though from using ECMAScript and C++.

---

### Post by dwblas on 2007-04-04
Guido decided that a structured format was better than free form when he first started coding Python.  C/C++ uses the free form format.  Each programming language is as it is, and we can either use it as it is or code our own.  If you don't like the structured format, then perhaps Python is not a good choice.
[http://en.wikipedia.org/wiki/Free-form_language](http://en.wikipedia.org/wiki/Free-form_language)

---

### Post by LaRoza on 2007-04-04
I'll get used to it.

The reason why I took a dislike to the ws was because the tutorial I had printed out did not show spaces in "if" statements and I received a lot of syntax errors. 

It works fine now. I just have to learn the rest of the syntax.

Do you dislike free form syntax?

---

### Post by pmasiar on 2007-04-04
> **LaRoza said:**
> However, {braces} are not redundant. What happens if I wanted to send the code in an e-mail, or copy it some where else and the formating is changed?

Try this: type in Python shell: "from __future__ import braces" to see if Python will have braces in the future. :-)

Also try: "import this" - read "The Zen of Python":

Readability counts.
Special cases aren't special enough to break the rules.
...

---

### Post by LaRoza on 2007-04-04
I will when I get home, I'm in school now taking advantage of their dsl connection and taking disadvantage of their Windows machines.

Readability does count, but it depends on what you are used to reading, ever see someone learn how to read and write Arabic? (Everything is "backward", relative to English)

---

### Post by pmasiar on 2007-04-04
> **LaRoza said:**
> Do you dislike free form syntax?

I programmed in languages with free form syntax for so many years... I don't dislike it, but I prefer clean Python style. 

One of features all code editors and IDEs have is to outline code properly - like Python requires.

What often happens with freeform syntax is you have to make changes in code of someone else who has different preferences in free form syntax (or does not care about proper code formatting at all). Tehn, before you can start even reading the code to understand it, you need to format it to "normal" standard. It is rather annoying, trust me.

Significant whitespace put me off of Python when I encountered Python first time, and I spent couple years with Perl - which is even more freeform language than average. Perl is jokingly known as "write-only language" - you can write the code but nobody can read it :-), and as an "executable line noise". 

Python is said to be "executable pseudocode" - you can show the code non-programmers and they can have idea what is going on.

---

### Post by LaRoza on 2007-04-04
You're right. I have only been programming for short while. I have no one to talk to about programming. It is frustrating. I have no internet connection at home so I can only use online tutorials at school. I don't have class today, but here I am.

---

### Post by j_g on 2007-04-04
> One of features all code editors and IDEs have is to outline code properly - like Python requires.

Wait a minute. Is this the same guy who said "I dislike IDEs", and now you're telling people to use an IDE like IDLE to better ensure that it handles leading blank space properly for Python???

When I was doing my first Linux project, I decided that I was going to add scripting capabilities to it (ie, to allow the user to write a script to control operation of the executable -- in the Windows world, we call this "automation"). So, I decided to use Python's C interface to add Python scripting. Naturally, I used the same editor to write my Python test script as I used to write my C source, GEdit.

What I quickly discovered is that Python's use of leading white space is not a good idea when using a text editor that is not specifically written to accomodate this Python paradigm. I had to manually make sure, after pressing ENTER, that each line's indentation was either the same, or different, than the preceding line, as needed. I suppose that one can get used to this manual process (if you're not simultaneously using any of the many, many languages that do not require this very Python-unique quirk). But I can definitely see how it can be very annoying. For example, I cut and paste some text from one function into another. Oops. The indentation of the pasted text now isn't want I want. I have to redo it manually. I can certainly see why some people dislike Python's use of leading blank space as significant.

---

### Post by pmasiar on 2007-04-04
> **LaRoza said:**
> You're right. I have only been programming for short while. I have no one to talk to about programming. It is frustrating. I have no internet connection at home so I can only use online tutorials at school. I don't have class today, but here I am.

No problem - I like your attitude! :-) With right attitude, you can overcome all obstacles!

You can download pages (save-as) to a floppy or UBS stick and read them at home. [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart) links online books I consider best for beginners. You can found there also course about data structures, and tasks to solve.

If you can afford only one book, "Python Pocket Reference" is cheap. I'll dig some links to Python cheatsheets and add them to wiki, too. Good suggestion. Can you print at school?

---

### Post by pmasiar on 2007-04-04
> **j_g said:**
> Wait a minute. Is this the same guy who said "I dislike IDEs", and now you're telling people to use an IDE like IDLE to better ensure that it handles leading blank space properly for Python???

Python has cross-platform IDEs. For a beginner, I recommend SPE over IDLE.

Am I allowed to dislike bloated IDE like VS? I don't miss VS at all. I use Eclipse for Java. I was explaining people why most gurus prefer vim/emacs for C/C++ and why it might be better choice. That mention of  IDE was in different context. 

BTW your post is OT here, not related to OP question - are you trying to hijack thread to start flamewars?

> I decided to use Python's C interface to add Python scripting. Naturally, I used the same editor to write my Python test script as I used to write my C source, GEdit.(...)What I quickly discovered is that Python's use of leading white space is not a good idea when using a text editor that is not specifically written to accomodate this Python paradigm. 

All you need to do is to set smart indent, and converting tabs to spaces. Sure, it is *very* bad idea to mix tabs and spaces in Python. It is so bad that IIRC it will be syntax error.

If your editor doen not support that - you choose bad tool for the job. IDLE and SPE are set properly, no confusion.

>  I can certainly see why some people dislike Python's use of leading blank space as significant.

Fine. Python is *not* for those people. I disliked it too, and wasted years with Perl, so I can relate :-)

---

### Post by j_g on 2007-04-04
> All you need to do is to set smart indent, and converting tabs to spaces. If your editor does not support that - you choose bad tool for the job. IDLE and SPE are set properly, no confusion.

I use GEdit to edit my code. Lots of people use GEdit as a "code editor" for lots of languages.

Now you're saying that a Python programmer should use IDLE or SPE because they're especially setup for this Python-unique coding requirement (ie, significant leading spaces). That's entirely different than your preceding statement:

> One of features all code editors and IDEs have is to outline code properly - like Python requires.

Mind you, I don't necessarily think that it's a bad idea to "lock in" code editing to a particular type of tool. I think that Python's choice of using embedded spaces as significant tends to do that, and a "code editor" for Python does not mean the same thing as a code editor for the vast majority of other languages out there. But that's an entirely different picture than the one you painted earlier.

> Python is *not* for those people <who don't like the significant leading spaces requirement>.

Now we're making some headway! This is the first time I've seen you admit that something you happen to like is not what everyone else wants. I have a dream... that one day the world will see you and Steve Ballmer in the same room, and chairs won't be flying in either direction. :lolflag:

But I'm not taking any chances, so I have the tear gas ready.

---

### Post by Wybiral on 2007-04-04
I too use GEdit for all of my coding, from python, C, C++, HTML, to assembly. It's a one-size fits all.

---

### Post by pmasiar on 2007-04-04
> **j_g said:**
>  Lots of people use GEdit as a "code editor" for lots of languages.

Now you're saying that a Python programmer should use IDLE or SPE because they're especially setup for this Python-unique coding requirement (ie, significant leading spaces). 

Seems like it is waste of time explaining anything to you...  I told you that you can use GEdit if you want - just read docs and set tabs be converted to spaces. Not a rocket science.

rest is BS, as usual. I should have ignored you. I will I promise.

---

### Post by LaRoza on 2007-04-05
Anyone have any suggestions for me?

Anyone know of any Forums dedicated to programmers of a specific language? Python, C++, Whitespace, etc...

As to the query above, I can print at school, we technically have a limit, but no one even knows about it. I do have printed-out tutorial pages strewn around my desk and programming books stacked around my chair. Getting to my computers is hard, but once I'm there, I have everything within reach. Thanks for the support!

---

### Post by pmasiar on 2007-04-05
You can always ask questions here. :-) or PM me if you feel too embarrassed.

[http://mail.python.org/mailman/listinfo/tutor](http://mail.python.org/mailman/listinfo/tutor) - for folks who want to ask questions regarding how to learn computer programming with the Python language - looks dead, but you might try. Let us know if it is alive!

To make more space, add a book shelf above monitor :-)

---

### Post by LaRoza on 2007-04-05
I have two bookcases. I had three, but one collapsed on dumped all the books on me.

I have too many computer books for a single shelf.

The book cases are holding my other books.

Python is an interesting language. It has features I wish were present in other languages. Of course, other languages have features I wish were in Python.

Thanks for the support.

---

