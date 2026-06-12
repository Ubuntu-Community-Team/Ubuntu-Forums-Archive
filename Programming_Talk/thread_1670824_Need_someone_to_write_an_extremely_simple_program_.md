---
title: "Need someone to write an extremely simple program for me"
date: 2011-01-19
forum: Programming Talk
---

### Post by maxsideburn on 2011-01-19
I am looking for someone who can write a program for me, it would probably take an experienced programmer 5 minutes or less. Alas my area of expertise is in graphics and audio/video, not programming.

It's for a good cause. It's a program that could help people with stroke-damage to their visual cortex regain some vision. I'm trying to help my father out. Initially I was going to make something like this using the video creation software I'm familiar with, but I think a program would be better.

Here is what I need:

A simple program that when executed goes fullscreen and displays a solid bright green background. somewhere on the screen there should be a small black square randomly placed. when the user presses the spacebar (to confirm they've found the square) it should disappear and another random black square should appear somewhere else. pressing escape should close the program.


Thank you so much for looking at this. Any help would be most appreciated.

---

### Post by worksofcraft on 2011-01-19
> **maxsideburn said:**
> I am looking for someone who can write a program for me, it would probably take an experienced programmer 5 minutes or less. Alas my area of expertise is in graphics and audio/video, not programming.

It's for a good cause. It's a program that could help people with stroke-damage to their visual cortex regain some vision. I'm trying to help my father out. Initially I was going to make something like this using the video creation software I'm familiar with, but I think a program would be better.

Here is what I need:

A simple program that when executed goes fullscreen and displays a solid bright green background. somewhere on the screen there should be a small black square randomly placed. when the user presses the spacebar (to confirm they've found the square) it should disappear and another random black square should appear somewhere else. pressing escape should close the program.


Thank you so much for looking at this. Any help would be most appreciated.

This does indeed sound quite easy, but how would you know that the user isn't simply pressing the space bar without even looking for the square?

Do you envisage adding things to it like perhaps monitoring the time it takes to find the square or changing colors and shapes or perhaps add some sound effects so that the user gets a cue when the next random square has appeared?

If things like this are known it can often be taken into consideration during the initial design :)

---

### Post by maxsideburn on 2011-01-19
not necessary.

if the user goes on to the next square without looking for the first one they are defeating the purpose of using the program. there is no purpose to "cheating", it would not help them in any way.

a simple program like I described should do the job just fine. it's simply to give them something small to find each time. I've made a prototype version on DVD...but the squares are not random, and therefore the pattern can be learned. I'm trying to avoid that.

---

### Post by zoidbergi on 2011-01-19
Hey

I wrote a quick and ugly python app that does this for you. Quit with space or Alt-f4, new boxes with space.

Open it up in a text editor and edit on the first lines if you want to change box size or color. It requires gtk and cairo bindings for python.

---

### Post by zoidbergi on 2011-01-19
multipost

---

### Post by zoidbergi on 2011-01-19
multipost and cant find where delete is..sigh

---

### Post by worksofcraft on 2011-01-19
> **maxsideburn said:**
> not necessary.

if the user goes on to the next square without looking for the first one they are defeating the purpose of using the program. there is no purpose to "cheating", it would not help them in any way.

a simple program like I described should do the job just fine. it's simply to give them something small to find each time. I've made a prototype version on DVD...but the squares are not random, and therefore the pattern can be learned. I'm trying to avoid that.

Hey max', I did attached program, but can't work out how to make it go full screen other than clicking on the maximize button at the moment :confused:

Archive has 64 bit and 32 bit Linux versions. It can be recompiled for Windows and OS X and Sun OS I believe.

Also enclosed is the source code, but it uses a library known as AGG which I have not enclosed.

p.s. I deleted the archive here as it has been superseded in a later post... Still haven't managed to make it go full screen though, looks like I might have to hack the X11 platform support for AGG :(

---

### Post by sdowney717 on 2011-01-19
zoidbergi very nice program.

just need to download and goto permissions and make it executable.
then click on it and select run in terminal

---

### Post by kostkon on 2011-01-19
A small one (few lines) and lightweight, made with pygame. The only thing needed is the installation of pygame, which is very easy, i.e.
```
sudo apt-get install python-pygame
```

If you want, you can easily change the size of the square (it's now 20 pixels wide) and the background colour, by editing the values of the following lines in the script file:
```
BG_COLOUR = 114, 247, 99  # RGB light green (114, 247, 99)
RECTANGLE_COLOUR = 0 ,0 ,0  # RGB black
RECTANGLE_WIDTH = RECTANGLE_HEIGHT = 20  # size in pixels
```

Make it executable and then double-click on it and select *run in terminal*.

---

### Post by maxsideburn on 2011-01-20
thanks a bunch guys.

I've given it some more thought and considered the following:

**A way to track progress**: Each time the user completes a set of 50 it could show them the time it took to complete those 50. They could write down and log their progress over time.

**Hand-eye coordination**: Perhaps simply hitting a space bar isn't the optimal thing, I was only thinking about retraining the eyes, but if there is motor damage it may help a lot to have the person actually click on the box when they find it to advance to the next one. This would retrain the brain to not only see on that side, but to co-ordinate with that visual stimuli. Of course the box would have to be a little larger, at least as big as a mouse cursor.

Again I wish I had some idea of how to program this myself, but alas I'm hopeless when it comes to any kind of coding or scripting.

---

### Post by worksofcraft on 2011-01-20
> **maxsideburn said:**
> thanks a bunch guys.

I've given it some more thought and considered the following:

**A way to track progress**: Each time the user completes a set of 50 it could show them the time it took to complete those 50. They could write down and log their progress over time.

**Hand-eye coordination**: Perhaps simply hitting a space bar isn't the optimal thing, I was only thinking about retraining the eyes, but if there is motor damage it may help a lot to have the person actually click on the box when they find it to advance to the next one. This would retrain the brain to not only see on that side, but to co-ordinate with that visual stimuli. Of course the box would have to be a little larger, at least as big as a mouse cursor.

Again I wish I had some idea of how to program this myself, but alas I'm hopeless when it comes to any kind of coding or scripting.

Easier done then said in this case I think - lol.
I just enclose 32 bit version this time cuz it seems to also work on 64 bit Ubuntu.
I also left in the key press to reposition the random square but it doesn't count for the time/accuracy thing and can be used to simply restart the timer like if the subject needed to attend to something else for a while.

To avoid clutter of the display I output average time and positioning accuracy of clicks to stdout on program exit so you could pipe that into a log file and monitor progress or maybe even import in a spread sheet so you can make a graph of progress :)
OTOH if you prefer I can put controls on the screen to adjust size of the random square and also the accuracy that you have to click it with... as well as display performance... it's just that I thought it might be distracting for someone who has visual or coordination problems.

Anyway soz to who ever viewed version 0.0.2
I learned that to get elapsed time I should not use the clock() function but gettimeofday() instead... hence now version 0.0.3

---

