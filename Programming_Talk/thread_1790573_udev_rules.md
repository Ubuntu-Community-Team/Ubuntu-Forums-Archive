---
title: "udev rules"
date: 2011-06-25
forum: Programming Talk
---

### Post by jaypatel on 2011-06-25
I am using udev rules to detect removable drives which executes a script having only this line:
notify-send "Drive detected".
```

#!/bin/bash
notify-send "Drive detected"

```1.My udev rules are perfect.Had them checked
2.Script is getting executed.Tested it by using touch /tmp/test command in the script.
3.The script works fine when run manually.
What is the problem?

---

### Post by Arndt on 2011-06-25
> **jaypatel said:**
> I am using udev rules to detect removable drives which executes a script having only this line:
notify-send "Drive detected".
```

#!/bin/bash
notify-send "Drive detected"

```1.My udev rules are perfect.Had them checked
2.Script is getting executed.Tested it by using touch /tmp/test command in the script.
3.The script works fine when run manually.
What is the problem?

You don't say what the problem is, but I guess notify-send does something useful when you run the script by hand, and this doesn't happen when it's executed by udev.

What is notify-send? Is there some difference in the environment of the two different executions, like the DISPLAY variable or something?

---

### Post by Cheesehead on 2011-06-25
Try sending the notifications to an active display. Scripts run by udev and cron and root don't inherit your user's $DISPLAY environment variable.```
DISPLAY=:0.0 notify-send "Drive detected"
```

---

### Post by jaypatel on 2011-06-27
@Cheesehead.Thanks a lot.Worked like magic :)

---

