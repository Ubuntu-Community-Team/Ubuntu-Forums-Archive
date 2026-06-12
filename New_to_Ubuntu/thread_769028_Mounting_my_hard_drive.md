---
title: "Mounting my hard drive"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Malikius on 2008-04-26
I have a number of questions here. 

1. I am trying to mount my terraserver drive and don't know how. 
   (I have a drive that says USB drive) I'm assuming it's that one. 
2. In the 7.10 I could go to the partioning function and now it isn't anywhere I can find in the 8.04 upgrade. 
3. I need to find out how to switch my computer from WORKGROUP to DALLTAB. 
4. How do I go to administrative mode to give myself "god mode"? 
-------------------------------------------------------------------------
I am even more confused with this new upgrade then I was with 7.10, have posted simiular topics on other sections of this forum but nobody has answered.

Please help me. I am going bald, pulling out what little hair I have left. :(

---

### Post by davmac on 2008-07-16
1. I've always found that any USB drive I've plugged in always automounts so can't answer this one.

2. Start up Synaptic (System->Admin->Synaptic) and install gparted. You'll then find it in the menus (under accessories, from memory).

3. Press alt-F2 and type in "gksudo gedit /etc/samba/smb.conf". Look for the line that starts "workgroup = " and amend that accordingly. This won't be effective until Samba is restarted - unless you're already familiar with how to do this, the easiest way is to reboot your machine.

4. If you're working in a terminal, prefix your command with "sudo", if you're working in the GUI, press alt-F2 and type, for example "gksudo nautilus", or whatever progam you wish to run. BE VERY CAREFUL WHAT YOU'RE DOING... but then you knew that already didn't you :)

---

