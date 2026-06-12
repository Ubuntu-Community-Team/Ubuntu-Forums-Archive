---
title: "Dual Boot System With automatic Disk check goes to BSOD"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Herber on 2008-09-28
I have installed a Dual boot setup on a Dell 8200 Desktop.  Both OS's (windows XP and Ubuntu 8.4) work great, but when I bood to the windows partition the system wants to do a Disk Check prior to opening.  If I allow the check the system goes to a blue screen of death.  If I prevent it by pressing any key, the system boots normally and is fine.  I would like to somehow prevent the Disk Check.

-----
Dual boot single drive Windows XP/Ubuntu 8.4, 1Gb Ram, P4, 2.4Ghz

---

### Post by PocketDog on 2008-09-28
Ah, I miss those serene blue screens. Try the instructions here to disable chkdsk on startup [http://xphelpandsupport.mvps.org/how_do_i_prevent_chkdsk_from_run.htm](http://xphelpandsupport.mvps.org/how_do_i_prevent_chkdsk_from_run.htm)

---

### Post by Herber on 2008-09-28
Thanks, that fixed the problem.

---

