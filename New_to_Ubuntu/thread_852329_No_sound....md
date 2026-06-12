---
title: "No sound..."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by PHATSPEED7x on 2008-07-07
My computer has no sound. I noticed that xubuntu didn't load any sound mixer for my computer. I have no little speaker icon, or volume control. How do I fix this? I bought new speakers, and I would really like to hear them.

---

### Post by AOZ on 2008-07-07
hmmm i dont know how this will work in xubuntu but i remember having a similar issue and fixing it by getting the ALSA mixer GUI via synaptic. There you can alter many settings relating to sound

You may also want to check for any sound drivers you may be missing if this is a new install

As for the speaker icon, you can right click on the panel on the top of your screen and select add to panel, then add the volume control

---

### Post by PHATSPEED7x on 2008-07-07
How would I check for the sound drivers...

---

### Post by AOZ on 2008-07-07
well im not sure if this works becasue i use ubuntu, but there is an option in system>admin>Hardware testing. do the sound test. If that doesnt work than go system>admin>hardware drivers. byt he way i guess i should ask what soundcard you use

---

### Post by PHATSPEED7x on 2008-07-07
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00190802&lc=en&cc=us&dlc=en&product=92892&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00190802&lc=en&cc=us&dlc=en&product=92892&lang=en)

Here are the computer specs...

---

### Post by AOZ on 2008-07-07
It looks like a few other people have had troubles with the ESS sound card aswell. try opening a terminal Applications>acceessories>terminal and just type alsamixer. make sure the master, PCM and frotn are all on

---

### Post by PHATSPEED7x on 2008-07-07
yes all are on, and all are at 100%.

---

### Post by PHATSPEED7x on 2008-07-07
LOL Figured it out. Helps to have the jack on the back of the computer pluged into the right hole. LOL. THanks alot for the help though...

---

### Post by AOZ on 2008-07-07
lol no problem

---

