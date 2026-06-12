---
title: "I did a &quot;kill process&quot; and I think I messed up my python install"
date: 2007-11-29
forum: Programming Talk
---

### Post by tc101 on 2007-11-29
I wrote a test program that was caught in a loop and I couldn't get it to stop.  It was running in IDLE and even when I closed the Shell, the window with the code in it would not close.  I tried several things and eventually went into Systom Monitor and did a kill process on IDLE.

Now some things are ot working the same way.  The problem that I notice so far seem to be related to MySQLdb, but I am not absolutely sure of this.  

So what do I do to fix this?  Uninstall and reinstall python, or MySQLdb, or what?

---

### Post by tc101 on 2007-11-29
It may have been a logic error on my part.  I am learning so many new things I get confused.  I have everything working now, but I am going to leave this thread open because I still have a suspicion that one command in python works differently since I did the kill, but I could be wrong.  If anyone has any ideas or thoughts on this I would like to hear them.

---

### Post by smartbei on 2007-11-30
Well, I doubt that Python is behaving differently due to the kill process. You were only reading/executing the python interpreter and not editing it so there should be no reason for a lasting effect. There have been many, many times when I killed a python process due to its taking too long (projecteuler.net puzzles mostly :)). What is the command that you suspect gives different output?

---

### Post by tc101 on 2007-11-30
> What is the command that you suspect gives different output?

I created some global variables without defining them.  I think this worked before the kill.  I just had the code:

"""
Global variables
"""
amt1
amt2
amt3

After the kill this gave me an error 
NameError: name 'amt1' is not defined

I just defined the varialbesl

amt1=0
amt2=0
amt3=0

and it works now.  

Did it ever work or was it just my imagination?  I was doing so many new things as I learn python and linux that I may have gotten confused.

---

