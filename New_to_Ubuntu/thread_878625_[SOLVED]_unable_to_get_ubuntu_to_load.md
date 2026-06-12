---
title: "[SOLVED] unable to get ubuntu to load"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by hazman on 2008-08-03
unable to get ubuntu to load.first 4 lines load then it stops. its a fresh install of 7.10

---

### Post by ajgreeny on 2008-08-03
If you mean from the live CD, check both the burn quality and also the iso md5sum to check all is well there.  If it really is from an installation on hard disk, there is obviously something very wrong and it may need a better man than me to help, but what is the 4th and final line at which it all stops?

---

### Post by Bodsda on 2008-08-03
If it is a hard disk install, then im assuming you see a grub menu. When there instead of booting Ubuntu press 'e' then youll be taken to the boot line (might have to press 'e' again cant remember) remove 'quiet' from that line then press 'esc' then 'b' this should give you more information and error messages which would be helpfull if you posted

Hope this helps

Bodsda

---

### Post by ajgreeny on 2008-08-03
>  then press 'esc' then 'b'
If you want to try what Bodsda suggested he nearly got it right.  Instead of **esc** you need to hit **return** to accept the edit you just made.  **esc** will go back to the original.

---

### Post by hazman on 2008-08-03
last time i installed it i had to enter something to set computer up as i have to plug h/drive in another laptop to install and put it back in cos i gone in to recovery mode tried starx but says theres no screen

---

