---
title: "Cursor pointer constantly displays cross + more problems"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by areeman on 2012-09-17
Hello,

I have been using ubuntu 10:04 for a year now with hardly any problems. 
After installing gtk-sunlight following instructions from [here]("https://launchpad.net/%7Erealtime.sunlight.wallpaper/+archive/rswhttp://") a bunch of problems have occurred:

1. The cursor constantly displays the cross symbol in most applications including nautilus.

2.  Many important keyboard shortcuts have disappeared from the shortcut  menu. Although these shortcuts work fine when added again. 

3. Most strangely, when firefox is open it appears to hijack to keyboard meaning the terminal and other applications will not accept keyboard input until firefox is closed. Other applications, such as gnome-terminal and nautilus, do not hijack keyboard control.

4. The common border on all windows has disappeared i.e. no close,minimize or maximize buttons.

I  have uninstalled the gtk-sunlight application but sadly this did not  change the situation. I have also backed up and moved the .gnome .gconf  folders in an attempt to restore settings but this also failed. 

The reason I have posted all of these problems here is that they are most likely all related, probably to a broken windowing system. 

This is my first post here by the way so apologies for any noob-ness. 

Thanks for any help :)

Andy

edit: I am not using compiz

---

### Post by areeman on 2012-09-17
Solved this problem by reinstalling gnome-session and ubuntu-desktop:

```
 sudo apt-get install gnome-session ubuntu-desktop 
```

---

