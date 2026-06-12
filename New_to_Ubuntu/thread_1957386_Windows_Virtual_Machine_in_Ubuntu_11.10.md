---
title: "Windows Virtual Machine in Ubuntu 11.10"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-04-12
Hello everyone

Would anyone know where I can get my hands on or the name of a Windows (7 or XP) virtual machine I can use on Ubuntu? I've tried for months to get some things working in Ubuntu and the forum replies ran dry on getting it to work too so a VM seems to be like my only option.

Thanks in advance!

---

### Post by na5h on 2012-04-12
A virtual machine is just like any other machine...only, well...virtual. In order to run Windows as a virtual machine, you still have to purchase a copy of Windows. As for any pointers to illegal downloads, I'm afraid that you will get no help from this forum!

Edit: If you are only looking for the APPLICATION needed to run/create virtual machines, [Virtualbox]("https://www.virtualbox.org/") is a good choice! It can also be found in the Software Center (Open Source edition). If you wish to have USB-support, then you need to install the PUEL-licence version from the Oracle Virtualbox website (mentioned above). Both versions are free of charge! There are also many threads in this forum about how to enable USB-support in Virtualbox, if you need help.

---

### Post by jerome1232 on 2012-04-12
Oracles virtualbox works great and is easy to use, install it from the software center. As stated you do need a valid copy of Windows to use.

I also wanted to add if you plan on using it for windows games, it just won't work well if the games are 3d. You'll need a dual boot for that sort of thing.

---

### Post by QIII on 2012-04-12
I use the repo provided by virtualbox.org.

Updates are quicker than waiting for them to get into the Ubuntu repo.

The instructions are available at virtualbox.org.

---

### Post by haqking on 2012-04-12
> **Drowz0r said:**
> Hello everyone

Would anyone know where I can get my hands on or the name of a Windows (7 or XP) virtual machine I can use on Ubuntu? I've tried for months to get some things working in Ubuntu and the forum replies ran dry on getting it to work too so a VM seems to be like my only option.

Thanks in advance!

are you asking for a virtualisation program or a virtual XP/w& machine ?

if it is the first see the posts above, Virtualbox works great.

if it is the second you need to create your own Windows Virtual machine using something like virtualbox so you need a valid licensed version of windows to do that.

Peace

---

### Post by caron gangoo on 2013-02-20
Hi everybody !

I am trying to setup a virtual machine whatever it is by wmplayer, wmworkstation or even oracle virtual box for ubuntu12.10.
But never succeeded ! Either there is no reaction ( VM WARE, AQEMU, QEMU ) or I am almost done in virtual box but at the end ( see SNAPSHOT not MY PHOTO!LOL!)
So please hheeeeeellllllppppppppppp):P. U can also mail me on [email]carongangoo_2005@yahoo.fr[/email] or add me on Fb.

SOS MAYDAY

Caron

p.s : has anyone already succeeded or even tried !??!?!?!

---

### Post by caron gangoo on 2013-03-10
Hi everybody !

I am making this post to inform everybody that ORACLE VIRTUALBOX works almost perfectly on Linux Mint 14 CINAMMON.  :) 
I was trying since a so long time to setup a WINDOWS 98 SE VM MACHINE ! Itried with VM PLAYER, QTEMU but setup was always freezing after copying files !
I tried for that 100 times to do it on ORACLE VIRTUABOX but I did got always the same error : FAULT OUTSIDE THE MS DOS EXTENDER " ( with many numeric figures !)[ATTACH=CONFIG]240002[/ATTACH][ATTACH=CONFIG]240001[/ATTACH][ATTACH=CONFIG]240002[/ATTACH] :twisted: 
On last resort, I downloaded last version for LINUX MINT 14 CINAMMON . Of course , new software but same old problem ! :oops: 
Then I solved it ! This is how : 8) 

To install WIN 98 SE as guest on linux MINT 14 CINAMMON , you must have a win98 ISO but also the BOOT DISK in .img format ! I advise you to also download SCI TECH DISPLAY DOCTOR ( for display in 32 bit in win98 ) and RAIN , a cooler for " cool" running on win 98 SE.


ABOUT VIRTUABOX SETTINGS : ( MAY BE THESE CAN ALSO BE USED IN UBUNTU12.10 ORACLE VIRTUBOX VERSION ) !

SETTINGS -GENERAL- ADVANCED- DISABLE SHARED CLIPBOARD & DISABLE DRAG'N' DROP !

SETTINGS-SYSTEM-MOTHERBOARD 64 RAM -CHIPSET PIIX3( I run a DELL VOSTRO 64 BIT...). I did not enable ANY other feature in this section !
                SYSTEM-MOTHERBOARD-DISABLE PAE/NX !
                SYSTEM ACCELAREATION- NO FEATURE to be  ENABLED !!!

SETTINGS-DISPLAY- DO NOT ENABLE 2 OR 3 D ACCELERATION ! (if you are on a home or boosted graphic gamer pc , perhaps you can...if you dare...LOL!) VIDEO MEMORY- 36 MB

I think it's all ..oh yes for sound driver , better choose " soundblaster" ..

And that works ! I don;t get internet conflicts with mu USB DONGLE and my virtual machine whose running so so smoothly....

Cheers from Rodrigues Island !  ( 500 km S-E of Mauritius Island)

Caron

---

