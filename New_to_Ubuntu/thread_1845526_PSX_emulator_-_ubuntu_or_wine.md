---
title: "PSX emulator - ubuntu or wine ?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by blade4 on 2011-09-17
Hi everyone , this is more of a discussion question . Which is better : epsxe on linux or on wine ? I only wanna know cuz I've already got epsxe prepped up on my windows partition and don't really want to go through the grief of collecting all the components for the linux based one only to find that the wine version runs better . 

BTW , the wine version for my pc does work . Marvel vs capcom gives good fps constantly , but it makes it heat up a lot . 

Views invited ....

Cheers

---

### Post by P05TMAN on 2011-09-17
> **blade4 said:**
> Hi everyone , this is more of a discussion question . Which is better : epsxe on linux or on wine ? I only wanna know cuz I've already got epsxe prepped up on my windows partition and don't really want to go through the grief of collecting all the components for the linux based one only to find that the wine version runs better . 

BTW , the wine version for my pc does work . Marvel vs capcom gives good fps constantly , but it makes it heat up a lot . 

Views invited ....

Cheers
  IMHO, I think the native Linux epsxe runs the emulation of PSX games extremely well. I think that performance would be hindered in Wine. It's kind of like running an emulator in an emulator, there are bound to be noticeable faults

---

### Post by blade4 on 2011-09-17
Hey Po5tman , thanks for the reply . Yes it does seem logical that native emulators should be less resource intensive - only the thing is that I just tried epsxe native on my system and it is , according to top , two to three times more processor intensive than wine . This is when both were configured for speed ! 

Any suggestions ?

---

### Post by P05TMAN on 2011-09-17
> **blade4 said:**
> Hey Po5tman , thanks for the reply . Yes it does seem logical that native emulators should be less resource intensive - only the thing is that I just tried epsxe native on my system and it is , according to top , two to three times more processor intensive than wine . This is when both were configured for speed ! 

Any suggestions ?
got me there....??  Sorry, lol

---

### Post by doomsday440 on 2012-02-12
Wine is MUCH faster to get set up on linux to run ePSXe, I haven't been able to run the native linux version as I've looked all over for the libgtk-1.2 files and installed them. (they're 64 bit, ePSXe requires the 32 bit versions and the ubuntu software center refuses to install them because its the wrong architecture) so i can't really say for sure if it runs faster or slower. I'm on an AMD Phenom II x4 955 with a Radeon HD5850.. even if i got the linux version running there probably wouldn't be much of a performance difference as it already runs perfectly fine. However i'm running on the 64 bit version of Ubuntu 11.10 so epsxe gives me the error:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64

If you're on 32 bit then you should be fine, check this link to get yourself set up with the libgtk1.2 files required to run it, its a bit hard to find sometimes.

[http://ubuntuforums.org/showthread.php?t=1784254](http://ubuntuforums.org/showthread.php?t=1784254)

happy emulating :3

---

### Post by mastergkage on 2012-02-12
Try playing around with different accessories or file ( i cant find the right word) like different set of grafx driver, controller, sound files etc etc. native is better. If you will run an emulator from an emulator it will take much resources, than running a single emulator right? try experimenting with different version of bios

---

