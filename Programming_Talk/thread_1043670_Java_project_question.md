---
title: "Java project question"
date: 2009-01-18
forum: Programming Talk
---

### Post by Coldhearth on 2009-01-18
Hi there,

I would like to practice my Java for my college classes with someone who already has some good experience with Java by making a program with that person...
On msn would be ideal to communicate... 
I would like to do this because I think programming a project together with someone who already knows Java is a good learning experience.

Is anyone here interested to do this with me? :) 

Thanks,
Coldhearth

---

### Post by Tomosaur on 2009-01-18
> **Coldhearth said:**
> Hi there,

I would like to practice my Java for my college classes with someone who already has some good experience with Java by making a program with that person...
On msn would be ideal to communicate... 
I would like to do this because I think programming a project together with someone who already knows Java is a good learning experience.

Is anyone here interested to do this with me? :) 

Thanks,
Coldhearth

It is only a good experience if you both work on different parts. Having two people editing the same code is a nightmare (which is partly why we have things like subversion and cvs). I would strongly discourage you from starting a project with somebody else. It is almost always better to start it yourself - get a firm idea of where you want it to go, then invite people to help out if they're interested. Very, very few things which are 'designed by committee' succeed.

You could, however - just find an open-source Java project and take a look at its code, which would probably be a better way to learn imho.

---

### Post by Coldhearth on 2009-01-18
Oh okay thank you for the advice...
I would like to start a project but I actually have no idea what program to make...
I've always wanted to create my own Java based Msn client but that will be a bit to much to start with I think :(

Any suggestions maybe that are good for someone like me...?

---

### Post by HotCupOfJava on 2009-01-18
Well it depends on how much practice you have already had with Java....

Got the basic syntax down?
Know about arrays, ArrayLists, etc.?
Have you used any of the GUI stuff (swing, AWT)?
Tried messing with any of the I/O classes (writing and reading from files)?

I could give a few suggestions, but I wouldn't want to insult your intelligence by assuming you didn't know something that you are already very familiar with. On the other hand, I wouldn't want to sound like a know-it-all by shooting way over your head.

---

### Post by module0000 on 2009-01-19
If you don't know where to start, start at the basics..

Like the poaster HotCuptofJava said, I don't want to insult your intelligence by suggesting projects that are too simple, but also don't want to recomend things over your head...

Here a few project ideas for you that are practical, and 'meet in the middle' as far as difficulty is concerned:

1. a simple chat program, 1 IP to another, learn about sockets!

2. Pong.  The simplest game you ever played, until you try to recreate it.  "Game programming" may not be where you want to go, but writing even the simplest[pong] of games can be more challenging and educational than you thought.

3. Open source projects.  Joining a team of developers working together on an open source project is a great way to advance your programming skills, while receiving constructive feedback and correction from other developers of all skill levels.

---

### Post by Coldhearth on 2009-01-19
I think the things HotCupOfJava said are about thing I have knowledge of.
But like I said I haven't had the opertunity to use any of these all together in a project.
I know some sockets, some I/O some collections but all in simple exercises...
So I need a suggestion for a project to learn from.

I also don't realy like game programming... I would like to write programs in java wit swing and awt later on and maybe later I'll start on the OS level... but that's not for now.

You have any project ideas that are good for someone of my level.
It would also be nice if I could use the program of the project afterwards.

Thx

---

### Post by HotCupOfJava on 2009-01-19
Well - I'll tell you about something I did that you may find challenging and useful. I used to use VIM for all of my code-editing, but there were some features I wanted that it lacks. I wanted it to auto-complete brackets, parenthesis, braces and quotes for me. I wanted to be able to see which line number I was on without having to count each one (for debugging). I also wanted to be able to "browse" for my files without having to know exactly which directory I had saved something in. I didn't want to worry about accidentally hitting a wrong key and creating a new file or destroying one. So - I coded my own text editor for all of these features. Now, something like Netbeans or Eclipse can of course do all of this and more, but I just wanted to keep it simple and lightweight, and I liked the idea of making my own custom editor and reusing it later. So, that is what I did.

There are plenty of Swing components in use of course (JTextArea, JMenuBar, etc). I/O classes get involved for opening and saving files. I did use the JFileChooser graphical interface to help this out (also used FileFilters to help spot ONLY .java files). I even extended the class to append a ".java" to the ends of filenames automatically (so inheritance comes into play). There is plenty to do in the way of String parsing, and you can use the standard String manipulation methods for this or experiment with the regular expressions classes if you want to learn more about that. 

And of course I have been able to use this "project" over and over again for OTHER projects. And I'm always coming back to the source code to add some new feature I dreamed up.

Might be just the thing you're looking for to try something like that.

---

