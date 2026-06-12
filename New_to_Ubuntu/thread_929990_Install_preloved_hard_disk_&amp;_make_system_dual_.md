---
title: "Install preloved hard disk &amp; make system dual boot"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by bucktron on 2008-09-25
I have a old hard disk cannibalised from a old (circa 2003) PC. It has windows XP installed on one partition. Now, if I plug this hard disk into my ubuntu box what do I have to do to dual boot?
Can I just use grub to update my boot list to point to the windows partition and away I go?

---

### Post by kansasnoob on 2008-09-25
Well, there are a number of small complexities to consider:

Are both hard drives IDE? If so will they share the same cable? If so you should make sure that your existing drive is set up and connected as Master and the new drive (w/windows) is connected and set up as slave.

In that scenario you should be able to just add the Windows entry to Grub, but you'll want to use drive mapping:

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

In any other scenario; two IDE drives connected to seperate IDE ports on the MOBO, one IDE and one SATA, or two SATA's, then BIOS settings come into play.

Do you know how to change the "jumper" settings on the drives?

Lots of little hardware questions can arise.

---

### Post by Titan8990 on 2008-09-25
As well as the fact that when you take a Windows and put it on a different machine it freaks out. All the drivers will be wrong and it will once again require activation. Officially, what you are trying to do is illegal as well (against Microshaft licensing). This might give you some troubles with reactivation.

---

### Post by Therion on 2008-09-25
I've tried dual-booting via dual drives.  CAN it be done?  Yes.  

Is it about two-and-a-half buttloads easier to dual-boot using a single drive and use the other for data and backups and such?  You betcha.

---

### Post by bucktron on 2008-09-25
Both drives are IDE so that should be OK. 
However the activation and drivers thing doesn't sound too clever as I've got no documentation for the old machine.
I'll try it out anyway and see what happens.
Thanks for the prompt replies!

---

