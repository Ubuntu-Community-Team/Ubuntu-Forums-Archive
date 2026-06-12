---
title: "Low graphics mode after user switch"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by satjat on 2008-07-18
Sometimes my 8.04 system boots up in low graphics mode.
At first I thought it was random but it only seems to happen when I have used the fast user switch panel. It works perfectly to switch users but on the next reboot the resolution is low and the nvidia drivers not in use. I have a backup of my xorg.conf but replacing it doesn't work... Using EnvyNG fixes the problem until next time I switch users. If, instead of using the panel,I logoff or restart X with ctrl-alt-bcksp and login as another user there is no problem.
Is something not installed correctly?

---

### Post by cprofitt on 2008-07-21
Try ensuring that the video cable is firmly attached... while doing that check to see if there are any bent pins. I recently had a problem with that and it was a loose cable.

---

### Post by satjat on 2008-07-22
Although I do not understand how this can be possible it seems like it is happening only when the monitor is connected through DVI.
Following your advice I switched cables to make sure and since it worked as it should with the d-sub cable I got suspicious.
I tried 3 different monitors with more than 10 cables and the result is the same. All d-sub cables work but all the DVI cables have problems. Not always the same, repeatable problem, but problems with resolution mostly after user switching.
Is there any way the connector on the card (nvidia 6200) is not sending some kind of "monitor present" signal?
The other thing is that the 3 monitors I used where the same model (LG 22wtq, if I remember correctly) so it might be some incompatibility with the specific monitor. I will try and test this up with some other monitor.
Is there any change to the driver if I want to use the DVI connector? I thought the card managed those things "on board" but it looks like it's not.
Thank you

---

