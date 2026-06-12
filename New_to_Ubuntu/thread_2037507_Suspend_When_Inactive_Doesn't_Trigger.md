---
title: "Suspend When Inactive Doesn't Trigger"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by DGINSD on 2012-08-04
Suspend works fine and hibernate works fine but setting suspend when inactive won't trigger the suspend action. I'm assuming something is telling the system there's still activity since both suspend and hibernate work fine when triggered from the drop down or command line.

So what kind of events keep the machine in an active state, and how can I monitor whats causing mine to not suspend?

Google search, of which I'll admit not being that great at, produced some advice of checking out gconf-editor  apps>gnome-power-manager>actions which no longer exists in 12.04 however in Dconf-editor org>settings-daemon>power looks like where all those settings went, and the keys seem to change with changes to the gui in the settings manager.

So How do I go about trouble shooting this issue?

---

### Post by DGINSD on 2012-08-05
So I did a bit of experimentation this morning to see if I couldn't narrow down the issue. I started by doing a secondary install to make sure this feature even works on my machine, which it did, but I did learn this. If you have the "turn screen off when inactive", under, "brightness and lock", set to never, this seems to keep suspend when inactive from working. This was true on a totally unmodified fresh install. But when both were set to five minutes (or I'm sure whatever) it worked fine.

So I then tried disabling things to see whats causing my machine to keep from auto suspending, I tried not running my Conky and also disabled a back-light script that I use, this changed nothing. I shut down networking, this also did nothing.

So now I'm back to square one, the only thing I can think is the FGLRX driver may be causing some issue keeping the systen in an active state. 

Incidentally on the secondary test install, I didn't install the proprietary FGLRX driver. Whats odd is after the auto suspend on this test install, resuming resulted in a hung system. I've had similar random hangs before on my main install, that I thought was due to the FGLRX driver, but now I'm thinking otherwise. How to fix or even get more info regarding this is beyond me, just thought it interesting, this was the first time I experienced any type of hang without FGLRX loaded.

---

### Post by Hadaka on 2012-08-05
Have you checked ..System Settings ..> Power &&  Brightness and Lock?

the power settings effect the brightness and lock per a note under power.
good luck

---

### Post by DGINSD on 2012-08-05
> **Hadaka said:**
> Have you checked ..System Settings ..> Power &&  Brightness and Lock?

the power settings effect the brightness and lock per a note under power.
good luck

I've actually considered that after a while that lock may be involved so I activated to see. The screen blanking takes place but no where near the time I have set and about 30 seconds after that something else takes place, but what ever it is freezes the system and I must sysrq R S E I N U B to restart. All this has thrown me for quite a loop because as I stated in my OP both suspend and hibernate work flawlessly from the top right corner button drop down or command line.

Whats also odd that i noticed is sometimes changing settings won't actually change behavior, and settings need to be changed two or three times before they take effect?

---

