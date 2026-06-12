---
title: "how to get started as a programmer ?"
date: 2006-11-06
forum: Programming Talk
---

### Post by techrush on 2006-11-06
My experience to programming has been fairly limited. I can write and understand html/css, ive went through a couple very basic python tutorials and i've dabbled in php but never really created anything on my own. I cant even say i understand much more than the basics of programming. 

Most of the tutorials on the net seem to just be an introduction to the language and/or geared towards experienced programmers. Im looking for recommendations on how someone with little to no experience can actually go about learning to program. 

Im leaning towards the python/ruby side of things as that seems the more reasonable way to go for a beginner like myself.

As far as things id like to create....i wouldnt mind doing a little rss reader or maybe some scripts to help me organize my massive amount of audio samples.

If anyone could point me in the direction of some material to help out a newb id appreciate it :)

---

### Post by po0f on 2006-11-06
For Python, which I would recommend for a beginner:
[list]
[*][The Official Tutorial](http://www.python.org/doc/2.4.4/tut/tut.html): This is the official tutorial.  Python version 2.4.4 as per Edgy's defaults.
[*][A Byte of Python](http://byteofpython.info/read/): I found this one a little easier to read.  After trying to read the official tutorial, I read this, then went back and finished the former.
[*][Dive Into Python](http://www.diveintopython.org/): When I was learning Python, I found it helped to read a lot of "for beginner's" documentation, and found this one indispensable.  (Installed by default on Dapper/Edgy, don't know about previous Ubuntu versions.)
[*][ASPN's Python Cookbook](http://aspn.activestate.com/ASPN/Cookbook/Python/): Very useful for looking up snippets of code that you can't get quite right.
[/list]

Hope this helps.

---

### Post by techrush on 2006-11-06
ive actually went through the byte of python tutorial and did find that it helped me learn the very very basics of python. i also own a hard copy of dive inoto python. this book assumes too much prior knowledge that i just do not have. ill try the official tutorial you linked too. thanks.

---

### Post by po0f on 2006-11-07
techrush,

Sorry, I just read that Dive Into Python is for experienced programmers.  I did not take into account that you said you had little programming experience.

Just starting out, are there any specific issues you are having?

---

### Post by techrush on 2006-11-07
i geuss my main issue is trying to get over "the hump" i understand

print "hello world" 

and i even understand a lot of the flow control stuff and how string variables etc all work. 

what im not "getting" is how to transfer all these concepts into an actual working useful program.

---

### Post by cwaldbieser on 2006-11-07
> **techrush said:**
> i geuss my main issue is trying to get over "the hump" i understand

print "hello world" 

and i even understand a lot of the flow control stuff and how string variables etc all work. 

what im not "getting" is how to transfer all these concepts into an actual working useful program.

That comes with experience.  The more code you read and write, the more you will be exposed to different techniques and patterns.  After a while, you will find that you start recognizing ways to solve different problems.  Different combinations of concepts work for different sorts of problems.

You may want to take some existing program you would like to learn about and try to see if you could figure out how you would write it.  If you get stuck, you can look at the author's code and see how he or she actually implemented the program.  There are often many different approaches to tackling similar problems.  Practice teaches you what works best with the least effort.

---

### Post by po0f on 2006-11-07
techrush,

Just as an example, this was my first Python script.  It strips comments out of config files:
```
#!/usr/bin/env python
"""To specify more comment characters, single- or double-quote
them.  For example, vimrc files use " as a comment character,
so you would run commstrip.py like this:
    commstrip.py /path/to/vimrc '"'
Be aware that certain characters will be interpreted by your
shell if you do not quote them, you have been warned."""

import sys

def main():
    comment_chars = [ '#' ]

    try:
        file = sys.argv[1]
    except IndexError:
        print "No file specified, aborting."
        sys.exit(1)

    try:
        fd = open(file)
        lines = fd.realines()
        fd.close()
    except IOError:
        print "Error reading %s, aborting." % (file)
        sys.exit(1)

    try:
        for arg in sys.argv[2:]:
            if len(arg) == 1:
                comment_chars.append(arg)
            else:
                print "Invalid argument %s, continuing." % (arg)
    except:
        pass

    lines_ok = []
    for line in lines:
        tmp_line = line.strip()
        if not tmp_line:
            continue
        elif tmp_line[0] in comment_chars:
            continue
        else:
            lines_ok.append(line.rstrip())

    print "\n".join(lines_ok)

if __name__ == "__main__":
    main()
```

As you can see, I rarely use this script, but it's handy when I need it.  Of course there are single line shell scripts that do the same, but this was more of a learning exercise for me.

---

### Post by dwblas on 2006-11-10
You have to first define something that you want, then break it down into pieces that will become functions or individual program files, and then find a way to write each one individually.  Perhaps something like a program to back up your computer files, using a text file with the dirs you want to backup as an input.  You could also examine the source code for something like a python system to store music, which would give you an idea of how to use a database, as well as GUIs.  Don't be at all concerned if you don't understand parts of it.  The point is to expand what you know, and you can only absorb so much at one time.

---

### Post by reynoldlariza on 2006-11-10
huh? why is it that there's no switch???

I looked and tried some scripts from the terminal....
I felt like looking at pascal+basic combination though... 

I still like PERL/PHP/C/C++ better, I got a reliable view of which block a line of code is in and out. plus, there's switch()!

---

### Post by dwblas on 2006-11-10
Most people use a dictionary or list instead of a switch statement.  IMO it is more efficient, easier to understand, and takes up far fewer lines of code.  But for the creative-challenged, here is how you would program a switch in python.  There are surely a lot more examples on the web.  Python arguably has the most examples of any language.
```
result = {
  'a': lambda x: x * 5,
  'b': lambda x: x + 7,
  'c': lambda x: x - 2
}[value](x)
```
Just a final random thought.  What is the difference between:
```
switch 'a' :
      do a
switch 'b' :
      do b
```
and
```
if x=='a' :
  do a
elif x=='b' :
  do b
etc?
```

---

