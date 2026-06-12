---
title: "Grub+Install question-Dual boot Hardy/Feisty"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Harpoon on 2008-04-26
My laptop has a working dual boot setup with XP and Feisty.  I am looking to change that to a dual boot with Hardy (replacing XP) and my working Feisty setup. Feisty has separate root and home partitions.

Here is the installation question:
If I boot up the live Hardy CD and install from that (putting the whole installation on that one formerly XP partition--don't need help with partitioning), will grub also pick up the Feisty install - - or do I have to watch out for a few options that I missed before.I'd like to avoid having to manually edit the grub menu everytime I do a kernal update. If I need to do chain loading, then I'd like to work out those details before doing the install as I only have access to this one computer (I've already gathered the references for that).

Postscript:  I'm considering buying a larger HD for this machine, in which case the question would then be Hardy/Gutsy/Feisty.  

And for those who would ask why?
Feisty = known working for production machine; 
Gutsy = replacement for Feisty as I gain assurances it plays nicely with my demands; 
and one other for testing and all around self punishment (must have something to "fix" if everything else is working as advertised).

Ten years with *nix and still a noob.  I remember doing this with LILO a while back, but never with multiple Ubuntus.

All replies appreciated.

---

### Post by Thingymebob on 2008-05-12
Not tried with 2 versions of ubuntu but grub always picked up the kernels from any other distro I had installed,  however I do have a seperate small /boot partition which is common among all distros.

---

### Post by shifty_powers on 2008-05-12
afaik, the installation routine should pick up other os's, including other versions of ubuntu and add them to grub...

---

### Post by zvacet on 2008-05-12
> I'd like to avoid having to manually edit the grub menu everytime I do a kernal update.

If Hardy doesn´t pick up your Feisty you will have to chainload.One which you choose to chainload put below this line 

### END DEBIAN AUTOMAGIC KERNELS LIST

and you will not have to manually edit grub because of kernel update.

---

