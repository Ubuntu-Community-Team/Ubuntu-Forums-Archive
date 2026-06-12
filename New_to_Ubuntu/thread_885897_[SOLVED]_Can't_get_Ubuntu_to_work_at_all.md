---
title: "[SOLVED] Can't get Ubuntu to work at all"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Keshi135132518 on 2008-08-10
Hey,

I have a HP Pavilion A1020 AMD 64bit 3200+ MHz/ desktop computer, with Windows XP currently installed in it as the main operating system. 

I first downloaded Ubuntu 8.04 LTS Desktop Edition (64-bit) in June of this year and burnt it as an iso image on a blank disk. First few times I tried it out booting from the CD to run the live sessions and it was working fine. Then, I started getting these SQUASHFS errors that look kind of like this:

[   205.7485735]SQUASHFS error: unable to read page, block led01853, size a4e3
[   205.7485735]SQUASHFS error: sb_bread failed reading block 0x7b42f

(or something like that) These errors just keep on going. But sometimes, it would actually load, and eventually I managed to get it installed. Except, I didn't install it properly and I had trouble booting the computer. I couldn't reinstall xp either. So, I took my computer to the shop to get it repaired. Turns out one of the wires was broken, so we got it fixed and I got my computer back (without any operating system on it). I tried to reinstall Ubuntu again but it didn't work, so I installed xp instead because I was just so desperate to get back on the internet. Everytime I go to install Ubuntu, I get the same errors. I change the BIOS settings, I still get the same errors. I change the ACPI settings, the numbers in the errors turn into zeros so it looks something like this:
  
[   000.0000000]SQUASHFS error: unable to read page, block led01853, size a4e3
[   000.0000000]SQUASHFS error: sb_bread failed reading block 0x7b42f
[   000.0000000]SQUASHFS error: unable to read page, block led01853, size a4e3
[   000.0000000]SQUASHFS error: sb_bread failed reading block 0x7b42f
[   000.0000000]SQUASHFS error: unable to read page, block led01853, size a4e3
[   000.0000000]SQUASHFS error: sb_bread failed reading block 0x7b42f
[   000.0000000]SQUASHFS error: unable to read page, block led01853, size a4e3
[   000.0000000]SQUASHFS error: sb_bread failed reading block 0x7b42f

I have downloaded the normal version, the 64-bit, and the alternate versions of Ubuntu, but I am unable to install any of them. I ordered the disk and I received it in July, but even that one won't work. If I check any of the disks for errors, they all say 3 errors! I can't get the live session to work and I can't install it. The icing on the cake is, I could install it on my friend's computer, even thoguh they have the same computer as me! 

I have tried everything and I am really out of ideas. I do not wish to have Windows XP as my main operating system. It has no sound at all, the stanby function is gone and it's missing a lot of the programs it originally came with since i reinstalled it. So keeping XP is not an option. I have browsed various threads on this forum and have tried many suggestions but none of them have worked so far. 

I don't know how much of this information is relevent or necessary, but I think that's everything.

Any help at all would be much appreciated :)

---

### Post by alzie on 2008-08-10
First thing I'd do is run a cd cleaner in the drive (if you have one) and check the CDs for scratches.

I did a search and the only thing I could find that sounds similar to your case is this one: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=870184](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=870184)

They resolved the problem by going into the BIOS and changing the DMA settings for the CD drive.

It seems very odd that your computer says all 3 CDs have 3 errors.

I hope this helps.

---

### Post by Crafty Kisses on 2008-08-10
Not sure if you ran a md5 check yet, check if everything comes out OK, if I were you I'd burn another CD off of a different mirror and if that doesn't work, do the drive cleaner.

---

### Post by InfinityCircuit on 2008-08-10
This definitely sounds like a hardware problem if all three of these disks failed for you.  I would recommend returning it to the shop and complaining that they didn't fix the problem.

---

### Post by Keshi135132518 on 2008-08-10
I've burned several of them using different burners and all at x4 or less. But even the one I ordered from Canonical says 3 errors? they all seem to work fine on other computers but none of them work on mine...

I don't think the drive is dying because I had my computer serviced only last month and I can still successfully install XP from the disk. I had this problem before I took it to the shop to get it fixed as well, so I don't think it has anything to do with the shop.

---

### Post by Crafty Kisses on 2008-08-10
> **Keshi135132518 said:**
> I've burned several of them using different burners and all at x4 or less. But even the one I ordered from Canonical says 3 errors? they all seem to work fine on other computers but none of them work on mine...

I don't think the drive is dying because I had my computer serviced only last month and I can still successfully install XP from the disk. I had this problem before I took it to the shop to get it fixed as well, so I don't think it has anything to do with the shop.

If you want Ubuntu really bad and can't seem to do it with the CD you could always try Wubi.

---

### Post by Keshi135132518 on 2008-08-10
> **alzie said:**
> First thing I'd do is run a cd cleaner in the drive (if you have one) and check the CDs for scratches.

I did a search and the only thing I could find that sounds similar to your case is this one: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=870184](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=870184)

They resolved the problem by going into the BIOS and changing the DMA settings for the CD drive.

It seems very odd that your computer says all 3 CDs have 3 errors.

I hope this helps.

I have no idea where the DMA settings are! 

I put the CD in, I go into "Try without installing" and the Ubuntu thing comes up, the orange bar starts moving up and down, and I can hear the CD loading for like, 10 seconds, and then it just stops altogether and the computer goes really quiet, then the errors come up after about 3 minutes. :S

---

### Post by alzie on 2008-08-10
At the Ubuntu start screen,  press F6 once and you should see a section "boot options" in white near the bottom of the screen.  Use the backspace or delete key to remove "quiet splash" from that line.

That will show what all is being installed when you startup.  Hopefully we can identify the problem that way. 

We still want to use "Try Ubuntu without making changes"

---

### Post by Keshi135132518 on 2008-08-11
Ahhh... I downloaded Ubuntu 7.04 and after a few attempts I managed to get it working and successfully install it! It seems that my computer just didn't like 8.04...

Thank you to everyone who tried to help though.

---

### Post by tekorei on 2008-08-23
Hi all, It seems that you solved your problem, anyway I wan to add that I had the same error when trying to install Ubuntu, I checked the ISO, checked the cd burned but always got an error. I ordered the original CD and the same problem. So I tried swapping my DVD-Drive (LG) for another one and the problem dissapeard. It seems that my DVD-Drive had problems reading the CD

---

### Post by durand on 2008-08-23
> **Keshi135132518 said:**
> Ahhh... I downloaded Ubuntu 7.04 and after a few attempts I managed to get it working and successfully install it! It seems that my computer just didn't like 8.04...

Thank you to everyone who tried to help though.

If you want to, you can upgrade to hardy from there. I found this guide with google. You can't go straight to hardy because you are a version out.

[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Upgrade+Ubuntu+Server+from+Feisty+(7.04)++to+Hardy+(8.04)/b434c](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Upgrade+Ubuntu+Server+from+Feisty+(7.04)++to+Hardy+(8.04)/b434c)

---

