---
title: "Really strange behavior while booting"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by ceciliasp on 2013-12-13
My computer have dual boot, Windows 8 (pre-installed) and Ubuntu 12.04
On a random basis, I can't boot to Ubuntu. I get to see the GRUB screen with all the booting options but sometimes, after the countdown (or after pressing enter when the countdown does not appear) the screen stays dark and nothing happens. After rebooting or running the live usb and rebooting again I can boot into Ubuntu. I don't know if the following has anything to do with this but a few days ago I configured the hybrid suspend option to be able to hibernate. The script shows like this:
```
# Always use suspend_hybrid instead of suspend
if [ "$METHOD" = "suspend_hybrid" ]; then
METHOD=suspend
fi
PM_HIBERNATE_DELAY=300  # time in seconds until hibernate (suspend to disk) occurs; 900 means 15 minutes"
```
I really can't tell if both things are related or not, but I think that this configuration might have caused some damage to my booting system. Can anybody point me in what direction I should start looking for a solution?
Thanks Cecilia

---

### Post by PaulBx on 2013-12-14
My machine stops with a black screen on every boot. If I use the keyboard to boost the screen intensity I can see it sitting, waiting for a password (my drive is encrypted). It's possible yours just needs the intensity cranked up. I just live with it now, it's only a minor annoyance now that I know what is happening.

---

### Post by ceciliasp on 2013-12-14
Thanks PaulBx for the answer, but I don't thinks that's the problem since the failure is random... sometimes it will boot and sometimes will not.
I'll keep looking...
Thanks anyway

---

### Post by col48 on 2013-12-14
Not really an answer, more an observation: the random nature of the problem could be a matter of timing, ie it could be a problem which only occurs when a race between two contemporaneous processes turns out one way rather than another. Sometimes when I boot up after choosing between the Ubuntu versions available to me the GUI login screen does not appear (the subject of another thread) and often when I login the screen takes a moment or two to resolve into something sensible. In the former case, when the GUI does not appear, the screen shows a whole-screen Terminal which I can login with.

So it could be that PaulBx has offered a clue after all.

---

### Post by ceciliasp on 2013-12-14
Well... trying to fix the  problem I ended up screwing my whole system and not booting at all.
Here's my boot repair log [http://paste.ubuntu.com/6574355](http://paste.ubuntu.com/6574355)

Thanks!

---

