---
title: "Problem using HandBrake within a Python program"
date: 2009-05-19
forum: Programming Talk
---

### Post by M4rotku on 2009-05-19
Hey guys,

Lately I've had the urge to watch all of the episodes of the show "Wonder Years" in order.  My dad has them on DVD, but I wanted to rip them to my hard drive while I was at it in case I want to watch them again while away at college.

I was frustrated with how in AcidRip, one has to manually set all of the settings and enter the title each time for each episode.  This meant setting an episode, letting it run for 20 minutes, coming back to my laptop and setting another one, etc.  Very tedious.

I decided that I wanted to write a program to automate this task. :D
Since I've been trying to learn Python, I decided to use Python instead of C++ with which I have more experience.  However, I've run into a few errors and I was wondering if you guys could help a bit.  I've included the .py file, the text file that the program creates, and the output of the program when ran in the terminal.

______________________________________________________________________

The following errors occurred when I ran the program and I have no clue what they mean.  Here they are from the output file:

line 25:  
Output format couldn't be guessed from file name, using default.

lines 46-47: 
Segmentation fault
sh: --format: not found

line 118:
sh: Syntax error: Unterminated quoted string

_______________________________________________________________________

The error in line 25 reports that the output format couldn't be guessed from file name, but I told it in the command given to HandBrake to use .avi

The same thing confuses me about the errors in lines 46-47 and I have no idea what the error in line 118 means.

I realize that this is a very long and tedious question, but any help would be appreciated.  I know that my program is very amateur, but I still don't understand how that is causing these errors.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-05-19
Just a note that I forgot to add.

The first episode was not ripped.  I'm sure you guys probably know that from the errors, but I just realized it. ](*,)

---

### Post by M4rotku on 2009-05-19
Another note, the fifth episode failed to rip.

---

### Post by steeleyuk on 2009-05-19
I think I've sorted it.

You needed extra "" around the filename in the HandBrake string.

I also didn't get chance to check multiple tracks, the only DVD I have at hand is Raising Arizona which has one track.

Edit: I'm no Python expert either... :) Still learning a lot myself.

---

### Post by M4rotku on 2009-05-19
Thanks, that fixed the problem.

However, I'm having another problem.  Hopefully an easier-to-fix one.  When I set the program to rip 15 or so shows in a row, it overheats and the dvd drive sounds really bad.  I thought I had broken it.  Is there any kind of a pause function that I can use to pause the program for a minute or two so that it can cool down?

Also, does anyone have any idea how long I should pause it in between rips so that I am not too hard on my drive?

Much thanks,
M4rotku

---

### Post by steeleyuk on 2009-05-20
You can use the sleep module.

At the top of your code, put: import time

Then probably after you've ripped each episode, use time.sleep(x) where x equals the number of seconds.

---

