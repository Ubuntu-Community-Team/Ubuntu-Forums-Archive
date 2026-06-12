---
title: "[SOLVED] Where would you throw scripts that you want to startup automatically?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by wardrich on 2008-10-28
I want to write a script. or append a line to a file that loads up when the system starts... Really, all I want is for the system to automatically "xset -b"... because I'm sick of getting my ears blasted with a loud BEEP when I hit backspace too many times.  lol.

---

### Post by billgoldberg on 2008-10-28
Well, the system beep can be disabled in system, preferences, sound.

But to answer your question:

system, preferences, sessions is where you would put your scripts you want started at boot.

---

### Post by Rinzwind on 2008-10-28
From memory:

> sudo gedit /etc/modprobe.d/blacklist
Append this line:> blacklist pcspkr

To kill the speaker this time: 
> sudo modprobe -r pcspkr

---

### Post by wardrich on 2008-10-28
Thanks guys!  I can't believe I missed that option there to turn it off... :\

---

### Post by Xiong Chiamiov on 2008-10-28
I learned today to add things to /etc/rc.local.

---

