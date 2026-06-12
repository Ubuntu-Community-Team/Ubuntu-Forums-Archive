---
title: "[SOLVED] Capture exit value in rc.local"
date: 2007-06-01
forum: Programming Talk
---

### Post by x1a4 on 2007-06-01
Hi,

How do I capture (into a variable) the exit value of a command executed in _/etc/rc.local_?

Thank you.

---

### Post by cwaldbieser on 2007-06-02
> **x1a4 said:**
> Hi,

How do I capture (into a variable) the exit value of a command executed in _/etc/rc.local_?

Thank you.

Something like:

(example /etc/rc.local script)
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#Execute some custom script.
/usr/local/bin/custom_script.sh
#Save the exit status to a variable.
EXIT_STATUS=$?
#Do something later with the exit status...

exit 0

```

---

