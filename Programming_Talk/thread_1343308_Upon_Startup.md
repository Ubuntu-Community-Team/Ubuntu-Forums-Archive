---
title: "Upon Startup"
date: 2009-12-01
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-01
What's Up?

OK, So just wondered how could i execute a text file to run in terminal upon start-up preferable hidden? Pretty simple I hope ;-)

Thanks Bye.

---

### Post by Barriehie on 2009-12-01
Do you want it to run as a daemon so it only shows up in the system monitor, perhaps putting a PID file in /var/run/*somefile.pid*???

If that's the case I've done it by putting a calling script in /etc/init.d and the running script is in ~HOME/bin/daemons.  The daemon script is picsdaemond and it generates a PID file and runs until it either detects a stop file or the machine is shut down/rebooted.

There may be other/better ways to do this but this has been working flawlessly on my machine for weeks.  I initially had it generate a logfile of it's actions and nothing was abnormal so I removed that feature.

Once the calling script is placed in **/etc/init.d/*somefilename*** you'll have to update the init scripts with **sudo update-rc.d *somefilename* defaults**.  See the manpage on update-rc.d to be aware of all of the options.

Calling script:
```

#!/bin/sh

#
# Start picsdaemond daemon that renames and moves
# downloaded .jpg files.
#


bash -c /home/barrie/bin/daemons/picsdaemond 1>/dev/null 2>/dev/null &

exit 0

```

Barrie

---

