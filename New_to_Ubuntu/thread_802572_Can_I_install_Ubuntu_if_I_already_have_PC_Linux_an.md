---
title: "Can I install Ubuntu if I already have PC Linux and Windows XP installed?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sashag on 2008-05-21
Hi

I was wondering if I can download the new Ubuntu 8.04 onto my computer if I already have PC Linux and Windows XP installed?
I have the live CD version of both PC Linux and Ubuntu. I started
to download Ubuntu, but stopped when I got the pop up window that said that everything would be wiped out if I used the partition function. I also tried downloading Ubuntu inside my Windows XP OS, but I got the popup window that said that I didn't
have enough room to run it alongside Windows XP. I'm guessing
that when I installed PC Linux and Windows XP, I didn't leave enough room to download any other OS.

Is there a way to do this without affecting either PC Linux or Windows XP? I especially don't want to mess up Windows XP, as I have already had to reinstall it three times in the last few weeks after playing around with various Linux OS. Thanks.

---

### Post by kk0sse54 on 2008-05-21
Yes it's possible to create another partition and then use the swap partition from PC Linux for both that and Ubuntu. For more on Multi-Boot with more than one OS go [Here]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by FreewheelinFrank on 2008-05-21
How big are the existing partitions and how full?

---

### Post by SunnyRabbiera on 2008-05-21
Yes, triple booting is possible, though I hope you have room for it.

---

### Post by phidia on 2008-05-21
You need to use the alternate cd image. The alternate cd will allow you to install without changing your grub set up.
You also will need to figure out which partitions xp and your other linux is on and see how much free space you can claim for ubuntu. 
Some of the how tos [here]("https://help.ubuntu.com/community/CommonQuestions") may be useful.

---

### Post by pdtpatrick on 2008-05-21
Tripping booting on one harddrive - i wouldnt recomment it so much just because if that harddrive goes bad, you not only lose one os, but you lose all three. Anyway - check your partition table and see how much space you have and whats using what. Then resize accordingly and install the OS. GRUB should be able to display all three at boot time to allow you the opportunity to select which to boot to. 

Make sure you have an external harddrive that you save all your documents to just incase.

---

