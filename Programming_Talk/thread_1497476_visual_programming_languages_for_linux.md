---
title: "visual programming languages for linux?"
date: 2010-05-30
forum: Programming Talk
---

### Post by steve19137 on 2010-05-30
i once had a lego mindstorms nxt, and it used a graphical programming tool. at the time, i had no idea that i was writing actual programs for a robot, but then again, i never gave it much thought. well, recently i have gotten into computer languages. i started python (twice!) to find that i could never get past learning about modules. i got really hung up on it, and i never figured out why. i tried to pick up C, and i even read the C Programming Language book, the really small one written by the inventors of C. I had heard that it was a great resource for those looking to learn C, but then i realized that it meant that it was great for *current programmers* trying to learn C. ive never been a real programmer. so i thought that i would look into a visual/graphical programming language for linux. are there any out there?

---

### Post by trent.josephsen on 2010-05-30
You can get NI LabView for Linux.  It's proprietary, though, and expensive even at student-discount prices.  I'm sure there are others.  "visual programming linux" brings up quite a few hits, mostly questions very similar to yours.

But in large part you won't find visual programming languages on Unix-like platforms -- not to the same extent as Windows or Mac.  Unix was from the beginning very strongly language-oriented.  There is still a dominant and largely accurate sense that GUIs exist mostly for the convenience of novices and you should use the shell for anything demanding real power.  As a result, there isn't much interest in developing that kind of thing: if you want to learn to program, learn to do it "right".  ;)

Interestingly, some people have said that because the language centers of the human brain are so large and dominate our communicative abilities, written language (code) is a better way to interact with a computer than dragging icons around.  Just try communicating for a day without using words -- just gestures, pictures and facial expressions.  That's like using a GUI:  you can manage it, but it's a lot more work both for you and for the computer.  (Take that analogy with a grain of salt.)

Anyway, I'd suggest Python if you're interested in learning to program, and later Perl and maybe C.

---

### Post by ju2wheels on 2010-05-30
KTurtle (more for kids or absolute beginners to programming)
Alice (based on Java, recommend trying it alice.org, need Alice 3 for Linux)
[http://en.wikipedia.org/wiki/Visual_programming_language](http://en.wikipedia.org/wiki/Visual_programming_language)

---

### Post by juancarlospaco on 2010-05-30
**Try Quickly.**

*I use ed and python*

---

### Post by Redache on 2010-05-31
Python does seem like the best language to start with because it enforces good programming style(which is a hot topic :P) and can get you writing awesome programs quickly. 

I've been learning Python as part of my Google Summer of Code project and a lot of the problems I've had is with trying to translate what I knew in Java to Python, although they are similar in concept they are different in execution.

What issues did you encounter with Modules in Python? I'm sure people here can help you out with whatever questions you have. It's best to stick to a single language and learn that as once you manage to get comfortable with one others are a lot easier to grasp.

---

### Post by mmix on 2010-05-31
[http://en.wikipedia.org/wiki/Processing_%28programming_language%29](http://en.wikipedia.org/wiki/Processing_%28programming_language%29)

> 
One of the stated aims of Processing is to act as a tool to get non-programmers started with programming, through the instant gratification of visual feedback.


---

### Post by kalaharix on 2010-05-31
Hi

Gambas is great and provides a graphical interface to programming. It is object oriented based on a Java model but can be made to behave a bit like VB6. It receives derision from the Linux community because of that, but the fact is that more programmers have started life on visual basic than on Python and TIOBE suggests that more visual basic is used in the real world (particularly small data-based software) than Python. The Linux community is very protective of the geek image and reluctant to let the hoy-polloy join in. They see no correlation between this attitude and the fact that Linux just can't break into the desktop market.

"That's like using a GUI: you can manage it, but it's a lot more work both for you and for the computer. (Take that analogy with a grain of salt.)" Wot a larf! More like Lott's wife I am afraid: Tell me, do you use terminal on your phone or the gui?

---

### Post by ssam on 2010-05-31
have a look at some glade tutorials.
[http://glade.gnome.org/](http://glade.gnome.org/)

it lets you draw out an interface, and then add code that is triggered on events like button presses. you can choose between several programming languages.

---

### Post by trent.josephsen on 2010-05-31
Gambas is not a visual programming language, but an ordinary programming language with a GUI IDE.  There's a **huge** difference.

> **kalaharix said:**
> "That's like using a GUI: you can manage it, but it's a lot more work both for you and for the computer. (Take that analogy with a grain of salt.)" Wot a larf! More like Lott's wife I am afraid: Tell me, do you use terminal on your phone or the gui?

I'm not sure what you mean.  A phone is a simple tool.  You tell it the number and it calls for you.  Neither a language nor a graphical interface is necessary.  What kind of phone do you have?

The analogy was frivolous, meant to convey a position held by some others, and not necessarily by myself (although I think there is some truth in it).  Besides, try "find -name '*.pm' -or -name '*.pl' -exec grep -l Dumper {} \;" in a GUI. ;)

---

### Post by steve19137 on 2010-05-31
i guess ill give python another try. i also like the processing application posted. im going to try that some more.

---

