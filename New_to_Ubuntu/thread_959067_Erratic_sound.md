---
title: "Erratic sound"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Maximusmaximus on 2008-10-26
I have been using Ubuntu for around a month now. withing this period i have been getting wildly erratic sound problems. to the point where the computer will crash. this makes it particuarally hard as i have alot to do with music etc and refuse to go back to windows. 

i have also been having problems with audacity. The recording glitches and cuts out lags etc. 

i don't have a proper sound card (i use the inbuilt sound hardware with the motherboard) which leaves me to believe that the problem is there. i also do not want to have to buy a new sound card if it is a software issue.

---

### Post by alienexplorers on 2008-10-29
Are you using pulse audio, if so there are some problems with it.  Try looking here [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by gorgon on 2008-10-29
Hi there,

A bit more info on when the glitches happen, when they don't happen, what soundcard you got, would be helpful to figure out your problem.

to find your audiocard type this in a teminal:
```

lspci

```
and scroll up to find 'Audio device'

If you record a lot Id recommend you to install the Ubuntu Studio packages. It has a 'real-time kernel' which is ideal for recording and working with sound. If the problem persists, try using Jack (comes in ubuntu studio) with different configurations (most importantly try different sizes for frames and buffers).

Hope that helps!

---

