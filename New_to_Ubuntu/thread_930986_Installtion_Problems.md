---
title: "Installtion Problems"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by iMrBlankie on 2008-09-26
I am new to Unbuntu and I am having problems with the installation.

I succesfully load the disc and I get to this screen.

[IMG]http://i47.photobucket.com/albums/f200/Zabuza_The_Demon/DSCF3028.jpg[/IMG]

Then I click install Unbuntu and it goes to this screen
[IMG]http://i47.photobucket.com/albums/f200/Zabuza_The_Demon/DSCF3030.jpg[/IMG]

it finishes loading and goes to this black screen and commences in repeating the same thing over and over again for hours.

[IMG]http://i47.photobucket.com/albums/f200/Zabuza_The_Demon/DSCF3031.jpg[/IMG]
[IMG]http://i47.photobucket.com/albums/f200/Zabuza_The_Demon/DSCF3033-1.jpg[/IMG]

I need help!!!!

---

### Post by phidia on 2008-09-26
What are your system specs (cpu speed, ram, video card) and have you tested the cd by selecting "Test CD for Defects"?

---

### Post by shifty_powers on 2008-09-26
also, you might want to try the alternate install cd...

---

### Post by iMrBlankie on 2008-09-26
Um, even when I click check for cd defects it does the same exact thing.

Intel Pentium 4 1.5 GHz

364MB of RAM 

and about 7.5gb on my Harddrive

Nvidia GeForce 2 GTS/Geforce2 Pro

---

### Post by iMrBlankie on 2008-09-26
I burned this cd myself using the ISO file fromt the site.

---

### Post by iMrBlankie on 2008-09-26
Hello?

---

### Post by jARLAXL on 2008-09-26
1. did you check the cd with md5sum? It happened to me that i was downloading the ISO image an windoze machine and all md5sums were wrong
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
after you verify it with md5sum burn the cd and then use the option "check cd for defects"
2.did you try to boot the cd without installing it(1st option when cd boots)?
please try these first and then report back.

---

### Post by iMrBlankie on 2008-09-26
I tried them all even the option of booting on windows nothign works.

---

### Post by Tatty on 2008-09-26
It sounds very likely to be a bad burn.  Go back and check the md5sum of your .iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then burn it again using a slower speed.

---

### Post by shifty_powers on 2008-09-26
go to

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and click on the box that talks about the alternate cd. download that and try installing with it rather than the live cd...

---

### Post by jARLAXL on 2008-09-26
how about trying to boot the cd in another machine? with a good cd reader. and then check the cd there for defects. it looks like a cd read error to me.

---

### Post by iMrBlankie on 2008-09-26
New news my harddrives failed on me -__- and now my computer won't boot up all together -_____- Posting from my Wii now

---

### Post by JC Cheloven on 2008-09-26
> **iMrBlankie said:**
> New news my harddrives failed on me -__- and now my computer won't boot up all together -_____- Posting from my Wii now

I don't know if a corrupted cd is able to produce such an effect. Perhaps it is, but rather than guessing the causes, I would try to start again from the beginning. That is:

-> Take your windows installation disk, boot from it, open a recovery console, and type "fixmbr". This should allow you to run windows as usual.

-> Download the iso image (the alternate cd at your option), at a low speed, and check its integrity as people wisely told you in this thread.

-> If you've downloaded the live cd, try a live session before installing.

-> If everything succeded, you should confidently install.

---

### Post by iMrBlankie on 2008-09-27
-sigh- My hardrive fried... I'm back on but I'm using my 20gb which is not alot of space at all.

---

