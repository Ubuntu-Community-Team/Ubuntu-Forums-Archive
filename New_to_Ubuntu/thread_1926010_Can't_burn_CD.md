---
title: "Can't burn CD"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by kanjiline on 2012-02-15
Help!

I want to burn a Xubuntu install CD. However, when I try to burn the CD, I am forced to choose between


[LIST=1]
[*]Empty CD-R: 27.1 MB free storage space
[*]Image file
[/LIST]
Neither of these choices helps me! The CD-R is brand new out of the box and should have a lot more than 700 MB available. And an image file (.iso) is not what I want because the computer will not boot from it!


The burner is a "BENQ DVD DD DW1640". Neither Brasero nor the no-name CD Creator will let me burn the files to the CD-R. This is so frustrating!


The CDs are not damaged. The burner should be working fine. Both the burner and empty CD-Rs work o.k. when the same machine is booted to Windows XP. But I can't burn this CD in Ubuntu 11.10.


What to do?

---

### Post by kanjiline on 2012-02-15
O.K., I am in Windows now... but I am having a problem here, too. Tried using NERO to burn the CD, but after completion NERO tells me there are about fifty errors (= discrepancies between what's been burned on CD and the source on the hard disk).

Perhaps the burning device is less than 100% working, and Ubuntu is less forgiving of its faults than Windows?

---

### Post by Rodney9 on 2012-02-15
This page has a good guide on burning Ubuntu install discs - 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Rodney

---

### Post by kanjiline on 2012-02-15
Rodney, thanks, but I had already read that page in its entirety and followed its advice. In particular, I did set the write speed at the lowest possible value (12x).

In the meantime... I stuck the (supposedly faulty) CD in the drive and let the computer boot with it. Then I chose "test for errors" in the boot-up screen and this completed without any complaints ("keys: press any key to reboot.")

Your thoughts?

---

### Post by kanjiline on 2012-02-15
winh8r, thank you but your advice has nothing to do with my question, I'm afraid.  Remember, my question is, Why can't I burn CDs in Ubuntu?

---

### Post by kanjiline on 2012-02-16
Bumping, hoping for an experienced user to chime in with advice. 

In the meantime, I tried three times to install Xubuntu using the CD that I burned in Windows with Nero. Every time the result was awful... installation incomplete, keyboard input during registration not recognized, network (ethernet to router; mobile broadband) not recognized, mouse leaving artefacts on screen. 

Could be because the Xubuntu install CD's self test isn't thorough enough to detect that it has errors. Could be because of some hardware/driver incompatibility. Or who knows what.  

Right now I am not focusing on the Xubuntu install anymore. I want to know, has anyone else besides me experienced that you tried to burn a CD-R with 600+ megabytes of data and Ubuntu or Brasero wouldn't let you... i.e., it let you choose only between a 27 megabytes empty CD and burning as an .iso... with only the second option actually selectable? [B]Did you solve that problem and how?

If not, then what steps should I do next?

[/B](Just so there is no confusion: the 384 mb PC that I am trying to install Xubuntu on is my own, and the 1 gb Ubuntu machine with the CD burning problem is my friend's... I am her computer helper and she is depending on me to solve this.)

---

### Post by Silent Warrior on 2012-02-16
Not a day gone, and you bump already? You must be eager! :)
---------
(Bah, I just authored a fairly lengthy reply (well, 6+ lines, anyway, unbroken text in the editor box), and it turns out I was full of ****... One more try, eh?)

I really don't understand why that's happening, nor do I know what exactly IS happening. Have you tried K3b? Are you perhaps accidentally trying to burn the CD-image in DVD-mode? Is the burner internal or external? I am kinda grasping for straws, but I don't see what else I can do...

---

### Post by kanjiline on 2012-02-16
Thank you for your questions. I am home now and won't be in front of that machine again until next week. However: (1) it's an internal device (see my opening post for brand and model); (2) did not try K3b, tried Brasero and (from Nautilus) something called CD/DVD maker or creator (apparently Ubuntu's default method for burning CDs); (3) I made sure that whenever I had a choice between CD and DVD, I chose CD.

I am sort of knowledgeable about Windows. In Windows, I would know to open the error log and study it for clues. I don't even know where the error log is in Ubuntu. Nor do I see a "device manager" equivalent where I can see if any devices are flagged as faulty (and why).

---

### Post by merlinof2 on 2012-02-16
Also issue with Brasero.

Burns fine, ISO or files as long as I pull the files from the local drive.  If I try to burn CD's using files from a network drive, (my goal), all proceeds as normal, Brasero sees the network and adds the files to the compilation, but no joy, volume label changes per my instructions, but no files are burned to the drive.  I move the files to a local directory and try again, it works perfectly.  "permissions ?"

K3b has an almost similar result, burns local files perfectly, but won't see the network drives at all.

any assistance or direction would be appreciated.  

PS: xfburn performs as K3b does.

---

### Post by BBQdave on 2012-02-16
> **kanjiline said:**
> winh8r, thank you but your advice has nothing to do with my question, I'm afraid.  Remember, my question is, Why can't I burn CDs in Ubuntu?

+1 for **Xfburn**  :D

I had trouble with *Brasero* too, thought it was my old notebook's hardware.  Tried **Xfburn**, no coasters since.

---

