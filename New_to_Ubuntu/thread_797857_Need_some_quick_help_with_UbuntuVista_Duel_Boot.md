---
title: "Need some quick help with Ubuntu/Vista Duel Boot"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by SuperNapalm on 2008-05-17
Okay, I've finally figured out that Ubuntu is WAY better than XP in terms of handling music/video and college work (at least from my experience). I'm now going to switch my main OS to Ubuntu and have Vista as my secondary OS until Wine has better support for games.

I just have a quick question. I'm going to move all my critical files over to Ubuntu, wipe XP off and then install Vista. My question is will Vista overwrite the menu i see when I start the PC (duel booting xp and ubuntu atm) and interfere with me trying to load Ubuntu once everything is set up? It's just I don't have a lot of places to backup my data to do clean installs of both OSes and I'd prefer not to go digging into my wallet right now :P

Cheers for any help ;)

---

### Post by SEMW on 2008-05-17
> **SuperNapalm said:**
> My question is will Vista overwrite the menu i see when I start the PC (duel booting xp and ubuntu atm) and interfere with me trying to load Ubuntu once everything is set up?

Yes, it will.  It's very easy to fix, though -- just download [EasyBCD](http://neosmart.net/dl.php?id=1) on Vista, run it, go to 'add an entry', select the Linux tab, select Type 'GRUB', and select the partition you've got Linux on (see [screenshot](http://www.technibble.com/articlecontent/2007/05/easybcd-1.jpg)), and it'll configure the Vista bootloader to give you the option to choose between Windows and Linux.

---

### Post by wolfen69 on 2008-05-17
go [HERE]("http://neosmart.net/wiki/display/EBCD/Linux") for instructions. just go to the section "Linux before Vista".

---

### Post by tjwoosta on 2008-05-17
yes installing vista will overwrite the master boot record with the default windows bootloader, but it is very simple to restore grub using the ubuntu live cd, then after if GRUB doesn't recognize your vista partition (it should because you previoulsy had xp) but you may need to manually edit your /boot/grub/menu.lst to point toward vista rather then the old xp partition (not hard)

here is a guide i used to restore grub with the live cd
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by SuperNapalm on 2008-05-17
Agrh, too many options :P
Dosn't really matter though I can read up on them tomorrow before i install Vista.

Until then, bye bye XP :D

---

### Post by SuperNapalm on 2008-05-17
Okay so I've backed up all my data onto Ubuntu and wiped XP from my system.
Can someone tell me how to add more space to the Ubuntu partition? I want to add 40-50gb and use the rest to install Vista.

EDIT: I have GParted installed but can't find a way to add more space

---

### Post by tjwoosta on 2008-05-18
in order to resize the partition you will need to use the gparted that is on the live cd because you cant alter a partition while its mounted

but with the live cd gparted you can just right click the partiiton and choose resize

---

