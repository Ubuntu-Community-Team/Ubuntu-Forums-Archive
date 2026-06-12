---
title: "Monitor and video card suppors 1900x1200"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by Iain Banks on 2013-06-30
Hello,

just recently installed Ubuntu and when I go into the Display settings I cannot seem to set it to 1900x1200.

On windows I can do this just fine so clearly my monitor and video card supports the resolution. How would I go about setting this to be my resolution as currently everything looks out of focus.

---

### Post by deadflowr on 2013-06-30
Do you know what graphics card you have?

If not, open a terminal and enter this
```
lspci | grep VGA
```

To open a terminal, either try [pressing "ctrl+alt+T", or press the windows button to open the dash/search window and type terminal, then launch the terminal.

---

### Post by Iain Banks on 2013-06-30
> **deadflowr said:**
> Do you know what graphics card you have?

If not, open a terminal and enter this
```
lspci | grep VGA
```

To open a terminal, either try [pressing "ctrl+alt+T", or press the windows button to open the dash/search window and type terminal, then launch the terminal.

VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)

---

### Post by deadflowr on 2013-06-30
And what version of Ubuntu are you running?
12.04, 12.10, or 13.04.

I ask because each one might have differing drivers and methods to install them.

---

### Post by Iain Banks on 2013-06-30
13.04.

---

### Post by deadflowr on 2013-06-30
Ok.

Try opening the dash menu (press the windows button on the keyboard, or click on the icon at the top of the launcher on the rightside of the desktop)
and type "software and updates".
The software and updates should show up, NOT software updater.(this runs the updater program, which you don't want).
If the software and updates doesn't show up, try "system settings"
If system settings, open it and go down to software sources, open it.
A new window will open and the last tab is additional drivers, select it and wait for it to run it's thing, when it's ready it'll show a list of drivers you can try for your card.
Best bet is to select the recommended driver and then select activate.
Enter your password and let it install.
When it's done, it'll ask you to reboot.

When rebooted a new program should be install called nvidia xserver settings. This is the nvidia driver control panel, your setting should be settable here.

If at any point trouble occurs look over this 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Added: If it doesn't say recommended, look at ones that say tested.

---

### Post by Iain Banks on 2013-06-30
> **deadflowr said:**
> Ok.

Try opening the dash menu (press the windows button on the keyboard, or click on the icon at the top of the launcher on the rightside of the desktop)
and type "software and updates".
The software and updates should show up, NOT software updater.(this runs the updater program, which you don't want).
If the software and updates doesn't show up, try "system settings"
If system settings, open it and go down to software sources, open it.
A new window will open and the last tab is additional drivers, select it and wait for it to run it's thing, when it's ready it'll show a list of drivers you can try for your card.
Best bet is to select the recommended driver and then select activate.
Enter your password and let it install.
When it's done, it'll ask you to reboot.

When rebooted a new program should be install called nvidia xserver settings. This is the nvidia driver control panel, your setting should be settable here.

If at any point trouble occurs look over this 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Added: If it doesn't say recommended, look at ones that say tested.

How long should it take to install?

---

### Post by deadflowr on 2013-06-30
Installation time depends on your internet connection speed, as it downloads the files and installs them.

---

### Post by lyianx on 2013-06-30
> **deadflowr said:**
> Ok.  Try opening the dash menu (press the windows button on the keyboard, or click on the icon at the top of the launcher on the rightside of the desktop) and type "software and updates". The software and updates should show up, NOT software updater.(this runs the updater program, which you don't want). If the software and updates doesn't show up, try "system settings" If system settings, open it and go down to software sources, open it. A new window will open and the last tab is additional drivers, select it and wait for it to run it's thing, when it's ready it'll show a list of drivers you can try for your card. Best bet is to select the recommended driver and then select activate. Enter your password and let it install. When it's done, it'll ask you to reboot.  When rebooted a new program should be install called nvidia xserver settings. This is the nvidia driver control panel, your setting should be settable here.  If at any point trouble occurs look over this  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)  Added: If it doesn't say recommended, look at ones that say tested.  And what if it doesnt load any additional drivers?  im using on board video : Intel Corp Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller on 13.04. (also my onboard sound isnt right. There is noise, but voices seem displaced).

---

### Post by deadflowr on 2013-06-30
> **lyianx said:**
> And what if it doesnt load any additional drivers?  im using on board video : Intel Corp Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller on 13.04. (also my onboard sound isnt right. There is noise, but voices seem displaced).

Intel provides open-source drivers only, so what you have is what you'll get.
Additional drivers installs close source drivers.

---

### Post by Iain Banks on 2013-06-30
Fixed it and its now looking splendid thanks.

---

### Post by deadflowr on 2013-06-30
Nice to hear.

If any other issues arise you can look over the link to the howto I provided for the nvidia cards
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And if the solution holds, follow this thread, post#2 should suffice, on how to mark this thread as solved
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

Good luck and you know where you can go to get help.

---

