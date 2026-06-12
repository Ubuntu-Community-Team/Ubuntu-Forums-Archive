---
title: "How to use Quickly and Terminal"
date: 2011-06-28
forum: Programming Talk
---

### Post by Mr_Electric on 2011-06-28
Hi Everyone,

I am new to Ubuntu and python programming and I have a couple of questions:

1) Is there a way for a gui application (developed with quickly) to type commands in terminal( screen /dev/ttyACM0 to control my arduino) and how do I write a python code for it (so that if a button is clicked it sends a 1, for example)
2) Is there a way to interface a webcam window into the application and how would I do that


Thank You,
mr_e

---

### Post by TwoEars on 2011-06-28
> **Mr_Electric said:**
> Hi Everyone,

I am new to Ubuntu and python programming and I have a couple of questions:

1) Is there a way for a gui application (developed with quickly) to type commands in terminal( screen /dev/ttyACM0 to control my arduino) and how do I write a python code for it (so that if a button is clicked it sends a 1, for example)
2) Is there a way to interface a webcam window into the application and how would I do that


Thank You,
mr_e

1) Not quite sure what you're asking for. You can take the input from a user and run it, yes. And yes, you can run native ocmmands using the sys module.

2) You can use gstreamer to do this, or check out V4L

Also, I don't recommend doing anything nor learning through Quickly. Everything you do will be more worthwhile if you learn to program properly and don't use programs like Quickly.

---

### Post by Kavita123 on 2011-06-29
your question did not tell everything you want to know! please be more descriptive so anybody can answer your question.

---

### Post by Mr_Electric on 2011-06-29
I would like to develop an application in the GUI that sends serial commands to my arduino ([http://arduino.cc/](http://arduino.cc/)). I have already found a way to send commands through Terminal by using the screen /dev/tty commands (mine shows up as /dev/ttyACM0). I need help on writing the python program that types commands in the Terminal similar to Mac OS's Automator that gives a message to the arduino when I click a button. 




I hope this is more specific
Thanks,
mr_e

---

