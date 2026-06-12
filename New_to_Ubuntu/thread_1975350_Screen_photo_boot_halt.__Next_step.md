---
title: "Screen photo boot halt.  Next step?"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-07
[http://i348.photobucket.com/albums/q339/BoyntonStu/Boothalt5712.jpg]("http://i348.photobucket.com/albums/q339/BoyntonStu/Boothalt5712.jpg")


My wife's PC gets to this step in booting from USB flash.

(Stopping: Automatic crash reporting generation failed)

It is a desktop not a battery operated laptop.

Any ideas?

---

### Post by Boyntonstu on 2012-05-07
Bump

---

### Post by Boyntonstu on 2012-05-08
Hey guys!!!

I am really stuck here.

What would you try next?

---

### Post by Boyntonstu on 2012-05-09
Bump

---

### Post by steeldriver on 2012-05-09
> **Boyntonstu said:**
> 
What would you try next?

Hi can you post some details to help us

- what Ubuntu version?

- what kind of PC? what graphics card?

- are you trying to boot a live USB or install from it? what options did you select ('Install' or 'Try'?)

- have you tried booting any other machine from the same USB to check it is not corrupted?

---

### Post by Boyntonstu on 2012-05-09
Hi can you post some details to help us

- what Ubuntu version?  

11.10

- what kind of PC? 

Dell Optiflex 330  

What graphics card? 

NVidia Quadro NVS 285 DMS-59 64MB Full Height PCI-E Video Card

- are you trying to boot a live USB or install from it? 

Live USB


what options did you select ('Install' or 'Try'?)

It is an installed USB that is not corrupted.

- have you tried booting any other machine from the same USB to check it is not corrupted?

Yes, it boots fine on another PC.

My thinking is that if I edited Grub2 to eliminate the tests that are not required (battery on a desktop), it would boot beyond the obstacle.


Thanks for replying.

---

### Post by bogan on 2012-05-09
Hi!, **boyntonstu**,

A hang-up after " Checking Battery State" is usually a sign of video driver problems. EDit: after reading your last Post: The problem is not with the Battery state check, but with what comes next.

Check out MAFoElffen's Step-by-Step Trouble shooter in the Sticky of 'Installations & Upgrades': Post #1. There is a full Index in Post #2.
[http://ubuntuforums.org/showthread.php?t=1743535&page=101](http://ubuntuforums.org/showthread.php?t=1743535&page=101)

As a first step guess you need to choose the 'nomodset' option after pressing 'ESC' during boot-up from the LiveCD/USB.

Chao!.** bogan**.

---

### Post by Boyntonstu on 2012-05-09
> **bogan said:**
> Hi!, **boyntonstu**,

A hang-up after " Checking Battery State" is usually a sign of video driver problems. EDit: after reading your last Post: The problem is not with the Battery state check, but with what comes next.

Check out MAFoElffen's Step-by-Step Trouble shooter in the Sticky of 'Installations & Upgrades': Post #1. There is a full Index in Post #2.
[http://ubuntuforums.org/showthread.php?t=1743535&page=101](http://ubuntuforums.org/showthread.php?t=1743535&page=101)

As a first step guess you need to choose the 'nomodset' option after pressing 'ESC' during boot-up from the LiveCD/USB.

Chao!.** bogan**.


Thanks,  I am off to study.

---

### Post by Peter09 on 2012-05-09
Try holding the shift key down when booting, it should get you to the boot menu. Select the top option and type 'e' for edit.
 
Move the cursor to just infront of the 'quiet' parameter and enter 'nomodeset'.
 
(no quotation marks).
 
Then type F10 to continue the boot.
What happens?

---

