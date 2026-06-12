---
title: "HOWTO: Automatically mount a drive in Dosbox"
date: 2007-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by wie6Ein0 on 2007-07-17
If you've seen [other]("http://ubuntuforums.org/showthread.php?t=171970") tutorials on how to automatically mount a drive in Dosbox, then erase whatever methods you've learned from your mind. What you're about to read is the easiest, simplest, and fastest way that I've found.

First off, go ahead and install Dosbox if you haven't yet
```
sudo apt-get install dosbox
```Alternatively you can use the Synaptic package manager located in (System -> Administration -> Synaptic Package Manager)

Now, once you have it installed, create a Launcher to Dosbox.
```

1) Right click the desktop.
2) Select "Create Launcher..." from the menu.
3) Fill in the appropriate information

**Type:** Application
**Name:** Dosbox Emulator
**Command:** dosbox
**Comment:** An emulator to run old DOS games

```Alternatively you can use the Launcher created by the program's installation located in (Applications -> Accessories -> Dosbox Emulator)

Now, once you've created (or located) a Dosbox Launcher, we can proceed to the next and final step.

Change the "**Command:**" portion of the Dosbox Launcher from "dosbox" to "dosbox /path/to/dosbox/drive/folder"

In my case, I had my Dosbox folder (where my DOS games are stored) at "/home/weston/.dosbox", so I changed my command from "dosbox" to "dosbox /home/weston/.dosbox"

Now, when you run the application launcher, dosbox will automatically mount the C: drive to the location you specified.

This method can also be preformed using the terminal.

---

