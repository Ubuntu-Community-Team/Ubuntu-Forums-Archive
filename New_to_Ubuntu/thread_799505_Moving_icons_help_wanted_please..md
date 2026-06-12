---
title: "Moving icons help wanted please."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by steve63 on 2008-05-19
Hi Everybody,
Just loaded Ubuntu 8.04 onto a 50GB partition and haven't booted into the Vista partition since, great OS, everything just seems to work without any hassle. Anyhow one thing is currently defeating me. I have loaded Avant Window Navigator and put lots of icons onto it (as it reminds me of my Mac) and managed to move the waste bin from the taskbar onto the desktop using nautilus via the gconf-editor (Googled that one) but cannot do the same for the power/log off icon. It is not locked to the taskbar and when I drag n drop it onto the desktop (after r clicking it and clicking move) it just moves itself back onto the taskbar. Can this be done?? Ideally I'd like to put it onto the Avant bar but it does the same for that too.
Thanks for any help,
Steve.

---

### Post by shadow-of-sin on 2008-05-19
To add a power off/quit button onto the avant dock, just right click on the dock, click on Preferences, go to Applets, scroll down to the Quit/logoff applet and then click on "Activate".

---

### Post by steve63 on 2008-05-19
Hi, thanks for the reply. When I follow your instructions to the applets page all I have is one applet available and active, the launcher/taskmanager manager, there is nothing else to select or scroll down to?? If I click on the + sign to add an applet all that does is open up a window asking me which folder to select an applet from??

---

### Post by shadow-of-sin on 2008-05-19
You must install the extra applets, type this in a terminal window:
```
sudo apt-get install awn-extras-applets-trunk
```

---

