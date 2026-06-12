---
title: "Nvidia 8700 w/ OpenGL Application is Choppy - Why?"
date: 2008-01-16
forum: Programming Talk
---

### Post by jeremy.oakes on 2008-01-16
When I try to run my OpenGL application in full screen resolution of 1920x1200 the updates are very choppy.

I am running a Dell XPS M1730 with  Dual Nvidia 8700. I installed the latest nvidia drivers using envy. I expect that I shouldn't have any issues running my openGL app. 

Should I be using some special nvidia libraries to offload the openGl calls to the Gpu? Or Is this handled my the OS automagically? 

I'm compiling against the -lglut library.

I would also like to note that I'm running dual core machine and bothe processors are pegged when I'm running my app. Cpu1 is pegged 100% with my applcation, and Cpu2 is pegged at about 95-97% with Xorg.

Any help is much appreciated!

---

### Post by luisromangz on 2008-01-17
Are other apps that use opengl affected by this? Maybe is a defect in your code... 

And well, about special nvidia libraries to offload the opengl calls to the GPU, eerrr, they are provided by the driver, you know.

---

### Post by jeremy.oakes on 2008-01-17
Fixed - There was a loop in the code causing the system to suffer.

---

### Post by *LO*Dman on 2008-05-17
hello there i have the same laptop as you the XPS M1730 I am new to ubuntu thoguth I would check it out I do not knowh ow to do anythign can you help me the biggest resolution I can get is like 640x cometing where o I get the ubuntu drivers    if you could respond to my email that would be good [email]storyderrick@gmail.com[/email]

---

