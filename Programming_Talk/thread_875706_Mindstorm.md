---
title: "Mindstorm"
date: 2008-07-31
forum: Programming Talk
---

### Post by Uchiha_madara on 2008-07-31
Hi Every one ,



i have to Create this Project :

 Buying LEGO Mindstorm Robot NXT and Programming it , But I don't Know what is the Perfect Programming Languages for this Issue
-I heared that C, C#, and visual basic 2005 are easy to Programming - , i need sites, Links, tutorial's that talking about Programming The Robot's

---

### Post by Nepherte on 2008-07-31
You could do it in Java as well.

---

### Post by Uchiha_madara on 2008-07-31
cool ...I need e-book,pdf files,link's Or tutorial 

Explain Programming robot's With Java, Please

---

### Post by Rocket2DMn on 2008-07-31
Moved to Programming Talk, you should be able to get more help here with your programming project.  Good luck.

---

### Post by nvteighen on 2008-07-31
> **Uchiha_madara said:**
> Hi Every one ,



i have to Create this Project :

 Buying LEGO Mindstorm Robot NXT and Programming it , But I don't Know what is the Perfect Programming Languages for this Issue
-I heared that C, C#, and visual basic 2005 are easy to Programming - , i need sites, Links, tutorial's that talking about Programming The Robot's
Who told you C or C++ is easy? If you already know some programming, maybe, but if not, prepare yourself to learn them with patience.

I believe Mindstorm robots use their own interface from Lego... possibly not Linux compatible.

---

### Post by henchman on 2008-07-31
have a look at 

[http://en.wikipedia.org/wiki/LeJOS](http://en.wikipedia.org/wiki/LeJOS)

this is used in our school to program the robots. it has an easy to lern api, and because you program in java you don't have to care for clearing your heap :)

---

### Post by dperfors on 2008-07-31
You can use any language.. I used smalltalk to communicate with the mindstorm NXT via the bluetooth adapter (virtual serial port). The downside is that it is not always possible to store the program on the robot itself, but if you don't need that, you are fine :)

---

### Post by Zugzwang on 2008-07-31
dperfors is 100% right. You can't use the usual compilers since the Mindstorm brick is not x86-compatible. You need to use some compiler that can generate programs for the robot and you are technically restricted to use a language that one of this compilers supports. I know that there is some "C" variant for doing this. 

However, if you plan to interface with the robot you can of course use any language for the "regular computer"-side.

---

### Post by lordhaworth on 2008-07-31
As far as ease is concerned it depends on how your willing to learn, im not very familiar with java but in languages like C you can build up most things you want in the code from scratch, so it may be difficult at first but you can do most things eventually without having to draw on anything more than your imagination. 
Whereas java (i believe) has a lot more built in functions? So there would probably be a bit more research for specific functions as you want them. 
(I would like to learn java soon to expand my programming horizons so correct me if Im wrong and ill start the learning now!)

---

### Post by pmasiar on 2008-07-31
You should get much better informed advice from mindstorm forums/mailing lists - and you need to find them, because you will have questions specific to LEGO, beyond simple programming.

Wikipedia knows all available languages, and pro/cons: [http://en.wikipedia.org/wiki/Lego_Mindstorms_NXT](http://en.wikipedia.org/wiki/Lego_Mindstorms_NXT)

---

