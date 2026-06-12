---
title: "[SOLVED] Got myself stuck on upgrade"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by intalekshul on 2008-07-04
I'm in an upgrade Konsole window.it was installing the upgrades configuring samba-common. Asked me what to do about installing the new version or keeping the locally modified version. I mistakenly selected #5 start a new shell to examine the situation. Now I'm in a root shell and I don't know what to do. How can I get back and choose #1 install the package maintainers version?

---

### Post by milosz.galazka on 2008-07-04
So you are using KDE, opened Konsole terminal and run which command?

---

### Post by ChameleonDave on 2008-07-04
We can't see what you can see.

---

### Post by intalekshul on 2008-07-04
I'm using KDE Kubuntu, upgrading to Hardy Heron version.During the upgrade after "getting new packages" while "installing the upgrades" install program opened up a konsole window informing me "setting up this, setting up that". When it got to "setting up samba-common" there was a new version of smb.conf, but the installed version had been locally modified. Asked me what I wanted to do?
1. Install the new one
2. Keep the old one
3. Show the differences
4. Show a side by side difference
5. Start a new shell to examine the situation
I hit 5 by mistake instead of 2.
How do I get back to choosing 2 or stopping this shell? I'm just sitting at a root# prompt

---

### Post by ChameleonDave on 2008-07-04
> **intalekshul said:**
> I'm using KDE Kubuntu, upgrading to Hardy Heron version.During the upgrade after "getting new packages" while "installing the upgrades" install program opened up a konsole window informing me "setting up this, setting up that". When it got to "setting up samba-common" there was a new version of smb.conf, but the installed version had been locally modified. Asked me what I wanted to do?
1. Install the new one
2. Keep the old one
3. Show the differences
4. Show a side by side difference
5. Start a new shell to examine the situation
I hit 5 by mistake instead of 2.
How do I get back to choosing 2 or stopping this shell? I'm just sitting at a root# prompt

You've just told us what led up to this, but you still haven't really described the current situation.  Am I going to have to modify smb.conf, reinstall samba, and press 5, just to see what options you have?

Edit: I have done as I said.  I reinstalled samba from the command line.  When I hit 5, it sent me back to the command line.  I typed exit, and it sent me back to the list of options where I could choose which version I wanted.

I imagine you are using Synaptic rather than apt-get on the command line, but I bet that it is exactly the same.  Simply exit the shell by typing "exit", and you will be back at the menu.

---

### Post by intalekshul on 2008-07-04
Thank you, I was afraid Exit would shut the whole process down. Thanks again.

---

