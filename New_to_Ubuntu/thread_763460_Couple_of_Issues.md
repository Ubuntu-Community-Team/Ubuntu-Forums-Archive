---
title: "Couple of Issues"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Apples123 on 2008-04-23
OK ive had Ubuntu for a couple of months now and im loving it, I first had 7.10 and just recently went to 8.04. However i have had two small problems which i was wondering if anyone would be able to help me fix. With both versons ive had trouble with the GRUB (i dual booth with xp 64bit) my wireless logitech usb keyboard does not work in the grub, so if i want to boot to windows i have to plug in the ps2 keyboard... kind of a pain not sure if it can be fixed.

The other issue im having is that i cant get alobe flash to work and instead have to use gnash which is not the same quality especially for youtube videos.

Im using compiz could this also be an issue?

Any ideas?

(Mods not sure where to put so i just decieded im a beginner and put it in here, feel free to move)

Thank You

---

### Post by Crafty Kisses on 2008-04-23
I don't think Compiz should be an issue while watching a video, but did you try installing flash-plugin-nonfree from the repos? That should work.

---

### Post by Apples123 on 2008-04-23
> **Codename said:**
> I don't think Compiz should be an issue while watching a video, but did you try installing flash-plugin-nonfree from the repos? That should work.


Haha Thank you very much i was just clicking on the one that asked me to install as i tried to watch videos... 

No does anyone know where i could find help for the grub what area i should post in?

Cheers

---

### Post by Xiong Chiamiov on 2008-04-23
I seem to remember reading on here once that there is some inherent limitation to using your kind of keyboard in GRUB.  However, my memory's not that great, so don't give up hope quite yet.

---

### Post by Crafty Kisses on 2008-04-23
> **Apples123 said:**
> Haha Thank you very much i was just clicking on the one that asked me to install as i tried to watch videos... 

No does anyone know where i could find help for the grub what area i should post in?

Cheers

I'd try the Beginners forum, shouldn't be a problem. :)

---

### Post by Apples123 on 2008-04-23
> **Xiong Chiamiov said:**
> I seem to remember reading on here once that there is some inherent limitation to using your kind of keyboard in GRUB.  However, my memory's not that great, so don't give up hope quite yet.

Any possibility of switching to lilo without a fresh install? 

and arnt i in the beginners fourms?

Cheers

---

### Post by Xiong Chiamiov on 2008-04-23
> **Codename said:**
> I'd try the Beginners forum, shouldn't be a problem. :)
Isn't this the beginner's forum...?

---

### Post by Crafty Kisses on 2008-04-23
> **Xiong Chiamiov said:**
> Isn't this the beginner's forum...?

He was asking where he should post his question, I proposed this forum. Yes it is the beginners forum, I'm aware of that.

---

### Post by ubername on 2008-05-04
I am also having the problem where my wireless keyboard is not recognised in grub. However it used to be, it was after one of the many (gratefully received) updates where it stopped working, so it seems that it can work, it just won't at the moment.

Thanks for any help.

---

### Post by sailor2001 on 2008-05-04
sudo dpkg-reconfigure xserver-xorg  and read keyboard instructions carefully.
This may be where you are having trouble

---

