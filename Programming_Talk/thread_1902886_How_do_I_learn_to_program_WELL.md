---
title: "How do I learn to program WELL?"
date: 2012-01-01
forum: Programming Talk
---

### Post by venom104 on 2012-01-01
I've been a computer science student for many years now. I've taken classes on everything from "introduction to computer science" to XML. Quite honestly, I haven't learned jack **** from classes when it comes to programming. I can do just about ANY programming assignment from any of my textbooks (and I design and code go though the exercises over and over again, just to have fun) but I haven't learned to program well.

Let me give you an example of what I mean by "learning to program well". I was developing a roguelike for a while, and I developed a prototype of a random map generator. But, instead of compiling all my cpp (source) files at the command line, I was using #include directives to include the source files in my program. From the mouths of the roguelike development irc channel that I regularly attend, this isn't what "real" programmers do. Here are a few more examples, I know what a constructor and a deconstructor are, but I don't know what to put in them besides deleting pointers. Also, I was writing a program that told the user how many words he/she/it entered at the command line, using a char * and the new keyword, but I wasn't sure where to delete the pointer because I was returning pointer to a char out of a function. 

Books have taught me so much, but I haven't learned GOOD programming practices and I haven't developed my own style of coding yet. How can I do this?

I'm applying for internships (I don't feel that I am ready to be a real programmer yet) and working on my roguelike and textbook problems, but I don't feel that's enough. I feel like I could benefit from having someone mentor me by giving me problems and grading my solutions, but that's never going to happen.

What can I do to learn how to program well?

And yes, I have looked into the "read before posting" threads here, they didn't answer my question.

---

### Post by ofnuts on 2012-01-01
> **venom104 said:**
> I've been a computer science student for many years now. I've taken classes on everything from "introduction to computer science" to XML. Quite honestly, I haven't learned jack **** from classes when it comes to programming. I can do just about ANY programming assignment from any of my textbooks (and I design and code go though the exercises over and over again, just to have fun) but I haven't learned to program well.

Let me give you an example of what I mean by "learning to program well". I was developing a roguelike for a while, and I developed a prototype of a random map generator. But, instead of compiling all my cpp (source) files at the command line, I was using #include directives to include the source files in my program. From the mouths of the roguelike development irc channel that I regularly attend, this isn't what "real" programmers do. Here are a few more examples, I know what a constructor and a deconstructor are, but I don't know what to put in them besides deleting pointers. Also, I was writing a program that told the user how many words he/she/it entered at the command line, using a char * and the new keyword, but I wasn't sure where to delete the pointer because I was returning pointer to a char out of a function. 

Books have taught me so much, but I haven't learned GOOD programming practices and I haven't developed my own style of coding yet. How can I do this?

I'm applying for internships (I don't feel that I am ready to be a real programmer yet) and working on my roguelike and textbook problems, but I don't feel that's enough. I feel like I could benefit from having someone mentor me by giving me problems and grading my solutions, but that's never going to happen.

What can I do to learn how to program well?

And yes, I have looked into the "read before posting" threads here, they didn't answer my question.
Read existing code. Lots of it. Mostly in the languages you use of course (that may include makefiles...) but sometimes other languages will widen your horizon. Try to understand why things are done that way, and, most importantly, why things were not done the way you would have done them... This will however only give you a low-level view of the code. 

If you want a broader view, usually belonging to a group (open source project, or programming job)  gives you rules to follow, and they usually make some sense.

I'm finishing reading "Clean Code" by Robert Martin, and although it's a bit Java-oriented, it expounds plenty of good principles that apply to all object-oriented languages.

Finally the first requirement to write good code is a healthy dose of self-criticism. Not being happy with the current version of the code even if it does the job is the first step towards good code. Your posting indicates that you are already there :)

Practice, practice,  practice,  practice,  practice...

---

### Post by satanselbow on 2012-01-01
+1 to the above.

Unfortunately / Ironically the key to being good at anything is making mistakes - or more to the point learning from the mistakes you do make.

Only thing I might add about "reading lots of code" is - don't take it as read that the code you read (especially in some text books) is actually good code. 

Critically analyse every line and see if you can do it better / faster / more efficiently. There is plenty of bad code in textbooks and the authors always like to hear from people who can do it better :lolflag:

---

### Post by Lars Noodén on 2012-01-01
As far as reading code goes, it usually only helps if you are looking at good code.  If you are into C, then the best place to start looking would be the OpenBSD project.

---

### Post by CptPicard on 2012-01-01
Use different kinds of languages, to implement different kinds of solutions. Over time, you'll learn a set of higher-level generic ideas, kind of "patterns" that are not dependent on language, but you'll be able to emulate given some given language. Getting that kind of an overall picture of things takes the [famous 10 years]("http://norvig.com/21-days.html"), but after that, you're more of a general "programmer" than just a "coder" in some given language.

---

### Post by cgroza on 2012-01-01
Explore different programming paradigms. They really open your mind and give you fresh ideas. Knowing more of them helps you solve problems more efficiently, since some solutions for some problems tend to make more "sense" in another paradigm than the usual OOP/Imperative one.

---

