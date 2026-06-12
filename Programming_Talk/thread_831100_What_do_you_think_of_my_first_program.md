---
title: "What do you think of my first program?"
date: 2008-06-16
forum: Programming Talk
---

### Post by MONODA on 2008-06-16
A while ago I decided to start learning python. This would technically be my third language (i also did some HTML and java script) after a bit of C and pascal. I must say that so far, I have yet to find one perfect guide for python, I have found 2 which together work great: dive into python and the official python docs. I have only learned a bit so I decided to test my knowledge and write somethings, here it is: EDIT: I just attached it, thought it would be better.
I used Geany IDE to write it which is quite nice. Anyway, what do you think? Anything I should add/fix/make better? How could I fix the organization of my code? How could I make it shorter, cleaner and more efficient? Please critisize!

---

### Post by -grubby on 2008-06-16
The first time I ran it, I tried to input numbers instead of words. I think it'd be more convienent if you could just input the number next to the word. Also, please add some comments. I'm not good at math at all, so I had no idea what was going on there. 

But otherwise, I like this program. You used some methods I never thought about using, and I didn't know you could use a triple quote to make a print statement over multiple lines without using a "\" statement at the end of each line break (if the print statement exceeds one line). 

Also, I would have made the input statements what you did with the print statements, but your way seems more organized to me.

---

### Post by MONODA on 2008-06-16
thanks for your reply. I thought about including the ability to just type in the number, Ill get on that now. About the comments, I dont think there is really anything to explain since those are just equations which I have listed at the end. I am not quite sure what you would like me to include in the comments. Could you please elaborate? Anyway, here is version 1.1
EDIT: Any other ideas/comments?

---

### Post by -grubby on 2008-06-16
Well, I like your new version. You should include else statements after your if and elif statements, because if you don't than the program just crashes if you enter an incorrect value and doesn't tell you anything. Also, comments are extremely helpful to somebody that looks at your program and has no idea of what's going on. If I find enough time, perhaps I'll post a version that I dabbled on here

---

### Post by MONODA on 2008-06-16
Ok, I added else statements at the end of the if code blocks (am i using the right terms?) here is what I have got, but when I get to the stage when it asks what I would like to do with the shape and I enter an invalid value, it prints "Please enter a proper value" twice instead of once. here it is

---

### Post by -grubby on 2008-06-16
I'm not exactly sure why that may be, but you need to use elif statements on the original input (if shape == "number"). So it'd go "if shape == "1", "elif shape == "2", etc

---

### Post by nvteighen on 2008-06-16
There's a bug! if you type 5, you get all equations (when it should show things for Pyramids) and if you choose 6, you don't get nothing (and it should list all equations).

What you could try now is to make your program more structured, i.e. breaking it into several reusable functions. For example, volume is always area * height * constant, so you could create a function that returns the variable part in which you pass height and area as arguments... and then multiply to the constant.

For this simple program, it's actually not necessary to do that. But, in future, when your programs get a bit more complex, it's the only way to keep things ordered and mantainable. It's all about acquiring the good habits :)

---

### Post by marialice on 2008-06-16
Remarks:
- decide what you want your program to do, decide how you're going to test it, then build it, then test it (now there is a menu option for pyramids but if you choose '5' you'll get 'all equations')
- whenever you find yourself copy-pasting, ask yourself if your code would be cleaner with a separate function or a different data structure, there are many duplicate lines now (unnecessary and an invitation for errors)
- comment, comment, comment, especially while your learning.

---

### Post by nvteighen on 2008-06-16
(Oh, great. You guys are faster than me... My post was on v1.1)

That line gets repeated because you're not using elif, so the else statement is referred to the last condition.

Something else: instead of repeating **print "Please enter a proper value"** you could create a variable that gets some value if there's a failure and then just check for that "error code" once at the end of the code in order to print the error message. That would be one step into structuring your code a bit more.

---

### Post by finer recliner on 2008-06-16
I dont think the program should exit after giving an output, instead it should loop back to the beginning to take another request. Currently it just exits after giving the output or errors out.

---

### Post by -grubby on 2008-06-16
> **finer recliner said:**
> I dont think the program should exit after giving an output, instead it should loop back to the beginning to take another request. Currently it just exits after giving the output or errors out.

Yep, I believe you would do it somewhat like this:

[php]
function()
    # Put the current code here, 
    # make sure to use the correct tab length
    
    # make the function call itself
    function()
# Call the function
function()
[/php]

Also, make sure to include a way to exit if you do it this way. That could happen simply by doing :
[php]
import sys

sys.exit()
[/php]

However, you'd have to implement that some way. Perhaps you could make another option in the initial input to exit?

---

### Post by MONODA on 2008-06-16
thanks for your feedback you guys, I dont have time right now to work on it some more, but tomorrow I will fix the bugs and do some cleaning in the code. I also plan on getting farther into the python documentation.

---

### Post by -grubby on 2008-06-16
Ok, well good luck!

---

### Post by ssam on 2008-06-16
nathangrubb thats not a good way to loop. it will keep opening new functions, but never close the old one. and will eventually give a "RuntimeError: maximum recursion depth exceeded" error or use all your ram.

really you want a loop. try

```

while True:
   print hello
   x = raw_input("do you want to stop [y/n]:")
   if x == 'y':
       break


```

