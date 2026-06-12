---
title: "Uninstalling ubuntu"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Arendyl on 2013-01-16
Let me start out by saying I am retarded. I dual-booted ubuntu windows. I decided to remove ubuntu, I just formated the partition instead of just following the instructions like an idiot. Now the Grub prompt is showing up giving me an error message that ubuntu is not there.. Is there any way to get my computer back to running normal?

---

### Post by deadflowr on 2013-01-16
What do you consider to be normal?

My assumption is that you are now running only Windows.

If this is the case, then you will probably need to follow this to remove grub.

[http://askubuntu.com/questions/151253/removing-grub-from-windows-system-after-uninstalling-from-withing-windows]("http://askubuntu.com/questions/151253/removing-grub-from-windows-system-after-uninstalling-from-withing-windows")

---

### Post by d4m1r on 2013-01-17
No, that would usually work...Except, it does not remove the Grub bootloader as you learned the hard way ;) It is not stored within the Ubuntu parition you had, but on the MBR (master boot record) that is also shared with Windows.

To remove grub, boot from your Windows CD and select the option to repair the install/boot record. It will overwrite your MBR with only Windows related files.

---

### Post by Alex Ibraj on 2013-01-17
[SIZE=3]The most stupid think every one of us that are new at Ubuntu is that we dual boot Ubuntu and Windows selecting each OS everytime from GRUB .... I made this mistake every time ... but after finding Easy BCD .... Well eveything goes awesome....

If I dont need Ubuntu or if I want to install another kind of Linux Distribution ... well I just delete the linux partitions(Swap ; / ; /boot) and extend my primary partitions.

But I never quit studying Ubuntu....

So if you need a solution for the future well .... For me is this free app Easy BCD 2.2

The link is here and the Dual booting methods are simple...[/SIZE];)

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

---

### Post by darkomano on 2013-01-29
EasyBCD (Neosmart) is violating copyright law.
 
It is disguising ntldr (Microsoft Copyright) as easyldr and pretending that it is a Neosmart development.
 
Recommending such a program is not a good move unless you are connected with Neosmart. Then you do just work for the boss. ;-)
 
I am not sure if EasyBCD is violating copyright of grub4dos disguising it as neogrub.
 
The product just steels and mimics foreign work.

---

### Post by daniell59 on 2013-01-29
I put Ubuntu on one hard drive and Windows on the other one. When I want to change operating systems, I have to go into the BIOS. I just feel that I want to keep them separate.

---

### Post by arpanaut on 2013-01-29
> **darkomano said:**
> EasyBCD (Neosmart) is violating copyright law.
 
It is disguising ntldr (Microsoft Copyright) as easyldr and pretending that it is a Neosmart development.
 
Recommending such a program is not a good move unless you are connected with Neosmart. Then you do just work for the boss. ;-)
 
I am not sure if EasyBCD is violating copyright of grub4dos disguising it as neogrub.
 
The product just steels and mimics foreign work.

Please cite the source of this information.
If true, I'm sure that MS and others would be all over them with lawyers and all.

---

### Post by darkomano on 2013-02-17
> **arpanaut said:**
> Please cite the source of this information.
If true, I'm sure that MS and others would be all over them with lawyers and all.
 
Everybody interested can prove this:
 
1. Download EasyBCD
2. Install in Windows 7
3. Go to EasyBCD installation folder
4. look for easyldr and extract strings - you will see Microsoft Copyright:
 
> V S _ V E R S I O N _ I N F O &#1029;&#1087;&#1102;    &#1054;  &#1054;?    &#1080;  S t r i n g F i l e I n f o &#1044;  0 4 0 9 0 4 B 0 L   C o m p a n y N a m e M i c r o s o f t C o r p o r a t i o n @  F i l e D e s c r i p t i o n B o o t L o a d e r r )  F i l e V e r s i o n 5 . 2 . 3 7 9 0 . 2 8 2 5 ( s r v 0 3 _ s p 2 _ r c . 0 6 1 1 0 3 - 1 3 0 3 ) : 
 I n t e r n a l N a m e o s l o a d e r . e x e &#1026; .  L e g a l C o p y r i g h t © M i c r o s o f t C o r p o r a t i o n . A l l r i g h t s r e s e r v e d . B 
 O r i g i n a l F i l e n a m e o s l o a d e r . e x e j %  P r o d u c t N a m e M i c r o s o f t ® W i n d o w s ® O p e r a t i n g S y s t e m @   P r o d u c t V e r s i o n 5 . 2 . 3 7 9 0 . 2 8 2 5 D  V a r F i l e I n f o 
 
No copyright notice about this in EasyBCD / Neosmart license file.
On Neosmart site you can read how "easyldr" is own development of Neosmart.
 
I think that Neosmart is a company of crooks which are stealing foreign work.
 
Same holds for neogrub - it is grub4dos with minor changes.
No copyright notice and clear violation of GPL.
Everybody interested can proof this easily.

---

