---
title: "Borked XP"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by tompickles on 2008-04-24
I used the new 8.04 LIve CD to resize my XP partition, and now it wont boot - it exists in the boot loader menu - but as soon as windows starts to boot (the scrolling thingy) it reboots itself - what do i do?! really need it back as ubuntu still isnt 100% reliable and XP was a pain to install.

---

### Post by Mazza558 on 2008-04-24
Can you access Safe Mode?

---

### Post by tompickles on 2008-04-24
nope - same thing happens then too.

---

### Post by Mazza558 on 2008-04-24
Did you defragment your XP partition before trying to resize? I've seen nasty things happen like this when you don't - files at the end of the partition get "cut off" sometimes.

---

### Post by tompickles on 2008-04-24
argh - dammit! i forgot to do that! shall i try a repair install on teh xp partition? if so, will it ask me for my licence key, cos i dont know where that is, and will it destroy GRUB? how do i reinstall grub?!

---

### Post by Paqman on 2008-04-24
Hmm, when you resized the XP partition did you defrag it first? And has it got enough free space. Windows will need several gigs of free space.

Otherwise, hit F8 during boot and try everything in there. If it boots run scandisk and defrag. If that doesn't work you might be looking at a repair install or reinstall.

---

### Post by Paqman on 2008-04-24
> **tompickles said:**
> how do i reinstall grub?!

[Easy peasy](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tompickles on 2008-04-24
oi think it has enough free space - about 8GB! so, i think i just borked it by not defragging - will try a windows repair install tomrrow - at least hardy seems to be working fine! but, you know how it is with windows - its there and you gotta have it boot at least

---

### Post by tompickles on 2008-04-24
is this repair install going to ask me for my product key - cos i dont actually know it

---

### Post by bvanaerde on 2008-04-24
> **tompickles said:**
> is this repair install going to ask me for my product key - cos i dont actually know it

Normally, no. This is only asked on a fresh installation, if I remember it correctly.
But I haven't had much success using the repair function... hope you have better luck.

---

### Post by tompickles on 2008-04-24
argh - BUGGER it! i dont want to do a reoinstall, and have to call up microsoft and explain that my system wont boot!

---

### Post by Paqman on 2008-04-24
> **tompickles said:**
> is this repair install going to ask me for my product key - cos i dont actually know it

Er, not sure. Possibly not.

[This page](http://support.microsoft.com/kb/315341) on the Microsoft Knowledge Base gives the not-particularly-helpful:

"After you repair Windows XP, you may have to reactivate your copy of Windows XP."

Which seems annoyingly non-committal, to me.

---

### Post by Zralou on 2008-04-24
Try hitting F8 at boot, then try "last known good configuration".

Sara Lou

---

### Post by bigken on 2008-04-24
what type of disc do you have ie system restore or oem if you have a oem and its a dell pc 
it does not ask for the key nor do most other oem installs but you have to activate windows good luck

you could also try using the[ UBCD]("http://www.ultimatebootcd.com/download.html") for windows and restore the registry

---

### Post by tompickles on 2008-04-25
> **Zralou said:**
> Try hitting F8 at boot, then try "last known good configuration".

Sara Lou

None of the options work - this screen loads auto matically.

I have just an oem i think. ill give it a whirl tonight, and if i need to re-activate, ill cross that bridge when it comes to it. id rather use the windows repair disk first, as i really dont know what im doing with UBCD, and if ive just wiped some windows :lolflag: then i need to fix missing DLLs etc.

:(

---

### Post by bigken on 2008-04-25
try this 1st in the recovery console 

chkdsk /p /r

---

### Post by tompickles on 2008-04-25
> **bigken said:**
> try this 1st in the recovery console 

chkdsk /p /r

is this from ubuntu or the windows XP Cd.
What does it do?

---

### Post by bigken on 2008-04-25
:rolleyes: windows :lolflag:

The CHKDSK /P command is diagnostic only...it performs and exhuastive check of the drive, but does not make any changes to the drive. In otherwords, it doesn't fix anything.

Now, on the other hand, the CHKDSK /P /R will locate bad sectors and recover readable information.


boot from your windows cd when you get to the setup screen or install press R to enter the recovery console select your windows partition usually 1 then you will be asked for the administrators password again hit enter at the prompt type the chkdsk /p /r if this does not fix your problem then go for a repair install

---

### Post by tompickles on 2008-04-25
bigken - thank you! you saved my XP partition. This worked an absolute treat, and has saved me the hours of doing a repair/or even a clean install. XP runs a bit sluggish (surprise surprise) but, ill try it after reboot - but i think this will probably be to having to defrag and a smaller partition.

thank you! :biggrin:

---

### Post by bigken on 2008-04-25
no probs pleased your sorted we are here to help each other

---

### Post by tompickles on 2008-04-26
I would mark this thread as [solved] but can't find the button :(

---

