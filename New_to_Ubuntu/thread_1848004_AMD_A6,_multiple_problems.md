---
title: "AMD A6, multiple problems"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Esot-Eric on 2011-09-21
Hey chaps, I've got a HP Pavilion dv6-6104ea here and it's been causing me a bit of grief. It's working pretty much alright now but I've had to disable the proprietary drivers for the AMD Radeon HD 6490M meaning I can't have unity (though I prefer the classic w/o effects anyway). If I put the drivers on I run into a bunch of weird problems, unity works but if I use Cheese the video capturing me acts all odd, it seems to have priority over everything else, for instance if I were to pull up the system monitor and locate it over the video the video would be seen rather than the system monitor. Other problems include a black screen on shut down sometimes which has white text and I'm afraid goes away a bit too quickly for me read, I saw multiple references to 'terminate' though, any users other than the initial one don't show on the login screen until I login as the initial one and log back out and trying to use switch user makes the screen go black with the mouse visible while the screen that usually plays when brought to the login screen plays. I must say it's all a bit of a bother, but fortunately I'm in no rush to fix it and I can always go back to Windows 7 if it's not solvable.

---

### Post by LowSky on 2011-09-21
the splash screen problem will ot go away. its an issue with Plymouth not accepting proprietary drivers. As long as the machine boots and turns off, what is the point of a purple screen with a few colored dots.

The Radeon chipset used by the A6 is very new. so you may need the newer driver than the one supplied by Ubuntu. Use the version from AMD's website or try to find a PPA that supports the AMD chipset.

---

### Post by Esot-Eric on 2011-09-23
Right oh, thanks. I think I'll just keep the card disabled until the clever chaps catch up and make the normal drivers work for this one. How long do you think that will take roughly? I understand the card needs to be working in order to access the higher quality audio, I'm more interested in that working. Annoyingly Ubuntu is a bit too much fun to leave just due to some driver problems so I shall just have to wait.

---

