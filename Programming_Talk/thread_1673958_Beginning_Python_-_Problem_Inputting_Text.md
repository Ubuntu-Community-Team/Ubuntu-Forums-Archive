---
title: "Beginning Python - Problem Inputting Text"
date: 2011-01-23
forum: Programming Talk
---

### Post by zhogan85 on 2011-01-23
I'm new to programming, but have been trying to teach myself python, as I've read that's a good place to start. I'm using IDLE and have tried both 2.6 and 3.1 but I keep running into the same problem. IDLE does not recognize when I type. Sometimes it will work initially, but it will stop letting me type after I run my program. Any help or ideas would be greatly appreciated.

---

### Post by CaptainMark on 2011-01-23
Something sounds wrong with your installation of idle, try removing it from software centre and reinstalling, if not, are you able to type in other windows/text editors??

---

### Post by FelipeAragao on 2011-01-23
purge idle
```
sudo apt-get purge idle-python2.6
```
then install it again.
are there any error messages? can you be more specific about the issue? Look, sometimes you are not able to open idle (2.6) more than once.

---

### Post by Cheesehead on 2011-01-23
Idle opens a 'Python Shell' window that shows you *results*. That's why you can't type much. You can type on the bottomost '>>>' prompt, but that's not where you do your work.

Select File -> New Window to create a window you can create programs in.
To test your program, save it (CTRL+S), then run it (F5)...and see the reults in the original 'Python Shell' window.

---

### Post by zhogan85 on 2011-01-24
Thanks for the replies, but my problems seem to have multiplied. I purged IDLE, and then reinstalled 3.1.3. Now, I can type in the shell, but whenever I open a new window, I cannot type. Further more, in the shell, when I try to run a very basic command, for example:

print "hello world! "

I get the following error:

print "hello, world! "
SyntaxError: invalid syntax

and it is highlighting the closing quotation mark. I also tried using ' ' but had the same result. Please help! I am really interested in learning to program but this start does not seem very auspicious.

---

### Post by zhogan85 on 2011-01-24
Sorry, ignore the error part of the previous post. I just figured out that apparently in python 3 "print" is a function and must be excecuted like:

print("hello world! ")

---

### Post by TheWeakSleep on 2011-01-24
> **zhogan85 said:**
> Thanks for the replies, but my problems seem to have multiplied. I purged IDLE, and then reinstalled 3.1.3. Now, I can type in the shell, but whenever I open a new window, I cannot type. Further more, in the shell, when I try to run a very basic command, for example:

print "hello world! "

I get the following error:

print "hello, world! "
SyntaxError: invalid syntax

and it is highlighting the closing quotation mark. I also tried using ' ' but had the same result. Please help! I am really interested in learning to program but this start does not seem very auspicious.

EDIT: Jeez you beat me to it :p :) glad to see you figured it out

Python 3 has slightly different syntax for certain things that can become confusing if you're used to Python 2.x

For instance, print is no longer a statement in Python 3 but a function. try:

```
print("Hello, World!")
```

---

### Post by zhogan85 on 2011-01-24
Thanks for the quick reply theweeksleep. Since I'm just learning I don't have the older syntax ingrained in me yet, so I'll stick with the latest version.

OK, so after trying several different versions of IDLE, I now have 3.1.3. When I opened a new window, it let me type, but when I went to run the program, i lost the ability to type when trying to type a file name to save it and from then on I cannot type in IDLE without restarting IDLE. I can still type fine in every other program, and have never had a similar problem.

---

### Post by llanitedave on 2011-01-24
> **zhogan85 said:**
> Thanks for the quick reply theweeksleep. Since I'm just learning I don't have the older syntax ingrained in me yet, so I'll stick with the latest version.

OK, so after trying several different versions of IDLE, I now have 3.1.3. When I opened a new window, it let me type, but when I went to run the program, i lost the ability to type when trying to type a file name to save it and from then on I cannot type in IDLE without restarting IDLE. I can still type fine in every other program, and have never had a similar problem.

I can't help you with the IDLE problem.  I recently started using Geany for Python editing, and I find it is a nicer application.

Congratulations for starting right out with Python 3.  Lots of people are still recommending the 2.xx series, but I think if you want to get started and start right, go with the latest version.  The libraries and other apps will catch up soon enough, and by the time you've mastered the language there will be plenty of support at hand.

---

### Post by kurum! on 2011-01-24
> **zhogan85 said:**
> Any help or ideas would be greatly appreciated.
```

#!/usr/bin/env ruby
puts "hello world"

```

```

$ ruby -e 'puts "hello world"'

```

---

### Post by Tony Flury on 2011-01-25
I can't help thinking that if you are a complete beginner (no disrespect intended), then starting out by using a IDE (like IDLE or any other) is actually a bad idea - as you end up spending a lot of time learning the IDE and not the language.

My recommendation is learn the language first - for python : Open a terminal and type 
```

$> python

```
and start using the interactive interpreter.

When you want to write stuff and save it - use gedit, or Kate or emacs, vi or your favourite text editor to write your code - and execute it.

I would only recommend a beginner progress to an IDE when they have learnt the basics of the language and they want to progress to a larger multiple file project - that is where an IDE can really help.

---

### Post by zhogan85 on 2011-01-25
Thanks for the advice Tony Flury, I'll do that while learning. Once I've learned the basics and am ready to move on maybe I'll return to this thread if I still have the same problem. And thanks for the encouraging words llanitedave and to all others for trying to help.

---

### Post by CaptainMark on 2011-01-27
+1 on using geany, i switched over the other week being a python beginner myself its really good and really easy to use, great if your learning multiple languages at once because you can use one program for all your languages

---

### Post by zhogan85 on 2011-02-02
UPDATE:

I seem to have found what was triggering the problem I was having, though I still have not found a solution. Apparently, if I use any hotkeys, like cntrl+N or ctrl+S, that is what is causing the problem of IDLE not allowing me to type. If I instead go to file->open new windown, or file->save I can continue to use IDLE.

I hope this helps a little.

Cheers!

---

### Post by zhogan85 on 2011-02-08
I gave up on my problem for now, but have started using geany, per your suggestions and I like what I've seen thus far so thank you kindly.

---

### Post by Asday on 2011-02-10
> **zhogan85 said:**
> UPDATE:

I seem to have found what was triggering the problem I was having, though I still have not found a solution. Apparently, if I use any hotkeys, like cntrl+N or ctrl+S, that is what is causing the problem of IDLE not allowing me to type. If I instead go to file->open new windown, or file->save I can continue to use IDLE.

I hope this helps a little.

Cheers!

This leads me to think something's keeping your Ctrl key held down, either in hardware or software.  Do you have a spare keyboard you can try?

---

### Post by zhogan85 on 2011-02-10
I don't have one easily accessible but ill try to get my hands on one in the next couple of days. I don't have this problem in any other program though which would lead me to believe it would be a software issue rather than a hardware one. Please correct me if I am wrong to think this.

---

### Post by Asday on 2011-02-10
No, you're probably right.  In windows, there's some awful "feature" stickykeys, which basically turns every modifier into a toggle, and I used to run into this behaviour all the time, but I assume Ubuntu hasn't an analogue, 'cause it's not terrible.

---

### Post by zhogan85 on 2011-02-10
Well if its not in the hardware, do you have any idea for fixing it if its the software that's the problem? I'm not in a rush to solve it as I've been using geany instead but it is frustrating to not have IDLE working properly.

---

### Post by Asday on 2011-02-11
Unfortunately, no, I have little experience.  Sorry.

---

### Post by zhogan85 on 2011-02-11
Well thanks anyway.

---

