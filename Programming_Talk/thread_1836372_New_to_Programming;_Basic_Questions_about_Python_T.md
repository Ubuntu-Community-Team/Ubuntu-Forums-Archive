---
title: "New to Programming; Basic Questions about Python Trail and Error"
date: 2011-08-31
forum: Programming Talk
---

### Post by Lestathim on 2011-08-31
I recently began trying to understand programming and started with Python.  I'm currently reading a book, How to Think Like A Computer Scientist, which is basically walking me through the beginning of this feat.  However I have ran into a small problem that I just can't figure out.  Here is a quote from the book:

In the context of programming, a function is a named sequence of statements that performs a desired operation. This operation is specified in a function definition. The functions we have been using so far have been defined for us,and these definitions have been hidden. This is a good thing, because it allows us
to use the functions without worrying about the details of their definitions.
The syntax for a function definition is:
def NAME( LIST OF PARAMETERS ):
         STATEMENTS
You can make up any names you want for the functions you create, except that you can’t use a name that is a Python keyword. The list of parameters specifies what information, if any, you have to provide in order to use the new function.
There can be any number of statements inside the function, but they have to be indented from the left margin. In the examples in this book, we will use an indentation of two spaces.

The first couple of functions we are going to write have no parameters, so the syntax looks like this:
def newLine():
   print
This function is named newLine. The empty parentheses indicate that it has no parameters. It contains only a single statement, which outputs a newline character. (That’s what happens when you use a print command without any arguments.)

The syntax for calling the new function is the same as the syntax for built-in functions:
print "First Line."
newLine()
print "Second Line."

The output of this program is:

First line.

Second line.

Notice the extra space between the two lines?

Okay so that is an excerpt from the book.  I am having a problem with fulling this.  What does it mean by indentation?  How am I supposed to write "print" under the def newLine(): ?  I'm sorry I know this is probably a very minuscule question but it's what I'm stuck on nonetheless.  Any help that anyone could give would be great.  Thanks a lot!

---

### Post by Bachstelze on 2011-08-31
Like this:

```
def newLine():
  print
```

Insert two spaces before print.

---

### Post by Lestathim on 2011-08-31
Thanks so much that worked perfectly however it created a new problem for me.  When I typed:

>>> def newLine():
...  print
 
Another series of ... appeared under the print.  As if it was expecting more input.  How exactly do I end the creation of the new function key?   Thanks again!

---

### Post by Bachstelze on 2011-08-31
Just press Return again. ;)

---

### Post by Lestathim on 2011-08-31
Wow hahaha!  Thank you so much!  The help is greatly appreciated!

---

### Post by Thewhistlingwind on 2011-08-31
Like this:
```

def testfun(your,arguments,here):
        if your in here:
              return "You just"
        elif arguments in here:
         return "lost"
     else:
         return "the game"

```;)

EDIT: I'm not even going to try formatting, basically inside every statement that expects "more" (Like a for loop or if statement) you usually end it with a :, hit return, and use some consistent number of spaces to indent. (1/2/4 spaces, etc.)

So if I define a function, write an if statement, then do a for loop, the stuff I put in the for loop should be indented six spaces if I'm using 2 space indents.

---

### Post by nvteighen on 2011-08-31
The basic idea is the following: 

0) Blocks are defined by indentation level.
1) After a colon, you have to use add a new indentation level.
2) You close a block by reducing the number of indentation levels by one.

That's it.

---

### Post by Lestathim on 2011-08-31
I think I understand where you guys are coming from with this.  See the problem I am having is I am using Python inside of the Terminal.  I'm not exactly sure how to program and i'm following instructions via this book to get the basic ideas.  Should I be using the Terminal or some third party program?  Also, how do I write multiple lines without the Terminal outputting them one at a time?  For instance I cannot write:

print "New Line One"
newLine()
print "New Line Two"

and get this:

New Line One

New Line Two

Instead, I write line one:
print "Line One" #and get
Line One

Then I have to type newLine() under the already printed line and so forth.  What I am asking is basically how do I write multiple lines?

---

### Post by kevinharper on 2011-08-31
I STRONGLY suggest that you watch this video series:
[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/)

It is from an MIT intro-to-programming class. They use python, but the class isn't about Python. It is to get you to think like a programmer.

The site also has links to problem sets (assignments) and class notes.

EDIT:
> Should I be using the Terminal or some third party program?
You can use gedit (or another text editor) and save your file as filename.py

EDIT2: Found this link that might help you.
[http://www.thegeekstuff.com/2009/09/python-hello-world-example-how-to-write-and-execute-python-program-on-unix-os/](http://www.thegeekstuff.com/2009/09/python-hello-world-example-how-to-write-and-execute-python-program-on-unix-os/)

It's for vi/vim, but should work the same for any text editor.

---

### Post by Lestathim on 2011-08-31
Wow Kevin you were right, that's an awesome link thanks for the tip on that.  I really appreciate the response thank you

---

### Post by kevinharper on 2011-09-01
Glad you found those links useful.

I think there is one problem set (assignment) per every 2 to 3 videos. I would watch the lectures and attempt a problem sets after every 3 videos. The professor talks about a recitation period - I would strongly advise you to use this forum as just that. Ask questions about anything you don't understand (of course, after doing some research on your own and not finding a resolve).

Also, you might want to consider marking this thread "solved" under "Thread Tools" if your questions were answered.

---

