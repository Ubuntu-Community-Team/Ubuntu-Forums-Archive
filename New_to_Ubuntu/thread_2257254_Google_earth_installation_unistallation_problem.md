---
title: "Google earth installation unistallation problem"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by rbg2 on 2014-12-18
I am a complete beginner to using ubuntu/ linux and so far the learning curve has been very challenging. I am on a 64bit ubuntu 12.04 laptop. I recently downloaded most recent 64bit google earth which crashed a couple of times before working. So i removed it using sudo apt-get remove google-earth-stable. I then proceeded to download 32bit google earth but that one was no good either, when i tried to unistall it using the same command before it just says package google-earth-stable is not installed. However if I type $ dpkg -l | egrep "google" on the command line I still get this line,
ii  google-earth-stable:i386                    7.1.2.2041-r0                       Explore, search and discover the planet
I also tried to remvoe google earth from the software centre but it just says "Breaks existing package 'google-earth-stable:i386' conflict: google-earth-stable()" and no button to uninstall it. I don't really understand whats is happening. Could anyone help me unistall this program? Thanks

---

### Post by oldos2er on 2014-12-18
Try ```
sudo dpkg -r google-earth
``` If it throws an error please copy/paste all the terminal output here.

---

