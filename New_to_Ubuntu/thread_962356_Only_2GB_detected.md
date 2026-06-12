---
title: "Only 2GB detected"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by bad_mofo on 2008-10-29
Hi all,

I am currently dual booting with Ubuntu 64 and Kubuntu 32.
The only reason for using the 32 bit OS is to develop applications using flex builder (installation on 64 but linux is not easy).

I have 6GB ram: 2x2GB and 2x1GB.

6GB is recognised on boot and is available in Ubuntu 64. Only 2GB is being used in Kubuntu 32. 

I would actually be happy with 3 and a bit gigs. I have also read that I could recompile the kernel with PAE to address the whole 6GB. I have also tried swapping

Since only 2GB is currently detected, will enabling PAE help? Are there any relatively simple guides to enabling PAE on Kubuntu?

Thanks in advance!

---

### Post by stephanvaningen on 2008-10-29
Check your hardware manual: possibly you have 4 RAM slots on your motherboard and it could be that in the hardware manual you will find that onle slot X and Y will be available for 32-bit, and all 4 slots in 64-bit...
--
(I am not 100% sure, but please check it to rule this out)
--
If this is the case, switching the 2G RAM cards with the 1G RAM cards in the slots will maybe solve your problem then...

---

### Post by bad_mofo on 2008-10-29
stephan, thanks for the quick response!

I have actually tried switching the ram blocks around, nothing changed. I think 1GB blocks are faster so maybe the motherboard (asus p5b deluxe) is still choosing to use the 1GB blocks first. I will try removing the 1GB blocks to see what happens.

---

### Post by random turnip on 2008-10-29
[EDIT]
Sorry, delete this post if you want, I misread the thread.

---

### Post by bad_mofo on 2008-10-29
[EDIT]
No need for this reply then.

---

