---
title: "HOW-TO: Set Docky2 to always show ontop"
date: 2010-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by antman8969 on 2010-06-06
one of the things that annoyed me about docky2 (and docky) was not being able to select an option that disables hiding, but doesn't cause the a maximized window to only maximize
its borders to the start of the dock.

well this will allow you to have a dock thats always visible and always ontop!

open up a terminal and execute these commands:

```
gconftool-2 --set "/apps/docky-2/Docky/Interface/DockPreferences/Dock1/FadeOnHide" --type bool "true"
``````
gconftool-2 --set "/apps/docky-2/Docky/Interface/DockPreferences/Dock1/FadeOpacity" --type float "1"
```you probably have to restart docky to take effect, but that'll do it!

Alternatively, you can open up the gconf-editor and go through the above file path and change it manually, just as easy.

---

