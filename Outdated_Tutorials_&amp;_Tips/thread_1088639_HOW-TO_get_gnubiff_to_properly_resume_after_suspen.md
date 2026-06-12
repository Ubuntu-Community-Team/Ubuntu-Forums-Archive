---
title: "HOW-TO: get gnubiff to properly resume after suspend"
date: 2009-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by halocaridina on 2009-03-06
Many people use gnubiff ([http://gnubiff.sourceforge.net/](http://gnubiff.sourceforge.net/)) as a mail notification program that checks for mail and displays headers when new mail has arrived.

One problem with the program is that it does not automatically resume mail checking and notification following a resume from suspend ([https://bugs.launchpad.net/ubuntu/+source/gnubiff/+bug/232367](https://bugs.launchpad.net/ubuntu/+source/gnubiff/+bug/232367)), which is a pain on mobile laptops and/or netbooks.

A fix for this is simply removing the applet from the panel and reloading it, which isn't very efficient.  Below is an easy solution that will do it for you automatically after resuming from suspend.

1) create a script in /etc/pm/sleep.d/ called 00gnubiff

```
sudo gedit /etc/pm/sleep.d/00gnubiff
```

2)  add the following to the script, save and close gedit:

```

#
# Restart gnubiff after suspension
#

case "$1" in
        resume|thaw)
                /usr/bin/killall gnome-panel
        ;;
        *)
        ;;
esac

exit $?

```

3) make the script executable

```
sudo chmod +x /etc/pm/sleep.d/00gnubiff
```

4) DONE!!!

How it works:

Executable scripts in the /etc/pm/sleep.d/ directory are examined when the system is placed into or resumed from suspend.  When the system is resumed, the script is executed, which reloads the gnome panels.  You may notice that following a resume from suspend, your panels are absent.  Don't be alarmed, in a second they will reappear and gnubiff will be working properly.

---

