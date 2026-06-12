---
title: "Compiz help please!"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by niko123 on 2008-07-05
Hello Everyone,

I am writing because i need help re-enabling my custom effects.
VIA-System>appearance> "visual effects tab">custom

It was working AWESOME!!! Last week, and i had it working for years...but all of a sudden when i turn on my computer...all my effects that used to be on compiz is now gone, and when i try to re-enable the  "custom" effects it give me the error..
```
 desktop effects could not be enable 
```

Extra info:

niko@laptop:~$ lspci |grep VGA

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Please help...I know it works, i just dont know what happen.

---

### Post by Troll_the_Great on 2008-07-05
Try disabling and then re enable the video card. It might work.

---

### Post by alienexplorers on 2008-07-05
Have you tried rebooting the system and then trying to reselect compiz.  On my system I have to select it two or three times before it takes.

---

### Post by niko123 on 2008-07-05
Hello,

I have tried both your methods, and it still doest work..

---

### Post by alienexplorers on 2008-07-05
Do you have the proper video drivers for your card installed?

---

### Post by tjwoosta on 2008-07-05
i have this same video card

mine works without any setup at all with Hardy (no installing drivers or anything)

but with Gutsy i had to make compiz skip the blacklist check
(because this card is blacklisted, but it does work)

more info
[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

---

### Post by PatrickMoore on 2008-07-05
run this in your terminal and post your results please.

```
ps ax | grep xcompmgr

```

---

### Post by niko123 on 2008-07-05
Hello, and thank you for the replys...

Yes, i have doubled checked my drivers and i have the correct drivers.


I See that there is a little part that tells you that you can "ignore the black list" Where is it that i would look to input that information...


And for the command:

```
 ps ax | grep x compmgr 
```

I get teh following out put
```

niko@laptop:~$ ps ax | grep xcompmgr
 6364 pts/0    R+     0:00 grep xcompmgr

```

Thank you guys for helping me!!

---

### Post by niko123 on 2008-07-06
bump...help please

---

### Post by tjwoosta on 2008-07-06
what i did was add 

SKIP_CHECKS=yes

to ~/.config/compiz/compizconfig/config

```
gksudo gedit ~/.config/compiz/compizconfig/config
```

---

