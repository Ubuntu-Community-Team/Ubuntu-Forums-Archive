---
title: "Lost my desktop and wireless"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by Ceeb on 2013-05-26
I have a system 76 Lemur laptop and I am a *total computer idiot*. Yesterday I think I tried to download a command to open compressed files, but either it failed or I didn't completely finish installing it. The next time I opened the computer, the desktop was gone. I tried rebooting it, but that just got rid of my wireless, too. Clearly fumbling my own way through this mess is making it worse.  

All my documents are still in there; so I assume all's not lost, and even if it were, that's ok, too; my important documents are all saved to Google Docs anyway.

Can anyone help me get the computer up and working again? It would really be fine if I just started over from scratch.

Thanks in advance!

Ceeb

---

### Post by ajgreeny on 2013-05-26
Assuming you are using a standard ubuntu system try running ```
sudo apt-get install --reinstall ubuntu-desktop
``` Use Ctrl+alt+T for a terminal if you are in a GUI with a garbled desktop, or just login to the command line if that is where you are ending up at boot, and then run that command from there.

---

### Post by Ceeb on 2013-05-26
holy crap, that worked! Thank you! Whew! And all my documents are still there, so double awesome. 

The wireless is still out; any suggestions? When I click the icon it says "wireless is disabled by hardward switch."

---

### Post by ajgreeny on 2013-05-27
I'm glad you're half way there!

Let's see the output of ```
lspci
sudo lshw -c network
```  for your network hardware.

---

