---
title: "Trying to find a way to make applications always start in the same position and size"
date: 2021-01-23
forum: New to Ubuntu
---

### Post by lelolelo on 2021-01-23
I want apps like Firefox to always start up in the same position and have the same size as last session, is it possible? 
I've tried [this method]("https://www.faqforge.com/linux/tweak-default-size-position-application-window-ubuntu-unity/") but this is not working for firefox.

---

### Post by ActionParsnip on 2021-01-24
Could try devilspie

---

### Post by Impavidus on 2021-01-24
To be pedantic, applications don't start in any particular position or size. Windows open in a particular position and size, but applications may open multiple windows or none at all. When an application wants a window, it asks the window manager to open a window with a particular size, position and title. It may also give an icon for the window, request to disable decorations or use full screen. The window manager then opens a window, if it can, but doesn't necessarily fulfil all requests.

So there are two approaches to this problem. You can tell the window manager to open a window with a particular title always at the same location and same size, or tell the application to always request the same position and size and tell the window manager not to override that. If application and window manager support this.

My Firefox always gets its window in the same position and size as the last time I closed it (the full height of my screen, but somewhat narrower, along the left edge), unless that causes it to overlap with an existing window. That's rarely the case. Firefox gets a big window, so I always give it its own desktop (I've got 15 of them).

---

### Post by lelolelo on 2021-01-24
> **ActionParsnip said:**
> Could try devilspie

Thanks! This was exactly what I was looking for!

---

