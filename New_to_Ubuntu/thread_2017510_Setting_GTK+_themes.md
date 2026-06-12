---
title: "Setting GTK+ themes"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Szymoninho on 2012-07-05
Hi, i'm using ubuntu 12.04 and yesterday i was trying to change GTK+ theme with the Gnome Tweak Tool but it doesn't see the theme i installed. It's both in .themes folder in my home directory and in /usr/share/themes folder, just as i read it should be. What's good is that the Tweak Tool doesn't see only the GTK+ theme i installed, it can see the default GTK+ themes, the icons i added etc.
Does anyone know the solution for this?

---

### Post by Frogs Hair on 2012-07-05
Hello and Welcome 

Two things I would check.
1. is the theme GTK 3.4 compatible ?
2. was the theme fully extracted ?
 
Some times after extracting the tar.gz checking the folders is a good idea because there may be compressed packages inside. Could you provide the theme name also.

---

### Post by Szymoninho on 2012-07-05
I'm pretty sure it's fully extracted, i scanned for .zip and .tar.gz files inside and it didn't find anything. I got it from here: [http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/) the source seems pretty reliable and after a long "research" i haven't found any people complaining about GTK+ themes from this package. I was wondering about the compatibility but i have no idea how to check it. There's a folder inside named "gtk-2.0" but does it straight mean it isn't compatible? Firstly i thought that the new versions of GTK can use older themes but your question really made me wonder. :-kThe theme itself is named Mac4Lin_GTK_Aqua_v1.0. I've tried installing some programs (other than gnome-tweak-tool) to put this theme in use but after like 5 tries gave up, cos i don't have a good internet connection here... Would you like to give me some commands just to check the compatibility?

---

### Post by Frogs Hair on 2012-07-06
According to Gnome Look the theme has not been updated since 2009 which would make it incompatible with Gnome 3(11.10-12.04) . See the link for GTK 3.4 themes. The theme also uses Emerald which is no longer officially supported.  [http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

---

### Post by Szymoninho on 2012-07-07
That's a shame, thanks a lot anyway :) i'll mark this as solved.

---

