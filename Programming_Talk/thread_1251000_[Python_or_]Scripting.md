---
title: "[Python or ?]Scripting"
date: 2009-08-27
forum: Programming Talk
---

### Post by swatto on 2009-08-27
Hello all,

Please don't laugh at me but Ive got to ask.  If I don't want to write full applications and just want to write scripts to automate tasks in Linux or Windows can Python be used for this or would I need to learn an alternative? and how do I learn how to interact with the Operating System in question when writing these scripts?

Thanks for any help

---

### Post by pepperphd on 2009-08-27
Nobody is going to laugh at you here! :guitar:

Yes, Python can be a wonderful tool for automation, as can BASH. From personal experience, I get more done in Python than in BASH, but that is probably because I have much more experience with Python, so when I think about making a small script I think it up in Python and hardly consider the alternatives. Don't underestimate the power of pipes and redirection. Combined with all of the tools in your PATH, shell scripting can accomplish amazing things.  

Here is a tutorial on Python. This and the book "Learning Python" by Mark Lutz (O'Reilly publishing) will get you up to speed on this wonderful language.
[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

I learned what I know about shell scripting from another book from O'Reilly, "Classic Shell Scripting".  However a quick Google search brings up what appears to be a nice place to start learning to automate your tasks:
[http://tldp.org/LDP/abs/html/part1.html](http://tldp.org/LDP/abs/html/part1.html)

Good luck on your journey.  May the source be with you.

---

### Post by kpkeerthi on 2009-08-27
Although Python is a complete programming language, it is good for scripting as well (its syntax is terse, yet readable). But unless you want to write cross-platform scripts, I suggest you stick with bash scripting. I recommend [Learning the Bash shell]("http://www.amazon.com/Learning-bash-Shell-Programming-Nutshell/dp/0596009658/ref=sr_1_1?ie=UTF8&s=books&qid=1251369971&sr=1-1") to get started.

---

### Post by swatto on 2009-08-27
Thanks for the replies :)

Im not completely new to Python - I know the general beginner stuff but just wondered is there anything specific I need to learn in Python (as opposed to learning how to program in Python to write full applications/programs) if I just want to create scripts to automate operating system tasks?

---

### Post by Nevon on 2009-08-27
That depends a lot on the task at hand. Whenever I try to automate something in Python, I find myself using a bunch of bash commands through the subprocess module, so for that Bash would probably be a better fit.

---

### Post by koonsolo on 2009-08-27
Good thing about python is that you can use the same script for both linux and windows (if you don't use OS specific calls), and you have access to great libraries like numpy or Python Imaging Library for example. Also check out this [Python Quick Reference]("http://rgruet.free.fr/PQR25/PQR2.5.html"), which is extremely handy.

---

### Post by swatto on 2009-08-27
Thankyou for your assistance.  I think I am going to try and script with Python because I know a little bit of it (and have multiple books on it) plus as you have said it is cross-platform providing I don't use OS specific calls.  So shall I just learn Python Programming as normal and adapt it to scripts I want to create to automate tasks?

---

