---
title: "[SOLVED] How to get broadcom drivers to work?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by keiichidono on 2008-07-13
I want to know how i can get the broadcom drivers to work in Linux because i got a friend interested in Ubuntu and she has a Dell Inspiron B130. I wanted to know how i can get wireless working, i heard it was easy but i just want to know in preparation for the installation tomorrow. We have access to a DSL modem so using internet resources isn't a problem. Thanks for any help.

---

### Post by TSS on 2008-07-13
I can at least tell you that you will have some way of getting wireless working.

If you look at this guide ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) you can see that two other people with that computer had success getting the Broadcom card to work.

There are other ways which might be better, like using the firmware cutter, but at least you know you have one option through ndiswrapper.

---

### Post by falcon61102 on 2008-07-13
I've found ndiswrapper to work best.  That guide is great, it's what I've used to get mine going.  If she has any trouble with the guide just post and we'll be able to figure it out.

---

### Post by keiichidono on 2008-07-13
I heard fwcutter is good, can i get some instructions for that too? Thanks guys, i really appreciate it. She really loves Linux so i don't want to crap up on her.

---

### Post by falcon61102 on 2008-07-13
Sorry, I haven't used fwcutter... I've had some good success with people with the HowTo LSS posted but haven't had to you fwcutter.

---

### Post by angelsguitar on 2008-07-13
I'd recommend this guide.  It helped me setup a friend's computer:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by redoscar3 on 2008-07-13
I googled your friend's Dell computer and suspect it uses the Broadcom 4318 wireless chipset.  I run an Acer Aspire AS-3003 laptop with the same chipset.  Before Hardy, I had the best luck when using ndiswrapper and the Windows driver.  However, with Hardy I find the b43 driver and fwcutter to do an excellent job and I think that suspend and hibernate now work better because of it.  This is only my experience over the past couple of years when I first installed Dapper on the Acer, then to Edgy, and now satisfactorily using Hardy.  Hopefully you also have a good experience on the Dell with Hardy.

Red

p.s. For me, the installation of the b43 driver was pretty automatic through the "restricted drivers" manager.  I just clicked through, rebooted, configured the wireless and I was online in a jiffy.

---

### Post by keiichidono on 2008-07-14
Thanks guys, wish me luck! :D

---

