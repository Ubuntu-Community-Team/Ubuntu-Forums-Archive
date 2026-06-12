---
title: "Unable to disable a graphics card in 11.10"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by Aaronneyer on 2011-11-14
I'm currently trying to set up Ubuntu for a friend but I'm running into a problem. He has an HP Pavilion dv6 with two graphics cards, a lower power intel, and a high performance ATI card.  Both of his cards are powered on, leading to the fan constantly running and the computer getting very hot.
I need to be able to turn off one of the graphics cards, but I am unable to.
I have tried using command such as:
echo OFF > sudo /sys/kernel/debug/vgaswitcheroo/switch
echo DDIS > sudo /sys/kernel/debug/vgaswitcheroo/switch
echo DIGD > sudo /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > sudo /sys/kernel/debug/vgaswitcheroo/switch
but none of them worked and both remain powered on. None of these had any effects.

I had a similar problem on my computer(HP Pavilion dv7 with dual graphic cards).  I tried many different things to fix mine but what seemed to fix it in the end was
echo DDIS > sudo /sys/kernel/debug/vgaswitcheroo/switch
followed by a reboot.  I tried this on his but was unsuccessful.

Does anybody know of a way to fix this?
Any and all help is appreciated.
Thanks,
~Aaron Neyer

---

### Post by Aaronneyer on 2011-11-15
Ok, I've solved the problem.

For his, we followed the instructions here: [http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html](http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html)
I tried doing that for me after a fresh install and it didn't work.  For mine I added:
"echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" to /etc/rc.local
and typing "echo DDIS > sudo /sys/kernel/debug/vgaswitcheroo/switch" in the command line and then rebooting.

After this however, I ran into another problem.  He is able to edit Compiz with CCSM, and change settings, but none of these work for me.  Also, certain unity things such as moving windows with Ctrl + Alt + Numpad(1-9) work for him but not for me.
We are both running Unity 2D.

---

### Post by Jacobonbuntu on 2011-11-15
....you can probably disable the card in the bios settings?
(if it is an onboard card)

---

### Post by Aaronneyer on 2011-11-15
I had tried that and was unsuccessful, but as I said in my previous post, I've already gotten the graphics card disabled.  Now I'm trying to figure out why CompizConfig and other things don't work on mine, while they do work on my friends.

---

### Post by Jacobonbuntu on 2011-11-17
...probably not of any help, but are you sure you use the right (proprietary) graphics driver? I can imagine something went wrong with initially having 2 cards active

---

### Post by Mark Phelps on 2011-11-17
> **Jacobonbuntu said:**
> ...probably not of any help, but are you sure you use the right (proprietary) graphics driver?
If the OP was running the wrong proprietary drivers, they would know that because their display would be trashed.

>  I can imagine something went wrong with initially having 2 cards active

That's not the case with Ubuntu.  It doesn't have both cards active; it has only one.  And, since these PCs generally do NOT provide a way in the BIOS to disable either of the cards, Ubuntu only installs drivers for the "first" card/chipset it sees.

You have to run the complicated script included in the link to disable the card you don't want to use.

---

### Post by Jacobonbuntu on 2011-11-17
> **Mark Phelps said:**
> If the OP was running the wrong proprietary drivers, they would know that because their display would be trashed.



That's not the case with Ubuntu.  It doesn't have both cards active; it has only one.  And, since these PCs generally do NOT provide a way in the BIOS to disable either of the cards, Ubuntu only installs drivers for the "first" card/chipset it sees.

You have to run the complicated script included in the link to disable the card you don't want to use.

I see, but what I meant was that the proprietary driver was not installed at all, which could limit the functionality. Didn't know about this PC, as my (older) PC's with onboard cards, they can be turned off in the bios

---

### Post by Mark Phelps on 2011-11-18
> **Jacobonbuntu said:**
> I see, but what I meant was that the proprietary driver was not installed at all, which could limit the functionality.
That's true -- but there is no such driver for Intel chipsets, and my guess would be, since that video chipset is running most of the time (at least, in Windows), it's most likely the one that Ubuntu found and installed drivers for.

>  Didn't know about this PC, as my (older) PC's with onboard cards, they can be turned off in the bios
Again ... true.  It's only the newer PCs, especially the ones with "switchable graphics" in which the OEMs specifically disable the ability to enable/disable video in the BIOS.  The feature is designed to automatically switch between graphics chips on the basis of the demand, so my guess is, that the OEMs do not want the buyers to be able to turn this off -- which is why I would never buy such a PC.

---

### Post by Jacobonbuntu on 2011-11-18
> **Mark Phelps said:**
> That's true -- but there is no such driver for Intel chipsets, and my guess would be, since that video chipset is running most of the time (at least, in Windows), it's most likely the one that Ubuntu found and installed drivers for.


Again ... true.  It's only the newer PCs, especially the ones with "switchable graphics" in which the OEMs specifically disable the ability to enable/disable video in the BIOS.  The feature is designed to automatically switch between graphics chips on the basis of the demand, so my guess is, that the OEMs do not want the buyers to be able to turn this off -- which is why I would never buy such a PC.

Thanks!

edit: but which card is turned of? he also has an ATI high performance card?

---

### Post by Mark Phelps on 2011-11-19
> **Jacobonbuntu said:**
> Thanks!

edit: but which card is turned of? he also has an ATI high performance card?

I have no way of knowing that ... but as I said earlier, my guess is that Ubuntu only configures drivers for the Intel chip.

The script in the link provided probably turns off the Intel chip so that Ubuntu will then see the other card -- and install drivers for that.

---

### Post by jockyburns on 2011-11-19
Why not take a screwdriver in hand and physically remove the graphics card you don't want to use? (or is that too simple?) At least you'll know it's not producing any heat into the insides of the computer. ;);)

---

### Post by jocheem67 on 2011-11-19
To get a grip on the issue one should really inform himself. We're talking hybrid graphics here and both AMD and nvidia use this technique on intel-based motherboards. 
A startingpoint is this link:

[http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page)

I'm using acpi_call on a dell xps15. It all requires some linux-knowledge and is not something to do without some good reading first. The developing of all the different methods is a bit fragmented and it's a bit of a hassle to learn what the best method is atm. So be warned...

---

### Post by Jacobonbuntu on 2011-11-19
[QUOTE=Mark Phelps;11471052 ...Ubuntu will then see the other card -- and install drivers for that.[/QUOTE]

As OP seems not to be around anymore, I take my chance to learn something (if it is ok wit you :) ), but are you sure? when I install Ubuntu, the proprietary drivers are never installed by default (Nvidia)

---

