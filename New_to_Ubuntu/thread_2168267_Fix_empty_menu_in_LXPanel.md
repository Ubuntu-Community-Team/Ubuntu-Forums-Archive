---
title: "Fix empty menu in LXPanel"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by Kanefa on 2013-08-17
I'm running 

```

#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p LXDE &
```

from [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel).  It states it will kill lxpanel, delete the current menu cache, and restart lxpanel.

I've changed LXDE to Lubuntu, but another than that I have copy and pasted the script.  What happens is it kills the lxpanel and then reloads it and "hangs" in the terminal.  None of the buttons in the newly loaded main menu work.  When I do click them the terminal writes out "Error: LXSession is not running."

---

