---
title: "Very Basic Question about Python"
date: 2011-09-01
forum: Programming Talk
---

### Post by Lestathim on 2011-09-01
I am new to Python and programming in general and just had a very basic question that I can't seem to find the answer for anywhere.  I am using IDLE to enter my Python code.  Prior to this I was just using the Terminal to do so.  What I can't seem to figure out is how to enter multiple lines of code before output is given.  For instance if I say:

print "Line One" #I Get
Line One
print "Line Two" #I Get
Line Two

How exactly do I write this so that it produces both outputs at one time?  Like for instance this:

print "Line One"
print "Line Two"

Line One
Line Two

I know that's probably a basic questions but the books I have been reading and my recent searches haven't seemed to yield any results.  Thanks a lot for your time!

---

### Post by karlson on 2011-09-01
> **Lestathim said:**
> I am new to Python and programming in general and just had a very basic question that I can't seem to find the answer for anywhere.  I am using IDLE to enter my Python code.  Prior to this I was just using the Terminal to do so.  What I can't seem to figure out is how to enter multiple lines of code before output is given.  For instance if I say:

print "Line One" #I Get
Line One
print "Line Two" #I Get
Line Two

How exactly do I write this so that it produces both outputs at one time?  Like for instance this:

print "Line One"
print "Line Two"

Line One
Line Two

I know that's probably a basic questions but the books I have been reading and my recent searches haven't seemed to yield any results.  Thanks a lot for your time!

```

print "Line One\nLine Two\n"

```

---

### Post by Smart Viking on 2011-09-01
```
print "Hello,"; print "Mars!"
```

Pythons executes the same way in IDLE as it does with a text file, one line at a time. But when it's in a text file, python know what the next line is.

---

### Post by Lestathim on 2011-09-01
Thanks a lot for the help guys.  That answers part of my question I'd say but it kinda raises another.  The book I'm reading "How to Think Like a Computer Scientist" (heres a link to the book [http://www.greenteapress.com/thinkpython/thinkCSpy/thinkCSpy.pdf](http://www.greenteapress.com/thinkpython/thinkCSpy/thinkCSpy.pdf)), has a part in it, on the bottom page 27, that has the user, after defining to make a new blank line, write this:


print "First Line."
newLine()
print "Second Line.

and in turn gets this:

First line.

Second line. 

When I write it this is what happens:

print "First Line."
First Line
newLine()

print "Second Line"
Second Line

So what I'm essentially do is entering some input, getting some output.  What I want to do is enter all of the input just like they did in the book, and get all of the output.  What I can't seem to do is just that.  I hope I'm explaining myself clearly enough, if not I apologize.  Anyway, thanks again for your time guys.

---

### Post by squenson on 2011-09-01
In IDLE, use the menu File > New Window. In that new window, you can type a program of several lines. Save the file then press F5 to run it.

---

### Post by Bachstelze on 2011-09-01
Notice how there is no ">>>" before the input, this not done through the interpreter. You must write the lines in a text file, save it as something.py and run it with

```
python something.py
```

---

### Post by Lestathim on 2011-09-01
Oh Oh Oh I understand!  Wow thanks so much for your help everyone.  I really appreciate it.  That all makes complete sense now.  Thanks again!

---

