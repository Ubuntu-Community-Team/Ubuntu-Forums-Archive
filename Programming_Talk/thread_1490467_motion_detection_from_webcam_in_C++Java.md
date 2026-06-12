---
title: "motion detection from webcam in C++/Java/*"
date: 2010-05-22
forum: Programming Talk
---

### Post by shababhsiddique on 2010-05-22
Hi
i am working on a project where a robotic arm plays a game of tic tac toe. the arm is complete so is the AI. now i am thinking about re designing the input process.

I wanted to take input through parallel port(laser sensors) for ease but now electronics are becoming complicated. and it is becoming a terminal more than a Robot.

I just wonder if i can do some programming here

How can i take image from the webcam and detect different colors from it (C++ preferred as i know it well and the other parts are written with it but you can also show me Java advice ) 

I need it really soon plz help me out with this. thanks in advance

---

### Post by shababhsiddique on 2010-05-22
bump

---

### Post by tookyourtime on 2010-05-22
vvvv is used for this sort of thing. Whether you can get it to work on linux or not I dunno.

You can write custom plugins, do loads of real time stuff, probably interface it with other programs. Its got motion and colour detection stuff built in.

[http://vvvv.org/tiki-index.php](http://vvvv.org/tiki-index.php)

---

### Post by PaulM1985 on 2010-05-23
I have had a little look into this area with intention of doing something like this (motion detection stuff) but never really got round to it.

I found opencv ([http://opencv.willowgarage.com/wiki/](http://opencv.willowgarage.com/wiki/)).  I haven't used it, but the documentation looks pretty good and seems to have plenty of useful functions for things like 3d reconstruction.

Paul

(This is for C++, C or Python, not Java)

---

### Post by shababhsiddique on 2010-05-23
thanks both of you I am lookin into it. Anyway do you guys suggest me any starting point for learnin C# as a whole?

---

### Post by PaulM1985 on 2010-05-23
Sorry, I didn't really understand the question.

Do I suggest that you start learning C#?
- I don't think the linux support for C# is that good yet.  Mono seems to be ok.  I tend to stick with C++ and Java for personal development.  However, there seems to be lots of companies wanting people who can develop with C#.  At work I am using C# for projects that I am working on.  So it would probably be worth learning for employment purposes.

Can I suggest any starting points for learning C#?
The O'Reilly series has a pretty good book.  Not sure of the title but would be easy to find on Google.  If you already know Java you will probably pick it up quite quickly as it is fairly similar.

Hope this helps.

Paul

---

### Post by shababhsiddique on 2010-05-24
> **PaulM1985 said:**
> Sorry, I didn't really understand the question.

Do I suggest that you start learning C#?
- I don't think the linux support for C# is that good yet.  Mono seems to be ok.  I tend to stick with C++ and Java for personal development.  However, there seems to be lots of companies wanting people who can develop with C#.  At work I am using C# for projects that I am working on.  So it would probably be worth learning for employment purposes.

Can I suggest any starting points for learning C#?
The O'Reilly series has a pretty good book.  Not sure of the title but would be easy to find on Google.  If you already know Java you will probably pick it up quite quickly as it is fairly similar.

Hope this helps.

Paul

thanks. Unfortunately i cant find any of them in my stores. and i cant even afford to buy online. 

My main target is to detect color/motion from captured image of Webcam on a robotic project. I have done so far in C++ but now it seems that i cant do webcam stuff in C++ that easily(may be possible but i have no clues no tutorials)

i wish to finish the project so if I have to learn a bit of C# for that it would be ok.

---

### Post by PaulM1985 on 2010-05-24
> **shababhsiddique said:**
> My main target is to detect color/motion from captured image of Webcam on a robotic project. I have done so far in C++ but now it seems that i cant do webcam stuff in C++ that easily(may be possible but i have no clues no tutorials)

It looks as though you could do this with OpenCV.  Look at the VideoCapture class.

---

### Post by shababhsiddique on 2010-05-27
> **PaulM1985 said:**
> It looks as though you could do this with OpenCV.  Look at the VideoCapture class.

thanks. sorry for late reply

I found OPENCV working and looks like a cool thing to hang out with. anyone here have any idea were to go from here.

i have already gone through the vid capture and face recognition functions a little bit.

thanks again to the community! love u guys

---

