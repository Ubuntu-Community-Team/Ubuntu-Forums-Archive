---
title: "python, pida, opengl, HELP!! (it seems awfully slow)"
date: 2006-04-05
forum: Programming Talk
---

### Post by Choad on 2006-04-05
well, firstly, when i press run in pida, the project doesnt actually run. it says something in a python console think and does nothing, but thats not such a biggy, i can just execute the file myself from the file manager

what is more worrying however is that i am learning to program in opengl, i found som eexamples on the net, and they run very very slowly!

even simple things like a rotating square...

and it completely maxes out my processor (amd athlkon xp 2000)

however i have xgl up and running very smoothly with my radeon 9550, which puts no strain on the processor at all!

so i think it isnt using my gpu

any suggestions?

---

### Post by aafshar on 2006-04-09
Hi, I am the PIDA author. Which version of PIDA? And also, what is the "it says something in a python console think and does nothing". This is worth actually reading.

I have recently been told that the Dapper version of PIDA is very old. This is rather depressing, as the one in Debian Unstable is very new.

Ali

---

### Post by Choad on 2006-04-10
hey, you are the author? congratulations on a fine program!

if i load the project, and then press F5 i get the error in "error1.png"

im not sure if this could be anything at all to do with the error but it doesnt actually output the correct filename for the project. it says 

'home/richard/my' ,
'.py'

as you can see in the picture, wheras the project is called "my proj.py"

bu that could be nothing...

the second image is what happens when i load the project, press "debug", and then press "continue"

it loads fine!?

the 3rd image is to show how much cpu that simple project is taking up. 100% all the time. there must be something wrong with this! i have a radeon 9550 and an xp athlon 2000 (not the fastest cpu in the world, but easily capable of games such as red faction, dawn of war etc)

oh the version is 0.2.2

---

### Post by LKRaider on 2006-04-10
The processor issue may be due you using Xgl.

Try running on a Xorg server and see if it makes a difference.

---

### Post by Choad on 2006-04-10
[QUOTE=LKRaider]The processor issue may be due you using Xgl.

Try running on a Xorg server and see if it makes a difference.[/QUOTE]
how do i do that? sorry im not that great in linux yet :)

---

### Post by aafshar on 2006-04-16
[QUOTE=Choad]

oh the version is 0.2.2[/QUOTE]

In Ubuntu terms that is about the same age as Hoary, and unfortunately we can't be supporting it. Ubuntu, please be encouraged to upgrade this package.

Ali

---

