---
title: "Boots to black screen instead of logon screen"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Squarenutt on 2008-07-22
Howdy all

 This is the first time I have not found anything on the forum to help me.

 I have just loaded 8.04 from the alternate cd. Everything went well until it was time to boot into the new system. Grub loads everything fine, But after the UBUNTU screen with the status bar finishes I get a black screen. Ive had something like this happen before back with breezy badger. Then I could just type my UN and PW even though I couldnt see the screen and it would load. That does not seem to be the case this time. 

 This is an Intel motherboard model D845GERG2 with on board video if that helps. Nothin fancy.

 Thanks in advance 

 Jeremy Stone

---

### Post by flytripper on 2008-07-22
laptop or pc? doh PC


got a small monitor?

---

### Post by Squarenutt on 2008-07-22
Its a medium sized lcd. Not realy sure about the actual size. 

 Its a model HW191A if that helps.

 I can tell its active its just that theres no image.

 Backlights on and it hasnt gone to sleep.

 Thankya

 Jeremy Stone

---

### Post by Squarenutt on 2008-07-22
Its a 1440x900 wide screen.

 Wish I had another monitor to try.

 Jeremy Stone

---

### Post by Squarenutt on 2008-07-22
GOT IT!


 I could tell That I was logged in even though I was doing it blind so I Ctl Alt F1'd it and got in. 

 then i ran: sudo dpkg-reconfigure xserver-xorg and answered no on the first question about video.

found the answer here:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Thanks for your help. Hope this helps someone else.

Jeremy Stone

---

