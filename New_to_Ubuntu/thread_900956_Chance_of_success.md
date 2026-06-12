---
title: "Chance of success?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Qebafhzn on 2008-08-25
How successful would a migration from Windows to Ubuntu would be? Both the md5 and the integrity check said "It's good," but it said it was missing some files that seemed unimportant, that could be downloaded online.

That being said, is there a chance that things could go wrong?

---

### Post by Qebafhzn on 2008-08-25
Also, in my D: drive, there is some kind of restoration file, but I don't know if it completely restores the OS, and I highly doubt that it will work on Ubuntu...

---

### Post by wpiter on 2008-08-25
Did you try the live CD? if the live CD works an installation will be succesfull.

To be on the safe side I would advise to create a restoration DVD of windows. Furthermore, if you would leave the D: partition intact you should always be able to revert back to windows, however i would still suggest using a restoration DVD.

---

### Post by Qebafhzn on 2008-08-25
Yes, the trail worked perfectly.
But how do I make a complete restoration CD of the entire Windows OS?

---

### Post by Qebafhzn on 2008-08-25
Bump.

---

### Post by stompr on 2008-08-25
A restoration disk would normally come packaged with your computer.  If you lost the first one that came with your computer, you can ask the PC manufacturer for another.

I'm under the impression that you can make a restore disk from an application in the Windows control pannel, but I've been slumming in Linux for a long time, so my Windows know-how is shady at best.

---

### Post by aloshbennett on 2008-08-26
If the live cd works fine, you shouldnt have trouble after installation. Here's a quick checklist:
1. Network
2. Sound
3. Display resolution

Do you have any software that creates the backup images? Laptops sometimes get shipped with some sort of recovery software.

Look around you. The way people are plunging in left and right, I would say chances are 100% unless you screw up something really bad.

Btw, read installation guide carefully. Especially around creating partitions (guided vs manual)

---

### Post by ntu on 2008-08-26
> **Qebafhzn said:**
> How successful would a migration from Windows to Ubuntu would be? Both the md5 and the integrity check said "It's good," but it said it was missing some files that seemed unimportant, that could be downloaded online.

That being said, is there a chance that things could go wrong?

When you say "it said it was missing some files", do you mean that it was showing you the updates to download when you are online. Nothing is 'missing' as I understand what you are saying.

---

### Post by ugm6hr on 2008-08-26
> **Qebafhzn said:**
> How successful would a migration from Windows to Ubuntu would be? Both the md5 and the integrity check said "It's good," but it said it was missing some files that seemed unimportant, that could be downloaded online.

That being said, is there a chance that things could go wrong?

You haven't explained what you mean.

When you say *migrate*, do you mean take all your files, bookmarks and emails etc from Windows to Ubuntu?

If so, I wouldn't expect too much success if you want it to be done automatically.  I have never used the *migration* tools in the Ubuntu installer, but I wouldn't ecpect them to work reliably.  Of course, these things can be migrated, but a modicum of knowledge is required.

If you are asking if an Ubuntu installation will be successful, then it depends what definition of successful you use.  Most desktop hardware works well, but laptops sometimes cause problems.  Things that can be an issue to resolve include: video drivers (most work by default, as yours appears to); sound drivers (again, most by default); ethernet drivers (99%+ default); wireless drivers (probably 60-70% by default); power-saving e.g. hibernate etc (not sure - I don't use).

It is important you know what you are getting yourself into before wiping Windows.  Make sure you do a bit of reading about Ubuntu / Linux before you remove the security blanket that is Windows.

---

### Post by shane19174 on 2008-08-26
If you're worried about losing documents, pictures, music, bookmarks, etc., just copy them all to CD/DVD or an external HD before installing Ubuntu. You should do this no matter what.

If, on the other hand, you're worried that the installation might go wrong and you'll end up without a working system:

1)That probably won't happen. Ubuntu works reliably on lots and lots of hardware. (Which doesn't mean it works on ALL hardware, of course.)

2) But you can still purchase a sort of insurance policy by doing a complete backup of your windows system, including installed programs, etc. You can do this with a program like Acronis True Image, which can boot from a live CD, backup your partition(s) to an external hard drive, and which can backup linux systems too. (Not trying to advertise here, but it's the software I know and use. Occasionally an older version is made available free in computer magazines, and you might even be able to find one on the web. That being said, the older versions may have problems with newer hardware, SATA in particular. Alternative programs would be Norton Ghost and, more in the spirit of open source, the SystemRescueCD, a linux live CD with the program Partimage. The latter seems the most promising to me, but I haven't tested it. SystemRecueCD can be found here: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)).

With such a backup, you can restore your Windows system just as it is if you need or want to.

Hope this helps,
Shane

---

