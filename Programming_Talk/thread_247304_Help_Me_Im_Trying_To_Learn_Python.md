---
title: "Help Me Im Trying To Learn Python"
date: 2006-08-30
forum: Programming Talk
---

### Post by zachsilvey on 2006-08-30
Ok im a 14 year old just getting into linux and am learning the language python. I like the language but I want to be able to compile the bytecode into an executable. I have a little experience in c++ on the windows side and  I would like to be able to compile python as easy as c++. Thanks](*,)

---

### Post by neilp85 on 2006-08-30
Check out py2exe, it converts python scripts into windows executables. On the linux side I don't know of any equivalent to this. It's not really necassary though so long as you put
```
#!/usr/bin/python
```
at the top of the file and place the script somewhere in your PATH.

---

### Post by dwblas on 2006-08-30
> #!/usr/bin/pythonAnd make it executable, otherwise you have to enter "python program_name" instead of just "program_name".  (Most take this for granted, but seeing how you are just starting, you may not know it.)

---

### Post by neilp85 on 2006-08-30
> **dwblas said:**
> And make it executable, otherwise you have to enter "python program_name" instead of just "program_name".

I wasn't thinking, should have mentioned that.
```
chmod +x helloworld.py
```

---

### Post by jpeddicord on 2006-08-30
That is the only thing keeping me from Python: It is a runtime executable and cannot be compiled. ](*,)

---

### Post by skymt on 2006-08-31
> **jacobmp92 said:**
> That is the only thing keeping me from Python: It is a runtime executable and cannot be compiled. ](*,)

How is that a problem? The end user can't tell the difference, unless it's a computation heavy program like a game or graphics program. Can you honestly tell me Deskbar or Alacarte is that much worse because they're written in Python?

---

### Post by Note360 on 2006-08-31
Hey dude I am the same age as you. Here is my tip. Just go. Learn Learn Learn. Learn vim, emacs, joe, nano. Learn Python (I suggest this first). Learn a IDE. Learn modules. Read. Write.

Schedule:
Read
Read
Read
Write
Write
Learn
Lunch
Read
Read
Write
Read
Learn
Write
Learn
Dinner
Learn
Read
Read
Write
Coffe Brake
Read/Write
(Until morning)

That is my tip.

---

### Post by Daverz on 2006-08-31
Way too much reading in that list.  The great thing about Python is that you can spend more time doing than reading.

---

### Post by loell on 2006-08-31
compiling python to binary?

 i beleive Ironpython can do that, but then you'll have to install mono ;) 
 someone also suggested py2bin, but i've googled and seems there is no such thing.

and i think zachsilvey is way pass reading, the thing is when learning a dynamic interpreted language like python, a learner will come to a point,
asking "Can an interpreted language be compiled" i've ask that same question before, guru would usually say, why would you want to? you'll loose portability.

---

### Post by moaxey on 2006-09-01
i do a bit of python

on mac there's a cool py2app module that you can add to your system and build impressive clickable applications... including all the code you need to run it without dependencies on target systems.

havent played with py2exe on windows, but it sounds the same

they're all derived from bindist utils 
which allows you to distribute binaries on linux
[http://docs.python.org/dist/dist.html](http://docs.python.org/dist/dist.html)

but of course, you only bother with this stuff after you've got your scripts properly working and tested by running them from the command line

python myscript.py

---

### Post by Note360 on 2006-09-01
YOu are right. I made it up at random.

---

### Post by daniel of sarnia on 2006-12-21
> **Note360 said:**
> 
Coffe Brake
Read/Write
(Until morning)

That is my tip.

What ever you do, don't get on a bad sleep cycle. Oh you'll be able to handle it at first. Maybe even a hole year. But sooner or later your heart will start hurting from the caffeine, your immune system will get so weak you'll get a virile infection and feel like your dieing for a month or so. You just end up getting messed up so bad you lose everything you gained. 

Trust me I know, and it sucks, Just practices during the day, get in good work habits, sleep right, eat right, work hard and you'll come out on top in the end.      

A side note, a guy at my school drank so much red bull so often, he might need heart sugary now.

But what ever, your body your mind. Some people can only learn somethings for them selfs.

EDIT: Forget to say, have fun man. I like python and C++ and I think they are a good place to get started. Good luck!

---

### Post by pmasiar on 2006-12-22
I created a web resource for beginning programmers who wants to learn python. It has copule links to online books especially good for beginner programmers, data structures, and some tasks to solve. [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) Enjoy.

---

### Post by gpolo on 2006-12-22
python comes with a tool called freeze, here it is located at /usr/share/doc/python2.4/examples/Tools/freeze, that is for Linux mainly. For Windows use py2exe, it works better than freeze in some tests I have done. I did a project and used py2exe to sell the binary, and worked very well ;)

---

### Post by gh0st on 2006-12-22
I am learning Python myself at the moment and I found this book really helpful

[http://diveintopython.org/](http://diveintopython.org/)

You can download the eBook as PDF or HTML for free from that site. It doesn't give you all the usual beginner rubbish like "What Is A Programming Language?" :) Just the stuff you need to get started in Python.

Very handy if you have a bit of programming knowledge already (you mentioned C++) and just want to transfer your skills to another language.

Hope that's of some use but it sounds like you know quite a bit already.

---

