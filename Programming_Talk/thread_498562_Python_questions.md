---
title: "Python questions"
date: 2007-07-11
forum: Programming Talk
---

### Post by laforge on 2007-07-11
Hey everyone I have a few questions about python.

I recently picked it up and found it quite easy to learn, it is probably my first actually "programing language" as I usually do web based stuff (Javascript, PHP, CSS, HTML) but I am having a few problems.

1. After trying different programs and running them in the terminal I was wondering if there was a way to actually turning them into a program that ran in a command line just by double clicking the file.

2. I would like to try learning GUI stuff as I have never done that and was wondering how hard it is in python compared to other languages and what I would need.  I found [this]("http://www.cs.luc.edu/~anh/python/hands-on/handsonHtml/handson.html#x1-830004") and tried copying and pasting the complete code below but get this error
```
ubuntu@ubuntu:~/Desktop$ python test2.py
Traceback (most recent call last):
  File "test2.py", line 2, in ?
    from graphics import * 

```
I figured it's probably because I don't have it saved in the right folder but I can't seem to find the one I need to put it into.

3. If I get the code from Q2 to work I would like to know if that would be switchable between windows and Ubuntu or would I need to recompile it some how?  Would I need change the code around or completly rewrite it for it to work correctly in windows?

Thanks for any help in advance.

Oh incase you don't want to look for the code in Q2 I will put i here.

```
from graphics import * 
 
def main(): 
    winWidth = 200  # give a name to the window width 
    winHeight = 150 #    and height 
    win = GraphWin('Face', winWidth, winHeight) # give title and dimensions 
    win.setCoords(0, 0, winWidth, winHeight) # make right side up coordinates! 
 
    head = Circle(Point(40,100), 25) # set center and radius 
    head.setFill("yellow") 
    head.draw(win) 
 
    eye1 = Circle(Point(30, 105), 5) 
    eye1.setFill('blue') 
    eye1.draw(win) 
 
    eye2 = Line(Point(45, 105), Point(55, 105)) # set endpoints 
    eye2.setWidth(3) 
    eye2.draw(win) 
 
    mouth = Oval(Point(30, 90), Point(50, 85)) # set corners of bounding box 
    mouth.setFill("red") 
    mouth.draw(win) 
 
    message = Text(Point(winWidth/2, 20), 'Click anywhere to quit.') 
    message.draw(win) 
    win.getMouse() 
    win.close() 
 
main() 
```

---

### Post by reacocard on 2007-07-11
> **laforge said:**
> Hey everyone I have a few questions about python.

I recently picked it up and found it quite easy to learn, it is probably my first actually "programing language" as I usually do web based stuff (Javascript, PHP, CSS, HTML) but I am having a few problems.

1. After trying different programs and running them in the terminal I was wondering if there was a way to actually turning them into a program that ran in a command line just by double clicking the file.

2. I would like to try learning GUI stuff as I have never done that and was wondering how hard it is in python compared to other languages and what I would need.  I found [this]("http://www.cs.luc.edu/~anh/python/hands-on/handsonHtml/handson.html#x1-830004") and tried copying and pasting the complete code below but get this error
```
ubuntu@ubuntu:~/Desktop$ python test2.py
Traceback (most recent call last):
  File "test2.py", line 2, in ?
    from graphics import * 

```
I figured it's probably because I don't have it saved in the right folder but I can't seem to find the one I need to put it into.

3. If I get the code from Q2 to work I would like to know if that would be switchable between windows and Ubuntu or would I need to recompile it some how?  Would I need change the code around or completly rewrite it for it to work correctly in windows?

Thanks for any help in advance.

Oh incase you don't want to look for the code in Q2 I will put i here.

