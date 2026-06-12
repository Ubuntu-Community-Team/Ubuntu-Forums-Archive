---
title: "What am I missing?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by GreenFire08 on 2008-06-26
Alright, another question. I have internet access now, which is great, but whenever I go to somewhere like YouTube, none of the videos play. However, I don't get an error message telling me what's wrong. Is there a certain component of FireFox that I need to get?

---

### Post by Nepherte on 2008-06-26
Did you install flash?

```
sudo apt-get install flashplugin-nonfree libflashsupport
```

---

### Post by rockerphil on 2008-06-26
you need the flash plugin for Firefox, so run this in terminal

sudo apt-get install flashplugin-nonfree

then restart your browser, and that should do it

---

### Post by GreenFire08 on 2008-06-26
Thanks for that command, guys. I had installed flash but for some reason didn't have the whole thing. Now it works!

---

### Post by bumanie on 2008-06-26
Flash no longer will work on my 8.04 - I have tried a number of 'fixes'. However a workaround for youtube is to open totem movieplayer and install the youtube plugin. The plugin is under edit. You can then choose youtube form the drop box where it says 'playlist' and then search for what you want.

---

### Post by BenAshton24 on 2008-06-26
Yes you need flash player. If you see an "install missing pluggins" button at the top of the screen whilst you are on a page with a flash video, (i.e. youtube) click it and follow the onscreen instructions. If you do not see this button visit [http://url.co.uk/dsuaf](http://url.co.uk/dsuaf) extract the tar.gz and run the install file in terminal. If the installation is successful, restart your browser and the videos should work. Hope this helps :D

---

### Post by bumanie on 2008-06-26
> **BenAshton24 said:**
> Yes you need flash player. If you see an "install missing pluggins" button at the top of the screen whilst you are on a page with a flash video, (i.e. youtube) click it and follow the onscreen instructions. If you do not see this button visit [http://url.co.uk/dsuaf](http://url.co.uk/dsuaf) extract the tar.gz and run the install file in terminal. If the installation is successful, restart your browser and the videos should work. Hope this helps :D
I have tried flash 9, flash 10 beta and flashplugin-nonfree libflashsupport, plus I have tried gnash - none work. It used to work fine, but doesn't any longer. I think it is some sort of conflict with updates and my setup.

---

