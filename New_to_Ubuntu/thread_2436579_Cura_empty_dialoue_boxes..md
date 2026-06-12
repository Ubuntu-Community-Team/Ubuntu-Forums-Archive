---
title: "Cura empty dialoue boxes."
date: 2020-02-09
forum: New to Ubuntu
---

### Post by lemon-cluster on 2020-02-09
Hi,   I'm not a techy user, please forgive a user oriented question.  

My Ubuntu 18.04.4 (64bit) system has run a late version of Cura 3D slicing software for several weeks with no problems.  In the recent week (I guess following Ubuntu system updates), 
the Cura software now opens a window without any text or menu tabs.  The 3D frame is shown and it can be rotated and zoomed. Random clicking around the window can open a dialogue box, but that is always empty.    
I upgraded/reloaded the latest Cura version (4.4.1) which runs in exactly the same way.  I have rebooted the system and used an older Ubuntu/kernel version to no effect. 

Can anyone help me to resolve this issue? 

Regards,  Dave.

---

### Post by lemon-cluster on 2020-02-09
Trying a few different things:  I had dropped the executable file onto my desktop, where it has worked for a good while.   This is where I popped the new version that had empty dialogue boxes and no menu tabs.   
I moved it to a dedicated directory within my home (admin) directory.  From here it almost works, it seems whole except for the top right of the window which is blank.    The menu tabs have appeared and by clicking around, I can get the menu to open up on the right...  I can load a file and slice it, just can't see the top right-hand quarter of the window.....   Very odd.

---

### Post by wildmanne39 on 2020-02-09
Thread moved to New to Ubuntu sub-forum.

---

### Post by Impavidus on 2020-02-10
It sounds like it cannot find a GUI theme or some fonts. I'm not familiar with Cura, but I see it's availabe from the official Ubuntu repositories, yet you write that you dropped the executable onto your desktop. It's usually best to install software from the official repositories whenever you can. Sometimes the software in the official repositories is tweaked a bit to better cooperate with Ubuntu. The downside is that it gives you a slightly older version. Ubuntu 18.04 will give you Cura 3.1.

When you install it from the official repositories, does it work?
I also found this bug report: [https://bugs.launchpad.net/ubuntu/+source/cura/+bug/1827859](https://bugs.launchpad.net/ubuntu/+source/cura/+bug/1827859)

---

