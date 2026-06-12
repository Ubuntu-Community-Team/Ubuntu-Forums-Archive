---
title: "Strange mouse behavior"
date: 2017-09-02
forum: New to Ubuntu
---

### Post by 5n31d3r on 2017-09-02
Hello people!
After last updtates, I've got this trouble: left mouse click &#1072;lways reacts only the second time(first_ left _click - nothing happens, second click - all OK, and this is for everythyng: open/close new programm, open/close folders in Nautilus, shut down, minimize etc... in a word everything that needs to be reacted on a first left-click, not make that). The mouse is OK(I checked 3, also on another PC). Situation with touchpad(I have notebook) is the same:(. Did anyone has the same problem and/or know the solution? Help me, please.
Thank You!
I have Ubuntu Desktop 16.04 x64.

---

### Post by BenginM on 2017-09-04
Hiya , welcome to the forums.

try with a previous or newer kernel , do you have other input devices attached , if so try to remove them and reboot without them and in a terminal run: $ tail -f /var/log/dmesg .. and preform left clicks and look for logs related to the mouse.

---

### Post by 5n31d3r on 2017-09-06
**BenginM **on "[COLOR=#000000]tail -f /var/log/dmesg" , I got:"[/COLOR](Nothing has been logged yet.)" nothing more(.

---

