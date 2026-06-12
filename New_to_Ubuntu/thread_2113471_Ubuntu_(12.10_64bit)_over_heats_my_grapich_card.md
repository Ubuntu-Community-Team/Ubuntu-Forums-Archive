---
title: "Ubuntu (12.10 64bit) over heats my grapich card"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by horagino12 on 2013-02-07
Hello i have a little problem i installed my ubuntu 3 days ago and when i was watching something on youtube by accident i touched my grapich card ( my open computer is on desk ) and it was really hot so i installed sensors to check the temp and it was 58c on idle i wasent doing nothing like playing bf3 or something 
my grapich card is asus hd 7870 dc2 v2 
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI PITCAIRN [Radeon HD 7800]
Subsystem: ASUSTeK Computer Inc. Device 0432
Kernel driver in use: radeon

a'm a bit noob at linux i just stared and i wish to start learning as soon as posible so please try to help me
and pls be more detail when trying to help so none of us get's angry when we cant understand each other
sorry for my english if i spelled something wrong

---

### Post by deadflowr on 2013-02-07
If the graphics card doesn't have a fan, then 58 degrees Celsius is reasonable.

Which begs the question, does the card have a fan?

You could try installing the proprietary drivers.

In the dash/menu type system settings, then go to software sources, then go to additional drivers and select a driver (most likely the first one) then click activate and enter your password, and let it install.

Follow this for better guidance:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by horagino12 on 2013-02-07
No no it has 2 fans and in windows the normal temp in idle is 34c + dc2 is really good cooling 
and btw about the other thing i gone check it in 1 minute but i probaly not gone get it becuase of my stupid english understanding ( writing is fine )

---

### Post by horagino12 on 2013-02-07
LIke i said i'm a noob and i dont know how to install the dirver
i downloaded fglrx-installer-9.0000 ( the updates because it had less bugs ) 
and i have folder 
arch etc lib usr xpic xpic_64a 
how do i begin installation?
and i  went into xpic_64a then to usr X11R6 LIB64 modules drivers and i found fglrx_drv.so so i tried to run it but it wont let me because it says it doesnt support it

---

### Post by verymadpip on 2013-02-08
Hello.
I recently installed a 7870 in my rig running 12.10 (64 bit).  I installed the drivers from the AMD website & my card runs at 21C at idle.

DO check deadflowr's link.

---

