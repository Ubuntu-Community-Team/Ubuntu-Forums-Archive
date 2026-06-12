---
title: "can only boot from recovery mode (graphics issue)"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by profPlum530 on 2013-05-18
hi im new and decently experienced with linux and ubuntu
ubuntu 12.04 alternative install
i can only boot when using resume on the recovery menu
ive seen some1 with a similar issue on this forum however i dont have a link to the specific thread
ik its an issue with the graphics driver i just installed: the latest fglrx from the ati website
ive seen a few things that i thought would help like using nomodeset or w/e when booting but it did nothing 
o ya and that thread that i saw on this forum talked about going into software sources and checking the radio box "using fglrx proprietary driver" or something but i dont seem to have that option because of my version of ubuntu (12.04 instead of 13.04)

---

### Post by ehsanoo on 2013-05-18
Search for "Additional Drivers" in Dash Home and open it, maybe you see the drivers needed there.

---

### Post by profPlum530 on 2013-05-19
o ya that radio might be called something else actually and i might already hav it checked (i hav a radio checked allowing me to download proprietary drivers) can any1 confirm/deny this? or giv a solution to my original problem?

@ehsanoo thanks for the reponse although it already says im using the driver id like to use in additional drivers and id like not to change

---

### Post by profPlum530 on 2013-05-19
fixed! ik there was something simple i was missing! (i believe this fix is only nessisary for those who have my problem and like me used full disk encryption)
1. if u want to get into the system with normal boot one time then just select the normal (non-recovery) boot in grub then press e and remove the line "gfxmode $linux_gfx_mode"
2. from there use the terminal command sudo gedit /etc/grub.d/10_linux
3. search for the line "gfxmode \$linux_gfx_mode" and replace with "gfxmode \auto"
4. save
5. run sudo update-grub

---

