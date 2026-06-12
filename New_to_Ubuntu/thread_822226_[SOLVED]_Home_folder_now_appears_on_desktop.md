---
title: "[SOLVED] Home folder now appears on desktop"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by jerrynewt on 2008-06-08
Just fired up my laptop (Toshiba Satellite Pro) 8.04 tonight and all of my home folder now appears on my desktop. Dual boot with 7.10 and 8.04. Any ideas how to fix this would be really appreciated. Thanks in advance.

---

### Post by jordanmthomas on 2008-06-08
Try running this:
```
 gconftool-2 --set /apps/nautilus/preferences/desktop_is_home_dir --type bool false

```

---

### Post by jerrynewt on 2008-06-08
Ok tried running that in terminal with no luck. Any more suggestions ? Thanks

---

### Post by kaboodle_fish on 2008-06-08
Go to getdeb.net and download Ubuntu Tweak which under Desktop - Desktop Icon has a setting to Use Home Folder as the desktop. Maybe ticking or unticking this might work for you.

Also there are other settings you may find useful in Ubuntu Tweak as well

---

### Post by jordanmthomas on 2008-06-08
You may need to log out / back in for that to take effect (or at least kill off nautilus)

Also, do you have a folder called Desktop in your home directory?  If not, nautilus might default to using your home folder instead.

---

### Post by jerrynewt on 2008-06-12
Here is what I get when I open the file browser for home.[ATTACH]73879[/ATTACH].
Notice the small desktop image upper right of the jerrynewt folder. Just wondering how to remove it. Tried to remove with the gconf editor with no results. Thanks for the help.

---

### Post by jerrynewt on 2008-06-13
Bump**

---

### Post by jerrynewt on 2008-06-14
Bump again **

---

### Post by wormser on 2008-06-14
This [thread]("http://ubuntuforums.org/showthread.php?t=47434&highlight=desktop+home") has a couple of solutions.  

> 
open gconf-editor (in Apps - System Tools) and navigate to 
apps - nautilus - preferences and unckeck the key "desktop_is_home_dir"

It might need a Ctrl Alt Backspace, but after the next login you should have a "desktop" dir under $HOME.

---

