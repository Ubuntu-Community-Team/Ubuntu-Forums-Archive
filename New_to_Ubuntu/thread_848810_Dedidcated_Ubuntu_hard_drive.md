---
title: "Dedidcated Ubuntu hard drive"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by PaulofOz on 2008-07-03
I currently run winxp on one HD and have my old w98 8Gig drive as slave. I bought a dedicated HD for Ubuntu to try out so I disconnected the two windows drives and install the ubuntu HD in their place. The system worked fine. When I changed back to the two Win HD's XP would not boot up. I run the XP install disk again and eventually it loaded and now it is not a problem. I'm thinking it was MBR issues? My question is: Will ubuntu cause this problem if I change over the HD's?  I am worried to try it again cause I don't want the hassle and loss of access to the internet and documents.

Paul

---

### Post by ZabiGG on 2008-07-03
Hi there,

Let me ask a very basic question. When you reconnected the two drives, did you connect them in the same sequence as before? The boot drive has to be master...

---

### Post by bluepowder7 on 2008-07-03
+1 to connecting them the right way - and also to double-checking BIOS stuff.
there's virtually nothing that gets stored on the mobo that would make hard-drive-musical-chairs a problem.

---

### Post by ChameleonDave on 2008-07-03
> **PaulofOz said:**
>  My question is: Will ubuntu cause this problem if I change over the HD's? 

Not sure what you mean by this.  Ubuntu will not cause any problems.  Physically moving hard drives around, however, confuses both the BIOS and operating systems, sometimes making it necessary to reconfigure the way they boot, in order to un-confuse them.

---

### Post by PaulofOz on 2008-07-04
**ZabiGG**- Yes I did install in the correct order.

**bluepowder7** - I'm interested to here more of what you have to say. One thing I did notice was the clock had changed after I re-installed the two Winows HD's

**ChameleonDave**- Are you refering to the boot sequence in the BIOS? Because I did check this when I was having the problem. 

All I want to know is. If I connect the Ubuntu drive up again, what  areas do i need to check to make sure everything is correct when the Windows HD's are reconnected?

I appreciate everyones input. Thankyou.

Paul

---

### Post by ChameleonDave on 2008-07-04
> **PaulofOz said:**
> 

**ChameleonDave**- Are you refering to the boot sequence in the BIOS? Because I did check this when I was having the problem. 

All I want to know is. If I connect the Ubuntu drive up again, what  areas do i need to check to make sure everything is correct when the Windows HD's are reconnected?



The main thing is that Windows needs to identify the correct partition as being "C:" when it boots up.  When GRUB and Ubuntu don't identify the correct partition as being "/", you can just correct that in config files such as /boot/grub/menu.lst and /etc/fstab.  However, I don't really know how Windows does such things.  It's all a bit opaque.  You never really know why Windows does stuff.

---

### Post by bluepowder7 on 2008-07-04
well, with BIOS, you can always reset to factory defaults, which gets you right back to a clean slate - then it's just a matter of hooking up the other hard drive, configuring BIOS to boot from it, and letting the show go on.

also, the MBR is on the hard drive, not on the motherboard.

you can do the complete opposite (replace your mobo with a new one, with obviously a new processor, possibly different chipsets, etc), and hook up your old windows hard drive to it and it'll still work - though it will obviously have to reload all the drivers.  but the OS for the most part will be there, and your software packages will still be installed like before.  i haven't tried that with linux, though.

---

### Post by PaulofOz on 2008-07-04
I must not have been as thorough as I first thought. I have discovered the dedicated linux drive alters the BIOS hard disk priority selection. That makes me feel a whole lot happier. Now, if only I could get my Spirit Lan 802.11b USB to work. I don't think the linux is even recognising it.

---

