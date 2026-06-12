---
title: "ubuntu 804 wont boot"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by mustava on 2008-06-27
Guys, please help, I have installed 804, fine, installed all the updates, fine, installed virtualbox, fine, installed winxp in virtualbox, again fine. reboot machine, and no problems, even installed dreamweaver on xp and still ok.

Now heres the prob, I have done the abive twice now, because when I power down at night after doing all of the above, when I come to switch on the next day, the os wont boot, i get the grub ok, and a bit of test in top left corner saying Starting up... then theres a lot of disk activity for a number of minutes but the screen stays black, not even a cursor.

Help plse
Mustava...

---

### Post by bumanie on 2008-06-27
ctrl-alt-F7 should start x and get you into the gui. Can't tell you why it is happening though. Someone else may know.

---

### Post by mustava on 2008-06-27
Thanks for that, but it musn't be getting that far, as it does nothing.

Mustava....

---

### Post by sydbat on 2008-06-27
Maybe boot through recovery mode? Choose option to fix whatever may be broken, then continue boot...see if that works.

---

### Post by mustava on 2008-06-27
Ok thanks, but where do i find recovery mode?
thought it may be on the ubuntu disk, but i cant see it.
Mustava...

---

### Post by saidinesh5 on 2008-06-27
recovery mode is whn you boot into the us...its shown during the grub is on its work

---

### Post by maestrobwh1 on 2008-06-27
It is usually the second grub line (recovery console).  If it hangs, you'll have to try to boot from the install CD and problem solve from there.  The kernel is hanging on something.

Also, depending on how long you have had Ubuntu, you might have more than one kernel to boot from in Grub.  Try another one if you do.

---

### Post by mustava on 2008-06-27
Thanks guys, done as suggested, and lo and behold, i'm using my ubuntu again. Just for the record, this has happened two nights running, following a power up the next day...spooky.
Mustava.

---

### Post by sydbat on 2008-06-27
Maybe you shouldn't turn your computer off...

---

### Post by mustava on 2008-06-27
Hi guys, I'm back. I appear to now be in a loop. after each powerdown, on power up the syatem hangs as before, so I have to use recovery every time now, on my forth at mo'. I did notice however that on shutdown, something about invalid hash something is displayed only for a moment then it shuts down, but its not on long enought for me to see.
Mustava...

---

### Post by mustava on 2008-06-29
Hi Guys and gals,
ok, still having probs with cold boot. My system will NOT boot without selecting recovery console i grub, and then selecting repair broken packages.

Now to try and fix this, on the next boot I did the above and when complete I chose the option try to fix x server. 
Since then my system wouldn't boot at all.

So on next boot I tried the fix broken packages and same on next boot, now it will boot but only when the recover console is selected.

Can anyone help please



Thanks Mustava...

---

### Post by mustava on 2008-06-30
Hi PPL,
Still trying to sort out, have now discovered that if i choose recovery console from the grub, and when asked to choose method, I just select normal boot everything works ok. But why do i have to use recovery console to boot?

Help please!!!

Mustava...

---

