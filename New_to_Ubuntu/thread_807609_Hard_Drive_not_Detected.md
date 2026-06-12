---
title: "Hard Drive not Detected"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by SurrealWraith on 2008-05-26
For school, I bring to my classes and use a Lenovo IBM Thinkpad T60.  Unfortunately, my high school's Tech Department has informed the Deans that freeware, sharewere, and opensource software is all illegal(quite similarly to Comcast's logic that all torrents are illegal), and I am therefore not allowed to run Ubuntu at school. 

While I have a working Windows serial, Windows installation disks do not recognize there being a hard drive.  I have partitioned and formatted the the hard drive in FAT, FAT32, and NTFS, yet it is still not recognized.  I tried to see if there was anything in my BIOS that would account for this problem, but it appears that my father set a password on the BIOS, which he has now forgotten.  How can I get the Windows installation to recognize the hard drive so I can dual-boot, and if this requires accessing my BIOS, how can I reset my password? 

Thank you in advanced for your help.

---

### Post by daberger on 2008-05-26
i would recomend getting windows in some way, backing up all ur data, installing windows and then dual booting with wubi as windows master and ubuntu slave

---

### Post by bumanie on 2008-05-26
To reset a passworded bios  - on a desktop, one removes the cover and then remove the button cell battery from the motherboard and then change the jumper setting for a couple of minutes before returning the jumper back to what it was and re-inserting the button cell battery. How easy this is to get to on a laptop, I can't say as I have never tried, but the process should be the same if you can get to the motherboard.
By the way, open source is not illegal, the only time any illegality comes into question is when one installs some proprietary codecs/or css codes to decrypt dvd's. Every dvd player in the world has css code breakers, otherwise they would not be able to read the discs. may be you should get the Deans to look at Sue me first microsoft at [http://digitaltippingpoint.com/wiki/index.php?title=Sue_me_first%2C_Microsoft](http://digitaltippingpoint.com/wiki/index.php?title=Sue_me_first%2C_Microsoft)
The state of legality/illegality is dubious.

---

### Post by SurrealWraith on 2008-05-26
> **bumanie said:**
> To reset a passworded bios  - on a desktop, one removes the cover and then the button cell battery and then change the jumper setting for a couple of minutes before returning the jumper back to what it was and re-inserting the button cell battery. How easy this is to get to on a laptop, I can't say as I have never tried, but the process should be the same if you can get to the motherboard.

Why didn't I think of this?  I feel really stupid now, especially having replaced these batteries in computers, my Sega Saturn, and even my NES cartridges.  Wow.  Thanks a lot; I will try this and report on the inevitable success.

---

### Post by Wim Sturkenboom on 2008-05-26
Dear SurrealWraith,

Can you get your hands on the exact text that was given to the deans? In my opinion, it's your laptop and you can do with it what you want (within the limits of the applicable law in your country of course).

How do you use it at school? Do you connect it to the school's network. In that case, I think that the Tech Department has the right to say that they will only allow Windows systems on their network (with a good motivation of course). If you use it stand alone, there's nothing that the Tech Department can do (my opinion).

To solve your HD problem, the follwoing might help:
I recently was asked to fix a (3 month old) laptop (Dell M2300) where the HD was recognised by Vista, Slackware and Ubuntu but not by XP. It turned out that XP needed a special driver if something called ***AHCI*** was enabled in the BIOS. As the driver was not available at that moment, the user opted to disable AHCI and could install XP.
This might do the trick for you as well.

---

### Post by daberger on 2008-05-26
> **Wim Sturkenboom said:**
> Dear SurrealWraith,
How do you use it at school? Do you connect it to the school's network. In that case, I think that the Tech Department has the right to say that they will only allow Windows systems on their network (with a good motivation of course). If you use it stand alone, there's nothing that the Tech Department can do (my opinion).

if you do connect to a schools network that only allows windows it would be no problem to buy a cheap network adapter (i got one for 30 bucks) and run the software with wine.

and interestingly enough,bumani, even though microsoft has a lawsuit against linux, dell.com sells computers running ubuntu and DOS. hmmm . hypocracy  much?

---

### Post by SurrealWraith on 2008-05-26
> **Wim Sturkenboom said:**
> Dear SurrealWraith,

Can you get your hands on the exact text that was given to the deans? In my opinion, it's your laptop and you can do with it what you want (within the limits of the applicable law in your country of course).

How do you use it at school? Do you connect it to the school's network. In that case, I think that the Tech Department has the right to say that they will only allow Windows systems on their network (with a good motivation of course). If you use it stand alone, there's nothing that the Tech Department can do (my opinion).

To solve your HD problem, the follwoing might help:
I recently was asked to fix a (3 month old) laptop (Dell M2300) where the HD was recognised by Vista, Slackware and Ubuntu but not by XP. It turned out that XP needed a special driver if something called ***AHCI*** was enabled in the BIOS. As the driver was not available at that moment, the user opted to disable AHCI and could install XP.
This might do the trick for you as well.

Firstly, no text was ever submitted to the deans.  It was all communicated verbally.  And no, I do not connect, nor do I have access to the school's network from my laptop, unless of course I were to crack the password.  However, a friend of mine was "caught" with a freeware file-deleter program on his external hard drive, which was then confiscated by the Tech Dept., followed by the Deans issuing a new rule baring students from bringing external hard drives into the building.  Also, by the logic of my Deans, if you are seen in a picture containing a red cup, you will face immediate suspension, no questions asked, as the only beverage that can possibly be contained by a red plastic cup is beer.  Frankly, it isn't worth arguing with the Deans and school district anymore, because I'm tired of getting detentions for being "overly defient".

Anyway, your idea for fixing my hard drive makes enough sense, I'll go ahead and give it a try as soon as I can get into my bios.  Thanks.

---

