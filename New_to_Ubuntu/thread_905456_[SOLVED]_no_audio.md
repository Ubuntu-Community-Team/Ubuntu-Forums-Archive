---
title: "[SOLVED] no audio"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-30
Hello!
my speakers were working fine, but then I installed limewire. I didnt download anything, just played a few songs since I couldnt figure out how to get ubuntu-restricted-extras to do so. anyway, then I go to youtube and no sound! then metacafe no sound! I exited limewire and checked my wires but still no go.
Help please?

---

### Post by gmxgeek on 2008-08-30
have you tried to restart ubuntu?
if that doesn't work, try
```

killall pulseaudio

```
in terminal and see if that resolves it

---

### Post by hyperhopper on 2008-08-30
killall pulseaudio worked


P.S. how do you learn all these commands?

---

### Post by hyperhopper on 2008-08-30
!!!!!whaoaoa
didnt you have less posts than me yesterday??????

---

### Post by gmxgeek on 2008-08-30
I browse the forums a lot, and pulseaudio was being a pain for me for a while, so i found out how to kill it dead.

And I basically spent most of last night on the forums. (Coudn't sleep, and problems just kept coming in :P)

---

### Post by hyperhopper on 2008-08-30
but how do you know all the answers????

---

### Post by gmxgeek on 2008-08-30
I spend quite a bit of time just messing around with linux, and browsing through man pages and forums. Currently i run ibex, and get some crashes about once a week, so i have gotten pretty used to repairing things in this manner. Many of these errors i have gotten myself and have fixed through trial and error, or forum browsing, and most of the problems have similar processes to find out what is wrong.

Basically, if you use your system enough, you get very familiar with what it should be doing, and how to tell what exactly is wrong. From there, its a lot easier to fix it

Practice makes perfect!

---

### Post by hyperhopper on 2008-08-30
Thanks! and I guess that ends the thread...

---

### Post by billgoldberg on 2008-08-30
Switch from PulseAudio to ALSA.

I haven't had any sound problems ever since I did that.

---

### Post by Nepherte on 2008-08-30
I always recommend people to fix pulseaudio. Pulseaudio is a great thing, once it is fixed.

---

### Post by gmxgeek on 2008-08-30
I  have never needed it myself, as everything i do works perfectly fine without it.

---

### Post by linuxguymarshall on 2008-08-30
Can someone fix this! There are more posts each and everyday about "My audio is not working" This happened this morning to me. Luckily its not the really hard to fix it it is annoying as hell when I just want to listen to Amarok

---

