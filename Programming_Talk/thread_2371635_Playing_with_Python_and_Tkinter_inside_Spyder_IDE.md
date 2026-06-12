---
title: "Playing with Python and Tkinter inside Spyder IDE"
date: 2017-09-16
forum: Programming Talk
---

### Post by Drone4four on 2017-09-16
I'm trying to run some Python code from a Python "Bookazine" .  Initially the material begins with some Python code for rudimentary rock-paper-scissors and hangman games which would run from the command line.  It&#8217;s been fun to play with.  But now the book ports the game scripts from the command line into Tkinter.  I&#8217;ve encountered a few issues.

[Here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/Main_Interface.py") is the parent (Main_Interface.py) script that I am working with. [Pastebin alternate]("https://pastebin.com/3caj1WJB").

[Here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/rockscissorspaper.py") is the rock-scissors-paper game module I am troubleshooting. [Pastebin alternate]("https://pastebin.com/C1MEcXR5").

[Here]("https://github.com/Angeles4four/PyMag-games") is the main directory for the whole project on GitHub.

When I run the Main_Interface.py script, the window pops up and looks pretty good.  But when I click on the option button to launch the subsequent script, rock-paper-scissors game, nothing happens.

Someone recommended that I begin to use an IDE and debugger which would help me troubleshoot.  So I've settled with Spyder2.  Spyder has identified all sorts of issues with my code. I counted 32 triangles with exclamation marks in my rock-scissors paper script.  Here are some near the top of the script in question:

```
Line 3: 'from Tkinter import *'; unable to detect undefined names
```

I kinda get this one based on a quantifiedcode doc called, "[using wildcard imports (from &#8230; import *)]("https://docs.quantifiedcode.com/python-anti-patterns/maintainability/from_module_import_all_used.html#using-wildcard-imports-from-import")"
which details how it&#8217;s better practice to specify which function within the imported module, rather than importing the entire module.  From the article:

> When an import statement in the pattern of from MODULE import * is used it may become difficult for a Python validator to detect undefined names in the program that imported the module. Furthermore, as a general best practice, import statements should be as specific as possible and should only import what they need.

So this might mean that the authors of the Python Bookazine are teaching less than best practices.  I am reluctant to make the leap to add every single function referred to in the game script because there are so many which leaves alotta room for error.  My question here: Even though it might be better practice to not import everything, still from Tkinter I should be able to import all the functions, right?  

```
Line 15:  local variable &#8216;names&#8217; is assigned to but never used
Line 16:  local variable &#8216;rules&#8217; is assigned to but never used
```

I don&#8217;t understand the issues identified at lines 15 +16 because the variables are indeed defined but they are in fact used shortly there after in the script.  My question: Why is Spyder saying these variables are never used when they actually are? Is Spyder expecting to have variables defined after they are called in a function, rather than the revers?

```
Line 20: 'game' may be undefined or defined from star imports: Tkinter
Line 28: &#8216;names&#8217; may be undefined or defined from star imports: Tkinter
Line 37: &#8216;rules&#8217; may be undefined or defined from star imports: Tkinter
```

The issues identified here at lines 20, 28 and 37 look similar to the issues referred to above. The functions and variables are indeed defined and they are not imported with Tkinter. What is Spyder trying to say here?

I&#8217;m using Spyder v3.1.4 and underneath I&#8217;m running Python v2.7 on Ubuntu 17.10.

Thanks for your attention.

---

### Post by Drone4four on 2017-09-17
In the image linked to below, do you see the overabundance of exclamation notifications next to the line numbers in Spyder?  When I mouse over them, a small dialog pops up and reveals a message, like the ones I shared in my initial post.  What is it that Snyder is telling that I am doing wrong here with every single Tkinter variable declaration / function call? [Have a look.]("http://i.imgur.com/rr4Xl0R.png")

---

### Post by vasa1 on 2017-09-17
You can use the forum's attachment facility to include images in your post. Click on the paper-clip icon. If you don't see it, click on "Go Advanced".

---

### Post by Drone4four on 2017-09-17
Hi **@vasa1**: After clicking Go Advanced, I was able to open the attachments function just fine.  I could see my list of previous attachments, like code samples and images.  I have used this feature on the forums many times.  But moments ago I attempted to attach the image but it wouldn't let me.  I tried in Chrome and Firefox.  Can't figure out why it's not working today.  Ah well.  I removed the embedded image and just turned it into a hyperlink. Is that better?

---

### Post by wildmanne39 on 2017-09-17
The image is probably to large, I had that happen to me a few days ago.

---

### Post by spjackson on 2017-09-18
> **Drone4four said:**
> 
I don’t understand the issues identified at lines 15 +16 because the variables are indeed defined but they are in fact used shortly there after in the script.  My question: Why is Spyder saying these variables are never used when they actually are? Is Spyder expecting to have variables defined after they are called in a function, rather than the revers?

In your function gui() you are assigning to variables that are **local** to that function only. In gui() you create some local variables, assign to them but do not use them in gui(). Once gui() exits, those local variables no longer exist. Elsewhere in your code you are referring to different variables with the same name and those different variables have not been initialised.

See the following where initialise_local() does nothing to the global x, but initialise_global() changes the global x.

```
#!/usr/bin/env python2

x = 1

def initialise_local():
    x = 4

def initialise_global():
    global x
    x = 6

def show():
    print(x)

initialise_local()
show()
initialise_global()
show()


```

---

### Post by Drone4four on 2017-09-22
Hi **@spjackson:**  Thanks for your reply.  You said:

> **spjackson said:**
> In your function gui() you are assigning to variables that are **local** to that function only. In gui() you create some local variables, assign to them but do not use them in gui(). Once gui() exits, those local variables no longer exist. Elsewhere in your code you are referring to different variables with the same name and those different variables have not been initialised. 

Yeah you are so right about the local vs global variables. I can't believe I missed that.  The sample in the magazine actually has the gui() function as the parent, with the other functions indented so the variables declared in the parent are in scope in the rest of the subsequent functions, like game() and result().  So I indented those two, along with the rest of the code in the script. 

When I execute the main script, it runs. That app opens.  But clicking the rock-scissors-paper button doesn&#8217;t open the game like should.  Since I sacked Spyder IDE, and am using Wing IDE, there are no more help tips giving any hints as what the issues are with my code.  I am now proceeding to learn how to use Wingware IDE&#8217;s debugger. 

My updated code with indents on can be found [here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/rockscissorspaper.py")  on GitHub.   Maybe someone can examine or review that problem code sample and make any suggestions.

Thanks for your attention.

---

### Post by spjackson on 2017-09-24
> **Drone4four said:**
> 
My updated code with indents on can be found [here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/rockscissorspaper.py")  on GitHub.   Maybe someone can examine or review that problem code sample and make any suggestions.


I find the source very hard to follow because indentation is done with a mixture of spaces and tabs. This is not a good idea in python: uses spaces or tabs for indentation, not both.

When the button is clicked in Main_Interface.py the function rockscissorspaper.gui() is called but that function doesn't do anything observable. Is it meant to be calling start()?

You can tell that it does nothing by
```

$ python2 rockpaperscissors.py

```

---

### Post by Drone4four on 2017-09-24
> **spjackson said:**
> I find the source very hard to follow because indentation is done with a mixture of spaces and tabs. This is not a good idea in python: uses spaces or tabs for indentation, not both.
I realize that my tabs and spaces are a serious problem with my code samples.  Spyder IDE messed it up.  I am scrambling to clean up Spyder&#8217;s mess. I apologize.

> **spjackson said:**
> When the button is clicked in Main_Interface.py the function rockscissorspaper.gui() is called but that function doesn't do anything observable. Is it meant to be calling start()?

You are right that gui() doesn&#8217;t do anything observable.  gui() merely declares some variables.  So I swapped out gui() with start() at the end but now I get this output:
```

$ python rockscissorspaper.py
Traceback (most recent call last):
  File "rockscissorspaper.py", line 84, in <module>
    start()
NameError: name 'start' is not defined
$ 

```
Here are lines 83 and 84:
```

if __name__ == '__main__':
	start()

```

I&#8217;m thinking that perhaps the tab/spacing alignment of the start() function is the problem earlier on in the script? But if you see [this link]("https://imgur.com/a/HPwtR") for an image of the page from magazine,  start() is deliberately nested within gui().  So how do I properly call start() from within gui() at the bottom of the script with the __name__ conditional?

I pushed my changes up to GitHub. [Here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/rockscissorspaper.py") is the link to the code in question.

Thanks for your attention and your patience, **@spjackson**.

---

### Post by spjackson on 2017-09-27
> **Drone4four said:**
> 
```

$ python rockscissorspaper.py
Traceback (most recent call last):
  File "rockscissorspaper.py", line 84, in <module>
    start()
NameError: name 'start' is not defined
$ 

```
Here are lines 83 and 84:
```

if __name__ == '__main__':
    start()

```

start() is a function nested inside gui(). It is only visible inside gui(), so you cannot call it here which is outside gui(). The __main__ block above is for when the script is called directly, not when it is fired from Main_Interface.py.
> 
I’m thinking that perhaps the tab/spacing alignment of the start() function is the problem earlier on in the script? But if you see [this link]("https://imgur.com/a/HPwtR") for an image of the page from magazine,  start() is deliberately nested within gui().  So how do I properly call start() from within gui() at the bottom of the script with the __name__ conditional?

I pushed my changes up to GitHub. [Here]("https://github.com/Angeles4four/PyMag-games/blob/master/tkinter/rockscissorspaper.py") is the link to the code in question.

Your problem earlier, which is why gui() did nothing, was that the big chunk of code from
```

    rps_window = Toplevel()

```
onwards was indented to be part of the start() function. In the magazine picture, all that code is part of gui() not part of start(). You appear to have corrected that now.

I have made a few corrections (mainly spelling of sticky and column and it now **calls mainloop()**) and it runs for me. I'm afraid that I only dabble a bit with Python and I don't use tkinter at all, so I can't guarantee that I've got this right.

---

### Post by Drone4four on 2017-09-28
> **spjackson said:**
> I have made a few corrections (mainly spelling of sticky and column and it now **calls mainloop()**) and it runs for me. I'm afraid that I only dabble a bit with Python and I don't use tkinter at all, so I can't guarantee that I've got this right.

Aye, there, friend.  Thanks for the help so far.  I ran my script with your changes and it runs much better.  It's not perfect, but it actually launches.  Thank you.  Using my difftool, I see that I had misspelled 'column' (without the n) like 20 times! I don't know how I missed all that.

I do see you added that function, 'mainloop()' at the very end.  It's not in the magazine .  At first I wondered how you came up with that idea to add that function.  I found [a StackOverflow post]("https://stackoverflow.com/questions/8683217/when-do-i-need-to-call-mainloop-in-a-tkinter-application") which explains that GUI programs in general have...

> ...to be able to handle all sorts of different kinds of events and interactions. This requirement is often implemented using a programming construct called an event loop. An event loop is the central control structure of a program. It waits for an event to happen, and then dispatches the appropriate handler.

mainloop() seems to be a programming convention for tkinter.  Interesting.

**@spjackson**: I know you said you are not all that familiar with tkinter, but I appreciate your help up to this point.

---

