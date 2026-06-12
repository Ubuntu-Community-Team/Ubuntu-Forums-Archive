---
title: "Lubuntu 16.04 on Dell Inspiron 1525, frequent crashes after screen off or suspension"
date: 2017-04-26
forum: New to Ubuntu
---

### Post by jameswd2 on 2017-04-26
I recently installed Lubuntu 16.04 LTS on an older Dell Inspiron 1525 given to me by a relative. For the the most part the setup is working quite well, but I am experiencing frequent system crashes.

The same error messages seem to be displayed each time, so I believe the source of the crashes are the same. I have included photos of the error screen and a profile report for my system in the post attachments. The crashes seem to happen when my system attempts to turn the display back on after the screen powers off due to power settings or when attempting to return from being suspended. The only well to get everything working again seems to be shutting down the system with the power button and then rebooting. I'm trying to use this computer at work, and the reboots are becoming a nuisance. 

What could be the cause of the crashes? Is it related to the hardware I'm using? Could anyone help me understand the error messages I'm seeing? 

I'm still fairly new to using GNU/Linux, so any advice or guidance would be greatly appreciated!

---

### Post by lammert-nijhof on 2017-04-29
I'm using the same Intel graphics chip in an Inspiron 1521 with Ubuntu 16.04 and have no issue. I see however a strange thing in you output: 	 	 	
> 
Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz		: 2000.00MHz
Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz		: 1667.00MHz

Both processors should run at all times on the same frequency. It could be an accidental timing issue, but I have never seen it before. 
Did you change something with respect to CPU frequency? 

I have no glue about the error messages, but you could change your brightness/lock and power settings for the moment to avoid those crashes.

---

### Post by mörgæs on 2017-04-29
If you do a live boot of 17.04, can the system go into and out of powersave without problems?

---

### Post by jameswd2 on 2017-05-04
I'll try that and see what happens. I had 16.10 installed on this PC before and I suffered the crashes then too. Thanks for the reply.

I haven't made any changes in how the processors function, at least none that I am aware of.

I made some changes using the Xfce power manager like you suggested. I'll see if that helps alleviate the problem. Thanks!

---

