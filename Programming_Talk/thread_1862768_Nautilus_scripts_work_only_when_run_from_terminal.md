---
title: "Nautilus scripts work only when run from terminal"
date: 2011-10-17
forum: Programming Talk
---

### Post by vivekratnavel on 2011-10-17
I downloaded a script from [here]("http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here") to open a root-enabled instance of a nautilus window in selected location. The script did not work at first. Then I changed it as below to run it from terminal, which works perfectly.
```

#!/bin/bash
# root-nautilus-here
# opens a root-enabled instance of a nautilus window in selected location
# requires sudo priviledges and gksudo, which may involve security risks.
#Install in your ~/Nautilus/scripts directory.
#
# Placed in the public domain by Shane T. Mueller 2001
# Fixes provided by Doug Nordwall
#
# 2004.04.18 -- keith@penguingurus.com - Added gksudo usage to provide popup
#               password window if sudo has expired.  Line only echos got
#               root to std output.  But gksudo updates your sudo access
#               privs, so running nautilus with sudo will succeed
#               without asking for a password.


func()
{
gksudo -u root -k -m "Enter Root password for nautilus root access" /bin/echo "Got Root?"
eval sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
exit 0
}

export -f func

gnome-terminal --execute bash -c "func ; bash"

```

How to make the script work without having to run from the terminal?

---

