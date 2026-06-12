---
title: "atheros drivers didn't make the move"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by brodiesel on 2008-11-05
so, i posted this before, but in a confusing way. i'll try to be clearer here.

the install to intrepid went well, except for one thing; my atheros drivers didnt make the move from hardy. i have an icon telling me i am not connected, and when i go to "restricted drivers" it only lists a graphics card. Oddly, when i run hardy off the live disc ( as i have to) it automatically connects to my network and all the drivers are preinstalled.

so how do i get these drivers without getting online?

---

### Post by brodiesel on 2008-11-05
anybody? suggestions? know of a good wall i can bang my head against?

---

### Post by brodiesel on 2008-11-06
hey e'erbody, just wanted to update the conversation, as i know how many of you are waiting with baited breath tosee how it turns out...

[http://ubuntuforums.org/showthread.php?t=972691]("http://ubuntuforums.org/showthread.php?t=972691")

---

### Post by igknighted on 2008-11-06
Ubuntu 8.10 is using new atheros drivers (more FOSS friendly).  Instead of the old madwifi drivers, the new one is called ath5k or ath9k, depending on your card.

The catch is that it is not enabled by default.  Try this to see if it works: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by brodiesel on 2008-11-06
thanks igknightd, that is illuminating. it still doesnt answer two of my more important questions, like why it works fine on the live disc, and how it is that i can download that package without an internet connection.

what i am currently trying to do is find a way to download something while running in live mode that can be found once i start the install version, but i'm not sure if thats possible.

the other piece of information is that when i look at the list of hardware drivers in the install version, there is no option for the madwifi or atheros, and instead there is one driver labeled as a genereic "software modem" and in the description it says "your modem will not work if this is not enabled." of course to enable it you NEED AN INTERNET CONNECTION. 

double you tee eff?

---

