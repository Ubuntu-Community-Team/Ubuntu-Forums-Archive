---
title: "what is the most appropriate programming language for basic graphic applications"
date: 2007-06-16
forum: Programming Talk
---

### Post by mozkaynak on 2007-06-16
Hi,
I am a PhD student and I am supposed to develope an observation software so observers will use tablet PC to conduct observations.

A list of tasks will be present on the screen and as the observer observe that task he will click on the screen and when he observe another task then the observer will click on that task's name. so the software will log the name of the task and the time when the task was observed on a text file.

I was thinking using MS Access and create a form with the list of the tasks and once these tasks were clicked, the logs can be kept on a table.

Then I decided to use a programming language (so I can use my own ubuntu machine for coding and development). I was suggested to use Java. I think I can learn it. I have Pascal and Visual Basic Experience.

Can anyone suggest me a programming language and a coding environment for ubuntu?
Please also pass me some details of your suggestion such as which library/component of programming language will help me .
I am a quick learner.

 Observers will use windows tablet PC during observations so whatever I create in Ubuntu should work in windows.

Thanks....

---

### Post by Modred on 2007-06-16
Alright, so I accidentally erased the post I was about to create.  Instead of Java, I would probably use an interpreted language such as Python for development.  You could use the [Tkinter](http://www.pythonware.com/library/tkinter/introduction/) gui module to create the interface, and unlike with Java, you don't need to recompile every time you make some small change (assuming you were using swing or awt widgets with Java).

Of course, the Windows machines are more likely to already have Java installed, but you could also bundle your final product using something like [py2exe](http://www.py2exe.org) so that the observers' computers wouldn't need a Python installation to run the program (or just install Python on the target machiens).

Really, Java would be fine for what you're doing.  But when it comes to text IO with files, Python definitely has a leg up on simplicity, and if you're unfamiliar with both Java's GUI tools and Tk, then it's really a coinflip as to which would be better.  I'd probably still go Python.

I'm writing all of this assuming you'll write the GUI code yourself.  If you use an IDE or GUI builder, then Java might not be so much extra work after all.

---

### Post by samjh on 2007-06-16
Java GUI designed is as easy as Visual Basic if you use Netbeans.  It has a very easy-to-use GUI designer.

For the kind of text-file IO that has been described by OP, the "simplicity" of Python won't have much of a leg-up on Java.

Using Java + Swing with Netbeans and its GUI editor, will be more extensible than using Python + Tk, and probably more efficient.

Netbeas: [www.netbeans.org](www.netbeans.org)
Java tutorial: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

The use case described in the original post could probably be done in just one or two hours in Java, once the language & Swing basics have been learned (which will probably only take three or four hours with prior programming experience).

---

### Post by kknd on 2007-06-16
samjh is wright, Java is a good choice.

If you have knowledge of math, monads and etc, you will find Haskell a good language. You can do a GUI using Glade, and use it in Haskell with the gtk2hs library.

---

### Post by pmasiar on 2007-06-16
> **mozkaynak said:**
> A list of tasks will be present on the screen and as the observer observe that task he will click on the screen and when he observe another task then the observer will click on that task's name. so the software will log the name of the task and the time when the task was observed on a text file.


Although Java is popular in business world and used ofter in enterprise-level programming, Python and EasyGUI will get you to your goal much faster. Just look at easyGUI - it cannot get any simpler than that.

---

### Post by ankursethi on 2007-06-17
Your development time will be significantly reduced while coding in Python. I'd say +1 to Python.

EDIT : I have taken only a look at Haskell, and I must say it's something to consider.

---

