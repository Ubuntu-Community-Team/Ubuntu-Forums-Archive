---
title: "Access another program using  java"
date: 2012-04-27
forum: Programming Talk
---

### Post by forsubhi on 2012-04-27
I want to access an already opened calculator using java and  write number on it without using the keyboard 

I mean I want to access another program from my program and use write something in another program without using keyboard (but using java commands) 

how can I do that ? 

and if the description is not clear I can explain more

---

### Post by PaulM1985 on 2012-04-28
I think you have two options for this:

1 - Write some driver for your device so it works like a keyboard.  I have no idea how this works, but someone on here will probably have an idea.  Googling seems to come up with plenty results.

2 - You write the calculator as a server that you can connect to from your input device software and then post requests from the device software to the calculator. - This is probably not the best idea because if you want to use the input device for another piece of software, you need to make that other program a server aswell.  A device driver would be best.

Paul

---

### Post by ofnuts on 2012-04-28
> **forsubhi said:**
> I want to access an already opened calculator using java and  write number on it without using the keyboard 

I mean I want to access another program from my program and use write something in another program without using keyboard (but using java commands) 

how can I do that ? 

and if the description is not clear I can explain more

More or less you want to sent to the code that runs the calculator app the X events it would receive if the user clicked the buttons (or keyed the numbers, which, if the calculator accepts keyboard input, will be much easier since there won't be any need to know the button positions).

But in any case I don't think you can do that with plain Java.

---

### Post by mehaga on 2012-04-29
> **forsubhi said:**
> I want to access an already opened calculator using java and  write number on it without using the keyboard 

I mean I want to access another program from my program and use write something in another program without using keyboard (but using java commands) 

how can I do that ? 

and if the description is not clear I can explain more

In short, description is not clear :)

If you have access to calculator's code (which you probably don't), you can use some inter-process communication mechanism, like message queue. Do you need to target a specific application or any calculator? What exactly are you trying to achieve? What needs to happen after you've sent value(s) to the calculator? Return calculated value? Just display the input?...

---

### Post by forsubhi on 2012-04-29
the specific description is I am working on speech recognition project that convert my speech to command that control any program like calculator , example : 
I say open gedit : the system should open the program ( gedit ) , it is easy and it is achieved by calling the program from java  then I want to say "write one two three" then the gedit should write one two three . 
the calculator has the same description to gedit .

---

### Post by mehaga on 2012-04-30
> **forsubhi said:**
> the specific description is I am working on speech recognition project that convert my speech to command that control any program like calculator , example : 
I say open gedit : the system should open the program ( gedit ) , it is easy and it is achieved by calling the program from java  then I want to say "write one two three" then the gedit should write one two three . 
the calculator has the same description to gedit .

Try this [http://java.dzone.com/tips/write-your-own-custom](http://java.dzone.com/tips/write-your-own-custom)

Just an advice... A guy asked [similar question]("http://stackoverflow.com/questions/7004303/sending-input-to-application-from-java") on SO and got an answer in 20 minutes. That's how I got the above link. When you have a concrete question, it's much better to ask there.

---

