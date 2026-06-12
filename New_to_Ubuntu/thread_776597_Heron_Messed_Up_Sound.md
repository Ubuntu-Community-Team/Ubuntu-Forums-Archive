---
title: "Heron Messed Up Sound"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Amish_Gramish on 2008-04-30
Sound, Flash, and Firefox worked almost perfectly before I upgraded to 8.04 from 7.10, and now the only way I could get Flash working was by installing Firefox-2 (8.04 doesn't like to create anything for Flash for 3.0b except for the flashplugin-nonfree folder), but, for some reason, Firefox goes to [www.google.com](www.google.com) randomly on the page I'm on.  (It just did it about two minutes ago, too.)

Anyways, my sound is now pretty screwed up, because now it sounds fuzzy and "crackly."
Is there any way to fix it?

(I have a Compaq Presario F572US Notebook PC and I upgraded from Ubuntu 7.10.)

---

### Post by azurepancake on 2008-04-30
I'm not sure how much this will help you with your current problem, but when I installed Hardy, Flash was not working of course so I installed the flashplugin. After that, video would play, but there would be no sound.

I later ran "sudo apt-get install libflashsupport" into terminal, reset Firefox and now flash runs perfectly. 

I hope this helps you in some way!

---

### Post by Amish_Gramish on 2008-04-30
I already uninstalled and reinstalled libflashsupport when I only had Firefox 3.0 Beta, and that didn't solve the problem, what the problem is is that it won't make the files when it "installs" flashplugin-nonfree.

Anyways, are there any special drivers that I have to install for sound?

---

### Post by AndThenWhat on 2008-05-01
I have had sound problems and flash problems in firefox-3 with hardy also.  I think since this seems to be a common occurrence among new hardy users the developers will be working on a fix sooner or later.

---

### Post by distractible on 2008-06-14
Hi Amish Gramish!
Have you solved your sound problem yet? I also have a Compaq Presario laptop and when I upgraded from 7.10 to Hardy Heron I had the same issue. The sound is distorted and crackly. Just wondering if you have had any luck fixing it. 
Thanks!

---

### Post by poisonkiller on 2008-06-14
My sound is "distorted and crackly" too, is there any way to fix this? :)

---

### Post by poisonkiller on 2008-06-14
Hah, nevermind. I visited Ubuntu's IRC channel and solved my problem. It seems if you lower PCM in Volume Control, the "crackling" goes away. :)

---

### Post by distractible on 2008-06-15
Hi Poisonkiller! Woah--you fixed it? Can you tell me what your steps were exactly? I'm not sure what the IRC channel is or where to access Volume Control! : )

---

### Post by distractible on 2008-06-15
Doh! Just found it. You're right, that worked! Thanks, Poisonkiller!

---

