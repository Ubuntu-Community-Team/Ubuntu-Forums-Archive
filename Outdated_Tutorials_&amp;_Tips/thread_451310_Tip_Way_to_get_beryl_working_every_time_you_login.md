---
title: "Tip: Way to get beryl working every time you login"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by SomethingCronic on 2007-05-22
This is just a very small tip for anyone else who has had a problem with beryl crashing out or reverting to a standard window manager when you set 'beryl-manager' to run from startup.(Basically, I've found when I want kiba-dock and beryl to load automatically at login, sometimes beryl doesn't load properly and I'm left with large black space on the bottom of the screen where kiba-dock loads)

by creating a pause between loading beryl and kiba I was able to load both applications perfectly, with no problems since. I created a script:

---
```
#!bin/bash
beryl-manager
sleep 4
kiba-dock
```---

save this as startupscript.sh then make sure it's executable by:

```
chmod ugw+x startupscript.sh
```

Remove kiba-dock and beryl-manager from your sessions list, and add ~/startupscript.sh

Reboot, and it should just work.

-Mike

---

