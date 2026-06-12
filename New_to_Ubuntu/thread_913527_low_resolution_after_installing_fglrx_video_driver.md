---
title: "low resolution after installing fglrx video driver"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Kronie on 2008-09-07
title says it all. i had some issues with games in wine.. when i start the game, the screen divides into 2 woekspaces and each of them showing identical pictures in horrible quality.. so i remembered that i recently removed my video driver, and thot that that might be the reason why i was getting those issues. so i installed fglrx and after reeeboot, max resolution i can put is 800*600 with 75Hz refresh rate. monitor's native is 1280*1024*75. 
my videocard is radeon X600.

---

### Post by talsemgeest on 2008-09-07
If you are using Hardy Heron, you should restart the computer, and if it has a countdown, puch escape. From there, go into the recovery mode, and choose the option to repair the graphics, which should do it automatically. If that doesn't work, do the same thing again but this time go into the root terminal, and type ```
dpkg-reconfigure xserver-xorg
```
and that should do it.

---

