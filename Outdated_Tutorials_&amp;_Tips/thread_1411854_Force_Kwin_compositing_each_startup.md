---
title: "Force Kwin compositing each startup"
date: 2010-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by samantha_ on 2010-02-20
Sometimes, kwin compositing is mysteriously turned off when logging out.
The next time you login, you have to manually enable it again.
Ive designed a script, based on [http://ubuntuforums.org/archive/index.php/t-1224822.html](http://ubuntuforums.org/archive/index.php/t-1224822.html)
to fix this.

Steps.
1. Open a terminal
2. type in 
```

nano ~/.kde/Autostart/enable_compositing.sh

```
copy and paste this onto the terminal
```

#!/bin/bash

if [ "$(qdbus org.kde.kwin /KWin compositingActive)" == "false" ];
then
qdbus org.kde.kwin /KWin toggleCompositing
fi
if [ "$(qdbus org.kde.kwin /KWin compositingActive)" == "false" ];
then
qdbus org.kde.kwin /KWin toggleCompositing
fi

```
Ive done it twice, because sometimes it needs to be run twice to work properly (dunno why)

3. Save it by pressing Ctrl + X, then enter "y"
4. run 
```

chmod 647 enable_compositing.sh
```

disable the kwin compositing, restart, and youll find it running already !

---

