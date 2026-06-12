---
title: "Problems with a shell script"
date: 2007-10-05
forum: Programming Talk
---

### Post by daltocli on 2007-10-05
Heya,

I'm running FluxBox currently, mainly so I can keep everything at a minimum for gaming.

One thing I found quite useful in KDE was yakuake, however I don't want to install all the libs, etc. So instead I found this script:

```
#!/bin/bash
if wmctrl -l | grep "PopUp"
        then wmctrl -v -c "PopUp" && exit
        else urxvt +sb -bl -geometry 127x30+2+0 -T "PopUp" -e screen -d -R popup
fi
```

I bound this to F12 in FluxBox, however I have a problem: While it opens a popup window just fine, it doesn't close it again! Just clears the "PopUp" screen for a second before restoring the previous contents.

Any ideas how to resolve this?

---

### Post by kast on 2007-10-25
have you tried adding an 

exit 1 at the end, before the fi?

---

