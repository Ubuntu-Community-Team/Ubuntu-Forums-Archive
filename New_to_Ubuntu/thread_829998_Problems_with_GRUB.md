---
title: "Problems with GRUB"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by kugelinis on 2008-06-15
Hello! As we all know Ubuntu is very and very nice, but i have problem.... So, i wanted to make triple boot with ubuntu, osx and windows... But i made mistakes at partitioning, so i don't know how to write grub's menu.lst correctly (now i have windows and ubuntu booting) i want to make osx partition bootable... Here is my setup: [http://img395.imageshack.us/my.php?image=screenshogtzv0.png](http://img395.imageshack.us/my.php?image=screenshogtzv0.png)
And here is my menu.lst. (TXT for that, because there can be attached only txt...)

Please, don't laugh so much :) If you guys can't help me, i will shoot myself :D

---

### Post by mikewhatever on 2008-06-15
Do you get any errors when trying to boot OSX?

---

### Post by Biggy on 2008-06-15
Try to install Startup-Manager from Applications >Add/remove
or download and burn [SuperGrub Disk]("http://supergrub.forjamari.linex.org/") to fix grub.

---

### Post by meierfra. on 2008-06-15
> Do you get any errors when trying to boot OSX?
I'm pretty sure that the OP gets Grub Error 12 (Since grub cannot apply "makeactive" to  logical partition)

Anyway, according to this thread

[URL="http://ubuntuforums.org/showthread.php?p=5184447"]
http://ubuntuforums.org/showthread.php?p=5184447[/URL]

one should NOT boot OSX from the Grub menu.

---

### Post by kugelinis on 2008-06-15
> **meierfra. said:**
> I'm pretty sure that the OP gets Grub Error 12 (Since grub cannot apply "makeactive" to  logical partition)

yes you're right i'm getting the 12error.... jeez, i wanted to get it.... some people got it :)

---

### Post by linfidel on 2008-06-15
> **kugelinis said:**
> Hello! As we all know Ubuntu is very and very nice, but i have problem.... So, i wanted to make triple boot with ubuntu, osx and windows... But i made mistakes at partitioning, so i don't know how to write grub's menu.lst correctly (now i have windows and ubuntu booting) i want to make osx partition bootable... Here is my setup: [http://img395.imageshack.us/my.php?image=screenshogtzv0.png](http://img395.imageshack.us/my.php?image=screenshogtzv0.png)
And here is my menu.lst. (TXT for that, because there can be attached only txt...)

Please, don't laugh so much :) If you guys can't help me, i will shoot myself :D
Your partitioning looks OK although I'm not familiar with OSX.  Also, the grub menu looks basically correct, although it may be better to use rootnoverify rather than simply root for the OSX and Windows entries.  Perhaps you have some other problem?

Grub is actually pretty simple.  You can change the order however you want.  You just 
1.  set any title your want, then 
2.  set the root: hd0 = sda, and 0 = partition 1.  So HD0,0 is grubs way of saying sda1, and HD0,1 means sda2.  Then, 
3.  you need to tell it what to do, which in the case of non-linux OS, is usually chainloader +1 - basically, blindly boot from the 1st sector past the bootloader for that "root".

---

### Post by mikewhatever on 2008-06-15
OK, that makeactive thing makes sense. What if you delete that line from OSX section?

---

### Post by kugelinis on 2008-06-16
> **mikewhatever said:**
> OK, that makeactive thing makes sense. What if you delete that line from OSX section?


I'm getting 
Starting up.....
Error loading booter

---

### Post by bumanie on 2008-06-16
Have a look at easy bcd bootloader from [neosmart]("http://neosmart.net/dl.php?id=1") It is apparently very good for configuring triple boot systems.

---

### Post by kugelinis on 2008-06-16
> **bumanie said:**
> Have a look at easy bcd bootloader from [neosmart]("http://neosmart.net/dl.php?id=1") It is apparently very good for configuring triple boot systems.
It's for Win Vista, and I'm using xp.... Anyway, i read about putting chain0 to boot/grub/OSX folder.... So, i entered the grub, changed hd?,? to mine and i'm getting this: Error17: Cannot mount the selected volume.... I think that was a little step forward :) 

BTW, i want to say "thank you" for everyone who tried help me.... Maybe i get the osx working :)

---

### Post by bumanie on 2008-06-16
I believe easy bcd boot loader works with xp and vista and will boot linux and mac.

This is from the wiki on easy bcd 

It all depends on who you ask or what you want to get done, but

    * EasyBCD is NeoSmart Technologies 100% free Vista bootloader modification tool.
    * A way to get your Vista working with Linux, BSD, Mac OS X, and dozens more operating systems without a headache!
    * An IT Guy's number 1 Vista-troubleshooting tool.
    * A multiple award-winning application, used and recommended by people at PC World, Microsoft, and more!
    * The best way to do just about anything with Windows Vista before it even turns on!
From [here]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home")
Sorry, I quoted about vista there, but it does work with xp as far as I know. easy bcd was certainly around prior to vista. Can't promise the latest version works with xp, but earlier versions certainly did. I think earlier some versions are still available.

---

### Post by kugelinis on 2008-06-28
Finally! I got OSX working.... So, I installed Leopard instead of Tiger, d-loaded pc-efi and..... Hooray! Grub can load it :) Thank you guys for help!!! :popcorn:

---

