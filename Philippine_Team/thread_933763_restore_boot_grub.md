---
title: "restore boot grub"
date: 2008-09-29
forum: Philippine Team
---

### Post by killer_d76 on 2008-09-29
i know this has been asked before though i can't seem to find where to look for the answer.. i am planning to remove, delete and re-install Windows XP on my laptop (my son requested it for me to do so)for some reason, now i understand and i have read that if you re-install Windows it will delete the existing "boot grub", just in case.. how am i going to restore it back since i don't want to format the whole drive?, i don't have enough extra external HDD to back-up all my files on my Ubuntu, and i don't want to got to the whole process of setting it up again!.

---

### Post by Script Warlock on 2008-09-29
load-in the live cd 
try ubuntu without install in the computer
open the terminal and type
              sudo grub(supply your password if he ask for it)

         grub> find /boot/grub/stage1
             hd0 (or whatever number given by the "find" result)
             > root (hd0,1)
             > setup (hd0)
             > quit 

restart your system.....

---

### Post by wersdaluv on 2008-09-29
Ito favorite ko [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by killer_d76 on 2008-09-30
ok thanks guys.. i'll try it first on VBox!..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86799&d=1222747977[/IMG]

---

### Post by killer_d76 on 2008-09-30
@boyet, i tried using your procedure first.. and it works!.. hehehe, now i'm confident to delete windows now!... WOHHOOOO... thanks bro!.

---

### Post by Script Warlock on 2008-09-30
ya but thats the same proc of wersdaluv link....hehehhe cheeers:D

---