---

### Post by -grubby on 2008-06-16
erm...ssam, it's always worked for me. Then again, I've only used it for apps that function sort of like a terminal. I have gotten that error before, however. Perhaps I'll try it your way

---

### Post by ssam on 2008-06-16
try running this this
```

def a(x):
     print x
     a(x+1)

a(0)

```

for me it dies at 998

---

### Post by Can+~ on 2008-06-16
> **ssam said:**
> try running this this
```

def a(x):
     print x
     a(x+1)

a(0)

```

for me it dies at 998

[PHP]>>> import sys
>>> sys.getrecursionlimit()
1000
>>> sys.setrecursionlimit(1001)[/PHP]

---

### Post by MONODA on 2008-06-17
Well I have fixed the bug (turns out that i had removed that feature on purpose but forgot to remove it from the menu [i didnt want it any more b/c finding the SA and Vol of pyramids is more complicated than for other shapes]). I have been looking at the code posted but really dont understand it, could anyone give me a way to loop back to the beginning if someone enters an incorrect value at a menu? thanks

---

### Post by MONODA on 2008-06-17
I have a TI-84 plus calculator, is there any way to install this application on it?

---

### Post by -grubby on 2008-06-17
> **MONODA said:**
> Well I have fixed the bug (turns out that i had removed that feature on purpose but forgot to remove it from the menu [i didnt want it any more b/c finding the SA and Vol of pyramids is more complicated than for other shapes]). I have been looking at the code posted but really dont understand it, could anyone give me a way to loop back to the beginning if someone enters an incorrect value at a menu? thanks

You could just enclose everything in a while True: statement

---

### Post by MONODA on 2008-06-17
> You could just enclose everything in a while True: statement
thanks, Ill get to fixing it up now. BTW do you know anything about how to get this on to a TI calculator?
EDIT: Wait, I am not to sure how I would use that to loop back to the beginning of the program. could you maybe show me an example? thanks.

---

### Post by -grubby on 2008-06-17
> **MONODA said:**
> thanks, Ill get to fixing it up now. BTW do you know anything about how to get this on to a TI calculator?

nope, sorry :(. But, I believe some calculators you can program on..perhaps you could convert this to calculator language or somethinG?

---

### Post by guilly on 2008-06-17
> **MONODA said:**
> thanks, Ill get to fixing it up now. BTW do you know anything about how to get this on to a TI calculator?
EDIT: Wait, I am not to sure how I would use that to loop back to the beginning of the program. could you maybe show me an example? thanks.

I haven't ran your program or anything but you could just wrap your code in a while statement like stated previously and after each iteration prompt the user to enter yes or no if they would like to continue... Then just keep testing for true and until the user says no your program should just keep looping

---

### Post by werries on 2008-06-17
the easiest way to loop would be to stick the whole code in a while loop, like
```
yn=y
while yn=='y' || yn=='Y':
...
...
        yn=input("Would you like to do another calculation(y/n)?:")

```
This way, the entire program would go through once, and then ask if you wanted to go through it again, and then go through it again if you said yes. I'm not sure if I implemented this correctly, but you can figure it out. Its the general idea of what we always did in programming class in C++.

---

### Post by rlameiro on 2008-06-17
> **MONODA said:**
> ...BTW do you know anything about how to get this on to a TI calculator?


I don't think that there is a python interpreter for TI calculators, However, TI Calcs (the more advanced aka graphic ones) have A especific language that is a kind of BASIC they call it TI BASIC. You can also program in ASSEMBLY for the Z80 processor, but i would not recommend it if you dont understand the inner of a processor. You can stick with the TI BASIC. Maybe it would be I nice Idea, trying to translate you program, you could understand better some thing... but anyway, I am not an expert in python or basic anyway. 
Here you have a link about TI BASIC for thr TI-83 / TI-84
 calculators.

[http://tibasicdev.wikidot.com/home](http://tibasicdev.wikidot.com/home)

Good luck and keep going.

---

### Post by MONODA on 2008-06-19
Alright, I have been working on this, I have added the loop and some comments (even though I dont see the benifit of this since all it does is make things crowded...). I am thinking of having "units^2" or "units^3" after each response, how could I do this?

---

### Post by nvteighen on 2008-06-19
> **MONODA said:**
> Alright, I have been working on this, I have added the loop and some comments (even though I dont see the benifit of this since all it does is make things crowded...). I am thinking of having "units^2" or "units^3" after each response, how could I do this?
Excuse me: Where's the new code? I'd like to see what happens with that while-loop.

By the way, the benefit of commenting code is that, if you happen to look back at it in, say, 3 months or more, you'll automatically understand what you did. And also, because if you happen to work with other programmers in some project, you'll be used to comment code and your colleagues will understand what your code is meant to do immediately. Of course, look for some balance (as old Aristoteles...): don't fill everything with comments either! :)

---

### Post by guilly on 2008-06-19
> **MONODA said:**
> Alright, I have been working on this, I have added the loop and some comments (even though I dont see the benifit of this since all it does is make things crowded...). I am thinking of having "units^2" or "units^3" after each response, how could I do this?

Just to add to the hole commenting thing. Not sure if your planning on becoming a programmer as a profession. But I would say that 80% of the you will be doing maintenance on somebody else' code therefore comments become very handy!!

---

