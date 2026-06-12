---
title: "Not remembering keyboard layout"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by pepplewick on 2008-04-30
Anyone else experiencing this is Hardy Heron. I'm using a basic Cherry PS/2 keyboard and on boot up it works but certain keys function oddly...the most annoying being the @ key which gives me " instead. When I go into Layout and set it to a basic British Keyboard all is well. Then once I reboot it's forgotten the settings and reverts. I know the keyboard's fine because I use XP on another partition it has no issues. Any thoughts? Thanks.

---

### Post by bluefrog on 2008-05-13
in a terminal
sudo dpkg-reconfigure console-setup

choose your british keyboard, accept the other things by default.

your keyboard will be the same in console or underneath X

---

