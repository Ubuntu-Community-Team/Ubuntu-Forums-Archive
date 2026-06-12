---
title: "nvidia-glx-new and xserver-glx in hardy"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by AlokaParyetra on 2008-07-25
I kinda new to this stuff, so i'm just looking for an explanation.

What's the deal with the nvidia-glx and the xserver-glx? What does each do? Can they both be running?

Right now i have both installed. Certain things seem to be running faster (like compiz and stuff), but some games are running slower.

Before, i had just the nvidia drivers installed (from the ubuntu repositories), and i had the opposite going on (faster games, slower compiz).

Also, after installing xserver-glx, i noticed some strange lines appearing at the top of windows when i move it around or switch desktops using the cube.

So, should i keep xserver-glx or not?

P.S. if important, graphics card is nvidia 8-something.

---

### Post by sdennie on 2008-07-25
There is no need to use xserver-glx with nvidia cards and I recommend uninstalling it.  If you are using a laptop and compiz is frequently choppy while not using xserver-glx, it's likely a problem with PowerMizer that you can fix using this guide:  [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

---

