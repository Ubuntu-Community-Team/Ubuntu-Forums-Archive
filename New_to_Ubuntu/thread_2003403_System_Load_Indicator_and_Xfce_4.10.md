---
title: "System Load Indicator and Xfce 4.10"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by vasa1 on 2012-06-14
**Admission**: I've posted this [here]("http://forum.xfce.org/viewtopic.php?pid=26694#p26694") as well but since uploading images is more convenient here, I'm trying here as well.
[center]++++++[/center]

I'm on Ubuntu 12.04 and running Xfce 4.10 session. I installed Xfce 4.10 from the launchpad ppa ([https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)). My system is fully updated.

I'm having a problem with how System Load Indicator 0.2 (from the Ubuntu Software Center) displays in an Xfce session.

I find that as I progressively increase the number of parameters displayed, the area of each component shrinks instead of remaining the same size. The rest of the Xfce panel is unaffected.

In contrast, when I run an Ubuntu (Unity 3D) session, there is no shrinking of areas.

I've marked the System Load Indicator in red in the images. I've put up 5 images:
first Xfce, just %CPU usage selected
second Xfce, added Memory
third Xfce, added Network
fourth Xfce, added everything
fifth, the Unity 3D panel with everything

As I keep adding features, the System Load Indicator graphic seems to shrink. Even with just two features, the graphic isn't readable.

---

### Post by mastablasta on 2012-06-14
can't you increase the size the indicator takes on the panel?

---

### Post by vasa1 on 2012-06-14
> **mastablasta said:**
> can't you increase the size the indicator takes on the panel?
There is a setting in Preferences to alter the "system monitor width" from 10 pixels upwards, but it doesn't help. The graphical area actually decreases in size when I increase the width.

Edit: and it's unnecessary when running Unity 3D.

---

### Post by vasa1 on 2012-06-17
Bump.

---

### Post by vasa1 on 2012-06-17
I filed [https://bugzilla.xfce.org/show_bug.cgi?id=9040](https://bugzilla.xfce.org/show_bug.cgi?id=9040). Thanks for looking into the issue, Toz! :)

---

