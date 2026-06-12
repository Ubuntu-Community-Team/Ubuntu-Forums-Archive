---
title: "Cannot view youtube videos on firefox"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by professorTHC on 2008-06-06
I think i lost my other thread and ii cant find it. but i have firefox and i isntalled the java plugin and the shockwave plugin as well as a few others, and i still cant get youtube videos to play on firefox. no flash videos work for that matter, it just turns blank white and nothing happens, any ideas? thanks in advance!

---

### Post by DestroyMicroshaft on 2008-06-06
Try the flash non free in synaptic.

---

### Post by finito on 2008-06-06
Are you running 64bit or 32bit. 

When i get that error I juts close all Firefox windows open and revisit the site it works fine, although I rarely get it anymore since the new updates.

---

### Post by nothingspecial on 2008-06-06
```
sudo apt-get install flashplugin-nonfree
```

Then restart firefox.

---

### Post by iaculallad on 2008-06-06
Install the libflashsupport to view youtube videos

```
sudo apt-get install libflashsupport
```

---

### Post by professorTHC on 2008-06-06
still no luck guys. i had the non free one installed and i just installed the lib one, but to no avail. i noticed that the shockwave player might interfere, but enabled or disabled, nothing happens. when i turn it off, it says i need to download the latest flash player, but when i look in synaptic it says i have the latest version installed already.

---

### Post by Fedz on 2008-06-06
Just un-installed the flashplugin-nonfree from System > Admin > SPM and went to home > (view > show hidden files) > .mozilla (folder) > plugins (folder) > and deleted libflashplayer.so (file).

Downloaded and installed [flash player 10](http://labs.adobe.com/downloads/flashplayer10.html).

Had no problems so far viewing multiple flash content in multiple browser tabs :-D

---

### Post by SunnyRabbiera on 2008-06-06
> **professorTHC said:**
> still no luck guys. i had the non free one installed and i just installed the lib one, but to no avail. i noticed that the shockwave player might interfere, but enabled or disabled, nothing happens. when i turn it off, it says i need to download the latest flash player, but when i look in synaptic it says i have the latest version installed already.

what is your kernel/processor type?

---

### Post by Xerp on 2008-06-06
Gnash works for me...

---

### Post by professorTHC on 2008-06-08
spm shows that i have it, but i dont see it in the firefox addons column. could that be the issue?

---

### Post by alienexplorers on 2008-06-08
With your flash player program, did you make a symbolic link to /home/yourname/.mozilla/plugins

---

### Post by alienexplorers on 2008-06-08
With your flash player program, did you make a symbolic link to /home/yourname/.mozilla/plugins

---

