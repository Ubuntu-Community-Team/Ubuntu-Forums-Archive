---
title: "How to install Xp on a Ubuntu (ext2) formatted HD?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by amilo si1520 on 2008-11-26
Hey,

I am trying to install XP again on my laptop, but under the setup I take this message: 

"Setup did not find any hard disk drives installed in your computer.
Make sure bla bla bla bla bla"

I guess this is happening because the hard disk is ext2 or ext3 formatted so probably XP Setup won`t recognize it.

If anyone could help me it will be really appreciated!








No one that brings irony and swears is welcomed to reply!

---

### Post by Paqman on 2008-11-26
You probably have a SATA hard drive. XP can't detect or use SATA drives by default. There's two ways around this:

[LIST=1]
[*]If you have a SATA driver disk then you when Windows says "Press F6 to add a SCSI driver", do so and load you driver off the floppy. You might be able to get SATA drivers off the manufacturer's website.
[*]You may be able to go into your BIOS and set your hard drive to legacy mode. Look for something that will switch the drive from AHCI to IDE or legacy mode.
[/LIST]

The other option is get your hands on an XP disk with the latest XP service packs slipstreamed into it. You can possibly make one yourself, but it's pretty involved. The latest service packs introduce SATA support into XP.

---

### Post by amilo si1520 on 2008-11-26
Man, thank you very much for the very real help!

It is exactly as you said it, a SATA HD.

I was going to press that F6 but I dont have a floppy on my laptop.

For the moment the drive is in auto mode. I will try it now in IDE mode, maybe it works.

By "the lastest service packs" you mean SP2, or SP3?

Thank you once again!

---

### Post by louieb on 2008-11-26
> **amilo si1520 said:**
> No one that brings irony and swears is welcomed to reply!
:lolflag:Sorry but just can't help myself. You would not go to windows forum and ask them how to install Linux.  (or maybe you did who knows). Anyway from the fine folk in Redmond   [Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by amilo si1520 on 2008-11-26
TO louieb:

Using irony just to show of (which is why people like you do it) makes you people look realy realy realy stupid.

I say this because Paqman which did not used irony but showed understanding, gaved the solution directly by localising the problem to the SATA HD. Fix that, you are done! This was the help I was looking for.

Now, lets analyise a litle bit what was that you said: 

"You would not go to windows forum and ask them how to install Linux."

if I had Linux installed before and then I installed Windows and then I want to install Linux again but because of the installation of Windows this seems to be impossible or complicated, why not asking in a Windows users forum? Why not? Why?

So why not asking in a Linux users forum about a problem that it could have beeing related with the fact that the OS of the unit which I am trying to sett up is actually a Linux OS, Ubuntu? Why not? Why?

You also "(or maybe you did who knows)"

Now I say, maybe YOU done this, WHO KNOWS? Since that you are giving it as a possibility.. It was not at all in my mind, but it was in yours since that you wrote it here.. So

But lets see now your skills: "Anyway from the fine folk in Redmond Remove Linux and Install Windows on Your Computer"

[Edited by staff for foul language]

now help your self understanding this..

TE QIFSHA MOTREN!

---

### Post by markjensen on 2008-11-26
amilo, calm down.   Louie found that little line amusing (and it was), and you go and call him "stupid" and swear at him???

Seriously, you are getting worked up and angry over nothing.

---

### Post by amilo si1520 on 2008-11-26
markjensen: "you are getting worked up and angry over nothing."

when you have a problem and need help but instead of that you have to deal whith irony, is this nothing?

even if I was wrong about asking about my problem in this forum, which I was not because i took the right help with the very first answer (Paqman thanx man!) so even if I was wrong, who knew everything since he/she was born? 

I am out of this!

AA louieb you are from Texas? OBAMA FOR LIFE! WE LIKE HIM VERY MUCH HERE IN ALBANIA! MUCH SMARTER THEN THAT LAST ONE FROM TEXAS! HAHAH

---

### Post by sdennie on 2008-11-26
Thread closed.  This problem has been solved and there is no reason to turn it into a shouting match.

---

