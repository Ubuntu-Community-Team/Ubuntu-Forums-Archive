---
title: "HOWTO: XFWM4 with fancy (and fast) composite manager in Gnome"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by JimmyJazz on 2006-06-03
I orginally posted this under the Dapper section so I decided to repost it here since that section is close.

---------------------------------------------------------------------------

this is just a quick little tip, you can get some amazing looking composite magic with XFWM4 now, not to major a major improvement in speed

just enable compositing in Xorg.conf by adding the following lines...

```
Section "Extensions"
        Option      "Composite" "Enable"
EndSection
```

install xfwm4 (read this guide)...

[http://ubuntuforums.org/showthread.php?t=88393]("http://ubuntuforums.org/showthread.php?t=88393")

to tweak the settings  run "xfce4-settings-show" then select "Window Manager Tweaks"

you can get some great looking shadows and transparencies as well adding desktop boundries. Check out my screen shot...

[[IMG]http://jimmyjazz.homeip.net:808/xfwm4shot_th.png[/IMG]]("http://jimmyjazz.homeip.net:808/xfwm4shot.png")

---

### Post by barbarian on 2006-06-03
Thanks looks really cool I'm going to prove it on my Xubuntu machine.

---

### Post by xXx 0wn3d xXx on 2006-06-03
Everything went fine but I don't have the composite manager/shadown option.

Edit:I lost my DRI support for my ATI Radeon Xpress 200M card after switching wms. I get this message:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

