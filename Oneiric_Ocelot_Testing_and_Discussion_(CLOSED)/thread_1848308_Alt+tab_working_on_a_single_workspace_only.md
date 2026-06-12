---
title: "Alt+tab working on a single workspace only?"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Martin Vysny on 2011-09-22
Hi guys, nice work on Oneiric! I have one question: in Natty the Alt+Tab key-press shows windows on current workspace only. This was changed in Oneiric: it now shows all windows from all workspaces. Is there a way to turn this off (to revert to behavior as in Natty)? I have one krusader opened on each workspace and currently it is kind of guessing game, which krusader will I switch into. Thanks!

---

### Post by dino99 on 2011-09-22
set the workplaces preferences (right click) or reload metacity (metacity --replace &)

---

### Post by Martin Vysny on 2011-09-28
> **dino99 said:**
> set the workplaces preferences (right click) or reload metacity (metacity --replace &)

Thanks... but I no longer use metacity. I'm using Unity 3D on Oneiric. Also, on right click, I can only change a wallpaper - there is nothing resembling "workplaces preferences".

---

### Post by justynbutler on 2011-09-30
If you open compizconfig-settings-manager and navigate to "Ubuntu Unity Plugin" -> "Switcher" and select "bias alt-tab sorting to prefer windows on the current viewport" that will help.

However, I think that an extra default keybinding is needed to switch between windows on the current workspace. I suggest ctrl-alt-tab.

Bug for this issue:
[http://bugs.launchpad.net/unity/+bug/863399](http://bugs.launchpad.net/unity/+bug/863399)

If this affects you please add to the discussion or select the "this bug affects you" option at the top.

---

### Post by bbrg548 on 2011-09-30
> **justynbutler said:**
> If you open compizconfig-settings-manager and navigate to "Ubuntu Unity Plugin" -> "Switcher" and select "bias alt-tab sorting to prefer windows on the current viewport" that will help.

However, I think that an extra default keybinding is needed to switch between windows on the current workspace. I suggest ctrl-alt-tab.

Bug for this issue:
[http://bugs.launchpad.net/unity/+bug/863399](http://bugs.launchpad.net/unity/+bug/863399)

If this affects you please add to the discussion or select the "this bug affects you" option at the top.

Both done!

---

