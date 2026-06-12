---
title: "Failed to create swap space?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by lubug on 2012-07-26
[B]"The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed."

[/B][B]I am getting this error while installing Lubuntu on an older Acer laptop (40GB hard drive, 256 MB RAM).

Interestingly, I get this error when I try to install Lubuntu 12.04 on the laptop, but not when I install Ubuntu 11.10. In both cases I am installing from a USB drive. The Ubuntu 11.10 installation proceeds just fine. But Ubuntu runs too slowly on this older machine so I wanted to try Lubuntu.

I have tried to install Ubuntu 11.10, and then "upgrade" it to Lubuntu 12.04 (I had imagined that the Lubuntu upgrade wouldn't require recreating the swap space), but the same failure occurs even then, too.

Does anyone know definitely what the source of this failure is? There are plenty of forum posts out there suggesting without any authority that one check the hard drive. I don't see any evidence that that's the problem.
 [/B]

---

### Post by oldos2er on 2012-07-26
Post moved to its own thread.

---

### Post by Bufeu on 2012-07-26
Can you post a screenshot from GParted?

---

### Post by NikTh on 2012-07-26
Hi , 
i don't know about this error (maybe its an installer bug? ) but i think you can proceed with installation without create a swap space. 
Leave some GB's empty so when installation finish , you can create a swap space after, with Gparted. 

Thanks

Thanks

---

