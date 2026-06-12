---
title: "Sound from Line In"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Macdelaney on 2008-08-16
I have my xbox 360 connected to the Line In port of my pc so the sound comes out of the speakers. I installed Ubuntu yesterday, and cant find a way to make it work. I'm new to this, so i havent try anything and i'm already short of ideas.
Any help at all will be much appreciated, and thanks for taking your time to read this.

---

### Post by nicedude on 2008-08-16
try the following command at a terminal and make sure that the line in is turned up.

sudo alsamixer

Hope that works

---

### Post by Macdelaney on 2008-08-16
I have alredy tried that, but didnt work
Thanks for replying!

---

### Post by Macdelaney on 2008-08-16
I've just found that if I set the gnome-sound-recorder to record from "Capture 2" it records some VERY distorted sound while I play, it seens to be from the xbox because of some sounds I could make uo between all the gibberish, but I dont know how to make that sound come directly to the speakers (without recording and then listening to it), and even then, the sound is incredibly messed up. Any ideas?

---

### Post by nicedude on 2008-08-17
Heres two more commands you can run to check settings

In sound properties you might try seeing if yours is using alsa or pulse etc and try different ones

and in sound recorder you might make sure you have line in selcted

Here are the command line commands to open them

gnome-sound-properties
gnome-sound-recorder

---

