---
title: "Since update 23.04 can't wake up after a long suspend"
date: 2023-05-06
forum: New to Ubuntu
---

### Post by sash5 on 2023-05-06
I did an update to 23.04, and now i see a very strange behavior. If my PC goes to sleep, mouse is switched off, there is no light. Light on power button on the PC case is blinking, all other lights are switched off. If i press a key, PC wakes up normally. 
But if i wait for a long time, maybe an hour,  i seen that the mouse is on, PC case lights are on, and it looks like PC is not suspend any mode, but keyboard if off, caps lock not working, and if i press any button, it doesn't wake up and i have to restart.

---

### Post by jmarc3 on 2023-05-06
I see exactly the same on a HP Pavilion 27 i7 7700T + radeon R7 M460. I do not know where to start from there.

---

### Post by zebra2 on 2023-05-09
you can try 
sudo systemctl mask hibernate.target hybrid-sleep.target

reboot
You can check this result with systemctl status hibernate.target hybrid-sleep.target

most likely it isn't waking from hibernate.  
note: do not mask "sleep.target"

---

### Post by sash5 on 2023-05-21
Everything is disabled, but the problem is still appears

sudo systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target


&#9675; sleep.target - Sleep
     Loaded: loaded (/lib/systemd/system/sleep.target; static)
     Active: inactive (dead)
       Docs: man:systemd.special(7)

&#9675; suspend.target - Suspend
     Loaded: loaded (/lib/systemd/system/suspend.target; static)
     Active: inactive (dead)
       Docs: man:systemd.special(7)

&#9675; hibernate.target - System Hibernation
     Loaded: loaded (/lib/systemd/system/hibernate.target; static)
     Active: inactive (dead)
       Docs: man:systemd.special(7)

&#9675; hybrid-sleep.target - Hybrid Suspend+Hibernate
     Loaded: loaded (/lib/systemd/system/hybrid-sleep.target; static)
     Active: inactive (dead)
       Docs: man:systemd.special(7)

---

