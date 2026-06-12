---
title: "ISO's wont burn"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-03-15
I have downloaded about 15 different variants of Linux (most Ubuntu based) and have tried to burn them onto a CD or DVD to install. I have tried burning with Xfburn and Brasero in Ubuntu and Lubuntu and Nero and Windows burner in Windows 7. All applications have shown that they were burning the image onto the disc, but when I try to load off of the disc it says operating system not found. Loading the disc back into any running OS shows that I have inserted a blank disc. 

Can anyone give me some guidance on how to burn an iso and be successful. I have done this many years ago the first time I tried Linux. I never had any problem doing this until this last week.

---

### Post by chipbuster on 2012-03-15
Well the simple answer here is that you might have been doing simulated burns the whole time. Given your experience and multiple programs though, I feel like that might not be likely. just make sure you haven't been setting the burning program to "slmulate."

What type of disc are you using? Is the burner rated for that disc? CD-R burners sometimes don't make a scratch on CD-RW media. Have you tried it with a different drive?

---

### Post by Rodney9 on 2012-03-15
You are using 'Burn Image' as shown in the pic below.

It maybe the media, try a different brand or slow it to slowest burn speed.

As already said try different hardware .

Rodney

---

### Post by theducksfan2010 on 2012-03-15
No, I have made sure it was not on simulated burn, this has been across multiple burners on multiple machines, and with over 4 different brands. Yes I was clicking on the same button as in the .jpg, and this problem is only burning ISO's, these same discs work just fine for burning data and music.

---

### Post by ixtok on 2012-03-15
Sounds like your cd burner is bad after trying all those different programs. Can you copy a file onto a blank cd?

---

### Post by chipbuster on 2012-03-15
-Multiple machines
-Multiple media
-Multiple programs

-Does not work for Linux ISO (disc is not burned at all)
-Works fine for any other media

My only conclusion is that there is a vengeful Microsoft ghost in your house. Perhaps attempting to appease it with a friendly-looking paperclip will cause it to leave.

---------------------
Really though, I can't think of what might be causing your problem. The only suggestion I have is to attempt to burn the iso with the dd utility, although this is unlikely to succeed given what you've already tried.

---

### Post by roger_1960 on 2012-03-15
Hi

You are not by any chance formatting the discs (you shouldn't) before you try to burn the iso?  Long shot but I can't think of anything else.

---

### Post by winh8r on 2012-03-15
Firstly, you should be able to tell if there is anything on the disk just by looking at it , a new disk has a uniform appearance across the entire surface, whilst a disc containing data has darker areas.

Secondly, md5 checksums will confirm the integrity of the downloaded iso before you burn it:

See here for details: [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

You need to burn the** contents** of the iso to the disc, not just the iso, when it is complete you should see numerous directories on the disc and not just a single iso file.


Make sure your machine is actually booting from the correct drive also.


check here for further info: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by theducksfan2010 on 2012-03-15
Make sure your machine is actually booting from the correct drive also.


check here for further info: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")[/QUOTE]yes the burners work for other items (mp3s, data files etc), the ISO's are complete (work from USB), abd the drive will boot when I insert a valid bootable cd/dvd. 


The discs that are being burned are on blank discs and come out blank (can tell looking at back).

How do you burn a ISO in a windows partition using dd in Linux??

Yes I am burning the contents,

---

### Post by gscratch on 2012-11-02
again, just another wild idea:  you've said "burning" several times.  Are you sure you're instructing your burning program to create an ISO disk?  My "CD Burning" program had a different command (menu choice) to create a ISO disk and it was different just 'burning' files onto a CD.  For example, there should NOT be a choice to "make this CD bootable"

---

### Post by squakie on 2012-11-02
> **winh8r said:**
> ....

You need to burn the** contents** of the iso to the disc, not just the iso, when it is complete you should see numerous directories on the disc and not just a single iso file.

.....




Sure you don't want to reword that?  I know where you are coming  from, but you burn the ISO only - the files are part of the image ;)

---

### Post by squakie on 2012-11-02
Also, it's been kind of a rule for me to not burn to a CD-RW or DVD-RW.  I've just never had much luck with the linux ISO's being burnt to those.  Also, I'm sure you already know, but things like the 12.10 ISO need to go on a DVD - it's too big for a CD.

---

### Post by sammiev on 2012-11-02
Do you have a USB thumb drive to test? Just a suggestion. :)

---

