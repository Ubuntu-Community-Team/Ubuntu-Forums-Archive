---
title: "Keyboard not recognized after driver update =*("
date: 2017-12-23
forum: New to Ubuntu
---

### Post by langendoerfer on 2017-12-23
I broke it...
I'm on a lenovo t430 and Ubuntu 16.04, after installing the latest synaptic driver to try and fix my touchpad issues my keyboard no longer works after the re-start. The keyboard is recognized in grub & W10 on a separate partition. How can I revert this driver, in recovery mode the keyboard is working in the terminal but i'm at a loss with where to go from here. I would greatly appreciate any guidance

---

### Post by langendoerfer on 2017-12-23
update
I followed the following:

sudo apt-get remove synaptic*
sudo apt-get purge synaptic*
sudo apt-get autoremove
sudo apt-get autoclean

to no avail... Still no keyboard recognition at log-in

---

### Post by langendoerfer on 2017-12-23
thank you google-fu;

sudo apt install xserver-xorg-input-all

solved my problem... However my touchpad functions are still not working, which is what let me into this situation initially. Double tap on the track pad still does not work.

---

