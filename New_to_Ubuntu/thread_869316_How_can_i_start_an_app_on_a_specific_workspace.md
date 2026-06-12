---
title: "How can i start an app on a specific workspace?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Bodsda on 2008-07-24
Hi, as alot of people, i have 4 workspaces/desktops (4 faces of the cube) can i start a app on a specific workspace? eg, how would i start (from terminal) xchat on workspace 2?

Thanks

Bodsda

---

### Post by sdennie on 2008-07-24
You can.  First install ccsm:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects.  In the "Place Windows" plugin there is a tab for specifying window placement.  An example entry would be "class=xchat".

---

