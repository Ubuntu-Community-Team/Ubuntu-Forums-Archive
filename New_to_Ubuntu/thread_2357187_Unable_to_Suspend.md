---
title: "Unable to Suspend"
date: 2017-03-30
forum: New to Ubuntu
---

### Post by Hasimir on 2017-03-30
Hi :)
So I'm running Ubuntu 16.04 LTS on an Asus Zenbook UX310UQK ... and am unable to Suspend.
When closing the lid or clicking the sleep button, on re-awake the screen stays black (but lighted up) and the only way to access the computer again is to long press the Power button to shut down, and then reboot.
I read that this is a common (?) problem, with some procedures to "debug" that at a first glance look more like a diagnostic than an actual fix.
(PS: I've used linux before, but I consider myself pretty n00b)

Is there something I can do to actually get the Suspend (or even the Hybernate!) function to work?
Someone said it might depend on the current kernel not supportin the hardware ... is the problem solved in Ubuntu 16.10 or 17?
Can I update the kernel without reinstalling the whole system?

Thanks a lot for the help! :D

---

### Post by Futant on 2017-04-02
Hi, welcome to the forums! It is indeed [possible]("https://wiki.ubuntu.com/Kernel/MainlineBuilds") t[FONT=Verdana]o install other kernels to see if they work better with your system. Good luck![/FONT]

---

### Post by Hasimir on 2017-04-03
I've upgraded the kernel to v4.10.8 but still no joy.
I'll now experiment with the latest v4.11 RC hoping for the best ¢_¢

YESSSSS!
Kernel v4.11.0rc5 did the trick :D

I used "Ukuu" to help me do everything neatly.

---

### Post by blackcommand on 2017-04-03
Have you had a look at this article at "Ask Ubuntu" [http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line](http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line)

---

### Post by Hasimir on 2017-04-03
Nope, not that thread. But I found the same command from another article.
Hybernate kind of worked, but on resume the system was full of glithces.
But I was just interested in the Suspend function anyway ;)

---

