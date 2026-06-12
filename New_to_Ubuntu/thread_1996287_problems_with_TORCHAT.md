---
title: "problems with TORCHAT"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Dethmetl on 2012-06-04
I'm running ubuntu 12.04 and am having trouble with TORCHAT, when I open it for the first time, it works fine, when I close it and try to open it again, I'm hit with the message,

"Torchat: Port already in use
Something, probably another TorChat instance, is already listening at 127.0.0.1:11009. You must create another profile using different ports to be able to start TorChat a second time."

I assume this means somewhere the first instance must still be running, I don't know how to close it, or find it though. I don't believe its in my system tray (top right?), and its definitely inactive on my sidebar panel. any ideas?

---

### Post by Dethmetl on 2012-06-04
bump

---

### Post by 7bit on 2012-06-12
> **Dethmetl said:**
> 
I assume this means somewhere the first instance must still be running, I don't know how to close it, or find it though. I don't believe its in my system tray (top right?), and its definitely inactive on my sidebar panel. any ideas?

If it is running then it is in the systray (maybe Unity also messed the systray up like so many other things, people should really boycott this nonsense, but normally it should be in the systray and there you can close it. You can also close it from the context menu in the TorChat main window). Clicking only  the X on the window border will *not* exit it, it will only minimize it to the systray.

If it is runing then you should see the process in htop. Try to look for also for a tor process (running under your user id) and the tor.sh shell script, one of these (or both) might also still be running and their processes have inherited the socket handles, even after the main program really exited. Use htop or somethig similar to find them and kill them.

Normally this should not happen, it should exit cleanly. If it doesn't then its a bug.

Also please don't use the Ubuntu repository version of torchat, it currently has a dangerous bug (its fixed in Debian already but for Ubuntu I am still waiting). You should download the original .deb from github/prof7bit and then open a console in the same folder where you downloaded the deb and install it with

sudo dpkg -i torchat-0.9.9.551.deb

This will remove the previously installed Ubuntu package and replace it with the original upstream version.

---

### Post by 7bit on 2012-06-13
From doing a quick google search It seems it can be  necessary in Unity or Gnome 3 to install a separate package or apply  some configuration regarding some kind of panel icon "whitelist" (WTF???) to  your panel bars so that they are actually able to show such essential things as tray icons.  

Normally the freedesktop standard would dictate that any desktop  environment has a systray where applications can show an interactive icon but it seems Ubuntu does not like to conform to any standards anymore lately. TorChat expects to be run in a standards compliant desktop environment where there is a systray. 

Google for "Unity tray icon missing" or similar search terms and you might find hints for what to do to get the systray back, other applications seem to be suffering from the same Ubuntu bug of missing the systray (I don't use Unity or Gnome myself so I cannot help).

---