```
from graphics import * 
 
def main(): 
    winWidth = 200  # give a name to the window width 
    winHeight = 150 #    and height 
    win = GraphWin('Face', winWidth, winHeight) # give title and dimensions 
    win.setCoords(0, 0, winWidth, winHeight) # make right side up coordinates! 
 
    head = Circle(Point(40,100), 25) # set center and radius 
    head.setFill("yellow") 
    head.draw(win) 
 
    eye1 = Circle(Point(30, 105), 5) 
    eye1.setFill('blue') 
    eye1.draw(win) 
 
    eye2 = Line(Point(45, 105), Point(55, 105)) # set endpoints 
    eye2.setWidth(3) 
    eye2.draw(win) 
 
    mouth = Oval(Point(30, 90), Point(50, 85)) # set corners of bounding box 
    mouth.setFill("red") 
    mouth.draw(win) 
 
    message = Text(Point(winWidth/2, 20), 'Click anywhere to quit.') 
    message.draw(win) 
    win.getMouse() 
    win.close() 
 
main() 
```

1) you can create a .desktop file for them that will launch it in a terminal.

2) you need the graphics module, whatever that is. It's hard to tell without knowing what guide you're using.

3) this depends on what that graphics module is. However, if you use wxwidgets for the GUI stuff it will be perfectly portable across Win/Lin/OSX. (GTK is portable too, but not so much. QT4 is upposed to be really portable, but I haven't tried it yet)

---

### Post by laforge on 2007-07-11
Thanks for the info.  On my first question I was kind of wondering how to "compile" python to a "executable" file if that's what they call them in Linux.  You know so people who doesn't have python installed can run the file.

I guess what I mean is can I compile a program so that I can send it to a friend who runs windows and have them run it without installing the python package.

---

### Post by pmasiar on 2007-07-11
> **laforge said:**
> 1. ...if there was a way to actually turning them into a program that ran in a command line just by double clicking the file.

shell (ie bash) has way to make programs executable: first line should contain so called [shebang:](http://en.wikipedia.org/wiki/Shebang_%28Unix%29) #!/usr/bin/python , and file has to be executable, see [chmod](http://en.wikipedia.org/wiki/Chmod)

> 2. I would like to try learning GUI stuff as I have never done that and was wondering how hard it is in python compared to other languages

GUI is hard is every language because you cannot (and don't want to) predict in which order user will interact with controls (==widgets). Python has [easygui](http://www.ferg.org/easygui/) module which makes it easier (for the price of much simplicity). 

Seems like you lack ideas what to program (hint: *not* GUI), see wiki in my sig for training tasks. 36 tasks of pythonchallenge alone should keep you happy (and having fun) for couple of months.

Re Code error: Looks like module "graphics" is not installed (or not properly - in right place). BTW "import *" is bad habit, it pollutes your namespace with god knows what. Always import by name only: from graphics import a, b, c

>  if that would be switchable between windows and Ubuntu or would I need to recompile it some how?  Would I need change the code around or completly rewrite it for it to work correctly in windows?

Depends how you write it. Read docs: most modules are cross-platform, those not mention that in docs.

Ppl say that pretty cross-platform GUI is wxPython. I don't use it: I do  web apps, they  are cross-platform enough for me :-)

To send program to other people you can send source to Linux users (Python is installed on every Linux), for ppl stuck with Windoze you need to compile it to executable. IIRC, pyrex is one way to do it.

---

### Post by laforge on 2007-07-12
Wow, ok thanks for all the info.

---

### Post by LaRoza on 2007-07-12
You can compile Python programs into byte code and Windows .exe files.

Using Tkinter is a good place to start for GUI programming, it looks good on all platforms.

If someone has Windows, ActivePython from activestate.com is good, it has most modules you'll use, including Tkinter.

---

### Post by boralyl on 2007-07-12
For GUI programming, I'm very fond of wxPython.  There is a good article at the wxpython wiki giving the pros and cons of wxPython and Tkinter [http://wiki.wxpython.org/Choosing_wxPython_over_Tkinter]("http://wiki.wxpython.org/Choosing_wxPython_over_Tkinter").  It's fairly easy to use, and if you like it I would reccomend the book "[wxPython In Action]("http://www.amazon.com/wxPython-Action-Noel-Rappin/dp/1932394621/ref=pd_bbs_sr_1/103-1485301-2307026?ie=UTF8&s=books&qid=1184281172&sr=8-1")

---

