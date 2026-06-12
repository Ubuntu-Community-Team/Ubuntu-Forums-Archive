---
title: "Ubuntu is running in low-graphics mode"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-27
I get this message when starting up. I tried pressing continue, but then the screen just turns black and I have to force a shutdown. I tried going into configure, but i couldn't find my specific graphics card (s3 prosavage ddr), and i found some generic one and pressed test, but then the screen went black again and i had to restart. Even when I press Shut Down, the screen just turns black and I gotta do a force shutdown.

This has happened before, but it only happens once and after I shut down, the problem is fixed. Any ideas?


Also, I'm running my windows partition now, that's how I'm able to get on the site.

---

### Post by philinux on 2008-06-27
Boot up in recovery mode.

In the menu choose xfix, see if that helps.

---

### Post by adobrakic on 2008-06-27
Alright, thanks. 
In that case, I'll brb. :D

---

### Post by adobrakic on 2008-06-27
This didn't work, I still get the low graphics mode popup

---

### Post by philinux on 2008-06-27
Ok, well you need to login in low graphics mode and reinstall/re-enable your graphics driver.

Hang on try the previous kernel from grub if you've updated recently.

---

### Post by adobrakic on 2008-06-27
The thing is that I can't. If I press "Continue," the screen just stays black and nothing happens. Maybe I should let it sit for a little longer. Thanks though, I'll try this.

---

### Post by adobrakic on 2008-06-27
Yeah, nothing's working. I also tried to get on an older version in the grub menu. Is there anything I could do with the live cd, or will I have to format or something?

---

### Post by philinux on 2008-06-27
You could have a look at your xorg.conf from the live cd. Also see if there are any backup files of it. 

What do you think caused this in the first place?

---

### Post by adobrakic on 2008-06-27
To be honest, I have no idea. I recently did 

```
sudo apt-get update
``` and
```
sudo apt-get upgrade
```

but it asked me to restart, which i did, and it worked fine then. Then I was on ubuntu and my keyboard went out (always does this-- p.o.s), and I had to restart, and that's when I started getting the low graphics mode popup.

You said to check the xorg.conf, but what would i specifically look for?

---

### Post by philinux on 2008-06-27
Well if I remember there was an xorg update recently.

Just browse /etc/X11 for any xorg config files. Look at the date stamp for when your system was working and compare the files.

Before you boot the live cd do this. If you can get to recovery mode, get the command line and try startx and see if any error messages.

---

### Post by adobrakic on 2008-06-27
When i did startx, I got a "fatal error" and it said like no screen found or something. I can't remember what it exactly said, it had quite a bit of text on the screen.

When I tried booting up live cd, i got the low graphics mode pop up again, and pressed continue and let it sit for like 15 minutes, and nothing happened. I think I might have to format.

---

