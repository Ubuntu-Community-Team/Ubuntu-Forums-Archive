---
title: "What Should I Learn?"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by chandler_bailey4 on 2013-10-01
Hi all,

I'm a 15-year old high school sophomore and I'm highly interested in learning how to code. In the future I would like to work for a company such as Canonical while working on the Ubuntu project. I am tech-savvy but have no prior experience with programming (although I'm taking Web Page Design this year). 

What languages of code would you all recommend me to learn and how should I go about doing so? Any books to read, specific tools/sites to use, or anything else you can help me with?

Thanks a bunch,
Chandler Bailey

---

### Post by Prime624 on 2013-10-01
C/C++ is common in game design.
Java is cross-platform and is my favorite for that reason.

I personally prefer Netbeans to code/compile.

While web page design is a start, it's hardly programming. Teaching yourself programming isn't as hard as it seems. I am semi-self-teaching Java, while taking a Java class (I know all the stuff being taught before it's taught, but I am learning better coding practices). Forums are always a great place.

Whatever you do, practice helps. Learning by necessity is a lot better than learning by book. Don't learn arrays until you have a chance to use them.

---

### Post by Vaphell on 2013-10-02
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) <- Programming talk, look at stickies

for beginners python is a good choice: it belongs to Linux Standard Base (=there is an expectation of linux distro always having python installed) and it's extensively used to write tools in Ubuntu, eg Software Center. It's expressive, you don't get bogged down with serious amounts of boilerplate code you'd have to write in other languages operating on lower levels of abstraction and has a ton of libraries that can be imported and do stuff for you.

In the end programming is about thinking in a certain way, if you know one language well you can program in dozens of them after few hours of learning their syntax because they all share fundamental concepts/building blocks.

---

### Post by whitesmith on 2013-10-02
From somebody who's been doing this for longer than you've been alive: learn from the masters. Read *The C Programming Language* by Brian W. Kernighan and Dennis M. Ritchie, despite its age one of the best (if not *the* best) of all programming books. Read *The C++ Programming Language* by Bjarne Stroustrup. The oldest editions are the best. Forget Java. It's so insecure most shops won't allow it in the door. For scripting I would go with *Programming Perl * by Larry Wall. Perl, it is said, is the glue that holds the Internet together. The right books, plus an active and curious mind, can translate to success. There's lots of work in front of you, because you'll also have to master at least one operating system. *nix is usually the best choice there Good luck!

---

### Post by Vaphell on 2013-10-02
Not so sure about perl. Sure, it's powerful but its nigh unreadable syntax is simply brutal for newcomers. In mainstream use it gets superseded by a more verbose but infinitely more readable and maintainable python, ruby, etc.

---

### Post by buzzingrobot on 2013-10-02
Follow your own interests where they take you as far as specific languages are concerned. 

But... languages are tools to express ideas.  Knowing the syntax of a language isn't that useful of you don't know how to express your ideas in it.  E.g., you can memorize how to create a pointer in C.  Will you know, though, when it's appropriate to use a pointer and when it isn't?

So, think about the fundamentals:  Algorithms and data structures, (which are better for what tasks, and why?) something about operating systems, etc.  It's the difference between being a chef and a cook who has memorized some recipes.

---

### Post by Impavidus on 2013-10-02
I started with C. I'm not telling you that's the best way to start, or even that there is a single best way to start, but it worked for me. Most big projects, like the Linux kernel itself, are coded in C or C++. Smaller things, where performance is less important, are often scripted in python or perl.

As a sidenote, I once started writing a game. I still work on it sometimes. I wanted some elements of to be controlled by separate scripts, so I needed to include a script interpreter. The thing with scripts is that the easier the scripting language is, the more complicated writing the interpreter becomes. I decided on using a simple interpreter and a complicated scripting language. It's written in reverse polish notation and uses a single stack to store all functions and data, including arrays that themselves can contain both functions and data. It was really fun writing that and it makes you think on how computers actually work. I got the idea from writing some PostScript.

---

