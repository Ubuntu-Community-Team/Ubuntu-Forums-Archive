---
title: "During Boot: Unable to Access Ubuntu"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by Sky001 on 2014-12-29
Hello everyone, 

A few months a go i installed the latest long term support version of Ubuntu as a dual boot on my hard disk drive. it worked all right, but I never managed to get Windows to boot properly. My windows 7 installation would almost always boot into start up repair. So eventually I downgraded and reinstalled windows vista which was the original operating system. 

Now, after starting up my pc, I'm unable to get the list of installed operating systems on my hard disk drive. The laptop always boots straight into Windows Vista. So my query is, can anyone help me get back the list of installed operating system without having my Vista installation freak out? 

Thanks in advance. 

p.s. Apologies if this is the wrong forum section. This place is huge.

---

### Post by grahammechanical on 2014-12-29
By re-installing Windows the Ubuntu boot loader (Grub) was over-written by the Windows boot loader, which does not recognise the existence of any operating system other than a Microsoft OS. You need Boot Repair. Accepting the recommended repair may fix it. Boot Repair also produces a report which it stores at the Pastebin site. Make a note of the URL to the location of your report. Then if the fix does not work, post the URL here and we can see it for ourselves and give more accurate advice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by Sky001 on 2014-12-29
Thank you for the super fast reply. I'm working on it right now. I'll post the results.

---

### Post by Sky001 on 2014-12-29
Thanks again. My problem is fixed. It was pretty easy from start to finish. I really appreciate the help. :D

---

