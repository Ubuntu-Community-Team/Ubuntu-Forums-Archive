---
title: "[SOLVED] where can i download desktop cube"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by JKSnort on 2008-09-20
where do i get desktop cube for Ubuntu?

add remove game me other programs, but i didn't see it there

o and what is a good flash animation program i could get for Ubuntu?

thanx

---

### Post by sayakb on 2008-09-20
Do you have desktop effects (animations) running? If so, then at a terminal, type in:
```
sudo apt-get install compizconfig-settings-manager
```
Press Alt+F2, and type in **ccsm**. In the settings manager window, enable Desktop Cube, Rotate Cube, Cube Caps. Also under General Options->Desktop Size, set the Horiz virtual size to 4.

---

### Post by guywithcable on 2008-09-20
Go to System -> Administration -> Synaptic Package Manager

Once there search for compizconfig-settings-manager and install that package.

Once installed, go to System -> Preferences -> CompizConfig Settings Manager (I think this might be called Advanced Appearance Settings or something else on some other systems.)

Now check Desktop Cube and Rotate Cube under the Desktop section.

You can use the buttons next to the checkbox to configure them.

---

### Post by bumanie on 2008-09-20
Follow [this guide]("http://www.neohide.com/ubuntu-desktop-effects-for-hardy-heron") to enable desktop effects

---

### Post by guywithcable on 2008-09-20
If you increase the number of desktops to 16, you could get a desktop octadecahedron! :)

(I think that's what it would be called.)

---

