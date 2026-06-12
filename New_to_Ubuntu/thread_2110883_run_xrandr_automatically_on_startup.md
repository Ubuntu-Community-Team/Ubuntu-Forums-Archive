---
title: "run xrandr automatically on startup"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by Haisiong on 2013-01-31
Noob here trying to automate the xrandr settings which make my netbook usable in Lubuntu 12.10.  I can manually copy and paste the following text into XTerm, hit enter, and it works like a champ:

xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.28 --panning 1024x768

(I found this after a few minutes googling.  It downscales so that the netbook native 1024x600 screen displays 1024x768.  Wonderful!)  

Now... after some HOURS googling I find numerous suggestions, but no definitive way to make this run on startup.  Tried a couple of methods involving editing:
 etc\rc.local
 etc\xdg\lxsession\LXDE\autostart
but no joy.

If I can't make this xrandr command run automatically, I would at least hope to make the command run in terminal with just a few mouse clicks, without having to copy and paste every time I boot the netbook.

Any help will be appreciated!

---

### Post by omeomi on 2013-01-31
You can just create a shell script to execute:
```
 #!/bin/bash          
xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.28 --panning 1024x768

```          
Save this anywhere (e.g. ~/fileName.sh) and make it executable:
```
chmod +x ~/fileName.sh
```

In the system settings there is an option to choose scripts that are run at startup (I don't know the exact name for Lubuntu). You can select the script there.

---

### Post by Haisiong on 2013-01-31
omeomi, thank you for the response.  I created the script per your instruction.  Then looking where to put the script for startup, I found 
this post by Lyfang:

   Add your startup applications in Lubuntu 12.10 like this:
    1. Go to /home/USERNAME
    2. Press Ctrl+h
    3. Go to /home/USERNAME/.config
    4. Create the folder autostart
    5. Go to the menu > right-click > add to desktop
    6. Move shortcut to /home/USERNAME/.config/autostart
    7. Restart Lubuntu

Tried this method, no joy.  But....  think I may have found a new twist.  Just noticed that of the several ways to get a terminal, UXTerm seems to be the only one that processes the xrandr command.  XTerm, LXTerminal, and Ctrl-Alt-T don't act on my xrandr command.  So maybe that is why I'm having difficulty getting it to autostart...

Thanks again -

---

