---
title: "Why a cd Boot, but no hard drive boot?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by infoanalysis on 2008-05-11
amd 64 bit 2048 ram 
8.04 ubuntu tried installing by alt cd as well
have change alm ost every BIOS configuration I can think of and added the psi=nomsi to the load command- initramfs everytime

---

### Post by Aearenda on 2008-05-11
Is it a mixed IDE/SATA configuration?
Have you tried all_generic_ide as a kernel parameter?

---

### Post by infoanalysis on 2008-05-11
Not quite sure,on features BIOS setup it has onboard sata -ide and for options it has disabled, ide and raid, I have tried all three options there,

How do I set "all generic ide" as a kernel parameter? at the end of the string like I did the psi=nomsi?

---

### Post by infoanalysis on 2008-05-11
Hey it worked, thanks again, how do I make that a permanent command on the menu?

After three days of jerking around I finally have bootable hard drive. I am sure the learning curve is just now starting

---

### Post by Aearenda on 2008-05-11
Great! See the instructions in [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15) for making it permanent.

---

### Post by infoanalysis on 2008-05-11
thanks once again! Now I have been trying to load flash player 9, which was easy when I was booting off the cd with an xp 32 bit partition on the hard drive. But since it is 64 bit - it does not support the 64 x86. on the new partition just for 8.04 ( XP is now off andhas been formated to ubuntu )But this is another thread - youhave been a lifesaver already- Ok so I can't watch youtube as of yet- the system is faster now and at least I am utilizing 64 bits.

---

### Post by Aearenda on 2008-05-11
I'm glad to be able to help - but I don't use 64-bit so you're right, Flash is another thread. But there are plenty around on it already, you shouldn't have to look too hard.

---

