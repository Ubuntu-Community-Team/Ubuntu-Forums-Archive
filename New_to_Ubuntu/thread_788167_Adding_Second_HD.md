---
title: "Adding Second HD"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Covalent Bond on 2008-05-09
Currently have a dual boot system (XP and Gutsy).  Before upgrading to Hardy, would like to add second HD where I would install Hardy.  Do I need to be aware of any special issues with the slave HD (assuming it is compatible with my computer).  IE, is there any special details I need to pay attention to before I buy the second HD.  Some say compatible with Windows, and I am wondering if this means it would not be compatible with Ubuntu.  I realize this is a very basic question, but I know little of the technical aspects of hardware compatibility.

CB

---

### Post by tszanon on 2008-05-09
Not at all. The only thing that limits what HD you can use is your motherboard. Checking its manual is all you have to do to know what HD you can buy.

Edit:
Being more specific, there are 3 common HD types: IDE/ATA, SATA and SCSI. That's the most important thing to notice. You probably can use only ATA or SATA.

Edit 2: oh, you posted before my first edit.

---

### Post by Covalent Bond on 2008-05-09
tszanon:

Thank for the quick reply.  I know what HD to get that is compatible with my computer, and I will install it and then install Hardy on the new drive.
CB

---

### Post by tszanon on 2008-05-09
> **Covalent Bond said:**
> tszanon:

Thank for the quick reply.  I know what HD to get that is compatible with my computer, and I will install it and then install Hardy on the new drive.
CB

Great. You're welcome.

---

### Post by JacquiOh on 2008-05-09
> **Covalent Bond said:**
> Currently have a dual boot system (XP and Gutsy).  Before upgrading to Hardy, would like to add second HD where I would install Hardy.  Do I need to be aware of any special issues with the slave HD (assuming it is compatible with my computer). 

CB

I've just installed HH on my 5 year old XP machine on a brand new hard drive. I did the initial install, format, etc in Windows.

Things I wish I had known this morning:

I partitioned in Windows when I didn't need to. The Ubuntu install did it for me. And I was worried there would be issues with the GRUB menu, but it was just the same as I have on my laptop where both OS are on the same HD.

What's particularily weird is that Windows can't see the partition where I have Ubuntu installed, but it can see the rest of the drive. 

Hope that helps a bit!

Jacq

---

