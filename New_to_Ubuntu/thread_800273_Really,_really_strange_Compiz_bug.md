---
title: "Really, really strange Compiz bug"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Fixman on 2008-05-19
Happens that, each time that I reboot the computer, the window decoration plugin turns the window shadow color to an ugly pink! If I check ccsm, it tells me that the shadow color it transparent (and if I change to another color, say, black transparent, it just works until the next reboot). What can this be? Help!

EDIT: 500 posts w00t.

---

### Post by EXCiD3 on 2008-05-19
Could be video driver issues. What card and driver are you using?

---

### Post by sdennie on 2008-05-19
If you are using nvidia, this is a known problem.  One thing you could try would be to make a startup script that waits a few seconds and then sets the shadow color.  Something like the following might work but, I have no way to test it:

```

#!/bin/bash

gconftool-2 --type=string --set /apps/compiz/plugins/decoration/allscreens/options/shadow_color "#ffffff00"

sleep 5

gconftool-2 --type=string --set /apps/compiz/plugins/decoration/allscreens/options/shadow_color "#000000ff"

```

---

