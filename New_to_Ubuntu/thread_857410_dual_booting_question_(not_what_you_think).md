---
title: "dual booting question (not what you think)"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by rdsii64 on 2008-07-12
Hello all. Once again here comes some one with another one of those dual booting questions. I am not going to insult your patients and ask how to dual boot windows and Linux. That much I can handle, not to mention you can't through a rock in a Linux forum with out landing on a post that will hand hold even the newest of new users. What I am going to ask you is something I have been unable to answer on my own with the search function or anywhere else. The version of windows I am running is 32 bit. The version of Ubuntu I am going try out is 64 bit. 

What I have been unable to find is information on any problems I am likely to run into when trying to dual boot a 32 bit os and a 64 bit os.

Any help would be greatly appreciated.

---

### Post by CautionaryX on 2008-07-12
You wont have any problems dual booting with one OS being 64-bit and the other 32-bit.

---

### Post by avtolle on 2008-07-12
> **cautionaryx said:**
> you Wont Have Any Problems Dual Booting With One Os Being 64-bit And The Other 32-bit.
+1

---

### Post by Kevbert on 2008-07-12
I've a mixture of 32 and 64 bit OS on my PC and no problems here.  You could even try using 32 and 64 bit versions of Ubuntu on the same PC - the only (minor) problem is remembering which one is which in the boot menu as they will have the same kernel names!

---

### Post by AnLGP on 2008-07-12
I've never done it but to comment to this

> the only (minor) problem is remembering which one is which in the boot menu as they will have the same kernel names! 

to avoid that minor problem just edit the grub menu list and change the "title" to

title Ubuntu64

and for the other

title Ubuntu32

---

### Post by crazyness003 on 2008-07-12
> **AnLGP said:**
> I've never done it but to comment to this



to avoid that minor problem just edit the grub menu list and change the "title" to

title Ubuntu64

and for the other

title Ubuntu32

I have this EXACT setup. 
sda 1: 32bit Ubuntu
sda 2: 32bit Windows XP
sda 3: 64bit Ubuntu (default)

I use 64 bit more. Im actually gonna redo my system and dedicate 1/3 of my hdd to Ubuntu64, 1/3 to WinXP, and 1/3 for testing other distros.

When you boot into an OS, the other installed OS's do not affect anything that happen on your current one. They only act as other file disks. You just have to be careful to not mess around with the other OS's partition while in the one you booted in since any changes can go wrong and you end up with a disabled OS (the one you made the changes to).

---

### Post by Kevbert on 2008-07-12
The only problem you'll have after renaming the kernels is that after some updates you may find the names revert back to their original names.

---

### Post by kansasnoob on 2008-07-12
My daughter has 64 bit Vista Ultimate on her machine with a dual boot of 32 bit Kubuntu, no problems. She tried 64 bit Kubuntu first but did have some problems ............. I can't tell you what, kids tell dads nothing! They only ask for money!

---

### Post by rdsii64 on 2008-07-14
just wanted to let those who offered an answer to my question that I just finished intalling 64 bit 8.04 on my machine. My machine is a coolermaster cosmos case, an evga 780i motherboard, a Q9450 quad core processor, 4 gigs of corsair ddr 800 ram. I still have replace my current pair of nvida 7600 gt's. when the money is there I will replace them with a pair of 98oo gtx's.

anyway she is running smooth and fast. now to go and play with compiz.

thanks

ron

---

