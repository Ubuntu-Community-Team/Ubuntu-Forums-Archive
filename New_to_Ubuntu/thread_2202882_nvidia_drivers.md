---
title: "nvidia drivers"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by swipisnt on 2014-01-31
hello my friends.
simple question it is normal that terminal shown nvidia-current  is already the newest version (used sudo apt-get install nvidia-current command) but Additional Drivers shown that no proprietary drivers are in use on my system?

thank you for your time

---

### Post by egeezer on 2014-01-31
Did you restart after installing the nvidia-current?

---

### Post by swipisnt on 2014-01-31
yes. i have this problem from my ubuntus fresh installation. and i have no problem playing games so i think drivers are working, just additional drivers didnt shown (i guess).

---

### Post by egeezer on 2014-01-31
Seems a bit odd that Additional Drivers doesn't show your nvidia driver. Usually it takes a long time to scan for drivers (progress bar goes back and forth seemingly forever!) and eventually shows you a panel with the lineup.

If you have Synaptic installed, you might check in there (just search on the word nvidia) to see what is marked as installed.

---

### Post by swipisnt on 2014-01-31
synaptec shown that nvidia304, nvidia-current, nvidia-libopencl304, nvidia-opencl304, nvidia setting, settings304, nvidia common and xserver-xorg-video-nouveau-lts-raring are installed. nvidia drivers are different from xserver-xorg? coz both are installed

---

### Post by egeezer on 2014-01-31
Nvidia drivers are what runs Xorg, so you are apparently running on the proprietary drivers.  No idea what Additional Drivers is doing wrong, your installation is apparently running fine.

---

### Post by swipisnt on 2014-02-01
ok thank you very much. if my drivers is ok so i just ignore Additional drivers software.
thanks for help.

---

