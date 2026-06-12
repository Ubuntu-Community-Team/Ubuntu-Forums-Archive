---
title: "Ubuntu not reading DVD-R disc"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by MrMoose9000 on 2008-05-20
I bought a 15$ pack of burnable DVD's, which i could put the ISO onto. The brand is Maxwell, if that helps.

Is there something i need to install before the computer can read the disc, because when i insert it, it doesn't even show me that the disc is even in the drive.

I've searched and found simaller threads, yet with no actual answers. So i figure I'll try my luck'

Also, I used the command sudo cdrecord -scanbus in the terminal, and my result is
scsibus1:
	1,0,0	100) 'HL-DT-ST' 'CD-RW GCE-8481B ' 'C102' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
scsibus2:
	2,0,0	200) *
	2,1,0	201) *
	2,2,0	202) *
	2,3,0	203) *
	2,4,0	204) *
	2,5,0	205) *
	2,6,0	206) *
	2,7,0	207) *

.. if that helps anybody

---

### Post by robalcorn on 2008-05-20
Looks like a cd-rw drive not dvd?

---

### Post by MrMoose9000 on 2008-05-20
> **robalcorn said:**
> Looks like a cd-rw drive not dvd?

I figured that was the problem. I feel kind of stupid now that i realize how obvious the problem was. Thanks anyway.

---

