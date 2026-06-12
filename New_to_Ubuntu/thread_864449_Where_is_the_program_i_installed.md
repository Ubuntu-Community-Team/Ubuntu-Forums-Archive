---
title: "Where is the program i installed?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by mdmytryk on 2008-07-19
I just installed Pulse Audio Volume Control through Add/Remove programs. Now that its installed, i cant seem to find where it is. Its not under Applications>sounds &video nor is it under any System>admin or prefs.  When i do a search for it, i cant find an executable file to open it.  Where the heck is it?

thanks for the help

---

### Post by rockerphil on 2008-07-19
why not just install ALSA? it works fine for controling sound volume, just run this in terminal

sudo apt-get install alsagui

and i know for a fact that will show up

---

### Post by mevets on 2008-07-19
you should run:
```
pavucontrol
```

---

### Post by NikoC on 2008-07-19
What if you do ALT + F2 and then type: pavucontrol ?

You could add this item to your menu manually via right clicking the main menu...
Got the information [here]("https://wiki.ubuntu.com/PulseAudio").

Cheers.

---

### Post by Ekeluo on 2008-07-19
You might need to install pulseaudio device chooser (padevchooser) and its recommended packages (if it's not already installed). Should show in system tray when opened. Left-click (not right-click) to open menu and select volume control.

---

### Post by mdmytryk on 2008-07-19
I didnt even think to run it from the terminal.  And sure enough, after installing the chooser it was right there.

Thanks for the prompt help guys, much appreciated.

---

### Post by sdennie on 2008-07-19
For future reference, when I install packages and can't figure out what commands they have installed, I generally use this to find the binaries:

```

dpkg -L name_of_package | grep bin/

```

---

