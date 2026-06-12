---
title: "Bit of help plz?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by madrunner on 2008-07-27
hey im new to Ubuntu and to linux as a whole, i installed my copy of Ubuntu using Wubi, and everything was fine, i restarted my computer and selected Ubuntu, it starts a little slow, but after it starts the background image is off center, there is a large chunk of it missing, on the right and bottom part of my moniter, also i never had to login to ubuntu, so my questions are
How can i speed up my Ubuntu?
How can i fix my moniter problem?
How do i install aplications into Ubuntu?
thank you for your help and remember i am new to linux so keep the high tech talk at a minimum, i am a moron.

---

### Post by Vakman on 2008-07-27
Well with Wubi performance does take a bit of a hit, I have to say.
Do you have the correct drivers installed for your video card? Also, which video card do you have. If you do not know please post the output of
```
lspci
```
And lastly, there are a lot of applications here go to Applications > Add/Remove and get the ones you would like. You can search for applications in there. Of course, you can also download applications from websites just as you would in Windows. Except not .exe files of course.

---

### Post by madrunner on 2008-07-27
how do i use an output, lol, sry im very new. and there is no start bar on my ubuntu? or are you talking about this website?

---

### Post by RequinB4 on 2008-07-27
I have the same problem using my TV as a moniter.  You should see if your moniter has an auto adjust button or if you can manually change the horizontal/vertical display of your moniter (this will most of the time be easier then trying to fix the X server itself)

Welcome!  There are a few things you should know (that will hopefully answer your questions)

(The default location for) your menus in on the upper left hand side of your screen.  It's pretty self explanatory, I would have fun poking around :)

One thing to note is applications --> terminal.  This is your command line interface to your machine, and many of the support people on these forums will give you commands to run there (simply because its a lot easier then trying to tell someone how to do it the graphical way). People will generally show these with ```
code boxes
```

Here is a link for more terminal help : [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) 

Check my signature for some important links, these will help a lot, and you DON'T have to get everything at once :P

---

### Post by stevoo on 2008-07-27
since Wubi is an application in Windows, it will always be a lot slower than the actual think. So do not expect major speed ups. But it is good for trials. 
If you like it you can then dual boot and have it as a normal OS and use that instead.
Future hopes :P

i dont now how it works so i can say for sure so ill be takin a hit in the dark here, try opening a terminal and typing
```
metacity --replace 
```

---

### Post by madrunner on 2008-07-27
so see if my moniter has an auto adjust button cuz my moniter displays fine for XP, i should have mentioned i was duel booting before, huh? thank you to both of you! I can not find my terminal because of the problem with my moniter

---

### Post by Vakman on 2008-07-27
To get to the Terminal, go to Applications > Accessories > Terminal. When someone asks you to post the output of something in a code box use the terminal. So anyway, please post the output of 
```
lspci
```

---

### Post by madrunner on 2008-07-27
so wubi is not the real thing then? I have a full screen picture now but all it is is a crosshair mouse and a desktop background nothing else should i install Ubuntu fully?

---

### Post by Vakman on 2008-07-27
Well Wubi is the real thing in a sense, it installs Ubuntu still it will have worse performance than a regular partition with Ubuntu on it. So... did you find the terminal? Go where I said, remember "To get to the Terminal, go to Applications > Accessories > Terminal."?

---

### Post by madrunner on 2008-07-27
this is what my ubuntu looks like [IMG]http://i222.photobucket.com/albums/dd50/madrunner15/ubuntu_desktop.png[/IMG]
no bars like there should be wut did i do wrong? should i try to reinstall it?

---

### Post by Vakman on 2008-07-27
Is it always like that? That is a bit odd. Every time you start up the computer it is like that?

---

### Post by stevoo on 2008-07-27
try hitting ctrl+alt+f1 
that will put you in a terminal.
ctrl+alt+f7 will bring you back into the gui mode.

try everything there.

---

### Post by Vakman on 2008-07-27
Oh good thinking stevoo. Yeah, do that :lolflag:
I didn't even think of it.

---

### Post by madrunner on 2008-07-27
@thisislaw yes its always like that
@Stevoo I will try that thank you!

---

### Post by RequinB4 on 2008-07-27
[http://ubuntuforums.org/showthread.php?t=862686](http://ubuntuforums.org/showthread.php?t=862686)

Try Pressing Alt-F2 and typing ```
gnome-panel
```

---

### Post by madrunner on 2008-07-27
ill try that also just got to wait for Ubuntu to boot up!

---

### Post by sdowney717 on 2008-07-27
wubi works just like it would in ext3 partition. The performance hit is minor. 

It is an extremely easy way to test out and use ubuntu for those who perhaps fear repartitioning. If you want a pure linux system then switch to an regular install. But you likely wont notice the difference.

[http://www.crunchgear.com/2007/10/25/wubi-super-easy-linux-installation/](http://www.crunchgear.com/2007/10/25/wubi-super-easy-linux-installation/)

> 
The performance is identical to a standard installation, except for hard-disk access which is slightly slower. If your hard disk is very fragmented the performance will degenerate. However, once the Ubuntu install created by Wubi has been transferred to a dedicated partition using LVPM, the hard drive access speed will be identical to that of a standard Ubuntu installation."


---

### Post by Vakman on 2008-07-27
If for some reason it says it is not installed, again press ALT + F2 and put this
```
sudo aptitude install gnome-panel
```

---

### Post by madrunner on 2008-07-27
Hitting alt F2 did nothing when i hit ctrl+alt+f1 my moniter went blank then loading please wait... apeared now it is stuck at that screen with a blinking "_" under it

---

### Post by stevoo on 2008-07-27
can you type ?

---

### Post by madrunner on 2008-07-27
yes i can type i typed the sudo thing and hit enter but nothing happend

---

### Post by Vakman on 2008-07-27
Type "sudo aptitude install gnome-panel" only if 
```
gnome-panel
```
did not work.

---

### Post by madrunner on 2008-07-27
nothing at all works its just stuck at Loading Please wait...
any help, and could you point me to a place with a tut to install Ubuntu with out wubi? i think i will try ubuntu by its self

---

### Post by Vakman on 2008-07-27
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
You can install download Ubuntu here. Pick which one you need. And burn the ISO to a CD. Or request a CD I guess but burning the ISO is usually easier if you have a blank CD laying around.

---

### Post by stevoo on 2008-07-27
[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by madrunner on 2008-07-27
i allready have that iso because u need it for Wubi, and i am now looking in to duel booting Ubuntu and Xp thank you to all those who helped me!

---

