---
title: "Ibex installs but then upon login it reverts back to splash screen??"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-11-01
I installed Ibex, everything seemed to work fine... but then it goes to the login screen, I type my username and pass and it seems to begin to login (despite that the top bar seems to have the same theme from 8.04), but then it goes back to the login screen. Help someone?

---

### Post by Watchtow3r on 2008-11-01
am i really the only person with this problem?

---

### Post by jonofan on 2008-11-01
I have not experienced the same problem, but my status bar is the same as 8.04.

Try logging on with a different session. From the login screen choose Options > Failsafe GNOME or Terminal.

---

### Post by diablo75 on 2008-11-01
It might have something to do with Compiz (or the hardware drivers for your video card), so hopefully the failsafe option mentioned above will help get you logged in.  If you do get logged in, I would check System>Administration>Hardware Drivers first to see if anything needs to be enabled.

---

### Post by Watchtow3r on 2008-11-03
I tried the failsafe and I couldn't login. The most it did was that sometimes it logged me in long enough for me to click on the guest account, and it logs in there and stays there without logging out. However, I can't access internet on the guest account, and I'm pretty sure I wouldn't be able to change hardware driver settings, or at least not for my main account. Any other help? I don't know any terminal commands so I can't really login that way.

---

### Post by Watchtow3r on 2008-11-03
Ok I got logged in by going to the shell prompt and typing 

sudo apt-get remove compiz
sudo apt-get remove compiz-core

But now how can I re-enable compiz? I click on System>Prefs>Appearance then click on the Visual Effects tab, but it won't let me use the normal or the extra effects. Do I have to reinstall Compiz? And if so will I have the same problem as before?

---

### Post by Watchtow3r on 2008-11-03
> **diablo75 said:**
> It might have something to do with Compiz (or the hardware drivers for your video card), so hopefully the failsafe option mentioned above will help get you logged in.  If you do get logged in, I would check System>Administration>Hardware Drivers first to see if anything needs to be enabled.

Also I went to that and I didn't see any drivers listed. So I guess I need to download the drivers again? BTW I have an Intel 945GM graphics chip.

---

