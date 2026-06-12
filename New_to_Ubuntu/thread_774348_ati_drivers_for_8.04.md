---
title: "ati drivers for 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Matt26 on 2008-04-29
i have just updated my ubuntu installation from 7.10 to 8.04 and i ran into a video issue when i was prompted to install a restricted video driver for my ati graphics card (Radeon 9800XT) after the upgrade had completed- once i installed the video driver and rebooted i received a completely blue screen (no taskbar, icons, wallpaper etc) after logging into ubuntu and nothing came up for me, so i used the xfix option to restore my video driver.. is there a way that i can find a compatible driver for my video card?  right now (without the restricted driver installed) i can see my desktop and use applications, but windows are slow to render on the screen, lines are appearing vertically on the screen after menus are opened, and the overall graphic performance is just not good at all.  if anyone has any suggestions as to how i can solve this issue i would greatly appreciate it.  thanks.

---

### Post by JohnoDC on 2008-04-29
I have exactly the problem with my 9550 radeon, the screen goes out of range then i have to restore it to get the screen back.
its as soon as i use the ati accelerated driver, have tryed installing from official website but same results.

---

### Post by Matt26 on 2008-04-30
i just installed the latest drivers from the ati website for linux and the issue is still persisting- does anyone know of how this can be resolved?  my guess is that this is one of those odd hardware issues that has not been encountered by many people to date- the thing is, this issue only began AFTER upgrading ubuntu from 7.10 to 8.04- is it possible that 8.04 does not support this card for some reason (ATI Radeon 9800XT)?  any help would be greatly appreciated.

---

### Post by Saint Angeles on 2008-04-30
i have a different card than you but this should maybe help a little:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by Matt26 on 2008-05-02
thanks for the suggestion- i discovered a way to resolve my video issue.. i downloaded and installed Envy-NG and used it to automatically install the appropriate video drivers for my ATI card- this actually yeilded the same results as my last attempt to install the drivers, so i used xfix to restore my X window config, then used EnvyNG to uninstall the drivers it had just installed, and when i rebooted and logged back in, my desktop was acting normally again- before the upgrade to 8.04.. so i still don't have the ATI driver installed, but it is back to the default driver config which is fine until i can figure out how to get the ATI driver installed successfully (without the blank blue screen that shows up after logging in). weird how resolutions can be discovered purely by accident!

---

