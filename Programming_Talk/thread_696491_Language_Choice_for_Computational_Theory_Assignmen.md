---
title: "Language Choice for Computational Theory Assignment?"
date: 2008-02-14
forum: Programming Talk
---

### Post by KoRnholio on 2008-02-14
So, I have an assignment coming up later this semester in a Theory of Computation class, and I'm looking for a language to learn by writing it.  Writing everything in Java (what most people do for this assignment) is boring, and I like learning new languages.

The assignment is:
1.  Parse any regular expression into an NFA (non-deterministic finite automata)
2.  Convert the NFA into a DFA (deterministic finite automata)
3.  Minimize the DFA

Currently I know Java, C, C++, PHP, ML, Lisp (actually learning this for another assignment this semester), and Prolog, so those are kind of off the table.

The languages I'm currently considering are:
1.  Python
I've been wanting an excuse to learn this for a while, and I hear its both imperative and functional, which is a plus for me. 

2.  Perl
Seems like an interesting language.  My rationale for including it on this list is that a lot of Perl code seems to include regular expressions.  Of course that isn't logical at all, but if that means that programmers interested in computational theory gravitate towards Perl, then there might be some weight towards it in picking a language for this assignment.

3.  Haskell
I've heard good things about this, but don't know much about it.  If someone makes a convincing argument for using this, I may go for it.

4.  I'm open to other suggestions, if a convincing argument is made.

So, I want input from people knowledgeable in computational theory to weigh in on this.  Remember, I'm not casually learning this language for the hell of it, I'm learning it for a non-trivial computational theory assignment.  I'm fairly interested in hearing from experts on the languages what reasons their language of choice would be well-suited for this application.  I know it 'can' be done in any language, but any language features that help or hinder an assignment like this would be helpful to know.  

Also, the fact that this is an assignment for a grade makes ease of learning a factor as well.

---

### Post by hardyn on 2008-02-14
if you know all of the above python will be a breeze, it writes like english.

---

### Post by LaRoza on 2008-02-14
I don't understand what you are trying to do, not because of your explanation, but because I am not educated in that field.

With that in mind, I cannot recommend a language for your purpose. Seeing you know a wide range of languages, you should be much better suited for chosing a language.

For you, I think browsing wikipedia's entry on each language will help you make your decision.

---

### Post by CptPicard on 2008-02-14
My wisdom regarding school assignments would be that you shouldn't combine several learning experiences into one, you'll just make life more difficult for yourself. After all you have a deadline too. Use the language you know best, and do additional learning on your own time, when you can afford to fail the experiment.

I've got to second Python too, though... Java forces you to do much more "architecturing", and Python's dictionaries are just perfect for your automata's transitions.

My condolences btw... can't imagine anything more non-educational and an intellectual waste of time than doing theory of computation by coding... :(

---

### Post by Mr.Carramba on 2008-02-14
as mentioned before I would suggest to use language you already now, since the point of Computational Theory (CT) is to learn about it, not to learn new language. If you start working with assignment and new language you effort will by in learning new language and less on learning CT. So fockus on whats intendet to learn ^^

---

### Post by pedro_orange on 2008-02-14
Aye do it in something you know.

Then you can spend more free time going out to the pub. Thats what unis about!

---

### Post by uljanow on 2008-02-14
An assembly language would be an interesting choice. Even Turing Machines could be easily written in Assembler because there is no need for a higher level of abstraction.

---

### Post by CptPicard on 2008-02-14
Hmm.. the state graph does benefit greatly from having a good high level abstraction. I fail to see how you'd implement that cleanly in ASM...

---

### Post by uljanow on 2008-02-14
An alternative for state graphs is using functions of type (state x symbol -> state).

---

### Post by CptPicard on 2008-02-14
True. But running the minimization algorithm would be difficult :)

---

### Post by pmasiar on 2008-02-14
> **uljanow said:**
> An assembly language would be an interesting choice.

Interesting like in: everyone will be curious: "what the hell OP was thinking when decided to do it in ASM?" :-)

I do not see any reason to write research version of anything in ASM. Maybe small parts of a production version of some software running in system with little memory - but there Forth would be even better.

Try learning Python over a weekend. If you like it, try prototyping it in Python. If not, use one of the language you know, and learn Python later. You will use it on your next project, because it IS very fast and agile language.

Stay away from Perl - Python can do everything Perl does, with simpler syntax, and unlike Perl, you can understand your code 6 months later.

---

### Post by KoRnholio on 2008-02-15
> **CptPicard said:**
> 
My condolences btw... can't imagine anything more non-educational and an intellectual waste of time than doing theory of computation by coding... :(

It's not as it seems. My professor is very theory-oriented, and dislikes giving a lot of programming assignments.  Actually, this is the only programming assignment of the semester.  We essentially have all semester to work on it.

Thanks for the responses - I think I'll go with Python.  As for the comments about not trying to do two things at once, I already have the other part down.  I know how to do all of the operations in this assignment by hand (NFAs and DFAs are probably the most trivial part of this class), so that's not going to be a problem.

---

