---
title: "Nvidia graphics problem"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by potixl on 2013-11-08
Hi all,
I have a Lenovo G580 which has the Intel HD Graphics and Nvidia GT635M videocards
I recently installed Ubuntu, but i noticed my PC detected only my Intel HD Graphics

I tried to install the Nvidia drivers by installing nvidia-current and nvidia-settings, but when i restart and login, my interface doesn't show up (i just see a black screen and my cursor).

Can anybody help me to find out if my Ubuntu can see the Nvidia cards and to install the drivers.

Also, if my Nvidia card works, how can i switch betwee the 2 graphic cards when needed?

Thank you very much.

---

### Post by CatKiller on 2013-11-08
You'll probably want to check out bumblebee for your Optimus setup.

---

### Post by shabuboy on 2013-11-08
I am a beginner, but I would try this...
- Hit shift key during bootup, and go to the recovery option and command line
- uninstall whatever you installed.
- If you are able to boot up normally, run the 3rd party app drivers and see if your Nvidia is listed.

Also see if this helps...
[http://askubuntu.com/questions/352093/need-to-deactivate-nvidia-driver-from-recovery-mode-or-using-ubuntu-12-04-instal](http://askubuntu.com/questions/352093/need-to-deactivate-nvidia-driver-from-recovery-mode-or-using-ubuntu-12-04-instal)

---

