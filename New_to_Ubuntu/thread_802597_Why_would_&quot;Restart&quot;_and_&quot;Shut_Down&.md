---
title: "Why would &quot;Restart&quot; and &quot;Shut Down&quot; options disappear?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Donalb on 2008-05-21
Hey all, 
So I was playing around with some stuff (trying to install Rio Karma support) and failed. Then I moved on to trying again to enable desktop effects (not getting very far) when I tried calling up System>Preferences>Appearence, which failed to display (tried a few times). 

So that's what I was doing.

So I decided to do a reset, (no apps open)  but the Quit screen was missing both the Shut Down & Restart options. I had to do a hard power off to reset.



Any ideas, and should the problem reoccur, anything else I should try?


Regards
Donal
Ireland

---

### Post by nicedude on 2008-05-21
From what you say you were doing I have no idea what you did to cause this. That said in the future if you cannot access your shutdown/restart buttons you can use the command below to reboot by running it in a terminal window.

sudo reboot

That would be safer for your system than a hard power down.

---

### Post by Donalb on 2008-05-21
Thanks! Nice and simple.
Give me a year or two on Linux and I'll have some of these tricks in my head! 

Regards
Donal

---

### Post by leboea on 2008-05-21
go to **System>Administration>login** 'enter your password '   select **local tab** and under the Menu bar options select Show Actions Menu and close the window. Try to shut down again

Let me know if this works.

---

### Post by Donalb on 2008-05-23
Hey Leboea,
Sorry, but the problem was already solved because I had already done a hard reset. I was just curious about the cause/behaviour.
(BTW, those setting were already suggested).
What I did forget to mention in the original post was that the Terminal also wouldn't start, so sudo -reboot wouldn't have worked either.

Thanks anyway
Donal

---

### Post by BandD on 2008-05-23
This happens to me every once in a while as well.  I'm still not sure exactly what causes it.  But if it happens again you can try Ctrl+Alt+Backspace.  That will log you out and you can log back in again.

If that doesn't work, or the buttons are still missing when you log back in, then you can log out again (Ctrl+Alt+Backspace) and click the options button in the lower left by default at the login screen.  

Or you can press Ctrl+Alt+F5 (F1-F6 should work) which will take you to a virtual terminal (the screen willl go black and you should see a terminal window where you can type the sudo reboot command).  If this fails for whatever reason you can press Ctrl+Alt+F7, this should get you back to your desktop.

---

### Post by sagara on 2008-08-23
> **leboea said:**
> go to **System>Administration>login** 'enter your password '   select **local tab** and under the Menu bar options select Show Actions Menu and close the window. Try to shut down again

Let me know if this works.

leboea, I ended up with this same problem (not sure how) but your suggestion fixed the problem! thanks! :D

---

