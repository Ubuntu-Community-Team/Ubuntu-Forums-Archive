---
title: "Extending My Desktop across 2 Displays"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Lee05162004 on 2008-11-03
I have a laptop with an ATI Radeon Express 200m graphics card in it and it also has a vga out. What I would like to do is to extend my desktop via the vga out to my tv which has a vga input on it. As of right now I am able to clone the original desktop but wwhat I would like to do is be able to set up the displays so I can move programs over to the 2nd display. For example, right now I'm watching a movie but would also like to have Firefox and Pidgin up on my laptop monitor. After the 8.10 upgrade I have the ATI Catlyst Control Center available but it does not give me the option to extend the desktop, only to clone it. Am I just missing something here? Do you have any suggestions? Thanks for the help.

---

### Post by jpeery on 2008-11-13
BUMP, I'm having the same issue.  Any help?

---

### Post by pzs on 2008-11-13
Nvidia cards can do this using a TwinView (that's what I use) but you can also do it using a tool for X called Xinerama. If you Google for xinerama tutorials, you should find something to help you out.

---

### Post by alternotgoto on 2008-11-15
Try add this to the bottom of you /etc/X11/xorg.conf using your favourite editor under sudo.

Section "ServerFlags"
       Option "Xinerama" "true"
EndSection


Once complete then Alt-Ctrl-Backspace to restart you X server

---

