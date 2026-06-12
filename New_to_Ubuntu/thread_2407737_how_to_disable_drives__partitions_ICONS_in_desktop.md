---
title: "how to disable drives / partitions ICONS in desktop  display ?"
date: 2018-12-08
forum: New to Ubuntu
---

### Post by anneranch on 2018-12-08
On standard Ubuntu (16.04) desktop I get an icon for every disk / partition displayed. In my case on left side of the desktop.
I do not know the official name of this "status bar (?) ". 
Is there a **permanent way to stop (disable)  these icons** to be displayed?
They serve no useful purpose except clutter the status bar - for me.

---

### Post by TheFu on 2018-12-08
Just a guess, but how are those partitions being mounted?
If they are manually mounted via the fstab file, I think they won't be shown as separate in the GUI.

But I don't run Unity, so I can't check that here.

There are a few side effects by mounting via the fstab - mounts would happen at boot and the exact mount options can be controlled, which would likely make the storage 20-40% faster.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) explain.  Warning - only use the fstab method, not the other options.  Also, whenever editing system files, best to use **sudoedit** as the command for many reasons. It is safer, it supports any editor you like, and it is installed onto every Linux system that supports sudo.

---

### Post by deadflowr on 2018-12-08
See if this works
[s]You need dconf editor installed
```
sudo apt install dconf-editor
```
or install it through Ubuntu Software either way will work.
(It'll show as dconf editor in the apps menu)
then open it and go to com > canonical > unity > devices > blacklist.
toggle the to use default value to off.[/s]

(Nevermind, the toggle option is only in newer releases, dconf in 16.04 doesn't have that setting
seems moot to install it then I thought it had the settings but I guess not)

Now go to you launcher bar (what the left side panel is called.)
And right click on the icons in question and select the Unlock from Launcher.
The icons should be gone, and with the default value set to off they should stay gone.

Note they [s]will[/s] might reappear when ever any device is mounted.
But they should disappear when the device is unmounted.

---

