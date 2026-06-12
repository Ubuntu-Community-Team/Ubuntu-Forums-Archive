---
title: "System program problem alert"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Primus1 on 2012-12-09
Hi, I have been getting these alerts recently (screen cap attached). Think it started when Firefox started to hang usually when three or more tabs were open. They only way to switch the machine off was to press the power and hold it as nothing else responded. I don't know if the two are linked.

---

### Post by Frogs Hair on 2012-12-09
I am not an a Firefox computer at the moment but, you may want to check under Edit  > Preferences > Advanced > General and disable hardware acceleration and see if there is a difference.

---

### Post by Primus1 on 2012-12-09
I've unchecked hardware acceleration. That would cause these worrying system problems you think?
the alerts in my attachment popped up as soon as I booted today, when Firefox wasn't running.
Thanks for the reply.

---

### Post by mlentink on 2012-12-09
When it happens again, please click on the button to show details, and let apport do its search (may take a while). Then you can see in which program the error occurs. The second screenshot indicates that it does indeed have something to do with your graphics card and/or hardware acceration.

---

### Post by Primus1 on 2012-12-09
> **mlentink said:**
> When it happens again, please click on the button to show details, and let apport do its search (may take a while). Then you can see in which program the error occurs. The second screenshot indicates that it does indeed have something to do with your graphics card and/or hardware acceration.

Ah, there is a bit of Apport info in one of the images i posted:

"Aport has detected a possible GPU hang. Did your system recently lock up and/or require a hard boot?"

Then:

/usr/share/apport-gpu-error-intel.py

I thought it said CPU but you are right it's GPU. I think this machine has 'onboard' graphics, so not a separate graphics card.

---

### Post by Primus1 on 2012-12-10
It happened again today. I've attached the full Aport report, sorry about the format it wouldn't let me copy and paste so I had to take 4 screen caps to get it all in

---

