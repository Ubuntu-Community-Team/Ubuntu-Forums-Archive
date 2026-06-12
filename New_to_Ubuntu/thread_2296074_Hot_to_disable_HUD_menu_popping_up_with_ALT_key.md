---
title: "Hot to disable HUD menu popping up with ALT key"
date: 2015-09-23
forum: New to Ubuntu
---

### Post by solidblue on 2015-09-23
I'm having a problem with the HUD menu popping up whenever I press the ALT key. 

I've already disabled it in the keyboard shortcut settings, "Key to show the HUD" there is showing as disabled. However it still pops up every time I press ALT.

I also installed CompizConfig Settings Manager, in the Ubuntu Unity Plugin settings there it shows "Key to show the HUD when tapped" as disabled, yet it's still popping up with ALT.

uname -a gives Linux ubuntu 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Anything else obvious I'm missing here? I'm using Ubuntu via VMware Fusion on OSX but I don't think that would cause any menu setting issues (correct me if I'm wrong).

---

### Post by kryten35 on 2015-09-23
Disabling works for me on ubuntu 15.04

Does changing it to a different key work?

Its either a bug with yor version of ubuntu or your virtualisation program is causing it.
Dont really understand what the precise problem is though.Why keep tapping alt key if you dont want hud to appear?

---

### Post by solidblue on 2015-09-24
Changing to a different key makes the different key bring up just HUD search option, while ALT still brings up the full HUD menu (the same as clicking on the HUD icon).

The problem is that because I'm running it in VMware, I alt-tab to other windows in OSX, and whenever I alt-tab back to the Ubuntu window it'll register that alt and open the HUD automatically.

---

### Post by kryten35 on 2015-09-24
Ok i see.But i think your confusing the dash with the hud.

Super(hold)  opens the LAUNCHER bar on left hand side with shortcuts to applications
Super(tap) opens the DASHBOARD and defaults to the home LENS.The box at top is to "search your computer and online sources"
Alt(tap) opens the HUD  a single box where you can "type your command"
Alt(hold) opens the applications menu.

Alt +Tab  between windows  doesnt open the hud for me because you press and hold alt.
If i change "key to show the hud" to Ctrl R  then Ctrl R only  opens the HUD.Alt(tap) has no effect and alt(hold) opens app menu.

So everything is working as it should for me.It looks as if there is a conlict between VMware and your ubuntu install.
I dont think theres going to be an easy answer.An update to either VMware or more recent version of linux might solve it.

---

### Post by solidblue on 2015-09-25
Yes you are correct, it's the dashboard that ALT is opening, not the HUD. Disabling the shortcut for the dashboard solved my problem, thanks.

---

