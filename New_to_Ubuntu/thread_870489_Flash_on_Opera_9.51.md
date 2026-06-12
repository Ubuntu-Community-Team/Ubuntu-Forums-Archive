---
title: "Flash on Opera 9.51"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Vega on 2008-07-25
Hai Guys!

How would one go about installing Flash Player 9 on the latest version of Opera? The current install files for Hardy on Adobe's site only apply to Firefox 3 from what I saw.

Thanks for any input

---

### Post by sdowney717 on 2008-07-25
If you get stuck this is what I did.
partly to see if it worked, and it did.

Installed windows opera on WINE
Installed windows flash 9 on WINE

---

### Post by aullidolunar on 2008-07-25
Try go into opera preferences:
Tools>Options>Avanced (tab)>Content (left item)>Plugins
And add firefox|iceweasel plugins folders and don't forget to include the one in your
~/.mozilla

---

### Post by kriukov on 2008-07-25
The Mozilla/Firefox plugin works for Opera too.

Get the plugin from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Unpack it and put libflashplayer.so into .opera/plugins in your home folder

Restart Opera

---

### Post by sdowney717 on 2008-07-25
when you install the flash version from adobe using terminal. It will ask you if you wish to do another install. I suppose pointing the installer to the proper location for Opera, will install the libflashplayer.so in the right location for opera.

I had some problem with the adobe player. It would stutter and halt.
But the ubuntu flash version 9 found in ubuntu repositories works a lot better.

Is the version in repositories optimized for ubuntu?

---

### Post by kriukov on 2008-07-25
What the installer apparently does is just copies the *.so file into the plugins directory. It can be done manually in case it does not copy it into the Opera plugins.

---

### Post by sdowney717 on 2008-07-25
yes, when opera or firefox starts, it looks in the plugin folder to see what plugins are available. So the install really just puts the file in the right folder.

---

