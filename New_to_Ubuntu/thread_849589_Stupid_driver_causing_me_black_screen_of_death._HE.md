---
title: "Stupid driver causing me black screen of death. HELP!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Alex J. on 2008-07-04
So, every time I install a certain video driver from the Ubuntu repository, the screen goes all black after GRUB. Most recently I clicked on the "enable video card" box in system>hardware drivers and it automatically installed the bad driver causing a blank screen on reboot.

I keep updating it, and accidentally installing it, and the only way I know to get it back is to completely reinstall ubuntu, which means I have to go through the entire wireless driver process again.

Any POSSIBLE way that I could get my lovely screen back instead of a black void? Also any way I can makes sure it NEVER installs this driver ever again?

PLEASE help. This is driving me nuts.

---

### Post by Alex J. on 2008-07-04
So, used the GRUB Recovery mode. HOORAY. No more reinstalls! But I still have stupid fuzzy lines all over the freaking place...any hints still welcome.

**Any way I can make sure that this driver stops getting installed automatically? I HATE it.**

---

### Post by OldTimeTech on 2008-07-04
Have you used envy out of synaptic package manager?  It might help load the right driver.

---

### Post by TheTrlak on 2008-07-04
I had the same issue going on. Right now im avoiding updating them and I have been attemtping to compile my own kernel so the nvidia installer will load the correct driver but my system doesnt match the correct GCC >.>; I have a forum thread going on somewhere here about it. Also if you are using a 64-bit os or not go look over there because there is an nvidia thread that teaches how to manually install your drivers... I'll post an edit with the hyperlink.

Edit: ok here is the link to the installation guide that seems to work for alot of people.

   [http://ubuntuforums.org/showthread.php?t=819210](http://ubuntuforums.org/showthread.php?t=819210)


The following link is to my own thread and basically some ideas and other guides were placed depending on if you encounter any problems.

   [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5314827](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5314827)

---

