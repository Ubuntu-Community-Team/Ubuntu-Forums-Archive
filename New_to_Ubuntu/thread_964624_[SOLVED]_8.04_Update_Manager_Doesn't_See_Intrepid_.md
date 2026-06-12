---
title: "[SOLVED] 8.04: Update Manager Doesn't See Intrepid Upgrade"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by REDace0 on 2008-10-31
This is really baffling. I have the option in Software Sources set to "Normal Releases" on both of my computers. My desktop found it and upgraded with no problems, but my laptop can't see the update for some reason. Since they essentially have the same packages installed, I really don't know what could be causing this. Any ideas?

---

### Post by SunnyRabbiera on 2008-10-31
you more or less need to set up for distribution upgrades, but my advice is if you are a newer user stick to hardy for now till some bugs are fixed

---

### Post by Bakon Jarser on 2008-10-31
sudo apt-get dist-upgrade

---

### Post by guix on 2008-10-31
```
Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Software Sources

   2. click on the "Updates" tab and change "Show new distribution release" to "Normal releases"

   3. Start System/Administration/Update Manager

   4. Click the Check button to check for new updates.

   5. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.

   6. A message will appear informing you of the availability of the new release.

   7. Click Upgrade.

   8. Follow the on-screen instructions.
```

---

### Post by REDace0 on 2008-10-31
Perhaps I wasn't clear. I upgraded my desktop with no problems. I have tried the command-line approach as well, and the network upgrade (which is what I did on my desktop). It appears that, for whatever reason, when I update my package lists it simply doesn't see Intrepid. I'm gonna go fiddle around with aptitude. Thanks to those who posted in the interim.


**UPDATE**
I got 'sudo apt-get dist-upgrade' to do something by manually editing /etc/apt/sources.list to point to 'intrepid' instead of 'hardy'. Let's see if this works.

**UPDATE2**
That worked. I edited just the us.archive.ubuntu.com/ubuntu locations to intrepid first. That got most of it. I changed the rest of the 'hardy's to 'intrepid's and am doing a 'sudo apt-get dist-upgrade' now. It appears to be working just fine. How do we mark this one "SOLVED"? (Nvm. I figured it out).

---

