---
title: "[SOLVED] Writing Japanese Characters"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by FaBioW114 on 2008-09-28
Hello,

I need to install japanese fonts (hiragana, katakana and kanji). I've seen some tutorials in the net, but they are not what i'm searching for. I don't wanna change my system's languange nor change my keyboard settings to write only japanese or only english, just want to be able to write japanese characters anywhere. One of these tutorials was what I wanted, but something was wrong... =( it said something about pressing <SHIFT>+<SPACEBAR> (after installing some packages etc, of course) and the keyboard input automatically changes to japanese writing. Is it really possible? If a press these keys i can write japanese characters anywhere (firefox, openoffice, gedit,...)? 
I use ubuntu 7.04 feisty fawn. Whoever answers my request, please remember I'm a ubuntu newbie, i barely know how to use the terminal... =/

Thank you very much!

---

### Post by Pro-reason on 2008-09-28
I don't think there are any tutorials designed to set up your computer to input only Japanese, because Japanese people need to input things in our Roman alphabet all the time.

I think you misunderstood those tutorials.  They are for setting it up so that you can input both languages.  I'd advise you to go back and re-read them.  They are what you need.

&#24184;&#36939;&#12434;&#31048;&#12426;&#12414;&#12377;

---

### Post by ShadowWraith on 2008-09-28
I use a very handy program called scim, which pops up a little bar that you can use to select basically any language in the corner of your screen.
To install it, go into the menu and System>Administration>Synaptic and search for scim. Or, put this into your console:
**sudo apt-get install scim**

---

### Post by FaBioW114 on 2008-09-29
> **Pro-reason said:**
> I don't think there are any tutorials designed to set up your computer to input only Japanese, because Japanese people need to input things in our Roman alphabet all the time.

I think you misunderstood those tutorials.  They are for setting it up so that you can input both languages.  I'd advise you to go back and re-read them.  They are what you need.

&#24184;&#36939;&#12434;&#31048;&#12426;&#12414;&#12377;

I don't want to write only japanese, i want to change to japanese or to english whenever i want by pressing some kind of command or some other simple way. But if it's not possible, is there a way in which i can use japanese characters in a specific program? For exmaple in openoffice, if i change some settings there, if i write "ka", then a 'ka' characher appears?

---

### Post by hashimoto on 2008-09-29
> **FaBioW114 said:**
> I don't want to write only japanese, i want to change to japanese or to english whenever i want by pressing some kind of command 

FaBioW,

I just tested this doing as was told here: [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
Also: add japanese language support, make sure you have the scim installed (at least it is by default in Hardy). Reboot, and you can easily change back and forth between roman and japanese characters with ctrl+space.

---

### Post by FaBioW114 on 2008-09-29
thank you ShadowWraith and hashimoto,

You both helped, I tried SahdowWraith's way, but there was something missing (the enable support box, my fault >P) and hashimoto did it, thank you guys! \o/

---

### Post by Pro-reason on 2008-09-29
> **FaBioW114 said:**
> I don't want to write only japanese, i want to change to japanese or to english whenever i want by pressing some kind of command or some other simple way. But if it's not possible, is there a way in which i can use japanese characters in a specific program? For exmaple in openoffice, if i change some settings there, if i write "ka", then a 'ka' characher appears?

Through inattention, you have completely misunderstood not only the SCIM tutorials you were reading, but also my clarification.

---

