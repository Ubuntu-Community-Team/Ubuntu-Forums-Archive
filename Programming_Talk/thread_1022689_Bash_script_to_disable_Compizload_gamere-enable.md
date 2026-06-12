---
title: "Bash script to disable Compiz/load game/re-enable"
date: 2008-12-27
forum: Programming Talk
---

### Post by Maveric3477 on 2008-12-27
Hi, I'm a terribly lazy person at heart, and I really dislike having to disable compiz so I can play Urban Terror, and then re-enabling it when I've finished =]. I like my desktop effects too much to get rid of them, and playing with Compiz enabled doesn't work out, so I thought I'd make a script. 

```
#!/bin/bash
metacity --replace &
/home/maveric/Desktop/UrbanTerror/ioUrbanTerror.i386
compiz --replace 
exit
```

Which works.. but doesn't. It stops compiz, loads Urban Terror and when I close Urban Terror it starts compiz.

It's all good until I open up my system monitor and see 10 (or so) compiz's in the process list. That didn't worry me, they were 100kb or so. However, I scrolled down and saw another 10+ compiz.real which are using ~20mb or memory. Not really what I want :P

So, any ideas how I can modify that code so it doesn't create multiple instances of compiz and compiz.real? Perhaps what I need to google?

If it's not going to be something easy, I'll just put up with the extra few mouse clicks, but I'm more interested in solving the problem now over the laziness part :P

---

### Post by Maveric3477 on 2008-12-27
No one has any ideas how I can get it to re-use the same compiz as before, rather than starting a new one?

---

### Post by Ahadiel on 2008-12-28
A very "hackish" way to do it would be to pkill metacity before starting compiz, and vice versa.

---

