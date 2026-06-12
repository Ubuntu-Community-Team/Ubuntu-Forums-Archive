---
title: "Wubi Question and Ubuntu studio"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by DarknessEnemy on 2008-06-28
I have some questions, and I hope that your inner data about the topic can answer this:

Can I install 2 ubuntu OS on one laptop with Wubi or I shall use the right way?

Does Ubuntu Studio Install like edubuntu? If so. It could delete previous apps (like Compiz Fusion, Amarok, VLC, etc)?

If not, Is it another complete distro? If so. Does it have Wubi? Can be installed even when you already have ubuntu installed?

I hope you can answer this. Thank you in advance.

---

### Post by angry_johnnie on 2008-06-28
I don't think you can install another *buntu with the same instance of Wubi that you have already used.  You'd have to use another one.


You could however, install the ubuntustudio-desktop metapackage.  But then, ubuntustudio uses a different kernel.  You wouldn't lose the generic kernel.  You'd just have to choose which one to use from the grub menu.

Bad thing is you don't get a grub menu with wubi, do you?  Boot your computer and choose ubuntu from the windows loader, and then press the escape key, just to see whether grub shows up.  If it does, that is where you would have to choose which kernel to use.

Honestly, I think this question would be better answered in the Wubi section of the forums, which is located [here]("http://ubuntuforums.org/forumdisplay.php?f=234").

---

