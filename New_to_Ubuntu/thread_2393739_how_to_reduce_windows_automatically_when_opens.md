---
title: "how to reduce windows automatically when opens"
date: 2018-06-07
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-07
is there any way to have the windows set to open at a certain size?  it seems like chromium or libre writer opens full screen.  i always have to resize.  anyway of fixing this?  thank you.

---

### Post by vanadium on 2018-06-07
Unfortunatelly it is not that obvious to take your own control over how windows open the first time. The behaviour partly depends on the Window manager, but may also be determined by the application. On gnome, the behaviour usually is more or less that the previous state is remembered. So if you fully close either firefox or LO with unminimized window, next time these apps should start unminimized.

I am currently controlling a few windows using the venerable devilspie program on Ubuntu gnome desktop. Users of the compiz window manager, the WM used by Unity desktop, but can also be used with Mate and xfce, have the possibility to define windows rules in the Compiz Config Setting Manager.

---

### Post by bodhin2 on 2018-06-07
some things work and some don't - libre office and chromium for example....  open full tilt screen everytime......

---

### Post by vanadium on 2018-06-07
For me it works on Ubuntu 18.04 Gnome for LibreOffice. Don't have Chromium. You did not indicate what desktop you are using.

---

### Post by bodhin2 on 2018-06-20
reg ubuntu - gnome.  10.04.  yes the windows are all over the place as how they work when they open and also where they open.  thanks - anymore niblles - would be appreciated.

---

### Post by vanadium on 2018-06-23
You might try some tricks. In dconf editor, set org.gnome.mutter center-new-windows to true - this should cause windows to be launched centered instead of on a "smart" place. Also, set org.gnome.mutter auto-maximize to false, to avoid that large windows automatically get maximized. Don't know how well this may work, because in many cases applications determine their window position.

---

### Post by bodhin2 on 2018-06-23
ok thanks but messing with that stuff might just cause more issues for me to try to fix and then more hlel needed by forum members.  trying to live with it as it is.

---

### Post by vanadium on 2018-06-25
It is your choice, but dconf settings are fully reversible and can if the need arises all be reset to factory default with one command.

---

### Post by bodhin2 on 2018-06-25
thanks vandaium. I know so little command line stuff even after 10 plus years of linux that if everything is generally working pretty sweet - then just din't break stuff.  :-)

---

