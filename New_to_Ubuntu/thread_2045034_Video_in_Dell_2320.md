---
title: "Video in Dell 2320"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Keven Ryan on 2012-08-20
I can't get any Ubuntu or any other Distro for that matter installed on Dell One 2320. You can use the live distros, but only under . Hoping someone can help with a workaround or would I be better off waiting for Ubuntu 12.10?

---

### Post by Vakman on 2012-08-20
Sorry, the title of this is misleading. Is there an issue with video or with the actual installation? What happens when you do install Ubuntu or try to? Also, under what?

---

### Post by Keven Ryan on 2012-08-20
> **Thisislaw said:**
> Sorry, the title of this is misleading. Is there an issue with video or with the actual installation? What happens when you do install Ubuntu or try to? Also, under what?
I'm a newbie, bear with me.. You can in fact install Ubuntu and other distros,but when you reboot the screen just flickers. my research tells me many others are frustrated as well. Drivers? Kernel? Not sure. I'll keep looking...Thanks

---

### Post by Bashing-om on 2012-08-20
kevin Hi ! ... welcome to the forum.

 Hey, with the live CD ..boot it up and as soon as the bios screen clears, hold down the shift key ... this brings up ubuntu boot options. (at bottom of screen)
choose to boot with the nomodeset option --Remove existing options and add *nomodeset* to avoid module loading, especially if having video issues.//
//we can load a graphics driver at a later time.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by Vakman on 2012-08-21
> **Bashing-om said:**
> kevin Hi ! ... welcome to the forum.

 Hey, with the live CD ..boot it up and as soon as the bios screen clears, hold down the shift key ... this brings up ubuntu boot options. (at bottom of screen)
choose to boot with the nomodeset option --Remove existing options and add *nomodeset* to avoid module loading, especially if having video issues.//
//we can load a graphics driver at a later time.

[INDENT]hth <==BDQ
[/INDENT]

This. Or if it is already installed, then set this same option when you see the GRUB menu. Here is another thread about it: [http://ubuntuforums.org/showthread.php?t=1964792](http://ubuntuforums.org/showthread.php?t=1964792)

---

### Post by Keven Ryan on 2012-08-21
Thank-you! This is all new to me, but, when after I install the screen of course is blank or flickering. How would I get to grub? Is that command line?

---

### Post by kemtnbkr on 2012-08-21
To get to the GRUB options, simply hold down shift as you are booting- it will pause boot and bring you to the GRUB menu.  And yes, it is basically a command line interface, nothing too fancy.

---

### Post by Keven Ryan on 2012-08-21
Thank-you! That all worked, but after my install I could not go any further. The screen becomes blank and I can't go back to nomodset. Any Ideas? Do I need to get to command line to do any changes? Thanks again

---

### Post by Keven Ryan on 2012-08-21
Great! And what changes would I make so that when I reboot Linux will start. Normally? Thank-you

---

