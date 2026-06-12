---
title: "Unable to install device manager"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by rltkmkc on 2008-07-20
Hi I'm new to Ubuntu. I've read through a couple of posts about installing a device manager. They gave a couple of commands that your suppose to run in terminal but when I try sudo apt-get install gnome-device-manager I get an error "E: Couldn't find package gnome-device-manager". When I try running "sudo gnome-device-manager" I get another error "sudo: gnome-device-manager: command not found". Which I'm assuming is because the first failed. So what am I doing wrong? Thanks Rodger

---

### Post by MattBD on 2008-07-20
It show as being in the Universe repository. Have you enabled this repository?
To enable it, open Synaptic, go to Settings>Repositories and check the box for it. It'll prompt you to reload the software sources, then you should be able to install it, either using Synaptic or apt-get from the command line.

---

### Post by rltkmkc on 2008-07-20
MattBD thanks for the fast reply. When I went to Settings>repositories the box was already checked for "community-maintained open source software (universe)". Is that the box you wanted me to see if was checked?

---

### Post by MattBD on 2008-07-20
> **rltkmkc said:**
> MattBD thanks for the fast reply. When I went to Settings>repositories the box was already checked for "community-maintained open source software (universe)". Is that the box you wanted me to see if was checked?

Yes, that's it.

If you close Synaptic, then run the following command:
```
sudo apt-get update
```
followed by:
```
sudo apt-get install gnome-device-manager
```
That should do the trick. I'm assuming you're running Hardy Heron here.

---

### Post by rltkmkc on 2008-07-20
Hardy Heron? I'm really new to Ubuntu. I installed Ubuntu 7.10-the Gutsy Gibbon. I assume Hardy Heron is a different version. Should I change? I can always reinstall isn't like I have a lot installed in this version I'm just starting to learn linux.

---

### Post by rltkmkc on 2008-07-20
I'm downloading 8.04.1 to catch up. I'll reinstall it once it's done. Maybe that will solve my problem thanks

---

### Post by MattBD on 2008-07-20
Yes, Hardy Heron is the current version. It may be that the gnome-device-manager package isn't in Gutsy. If so, that would be why you can't install it.
I'd download Hardy and try it out, after all you might as well have all the up to date features (believe me, Firefox 3 alone is worth downloading it for, it's way faster than FF2). If you have any kind of technical problems you can always go back to Gutsy.

---

### Post by rltkmkc on 2008-07-20
Thanks MattBD that fixed the problem.

---

