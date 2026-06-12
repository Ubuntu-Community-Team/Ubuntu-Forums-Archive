---
title: "Turning camera phone into webcam"
date: 2010-11-21
forum: Programming Talk
---

### Post by ntd172 on 2010-11-21
Hi guys, 

I would like to turn my camera phone into a webcam for pc. And I've been searching the solution and the open source for the program. However, I didn't find much. 
I don't know where and how I should to start up my project. I need help from you guys. 

Thank you.

---

### Post by Zugzwang on 2010-11-21
Probably the first thing to check is if you phone can be "convinced" to do that task. Try to get hold of technical documentation of it. 

Is there a Windows program to do what you want? Probably the phone doesn't have that functionality. In that case, you can
[LIST=1]
[*]Try to alter its firmware (very tricky, not to say hopeless)
[*]Try to load a Java mobile edition program to it that captures camera data. Note that for this solution, the phone must provide the functionality to get access to the camera by a Java program (not too unlikely) and to somehow allow sending USB data (very unlikely).
[/LIST]

---

### Post by ntd172 on 2010-11-21
Hi Zugzwang, thank you for your reply. Actually I intend to write a program in Linux, not in Windows. 

Do you have any idea how to start up my project? Thank you.

---

### Post by soapytheclown on 2010-11-22
this would depend greatly on the phone you're trying to use and its very unlikley that you'd be able to write one program for all phones. you should probably start by writing some programs that run on your phone that get access to the camera since thats the base of your project and to begin that you should look for the sdk and developer tools for your phone OS.

---

### Post by Zugzwang on 2010-11-22
> **ntd172 said:**
> Hi Zugzwang, thank you for your reply. Actually I intend to write a program in Linux, not in Windows. 


What I was trying to say was: if there is a Windows program to do what you want, then you have some assurance that the phone is actually capable of doing what you want it to do. If not, whether the phone supports what you want it to do is totally open. Other than that, as I've already written, you might want to consider to start by checking if you phone can be "convinced" to do that task.

---

