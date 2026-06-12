---
title: "Howto pause suspend/hibernate when program is running"
date: 2011-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by abuster on 2011-05-19
If you have backups running with backintime, like I do, you will sometime experience suspend/hibernate not working. Suspend/hibernate will fail, because backintime refuses to suspend. Also, if you're backing up over network, the network gets pulled down by pm-suspend, and BIT(backintime) will hang/fail. Then again, when BIT is hanging, suspend will always fail(BIT refuses to suspend).

I've made a simple fix, which pause hibernate/suspend and wait until backintime is done. This fix is also possible to use on other programs, which refuses to suspend, needs a clean shutdown to work in a proper way or should have higher priority than power saving.

```

sudo touch /etc/pm/sleep.d/01_backintime
sudo chmod +x /etc/pm/sleep.d/01_backintime
sudo nano /etc/pm/sleep.d/01_backintime

```/etc/pm/sleep.d/01_backintime:
```

#!/bin/bash
# Arve Seljebu, may 2010

# check if script parameter is hibernate or suspend
case "${1}" in
  hibernate|suspend)
    # run loop as long as program /usr/bin/backintime is running
    while pgrep -f "/usr/bin/backintime "; do
      sleep 5
    done
  ;;
esac

# always exit cleanly
exit 0

```The space behind /usr/bin/backintime is on purpose, as the frontend is called /usr/bin/backintime-gnome. This is also the key to pause suspend, you will need a way to distinguish the program from the others. If you simply use:
```

while pgrep -f backintime; do

```any program with backintime in the command or parameter will cause suspend to wait. For example "nano /etc/pm/sleep.d/01_backintime" will be such a program.

Also, a program that never ends and is matched by pgrep, will cause suspend to always pause. I have not tried to abort suspend if this is happening. Be careful, you have been warned.


Reference: [http://blog.seljebu.no/2011/05/howto-pause-pm-suspend-when-program-is-running/](http://blog.seljebu.no/2011/05/howto-pause-pm-suspend-when-program-is-running/)

---

