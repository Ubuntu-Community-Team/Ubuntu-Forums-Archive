---
title: "Having a problem withe the sound!"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Tarif Ezaz on 2008-05-14
I have installed ubuntu 8.04 in my 32-bit pc. But I'm having a problem with the sound. I can't hear anything, not even the welcome tune! My sound card is SigmaTel Audio and I've heard ubuntu is ok with it. So, what's the problem.

I am a user of ubuntu for over six months. I still have my laptop installed with 7.04. But did not have any problems with that:). I've already gave many of my friends this version and they will also ask for help if there's a problem:mad:. So please help!

I have Pentium D and 512 RAM

Thanks in advance!
Tarif

---

### Post by nicedude on 2008-05-14
I am not sure this will help but if you go to top menu bar and click System -> Preferences -> Sound , then when that comes up try selecting Alsa for all the device settings then just test with the button right next to the selection.

Hope that works :-)

---

### Post by Michael.Godawski on 2008-05-14
Let's start easy:

run ```
alsamixer
``` in terminal and increase the volume of master and pcv if down.

---

### Post by Tarif Ezaz on 2008-05-19
Thanks Michael and Nicedude for your support and sorry for being late. Yes, I've already checked System -> Preferences -> Sound with every possible combinations. And also I've tried alsamixer, but it's not working as yet. I think we have a more complicated problem here!

Waiting for support :D

Tarif

---

### Post by bmac on 2008-05-19
This may seem like a lame thought, but did you check you volume control applet and assure that master - pcm - cd - etc are turn up or not muted???
Right click on volume control and select open volume control....

Just a thought...

---

### Post by Tarif Ezaz on 2008-05-19
Yup, bmac. I've tried that as well. But to no avail :confused:

---

### Post by Tarif Ezaz on 2008-05-20
They are showing the name at alsamixer! So, what to do?

---

