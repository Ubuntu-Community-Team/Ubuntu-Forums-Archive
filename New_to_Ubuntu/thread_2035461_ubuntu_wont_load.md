---
title: "ubuntu wont load"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by pacbas252 on 2012-07-30
**[SIZE=2]started with computer with winxp and dvdr.  have since reformatted hard drive.[/SIZE]**

**[SIZE=2]initially screen went black after told ubuntu to load.  then tried nomodeset, noapic, apic=off[/SIZE].  [FONT=Arial][SIZE=3]now get "SIS630 comp. bus not detected, module not inserted" and then screen goes black."[/SIZE][/FONT]**



what should i try to get ubuntu to load?

---

### Post by levlaz on 2012-07-30
> **pacbas252 said:**
> **[SIZE=2]started with computer with winxp and dvdr.  have since reformatted hard drive.[/SIZE]**

**[SIZE=2]initially screen went black after told ubuntu to load.  then tried nomodeset, noapic, apic=off[/SIZE].  [FONT=Arial][SIZE=3]now get "SIS630 comp. bus not detected, module not inserted" and then screen goes black."[/SIZE][/FONT]**



what should i try to get ubuntu to load?


I found [this as an old bug]("https://bugs.launchpad.net/linux/+bug/87255"), maybe you could try that. Are you able to at least see the text-based login screen? 

Login as your normal user and blacklist the file. 

Best, 

Lev

---

### Post by Jay Christnach on 2012-07-30
Do you have "failsafe defaults" as BIOS settings?

---

### Post by Bashing-om on 2012-07-31
That sounds bad! 
question.... can you load ubuntu from the live CD (the try ubuntu option) ?

what happens then ?

               best to ya !

---

### Post by pacbas252 on 2012-07-31
> **Jay Christnach said:**
> Do you have "failsafe defaults" as BIOS settings?

no.  just optimal values or best perforamance values

---

### Post by pacbas252 on 2012-07-31
> **levlaz said:**
> I found [this as an old bug]("https://bugs.launchpad.net/linux/+bug/87255"), maybe you could try that. Are you able to at least see the text-based login screen? 

Login as your normal user and blacklist the file. 

Best, 

Lev

only screen i have is the ubuntu screen that says "try ubuntu without installing, install ubuntu,...  when i tell it to install ubuntu (after doing a nomodeset under other options), i get black screen with blinking cursor, then ubuntu 12.04 with 4  dots "counting down" then screen says 
**SIS630 comp. bus not detected, module not inserted,**

,then screen goes black.

---

### Post by pacbas252 on 2012-07-31
> **Bashing-om said:**
> That sounds bad! 
question.... can you load ubuntu from the live CD (the try ubuntu option) ?

what happens then ?

               best to ya !

what do you mean by "live cd" (i've tried loading via a usb and currently a cd (both downloaded from web).  I have tried the try ubuntu without installing option as i've tried the install ubuntu and both result in same blank screen after sis630 comp. bus not detected "message" (only if i have selected nomodeset under other options, otherwise i just get the blank screen immediately.)

---

### Post by IHeequ5i on 2012-07-31
When you made your CD, did you burn it at the slowest possible speed?  I had to do that in order to make a working CD.

---

### Post by pacbas252 on 2012-07-31
> **Doomspark said:**
> When you made your CD, did you burn it at the slowest possible speed?  I had to do that in order to make a working CD.

yes, in fact i burned it on 3 different burners on 3 different computers.

---

