---
title: "[SOLVED] problem with sound"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by xmunk on 2008-05-24
I'm having a problem running games like wow (in wine) ragnum, alien arena etc.  the games run fine but i have absolutely no sound.  I get sound in everything else except games. 

im using hardy and would post whatever config file but i have no clue where to start.

any help would be apreciated

---

### Post by sayakb on 2008-05-24
Just give it a shot.. install these two packages:
```
sudo apt-get install linux-backport-modules ubuntu-restricted-extras
```

---

### Post by robalcorn on 2008-05-24
> **xmunk said:**
> I'm having a problem running games like wow (in wine) ragnum, alien arena etc.  the games run fine but i have absolutely no sound.  I get sound in everything else except games. 

im using hardy and would post whatever config file but i have no clue where to start.

any help would be apreciated

Go to Applications/Wine/Config wine than go to audio and you wil get different options to select like Alsa or Oss try one use the test sound to see what happens.

---

### Post by MaindotC on 2008-05-24
Also try using:
```

winecfg

```
and selecting the "Audio" tab.  Make sure it selects a driver for you and click "Apply".  If that doesn't work, try selecting different sound drivers in winecfg and restarting your wine'd program each time.

---

### Post by xmunk on 2008-05-24
tried winecfg did alsa oss and jack still no sound.

i followed a tutorial a while back [http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739") and ever since then my sound hasn't worked in games just never got around to fixing it


thank you for the quick reply's

---

### Post by MaindotC on 2008-05-24
Do you have anything else running that requires sound? I have this problem with Teamspeak where it seems to take over control of the sound card and if I use any other applications I get no sound from them.

---

### Post by xmunk on 2008-05-24
nope nothing else running accept firefox.  but even without firefox i still get nothing

---

### Post by MaindotC on 2008-05-24
Ok I'm going to ask a couple more "baby" questions so forgive me if they're obvious.  Did you go to System -> Preferences -> Sound and select the different sound drivers available in the drop-down menus?  I'm not sure if you have to reboot each time you select a different driver.

Edit: Actually i tried it myself in my own sound menu.  Each time you select a different driver you can select "Test" and see if you have sound.

---

### Post by robalcorn on 2008-05-24
I checked out the link you posted and it mentions there is problems with wine. What about undoing what was suggested.

---

### Post by MaindotC on 2008-05-24
Dude, there are always problems with wine - or the installation on which wine is running or the way wine was installed or the hardware that wine needs to interact with.  Sure you can undo it, but that doesn't solve the problem.

In winecfg can you try selecting different options in Audio such as Hardware Acceleration, Sampling rate, and driver emulation?  This may take you a while.  Do yourself a favour - each time you make a different selection, paste in a notepad what you selected.  This way you go through all possible options and don't re-do any of them.  Combine this with the different options in System -> Preferences -> Sound.

Sorry, I know that's a lot of work but millions of other wine users are playing games so you should be able to joine them :)

---

### Post by xmunk on 2008-05-24
ok changing "sound events" back to alsa as opposed to pulse works for all games.  ;)

so the problem must be pulse.  I know about the wine problem.  i'm wondering what would make sound in native linux games die by using pulse?

---

### Post by MaindotC on 2008-05-24
Congratulations!  I knew you could get it working :)  Star me!  I haven't researched Hardy very much - installed it and had a lot of problems so I'm sticking w/ Gutsy per my sig - but I read someone mention on a different forum on which I posted to Pulse was rolled out w/ Hardy.  I'll verify this information when I get around to it, but at least you found the driver that works for you.

---

