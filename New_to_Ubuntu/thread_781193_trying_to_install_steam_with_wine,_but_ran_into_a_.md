---
title: "trying to install steam with wine, but ran into a wall..."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by fignig on 2008-05-04
how exactly do i do this:

and clicking on Install button. If the Gecko engine doesn't download (servers are down) then download wine_gecko.cab to the "/tmp" directory and point Wine to it (save this as-is to the "/tmp/file.reg" then import with command 'regedit /tmp/file.reg':

[HKEY_CURRENT_USER\Software\Wine\MSHTML]
"GeckoUrl"="z:\\tmp\\wine_gecko.cab"

i put the file wine_gecko.cab in the /tmp folder. and how do i point wine to it and save this as-is? i just don't get the wording. or maybe the concept, but i'm trying to learn.

---

