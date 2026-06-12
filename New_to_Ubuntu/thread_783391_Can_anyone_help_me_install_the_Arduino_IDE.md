---
title: "Can anyone help me install the Arduino IDE?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by cmdowns on 2008-05-05
I posted this as a reply to the original thread entitled "Arduino Diecimilia on Feisty Fawn" in Tutorials & Tips, but I was afraid it might not get noticed there, so I'm reposting here as a new thread. Anyways. . .

I'm a Linux noob and a new Ubuntu user working with Gutsy Gibbon. I'm attempting to install the Arduino IDE on my laptop. I'm trying to follow the instruction in the first post in [this thread](http://ubuntuforums.org/showthread.php?t=560259), but my knowledge fails me when I get to this part:
> **sedition said:**
> * Enter the extracted arduino folder, gedit and replace the launcher (arduino)


I'm sure this is something incredibly basic, but I'm at a loss. I have downloaded and extracted the arduino app, but I don't really understand what the OP means by "gedit and replace the launcher (arduino)". Could some benevolent guru spell this out for me please? I will repay you with praise and eternal gratitude (I know, what a deal!).

---

### Post by Keen101 on 2008-06-07
I'm not a linux guru, but i got the Arduino software to run on my 8.04 Heron system the other day. 

[http://www.arduino.cc/playground/Learning/Linux](http://www.arduino.cc/playground/Learning/Linux)

Step one: get  java runtime (jre. I searched for "jre" in synaptic package manager, and installed the "openjdk-6-jre" packages. Works great.

Step two: install the "gcc-avr" tools. also, the "binutils-avr", and the "avrdude" packages from the repositories. also the "acr-libc" package.

Step three:  searched for the "brltty" package in synaptic, and removed it just in case.

Step four: copy and extract the arduino software to my desktop. Open the folder. And double click on the "arduino" script file. When prompted what to do click "run"

hope that helps.

-Andrew
-keen101

---

### Post by cmdowns on 2008-06-07
Thanks for the reply. I wrote a post about the same issue in the Arduino forums. Someone there informed me that it should more or less just work. Strangely enough, it did. I can't believe I didn't just try to install it as is, but that really is the only explanation. That, or I screwed up something  significant the first time.

Anyway, it works now. Thanks for the reply.

---

### Post by Keen101 on 2008-06-08
that's good to hear. Well, if you figured it out, then you should mark this thread as "solved".


-keen101

---

