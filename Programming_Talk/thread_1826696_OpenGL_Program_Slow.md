---
title: "OpenGL Program Slow"
date: 2011-08-16
forum: Programming Talk
---

### Post by dr1134 on 2011-08-16
It is late and I am at a lost as what is wrong.

The two OS that I am using are:

Ubuntu Desktop 11.04
with gnu g++ compiler

Windows XP
with MinGw complier

Both use the same IDE: Code Blocks

I am using OpenGl and SDL

I am making a breakout like game from a tutorial. So far all I have is white screen with a black 2D rectangle. So not graphics graphics heavy stuff. I have it set up so that it moves on the x-axis when the left or right arrow key is hit. In the tutorial the rectangle moves on the x-axis by 0.5 and when I do that in my program it moves really slow. The only why to get it to move at a fast speed is to set it to 5 which is no big deal. However when I go to compile the program in Windows XP, 5 is way too fast and 0.5 is OK.

I can't for the life of me find out why there is a difference between the  Windows XP and Ubuntu program. The code that is compiled is the same on Windows and Ubuntu(Except for the speed). The tutorial use Linux and the gnu g++ compiler and when I copy the source code it too is slow but it worked in the tutorial. So it can't have been an error I made and I checked.

I have looked on Google for anything relating to this. I read that direct rendering is the problem but I have direct rendering on. Also the driver software for my Intel integrated graphics card is up to date. I have never had this problem before with any OpenGl program of running slow. 

Here is the link to the source code I am using: [http://pastebin.com/5kYn4XxW](http://pastebin.com/5kYn4XxW)

Also the tutorial was not using Ubuntu.

---

### Post by dr1134 on 2011-08-17
The Ubuntu and the Windows OS are not on the same computer. The Ubuntu OS dual boots with Windows Vista. Windows Vista use the same tools as the other two.

So I booted up Vista and compiled the code and the same thing happed. Moving at 5 across the x-axis was way to fast. So it has to be Ubuntu and not hardware. I have no idea why that is, I just check and I have the right driver software for my graphics card and it is up to date. 

Any help would be greatly appreciated as I can't not do anything more with the program until it is fixed.

---

### Post by dr1134 on 2011-08-17
I got an the driver from the Intel website and load it. Then I complied the program and it worked!!!

Why I have no idea.

---

### Post by kaktux on 2011-08-19
edit - deleted- something went wrong. posted in wrong thread.

---

